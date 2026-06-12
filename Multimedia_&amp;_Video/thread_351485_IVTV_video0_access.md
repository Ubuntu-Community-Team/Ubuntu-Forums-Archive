---
title: "IVTV video0 access?"
date: 2007-02-02
forum: Multimedia &amp; Video
---

### Post by radtek on 2007-02-02
I just installed IVTV via the edgy 6.10 tutorial, and everything installed fine -- no errors.

The problem is that  the players seem unable to access the video, video1, video24 and video32 ?files?

I'm assuming that it is a permissions issue since it appears to mimic my printer woes. 

How do I enable the permissions (these files are read-only "root") and will this actually fix my problem?

Tvtime viewer states that (no signal)**there is no such file or directory cannot open capture device /dev/video0**

As far as I can see video0 is not listed in the device manager under my Hauppage pvr150 pci card.

---

### Post by radtek on 2007-02-02
I thought I'd show this too:

```
radtek@ubuntu:~$ dmesg | tac | sed -n '/=\ \ END INIT IVTV\ \ =/,/= START INIT IVTV =/p;/= START INIT IVTV =/q' | tac
[17180452.160000] ivtv:  ==================== START INIT IVTV ====================
[17180452.160000] ivtv:  version 0.7.0 (tagged release) loading
[17180452.160000] ivtv:  Linux version: 2.6.17-10-386 mod_unload 486 REGPARM gcc-4.1
[17180452.160000] ivtv:  In case of problems please include the debug info between
[17180452.160000] ivtv:  the START INIT IVTV and END INIT IVTV lines, along with
[17180452.160000] ivtv:  any module options, when mailing the ivtv-users mailinglist.
[17180452.268000] ivtv0: Autodetected Hauppauge WinTV PVR-150 card (cx23416 based)
[17180452.268000] ACPI: PCI Interrupt Link [APC2] enabled at IRQ 17
[17180452.268000] ACPI: PCI Interrupt 0000:02:09.0[A] -> Link [APC2] -> GSI 17 (level, low) -> IRQ 225
[17180452.272000] ivtv0: Unreasonably low latency timer, setting to 64 (was 32)
[17180452.328000] tveeprom 2-0050: Hauppauge model 26052, rev G1B2, serial# 8830361
[17180452.328000] tveeprom 2-0050: tuner model is TCL M2523_5N_E (idx 112, type 50)
[17180452.328000] tveeprom 2-0050: TV standards NTSC(M) (eeprom 0x08)
[17180452.328000] tveeprom 2-0050: audio processor is CX25843 (idx 37)
[17180452.328000] tveeprom 2-0050: decoder processor is CX25843 (idx 30)
[17180452.328000] tveeprom 2-0050: has no radio, has IR remote
[17180452.416000] tuner 2-0061: chip found @ 0xc2 (ivtv i2c driver #0)
[17180452.696000] cx25840 2-0044: cx25843-23 found @ 0x88 (ivtv i2c driver #0)
[17180456.756000] cx25840 2-0044: loaded v4l-cx25840.fw firmware (16382 bytes)
[17180456.848000] wm8775 2-001b: chip found @ 0x36 (ivtv i2c driver #0)
[17180457.528000] ivtv0: loaded v4l-cx2341x-enc.fw firmware (262144 bytes)
[17180457.744000] ivtv0: Encoder revision: 0x02050032
[17180457.744000] ivtv0: Allocate DMA encoder MPEG stream: 128 x 32768 buffers (4096KB total)
[17180457.744000] ivtv0: Allocate DMA encoder YUV stream: 194 x 10800 buffers (2048KB total)
[17180457.744000] ivtv0: Allocate DMA encoder VBI stream: 120 x 17472 buffers (2048KB total)
[17180457.744000] ivtv0: Allocate DMA encoder PCM audio stream: 455 x 4608 buffers (2048KB total)
[17180457.744000] tuner 2-0061: type set to 50 (TCL 2002N)
[17180457.956000] ivtv0: Initialized Hauppauge WinTV PVR-150, card #0
[17180457.956000] ivtv:  ====================  END INIT IVTV  ====================

```

This might Help?

---

