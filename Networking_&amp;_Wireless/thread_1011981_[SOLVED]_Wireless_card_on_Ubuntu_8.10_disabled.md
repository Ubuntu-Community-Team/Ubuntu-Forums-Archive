---
title: "[SOLVED] Wireless card on Ubuntu 8.10 disabled?"
date: 2008-12-15
forum: Networking &amp; Wireless
---

### Post by jtreach on 2008-12-15
I think I may have accidently disabled the wireless on my network card and now I don't know how to re-enable it. This is the 'network part' of
the output from the 'lshw' command:

> 
*-network
                description: Wireless interface
                product: BCM4312 802.11b/g
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:0c:00.0
                logical name: eth1
                version: 01
                serial: 00:22:69:14:0b:db
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=wl latency=0 module=wl multicast=yes wireless=IEEE 802.11bg

Any ideas?

---

### Post by Ayuthia on 2008-12-15
You can try the following in the Terminal:
```
sudo modprobe -r b43 ssb wl
sudo modprobe wl
sudo /etc/init.d/networking restart
sudo iwlist scan
```
If it shows wireless sites, then the module is working.  By any chance, did you just update your system?

---

### Post by jtreach on 2008-12-17
I entered all of your commands and just get 'interface doesn't support scanning' messages and it still says 'wireless disabled'. I was screwing around with my networking settings and had to reinstall ubuntu but whether it was that or an update I'm not sure.

---

### Post by Ayuthia on 2008-12-17
Can you post the results of the following:
```
uname -a
lsmod|grep -e b43 -e wl
cat /etc/network/interfaces
```

---

### Post by jtreach on 2008-12-17
uname -a gives:

> Linux josh-laptop 2.6.27-9-generic #1 SMP Thu Nov 20 21:57:00 UTC 2008 i686 GNU/Linux

lsmod|grep -e b43 -e wl gives:

> wl                   1076372  0 
ieee80211_crypt        13572  2 ieee80211_crypt_tkip,wl

cat /etc/network/interfaces gives:

> auto lo
iface lo inet loopback
(The exact output had a blank line at the end, thought that might be relevent)


Thanks for sticking with me, I really appreciate it.

---

### Post by Ayuthia on 2008-12-17
> **jtreach said:**
> uname -a gives:



lsmod|grep -e b43 -e wl gives:



cat /etc/network/interfaces gives:

(The exact output had a blank line at the end, thought that might be relevent)


Thanks for sticking with me, I really appreciate it.

You might want to check and see if you can go back to a previous kernel version.  It will help us see if the connection problem is with the current kernel version.

When your system boots up, there should either be a list of menu options to run a particular kernel version.  If it does not display one, you should be able to get into the menu options by pressing escape.

---

### Post by Dantes1976 on 2008-12-17
Hey, sorry for intruding in this thread but I have a related/similar question. Yesterday I installed Ubuntu 8.10 on my Fujitsu Siemens Amilo Pro V3505, over the pre-existing Vista installation (and format of whole hd). The wireless internet worked perfectly until when I first started it up today, when both the wireless (it says it's disabled and I can't re-enable it) and the wifi on/off button and led light wouldn't work anymore. I tried the commands that were mentioned in this thread already and all the results were similar except for for "lsmod|grep -e b43 -e wl" I got:

> 
wl                1076372 0
ieee80211_crypt     13572 1 wl
iwl3945             98801 0
rfkill              17176 2 iwl3945
mac80211           216820 1 iwl3945
led_class           12164 1 iwl3945
cfg80211            32392 2 iwl3945,mac82011


and the lshw command gave:

> 
*-network DISABLED
     description: Ethernet interface
     physical id: 1
     logical name: pan0
     serial: ba:c7:97:a7:91:ce
     capabilities: ethernet physical
     configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes


My wifi card is an internal Intel PRO/Wireless 3945ABG [Golan] Network Connection (rev 02).

---

### Post by S_e_P_p on 2008-12-17
Hello,

I had some similiar issues with BCM4318.

Start your laptop and use the lan cable for internet.
Afterwards install all updates. Restart and check again for updates. If you have new one install them also. Restart again.

Go to System --> and Hardware Drivers. Activate the Broadcom Driver.

Afterwards type the following in an terminal:

sudo /usr/share/b43-fwcutter/install_bcm43xx_firmware.sh

THAN RESTART.

Again in an Terminal.

echo 1 > /sys/devices/platform/acer-wmi/wireless

It should be activated now. (can take some minutes)

Greets
Sebastian

---

### Post by jtreach on 2008-12-17
I tried the previous kernel version to no effect.

When I was (stupidly) fiddling with the networking settings I vaguely remember a command which I think may of essentially disabled the wireless card by sort of flicking a switch on the wireless card itself. So my thinking is that there may be a command which can re-enable it, but that it probably isn't software related. I ran ubuntu 8.04 (from the live cd) today and the wireless didn't seem to work on that either.

