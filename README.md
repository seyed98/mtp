# MTProtoProxy Auto Installer "" CentOS 7 ""
A very small script to install MTProtoProxy On CentOS 7
### Why this installer?
* Generate random secret
* Automatically configure firewall
* Create a service to run it on background and start up
* Setup proxy with small knowledge
* Simple updater
* Revoke and add secrets after install
## Install
On your machine run
```
curl -o MTProtoProxyInstall.sh -L https://git.io/fhkCo && bash MTProtoProxyInstall.sh
```
and wait until the setup finishes the install you will see the links after install. (Or enter `systemctl status mtprotoproxy -l` in case of any failure to see the links) <br />
To update, uninstall, change port, revoke secret or... the proxy, run this script again. <br />
### Firewall
Setup will try to configure the proxy on public zone. However you can manually enter these rules in case of any error or whatever. Just rerun the script and choose `Generate Firewalld Rules` and script will generate and apply firewall rules.
### Random Padding
Due to some ISPs detecting MTProxy by packet sizes, random padding is added to packets if such mode is enabled.
It's only enabled for clients which request it.
Add dd prefix to secret (cafe...babe => ddcafe...babe) to enable this mode on client side.

To deny all connections but ones with random padding, set "Secure Mode" true.
##### Install Master Branch
```
curl -o MTProtoProxyInstall.sh -L https://git.io/fhkCo && bash MTProtoProxyInstall.sh -m
```
## Control The Proxy
### Service
Use `systemctl start mtprotoproxy` to start, `systemctl stop mtprotoproxy` to stop and `systemctl status mtprotoproxy -l` to see logs of script.
### Config
To manually config proxy edit config.py in /opt/mtprotoproxy to change the config. Then restart the server using `systemctl restart mtprotoproxy` or just run script again.