### Post by fenian on 2007-02-02
First make sure you have mplayer installed (it's in the repos).Then try to capture some video with this command

cat /dev/video0 > /tmp/test_capture.mpg

wait like 5 seconds and press <ctrl> + 'c' then try to play it back with this command

mplayer /tmp/test_capture.mpg

Also tvtime does not work with the ivtv driver.You have to use mplayer or another video app. I
would recommend trying to set up mythtv to get the most out of your tv tuner.

---

### Post by fenian on 2007-02-02
Also to check that ivtv is initialized  type 

dmesg |grep Initialized

You should see an output like this

ivtv: Initialized WinTV PVR 150, card #0

---

### Post by radtek on 2007-02-02
The card and ivtv drivers seem to have been installed correctly. I've had trouble accessing devices since I did a fresh alt install of edgy 6.10. I'm running a sata RAID and I've put the root folder on a separate RAID partition. I have almost no permissions or access to files.

Is this because the /root partition and /home partition were installed separately? Should I do a fresh install and repartition to include / & /home on the same partition? 

                                   However the box is running so sweeet.

BTW  I installed myth tv and I'm having trouble- I think it has to do with permissions again.

I tried the front-end desktop- no go, then uninstall and reinstalled the front-end/backend pkg. But trying to create the ** /usr/share/xsessions/mythtv.desktop** I stalled out due to the permission issue. 

I'm still new at this. Aaaarg!

---

### Post by superm1 on 2007-02-02
> **radtek said:**
> The card and ivtv drivers seem to have been installed correctly. I've had trouble accessing devices since I did a fresh alt install of edgy 6.10. I'm running a sata RAID and I've put the root folder on a separate RAID partition. I have almost no permissions or access to files.

Is this because the /root partition and /home partition were installed separately? Should I do a fresh install and repartition to include / & /home on the same partition? 

                                   However the box is running so sweeet.

BTW  I installed myth tv and I'm having trouble- I think it has to do with permissions again.

I tried the front-end desktop- no go, then uninstall and reinstalled the front-end/backend pkg. But trying to create the ** /usr/share/xsessions/mythtv.desktop** I stalled out due to the permission issue. 

I'm still new at this. Aaaarg!
Sounds to me like you are missing a video group.
So your permissions for /dev/video0 don't show up like this right:
```
crw-rw---- 1 root video 81, 0 2006-12-23 21:04 /dev/video0
```
If this is the case, did you do something out of the ordinary for your install?  Like choose expert mode or anything?

---

### Post by radtek on 2007-02-02
[B]What is the command to pull up that code?
[/B]
I used the alternate CD so I could set up my RAID and did it in text mode. I don't recall seeing anything related to expert mode.

I hope a reinstall isn't in the future!

---

### Post by superm1 on 2007-02-02
> **radtek said:**
> [B]What is the command to pull up that code?
[/B]
I used the alternate CD so I could set up my RAID and did it in text mode. I don't recall seeing anything related to expert mode.

I hope a reinstall isn't in the future!
```
ls -l FILE
```
will show you the permissions for FILE.  so 
```
ls -l /dev/video0
```

How about this, do you have have udev installed?  It should have installed off the alternate disk, and it creates a file 
```
/etc/udev/rules.d/40-permissions.rules
```
Which sets the permissions for all the devices in /dev/.

```
dpkg -l | grep udev
```
should turn out something like this.  Particularly important is the ii (which means installed)
> ii  udev                                       093-0ubuntu18.0edgy2                 rule-based device node and kernel event mana


---

### Post by radtek on 2007-02-03
I tried the commands:

```
radtek@ubuntu:~$ ]**ls -l /dev/video0**
```

which returned:

```
crw-rw---- 1 root video 81, 0 2007-02-02 03:35 /dev/video0
```

Then grepped:

```
radtek@ubuntu:~$ **dpkg -l | grep udev**
```

which returned:

```
ii  udev     093-0ubuntu18.0edgy2      rule-based device node and kernel event mana
```

Do I need to **chown** the **video0** file? What else and how?

---

### Post by superm1 on 2007-02-03
> **radtek said:**
> I tried the commands:

```
radtek@ubuntu:~$ ]**ls -l /dev/video0**
```which returned:

```
crw-rw---- 1 root video 81, 0 2007-02-02 03:35 /dev/video0
```Then grepped:

```
radtek@ubuntu:~$ **dpkg -l | grep udev**
```which returned:

```
ii  udev     093-0ubuntu18.0edgy2      rule-based device node and kernel event mana
```Do I need to **chown** the **video0** file? What else and how?
Permissions on the video file are set up properly.  It is set so that anyone in the "video" group can capture content.  Next thing is to check who is in the video group.  If you are using mythtv, the mythtv user needs to be in this.  If you are just trying to capture from your regular user name, add them in.  Log out and back and permissions will take effect.

Here is what I see on my box:
```
supermario@portablemario:~$ cat /etc/group | grep video
video:x:44:supermario,mythtv

```

---

### Post by radtek on 2007-02-03
OK so far so good. This what I did:

** sudo gedit /etc/group**

And added some apps to the video line.

command returned:

```
radtek@ubuntu:~$ cat /etc/group | grep video
**video:x:44:radtek,tvtime,ivtv,vlc,zapping,camorama**

```

Logged out and tried tvtime. It returned **ivtv:invalid argument**

vlc seemed to be streaming something but I couldn't hear or see anything. The others-nothing.

Did I do this wrong?

---

### Post by fenian on 2007-02-03
TVTime wont work with the Hauppauge 150 or ivtv (it doesn't support mpeg decoders)..

[http://tvtime.sourceforge.net/cards.html](http://tvtime.sourceforge.net/cards.html)

You can use mplayer or xine to watch tv but you wont be able to tune channels natively,to do that you'll need mythtv or freevo.

---

### Post by radtek on 2007-02-03
Downloaded freevo and I'm a little confused on how to get xine or mplayer to play live TV. I've looked around and even tried editing the ** ~/.freevo/local_conf.py**

Xine wants a **channel.conf**. 

BTW ```
**scantv**
``` returns:

(this is only part of it)

```
57   (420.00 MHz): ???
[unknown (57)]
channel = 57

58   (426.00 MHz): ???
[unknown (58)]
channel = 58

59   (432.00 MHz): Discovery Health - Rlt
[Discovery Health - Rlt]
channel = 59

60   (438.00 MHz): ???
[unknown (60)]
channel = 60

```

So at least I know the card is working and getting a signal. 

What exactly to do to get some darn live TV?

BTW thanks for all the great help so far!

---

### Post by superm1 on 2007-02-03
> **radtek said:**
> OK so far so good. This what I did:

** sudo gedit /etc/group**

And added some apps to the video line.

command returned:

```
radtek@ubuntu:~$ cat /etc/group | grep video
**video:x:44:radtek,tvtime,ivtv,vlc,zapping,camorama**

```Logged out and tried tvtime. It returned **ivtv:invalid argument**

vlc seemed to be streaming something but I couldn't hear or see anything. The others-nothing.

Did I do this wrong?
Whoops I think you misunderstood my previous comment.  Your supposed to add users to that video group, not apps.  I have two user names, "supermario" and "mythtv"

---

### Post by radtek on 2007-02-03
OK, well freevo is a user, like mythtv?

What is my next step?

---

