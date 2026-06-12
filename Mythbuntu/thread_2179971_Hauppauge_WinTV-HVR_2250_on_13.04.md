---
title: "Hauppauge WinTV-HVR 2250 on 13.04"
date: 2013-10-10
forum: Mythbuntu
---

### Post by David_Stoll on 2013-10-10
I had to replace my mobo and therefore had to get a new tuner card because the card slots were not the same.  I got the 2250 tuner card and I'm not getting any /dev/video* devices.  I'm getting this on bootup:


```
$ dmesg | grep saa
[   24.222755] saa7164 driver loaded
[   24.222788] saa7164[0]: Your board isn't known (yet) to the driver.
[   24.222788] saa7164[0]: Try to pick one of the existing card configs via
[   24.222788] saa7164[0]: card=<n> insmod option.  Updating to the latest
[   24.222788] saa7164[0]: version might help as well.
[   24.222861] saa7164[0]: Here are valid choices for the card=<n> insmod option:
[   24.222919] saa7164[0]:    card=0 -> Unknown
[   24.222955] saa7164[0]:    card=1 -> Generic Rev2
[   24.222992] saa7164[0]:    card=2 -> Generic Rev3
[   24.223028] saa7164[0]:    card=3 -> Hauppauge WinTV-HVR2250
[   24.223067] saa7164[0]:    card=4 -> Hauppauge WinTV-HVR2200
[   24.223105] saa7164[0]:    card=5 -> Hauppauge WinTV-HVR2200
[   24.223152] saa7164[0]:    card=6 -> Hauppauge WinTV-HVR2200
[   24.223190] saa7164[0]:    card=7 -> Hauppauge WinTV-HVR2250
[   24.223228] saa7164[0]:    card=8 -> Hauppauge WinTV-HVR2250
[   24.223266] saa7164[0]:    card=9 -> Hauppauge WinTV-HVR2200
[   24.223304] saa7164[0]:    card=10 -> Hauppauge WinTV-HVR2200
[   24.223653] CORE saa7164[0]: subsystem: 1131:0000, board: Unknown [card=0,autodetected]
[   24.223656] saa7164[0]/0: found at 0000:04:00.0, rev: 129, irq: 16, latency: 0, mmio: 0xf7800000
[   24.223664] saa7164_initdev() Unsupported board detected, registering without firmware
```


I've looked at (and used the 22xx wiki), but it has not helped.


Would someone be so kind as to help me troubleshoot this?

---

### Post by novellahub on 2013-10-11
According to the wiki here:

[http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-2200#Making_it_Work_Easily](http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-2200#Making_it_Work_Easily)

You need to create a file called options under the /etc/modprobe.d folder.  The options file should have:

```
options saa7164 card=8
```

Then reboot and see if the card is recognized.

---

### Post by David_Stoll on 2013-10-16
Sorry I didn't respond sooner, but I didn't get a notification that someone posted.

Actually, I did that exact same method and I did find out that I can cat the device:  cat /dev/video1 > /tmp/test.mp4
However, mythtv has some issues with it.  In Mythtv backend, it detects it as a deice (I set it up as an MPEG2 device per the wiki), but I can't change to that source in MythTV frontend.  Other devices/sources work just fine within Mythtv.  I'm not sure how to trouble shoot it though.

---

### Post by cedyathome on 2013-10-17
Here's what I see in my "dmesg | grep saa" - I use the same card, but I'm on 12.04. Did you create your firmware files? They weren't included in the distro the last time I built the system.

[    6.304019] saa7164_downloadfirmware() no first image
[    6.304076] saa7164_downloadfirmware() Waiting for firmware upload (NXP7164-2010-03-10.1.fw)
[    7.674326] saa7164_downloadfirmware() firmware read 4019072 bytes.
[    7.674330] saa7164_downloadfirmware() firmware loaded.
[    7.674339] saa7164_downloadfirmware() SecBootLoader.FileSize = 4019072
[    7.674345] saa7164_downloadfirmware() FirmwareSize = 0x1fd6
[    7.674346] saa7164_downloadfirmware() BSLSize = 0x0
[    7.674348] saa7164_downloadfirmware() Reserved = 0x0
[    7.674349] saa7164_downloadfirmware() Version = 0x1661c00
[   14.532008] saa7164_downloadimage() Image downloaded, booting...
[   14.636012] saa7164_downloadimage() Image booted successfully.
[   16.656006] saa7164_downloadimage() Image downloaded, booting...
[   18.424023] saa7164_downloadimage() Image booted successfully.
[   18.472749] saa7164[0]: Hauppauge eeprom: model=88061
[   20.961784] DVB: registering new adapter (saa7164)
[   23.988822] DVB: registering new adapter (saa7164)
[   23.989548] saa7164[0]: registered device video0 [mpeg]
[   24.222166] saa7164[0]: registered device video1 [mpeg]
[   24.438737] saa7164[0]: registered device vbi0 [vbi]
[   24.438825] saa7164[0]: registered device vbi1 [vbi]

---

### Post by David_Stoll on 2013-10-17
Yes, I have NXP7164-2010-03-10.1.fw, but even so, cat'ing the device results in a video file playable in VLC or Mplayer.  It seems like the problem is mythtv configuration.

---

### Post by novellahub on 2013-10-17
> **David_Stoll said:**
> Sorry I didn't respond sooner, but I didn't get a notification that someone posted.

Actually, I did that exact same method and I did find out that I can cat the device:  cat /dev/video1 > /tmp/test.mp4
However, mythtv has some issues with it.  In Mythtv backend, it detects it as a deice (I set it up as an MPEG2 device per the wiki), but I can't change to that source in MythTV frontend.  Other devices/sources work just fine within Mythtv.  I'm not sure how to trouble shoot it though.

Try setting it up as a DVB tuner.  Not a MPEG2 Device.

---

### Post by David_Stoll on 2013-10-17
Isn't DVB for digitial?  I'm looking to record analog.

---

### Post by novellahub on 2013-10-18
> **David_Stoll said:**
> Isn't DVB for digitial?  I'm looking to record analog.

Yes it is.  I no longer have analog channels in my area so I use only DVB tuners.  I would have thought by the cable providers would no longer offer analog cable.

---

### Post by novellahub on 2013-10-18
Maybe this thread will help?

[http://ubuntuforums.org/showthread.php?t=1567490](http://ubuntuforums.org/showthread.php?t=1567490)

---

### Post by David_Stoll on 2013-10-18
This post seems to work for some people.  However, I don't have an option for an IVTV card.  I've got lots of options and maybe it's known as something else now, but maybe it's the V4L tuner?  Anyway, I set it up as V4L, as it seems to be similar in that it doesn't auto-detect the device, so you have to manually type it.  Once you do manually type in the device (/dev/video1), it sees it as a Hauppauge 2250, but it can't find channels on a scan, so I'm probably wrong about the V4L...?  I'd post on that other thread, but it's really old and so much has changed with the kernel and ubuntu version.

[http://ubuntuforums.org/showthread.php?t=1567490&page=4&p=10003585#post10003585](http://ubuntuforums.org/showthread.php?t=1567490&page=4&p=10003585#post10003585)

---

### Post by novellahub on 2013-10-18
> **David_Stoll said:**
> This post seems to work for some people.  However, I don't have an option for an IVTV card.  I've got lots of options and maybe it's known as something else now, but maybe it's the V4L tuner?  Anyway, I set it up as V4L, as it seems to be similar in that it doesn't auto-detect the device, so you have to manually type it.  Once you do manually type in the device (/dev/video1), it sees it as a Hauppauge 2250, but it can't find channels on a scan, so I'm probably wrong about the V4L...?  I'd post on that other thread, but it's really old and so much has changed with the kernel and ubuntu version.

[http://ubuntuforums.org/showthread.php?t=1567490&page=4&p=10003585#post10003585](http://ubuntuforums.org/showthread.php?t=1567490&page=4&p=10003585#post10003585)

Try just grabbing the channels from the listing source instead of scanning. From the other thread I referenced, it says it does not work scanning.

---

### Post by David_Stoll on 2013-10-18
Ok, I did the "grab channels from listing source", which did not give any sort of error and let me move foward and save the settings for that input.  I'm getting 0 byte recordings from that source.  Other sources are recording ok, so it's not a read/write access issue.

---

### Post by David_Stoll on 2013-10-19
Basically, I'm still at a point, where I can cat the /dev/video1 in a command prompt and get a video output and even change channels using the v4l script, but can't seem to find the right configuration in mythtv backend.  My other devices (2 HDHomeRun's) work just fine.

---

### Post by novellahub on 2013-10-21
Anyone else has this tuner?  I am at a loss why David is still having issue.  Is it a issue with analog tuner support in the newer Mythtv releases?

---

