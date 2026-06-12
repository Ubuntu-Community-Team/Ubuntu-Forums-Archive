---
title: "WAP Crashing"
date: 2010-06-03
forum: Networking &amp; Wireless
---

### Post by lvleph on 2010-06-03
I created a Wireless Access Point out of my Linux Mint box using **hostapd**, **dnsmasq**, and **dhcp3-server**. For some reason the WiFi loses connectivity at random times. The only way to get it back up and running is to do
```
sudo /etc/init.d/networking restart
sudo /etc/init.d/hostapd restart
```
or restart the computer.
I can't figure out why it is doing this and there appears to be nothing in **dmesg**, except something about ipv6.
```
[   13.268897] VBoxDrv: dbg - g_abExecMemory=ffffffffa0492a20
[   13.268961] vboxdrv: fAsync=0 offMin=0x2e3 offMax=0x2a8c
[   13.269037] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   13.269040] vboxdrv: Successfully loaded version 3.1.6 (interface 0x00100001).
[   13.564594] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control rx
[   13.565342] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   14.284918] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
[   17.419326] usb 4-1: usbfs: interface 1 claimed by usblp while 'usb' sets config #1
[   23.320009] wlan0: no IPv6 routers present
[   23.920018] eth0: no IPv6 routers present

```

However, **/var/log/syslog | grep dhcp** shows something
```
cat /var/log/syslog.1 | grep dhcp
Jun  2 09:20:08 Media-PC dnsmasq-dhcp[1456]: DHCPINFORM(wlan0) 192.168.1.9 00:21:63:23:91:8d 
Jun  2 09:20:08 Media-PC dnsmasq-dhcp[1456]: DHCPACK(wlan0) 192.168.1.9 00:21:63:23:91:8d George-PC
Jun  2 13:11:53 Media-PC dnsmasq-dhcp[1456]: DHCPREQUEST(wlan0) 192.168.1.9 00:21:63:23:91:8d 
Jun  2 13:11:53 Media-PC dnsmasq-dhcp[1456]: DHCPACK(wlan0) 192.168.1.9 00:21:63:23:91:8d George-PC
Jun  2 15:34:43 Media-PC dnsmasq-dhcp[1456]: DHCPREQUEST(wlan0) 192.168.1.9 00:21:63:23:91:8d 
Jun  2 15:34:43 Media-PC dnsmasq-dhcp[1456]: DHCPACK(wlan0) 192.168.1.9 00:21:63:23:91:8d George-PC
Jun  2 15:35:02 Media-PC dnsmasq-dhcp[1456]: DHCPINFORM(wlan0) 192.168.1.9 00:21:63:23:91:8d 
Jun  2 15:35:02 Media-PC dnsmasq-dhcp[1456]: DHCPACK(wlan0) 192.168.1.9 00:21:63:23:91:8d George-PC
Jun  2 16:52:53 Media-PC dnsmasq-dhcp[1395]: DHCP, IP range 192.168.1.3 -- 192.168.1.127, lease time 12h
Jun  2 16:52:54 Media-PC dhclient: For info, please visit https://www.isc.org/software/dhcp/
Jun  2 16:52:55 Media-PC dhcpd: Wrote 0 leases to leases file.
Jun  2 16:52:55 Media-PC dhcpd: Can't bind to dhcp address: Address already in use
Jun  2 16:52:55 Media-PC dhcpd: Please make sure there is no other dhcp server
Jun  2 16:52:55 Media-PC dhcpd: running and that there's no entry for dhcp or
Jun  2 16:52:55 Media-PC dhcpd: bootp in /etc/inetd.conf.   Also make sure you
Jun  2 16:52:55 Media-PC dhcpd: are not running HP JetAdmin software, which
Jun  2 16:52:55 Media-PC dhcpd: includes a bootp server.
Jun  2 16:53:47 Media-PC dnsmasq-dhcp[1395]: DHCPREQUEST(wlan0) 192.168.1.9 00:21:63:23:91:8d 
Jun  2 16:53:47 Media-PC dnsmasq-dhcp[1395]: DHCPACK(wlan0) 192.168.1.9 00:21:63:23:91:8d George-PC
Jun  2 18:09:32 Media-PC dnsmasq-dhcp[1395]: DHCPREQUEST(wlan0) 192.168.1.9 00:21:63:23:91:8d 
Jun  2 18:09:32 Media-PC dnsmasq-dhcp[1395]: DHCPACK(wlan0) 192.168.1.9 00:21:63:23:91:8d George-PC
Jun  2 18:09:37 Media-PC dnsmasq-dhcp[1395]: DHCPINFORM(wlan0) 192.168.1.9 00:21:63:23:91:8d 
Jun  2 18:09:37 Media-PC dnsmasq-dhcp[1395]: DHCPACK(wlan0) 192.168.1.9 00:21:63:23:91:8d George-PC
Jun  2 19:05:30 Media-PC dnsmasq-dhcp[1421]: DHCP, IP range 192.168.1.3 -- 192.168.1.127, lease time 12h
Jun  2 19:05:31 Media-PC dhclient: For info, please visit https://www.isc.org/software/dhcp/
Jun  2 19:05:31 Media-PC dhcpd: Wrote 0 leases to leases file.
Jun  2 19:05:31 Media-PC dhcpd: Can't bind to dhcp address: Address already in use
Jun  2 19:05:31 Media-PC dhcpd: Please make sure there is no other dhcp server
Jun  2 19:05:31 Media-PC dhcpd: running and that there's no entry for dhcp or
Jun  2 19:05:31 Media-PC dhcpd: bootp in /etc/inetd.conf.   Also make sure you
Jun  2 19:05:31 Media-PC dhcpd: are not running HP JetAdmin software, which
Jun  2 19:05:31 Media-PC dhcpd: includes a bootp server.
Jun  2 19:06:05 Media-PC dnsmasq-dhcp[1421]: DHCPREQUEST(wlan0) 192.168.1.9 00:21:63:23:91:8d 
Jun  2 19:06:05 Media-PC dnsmasq-dhcp[1421]: DHCPACK(wlan0) 192.168.1.9 00:21:63:23:91:8d George-PC
Jun  2 21:47:44 Media-PC dnsmasq-dhcp[1429]: DHCP, IP range 192.168.1.3 -- 192.168.1.127, lease time 12h
Jun  2 21:47:45 Media-PC dhcpd: Wrote 0 leases to leases file.
Jun  2 21:47:45 Media-PC dhcpd: Can't bind to dhcp address: Address already in use
Jun  2 21:47:45 Media-PC dhcpd: Please make sure there is no other dhcp server
Jun  2 21:47:45 Media-PC dhcpd: running and that there's no entry for dhcp or
Jun  2 21:47:45 Media-PC dhcpd: bootp in /etc/inetd.conf.   Also make sure you
Jun  2 21:47:45 Media-PC dhcpd: are not running HP JetAdmin software, which
Jun  2 21:47:45 Media-PC dhcpd: includes a bootp server.
Jun  2 21:47:45 Media-PC dhclient: For info, please visit https://www.isc.org/software/dhcp/
Jun  2 21:47:49 Media-PC dnsmasq-dhcp[1429]: DHCPREQUEST(wlan0) 192.168.1.9 00:21:63:23:91:8d 
Jun  2 21:47:49 Media-PC dnsmasq-dhcp[1429]: DHCPACK(wlan0) 192.168.1.9 00:21:63:23:91:8d George-PC
Jun  2 22:30:37 Media-PC dnsmasq-dhcp[1431]: DHCP, IP range 192.168.1.3 -- 192.168.1.127, lease time 12h
Jun  2 22:30:38 Media-PC dhcpd: Wrote 0 leases to leases file.
Jun  2 22:30:38 Media-PC dhclient: For info, please visit https://www.isc.org/software/dhcp/
Jun  2 22:30:38 Media-PC dhcpd: Can't bind to dhcp address: Address already in use
Jun  2 22:30:38 Media-PC dhcpd: Please make sure there is no other dhcp server
Jun  2 22:30:38 Media-PC dhcpd: running and that there's no entry for dhcp or
Jun  2 22:30:38 Media-PC dhcpd: bootp in /etc/inetd.conf.   Also make sure you
Jun  2 22:30:38 Media-PC dhcpd: are not running HP JetAdmin software, which
Jun  2 22:30:38 Media-PC dhcpd: includes a bootp server.
Jun  2 22:31:23 Media-PC dnsmasq-dhcp[1431]: DHCPREQUEST(wlan0) 192.168.1.9 00:21:63:23:91:8d 
Jun  2 22:31:23 Media-PC dnsmasq-dhcp[1431]: DHCPACK(wlan0) 192.168.1.9 00:21:63:23:91:8d George-PC
Jun  3 02:42:11 Media-PC dnsmasq-dhcp[1431]: DHCPREQUEST(wlan0) 192.168.1.9 00:21:63:23:91:8d 
Jun  3 02:42:11 Media-PC dnsmasq-dhcp[1431]: DHCPACK(wlan0) 192.168.1.9 00:21:63:23:91:8d George-PC
Jun  3 02:55:51 Media-PC dnsmasq-dhcp[1431]: DHCPREQUEST(wlan0) 192.168.1.9 00:21:63:23:91:8d 
Jun  3 02:55:51 Media-PC dnsmasq-dhcp[1431]: DHCPACK(wlan0) 192.168.1.9 00:21:63:23:91:8d George-PC
Jun  3 03:12:31 Media-PC dnsmasq-dhcp[1431]: DHCPREQUEST(wlan0) 192.168.1.9 00:21:63:23:91:8d 
Jun  3 03:12:31 Media-PC dnsmasq-dhcp[1431]: DHCPACK(wlan0) 192.168.1.9 00:21:63:23:91:8d George-PC
Jun  3 03:36:04 Media-PC dnsmasq-dhcp[1431]: DHCPREQUEST(wlan0) 192.168.1.9 00:21:63:23:91:8d 
Jun  3 03:36:04 Media-PC dnsmasq-dhcp[1431]: DHCPACK(wlan0) 192.168.1.9 00:21:63:23:91:8d George-PC
Jun  3 05:24:29 Media-PC dnsmasq-dhcp[1431]: DHCPREQUEST(wlan0) 192.168.1.9 00:21:63:23:91:8d 
Jun  3 05:24:29 Media-PC dnsmasq-dhcp[1431]: DHCPACK(wlan0) 192.168.1.9 00:21:63:23:91:8d George-PC
Jun  3 05:53:56 Media-PC dnsmasq-dhcp[1431]: DHCPREQUEST(wlan0) 192.168.1.9 00:21:63:23:91:8d 
Jun  3 05:53:56 Media-PC dnsmasq-dhcp[1431]: DHCPACK(wlan0) 192.168.1.9 00:21:63:23:91:8d George-PC
Jun  3 05:57:35 Media-PC dnsmasq-dhcp[1431]: DHCPREQUEST(wlan0) 192.168.1.9 00:21:63:23:91:8d 
Jun  3 05:57:35 Media-PC dnsmasq-dhcp[1431]: DHCPACK(wlan0) 192.168.1.9 00:21:63:23:91:8d George-PC
Jun  3 06:02:16 Media-PC dnsmasq-dhcp[1431]: DHCPREQUEST(wlan0) 192.168.1.9 00:21:63:23:91:8d 
Jun  3 06:02:16 Media-PC dnsmasq-dhcp[1431]: DHCPACK(wlan0) 192.168.1.9 00:21:63:23:91:8d George-PC
Jun  3 06:02:19 Media-PC dnsmasq-dhcp[1431]: DHCPINFORM(wlan0) 192.168.1.9 00:21:63:23:91:8d 
Jun  3 06:02:19 Media-PC dnsmasq-dhcp[1431]: DHCPACK(wlan0) 192.168.1.9 00:21:63:23:91:8d George-PC
Jun  3 07:09:31 Media-PC dnsmasq-dhcp[1431]: DHCPREQUEST(wlan0) 192.168.1.9 00:21:63:23:91:8d 
Jun  3 07:09:31 Media-PC dnsmasq-dhcp[1431]: DHCPACK(wlan0) 192.168.1.9 00:21:63:23:91:8d George-PC
Jun  3 07:12:55 Media-PC dnsmasq-dhcp[1431]: DHCPREQUEST(wlan0) 192.168.1.9 00:21:63:23:91:8d 
Jun  3 07:12:55 Media-PC dnsmasq-dhcp[1431]: DHCPACK(wlan0) 192.168.1.9 00:21:63:23:91:8d George-PC
Jun  3 07:14:32 Media-PC dnsmasq-dhcp[1431]: DHCPINFORM(wlan0) 192.168.1.9 00:21:63:23:91:8d 
Jun  3 07:14:32 Media-PC dnsmasq-dhcp[1431]: DHCPACK(wlan0) 192.168.1.9 00:21:63:23:91:8d George-PC
Jun  3 10:31:26 Media-PC dnsmasq-dhcp[1431]: DHCPREQUEST(wlan0) 192.168.1.9 00:21:63:23:91:8d 
Jun  3 10:31:26 Media-PC dnsmasq-dhcp[1431]: DHCPACK(wlan0) 192.168.1.9 00:21:63:23:91:8d George-PC
Jun  3 10:42:54 Media-PC dnsmasq-dhcp[1431]: DHCPREQUEST(wlan0) 192.168.1.9 00:21:63:23:91:8d 
Jun  3 10:42:54 Media-PC dnsmasq-dhcp[1431]: DHCPACK(wlan0) 192.168.1.9 00:21:63:23:91:8d George-PC
Jun  3 10:53:19 Media-PC dnsmasq-dhcp[1431]: DHCPREQUEST(wlan0) 192.168.1.9 00:21:63:23:91:8d 
Jun  3 10:53:19 Media-PC dnsmasq-dhcp[1431]: DHCPACK(wlan0) 192.168.1.9 00:21:63:23:91:8d George-PC

```
10:30 was when I restarted the networking and hostapd. I am unsure why this is happening
```
Jun  2 21:47:44 Media-PC dnsmasq-dhcp[1429]: DHCP, IP range 192.168.1.3 -- 192.168.1.127, lease time 12h
Jun  2 21:47:45 Media-PC dhcpd: Wrote 0 leases to leases file.
Jun  2 21:47:45 Media-PC dhcpd: Can't bind to dhcp address: Address already in use
Jun  2 21:47:45 Media-PC dhcpd: Please make sure there is no other dhcp server
Jun  2 21:47:45 Media-PC dhcpd: running and that there's no entry for dhcp or
Jun  2 21:47:45 Media-PC dhcpd: bootp in /etc/inetd.conf.   Also make sure you
Jun  2 21:47:45 Media-PC dhcpd: are not running HP JetAdmin software, which
Jun  2 21:47:45 Media-PC dhcpd: includes a bootp server.
Jun  2 21:47:45 Media-PC dhclient: For info, please visit https://www.isc.org/software/dhcp/

```
Or why George-PC is continually reconnecting. That PC is running Windows Vista, so that may have something to do with it. I don't have control over that comp, but I can get the owner to do what ever is needed.

