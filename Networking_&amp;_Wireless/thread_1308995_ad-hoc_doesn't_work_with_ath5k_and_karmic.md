---
title: "ad-hoc doesn't work with ath5k and karmic"
date: 2009-11-01
forum: Networking &amp; Wireless
---

### Post by pdwerryhouse on 2009-11-01
Hi all,

The Atheros AR5001 wireless card (using ath5k) works perfectly on my netbook using a Managed wireless network, but simply refuses to work when in ad-hoc mode, under Ubuntu karmic.

There aren't any odd error messages in the syslog or dmesg - it just seems that the card/driver doesn't see the other laptop that I'm trying to connect to. I've pinpointed the issue to this netbook, because the remote laptop is working fine when talking to other devices using ad-hoc.

Anyone had any success with it?

---

### Post by araidian on 2010-04-11
I have this exact problem i have basically narrowed it down to the driver refusing to go into ad-hoc mode am wondering if there is a way to force it when you load the driver.  it's an extremely annoying problem but i think that it will work if you can get it into that mode, i have also tried using wicd but that doesnt work either, but i could use the iwconfig wlan0 mode Ad-Hoc command to force it but it wont create the network though the gui .. and when i returned to network-manager i can create the network interface but cant force it to go into ad-hoc mode and i get an error like "SET failed on device wlan0 ; device or resource busy" and so on.  If i try creating a network using network-manager  it crashes and the network manager disappears from the system tray.

