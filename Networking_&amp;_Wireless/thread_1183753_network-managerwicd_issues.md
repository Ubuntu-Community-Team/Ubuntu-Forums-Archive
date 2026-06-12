---
title: "network-manager/wicd issues"
date: 2009-06-10
forum: Networking &amp; Wireless
---

### Post by moore.bryan on 2009-06-10
multiple issues/questions, so here goes:
[LIST][*]fresh install of xubuntu 9.04[*]running 2.6.28-11-generic kernel[*]using ath5k driver[*]network-manager can see my networks and connect to them[*]wicd can see my networks, but cannot connect to them
[/LIST]
now, here's the "rub:" network-manager "manages" my wireless to the point of 11mb/s on a network running a t3 backbone. wicd, although it can see my wireless networks, cannot connect to any of them. in my previous install of jaunty, wicd got me between 85 and 90 mb/s on the same connection. my guess is it's either the ath5k driver/module or network-manager. perhaps someone more trained in networking can instruct me? i just want my network to be used to the "fullest" extent.

thanks!

---

### Post by kerry_s on 2009-06-10
post the output of> **sudo iwconfig**

try killing the network managers and doing it from command line, to check if its actually them.
example:
[B]sudo iwconfig wlan0 essid "your-name" rate 11M
sudo ifconfig wlan0 up
sudo dhclient wlan0
[/B]

---

### Post by moore.bryan on 2009-06-10
do things become significantly more complicated if i tell you my work wep is passphrased?

after a little research, it seems this is, somewhat, a known issue with ath5k; however, no one seems to be trying to anything about it because of the push for ath9k.

---

### Post by kerry_s on 2009-06-10
> **moore.bryan said:**
> do things become significantly more complicated if i tell you my work wep is passphrased?

after a little research, it seems this is, somewhat, a known issue with ath5k; however, no one seems to be trying to anything about it because of the push for ath9k.

okay add key to the command:
**sudo iwconfig wlan0 essid "your-name" rate 11M key xxxxxxxx**

i'm one of those that never liked the overhead of network managers, i prefer to script mine. when i need mobile i usually use "network-config" as it provides a nice gui for setting up lots of places.

---

### Post by moore.bryan on 2009-06-10
> **kerry_s said:**
> post the output of> **sudo iwconfig**
```
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"S1MM0NSD0LF1N"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1D:70:03:56:E1   
          Bit Rate=11 Mb/s   Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Encryption key:1944-6514-6378-950A-0B0C-0D0E-0F   Security mode:open
          Power Management:off
          Link Quality=65/100  Signal level:-53 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.
```
then, i killed nm by uninstalling it. and put in:
> ```
[B]sudo iwconfig wlan0 essid "your-name" rate 11M key xxxxxxxx
sudo ifconfig wlan0 up
sudo dhclient wlan0
[/B]
```
and got this:
```

Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:19:7e:25:8d:31
Sending on   LPF/wlan0/00:19:7e:25:8d:31
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPOFFER of 172.31.8.33 from 1.1.1.1
DHCPREQUEST of 172.31.8.33 on wlan0 to 255.255.255.255 port 67
DHCPACK of 172.31.8.33 from 1.1.1.1
bound to 172.31.8.33 -- renewal in 299630 seconds.

```
i can ping with heavy packet loss, greater than 70%, but no web browsing.
> i'm one of those that never liked the overhead of network managers, i prefer to script mine. when i need mobile i usually use "network-config" as it provides a nice gui for setting up lots of places.
i'd rather use nothing, as well, but it seems i'm always in a "weird" wireless situation where i need them. alternatives are greatly appreciated!

---

### Post by moore.bryan on 2009-06-10
so i've completely uninstalled nm and wicd, installed network-config and i'm connected, but still things feel really slow. speedtest.net puts my download speed @ 12.28mb/s, upload @ 6.69mb/s.

---

### Post by kerry_s on 2009-06-10
your signals not great "65/100" but thats decent, there is a bit of noise "Noise level=-95 dBm" thats a bit high, must have a lot of wifi in the area.

thats the right output so your connected.
the routers set up a little weird. 
"1.1.1.1" is kinda strange for the router address
dhcp lease time is about 3 days, a little long.

