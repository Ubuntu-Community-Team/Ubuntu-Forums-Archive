---
title: "can't connect to any wireless network"
date: 2010-12-26
forum: Networking &amp; Wireless
---

### Post by Honza007 on 2010-12-26
Hello,
I can't connect to any wireless network although my drivers seems to be working fine. I think it's somehow related to "Network connections" manager.
Please see attached image.

My current wired network (eth0) works fine I can ping google.com or browse Internet.

Thank you for any help.

Running Ubuntu x64 10.10, HP 8510p, Broadcom 1Gbps ethernet, Intel 4965agn

---

### Post by Honza007 on 2010-12-26
ok I removed network manager:
```
sudo apt-get remove network-manager
```
rebooted PC
and now ifconfig doesn't show any wlan0...

---

### Post by spiky001 on 2010-12-26
I think you need to reinstall network manager then post the output of ```
lspci
``` it will help others to see wireless card, I think the problem is with the drivers of wireless card

---

### Post by Honza007 on 2010-12-26
> **spiky001 said:**
> I think you need to reinstall network manager then post the output of ```
lspci
``` it will help others to see wireless card, I think the problem is with the drivers of wireless card

well it used to work without any problems on liveCD of Ubuntu 10.10. x64:

here is the output:
```
jan@ntb1:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:03.0 Communication controller: Intel Corporation Mobile PM965/GM965 MEI Controller (rev 0c)
00:03.2 IDE interface: Intel Corporation Mobile PM965/GM965 PT IDER Controller (rev 0c)
00:03.3 Serial controller: Intel Corporation Mobile PM965/GM965 KT Controller (rev 0c)
00:19.0 Ethernet controller: Intel Corporation 82566MM Gigabit Network Connection (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HBM (ICH8M-E) LPC Interface Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc M76 [Radeon Mobility HD 2600 Series]
01:00.1 Audio device: ATI Technologies Inc RV630/M76 audio device [Radeon HD 2600 Series]
02:06.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b9)
02:06.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b9)
02:06.3 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 20)
03:00.0 USB Controller: NEC Corporation USB (rev 43)
03:00.1 USB Controller: NEC Corporation USB (rev 43)
03:00.2 USB Controller: NEC Corporation USB 2.0 (rev 04)
10:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
```
any help is greatly appreciated

btw I did:
```
sudo apt-get install network-manager
```
(reboot)
and it didn't solve anything.

---

### Post by spiky001 on 2010-12-26
Ok open software sources Administration/software sources, tick the box down the bottom cd,
close software sources insert your cd open update manager, It should update including off of the cd hopefully it will install drivers you need

---

### Post by Honza007 on 2010-12-26
> **spiky001 said:**
> Ok open software sources Administration/software sources, tick the box down the bottom cd,
close software sources insert your cd open update manager, It should update including off of the cd hopefully it will install drivers you need

Just before I do that - isn't that problem of network manager itself? I installed "Wifi Radar" and the wireless adapter seems to be working fine - please see attached picture.

The follow up problem is that I can't manage my **wired** adapter with this wifi radar so I need that "network manager" software working.

---

### Post by hugmenot on 2010-12-26
First of all that empty Wireless tab you show is not supposed to contain anything because it is meant for »presets«, i.e., wireless networks that you have been connected to in the past and have saved some settings and passwords for.

Secondly, does the left click menu of the applet show any networks?
That is, do you get scan results?

You can get textual scan results from NetworkManager via:

```
nmcli dev wifi
```

or you can get textual scan results from the kernel directly:

```
sudo iw wlan0 scan
```

And then, when you connect you can have log output by reading 

```
less /var/log/daemon.log
```

New messages appear at the bottom. This should give clear information about is going on while connecting.

Please report back.

---

### Post by Honza007 on 2010-12-26
> **hugmenot said:**
> First of all that empty Wireless tab you show is not supposed to contain anything because it is meant for »presets«, i.e., wireless networks that you have been connected to in the past and have saved some settings and passwords for.

Secondly, does the left click menu of the applet show any networks?
That is, do you get scan results?

You can get textual scan results from NetworkManager via:

```
nmcli dev wifi
```

or you can get textual scan results from the kernel directly:

```
sudo iw wlan0 scan
```

And then, when you connect you can have log output by reading 

```
less /var/log/daemon.log
```

