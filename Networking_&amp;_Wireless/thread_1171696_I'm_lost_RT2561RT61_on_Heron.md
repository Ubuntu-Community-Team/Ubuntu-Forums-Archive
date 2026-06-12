---
title: "I'm lost: RT2561/RT61 on Heron"
date: 2009-05-27
forum: Networking &amp; Wireless
---

### Post by mcvos on 2009-05-27
What I really want to know is: why doesn't this just work out of the box? I thought Ubuntu was supposed to be dead easy to get working, but Ubuntu is the OS where I consistently have trouble getting wifi working.

I'm not a sysadmin, I'm just a user and programmer, and I just want this to work.

Anyway, I've got a Belkin wifi card that apparently has a RT2561/RT61 chipset. I don't know if that means I need to follow the instructions for the [RT2500]("https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500") or the [RT61]("https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT61?action=show&redirect=Rt61WirelessCardsHowTo"). I've been trying to follow the RT2500 instructions so far, including rather detailed instructions that seem to [replace a driver with a freshly compiled one]("http://ubuntuforums.org/showpost.php?p=3595458&postcount=6"), but that process fails somewhere along the line (probably because I have heron rather than gibbon).

My main problem is: most instructions point to stuff that doesn't exist, or works different than how the instructions claim it should. System->Preferences->Networking doesn't exist, System->Administration->Network doesn't show /wsomethingorother0 or similar paths at all. (Also really odd is that I have to enter ssid manually, rather than that it detects which networks are present. Doesn't exactly inspire confidence that the wifi is actually working.)

And I do find lots and lots and lots of instructions that seem vaguely related to my problem, but I'm not sure which are relevant for me. Can I follow instructions for RT2500 on gutsy gibbon, or do I need heron-specific instructions? Do I need RT2500, RT61, RT2561 or something completely different?

There's just too much, and I have no idea what it all means.

Isn't it possible to just write a tool for Ubuntu that figures this stuff out and fixes it for you? And could someone please make sure that tool runs automatically on installation?

Anyway, some technical details of my machine:
```

04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
05:01.0 Network controller: RaLink RT2561/RT61 802.11g PCI

$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1d:7d:af:27:9d  
          inet addr:192.168.178.21  Bcast:192.168.178.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:7dff:feaf:279d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:28072 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18606 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:34040174 (32.4 MB)  TX bytes:1611067 (1.5 MB)
          Interrupt:251 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1662 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1662 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:83100 (81.1 KB)  TX bytes:83100 (81.1 KB)

wlan0     Link encap:Ethernet  HWaddr 00:11:50:de:7a:db  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-11-50-DE-7A-DB-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
lsmod includes stuff like:
```

rt61pci                27648  0 
rt2x00pci              12800  1 rt61pci
rt2x00lib              25344  2 rt61pci,rt2x00pci
rfkill                 10128  1 rt2x00lib
input_polldev           6928  1 rt2x00lib
crc_itu_t               3584  1 rt2x00lib
mac80211              192532  3 rt61pci,rt2x00pci,rt2x00lib

```
```

sudo lshv -C network
[code]
$ sudo lshw -C network
[sudo] password for mcv: 
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 01
       serial: 00:1d:7d:af:27:9d
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=full ip=192.168.178.21 latency=0 link=yes module=r8169 multicast=yes port=twisted pair speed=100MB/s
  *-network
       description: Wireless interface
       product: RT2561/RT61 802.11g PCI
       vendor: RaLink
       physical id: 1
       bus info: pci@0000:05:01.0
       logical name: wmaster0
       version: 00
       serial: 00:11:50:de:7a:db
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rt61pci latency=32 module=rt61pci multicast=yes wireless=IEEE 802.11g

```
~$ iwlist scan
```

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

