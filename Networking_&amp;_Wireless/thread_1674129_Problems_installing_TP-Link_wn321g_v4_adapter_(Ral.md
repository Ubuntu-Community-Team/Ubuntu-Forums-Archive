---
title: "Problems installing TP-Link wn321g v4 adapter (Ralink RT2070)"
date: 2011-01-23
forum: Networking &amp; Wireless
---

### Post by megavolt500 on 2011-01-23
I am a total newbie, running Ubuntu 10.10 (upgraded). I am trying to get my TP-Link wn321g ver4 working.
After spending over a week on various instructions which I found on various forums, I came across pesarak's instructions, found here:

[http://www.uluga.ubuntuforums.org/showthread.php?t=1285828&page=13](http://www.uluga.ubuntuforums.org/showthread.php?t=1285828&page=13)

who's directions I followed to the best of my ability. Unfortunately I was unsuccessful.

My device is shown (lsusb) as:
Bus 001 Device 002: ID 148f:2070 Ralink Technology, Corp. RT2070 Wireless Adapter

All was going more or less ok until I got to "make install". I then got this:

make -C /home/boss/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux -f Makefile.6 install
mkdir: cannot create directory `/etc/Wireless': File exists
make[1]: Entering directory `/home/boss/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux'
rm -rf /etc/Wireless/RT3070STA
mkdir /etc/Wireless/RT3070STA
cp /home/boss/2009_0525_RT3070_Linux_STA_v2.1.1.0/RT2870STA.dat /etc/Wireless/RT3070STA/.
install -d /lib/modules/2.6.35-24-generic/kernel/drivers/net/wireless/
install -m 644 -c rt3070sta.ko /lib/modules/2.6.35-24-generic/kernel/drivers/net/wireless/
install: cannot stat `rt3070sta.ko': No such file or directory
make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/boss/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux'
make: *** [install] Error 2

I did the manual file copying, but when I got to:
sudo cp ./rtk3070sta.ko /lib/modules/`uname -r`/kernel/drivers/staging/rt3070/

I got:
cp: cannot stat `./rtk3070sta.ko': No such file or directory

When I tried to start the module I got:
FATAL: Module rt3070sta not found

I really don't know where to go from here. Can anyone please help me?

---

### Post by chili555 on 2011-01-23
I have no doubt that this old file won't work:> [COLOR="Red"]2009[/COLOR]_[COLOR="Red"]05[/COLOR]25_RT3070You are running the latest kernel. Your device is supposed to work with rt2800usb. ```
$ modinfo rt2800usb | grep 2070
alias:          usb:v[COLOR="Red"]148F[/COLOR]p[COLOR="Red"]2070[/COLOR]d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v8516p2070d*dc*dsc*dp*ic*isc*ip*
```Did it not work for you? Please do:```
sudo modprobe rt2800usb
iwconfig
dmesg | grep -i rt2
```Thanks.

---

### Post by megavolt500 on 2011-01-23
UPDATE:
I have FINALLY managed to get past "make install".
Now the problem is that when I try to start the module I get:

FATAL: Error inserting rt3070sta (/lib/modules/2.6.35-24-generic/kernel/drivers/net/wireless/rt3070sta.ko): Device or resource busy

Can anyone please help me with this?

---

### Post by chili555 on 2011-01-23
> Can anyone please help me with this?Please see above.

---

### Post by megavolt500 on 2011-01-23
Sorry, I posted before I saw your post.

My results;

modinfo rt2800usb | grep 2070

alias:          usb:v8516p2070d*dc*dsc*dp*ic*isc*ip*


iwconfig



wlan1-wlan0  IEEE 802.11bg  ESSID:"upstairsnetwork"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:21:27:F5:38:82   
          Bit Rate=48 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=65/70  Signal level=-45 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

wlan0     Ralink STA  ESSID:""  Nickname:"RT2870STA"
          Mode:Monitor  Frequency=2.437 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=100/100  Signal level:0 dBm  Noise level:-83 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

dmesg | grep -i rt2


[ 3640.331155] usbcore: registered new interface driver rt2800usb

---

### Post by chili555 on 2011-01-23
It appears your Ralink is working. I wonder why you have two wireless interfaces with one named wlan1-wlan0. Are you trying to connect two wireless interfaces at once? Let's have a look at:```
lsmod | grep -e rt2 -e rt3
```Thanks.

---

### Post by megavolt500 on 2011-01-23
I have a wireless card that doesn't work as well. In places with weak reception I would like to use the wn321g because I can stick it on a cable and extend it. Do I have to turn off the card in some way so that the usb adapter will work?

lsmod | grep -e rt2 -e rt3

rt2800usb               8367  0 
rt2800lib              28897  1 rt2800usb
rt2x00usb               9779  2 rt2800usb,rt2800lib
rt2x00lib              27275  2 rt2800lib,rt2x00usb
mac80211              231541  3 rt2x00usb,rt2x00lib,b43
rt2870sta             406690  1 
cfg80211              144470  3 rt2x00lib,b43,mac80211
crc_ccitt               1351  2 rt2800usb,rt2870sta
led_class               2633  2 rt2x00lib,b43

---

### Post by chili555 on 2011-01-23
Would it work for you to disable the other card altogether? It would sure make getting the TP-Link to work easier. Is the other card an internal card? Broadcom, perhaps? Please post:```
lspci -nn
modinfo rt2870sta | grep 2070
```

---

### Post by megavolt500 on 2011-01-23
Yes. If I'm not mistaken, it's a Dell 1350 internal wireless card.

lspci -nn

00:00.0 Host bridge [0600]: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller [8086:2590] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller [8086:2592] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller [8086:2792] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 [8086:2658] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 [8086:2659] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 [8086:265a] (rev 03)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 [8086:265b] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller [8086:265c] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev d3)
00:1e.2 Multimedia audio controller [0401]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller [8086:266e] (rev 03)
00:1e.3 Modem [0703]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller [8086:266d] (rev 03)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge [8086:2641] (rev 03)
00:1f.1 IDE interface [0101]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller [8086:266f] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller [8086:266a] (rev 03)
02:01.0 CardBus bridge [0607]: Texas Instruments PCI1510 PC card Cardbus Controller [104c:ac56]
02:03.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
02:08.0 Ethernet controller [0200]: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile [8086:1068] (rev 03)


modinfo rt2870sta | grep 2070

alias:          usb:v148Fp2070d*dc*dsc*dp*ic*isc*ip*

---

### Post by chili555 on 2011-01-23
Please do:```
sudo gedit /etc/modprobe.d/blacklist.conf
```Add four lines:```
blacklist rt2800usb
blacklist rt2800lib
blacklist rt2x00usb
blacklist rt2x00lib
```Proofread carefully, save and close gedit. Reboot. Now can you see the TP-Link device when you click the Network Manager icon? Can you disconnect the Broadcom and connect the TP-Link?

---

### Post by megavolt500 on 2011-01-24
This is weird. it seems to be working, but I can't figure out how to use  the Network manager. I don't have any icon showing a Network Manager,  and it doesn't show up in any menu. I have a Network Connections, but it  just lets me configure the tcp-ip and the network settings - not the  hardware (at least as far as I can see). Ubuntu tells me that Network  Manager is indeed installed. In fact I uninstalled it and installed it  again, hoping to get the icons back, but no luck and it doesn't show up  anywhere in the menus.  Boy do I feel stupid. I bet that it's right in  front of my face somewhere and I don't see it. 
At the moment the TP-Link can't find networks, although I think it is recognized.

---

### Post by chili555 on 2011-01-24
The Network Manager icon, on newer default installations, looks like an antenna with radio waves at the top. Here is some information on missing applets: [https://help.ubuntu.com/community/NetworkManager](https://help.ubuntu.com/community/NetworkManager)> [B]Missing panel applet
[/B]
If you're missing the Network Manager panel applet, then (in Gnome) make sure that your panel contains the Notification Area applet. (Right-click on the panel to access the "Add to panel" command.) The NM applet can't be added directly to the panel, but is automatically part of the Notification Area. If you already have a Notification Area, but still no applet, then make sure the applet is installed. Just bc you have Network Manager does not mean you have the panel applet. Installing network-manager-gnome and restarting your system should make the panel applet appear in the Notification Area. (Instructions are needed for non-Gnome desktops.) 

---

### Post by megavolt500 on 2011-01-24
Wow. I have much bigger problems than I thought. Not only does my Network Manager not want to show up, but my Notification Area doesn't want to come up. I right clicked on the panel and chose the option "add to panel" (by the way, this option doesn't always show up. Sometimes I have to click a few times for it to show). I choose "Notification area" and click "add", but nothing happens. I tried to drag it there, but nothing.
I'm starting to think that something went wrong when I did the upgrade to 10.10.
I've been searching the internet for an answer, but no luck so far. How depressing.

---

### Post by megavolt500 on 2011-01-24
Got it. I got the Network Manager up, and disconnected the Broadcom. I think everything is working now.
Thank you so much for all your help. I really appreciate it.

---

### Post by yangfan88576638 on 2011-10-14
OMG, I have tried for hours until I typed 

sudo modprobe rt2800usb

And all of sudden, I got connected!!!

I should find this thread earlier.

OMG, this is a magic line. It can solve the ultimate problem of overall humanity!!!
Just type 

sudo modprobe rt2800usb

:popcorn:
> **chili555 said:**
> I have no doubt that this old file won't work:You are running the latest kernel. Your device is supposed to work with rt2800usb. ```
$ modinfo rt2800usb | grep 2070
alias:          usb:v[COLOR="Red"]148F[/COLOR]p[COLOR="Red"]2070[/COLOR]d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v8516p2070d*dc*dsc*dp*ic*isc*ip*
```Did it not work for you? Please do:```
sudo modprobe rt2800usb
iwconfig
dmesg | grep -i rt2
```Thanks.

---

