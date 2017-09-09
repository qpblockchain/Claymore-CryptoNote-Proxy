# Claymore CryptoNote No DevFee Proxy
Removes Claymore's 2%-2.5% mining developer fee using Stratum Proxy. Tested on Windows 10 Pro x64 with **_Claymore CryptoNote GPU Miner v9.7 Beta_**.

## How it works?
This proxy is placed between Claymore and Internet in order to catch the mining fee login packet and replacing the DevFee address with your wallet address.

## Requirements
#### Windows executable
* .Net Framework 4.0 or better

## Proxy.txt configuration file
```json
{
    "local_host": "127.0.0.1:14001",
    "pool_address": "xmr-us-east1.nanopool.org:14433",
    "wallet": "MYWALLET",
    "worker": "little_worker",
    "ssl": "true"
}
```
- **local_host**: IP/host name and Port to use as the proxy/server. Do **NOT** use "127.0.0.1" or "localhost", see the link [below](#Configure-a-custom-IP-and-host-name-in-Windows).
- **pool_address**: The pool address. For SSL/TLS you can prefix with ssl://
- **wallet**: Your Monero or exchange wallet with the Base and PaymentID.
- **worker**: Worker name for the DevFee. Can be "null".
- **ssl**: "true" to use SSL/TLS connection to the pool, or "false".

## Setup
### Configure a custom IP and host name in Windows
See [Adding a custom IP and Hostname in the Wiki](https://github.com/NanMetal/Claymore-CryptoNote-Proxy/wiki/Add-a-custom-IP-and-host-name).

### Configure Claymore
Edit your ```.bat``` or ```config.txt``` file with the ```local_host``` IP/host name used in the proxy:
```batch
-o ssl://xmr.mycustompool.org:14001 ...
```

## Run
Double click ```stratum_proxy.exe``` and Claymore software.

## Features
* Redirect DevFee shares to your wallet
* Supports SSL/TLS (only pool connection)
* Shows shares accepted, rejected and DevFee
* Custom worker name for DevFee
* Low CPU and memory usage
* Detect when a miner connect and disconnects
* Colorful output

## FAQ

### What is the connection flow of SSL/TLS?
Claymore Software (**NOT using SSL/TLS**) -> Stratum Proxy (using SSL/TLS) -> Remote Pool (using SSL/TLS)

### Why don't use Claymore with SSL/TLS?
Currently only the proxy will use SSL/TLS with the remote pool. So, don't use Claymore with SSL/TLS.

### What if I use other pool?
Claymore tries to mine the devfee on the same pool as you. You can try using  "-allpools 1" if it is not working.

### Is it compatible with every currency?
This proxy was designed to be used with Claymore CryptoNote version. I did not test others CryptoNight-like currencies.

### How can I check if it works?
You can check your pool stats, but some pool ignore small mining time if it did not find a share. But it mines for you!:

![devfee_shares](https://user-images.githubusercontent.com/6496385/29857323-86394312-8d2e-11e7-9ffa-83ad8399b747.png)

### Claymore warns me something about local proxy...
Claymore checks the pool's IP to avoid local proxies, if you have the warning make sure you are not using ```localhost``` or ```127.0.0.1```.  See [Adding a custom IP and Hostname in the Wiki](https://github.com/NanMetal/Claymore-CryptoNote-Proxy/wiki/Add-a-custom-IP-and-host-name).

### This works with the Claymore CPU version?
Yes but it's slow. Use [XMR-Stak-CPU - Monero mining software](https://github.com/fireice-uk/xmr-stak-cpu), is alot better.

## Credit & Donations
You can send a donation (ETH) to the authors of the original script:
- [JuicyPasta](https://github.com/JuicyPasta) - 0xfeE03fB214Dc0EeDc925687D3DC9cdaa1260e7EF (Ethereum)
- [Drdada](https://github.com/drdada) - 0xB7716d5A768Bc0d5bc5c216cF2d85023a697D04D (ethermine)

And if you want, not necessary:
- XMR: 48Ba1QniibJ34Di57C96M58Gq5EQ7ixuUNxcwnfe8zeCgy8UjCZWf4NAQW5P3iuE8EYc3MkA7DQ9USWDmijbN7b9HPZVTb8
- BTC: 3DTo7Nkkg64YhpdA9NnmV3TuDiQ8WcufrU