**lspci -k | grep Network**
```

04:06.0 Network controller: Atheros Communications Inc. AR922X Wireless Network Adapter (rev 01)
	Kernel driver in use: ath9k
	Kernel modules: ath9k

```

**/etc/network/interfaces**
```

auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet static
	address 192.168.1.2
	netmask 255.255.255.0
	broadcast 192.168.1.255

```

**/etc/dhcp3/dhcpd.conf**
```

default-lease-time              100000;
max-lease-time                  100000;

option subnet-mask              255.255.255.0;
option broadcast-address        192.168.1.255;
option routers                  192.168.1.2;
option domain-name-servers      208.67.222.222, 208.67.220.220;

subnet 192.168.1.0 netmask 255.255.255.0 {
        range 192.168.1.3 192.168.1.220;
				        }

```

**/etc/hostapd/hostapd.conf**
```

interface=wlan0
driver=nl80211
ssid=#######
channel=6
hw_mode=g
auth_algs=1
wpa=2
wpa_passphrase=#######
wpa_key_mgmt=WPA-PSK
wpa_pairwise=TKIP 
#CCMP
rsn_pairwise=CCMP

```

The only thing different from the default **dnmasq.conf** is 
```

interface=wlan0
dhcp-range=192.168.1.3,192.168.1.127,12h

```

