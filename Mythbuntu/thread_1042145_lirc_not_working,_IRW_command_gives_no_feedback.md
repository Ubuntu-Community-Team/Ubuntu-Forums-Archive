---
title: "lirc not working, IRW command gives no feedback"
date: 2009-01-17
forum: Mythbuntu
---

### Post by davidstoll on 2009-01-17
lirc wasn't working so I decided to try and remove it and re-install it with apt-get.  Well, I lost my MythBuntu Control Centre.  I was able to get that back, but the restricted drivers manager is missing now.

lirc is still not working and that is my primary concern.  When I run the irw command, I don't get any feedback when pressing buttons.

I would greatly appreciate any help people can give me.

Thank you!

---

### Post by laceration on 2009-01-17
I'm assuming you had Lirc working and it stopped.  What happens sometimes to bonk Lirc is the drivers get messed up after a kernel upgrade.  You can verify if your drivers are there by
```
cat /proc/bus/usb/devices
```
if by your remote receiver device you have 
```
driver=none
``` it obliviously indicates you have no driver
I might be getting ahead of myself, so tell if I am not on the right track.  Anyways, reinstalling Lirc is usually not as useful as reinstalling the drivers with dkms.  If I am guessing right that is what you need to do.
Instructions are at this page:
[https://help.ubuntu.com/community/InstallLirc/Hardy#Adding%20support%20for%20more%20remotes](https://help.ubuntu.com/community/InstallLirc/Hardy#Adding%20support%20for%20more%20remotes)

---

### Post by davidstoll on 2009-01-18
> **laceration said:**
> I'm assuming you had Lirc working and it stopped.  What happens sometimes to bonk Lirc is the drivers get messed up after a kernel upgrade.  You can verify if your drivers are there by
```
cat /proc/bus/usb/devices
```
if by your remote receiver device you have 
```
driver=none
``` it obliviously indicates you have no driver
I might be getting ahead of myself, so tell if I am not on the right track.  Anyways, reinstalling Lirc is usually not as useful as reinstalling the drivers with dkms.  If I am guessing right that is what you need to do.
Instructions are at this page:
[https://help.ubuntu.com/community/InstallLirc/Hardy#Adding%20support%20for%20more%20remotes](https://help.ubuntu.com/community/InstallLirc/Hardy#Adding%20support%20for%20more%20remotes)

Yes, it was working at one point and then it just stopped.  I also suspect that an update broke it.

This is what I get...
cat: /proc/bus/usb/devices: No such file or directory

I can cd into /proc/bus/usb , but I don't see devices.  An ls -a shows an empty folder.

---

### Post by laceration on 2009-01-18
Your usb remote receiver device should be showing up even if lirc or drivers were not installed.  Check the hardware.  Try another usb port.  Maybe the wire that is connecting usb to your motherboard got disconnected??  What about the usb cable, try another??  Do you have anything to hook up to the usb to test it, like a mouse or camera?

---

### Post by encom on 2009-01-18
I fixed the problem by opening up Myth-Control Centre on the front end,  and selecting another IR, hitting apply, then re-selecting my IR and hitting apply.  Works like it used to now for me.

---

### Post by davidstoll on 2009-01-18
> **laceration said:**
> Your usb remote receiver device should be showing up even if lirc or drivers were not installed.  Check the hardware.  Try another usb port.  Maybe the wire that is connecting usb to your motherboard got disconnected??  What about the usb cable, try another??  Do you have anything to hook up to the usb to test it, like a mouse or camera?

The device is definitely plugged in because the little light blinks when it detects an IR transmission.

That usb port is working.  If I connect a mouse to it, the mouse works.

---

### Post by davidstoll on 2009-01-18
> **encom said:**
> I fixed the problem by opening up Myth-Control Centre on the front end,  and selecting another IR, hitting apply, then re-selecting my IR and hitting apply.  Works like it used to now for me.

Before it stopped working completely, that did seem to help, but there is something more serious now.

---

### Post by davidstoll on 2009-01-19
Update:
The "lsusb" command does list the device.

---

### Post by davidstoll on 2009-01-20
> **laceration said:**
> I'm assuming you had Lirc working and it stopped.  What happens sometimes to bonk Lirc is the drivers get messed up after a kernel upgrade.  You can verify if your drivers are there by
```
cat /proc/bus/usb/devices
```
if by your remote receiver device you have 
```
driver=none
``` it obliviously indicates you have no driver
I might be getting ahead of myself, so tell if I am not on the right track.  Anyways, reinstalling Lirc is usually not as useful as reinstalling the drivers with dkms.  If I am guessing right that is what you need to do.
Instructions are at this page:
[https://help.ubuntu.com/community/InstallLirc/Hardy#Adding%20support%20for%20more%20remotes](https://help.ubuntu.com/community/InstallLirc/Hardy#Adding%20support%20for%20more%20remotes)

I tried to follow this, but I guess I'm too green when it comes to linux to follow it.

But again, the hardware is working because it shows up with "lsusb".

Also, I have two ir receivers.  One MCE and one StreamZap.  Same problem with both.

---

### Post by davidstoll on 2009-01-20
> **davidstoll said:**
> I tried to follow this, but I guess I'm too green when it comes to linux to follow it.

But again, the hardware is working because it shows up with "lsusb".

Also, I have two ir receivers.  One MCE and one StreamZap.  Same problem with both.

Well, I fussed around a little more.  I noticed that my devices were already listed in my .c file...exactly how they should be based on lsusb.

When I run these steps...

```
6. Now it's time to rebuild the modules. We'll start by clearing out the old one.

      sudo dkms remove -m lirc -v 0.8.3~pre1 --all


7. Now it's time to build your new one.

      sudo dkms add -m lirc -v 0.8.3~pre1
      sudo dkms -m lirc -v 0.8.3~pre1 build
      sudo dkms -m lirc -v 0.8.3~pre1 install


```

I get this error...

```
Error! There are no instances of module: lirc
0.8.3~pre1 located in the DKMS tree.

and

Error! DKMS tree does not contain: lirc-0.8.3~pre1
Build cannot continue without the proper tree.

```

---

### Post by laceration on 2009-01-20
Did you download the the modules source?
```
sudo apt-get install lirc-modules-source
```
or you can do it with synaptic.

and the
```
0.8.3~pre1
```
should be replaced with the version of the modules that you have.  Also make sure you include the path or cd into it.

instead of
```
cat /proc/bus/usb/devices
```
try
```
 cat /dev/bus/usb/devices
```
to see if the drivers are there.

If your problems are from Myth, I can't help you, since I don't use it or know much about it.

---

### Post by davidstoll on 2009-01-21
> **laceration said:**
> Did you download the the modules source?
```
sudo apt-get install lirc-modules-source
```
or you can do it with synaptic.
Yes, I have the latest...
lirc-modules-source is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.

[QUOTE=```
0.8.3~pre1
```
should be replaced with the version of the modules that you have.  Also make sure you include the path or cd into it.[/QUOTE]
Yes, it looks like I'm using 0.8.3.

[QUOTE=instead of
```
cat /proc/bus/usb/devices
```
try
```
 cat /dev/bus/usb/devices
```
to see if the drivers are there.[/QUOTE]
Both give me "No such file or directory"


I believe the problem is not with Myth.  It's in in the linux system somewhere.

---

### Post by laceration on 2009-01-21
When you plug in the usb mouse does anything show up with
```
cat /dev/bus/usb/devices
```?

Are you running 64-bit Ubuntu?

---

### Post by davidstoll on 2009-01-21
> **laceration said:**
> When you plug in the usb mouse does anything show up with
```
cat /dev/bus/usb/devices
```?

Are you running 64-bit Ubuntu?

I do have a USB mouse and keyboard plugged in.  No, nothing shows up with that command.  However, when I type in lsusb, I get confirmation that the devices are connected.

Yes, I am running 64-bit.

---

### Post by laceration on 2009-01-21
64-bit has a glitch where the cat /proc... does not return anything.  I though it would not apply to the cat /dev command but maybe it does.  If we get those commands to work we can see if your lirc drivers are installed.  Here is how to do it:
```
 gksudo  gedit /etc/init.d/mountdevsubfs.sh
```
Lines 42-45 are commented out with the "#" character, remove the "#" from those lines + save the file.
Again try
```
cat /proc/bus/usb/devices
```
if it doesn't work you might need to log out and back in or even reboot.
When you get a result c+p it here.

---

### Post by davidstoll on 2009-01-21
> **laceration said:**
> 64-bit has a glitch where the cat /proc... does not return anything.  I though it would not apply to the cat /dev command but maybe it does.  If we get those commands to work we can see if your lirc drivers are installed.  Here is how to do it:
```
 gksudo  gedit /etc/init.d/mountdevsubfs.sh
```
Lines 42-45 are commented out with the "#" character, remove the "#" from those lines + save the file.
Again try
```
cat /proc/bus/usb/devices
```
if it doesn't work you might need to log out and back in or even reboot.
When you get a result c+p it here.

What should I be seeing on lines 42-45, because mine looks like this...
```
}

case "$1" in
  "")
```

---

### Post by laceration on 2009-01-21
Just above that do you have 
```
	# Magic to make /proc/bus/usb work
	#
	mkdir -p /dev/bus/usb/.usbfs
	domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
	ln -s .usbfs/devices /dev/bus/usb/devices
	mount --rbind /dev/bus/usb /proc/bus/usb
```
(already uncommented)

---

### Post by davidstoll on 2009-01-21
> **laceration said:**
> Just above that do you have 
```
	# Magic to make /proc/bus/usb work
	#
	mkdir -p /dev/bus/usb/.usbfs
	domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
	ln -s .usbfs/devices /dev/bus/usb/devices
	mount --rbind /dev/bus/usb /proc/bus/usb
```
(already uncommented)

Doesn't look like it.  Please see attachment.

---

### Post by laceration on 2009-01-21
Maybe they changed that in Intrepid, I'm still using Hardy.  Add the code in my last post to the do_start() function. That would be after line 41 and before the closing "}".

---

### Post by davidstoll on 2009-01-21
> **laceration said:**
> Maybe they changed that in Intrepid, I'm still using Hardy.  Add the code in my last post to the do_start() function. That would be after line 41 and before the closing "}".

I inserted the lines, rebooted...I still get...

"cat: /proc/bus/usb/devices: No such file or directory"

---

### Post by davidstoll on 2009-01-27
It seems to me that there must be a record of my (in a log file somewhere) running the apt-get autoremove (or whatever it was I ran) a couple weeks ago.

Then I can just re-install whatever it was that got mistakenly auto-removed....?

But I don't know exactly where to go or (probably) how to even read the logs.

---

### Post by onesojourner on 2009-02-11
I am having the exact same problem. I woke up one day and lirc was totally broken. I am running 8.04 32-bit. 

I get all the same errors you do and I can see my mce remote.

cat: /proc/bus/usb/devices: No such file or directory

---

### Post by davidstoll on 2010-01-17
I just setup a frontend box (Acer Aspire R3610) and had the same issue and...

sudo apt-get install lirc-modules-source

...seemed to fix it.  Now IRW shows my button presses.

By the way, these Acer Aspire Revo nettops with the atom 330 CPU's and the Ion Nvidia cards with VDPAU (DxVA is what Windows calls it) is AWESOME!

i.e.
[http://www.newegg.com/Product/Product.aspx?Item=N82E16883103234&cm_re=acer_R3610-_-83-103-234-_-Product](http://www.newegg.com/Product/Product.aspx?Item=N82E16883103234&cm_re=acer_R3610-_-83-103-234-_-Product)

I know it says it's out of stock or no longer available, but keep an eye out and look in other places.  There is a 230 version that is probably just fine because it has the same Ion Nvidia card, which is where the power comes from (with VDAPU) to play HD videos.

---