cause of the weird router setup, i would first try, setting your own dns server: [https://www.opendns.com/start/device/ubuntu](https://www.opendns.com/start/device/ubuntu)
do number 8

man you move fast, in network-config you should be able to set the dns.
under custom dns.

---

### Post by moore.bryan on 2009-06-10
> **kerry_s said:**
> your signals not great "65/100" but thats decent, there is a bit of noise "Noise level=-95 dBm" thats a bit high, must have a lot of wifi in the area.
where did you get this information? i didn't see it in the print-out... there are two wireless routers within 20-feet of my desk, but that shouldn't put my connection to 12mb/s should it?
> the routers set up a little weird. 
"1.1.1.1" is kinda strange for the router address
dhcp lease time is about 3 days, a little long.

what can i say, our it guys aren't the brightest lights.
> 
cause of the weird router setup, i would first try, setting your own dns server:
this was something i was going to do any way, but just didn't get the chance; had to go pick-up wifey at work and leave my "pet project." why would changing the dns servers improve my connection?
> man you move fast,
i guess a little ocd when it comes to solving these things. wireless has always been a pita with ubuntu for me, since the lappie has atheros. i was just hoping the new ath5k wouldn't bug-out for me like it seems to do for so many others. add to that, i can't seem to get anything to work with madwifi now... just frustrating. thanks for your help and i'll post more when i get to work tomorrow.

---

### Post by kerry_s on 2009-06-10
> where did you get this information? i didn't see it in the print-out... there are two wireless routers within 20-feet of my desk, but that shouldn't put my connection to 12mb/s should it?

it's in your "sudo iwconfig"

```
wlan0     IEEE 802.11abg  ESSID:"S1MM0NSD0LF1N"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1D:70:03:56:E1   
          Bit Rate=11 Mb/s   Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Encryption key:1944-6514-6378-950A-0B0C-0D0E-0F   Security mode:open
          Power Management:off
          **Link Quality=65/100  Signal level:-53 dBm  Noise level=-95 dBm**
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

according to this page: [http://linuxwireless.org/en/users/Drivers/ath5k](http://linuxwireless.org/en/users/Drivers/ath5k)
11M is what it runs at & there's problems if you go above 18M

> why would changing the dns servers improve my connection?

the problem could be that the routers dns servers suck, so if it fails to resolve the address it would look like your not getting a connection when in fact it's just a dns issue.

---

### Post by moore.bryan on 2009-06-11
> **kerry_s said:**
> it's in your "sudo iwconfig"
right... i'm an idiot; forgot i posted that!
> according to this page: [http://linuxwireless.org/en/users/Drivers/ath5k](http://linuxwireless.org/en/users/Drivers/ath5k)
11M is what it runs at & there's problems if you go above 18M
interesting... why in the hell would a wireless driver *limit* the download speed?
> the problem could be that the routers dns servers suck, so if it fails to resolve the address it would look like your not getting a connection when in fact it's just a dns issue.
that also makes sense. like i wrote, i'll make the change and post back.

---

### Post by kerry_s on 2009-06-11
> interesting... why in the hell would a wireless driver limit the download speed?

got me, poor design?
i would push it see if you can get more, it says 11M to 18M, so maybe try 15M see how things go, slowly move it up.
it's easy with network-config, where it says rate, put "15M" instead of the default "auto".

---

### Post by moore.bryan on 2009-06-11
> **kerry_s said:**
> got me, poor design?
i would push it see if you can get more, it says 11M to 18M, so maybe try 15M see how things go, slowly move it up.
it's easy with network-config, where it says rate, put "15M" instead of the default "auto".
well, my speedtest still sucks, but i guess it is what it is. i started at 11m and moved-up 2m increments and saw nothing negative; stopped at 18m as per the info. now, to have the networks autoconfig'd at startup, i'm guessing i can just put my info into /etc/network/interfaces? 

another, possibly rhetorical, question: why would anyone use ath5k over madwifi if one has no rate limit and the other's is catastrophically slow?

---

### Post by kerry_s on 2009-06-11
> stopped at 18m as per the info. now, to have the networks autoconfig'd at startup, i'm guessing i can just put my info into /etc/network/interfaces?

don't stop try going beyond, the standard is 54M right?

/etc/network/interfaces:
```
iface wlan0 inet dhcp
wireless-essid XXXXXXXXXXX
wireless-key XXXXXXXX

```

> another, possibly rhetorical, question: why would anyone use ath5k over madwifi if one has no rate limit and the other's is catastrophically slow?

maybe you should switch?

---

### Post by moore.bryan on 2009-06-11
> **kerry_s said:**
> don't stop try going beyond, the standard is 54M right?
i will begin my diligent testing tomorrow morning and report to the community-at-large, or just you and me. ;-)
> 
/etc/network/interfaces:
```
iface wlan0 inet dhcp
wireless-essid XXXXXXXXXXX
wireless-key XXXXXXXX

```and what about setting the rate in this file?
> maybe you should switch?that's actually what i originally wanted to do, but no matter what tricks i use that i've learned, i can't get madwifi (the restricted drivers) to connect.

thanks, again, for all your help!

EDIT:

so, i worked some magic and got the original madwifi working; here's a MUCH different iwconfig:
```
ath0      IEEE 802.11g  ESSID:"35moore"  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:14:6C:F8:DE:96   
          Bit Rate:54 Mb/s   Tx-Power:8 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=47/70  Signal level=-48 dBm  Noise level=-95 dBm
          Rx invalid nwid:13165  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

---

### Post by kerry_s on 2009-06-12
> and what about setting the rate in this file?

oops :)

