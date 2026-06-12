---
title: "system proxy 12.04"
date: 2012-06-30
forum: Networking &amp; Wireless
---

### Post by falop on 2012-06-30
hi im using 12.04 with classic gnome desktop the proxy options havint worked since damb unity interface came along so i have been setting up a system proxy in terminal with these commands to use tor 
gsettings set org.gnome.system.proxy.socks host '127.0.0.1'
gsettings set org.gnome.system.proxy.socks port 9050
gsettings set org.gnome.system.proxy mode 'manual'
 and to stop it 
gsettings set org.gnome.system.proxy mode 'none'

this does chainge the ip address in firefox but when i check my external ip in terminal with command 
wget -q -O - checkip.dyndns.org|sed -e 's/.*Current IP Address: //' -e 's/<.*$//'

it shows my unproxied ip address.
 so does anyoine know of a way to send ALL network traffic through a system proxy on ubuntu 12.04 would greatly appreciate it thanks.

---

### Post by sanderj on 2012-07-01
I have only a little experience with SOCKS and proxies in general, but my reaction would be:

It's up to the application to be aware of a proxy / proxy setting at all, and to use it or not. And there are different ways to define a proxy. Wget for example wants that info in the *_proxy environment. So, do the commands you use set that environment variables?

And I wonder if wget can use a *SOCKS* proxy; it looks like it can use a *HTTP* Proxy.

See [http://www.switchroot.com/how-to-run-apt-get-wget-whois-etc-via-socks-proxy-using-proxychains](http://www.switchroot.com/how-to-run-apt-get-wget-whois-etc-via-socks-proxy-using-proxychains)


Anyway: if you want all traffic rerouted, I think you see a VPN.

---

