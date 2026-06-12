---
title: "Installing Wireless USB Network Adapter?"
date: 2011-03-18
forum: Networking &amp; Wireless
---

### Post by daleybugle on 2011-03-18
Hi, I am trying to use a Netgear Wireless Network USB Adapter (WNDA3200) which came with my Virgin Media 50mb package.
It works fine in win7, but when I insert it whilst using ubuntu nothing seems to happen.

I have tried using Ndiswrapper to install the drivers for the device from the windows/system32/drivers folder, but I get a message of "Not a valid driver .inf file." when I clicked install.
(I found the drivers for this device by using the device manager in windows, I don't know if thats right?)

Any help would be greatly appreciated, as my linux knowledge is very limited.

Thanks :-|

---

### Post by gobbledigook on 2011-04-09
hi there!

did you get this working?? 

i have tried the [madwifi method]("https://help.ubuntu.com/community/WifiDocs/Driver/Atheros") suggested for atheros devices in the wifidocs but nothing changes....

it pops up in lsusb:
```
Bus 001 Device 002: ID 0846:9018 NetGear, Inc. 
```

but i still only see my current wireless device under the applet, i'm assuming a second wireless device should turn up in here?

---

### Post by gobbledigook on 2011-04-09
it appears that support for this device is included in kernel linux-2.6.36.4 onwards... ubuntu is on kernel 2.6.35 at the mo' so i suppose i shall just have to wait for it to catch up!

i have tried compiling my own kernel and adding the [patch found here]("http://ns3.spinics.net/lists/stable-commits/msg09366.html")...  however i get errors when trying to patch it... so i copied the whole drivers/net/wireless/ath/ath9k/hif_usb.c file from kernel 2.6.36.4 and tried to compile it into the 2.6.35... the only thing left is to get the latest kernel not from ubuntu? but i'm not sure about the implications of using with an ubuntu box?

---

### Post by gobbledigook on 2011-04-09
ok vaguely got the wnda3200 working by using [ndisgtk here]("https://help.ubuntu.com/8.04/internet/C/ndiswrapper.html")... and the windows driver i extracted off my xp box, attached. install it and point it towards the .inf file and your good to go

only works on the 2.4ghz band though :(

---

### Post by walt.smith1960 on 2011-04-09
Yup, NDISwrapper only works with XP drivers.  32 bit or 64 bit as appropriate.  I'm not sure if the .deb file found on sourceforge would be helpful or not.  It does work on Netgear WNA1100 which is a ath9k based USB device.  Here is the info on mine which I'm using to send this:

Bus 002 Device 003: ID 0846:9030 NetGear, Inc.

[http://sourceforge.net/projects/ath9k-htc/](http://sourceforge.net/projects/ath9k-htc/)

---

### Post by gobbledigook on 2011-04-11
> **walt.smith1960 said:**
> It does work on Netgear WNA1100 
thanx for the link! didn't find that before but will try it out later... is that usb dual band? can you "see" any 5ghz networks in the applet?

---

### Post by walt.smith1960 on 2011-04-11
> **gobbledigook said:**
> thanx for the link! didn't find that before but will try it out later... is that usb dual band? can you "see" any 5ghz networks in the applet?

The WNA1100 is a 150mb. device--it's single band only.  The WNDA3**1**00 is dual band so I'd guess the WNDA 3200 is as well.

---

### Post by gobbledigook on 2011-04-11
hi, i got errors installing the package through the UCS... so tried from cli:

```
dan@mini-ubuntu:~$ sudo dpkg -i Downloads/ath9k_htc-installer_1-0_all.deb 
(Reading database ... 158931 files and directories currently installed.)
Unpacking ath9k-htc-installer (from .../ath9k_htc-installer_1-0_all.deb) ...
[COLOR="Red"]dpkg: error processing Downloads/ath9k_htc-installer_1-0_all.deb (--install):
 trying to overwrite '/lib/firmware/ar9271.fw', which is also in package linux-firmware 1.38.5[/COLOR]
Processing triggers for hicolor-icon-theme ...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_GB.utf8.cache...
Processing triggers for python-support ...
Errors were encountered while processing:
 Downloads/ath9k_htc-installer_1-0_all.deb

```

i tried rm the file but still got the same error... not sure about uninstalling linux-firmware 1.38.5 ?

ok checked out the [changelog here]("http://www.ubuntuupdates.org/packages/show/299993") and it appears that support for this device was added at 1.38.5... but i get nothing when i plug in (when not using the window drivers)

---

### Post by walt.smith1960 on 2011-04-11
I'm wondering if you're having some sort of conflict or something.  If it were me I'd probably open a terminal and type "lsmod" and see what modules are loading then "dmesg" to see if there is anything looks out of place there.  Have you tried "iwconfig" to see if anything shows up in wlan? I'm no expert by any means, just trying to share my experiences.

---

### Post by gobbledigook on 2011-04-12
no worries i appreciate your suggestions :)

i am using a netbook with built in wireless which is broadcom... the dongle i am plugging in is atheros, so i'm assuming they use different drivers and therefore conflict is not likely. lsmod wasn't showing anything useful, but i found a [tutorial here]("http://ubuntuforums.org/showthread.php?t=1309072") for installing the madwifi drivers for atheros. alas this didn't do the trick, although i can see the module being loaded by lsmod... 

i only wanted to use it as i have 5ghz n on my router and need a faster connection to stream HD content from my server, but i suppose i shall have to just hang out and see if it works in the next kernel update. 

as i mentioned before there is a fix, using the windows driver however you cannot "see" the 5ghz SSID, therefore i can only assume it is only working on the 2.4ghz band. works fine from my windows box :(

---

### Post by walt.smith1960 on 2011-04-12
I can't say how your device will behave but the WNA1100/ath9k device is recognized "out of the box" in Natty.  It is also recognized by a Natty LiveCD if you're inclined to give that a go.

---

