---
title: "Problem rooting HTC Evo 4G"
date: 2012-10-20
forum: Mobile Technology Discussions (CLOSED)
---

### Post by temporos on 2012-10-20
I can't figure this one out.  Maybe someone here can.  I'm running Lubuntu 12.04, and I'm trying to root my HTC Evo 4G (circa Feb 2011).  Here are some stats on it...

[LIST]
[*]HBOOT: 2.18.0001
[*]USB debugging: On
[*]USB Mode: charge only
[*]Mode: S-On
[/LIST]

I can get to the bootloader, and it seems LXDE recognizes that the phone is plugged in, because I'm offered the "Fastboot USB" header in the HTC bootloader.  When I try to root it, though, I get this:
```
$ ./fastboot oem get_identifier_token
< waiting for device >
```

And it just sits there like that forever.  It looks like it's not recognizing that the device is connected, so I ran this:
```
$ ./adb devices
List of devices attached 

$
```

Looks there like the device *isn't* being detected.  But then, look at this.
```
$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 13d3:5108 IMC Networks 
Bus 002 Device 002: ID 045e:00f0 Microsoft Corp. 
Bus 001 Device 004: ID 0bb4:0fff High Tech Computer Corp. Android Fastboot Bootloader
```

So the kernel *does* recognize the device and sees that it's connected to the USB port.  What's going on?  I'm stumped.

---

### Post by rootyourbrain on 2012-10-22
> **temporos said:**
> I can't figure this one out.  Maybe someone here can.  I'm running Lubuntu 12.04, and I'm trying to root my HTC Evo 4G (circa Feb 2011).  Here are some stats on it...

[LIST]
[*]HBOOT: 2.18.0001
[*]USB debugging: On
[*]USB Mode: charge only
[*]Mode: S-On
[/LIST]

I can get to the bootloader, and it seems LXDE recognizes that the phone is plugged in, because I'm offered the "Fastboot USB" header in the HTC bootloader.  When I try to root it, though, I get this:
```
$ ./fastboot oem get_identifier_token
< waiting for device >
```

And it just sits there like that forever.  It looks like it's not recognizing that the device is connected, so I ran this:
```
$ ./adb devices
List of devices attached 

$
```

Looks there like the device *isn't* being detected.  But then, look at this.
```
$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 13d3:5108 IMC Networks 
Bus 002 Device 002: ID 045e:00f0 Microsoft Corp. 
Bus 001 Device 004: ID **0bb4**:0fff High Tech Computer Corp. Android Fastboot Bootloader
```

So the kernel *does* recognize the device and sees that it's connected to the USB port.  What's going on?  I'm stumped.

Okay. I've seen this before, but with two different types of phones. (LG Optimus && Samsung S 4G)

According to the source that worked for me:
"
1.) **gedit /etc/udev/rules.d/51-android.rules** (*as root*)
2.) Paste the following:
 **SUBSYSTEM=="usb", SYSFS{idVendor}=="0bb4", MODE="0666"**
3.) *Save and Exit*.

**If you notice **idVendor =="0bb4"** <<-- That's HTC**

Then in the terminal:
./adb kill-server
./adb start-server
./adb devices (should now show your device info.)

Hope this helps.

---

### Post by temporos on 2013-01-16
> **rootyourbrain said:**
> 1.) **gedit /etc/udev/rules.d/51-android.rules** (*as root*)
2.) Paste the following:
 **SUBSYSTEM=="usb", SYSFS{idVendor}=="0bb4", MODE="0666"**
3.) *Save and Exit*.

**If you notice **idVendor =="0bb4"** <<-- That's HTC**

Then in the terminal:
./adb kill-server
./adb start-server
./adb devices (should now show your device info.)

That didn't work, unfortunately.  After much banging of head on wall, however, I found a solution (finally).  It's much like yours.

[LIST=1]
[*]Navigate in file manager to [COLOR="Blue"]/etc/udev/rules.d[/COLOR] directory.
[*]Click Tools > Open Current Folder as Root.
[*]Enter your password at the prompt and click "OK."  A new file manager window will open.  Use this new window for the rest of these instructions.
[*]Right-click on file [COLOR="Green"]51-android.rules[/COLOR] and open using gedit or leafpad.  If [COLOR="green"]51-android.rules[/COLOR] doesn't exist, create a new gedit/leafpad file and save it as this file.
[*]In line 1, copy/paste everything in red.  [COLOR="Red"]# fastboot/adb protocol on doubleshot (MT4GS)[/COLOR]
[*]In line 2, copy/paste everything in red.  [COLOR="red"]SUBSYSTEM=="usb", SYSFS{idVendor}=="0e79", MODE="0666", OWNER="*<username>*"[/COLOR]
[*]Replace *[COLOR="red"]<username>[/COLOR]* with your personal username.
[*]Click File > Save.
[*]Click File > Exit.
[*]Save your work in all open apps and log-out.
[*]Log-in and attempt to root device.
[/LIST]

---

