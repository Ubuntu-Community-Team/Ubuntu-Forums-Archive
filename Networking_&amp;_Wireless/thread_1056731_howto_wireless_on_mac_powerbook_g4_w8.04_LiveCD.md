---
title: "howto: wireless on mac powerbook g4 w/8.04 LiveCD"
date: 2009-02-01
forum: Networking &amp; Wireless
---

### Post by r.stiltskin on 2009-02-01
For "occasional" use of Ubuntu on a PowerBook G4 without installing on the Mac's hard disk:

1. Burn a copy of the Mac (PowerPC) Desktop CD from
[http://cdimage.ubuntu.com/ports/releases/hardy/release/ubuntu-8.04.1-desktop-powerpc.iso](http://cdimage.ubuntu.com/ports/releases/hardy/release/ubuntu-8.04.1-desktop-powerpc.iso)

2. Press the Mac's power button, immediately (as soon as it will go in) insert the CD in the drive and at the same time press the C (that's the letter C, NOT Ctrl) key (hold the key down until you're sure it's booting from the CD).

3. At the boot prompt, type: live-nosplash <Enter> 
and wait patiently (don't worry about the PCI: Cannot allocate resource region ... errors).

-------------------------
Now for the networking ...

Wired networking seems to work immediately -- all I had to do was plug in an ethernet cable.  Wireless is a little more complicated since the Broadcom firmware is not on the CD.

The first step can be done on the laptop if you have a working wired internet connection; otherwise do it on any other machine running Hardy (i.e. your desktop).

1. Install b43-fwcutter (using Synaptic or apt-get install or the "Hardware drivers" wizard that pops up after booting from the CD) and then when the Debconf window pops up, check the box to "Fetch and extract firmware".

2. a. Now you will find two folders, /lib/firmware/b43 and /lib/firmware/b43legacy.  But they are just on the ramdisk (or another machine altogether) so copy those folders to a usb drive.  If your usb drive mounts to /media/disk:
```
cp -r /lib/firmware/b43* /media/disk
```

b. In the future, when you boot the Mac, just copy those folders back to the ramdrive with:
```
sudo cp -r /media/disk/b43* /lib/firmware/
sudo chmod -R 755 /lib/firmware/b43*
```

3. a. If you just installed the b43 firmware directly on the Mac, you should immediately be able to configure your wireless connection by:
```
sudo iwconfig wlan0 essid [your access point] key [your WEP key]
dhclient wlan0
``` (the details depend on your local wireless configuration)

b. For future sessions, and if you just copied the b43 firmware to the Mac from your USB drive, 2 additional steps seem necessary before iwconfig will work; uninstall and reinstall the b43 driver as follows:
```
modprobe -r b43
modprobe b43
```
and then ```
sudo iwconfig wlan0 essid [your access point] key [your WEP key]
dhclient wlan0
```

In the future, each time you boot from the LiveCD, you'll have to perform the steps 2b and 3b, since the contents of /lib/firmware disappear when you shut down.

---

