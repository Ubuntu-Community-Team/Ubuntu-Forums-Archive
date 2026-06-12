---
title: "NetworkManager doesn't get correct IP address?"
date: 2011-03-05
forum: Networking &amp; Wireless
---

### Post by mvmacd on 2011-03-05
Hey. I usually use Wicd, or the old fashioned 
```
iwconfig eth1 essid abc; dhclient eth1;
``` method to connect to wifi... But when I share internet (with usb long-range adapter) I am forced to use NetworkManager, because I have no other multi-interface wifi manager. Anyway, I am connecting to a shared connection, from Vista. (Source: USB Wifi, sharing via: AdHoc; Vista) 

In the network settings, the IPv4 is set to Automatic DHCP. So I connect to the AdHoc network, (SSID is "abc") and in the syslog, this is what I get:
```


Mar  5 16:01:43 dell NetworkManager[2270]: <info> Starting dnsmasq...
Mar  5 16:01:43 dell NetworkManager[2270]: <info> (eth1): device state change: 7 -> 8 (reason 0)
Mar  5 16:01:43 dell NetworkManager[2270]: <info> Activation (eth1) successful, device activated.
Mar  5 16:01:43 dell NetworkManager[2270]: <info> Activation (eth1) Stage 5 of 5 (IP Configure Commit) complete.
Mar  5 16:01:43 dell dnsmasq[2349]: started, version 2.55 cachesize 150
Mar  5 16:01:43 dell dnsmasq[2349]: compile time options: IPv6 GNU-getopt DBus I18N DHCP TFTP
Mar  5 16:01:43 dell dnsmasq-dhcp[2349]: DHCP, IP range 10.42.43.10 -- 10.42.43.100, lease time 1h
Mar  5 16:01:43 dell dnsmasq[2349]: no servers found in /etc/resolv.conf, will retry
Mar  5 16:01:43 dell dnsmasq[2349]: cleared cache
Mar  5 16:01:44 dell ntpdate[2474]: can't find host ntp.ubuntu.com
Mar  5 16:01:44 dell ntpdate[2474]: no servers can be used, exiting
Mar  5 16:01:45 dell nm-dispatcher.action: Script '/etc/NetworkManager/dispatcher.d/01ifupdown' exited with error status 1.
Mar  5 16:01:48 dell dnsmasq-dhcp[2349]: DHCPDISCOVER(eth1) 192.168.1.106 00:22:fb:57:8c:92 
Mar  5 16:01:48 dell dnsmasq-dhcp[2349]: DHCPOFFER(eth1) 10.42.43.73 00:22:fb:57:8c:92 
Mar  5 16:01:48 dell dnsmasq-dhcp[2349]: DHCPDISCOVER(eth1) 192.168.1.106 00:22:fb:57:8c:92 
Mar  5 16:01:48 dell dnsmasq-dhcp[2349]: DHCPOFFER(eth1) 10.42.43.73 00:22:fb:57:8c:92 
Mar  5 16:01:49 dell dnsmasq-dhcp[2349]: DHCPDISCOVER(eth1) 192.168.1.106 00:22:fb:57:8c:92 
Mar  5 16:01:49 dell dnsmasq-dhcp[2349]: DHCPOFFER(eth1) 10.42.43.73 00:22:fb:57:8c:92 
Mar  5 16:01:49 dell dnsmasq-dhcp[2349]: DHCPREQUEST(eth1) 10.42.43.73 00:22:fb:57:8c:92 
Mar  5 16:01:49 dell dnsmasq-dhcp[2349]: DHCPACK(eth1) 10.42.43.73 00:22:fb:57:8c:92 Carol-PC

```
I tried it in Wicd, and it gets a 192.168.1.xx IP address.. (although earlier, it was doing the same thing! getting an 10.42.43.xx IP). Why does it do this? I found line in my /etc/hosts that started with "10.42.43.4" I think it was, so I deleted that line. (I think it pointed to localhost, or dell [my laptop's hostname])

So anyway, yeah, if I run "$ dhcpclient eth1" after I connect, it connects and gets a correct IP. but how come it keeps getting 10.42.43.x on its own? 
Thanks!

Oh, while I'm on the subj, how come It takes several tries of "$ iwconfig eth1 essid abc" before iwconfig says the SSID is abc? I have a script in ~/bin, called "con," so in my script I have it run iwconfig several times to apply the SSID. I noticed later, the script didn't work hardly at all, anymore (always getting 10.42.43.x, or something like that), so I made a function to loop, at second intervals, while the dhclient is running, to set the essid. and that seemed to fix it.. but does anybody know why I have to do it more than one time (even with the NetworkManager, and Wicd daemon not running? Because I'm *pretty* sure I disabled them and tried it, but maybe I'm mistaken..)? thanks!

---