New messages appear at the bottom. This should give clear information about is going on while connecting.

Please report back.

Ok the wireless adapter seems tobe working:
```
jan@ntb1:~$ sudo iw wlan0 scan
BSS XX:XX:XX:XX:ce:XX (on wlan0)
	TSF: 65032069054 usec (0d, 18:03:52)
	freq: 2437
	beacon interval: 100
	capability: ESS Privacy ShortPreamble ShortSlotTime (0x0431)
	signal: -51.00 dBm
	last seen: 2050 ms ago
	SSID: navinohradu01
	Supported rates: 1.0* 2.0* 5.5* 11.0* 6.0 9.0 12.0 18.0 
	DS Parameter set: channel 6
	RSN:	 * Version: 1
		 * Group cipher: CCMP
		 * Pairwise ciphers: CCMP
		 * Authentication suites: PSK
		 * Capabilities: (0x0000)
	ERP: <no flags>
	Extended supported rates: 24.0 36.0 48.0 54.0 
	WMM:	 * Parameter version 1
		 * u-APSD
		 * BE: CW 15-1023, AIFSN 3
		 * BK: CW 15-1023, AIFSN 7
		 * VI: CW 7-15, AIFSN 2, TXOP 3008 usec
		 * VO: acm CW 3-7, AIFSN 2, TXOP 1504 usec
	HT capabilities:
		Capabilities: 0x104c
			HT20
			SM Power Save disabled
			RX HT40 SGI
			No RX STBC
			Max AMSDU length: 7935 bytes
			DSSS/CCK HT40
		Maximum RX AMPDU length 65535 bytes (exponent: 0x003)
		Minimum RX AMPDU time spacing: 1/2 usec (0x02)
		HT RX MCS rate indexes supported: 0-7
		HT TX MCS rate indexes are undefined
```

and the log is following:
```
Dec 26 18:08:52 ntb1 wpa_supplicant[1462]: Failed to initiate AP scan.
Dec 26 18:08:52 ntb1 connmand[2650]: wlan0 scanning finished
Dec 26 18:08:53 ntb1 connmand[2650]: wlan0 INACTIVE (scanning)
Dec 26 18:09:52 ntb1 connmand[2650]: wlan0 SCANNING
Dec 26 18:09:52 ntb1 connmand[2650]: wlan0 scanning started
Dec 26 18:09:54 ntb1 connmand[2650]: wlan0 scanning finished
Dec 26 18:09:54 ntb1 connmand[2650]: wlan0 INACTIVE
Dec 26 18:10:52 ntb1 connmand[2650]: wlan0 SCANNING
Dec 26 18:10:52 ntb1 connmand[2650]: wlan0 scanning started
Dec 26 18:10:54 ntb1 connmand[2650]: wlan0 scanning finished
Dec 26 18:10:54 ntb1 connmand[2650]: wlan0 INACTIVE
Dec 26 18:11:52 ntb1 connmand[2650]: wlan0 SCANNING
Dec 26 18:11:52 ntb1 connmand[2650]: wlan0 scanning started
Dec 26 18:11:54 ntb1 connmand[2650]: wlan0 scanning finished
Dec 26 18:11:54 ntb1 connmand[2650]: wlan0 INACTIVE
Dec 26 18:12:52 ntb1 connmand[2650]: wlan0 SCANNING
Dec 26 18:12:52 ntb1 connmand[2650]: wlan0 scanning started
Dec 26 18:12:54 ntb1 connmand[2650]: wlan0 scanning finished
Dec 26 18:12:54 ntb1 connmand[2650]: wlan0 INACTIVE
Dec 26 18:13:51 ntb1 connmand[2650]: wlan0 SCANNING (scanning)
Dec 26 18:13:51 ntb1 connmand[2650]: wlan0 scanning started
Dec 26 18:13:52 ntb1 wpa_supplicant[1462]: Failed to initiate AP scan.
Dec 26 18:13:52 ntb1 connmand[2650]: wlan0 scanning finished
Dec 26 18:13:53 ntb1 connmand[2650]: wlan0 INACTIVE (scanning)
```

The other main problem is that I don't have the icon (disappeared) so I can't left-click it to list the wireless networks (please see attached image).

Other thought - if I'm currently connected via wired network (posting this reply) as far as I remember it was enlisted in **wired** connections list wasn't it? (please see attached image)

---

