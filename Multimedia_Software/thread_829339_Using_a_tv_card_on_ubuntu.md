---
title: "Using a tv card on ubuntu"
date: 2008-06-14
forum: Multimedia Software
---

### Post by ats51 on 2008-06-14
I am trying get one of my tv cards working with ubuntu and i am struggling as to what to do. i have both an hauppauge model and an adaptec model to choose from yet i am unable to get either to work.

my research has shown that it is possible to get a tv card working but i am really struggling on this front. i am not sure if mythtv is what i want as i just want to watch live tv and tvtime doesn't seem to support ivtv. anyway i cannot seem to get ivtv to install properly. i seem to have tied myself up in a knot with this one.

is anyone is able to help me out, recommend me a program to use and how to get ivtv running properly then it would be most appreciated.

---

### Post by saedelaere on 2008-06-15
> **ats51 said:**
> I am trying get one of my tv cards working with ubuntu and i am struggling as to what to do. i have both an hauppauge model and an adaptec model to choose from yet i am unable to get either to work.

my research has shown that it is possible to get a tv card working but i am really struggling on this front. i am not sure if mythtv is what i want as i just want to watch live tv and tvtime doesn't seem to support ivtv. anyway i cannot seem to get ivtv to install properly. i seem to have tied myself up in a knot with this one.

is anyone is able to help me out, recommend me a program to use and how to get ivtv running properly then it would be most appreciated.

Hi,

I'am developing a frontend for ivtv based tv-cards. 
[Here]("http://ubuntuforums.org/showthread.php?t=763698") you can find the corresponding thread.

But first of all you should tell us which tv-card you have. Therefor you could use the command:

```
sudo lspci -v
```

On my system this shows me among other things:
05:00.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
        Subsystem: Hauppauge computer works Inc. WinTV PVR 150
        Flags: bus master, medium devsel, latency 128, IRQ 22
        Memory at e4000000 (32-bit, prefetchable) [size=64M]
        Capabilities: [44] Power Management version 2

Now perhaps your device is already working correct. Show us the output of:

```
dmesg | grep ivtv
```

On my computer this looks like:

```

dmesg | grep ivtv
ivtv:  Start initialization, version 1.2.1
ivtv0: Initializing card #0
ivtv0: Autodetected Hauppauge card (cx23416 based)
ivtv0: Unreasonably low latency timer, setting to 64 (was 32)
ivtv i2c driver #0: Test OK
ivtv0: Autodetected Hauppauge WinTV PVR-150
ivtv0: Reopen i2c bus for IR-blaster support
cx25840 1-0044: cx25842-24 found @ 0x88 (ivtv i2c driver #0)
tuner 1-0061: chip found @ 0xc2 (ivtv i2c driver #0)
wm8775 1-001b: chip found @ 0x36 (ivtv i2c driver #0)
ivtv0: Registered device video0 for encoder MPG (4096 kB)
ivtv0: Registered device video32 for encoder YUV (2048 kB)
ivtv0: Registered device vbi0 for encoder VBI (1024 kB)
ivtv0: Registered device video24 for encoder PCM (320 kB)
ivtv0: Initialized card #0: Hauppauge WinTV PVR-150
ivtv:  End initialization
ivtv0: Loaded v4l-cx2341x-enc.fw firmware (376836 bytes)
ivtv0: Encoder revision: 0x02060039

```
As you can see my video device node is video0.
Then you could use cat to test your video device node (if one exists):

```
cat /dev/video0 > test.mpeg
```

This should produce an mpeg video file in you users home directory. Since you did not to tune any channel prior to the cat command you'll only see some flicker in the video file. But in this case your tv-card works.
Now you could proceed to my frontend and use it to watch tv :)
In any case you should install tha package "ivtv-utils" via synaptics. If you want to use my frontend there some more dependences.

Regards 
Saedelaere

---

### Post by Return Privacy on 2008-06-16
ATS51,
You should try SageTv program. It works great with hauppauge tv cards. It allows you to record tv shows, or watch tv shows. You can get it with a remote control also. I know they have a linux version, a windoze version, and a mac version.

---

### Post by ats51 on 2008-06-17
i pumped out the commands you recommended:

sudo lspci -v came up with

02:0a.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 02)
	Subsystem: Hauppauge computer works Inc. WinTV Series
	Flags: bus master, medium devsel, latency 32, IRQ 20
	Memory at f47fe000 (32-bit, prefetchable) [size=4K]

02:0a.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 02)
	Subsystem: Hauppauge computer works Inc. WinTV Series
	Flags: bus master, medium devsel, latency 32, IRQ 20
	Memory at f47ff000 (32-bit, prefetchable) [size=4K]


while dmesg | grep ivtv came up with nothing

cheers for your help

---

### Post by saedelaere on 2008-06-20
Your card should work out of the box with TV-Time or KDETV

Regards

---