```
Ubuntu 9.04
2.6.24-16-generic x86_64

---

### Post by mcvos on 2009-05-27
I'm getting the feeling that maybe my card counts as a RT61 card, so I tried following [those instructions]("https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT61?action=show&redirect=Rt61WirelessCardsHowTo").

Those instructions include downloading the driver source directly from ralink and compiling it. First I tried what looked suitable and recent:
```

http://www.ralinktech.com.tw/data/drivers/2009_0123_RT61_Linux_STA_v1.1.2.3.tar.bz2

```

Compiling failed. So I just got exactly what the docs told me to:
```

http://www.ralinktech.com.tw/data/RT61_Linux_STA_Drv1.1.0.0.tar.gz

```

Again, compilation failed, with exactly the same error:

```

make -C /lib/modules/2.6.24-16-generic/build SUBDIRS=/home/mcv/RT61_Linux_STA_Drv1.1.0.0/Module modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
scripts/Makefile.build:46: *** CFLAGS was changed in "/home/mcv/RT61_Linux_STA_Drv1.1.0.0/Module/Makefile". Fix it to use EXTRA_CFLAGS.  Stop.
make[1]: *** [_module_/home/mcv/RT61_Linux_STA_Drv1.1.0.0/Module] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make: *** [all] Error 2

```

Now the wifiDoc says it's originally written for Edgy, it has some notes about Gutsy, contains extra instructions for Feisty, and says it's not necessary for Intrepid, but Hardy (the LTS release!) isn't mentioned anywhere. Am I out of luck? Is there no wifi support for hardy heron?

---

### Post by chili555 on 2009-05-27
> wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBmIt looks like it's working perfectly to me. It just isn't associated with an access point yet. Network Manager, which is installed by default, is designed to disallow a wireless connection if you have a wired ethernet connection, which you do:> eth0      Link encap:Ethernet  HWaddr 00:1d:7d:af:27:9d  
          inet addr:192.168.178.21  Bcast:192.168.178.255  Mask:255.255.255.0If you detach the wire and reboot, do you see your wireless network in the Network Manager icon? Can you connect?> ~$ iwlist scanI would like to get my boot on the seat of the pants of whoever put this is a tutorial! This is from *man iwlist*:> Triggering  scanning  is  a privileged operation (root only) and normal users can only read left-over scan results.Do you get a better result with:```
**sudo** iwlist wlan0 scan
```

---

### Post by mcvos on 2009-05-27
Also, various docs seem to say `lsmod | grep rt61` should say "rt61 245128 1". For me, it says something entirely different:
```

rt61pci                27648  0 
rt2x00pci              12800  2 rt2500pci,rt61pci
rt2x00lib              25344  3 rt2500pci,rt61pci,rt2x00pci
mac80211              192532  4 rt2500pci,rt61pci,rt2x00pci,rt2x00lib
eeprom_93cx6            3840  2 rt2500pci,rt61pci

```

I'm currently trying to follow the Feisty Fawn instructions, and some of it seems to work for Hardy, but other things don't. For example, according to wconfig, my wifi card is at /wlan0 instead of /ra1 or /ra0.

Furthermore, stuff like `$ sudo iwpriv wlan0 set AuthMode=WPAPSK` always returns:
```

wlan0     no private ioctls.

```

No idea what that means, but iwconfig now says:
```

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"Schelhaas-Vos Wifi"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

I still get the feeling something is not quite right. Anyway, after this I can't continue. The instructions tell me to `sudo ifconfig ra1 DESIRED_IP netmask YOUR_NETMASK up`, but I have no desired IP (shouldn't my provider assign that to me through dhcp?), and have no idea what my netmask should be.

Can someone tell me what all this means, and if I'm on the right track or if I'd better start over in a completely different direction?

---

### Post by mcvos on 2009-05-27
> **chili555 said:**
> It looks like it's working perfectly to me. It just isn't associated with an access point yet. Network Manager, which is installed by default, is designed to disallow a wireless connection if you have a wired ethernet connection, which you do:If you detach the wire and reboot, do you see your wireless network in the Network Manager icon? Can you connect?
No. I don't see the network manager (at the top-right, right?) at all. In its place, there's a red arrow pointing downwards with an exclamation mark in it.