---

### Post by lvleph on 2010-06-04
Bump

---

### Post by lvleph on 2010-06-06
Come on someone must at least know what logs to look at. I just need help figuring out what is going on. I am getting really annoyed by this.

---

### Post by size_XXM on 2010-06-06
First of all - why are you using dhcpd *and* dnsmasq? Am I missing something here, or are you trying to run two DHCP servers on the same interface?

---

### Post by lvleph on 2010-06-06
I was following a tutorial. I did think this was strange. I mostly use the dhcp3, so i will uninstall dnsmasq and see what happens.

---

### Post by lvleph on 2010-06-06
Unfortunately, without dnsmasq I cannot browse the internet through my wireless. So I must have something setup incorrectly.

EDIT: However, getting rid of dhcp3 doesn't seem to hurt things.

---

### Post by size_XXM on 2010-06-06
I don't know aout dhpcd as I use dnsmasq exclusively myself, but isn't there a line which specifies an interface or something? Alternatively, get rid of dhcpd and try that way.

Another thing - I suppose you use /etc/network/interfaces to configure your network - no network manager or something like that? On my router, I typically don't need to touch init.d/hostapd - relevant parts of my interfaces file looks like this:
```
auto wlan0
iface wlan0 inet manual
        hostapd /etc/hostapd/hostapd.conf
auto br0
iface br0 inet static
        bridge_ports eth0  wlan0
        bridge_maxwait 0
        bridge_stp off
        address 192.168.1.1
        network 192.168.1.0

```