Does that sound logical?

---

### Post by Ayuthia on 2008-12-17
> **S_e_P_p said:**
> Hello,

I had some similiar issues with BCM4318.

Start your laptop and use the lan cable for internet.
Afterwards install all updates. Restart and check again for updates. If you have new one install them also. Restart again.

Go to System --> and Hardware Drivers. Activate the Broadcom Driver.

Afterwards type the following in an terminal:

sudo /usr/share/b43-fwcutter/install_bcm43xx_firmware.sh

THAN RESTART.

Again in an Terminal.

echo 1 > /sys/devices/platform/acer-wmi/wireless

It should be activated now. (can take some minutes)

Greets
Sebastian

Unfortunately, the b43 module does not work for this card.  The 14e4:4315 card (you can verify this chipset number by typing lsmod -nn in the Terminal) is not supported by the b43 module at this time.  The original poster can only use the wl or ndiswrapper module.

---

### Post by S_e_P_p on 2008-12-17
> **Dantes1976 said:**
> Hey, sorry for intruding in this thread but I have a related/similar question. Yesterday I installed Ubuntu 8.10 on my Fujitsu Siemens Amilo Pro V3505, over the pre-existing Vista installation (and format of whole hd). The wireless internet worked perfectly until when I first started it up today, when both the wireless (it says it's disabled and I can't re-enable it) and the wifi on/off button and led light wouldn't work anymore. I tried the commands that were mentioned in this thread already and all the results were similar except for for "lsmod|grep -e b43 -e wl" I got:



and the lshw command gave:



My wifi card is an internal Intel PRO/Wireless 3945ABG [Golan] Network Connection (rev 02).

I suppose you should open a new thread for this as the solution is probably different for your wlan card.

---

### Post by Ayuthia on 2008-12-17
> **Dantes1976 said:**
> Hey, sorry for intruding in this thread but I have a related/similar question. Yesterday I installed Ubuntu 8.10 on my Fujitsu Siemens Amilo Pro V3505, over the pre-existing Vista installation (and format of whole hd). The wireless internet worked perfectly until when I first started it up today, when both the wireless (it says it's disabled and I can't re-enable it) and the wifi on/off button and led light wouldn't work anymore. I tried the commands that were mentioned in this thread already and all the results were similar except for for "lsmod|grep -e b43 -e wl" I got:



and the lshw command gave:



My wifi card is an internal Intel PRO/Wireless 3945ABG [Golan] Network Connection (rev 02).

You do not have a Broadcom card so your system should not be using the wl driver.  You might try the following and see if your card will work:
```
sudo modprobe -r wl iwl3945
sudo modprobe iwl3945
sudo /etc/init.d/networking restart
```Hopefully that will do it.  If it doesn't you might want to create another thread with your card listed in the subject.  It will hopefully get you some more support from the community because they will see your card info.

---

### Post by Ayuthia on 2008-12-17
> **jtreach said:**
> I tried the previous kernel version to no effect.

When I was (stupidly) fiddling with the networking settings I vaguely remember a command which I think may of essentially disabled the wireless card by sort of flicking a switch on the wireless card itself. So my thinking is that there may be a command which can re-enable it, but that it probably isn't software related. I ran ubuntu 8.04 (from the live cd) today and the wireless didn't seem to work on that either.

Does that sound logical?

I suppose that is possible.  The trick is what command did you use?  Do you have a 8.10 live cd?  It is the one that should have the wl module that should work out of the box.  8.04.1 is the first version that came with this module.

---

### Post by jtreach on 2008-12-17
Okay that's useful to know. I don't have a 8.10 live cd at the moment (it's downloading) but I'll try it on that and then let you know.

---

### Post by jtreach on 2008-12-17
I found an old 8.04.1 live cd kicking around. The wireless still didn't work after booting into the live cd and there was no 'wireless is disabled' display in the network applet when clicked. I don't know if this is just because of updates to the network manager or it's because my wireless card is dead and a freshly 'used/installed' ubuntu won't recognise it.

---

### Post by Ayuthia on 2008-12-17
I am doubting that it is because the card is dead.  I say this because the system still recognizes the card.  However the card is still not responding.

Is there a switch on the laptop that turns your wireless on or off?  Also, can you tell me the make and model of your laptop?  Usually Dell has a better working ratio than other laptops with this card.

---

### Post by jtreach on 2008-12-17
I just fiddled with the wireless switch.... and it works. I'm a complete idiot, sorry to have wasted your time.

---

### Post by Ayuthia on 2008-12-17
Hey!  We found out it was a switch and not a command!  At least it was a cheap and easy fix.  Glad to see it working.

---

