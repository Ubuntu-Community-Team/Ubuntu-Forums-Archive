---
title: "ipod and banshee in lucid"
date: 2010-05-05
forum: Multimedia Software
---

### Post by giorsat on 2010-05-05
Hi everybody. Am I the only one who is not able to mount ipod under banshee? Ipods are seen in nautilus and rhythmbox while banshee is not able to mount it inside. The old trick killall - 9 nautilus procedure doesn't seem to work.

---

### Post by anivegmin on 2010-05-05
Same problem here since installing Lucid.
Worked fine under Karmic.
Now my Nano doesn't show up at all in Banshee.
Works fine with Rhythmbox.

---

### Post by Statik on 2010-05-06
Same trouble here except rhythmbox also segfaults. Banshee doesn't see ipod nano. 

Help!

:)

Statik

Ran banshee from the command line and here is what I'm getting:
```

statik@statik-laptop:~$ banshee
[Info 09:01:12.461] Running Banshee 1.6.0: [Ubuntu lucid (development branch) (linux-gnu, x86_64) @ 2010-04-04 14:20:11 UTC]
[Info 09:01:14.228] All services are started 1.497947s
[Info 09:01:15.374] nereid Client Started
[Warn 09:03:04.014] Caught and exception - System.Exception: org.freedesktop.Hal.NoSuchDevice: No device with id /org/freedesktop/Hal/device/usb_device_1d6b_2_0000_00_04_1_if0_0_scsi_host (in 'NDesk.DBus.Proxies')
  at Hal.IDeviceProxy.QueryCapability (System.String ) [0x00000]
  at Hal.Device.QueryCapability (System.String capability) [0x00000]
  at Banshee.HalBackend.HardwareManager.Resolve (Hal.Device hal_device) [0x00000]
  at Banshee.HalBackend.HardwareManager.OnHalDeviceAdded (System.Object o, Hal.DeviceAddedArgs args) [0x00000]
[Warn 09:03:04.016] Caught an exception - System.Exception: org.freedesktop.Hal.NoSuchDevice: no device with id /org/freedesktop/Hal/device/usb_device_1d6b_2_0000_00_04_1_if0_0 (in 'NDesk.DBus.Proxies')
  at Hal.IDeviceProxy.QueryCapability (System.String ) [0x00000]
  at Hal.Device.QueryCapability (System.String capability) [0x00000]
  at Banshee.HalBackend.HardwareManager.Resolve (Hal.Device hal_device) [0x00000]
  at Banshee.HalBackend.HardwareManager.OnHalDeviceAdded (System.Object o, Hal.DeviceAddedArgs args) [0x00000]
[Info 09:03:38.069] Received device command: action = Activate, device = /media/RODS_IPOD
[Info 09:11:25.624] Received device command: action = Activate, device = /media/RODS_IPOD
```
Looks like Banshee is seeing it but not recognizing it and doesn't know what to do with what its sending.

---

### Post by tehdog on 2010-05-07
Me too, neither with banshee 1.6.0 nor with 1.7.0,
```
altaica@Sklave:~$ banshee-1 
[Info  15:14:55.167] Running Banshee 1.7.0: [source-tarball (linux-gnu, i686) @ 2010-05-07 13:38:40 CEST]
[Info  15:14:56.211] All services are started 0,867937
[Info  15:14:58.969] nereid Client Started
[Info  15:16:15.241] Received device command: action = Activate, device = /media/ALTAICASIP
```my brother is already killing me because his computer won't work as he wants it to ;). Any simple solutions?

---

### Post by m4n_in_bl4ck on 2010-05-09
This is a known bug for Banshee:

[podsleuth: should activate HAL if needed, and needs DK=>udisks fix]("https://bugzilla.gnome.org/show_bug.cgi?id=615010")

I'm guessing we will all have to wait. :(

---

### Post by Statik on 2010-05-10
today's update took me farther from a solution. I don't even see the errors now. It just doesn't show up. Podsleuth sees nothing.