---

### Post by lvleph on 2010-06-06
Do you mind posting your hostapd.conf, dnmasq.conf also? And any other relevant files. I thought getting rid of dhcp3-server worked, but in fact it didn't.

---

### Post by lvleph on 2010-06-06
Using your interfaces file as a model resulted in a loss of all internet. I have never been able to successfully use a bridge.

---

### Post by size_XXM on 2010-06-06
No problem, do keep in mind I'm using it as a bridge, so omit/change any relevant settings.
```
# cat /etc/hostapd/hostapd.conf | grep -v ^\# | uniq
interface=wlan0
bridge=br0
driver=nl80211

ssid=#####

country_code=SK
ieee80211d=1

hw_mode=g
channel=11

macaddr_acl=0
auth_algs=1
ignore_broadcast_ssid=0

ieee80211n=1
ht_capab=[HT40-][SHORT-GI-40][MAX-AMSDU-3839][DSSS_CCK-40]

wpa=2
wpa_passphrase=########
wpa_key_mgmt=WPA-PSK
wpa_pairwise=CCMP
rsn_pairwise=CCMP

# cat /etc/dnsmasq.conf | grep -v ^\# | uniq
interface=br0
dhcp-range=192.168.1.2,192.168.1.200,24h
read-ethers
dhcp-boot=pxelinux.0

enable-tftp
tftp-root=/var/tftp
dhcp-authoritative
no-negcache


```