### Post by hugmenot on 2010-12-26
> **Honza007 said:**
> The other main problem is that I don't have the icon (disappeared) so I can't left-click it to list the wireless networks (please see attached image).

The icon part of NM is called nm-applet.

Check if it&#8217;s running:
```
pgrep -fl nm-applet
```

if not start it:

```
nm-applet & disown
```

If it&#8217;s not available at all:  install network-manager-gnome.

> 
Other thought - if I'm currently connected via wired network (posting this reply) as far as I remember it was enlisted in **wired** connections list wasn't it? (please see attached image)

Nope. You can make presets for the wired network just the same way (»Add« button) and give them names. E.g. @Home (static IP), @Work (DHCP), etc. You can then choose those presets from the network menu to switch.

---

### Post by Honza007 on 2010-12-26
> **hugmenot said:**
> The icon part of NM is called nm-applet.

Check if it’s running:
```
pgrep -fl nm-applet
```

if not start it:

```
nm-applet & disown
```

If it’s not available at all:  install network-manager-gnome.



Nope. You can make presets for the wired network just the same way (»Add« button) and give them names. E.g. @Home (static IP), @Work (DHCP), etc. You can then choose those presets from the network menu to switch.

Ok I tried following:
```
jan@ntb1:~$ killall gnome-panel &
[1] 4191
```
I read about it in other thread: ["Network Icon has disappeared"]("http://ubuntuforums.org/showthread.php?t=1653102")
*But it didn't help anything...*


```
jan@ntb1:~$ pgrep -fl nm-applet
1962 nm-applet --sm-disable
[1]+  Done                    killall gnome-panel
jan@ntb1:~$ nm-applet & disown
[1] 4260
jan@ntb1:~$ An instance of nm-applet is already running.

** (nm-applet:4260): WARNING **: <WARN>  constructor(): Couldn't initialize the D-Bus manager.

```

```
jan@ntb1:~$ sudo pgrep -fl nm-applet
[sudo] password for jan: 
1962 nm-applet --sm-disable
jan@ntb1:~$ sudo nm-applet & disown
[1] 4263
jan@ntb1:~$ An instance of nm-applet is already running.
```

```
jan@ntb1:~$ sudo apt-get install network-manager-gnome
Reading package lists... Done
Building dependency tree       
Reading state information... Done
network-manager-gnome is already the newest version.
network-manager-gnome set to manually installed.
The following packages were automatically installed and are no longer required:
  libopenal1 esound-clients libdiscid0 libsvga1 libmp3lame0 libesd0 liblzo2-2 esound-common
  libxvidcore4 libvdpau1 libmusicbrainz3-6 libaudiofile0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```
*It seems that it's installed...*
```
jan@ntb1:~$ sudo apt-get install nm-applet
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package nm-applet
jan@ntb1:~$ sudo killall gnome-panel &
[1] 4275
jan@ntb1:~$ 
```

Any other thoughts?

---

### Post by Honza007 on 2010-12-26
*I just updated the the topic name to make it more clear for others with similar problems.*

---

### Post by hugmenot on 2010-12-26
Did you log out yet? Normally it should definitely appear then.

You can also try to kill it and then start it:

```
pkill nm-applet
nm-applet & disown
```

Oh, and you need the NetworkManager background daemon running.

You could either just reboot your whole machine or start it by running

```
sudo start network-manager
```


I think all this icon business was the effect of your just blindly removing NetworkManager.
I bet that came out of reading this forum. Some people are just noobs giving noob advise around here.

---

### Post by Honza007 on 2010-12-26
I tried to rescan the network with my favorite command line tools package aircrack-ng and everything seems to be working fine:
1/
```
jan@ntb1:~$ sudo apt-get install aircrack-ng
```
2/
```
jan@ntb1:~$ sudo airmon-ng start wlan0
```

*It even complains about NetworkManager :):*
> Found 4 processes that could cause trouble.
[B]If airodump-ng, aireplay-ng or airtun-ng stops working after
a short period of time, you may want to kill (some of) them!

PID	Name
1201	NetworkManager
1211	avahi-daemon
1217	avahi-daemon
1462	wpa_supplicant[/B]


Interface	Chipset		Driver

wlan0		Intel 4965/5xxx	iwlagn - [phy0]
				(monitor mode enabled on mon0)