Rhythmbox segfaults with :
```
statik@statik-laptop:~$ rhythmbox
** (rhythmbox:5453): DEBUG: Loading the real store page

** (rhythmbox:5453): WARNING **: Syncdaemon already connected, not connecting again

liboauth: data to sign='GET&https%3A%2F%2Fone.ubuntu.com%2Fmusic%2Flogin&oauth_callback%3DNone%26oauth_consumer_key%3Dubuntuone%26oauth_nonce%3DN5JjhiBTfHEWK6W67TKpH5CnU%26oauth_signature_method%3DHMAC-SHA1%26oauth_timestamp%3D1273542574%26oauth_token%3D5PNzcH7DBMCMLXlW2LTK%26oauth_verifier%3DNone%26oauth_version%3D1.0'


liboauth: key='hammertime&WQq36vWcpqLblvpWPlvnWrBJTbjqZ4v09HqHRW4v2273NGHZbH8zd4hq3K9FX0SgWjqZtFHTnMm17HbQ'

** (rhythmbox:5453): DEBUG: navigation requested to https://one.ubuntu.com/music/login?oauth_callback=None&oauth_consumer_key=ubuntuone&oauth_nonce=N5JjhiBTfHEWK6W67TKpH5CnU&oauth_signature_method=HMAC-SHA1&oauth_timestamp=1273542574&oauth_token=5PNzcH7DBMCMLXlW2LTK&oauth_verifier=None&oauth_version=1.0&oauth_signature=1bPcet%2FTkJ%2FE7Mk8xgK9CiqFyOc%3D
Segmentation fault

```

*sigh* I was so happy, now, not so much. :)

Statik

---

### Post by m4n_in_bl4ck on 2010-05-10
This bug was fixed by Banshee developers last night but isn't yet available anywhere, except, of course, Git. Here is a short tutorial on how to compile the latest podsleuth from Git.

First, let's install the required packages to compile it:

```
sudo apt-get install git-core automake libmono-dev libndesk-dbus-glib1.0-cil-dev libndesk-dbus1.0-cil-dev libhal-dev libdbus-1-dev libsgutils2-dev mono-mcs mono-gmcs
```

That should do it. Now we've got to clone the podsleuth source code:

```
git clone git://git.gnome.org/podsleuth 
cd podsleuth
```

To compile the package, paste this in a terminal:

```
./autogen.sh && 
./configure --prefix=/usr &&
make
```

And finally, replace your version of podsleuth with the new one:

```
sudo make install
```

It's done. Just plug your iPod in and Banshee should recognize it as always.

Hope that works for you too!

---

### Post by toastermm on 2010-05-11
Thank you MIB!

Now it shows up in lsusb:
```

Me@Computer:~$ lsusb
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 05ac:1261 Apple, Inc. iPod Classic
Bus 001 Device 002: ID 058f:6377 Alcor Micro Corp. Multimedia Card Reader
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

Yay!  It's there.  Except nothing show up in Banshee or Rhythmbox.  It's not on the desktop either.  I'm not sure what happened in Lucid.

Any ideas?


****EDIT****

Sorry, turns out my ipod itself was frozen when I plugged it in. I reset it and it has showed up.  Silly me...  Thanks!

---

### Post by Statik on 2010-05-11
No Joy here!

dmesg gives:
```
[  197.180057] hub 4-0:1.0: unable to enumerate USB device on port 1
[  197.460070] hub 4-0:1.0: unable to enumerate USB device on port 1
[  197.740053] hub 4-0:1.0: unable to enumerate USB device on port 1
[  198.020072] hub 4-0:1.0: unable to enumerate USB device on port 1
[  198.300092] hub 4-0:1.0: unable to enumerate USB device on port 1
[  198.580067] hub 4-0:1.0: unable to enumerate USB device on port 1
[  198.860072] hub 4-0:1.0: unable to enumerate USB device on port 1
[  199.140041] hub 4-0:1.0: unable to enumerate USB device on port 1
[  199.420149] hub 4-0:1.0: unable to enumerate USB device on port 1
[  199.700063] hub 4-0:1.0: unable to enumerate USB device on port 1
[  199.980053] hub 4-0:1.0: unable to enumerate USB device on port 1
[  200.260053] hub 4-0:1.0: unable to enumerate USB device on port 1
[  200.540071] hub 4-0:1.0: unable to enumerate USB device on port 1
[  200.820078] hub 4-0:1.0: unable to enumerate USB device on port 1
[  201.100063] hub 4-0:1.0: unable to enumerate USB device on port 1
[  201.380072] hub 4-0:1.0: unable to enumerate USB device on port 1