```
iface wlan0 inet dhcp
wireless-essid XXXXXXXXXXX
wireless-key XXXXXXXX
**wireless-rate 54M**
```

> so, i worked some magic and got the original madwifi working; here's a MUCH different iwconfig:

so hows it working?

---

### Post by majamba on 2009-06-12
i had the most success with network-gnome-manager, had problems wicd connecting and kde wireless manager was not working 

apttitude install netwark-manager-gnome

then
change the file something nm-aplet

it is in /etc/xdg/nm-applet
change the line show in add KDE and semicolon

i hope your are familar with unix system after you install

here are sugestions

use the tab help complete some of entries in unix system

sudo nano /etc/xdg/nm    and press tab and see the file

---

### Post by kerry_s on 2009-06-12
> **majamba said:**
> i had the most success with network-gnome-manager, had problems wicd connecting and kde wireless manager was not working 

apttitude install netwark-manager-gnome

then
change the file something nm-aplet

it is in /etc/xdg/nm-applet
change the line show in add KDE and semicolon

i hope your are familar with unix system after you install

here are sugestions

use the tab help complete some of entries in unix system

sudo nano /etc/xdg/nm    and press tab and see the file

it's way faster not to use a network manager at all. you loss the extra bloat & daemons that those require and there's less in the way of your connection.
setting it in /etc/network/interfaces will bring it up, before it reaches the desktop instead of after. works good for your main connections, using network-config works great for other connections.

---

### Post by moore.bryan on 2009-06-12
so, i spoke too soon. i was able to get my *home* network, with wpa2-psk, setup; now, i'm back at work and no dice with ath0. see, ath5k creates wlan0 as the interface and madwifi ath0. now that i'm using the madwifi driver, i can't get it to connect. in fact, it doesn't seem to even put down--or up for that matter--ath0.

*sudo ifconfig ath0:*
```
ath0      Link encap:Ethernet  HWaddr 00:19:7e:25:8d:31  
          inet6 addr: fe80::219:7eff:fe25:8d31/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```
*sudo iwconfig ath0:*
```
ath0      IEEE 802.11g  ESSID:"S1MM0NSD0LF1N"  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1D:70:03:56:E1   
          Bit Rate:11 Mb/s   Tx-Power:17 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:1944-6514-6378-950A-0B0C-0D0E-0F   Security mode:restricted
          Power Management:off
          Link Quality=44/70  Signal level=-52 dBm  Noise level=-96 dBm
          Rx invalid nwid:43154  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```
*network-config output:*
```
$ echo "nameserver 208.67.222.222" > /etc/resolv.conf

$ echo "nameserver 208.67.220.220" >> /etc/resolv.conf

Configuring device ath0 :

$ iwconfig ath0 mode managed

$ iwconfig ath0 essid "S1MM0NSD0LF1N"

$ iwconfig ath0 rate auto

$ iwconfig ath0 key XXX...

$ ifconfig ath0 up

DHCP may take a while, please wait...
$ dhclient ath0
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.

--- 192.168.1.1 ping statistics ---
1 packets transmitted, 0 received, +1 errors, 100% packet loss, time 0ms

cp/

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:19:7e:25:8d:31
Sending on   LPF/ath0/00:19:7e:25:8d:31
Sending on   Socket/fallback
DHCPREQUEST of 192.168.1.2 on ath0 to 255.255.255.255 port 67
DHCPREQUEST of 192.168.1.2 on ath0 to 255.255.255.255 port 67
DHCPREQUEST of 192.168.1.2 on ath0 to 255.255.255.255 port 67
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 4
No DHCPOFFERS received.
Trying recorded lease 192.168.1.2
No working leases in persistent database - sleeping.

Configuring device eth0 :

$ ifconfig eth0 down
```
this is becoming quite ridiculous. this all worked *flawlessly* on my old crappy install... this is a *fresh* install and i shouldn't be having any of these issues!

---

### Post by moore.bryan on 2009-06-12
UPDATE

now, even switching back to ath5k (wlan0) gives no connection! wtf?

---

### Post by kerry_s on 2009-06-12
> **moore.bryan said:**
> UPDATE

now, even switching back to ath5k (wlan0) gives no connection! wtf?

:lolflag: the more you mess with it the worst its getting.

---

### Post by moore.bryan on 2009-06-12
yeah, thanks! ;-)

i'm really irritated about this because it shouldn't be this complicated, particularly considering my old install of xubuntu jaunty worked just fine and this one can't seem to get its act together.

---

### Post by moore.bryan on 2009-06-12
okay, this is stupid. using network-manager, i can connect with BOTH ath5k and madwifi drivers; BOTH also report my speed at 12mb/s. in windows, i get 54mb/s, and on my old install 54mb/s.

where can i even BEGIN to debug this mess!?

---

