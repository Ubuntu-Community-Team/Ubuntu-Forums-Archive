---
title: "Huawei EC1260 does not work on Xubuntu"
date: 2012-05-30
forum: Networking &amp; Wireless
---

### Post by flurospar on 2012-05-30
I downloaded Xubuntu 12.04 a few hours ago, but unfortunately I can't get a working internet connection!

I have a Huawei EC1260 USB modem. When I plugged it in my computer, Xubuntu, let alone the nm-applet did not show any signs of recognising the device.

The vendor ID is 12d1 and the product ID is 140b as determined through "lsusb".

Any ideas?

---

### Post by alexfish on 2012-05-30
if a fairly new device

can suggest looking here

[http://ubuntuforums.org/showthread.php?t=1974458](http://ubuntuforums.org/showthread.php?t=1974458)

before committing have a look here , they have a forum
**[Draisberghof - Software - USB_ModeSwitch]("http://www.google.com/url?sa=t&rct=j&q=usb%20modeswitch&source=web&cd=1&ved=0CGcQFjAA&url=http%3A%2F%2Fwww.draisberghof.de%2Fusb_modeswitch%2F&ei=BKzGT_r3IcS80QWZ1_TZBQ&usg=AFQjCNHXRDd_7g_A3ekgGQ2d_tARDOR6iA&cad=rja")**

regards 

alexfish

---

### Post by flurospar on 2012-05-31
The device is not recent. I remember getting it in late 2009 and it is a CDMA/HSIA model.

modemmanager, usb-modeswitch & usb-modeswitch-data are already installed.

Please note that I am using Xubuntu 12.04 in Live mode.

---

### Post by flurospar on 2012-05-31
Okay. I have figured out a crude solution to this problem:


[LIST]
[*]Plug the thing in.
[*]Run the following commands ```
sudo rmmod usb-storage
sudo modprobe usbserial vendor=0x12d1 product=0x140b
```
[*]Wait for some time (around a minute or two).
[*]The device is recognised in nm-applet. From there the setup is easy.
[/LIST]

However, it looks like that this solution is not permanent, and one has to type the commands each and every time.

Is there a more permanent (or maybe, automated) solution to this problem?

Please help. I am a newbie and this is the first time I am seriously considering switching over to Linux distros permanently.

(Posting this from Xubuntu).

**EDIT:**Also, if I connect after following the aforementioned steps, it succeds. But if I try to disconnect, and connect again, it fails.

---

### Post by alexfish on 2012-05-31
Ok

can follow this thread,
			 [SOLVED] [**modem-manager not working**]("http://ubuntuforums.org/showthread.php?t=1969322")
use the the terminal commands, if using live mode

---