May I also add that this is running on debian squeeze and the default hostapd.conf (which was the basis for my version) was since significantly changed (likely simplified).

Also, do you know anything beyond "it dosn't work" - are you able to authenticate but the DHCP fails, or what exactly is your problem? Cn you please describe your network setup?

---

### Post by size_XXM on 2010-06-06
Oh, one more thing - if you want to use openDNS, it makes more sense to let dnsmasq do the resolve, advertize itself as the dns server and use openDNS on the router. I do this by prepending openDNS to whatever I get from my ISP. The relevant line from /etc/dhcp3/dhclient.conf:```
prepend domain-name-servers 208.67.220.220;
```I have this line just above the long *request....* line.

---

### Post by lvleph on 2010-06-06
Okay, so I was not able to use bridging, but I was able to get rid of dhcp3-server in favor of dnsmasq. I had to add a startup script for MASQURADING in /etc/init.d/
```

#!/bin/bash
iptables -t nat -A POSTROUTING -s 192.168.1.0/24 -o eth0 -j MASQUERADE

```

Now hopefully this will fix all my problems.

One question though; in your hostapd.conf there seems to be a couple of lines for wireless n, can you explain those lines. My card can do wireless n, but I didn't see any listed settings for it in the man pages. I would like a mixed wireless including wireless n.