```
jan@ntb1:~$ sudo airodump-ng mon0
```
> CH  9 ][ Elapsed: 4 s ][ 2010-12-26 18:40                                         
                                                                                                                     
 BSSID              PWR  Beacons    #Data, #/s  CH  MB   ENC  CIPHER AUTH ESSID                                      
                                                                                                                     
 XX:XX:XX:XX:CE:XX  -50       10        0    0   6  54e. WPA2 CCMP   PSK  {myssid}                              
                                                                                                                     
 BSSID              STATION            PWR   Rate    Lost  Packets  Probes                                           
                                                                                                                     

jan@ntb1:~$ 

**I think that now it's all about that icon which disappeared.**

---

### Post by hugmenot on 2010-12-26
Ja, please don’t use airodump just to discover networks.

aircrack needs your card to be in Monitor mode to capture packets, but to use NetworkManager your card need to be in Managed mode.

You really don’t need airodump just to find networks. Just use NetworkManager for that. If you want to force a scan, then you can use

```
sudo iw wlan0 scan
```

It will scan and give you the result.

NetworkManager can’t be forced to scan, because scanning actually prevents sending anything to the network, so scanning all the time will prevent you using the internet.

Finally, if you want to use airodump, go and stop network-manager before, and re-enable it afterwards:

```
sudo stop network-manager
sudo airodump -i lwna0
sudo start network-manager
```

And use the left-click menu. It is for connecting.

---

### Post by hugmenot on 2010-12-26
And read herE:
[http://en.wikipedia.org/wiki/Network_detector](http://en.wikipedia.org/wiki/Network_detector)
[http://en.wikipedia.org/wiki/Monitor_mode](http://en.wikipedia.org/wiki/Monitor_mode)

Just leave it in Managed mode, it should work.

---

### Post by Honza007 on 2010-12-26
ok, after some "cleanup":
via Ubuntu software Center:
[LIST]
[*]connman-gnome
[*]wifi-radar
[/LIST]
via console:
```
sudo apt-get remove network-manager
```
(reboot)
```
sudo apt-get autoremove
```
(reboot)
```
sudo apt-get install network-manager
```
(reboot)

I can via left click connect to a wireless network (it's listed) and seems to be working. Please notice that even that I did not ever entered password for my wireless network it's listed as "auto n{blacklisted}1".

However I **can't manage via left click my current wired** network - change IP address etc... When I left click it all I see is:
> Wired Network
 device not managed
(as it is in uppertoolbar I can't make a printscreen of it as it enrolled)
while wifi has:
> Wireless Network
 disconnected
---Available---
n{blacklisted}1

***any thoughts how to make Network Manager to manage my wired network again?***

---

### Post by hugmenot on 2010-12-26
Do you have anything in /etc/network/interfaces now?

It should only contain this:

```
# The loopback network interface
auto lo
iface lo inet loopback
```

---

### Post by hugmenot on 2010-12-26
BTW, you can make a screenshot of the opened applet by using a screenshot tool with a time delay. For example:

```
gnome-screenshot --delay=5
```

and then you click on the menu within 5 seconds. Unfortunately opened menus eat key presses. That is a GTK limitation.

---

### Post by Honza007 on 2010-12-26
> **hugmenot said:**
> Do you have anything in /etc/network/interfaces now?

It should only contain this:

```
# The loopback network interface
auto lo
iface lo inet loopback
```

well it contains following:
> # This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.10.76
        netmask 255.255.255.0
        network 192.168.10.0
        broadcast 192.168.10.255
        gateway 192.168.10.1
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 192.168.10.1

btw thx for tip on that delayed screenshot! it looks like this (see attachement)

---

### Post by hugmenot on 2010-12-27
Yeah, everything below the line 
```
# The primary network interface
```
is the static configuration for your wired ethernet.

NM checks for static configuration in this file and if any is present it won&#8217;t touch the device at all. This is what is meant with »NM is not managing this device«.

Just remove all that. I guess one of the other connection managers you installed wrote those lines.

And now just simply click your wireless network, it should ask for the password.

I&#8217;m really surprised you manage to run aircrack, but you can&#8217;t figure out how to use the Networking applet.

---

### Post by Honza007 on 2010-12-27
Thank you for your reply. I'll keep it for future reference I had roll back to Win environment.

---

### Post by hugmenot on 2010-12-27
Great work.

---

