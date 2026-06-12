---
title: "Wireless card driver will not install"
date: 2010-12-27
forum: Networking &amp; Wireless
---

### Post by DuskGold on 2010-12-27
Told me to fo to /var/log/jockey.log

Got this I believe?

Any idea what may be wrong?

2010-12-27 21:22:37,907 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver
2010-12-27 21:22:37,990 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-12-27 21:23:19,342 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-12-27 21:23:19,516 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-12-27 21:23:19,543 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-12-27 21:23:24,061 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-12-27 21:23:25,218 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-12-27 21:23:28,963 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-12-27 21:23:28,964 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver
2010-12-27 21:23:29,034 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-12-27 21:23:31,742 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-12-27 21:23:31,903 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-12-27 21:23:31,929 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-12-27 21:23:33,203 DEBUG: Shutting down

---

### Post by Bucky Ball on 2010-12-27
Have you plugged in an ethernet cable and gotten all updates? That will identify your card. The wl drivers are now available from memory and should install without you having to screw around too much.

You might also run:

```
lspci
```

... in a terminal. Post your wireless card here (should be down the bottom somewhere) and we can figure if it is going to work 'out of the box'. The catch 22 is to get some wireless cards working you need to plug a cable in first to get the appropriate drivers (they are third-party and therefore can't be included in the Ubuntu install - you must be asked and agree to install them).

---

### Post by DuskGold on 2010-12-27
> **Bucky Ball said:**
> Have you plugged in an ethernet cable and gotten all updates? That will identify your card. The wl drivers are now available from memory and should install without you having to screw around too much.

You might also run:

```
lspci
```

... in a terminal. Post your wireless card here (should be down the bottom somewhere) and we can figure if it is going to work 'out of the box'. The catch 22 is to get some wireless cards working you need to plug a cable in first to get the appropriate drivers (they are third-party and therefore can't be included in the Ubuntu install - you must be asked and agree to install them).

Sorry new to Ubuntu.

I got my ethernet cable in, how do I know if I got all the updates?

I had the driver working yesterday but today my Nvida driver crashed and since then it wouldn't work anymore(wifi)

This is what that command brings up for me.
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
00:1f.6 Signal processing controller: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation GT216 [GeForce GT 240M] (rev a2)
01:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)
04:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
08:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe (rev 10)

---

### Post by Bucky Ball on 2010-12-27
Try System->Administration->Update Manager, then 'Check' if there is not already anything there.

Also in System->Admin you will find 'Additional Drivers'. Have a look there after updating. Is there the B43 driver available? If so, enable it.

Yes, as far as I know, Broadcom cards will work after an update. The B43 driver and appropriate firmware is now a few clicks to install (without having to screw about).

Your card:

```
04:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
```

---

### Post by DuskGold on 2010-12-27
I don't see an a additional drivers thing.

However my driver after updating activated, but is says it's not in use?

---

### Post by Bucky Ball on 2010-12-27
Where does it say that?

---

### Post by DuskGold on 2010-12-27
[http://oi51.tinypic.com/2pzmwqb.jpg](http://oi51.tinypic.com/2pzmwqb.jpg)

Here is a screenshot

---

### Post by Bucky Ball on 2010-12-27
Thanks, that is exactly what you want (almost!). You're definitely getting there. That is the driver you are after, but maybe hasn't downloaded the firmware. Try a restart and see what gives.

Ah, other thing. Switch off. Unplug ethernet cable, boot. Maybe not in use because the ethernet cable is.

One other option: In a terminal, with the cable in, type:

```
sudo apt-get update
```... then,

```
sudo apt-get upgrade
```Don't panic. This will not upgrade OS, only packages.

---

### Post by DuskGold on 2010-12-27
Wireless driver says it's working.

Detects wifi but does not connect to them.

Restarting change my res from 1366 x 768 to 1280 x 720 also :(

---

### Post by Bucky Ball on 2010-12-27
Well, all working via wireless card. Now a matter of getting your settings right so it connects to your access point (AP, probably your router). 

Make sure you have the correct details for your access point (ESSID: AP's name) and security key (WPA, WEP, whatever your router's using) then:

Right click the wireless icon and 'Edit Connections'
Go to the wireless connection;
Add the ESSID and security key to the IPV4 window.
As for resolution, reset to 1366x768.
Log out and back in again.

---

### Post by Bucky Ball on 2010-12-28
This might fix your issues. With ethernet cable in.

Go to Synaptic package manager and search for:

'b43-fwcutter' and 'firmware-b43-installer'. One of these maybe already installed. If they are both installed it is definitely a settings issue (as it is picking up the network but not connecting).
Mark them for installation and install.
Reboot.

---