I have come to the conclusion that wifi under ubuntu or linux for that matter is crap :( this is a very trivial thing to do "normally", the card i'm using is a dlink with a atheros AR5001X+ chipset ubuntu has given it the ath5k driver and i can connect it to my apple airport, however i can not create a network with it .. and i have been working on this on and off for about 2 days :( and on a mac it would be click click done.

---

### Post by araidian on 2010-04-11
ok update i managed to get it into ad-hoc mode and it's still not going .. just sits there connecting and disconnecting. i cant seem to get other devices to connect to it even with no encryption.

---

### Post by selak on 2010-04-27
Hello,

I solved this X-Files issue by using a bridge...

This is my "/etc/network/interfaces" :

```

auto wlan0
iface wlan0 inet6 static
address $YOURIPADDRESS
netmask 64
pre-up ifconfig wlan0 down
pre-up ifconfig wlan0 hw ether $YOURMACADDRESS
pre-up iwconfig wlan0 mode ad-hoc essid $ESSIDchannel $CH

auto unicast
iface unicast inet6 static 
address $YOURIPADDRESS
netmask 64
pre-up brctl addbr unicast
pre-up brctl addif unicast wlan0
pre-down ifconfig unicast down
post-down brctl delif unicast wlan0
post-down brctl delbr unicast
```I will try with the new UNR Lucid Lynx and the kernel 2.6.32.

After that, you can force the node to join the ad-hoc network with 

```
iwconfig wlanX ap XX:XX:XX:XX:XX:XX
```Don't forget to change the value beginning with $...

And give me feed back !

---

### Post by werepacman on 2010-05-22
p, li { white-space: pre-wrap; }  [FONT=DejaVu Sans]*Hi. I read solution by Selak.*[/FONT][FONT=DejaVu Sans][I] 
[/I][/FONT]
[FONT=DejaVu Sans][I]It works for me partly.
[/I][/FONT]
[FONT=DejaVu Sans][I]It seems Linux driver for AR5001 does`n support ad-hoc mode.
But with this advice my AR5001 card can finally be detected by other devices. I can connect to it with my girlfriend`s net-book with XP, but I still can`t share internet. 

I haven`t shared wifi before.[/I][/FONT]
 [FONT=DejaVu Sans]*May be I`ve missed something. *[/FONT]
[FONT=DejaVu Sans]*Could someone revise and correct my configuration?*[/FONT]
 [FONT=DejaVu Sans]**[/FONT]
 [FONT=DejaVu Sans][I]
[/I][/FONT]
[FONT=DejaVu Sans]*Here it is:*[/FONT]
 [FONT=DejaVu Sans]**[/FONT]
 [FONT=DejaVu Sans]*interfaces:*[/FONT]
 [FONT=DejaVu Sans]*>  	*[/FONT]
 [FONT=DejaVu Sans]*auto lo*[/FONT]
 [FONT=DejaVu Sans]*iface lo inet loopback*[/FONT]
 [FONT=DejaVu Sans]**[/FONT]
 [FONT=DejaVu Sans]*auto wlan0*[/FONT]
 [FONT=DejaVu Sans]*iface wlan0 inet6 static*[/FONT]
 [FONT=DejaVu Sans]*address 192.168.2.3*[/FONT]
 [FONT=DejaVu Sans]*netmask 255.255.255.0*[/FONT]
 [FONT=DejaVu Sans]*pre-up ifconfig wlan0 down*[/FONT]
 [FONT=DejaVu Sans]*pre-up ifconfig wlan0 hw ether 00:15:af:21:e1:46*[/FONT]
 [FONT=DejaVu Sans]*pre-up iwconfig wlan0 mode ad-hoc essid YYYYY  channel 6*[/FONT]
 [FONT=DejaVu Sans]**[/FONT]
 [FONT=DejaVu Sans]*auto unicast*[/FONT]
 [FONT=DejaVu Sans]*iface unicast inet6 static*[/FONT]
 [FONT=DejaVu Sans]*address 192.168.2.5*[/FONT]
 [FONT=DejaVu Sans]*netmask 255.255.255.0*[/FONT]
 [FONT=DejaVu Sans]*pre-up brctl addbr unicast*[/FONT]
 [FONT=DejaVu Sans]*pre-up brctl addif unicast wlan0*[/FONT]
 [FONT=DejaVu Sans]*pre-down ifconfig unicast down*[/FONT]
 [FONT=DejaVu Sans]*post-down brctl delif unicast wlan0*[/FONT]
 [FONT=DejaVu Sans]*post-down brctl delbr unicast*[/FONT]
 [FONT=DejaVu Sans]**[/FONT]
 [FONT=DejaVu Sans]*auto eth0*[/FONT]
 [FONT=DejaVu Sans]*iface eth0 inet dhcp*[/FONT]
 [FONT=DejaVu Sans]**[/FONT]
 [FONT=DejaVu Sans]*post-up /etc/network/script.sh*[/FONT]
 [FONT=DejaVu Sans]**[/FONT]
 [FONT=DejaVu Sans]*# script.sh contains:*[/FONT]
 [FONT=DejaVu Sans]*# iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE*[/FONT]
 [FONT=DejaVu Sans]*# iptables -A FORWARD -i wlan0 -j ACCEPT*[/FONT]
 [FONT=DejaVu Sans]**[/FONT]

[FONT=DejaVu Sans]**[/FONT]
[FONT=DejaVu Sans][I]
[/I][/FONT]
 [FONT=DejaVu Sans]**[/FONT]
 [FONT=DejaVu Sans]*$*[/FONT][FONT=DejaVu Sans]*sudo *[/FONT][FONT=DejaVu Sans]*iwconfig wlanX ap 00:15:af:21:e1:46*[/FONT]
 [FONT=DejaVu Sans]*192.168.2.3/255.255.255.0: Unknown host*[/FONT]
 [FONT=DejaVu Sans]*Failed to bring up wlan0*[/FONT]
[FONT=DejaVu Sans][I]
[/I][/FONT]
 [FONT=DejaVu Sans]**[/FONT]
 [FONT=DejaVu Sans]*- Why?*[/FONT]
 [FONT=DejaVu Sans]**[/FONT]
 [FONT=DejaVu Sans]**[/FONT]
 [FONT=DejaVu Sans]**[/FONT]
 [FONT=DejaVu Sans][I]
[/I][/FONT]
[FONT=DejaVu Sans][I]
[/I][/FONT]
[FONT=DejaVu Sans]***$*[/FONT][FONT=DejaVu Sans]*sudo *[/FONT][FONT=DejaVu Sans]*iwconfig:***[/FONT]
 [FONT=DejaVu Sans]*> wlan0     IEEE 802.11bg  ESSID:"YYYYY"  *[/FONT]
 [FONT=DejaVu Sans]*	    Mode:Ad-Hoc  Frequency:2.437 GHz  Cell: Not-Associated   *[/FONT]
 [FONT=DejaVu Sans]*	    Tx-Power=20 dBm   *[/FONT]
 [FONT=DejaVu Sans]*	    Retry  long limit:7   RTS thr:off   Fragment thr:off*[/FONT]
 [FONT=DejaVu Sans]*	    Power Management:off*[/FONT]
 [FONT=DejaVu Sans]* 	*[/FONT]
 [FONT=DejaVu Sans]**[/FONT]
 [FONT=DejaVu Sans]**[/FONT]
 [FONT=DejaVu Sans][I]
[/I][/FONT]
[FONT=DejaVu Sans][I]
[/I][/FONT]
[FONT=DejaVu Sans]***$sudo ifconfig***[/FONT]
 [FONT=DejaVu Sans]*> *[/FONT]
 [FONT=DejaVu Sans]*eth0	Link encap:Ethernet  HWaddr 00:1e:8c:c3:7a:42  *[/FONT]
 [FONT=DejaVu Sans]*	    inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0*[/FONT]
 [FONT=DejaVu Sans]*	    inet6 addr: fe80::21e:8cff:fec3:7a42/64 Scope:Link*[/FONT]
 [FONT=DejaVu Sans]*	    UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1*[/FONT]
 [FONT=DejaVu Sans]*	    RX packets:65734 errors:0 dropped:0 overruns:0 frame:0*[/FONT]
 [FONT=DejaVu Sans]*	    TX packets:76862 errors:0 dropped:0 overruns:0 carrier:0*[/FONT]
 [FONT=DejaVu Sans]*	    collisions:0 txqueuelen:1000 *[/FONT]
 [FONT=DejaVu Sans]*	    RX bytes:13397356 (13.3 MB)  TX bytes:10096021 (10.0 MB)*[/FONT]
 [FONT=DejaVu Sans]*	    Interrupt:18 *[/FONT]
 [FONT=DejaVu Sans]**[/FONT]
 [FONT=DejaVu Sans]*eth1	Link encap:Ethernet  HWaddr 00:80:48:b5:0b:af  *[/FONT]
 [FONT=DejaVu Sans]*	    inet6 addr: fe80::280:48ff:feb5:baf/64 Scope:Link*[/FONT]
 [FONT=DejaVu Sans]*	    UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1*[/FONT]
 [FONT=DejaVu Sans]*	    RX packets:5 errors:0 dropped:0 overruns:0 frame:0*[/FONT]
 [FONT=DejaVu Sans]*	    TX packets:14 errors:0 dropped:0 overruns:0 carrier:0*[/FONT]
 [FONT=DejaVu Sans]*	    collisions:0 txqueuelen:1000 *[/FONT]
 [FONT=DejaVu Sans]*	    RX bytes:1263 (1.2 KB)  TX bytes:3204 (3.2 KB)*[/FONT]
 [FONT=DejaVu Sans]*	    Interrupt:21 Base address:0xe800 *[/FONT]
 [FONT=DejaVu Sans]**[/FONT]
 [FONT=DejaVu Sans]*lo	  Link encap:Local Loopback  *[/FONT]
 [FONT=DejaVu Sans]*	    inet addr:127.0.0.1  Mask:255.0.0.0*[/FONT]
 [FONT=DejaVu Sans]*	    inet6 addr: ::1/128 Scope:Host*[/FONT]
 [FONT=DejaVu Sans]*	    UP LOOPBACK RUNNING  MTU:16436  Metric:1*[/FONT]
 [FONT=DejaVu Sans]*	    RX packets:160 errors:0 dropped:0 overruns:0 frame:0*[/FONT]
 [FONT=DejaVu Sans]*	    TX packets:160 errors:0 dropped:0 overruns:0 carrier:0*[/FONT]
 [FONT=DejaVu Sans]*	    collisions:0 txqueuelen:0 *[/FONT]
 [FONT=DejaVu Sans]*	    RX bytes:18734 (18.7 KB)  TX bytes:18734 (18.7 KB)*[/FONT]
 [FONT=DejaVu Sans]**[/FONT]
 [FONT=DejaVu Sans]*usb0	Link encap:Ethernet  HWaddr ce:bb:e1:09:60:e5  *[/FONT]
 [FONT=DejaVu Sans]*	    inet6 addr: fe80::ccbb:e1ff:fe09:60e5/64 Scope:Link*[/FONT]
 [FONT=DejaVu Sans]*	    UP BROADCAST MULTICAST  MTU:1500  Metric:1*[/FONT]
 [FONT=DejaVu Sans]*	    RX packets:0 errors:0 dropped:0 overruns:0 frame:0*[/FONT]
 [FONT=DejaVu Sans]*	    TX packets:1 errors:0 dropped:0 overruns:0 carrier:0*[/FONT]
 [FONT=DejaVu Sans]*	    collisions:0 txqueuelen:1000 *[/FONT]
 [FONT=DejaVu Sans]*	    RX bytes:0 (0.0 B)  TX bytes:90 (90.0 B)*[/FONT]
 [FONT=DejaVu Sans]**[/FONT]

---

### Post by selak on 2010-06-15
> **werepacman said:**
> 
 
 [FONT=DejaVu Sans]*- Why?*[/FONT]
 
 

Replace "inet6" by "inet" in /etc/network/interfaces.

I'm using IPv6 but you configured IPv4 address for your interface.

Best regards !

---

### Post by werepacman on 2010-07-12
Grate thanks [selak]("http://ubuntuforums.org/member.php?u=1060979")! It works!

---