---

### Post by lvleph on 2010-06-06
Okay, I have figured out some of what is happening.
The wireless crashes when someone is transferring large files. It was hard to figure this out when I have 3 people doing all sorts of stuff. Now why is it that running the following doesn't fix things
```
sudo /etc/init.d/networking restart
sudo /etc/init.d/hostapd restart 
sudo /etc/init.d/dnsmasq restart
```

---

### Post by size_XXM on 2010-06-06
I believe there's a special init-script that does a "persistent iptables" for Debian systems - look for a package iptables-persistent.
```
# cat /etc/init.d/iptables-persistent
#!/bin/sh
### BEGIN INIT INFO
# Provides:          iptables
# Required-Start:    mountkernfs $local_fs
# Required-Stop:     $local_fs
# Default-Start:     S
# Default-Stop:
# Short-Description: Set up iptables rules
### END INIT INFO

case "$1" in
start)
    if [ -f /etc/iptables/rules ]; then
        iptables-restore </etc/iptables/rules
    fi
    ;;
stop|force-stop|restart|force-reload|status)
    ;;
*)
    echo "Usage: $0 {start|stop|force-stop|restart|force-reload|status}" >&2
    exit 1
    ;;
esac

exit 0
```
I got my NAT instructions from [here](http://www.revsys.com/writings/quicktips/nat.html), but just today I ran into a [differet set of rules](http://switzernet.com/public/081001-alix-umts-debian/#_Toc213553473), somewhat simpler.

Wrt. 802.11n: While I have it set, I'm not getting anything beyond 802.11g - I'm still stuck at ~2,5 MiB/s of goodput. I got instructions from [here](http://linuxwireless.org/en/users/Documentation/hostapd#Wireless_Environment) (see 802.11n Setting summary).

---

### Post by size_XXM on 2010-06-06
Hmm. Does anything relating to hostapd show up in syslog or daemon.log (or what you have set as a logging facility in hostapd.conf)?

---

### Post by lvleph on 2010-06-06
daemon.log doesn't show any errors and same thing for syslog. They both just show various handshaking messages and such.

---

### Post by size_XXM on 2010-06-06
In that case I have no idea. Could be a driver issue (nothing suspicious in kern.log?) I suggest increasing hostapd's log verbosity and/or taking a tcpdump (wireshark capture) on the router or either of the machines transferring files. The fact that restarting  networking and hostapd doesn't bring back connectivity might mean that the machines are not trying to re-authenticate, perhaps? What do you need to do to re-establish connectivity?

---

### Post by lvleph on 2010-06-06
All I need to do is restart the WAP machine. Once it restarts then all wireless computers connect automatically.

---