```

```
statik@statik-laptop:~$ lsusb
Bus 004 Device 002: ID 046d:c018 Logitech, Inc. Optical Wheel Mouse
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 064e:a103 Suyin Corp. 
Bus 001 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. Mass Storage Device
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

This is what happened with the update yesterday. I noticed in the list there was a HAL update. Maybe that broke it?

Tried reseting the ipod and a different usb port. I got:
```
[  436.490054] usb 4-3: new low speed USB device using ohci_hcd and address 79
[  436.670065] usb 4-3: device descriptor read/64, error -62
[  436.960052] usb 4-3: device descriptor read/64, error -62
[  437.250052] usb 4-3: new low speed USB device using ohci_hcd and address 80
[  437.430065] usb 4-3: device descriptor read/64, error -62
[  437.730043] usb 4-3: device descriptor read/64, error -62
[  438.020059] usb 4-3: new low speed USB device using ohci_hcd and address 81
[  438.440045] usb 4-3: device not accepting address 81, error -62
[  438.620060] usb 4-3: new low speed USB device using ohci_hcd and address 82
[  439.050059] usb 4-3: device not accepting address 82, error -62
[  439.050089] hub 4-0:1.0: unable to enumerate USB device on port 3

```

Statik

---

### Post by m4n_in_bl4ck on 2010-05-12
Statik,

Your problem is not related to Banshee and Podsleuth. Maybe you should file a bug for that on Launchpad. ;)

---

### Post by Mphill102 on 2010-05-24
I found that if you disable USB auto mount. Banshee found my Ipod.
It worked for me.















In a terminal run
 gconf-editor 
Browse to **/apps/nautilus/preferences** and you will find two keys: **media_automount**  and **media_automount_open**. I unchecked them both.

---

### Post by lyhy on 2010-06-23
Thanks a lot, Mphill102 - that worked for me, too!

You know, I can't believe it has taken the better part of an afternoon to simply add a couple of CDs to my iPod. I have Ubuntu 10.04 (Lucid) and had Banshee 1.6.0. I upgraded that to 1.7.1 and it still didn't work - which absolutely floored me.

I mean, we're not talking about some esoteric item or activity here; we're talking about Banshee simply being able to see your iPod (which is kinda sorta popular) when you plug it in. You know, like Nautilus and RhythmBox can.

How they can let a product out the door that can't do this is beyond me. Even if this bug had snuck through the 1.6.0 release - well, bugs happen and that's life. Fine. But complaints are all over the Web about this, so how can they release 1.7.0 and then 1.7.1 without fixing it?

Just venting. Again, almost a whole stupid afternoon wasted on what should have been a 15 minute activity.

---

### Post by lyhy on 2010-06-28
Well, it worked a few days ago. I just tried it again and nothing. Unbelievable. I am so sick of the wasted time just trying to get Banshee to see my iPod when I plug it in it's not even funny.

And from the looks of it, many others are sick of this situation as well.

I think I'm going to switch to RhythmBox. Does anyone have any better ideas?

---

### Post by Statik on 2010-06-28
Well, the updates last week or so seemed to fix the issue for me. I haven't tried it this week yet. 

It seems like the issue is atleast being worked on.

Statik

---