After plugging the ethernet cable back in, I managed to get it going without rebooting, although this takes a surprising amount of work in Ubuntu. Isn't there some more helpful tool that can activate whatever network connection I want on the fly, without too much fuss? It still seems amazingly cumbersome to me.

> Do you get a better result with:```
**sudo** iwlist wlan0 scan
```
I do. Even after I've plugged my wired connection back in. A big list of wifi networks in my home. 

iwconfig and ifconfig:
```

mcv@lankhmar:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"Schelhaas-Vos Wifi"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1F:3F:11:33:D4   
          Bit Rate=1 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality=73/100  Signal level=-66 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

mcv@lankhmar:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1d:7d:af:27:9d  
          inet addr:192.168.178.21  Bcast:192.168.178.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:7dff:feaf:279d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:393 errors:0 dropped:0 overruns:0 frame:0
          TX packets:390 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:285766 (279.0 KB)  TX bytes:91599 (89.4 KB)
          Interrupt:251 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1614 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1614 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:82435 (80.5 KB)  TX bytes:82435 (80.5 KB)

wlan0     Link encap:Ethernet  HWaddr 00:11:50:de:7a:db  
          inet6 addr: fe80::211:50ff:fede:7adb/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:459 errors:0 dropped:0 overruns:0 frame:0
          TX packets:544 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:51867 (50.6 KB)  TX bytes:86022 (84.0 KB)

wlan0:avahi Link encap:Ethernet  HWaddr 00:11:50:de:7a:db  
          inet addr:169.254.9.123  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

wmaster0  Link encap:UNSPEC  HWaddr 00-11-50-DE-7A-DB-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```
iwconfig mentions an access point, despite my wifi not working and my ethernet being plugged in.

---

### Post by chili555 on 2009-05-27
Please do:```
sudo gedit /etc/NetworkManager/nm-system-settings.conf
```Make sure the line *managed=true* appears. If it's false, please change it, proofread, save and close gedit. Then do:```
sudo /etc/init.d/NetworkManager restart
```Does the icon now appear? If not, please try:```
nm-applet --sm-disable &
```How about now?> `lsmod | grep rt61` should say "rt61 245128 1"This is trivial and may be disregarded.> and if I'm on the right trackYou are on the right track. We need to get the Network Manager icon going and I believe you will connect. We are close.

---

### Post by mcvos on 2009-05-28
> **chili555 said:**
> Please do:```
sudo gedit /etc/NetworkManager/nm-system-settings.conf
```Make sure the line *managed=true* appears. If it's false, please change it, proofread, save and close gedit.
That file: /etc/NetworkManager/nm-system-settings.conf, doesn't exist at all. The directory /etc/NetworkManager doesn't exist. There is an /etc/network/ directory, but it doesn't contain anything suitable.

However, I've followed [some instructions]("http://ubuntuforums.org/showpost.php?p=3595458&postcount=6") that told me to uninstall it. After reinstalling, the dir exists, but nm-system-settings.conf still doesn't.

Have I wrecked my system? Can I get a fresh conf from somewhere? Should I just add managed=true to an empty file?

---

### Post by chili555 on 2009-05-28
You have not wrecked your system. Almost anything that can be done can be undone. What is the result of:```
nm-applet --sm-disable &
```Either the little icon will appear or informative error(s) will be displayed.

We can also try to configure this manually for now:```
sudo iwconfig wlan0 essid "Schelhaas-Vos Wifi"
sudo dhclient wlan0
```This assumes there is no encryption, WEP, WPA or the like on the system. Does your wireless connect or try to connect?

---

### Post by mcvos on 2009-05-28
> **chili555 said:**
> You have not wrecked your system. Almost anything that can be done can be undone. What is the result of:```
nm-applet --sm-disable &
```Either the little icon will appear or informative error(s) will be displayed.
After a fresh reboot without the cable connected, the network icon is already present. After this command, I get a second one. Clicking manual configuration pens the system->admin->network window. 

> We can also try to configure this manually for now:```
sudo iwconfig wlan0 essid "Schelhaas-Vos Wifi"
sudo dhclient wlan0
```This assumes there is no encryption, WEP, WPA or the like on the system. Does your wireless connect or try to connect?
No DHCPOFFERS received. But my wifi does have a WPA password.

Edit: complete output from dhclient wlan0:
```

Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:11:50:de:7a:db
Sending on   LPF/wlan0/00:11:50:de:7a:db
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

