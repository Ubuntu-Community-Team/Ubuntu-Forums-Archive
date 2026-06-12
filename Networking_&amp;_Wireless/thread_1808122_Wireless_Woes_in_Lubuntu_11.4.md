---
title: "Wireless Woes in Lubuntu 11.4"
date: 2011-07-19
forum: Networking &amp; Wireless
---

### Post by Roger-H on 2011-07-19
First off, thank you in advance for any assistance the community can provide.

My hardware, a Thinkpad R31, specs are here:

[http://www.thinkwiki.org/wiki/Category:R31](http://www.thinkwiki.org/wiki/Category:R31)

This is my wireless card:

[http://www.thinkwiki.org/wiki/IBM_High_Rate_Wireless_LAN_Mini-PCI_Adapter_with_Modem](http://www.thinkwiki.org/wiki/IBM_High_Rate_Wireless_LAN_Mini-PCI_Adapter_with_Modem)

I installed Lubuntu 11.04 today using the Minimal Install CD and these instructions, connecting my Thinkpad directly to the router via wired ethernet port:

[https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall](https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall)

And lastly, there's me, someone who's been playing around with computers since the days of DOS 3.1 (so I'm not afraid of using command prompts), but I've only been using Linux (one install of Ubuntu 10.4 on another machine) for a couple of months. I like Ubuntu and wanted to resurrect this old Thinkpad using Lubuntu.

According to the install instructions, there were known problems with the NetworkManager after an install like mine, involving unmanaged wired/wireless connections:

[http://wiki.debian.org/NetworkManager](http://wiki.debian.org/NetworkManager)

Sure enough, my wired connection was not appearing in Network Manager (even though it worked), and it was showing the list of wireless networks in the area (including mine) but it could not connect to any of them. The dialog box would take the password, try to connect, and then reappear, asking for the password again.

Following the instructions, now my /etc/networks/interfaces looks like this:

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
# auto eth0
# iface eth0 inet dhcp
```

And my /etc/NetworkManager/NetworkManager.conf looks like this:

```
# This file is installed into /etc/NetworkManager, and is loaded by 
# NetworkManager by default.  To override, specify: '--config file' 
# during NM startup.  This can be done by appending to DAEMON_OPTS in 
# the file:
#
# /etc/default/NetworkManager
#

[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=false
```

These also match the files on my other machine (my successful Ubuntu 10.4 installation that uses my wireless network without problems).

So, now my Thinkpad boots and voila, my wired connection (eth0) appears in the Network Manager. Same as before, the wireless connections in the area are appearing in Network Manager. Just to be thorough, I removed all existing wireless connection profiles before trying to connect to my own password-protected router again. Same thing, the dialog box takes the password, tries to connect, fails, and then prompts me for a password again.

How far away am I from the goal posts? Feet or miles? Please let me know what you think, thanks!

---

### Post by Roger-H on 2011-07-21
One thing I realized I left out: my own wireless network is password protected. My Ubuntu install on another machine (the one that has Ubuntu 10.4 and NetworkManager 0.8 and the wireless is working fine) says on the Wireless Security tab that my network is "WPA & WPA2 Personal." This is not one of the options that I can select on the Lubuntu machine.

I just tried connecting the Lubuntu machine to an unsecured network and it works just fine. This is frustrating. Is the NetworkManager that ships with Lubuntu just a dud or could it be something else?

---

### Post by SteveDee on 2011-07-21
> **Roger-H said:**
> ...
I just tried connecting the Lubuntu machine to an unsecured network and it works just fine. This is frustrating....

If you installed using the Minimal Install and you can connect to unsecured access points, you probably don't have wpasupplicant installed and/or configured.

I had a play with minimal install about 18months ago, and here are my notes:-
> 
...installed wireless-tools (for iwconfig & iwlist)

~$ sudo iwlist scanning    identifies my wifi with correct MAC, channel/freq, sig level & so on.

iwconfig    shows "ESSID: {correct name}" ...but "Access point: Not associated" {should show LAN MAC}

The "Specify an ESSID" dialog includes a key entry but not a security type selector (e.g. WEP, WPA)
The wpasupplicant package is installed....is this a dead end?

Installed lxnm    {removed network-manager & netapplet}

Still see "Access point: Not associated" when using iwlist

Try to create & use a wpasupplicant configuration file:-
    * Create new file: /etc/wpa_supplicant.conf
    * get passkey in hex using: wpa_passphrase "mySSID" "myPassPhrase"
    * Paste output into /etc/wpa_supplicant.conf

Sample output from wpa_supplicant:-
network={
	ssid="myEESID"
	#psk="mindYourOwnBusiness"
	psk=58afbf78d389a37c1fe204a2e3792162753587b3ffbdfcbe11c81fdf19be5237
}

Edit /etc/network/interfaces to include:-
auto wlan0
iface wlan0 inet dhcp
     wpa-driver wext
     wpa-conf /etc/wpa_supplicant.conf
...and edit out existing ESSID and passPhrase entries

Reboot...
...It works!

...sorry I'm short on time at the moment so have not edited my notes...may return later.

See also: [http://undiff.com/2008/08/wireless-with-wpa_supplicant-easier-then-you-think/](http://undiff.com/2008/08/wireless-with-wpa_supplicant-easier-then-you-think/)

---

### Post by Roger-H on 2011-07-24
Thanks for the help. wpa_supplicant was installed already, I tried the configuration instructions on that web page, unfortunately it didn't work. I'm sort of giving up at this point. The fact that it can connect to unsecured wireless networks is good enough.

---

### Post by cavalier911 on 2011-07-25
The link you provided showing your wireless adapter indicates it uses the orinoco_pci driver module.

From [http://linuxwireless.org/en/users/Drivers/orinoco](http://linuxwireless.org/en/users/Drivers/orinoco) 

WPA support is only available for Agere based cards, and requires a firmware download on startup. This support was introduced in 2.6.28.

not supported
WPA2
WPA-PSK (CCMP)

---

### Post by northd_tech on 2011-08-27
Does anyone who has more experience than I with lubuntu know why Synaptic Package Mgr. required me to remove **lubuntu-desktop**?  I needed to remove [Gnome] Network Manager (and applet) to get my wireless connection to quit throwing "Bad Password" errors when using Wicd.  See post #7 here:

[http://ubuntuforums.org/showthread.php?t=1675398](http://ubuntuforums.org/showthread.php?t=1675398)

I remember reading about a lubuntu-specific "lxnm" or something similar (but didn't take notes unfortunately) and this very old one was the only thread I found in a search regarding lubuntu and network manager(s):

[http://ubuntuforums.org/showthread.php?t=1273295](http://ubuntuforums.org/showthread.php?t=1273295)

Also, I'm running Lucid Lynx 10.04.3 LTS 64-bit (not lubuntu *per se*) under Ultimate Edition 2.7 (hacked up through 2.9, give-or-take) on a dual-core AMD64 laptop, but I'd like to be able to run a lighter, faster environment if possible.

---

### Post by praseodym on 2011-08-27
Try first to deactivate the NM in autostart. Restart Wicd:

```
sudo service network-manager stop
sudo service wicd restart
ps aux | grep Network #control
```

---

### Post by northd_tech on 2011-08-27
> **praseodym said:**
> Try first to deactivate the NM in autostart. Restart Wicd:

```
sudo service network-manager stop
sudo service wicd restart
ps aux | grep Network #control
```

As I linked at that post #7 of mine above, I already 'blasted' network-manager completely off my Ubuntu partition with a vengeance:

> **sudo service network-manager stop**
[sudo] password for JohnDoe: 
network-manager: unrecognized service
Wicd is already working SPECTACULARLY:
> eth1      Link encap:Ethernet  HWaddr 00:21:00:13:24:12  
          inet addr:192.168.0.5  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: ac85::221:fa:fe81:2412/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:421361 errors:0 dropped:0 overruns:0 frame:1897085
          TX packets:261223 errors:39 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:570469681 **(570.4 MB)  TX bytes:26887848 (26.8 MB)**
          Interrupt:19 
Not a single dropped connection or 'hiccough' since I restarted my system about **uptime**: 
> up 12:12,  2 users,  load average: 0.40, 0.69, 0.68
I'm just looking for a less bloated, faster Ubuntu desktop to run than Gnome on occasion (preferably with Wicd wireless manager, as I VASTLY prefer it to [Gnome]NM anyway).

> **ps aux | grep Network #control**
JohnDoe     18012  0.0  0.0   8704   900 pts/0    S+   04:26   0:00 grep Network


---

### Post by northd_tech on 2011-08-27
> **northd_tech said:**
> 
Wicd is already working SPECTACULARLY:
Not a single dropped connection or 'hiccough' since I restarted my system about **uptime**: 

Wicd is still rock-solid- not a single problem in 23+ hours:

> **ifconfig -a**
eth1      Link encap:Ethernet  HWaddr MAC address for WiFi
          inet addr:192.168.0.5  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: IPv6address Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:581931 errors:0 dropped:0 overruns:0 frame:3635056
          TX packets:367696 errors:70 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:772547130 (772.5 MB)  TX bytes:37867115 (37.8 MB)
          Interrupt:19

**uptime**
 15:44:24 up 23:33,  2 users,  load average: 0.86, 0.71, 0.67
 

---

### Post by praseodym on 2011-08-27
> ```
TX packets:367696 errors:[COLOR="Red"]70[/COLOR] dropped:0 overruns:0 carrier:0
```

You may check your mtu-value of your ISP. If someone uses the NM it should be chosen as a numer instead of "automatic". Or via terminal

```
sudo ifconfig [COLOR="Red"]eth1[/COLOR] mtu [COLOR="Red"]number[/COLOR]
sudo /etc/init.d/networking restart
```
Check if eth1 is the interface you want to change. Example:

```
sudo ifconfig eth1 mtu 1492
```

---

### Post by northd_tech on 2011-08-27
> **northd_tech said:**
> **ifconfig -a**
eth1      Link encap:Ethernet  HWaddr MAC address for WiFi
          inet addr:192.168.0.5  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: IPv6address Scope:Link
          UP BROADCAST RUNNING MULTICAST  **MTU:1500**  Metric:1
          RX packets:581931 errors:0 dropped:0 overruns:0 frame:3635056
          TX packets:367696 errors:70 dropped:0 overruns:0 carrier:0

It looks like my MTU is set at 1500 (bytes?- or whatever unit that is measured in).  I'm not sure what value my ISP would work best at (it's a 'mid-level' cable modem connection in the US about 2-3 miles from one of the 8 nodes on the original DARPAnet "internet backbone," so it should be a relatively speedy connection).

According to this site, I've got a 18.34 Mbps download and 0.80 Mbps upload rate across the continent to NYC, NY (which is pretty good for a residential connection, I believe):

[http://speakeasy.net/speedtest/](http://speakeasy.net/speedtest/)

Even at 70 'collisions' of 367696 packets, that is only ~0,19% 'error rate' for the transmitted packets, so I can live with < 1/5 percent error (and we have a LOT of wireless and ethernet traffic/devices sharing this location and ISP).

Do you know of a way to test my optimal MTU for this ISP?  I don't think their website or customer service will be very helpful from my past experience- I usually need to fix everything myself.

EDIT:  Of course, Wicd reports my wireless connection speed as 2 Mbps (but I seem to recall reading that Wicd and/or NM don't often get that correct).

---

### Post by praseodym on 2011-08-27
You may ask your ISP or google the value. Normally its 1500 or 1492 with DSL:

```
sudo ifconfig eth1 mtu 1492
sudo /etc/init.d/networking restart
ifconfig eth1
```
If it doesnt work, type the command again with 1500 to resume your status. Just ping some website and look if you have package loss:

```
ping -c 4 www.google.com
```

---

