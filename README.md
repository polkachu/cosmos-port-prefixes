# Cosmos Port Prefixes

## Rationale

Node operators in the Cosmos ecosystem often wants to run multiple Cosmos SDK-based nodes on the sames server to save cost.

The Cosmos SDK `init` command will generate `config.toml` and `app.toml` for each node. Without revision, the ports in these files will conflict with each other if multiple nodes are ran on the same server.

This project is an attempt to standardize these ports while avoiding port conflict. While any random non-conflicting ports can do, a standardized port prefix system can make the port assignment more predictable. Moreover, if two node operators follow the same system, they can easily exchange deployment scripts without breaking codes.

## How to Use

The best way to use the port prefix system is to use [Ansible deployment script](https://github.com/polkachu/cosmos-validators/blob/main/roles/node_configure/vars/main.yml).

You can also change these 9 ports (5 in config.toml and 4 in app.toml) manually. See below.

```yaml
config.toml:
  'laddr = "tcp://0.0.0.0:26656"': 'laddr = "tcp://0.0.0.0:{{ custom_port_prefix }}56"'
  'laddr = "tcp://127.0.0.1:26657"': 'laddr = "tcp://0.0.0.0:{{ custom_port_prefix }}57"'
  'proxy_app = "tcp://127.0.0.1:26658"': 'proxy_app = "tcp://127.0.0.1:{{ custom_port_prefix }}58"'
  'prometheus_listen_addr = ":26660"': 'prometheus_listen_addr = ":{{ custom_port_prefix }}61"'
  'pprof_laddr = "localhost:6060"': 'pprof_laddr = "localhost:{{ custom_port_prefix }}60"'
app.toml:
  'address = "tcp://0.0.0.0:1317"': 'address = "tcp://0.0.0.0:{{ custom_port_prefix }}17"'
  'address = ":8080"': 'address = ":{{ custom_port_prefix }}80"'
  'address = "0.0.0.0:9090"': 'address = "0.0.0.0:{{ custom_port_prefix }}90"'
  'address = "0.0.0.0:9091"': 'address = "0.0.0.0:{{ custom_port_prefix }}91"'
```

## Supported Chains and Prefixes

Note: Please do not use 266 as port prefix because this is the default

| Network             | Port Prefix |
| ------------------- | ----------- |
| Hypersign           | 109         |
| Kyve                | 110         |
| Quicksilver         | 111         |
| Defund              | 112         |
| Gitopia             | 113         |
| Deweb               | 114         |
| Archway             | 115         |
| Celestia            | 116         |
| Terra2              | 117         |
| Kujira              | 118         |
| Sei                 | 119         |
| Echelon             | 120         |
| Paloma              | 121         |
| Stride              | 122         |
| Cudos               | 123         |
| Althea              | 124         |
| Osmosis             | 125         |
| Juno                | 126         |
| Nomic               | 127         |
| Akash               | 128         |
| Chihuahua           | 129         |
| Bitcanna            | 130         |
| Comdex              | 131         |
| Sifchain            | 132         |
| Konstellation       | 133         |
| Evmos               | 134         |
| Kichain             | 135         |
| Umee                | 136         |
| Stargaze            | 137         |
| Cerberus            | 138         |
| Kava                | 139         |
| Certik              | 140         |
| Sommelier           | 141         |
| Gravity             | 142         |
| Injective           | 143         |
| Agoric              | 144         |
| Crescent            | 145         |
| Assetmantle         | 146         |
| Meme                | 147         |
| Galaxy              | 148         |
| Cosmos              | 149         |
| Androma             | 150         |
| Axelar              | 151         |
| Fetch               | 152         |
| Nym                 | 153         |
| Persistence         | 154         |
| Canto               | 155         |
| Passage             | 156         |
| Craft               | 157         |
| Source              | 158         |
| Teritori            | 159         |
| Bitsong             | 160         |
| Cheqd               | 161         |
| Desmos              | 162         |
| Dig                 | 163         |
| Firmachain          | 164         |
| IDEP                | 165         |
| Impacthub           | 166         |
| Lum                 | 167         |
| Odin                | 168         |
| Omniflix            | 169         |
| Vidulum             | 170         |
| Secret              | 171         |
| Rebus               | 172         |
| Nois                | 173         |
| Empower             | 174         |
| Jackal              | 175         |
| Okp4                | 176         |
| Saage               | 177         |
| loyal               | 178         |
| ICS Apollo          | 179         |
| ICS Sputnik         | 180         |
| Ollo                | 181         |
| Quasar              | 182         |
| Joe                 | 183         |
| Humans              | 184         |
| Mars                | 185         |
| ICS Curly           | 186         |
| ICS Gopher          | 187         |
| ICS Hero            | 188         |
| ICS Larry           | 189         |
| ICS Moe             | 190         |
| ICS Neutron         | 191         |
| ICS Slasher         | 192         |
| Alliance            | 193         |
| Pylons              | 194         |
| Heimdall            | 195         |
| Carbon              | 196         |
| Nolus               | 197         |
| Nibiru              | 198         |
| Lava                | 199         |
| Namada              | 200         |
| XPLA                | 201         |
| Crypto.com          | 202         |
| Planq               | 203         |
| Uptick              | 204         |
| Dymension           | 205         |
| Babylon             | 206         |
| Whitewhale(migaloo) | 207         |
| Alliance ordos      | 208         |
| Alliance corrino    | 209         |
| Alliance harkonnen  | 210         |
| Alliance atreides   | 211         |
| Andromeda           | 212         |
| eightball           | 213         |
| BlockX              | 214         |
| Noble               | 215         |
| Ojo                 | 216         |
| Aura                | 217         |

## JSON API

Here is the [JSON API](https://raw.githubusercontent.com/polkachu/cosmos-port-prefixes/main/networks.json).