---

### Post by chili555 on 2009-05-28
> the network icon is already presentYou should be able to right click it and make sure that networking is enabled. Then if you left click it, you should see 'Auto wlan0.' Here is a tutorial on Network Manager. [https://help.ubuntu.com/community/NetworkManager0.7](https://help.ubuntu.com/community/NetworkManager0.7)

At some point, you should see your network, ask it to connect, fill in your WPA details and connect.

Your wireless interface and driver appear quite healthy.

---

### Post by mcvos on 2009-05-28
> **chili555 said:**
> You should be able to right click it and make sure that networking is enabled. Then if you left click it, you should see 'Auto wlan0.'
Right clicking says networking is enabled, left clicking just gives me the system->admin->network window, which is as useless as ever.

> Here is a tutorial on Network Manager. [https://help.ubuntu.com/community/NetworkManager0.7](https://help.ubuntu.com/community/NetworkManager0.7)
Ironically, that page claims Network Manager aims for networking that "just works".

Anyway, if I understand correctly, I should set wireless to "roaming" if I wat to see a list of wifi networks. When I do that, left clicking on the icon gives me more options, including a neighbour's wifi. Not my own though (nor any of the other wifis my mac can see in my house).
"Connect to other wireless network" and entering my own ssid and password adds our own wifi to the list, but it looks like it still can't detect a signal. Bar is empty, no network connection.

> At some point, you should see your network, ask it to connect, fill in your WPA details and connect.

Your wireless interface and driver appear quite healthy.
But my Belkin card seems unable to detect all the wifi networks that my mac sees, though. Hardware issue, perhaps?

---

### Post by mcvos on 2009-05-28
I tweak the antenna of my wifi card a bit, click the network icon again, and to my surprise, the network icon disappears! I reboot, and after rebooting, not only is the network icon there, but when I left click, it shows all 4 wifi networks in my building. Including my own. All with the bar (signal strength?) about 50% orange. Click mine, enter WPA, and it works. I'm posting this from my ubuntu machine over wifi.

Thanks a lot for all your help. I wouldn't have been able to figure this out without you.

I'd send you flowers or candy if I knew where you lived.

---

### Post by chili555 on 2009-05-28
Glad it's working for you! Have fun and go get those updates and torrents!

---

### Post by mcvos on 2009-05-28
This is really depressing. I install a Windows game on Wine, run it, it hangs my machine, I reboot, and after the reboot, my wifi doesn't work anymore. It's still listed in the list of wifi networks (blue bars in the task bar are at 75-100%, orange bar in the menu at 50%), but no traffic gets through.

---

### Post by mcvos on 2009-05-28
After running `sudo iwconfig` my connection works again. Or it must have been me loading my router's config page, but I didn't change anything there, and my mac still worked fine, so I doubt that's it. But iwconfig doesn't fix my connection, does it? I was under the impression that it only displays information.

In any case, having to run iwconfig every time I start my PC is not really what I'm looking for. I want an internet connection that "just works", but at the moment it feels a bit unreliable.

---

### Post by mcvos on 2009-05-29
Update: after this morning's boot, my wifi works fine without any fiddling. Let's hope it stays that way.

---

