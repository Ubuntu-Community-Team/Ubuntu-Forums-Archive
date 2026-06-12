---
title: "Bluetooth Help"
date: 2008-06-16
forum: Multimedia Software
---

### Post by ssc351 on 2008-06-16
Hi,

I have a dell 640m inspirion...I got it from my dad and have been messing around on it for awhile.  The other day I noticed a little bluetooth light on the computer so I figured I'd give it a try since I never used bluetooth before. When I try and connect my phone, it can't find the computer.

In the bios, there is nothing that mentions having bluetooth or showing any bluetooth hardware.  However, here is what my dmesg gives:


[  160.679155] Bluetooth: Core ver 2.11
[  160.679296] NET: Registered protocol family 31
[  160.679301] Bluetooth: HCI device and connection manager initialized
[  160.679308] Bluetooth: HCI socket layer initialized
[  162.596441] Bluetooth: L2CAP ver 2.9
[  162.596449] Bluetooth: L2CAP socket layer initialized
[  160.798034] Bluetooth: RFCOMM socket layer initialized
[  160.798054] Bluetooth: RFCOMM TTY layer initialized
[  160.798057] Bluetooth: RFCOMM ver 1.8
[  163.647346] [drm] Initialized drm 1.1.0 20060810

What gives...am I reading all of this incorrectly?

---

### Post by ssc351 on 2008-06-18
bump

---

### Post by xc3RnbFO8P on 2008-06-18
I think you need a usb bluetooth dongle.

---

### Post by Kevbert on 2008-06-18
If you've got bluetooth then you want to turn the phone bluetooth on and make it visible to other devices.  Next open a terminal window and enter
```
hcitool scan
```
You should get a reply like this:
```
Scanning ...
        00:1E:DC:86:44:2D       K800i
```
This is the reply I get for my Sony Ericsson K800i phone.  The device address is the hex numbers and K800i is the name I've told my phone to use (it could be anything).
I've just looked at the specifications for your laptop and see nothing on bluetooth either on the Dell site or an independent site.  It may be an optional extra, may just mean that there's software support for it, or that it doesn't fully meet the bluetooth wireless specifications.

---

### Post by raymondvillain on 2008-06-19
I have 8.04 on a desktop.  Using a Rocketfish bluetooth keyboard and mouse.  Troubles with the mouse, no wheel effects.

If I type
"sudo hcitool dev"  I get

	hci0	00:10:60:EB:94:C8

If I type
"sudo hcitool scan" I get
Scanning.....

and then the prompt returns.  Can't figure it out.

I installed blueman ( [http://blueman.tuxfamily.org/](http://blueman.tuxfamily.org/) ) but it won't do anything.  By that I mean the window opens up but all of the buttons are inactivated.

Any suggestions?

---

### Post by Kevbert on 2008-06-20
> **raymondvillain said:**
> I have 8.04 on a desktop.  Using a Rocketfish bluetooth keyboard and mouse.  Troubles with the mouse, no wheel effects.

If I type
"sudo hcitool dev"  I get

	hci0	00:10:60:EB:94:C8

If I type
"sudo hcitool scan" I get
Scanning.....

and then the prompt returns.  Can't figure it out.

Any suggestions?

The device that is being displayed by the 'dev' option is the computer and not the keyboard or mouse.  The 'scan' option should show new addresses for both the keyboard and mouse.
Have you got 'gnome-bluetooth' and 'gnome-vfs-obexftp' installed ?  You can get these via Synaptic.
There's another command for bluetooth but I can't find it (in case hcitool fails to find devices).  Once you can see your bluetooth devices, there's a guide [here]("http://www.ubuntugeek.com/howto-setup-bluetooth-keyboard-and-mouse-in-ubuntu.html").

---

### Post by raymondvillain on 2008-06-20
Thanks for the tip.  It didn't change anything, though.  But I did check out the link you so thoughtfully provided and I discovered that I have no bluez-utils files in my /etc/init.d folder.  I think I used synaptics to install bluez-utils.  Is it possible they are in the wrong folder?  Where should they be?

---

### Post by Kevbert on 2008-06-21
If you look at the Ubuntugeek page and comment 5, you'll see the new paths. I think this may have been due to updated software (hence the change of filename).

---

### Post by ssc351 on 2008-06-23
Ya I guess I don't have it...here is what i get:

hcitool scan
Device is not available: No such device

---

