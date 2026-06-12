---
title: "Creative Zen Vision: M with Amarok"
date: 2007-02-21
forum: Multimedia &amp; Video
---

### Post by nickoli_02 on 2007-02-21
I followed [this]("http://thecrosstalk.blogspot.com/2007/01/amarok-music-manager.html") guide to build amarok with mtp support (note: the guide is for Edgy Eft but I'm using Dapper Drake, though this should not make a difference). Everything compiles fine and amarok is installed and functional: my problem is getting Amarok to detect my Creative Zen Vision: M. I tried going through Settings -> Configure Amarok -> Media Devices, and clicking auto detect, but it doesn't detect my Zen. 

Here is the output of lsusb:

```
$ lsusb
Bus 005 Device 006: ID 041e:413e Creative Technology, Ltd
Bus 005 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

```

So, simple enough.. my Zen is on bus 5 device 6. Now how do I mount it or get Amarok to see it? :)

---

### Post by fictivetoast on 2007-02-21
Try going to Settings-Configure Amarok, then click on the Media Devices sidetab at the bottom of the list.  Add device, then choose MTP as the plugin, and click ok.  Now try going back out to the main window, clicking on the Devices sidetab, and hitting "Connect" at the top.  If you're Zen is plugged in and turned on, if should notice it.

At least, that's what worked for me.

---

### Post by nickoli_02 on 2007-02-21
Zen is plugged in, turned on. I added it to Media Devices as you suggested. No dice. Amarok says: Could not connect to MTP device. Do I need to include a mount point?

---

### Post by nickoli_02 on 2007-02-21
OK I found an error message Amarok pops up when I try to autodetect devices:

```
No new media devices were found. If you feel this is an error, 
ensure that the DBUS and HAL daemons are running and KDE was 
built with support for them. You can test this by running 
"dcop kded mediamanager fullList" in a Konsole window.
```

```
$ dcop kded mediamanager fullList
ERROR: Couldn't attach to DCOP server!

```

I guess this is why Amarok isn't detecting my Zen... So, any ideas on how to fix this?

---

### Post by nickoli_02 on 2007-02-21
Obviously HAL and DBUS are running...

```
$ ps -ax | grep -a -e hal -e dbus
Warning: bad ps syntax, perhaps a bogus '-'? See http://procps.sf.net/faq.html
 4208 ?        Ss     0:01 /usr/bin/dbus-daemon --system
 4223 ?        Ss     0:08 /usr/sbin/hald
 4224 ?        S      0:00 hald-runner
 4229 ?        S      0:00 /usr/lib/hal/hald-addon-acpi
 4283 ?        S      0:00 /usr/lib/hal/hald-addon-keyboard
 4293 ?        S      0:13 /usr/lib/hal/hald-addon-storage
 4294 ?        S      0:10 /usr/lib/hal/hald-addon-storage
14846 ?        Ss     0:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session x-session-manager
14850 ?        S      0:00 /usr/bin/dbus-launch --exit-with-session x-session-manager
14849 ?        Ss     0:00 dbus-daemon --fork --print-pid 8 --print-address 6 --session

```

So, KDE wasn't built with support for HAL and DBUS daemons??

---

### Post by nickoli_02 on 2007-02-22
I restarted my computer and tried Amarok again. I got the same error message but when I run the command in the terminal I get a different output:

```
~$ dcop kded mediamanager fullList
/org/freedesktop/Hal/devices/volume_uuid_D0C4C482C4C46C72
hda1
31G Media

true
/dev/hda1
/media/hda1
ntfs
true

media/hdd_mounted

---
/org/freedesktop/Hal/devices/volume_uuid_6A5F_1690
hda2
6.3G Media

true
/dev/hda2
/media/hda2
vfat
true

media/hdd_mounted

---
/org/freedesktop/Hal/devices/volume_uuid_588662ab_71a3_48f6_8a52_931cceee03f6
hda3
60G Media

true
/dev/hda3
/
ext3
true

media/hdd_mounted

---
/org/freedesktop/Hal/devices/volume_uuid_1402_0B27
sda1
203G Media

true
/dev/sda1
/media/sda1
vfat
true

media/removable_mounted

---

```

And now I'm all out of ideas.

---

### Post by nickoli_02 on 2007-02-22
haha oookkkk the restart fixed everything... Amarok can talk to my Zen :) I think I'll close this post now.

---

### Post by d3athp3nguin on 2008-02-15
-also make sure libmtp 6 or 7 is installed.  Mine worked when I did the whole "Amarok Settings > devices > add device > MTP device" thing.  You have to hit the "connect" button yourself though.

Note that Gnomad2 is another alternative to add music onto your Zen.  The last time I used my zen on a windows machine, it nuked the zen firmware.  Never again...

---

### Post by d3athp3nguin on 2008-02-16
edit: duplicate, sorry.

---

