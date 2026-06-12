---
title: "[SOLVED] problem getting channel listing from schedulesdirect"
date: 2008-08-18
forum: Mythbuntu
---

### Post by boon2 on 2008-08-18
Hello,

I've been trying hard, really hard (really) to get a new Mythbuntu system up and seem to be running into brick walls left and right.  I'm hoping someone here can throw me a lifeline and get me on the right track.  

I've installed Mythbuntu 8.04.1, for the time being, on an Asus P5GZ-MX mobo w/ Intel 945GZ chipset, Intel Core2 4300 @ 1.80GHz , 1.5G RAM, ChainTech GEForce 7600 PCIe-16 (restricted Nvidia drivers installed), 40G PATA.

Capture card:
Hauppauge PVR-150 (non MCE) with IR receiver/blaster and silver, 45 key remote.
dmesg | grep ivtv  :
[SIZE="1"][   28.486604] ivtv:  Start initialization, version 1.1.0
[   28.488241] ivtv0: Initializing card #0
[   28.488246] ivtv0: Autodetected Hauppauge card (cx23416 based)
[   28.577487] ivtv0: Autodetected Hauppauge WinTV PVR-150
[   28.577489] ivtv0: Reopen i2c bus for IR-blaster support
[   28.776025] tuner 0-0061: chip found @ 0xc2 (ivtv i2c driver #0)
[   29.010030] cx25840 0-0044: cx25843-24 found @ 0x88 (ivtv i2c driver #0)
[   29.061407] wm8775 0-001b: chip found @ 0x36 (ivtv i2c driver #0)
[   29.070828] ivtv0: Registered device video0 for encoder MPG (4096 kB)
[   29.070847] ivtv0: Registered device video32 for encoder YUV (2048 kB)
[   29.070866] ivtv0: Registered device vbi0 for encoder VBI (1024 kB)
[   29.070885] ivtv0: Registered device video24 for encoder PCM (320 kB)
[   29.070887] ivtv0: Initialized card #0: Hauppauge WinTV PVR-150
[   29.070901] ivtv:  End initialization
[   49.980688] ivtv0: Loaded v4l-cx2341x-enc.fw firmware (376836 bytes)
[   50.179532] ivtv0: Encoder revision: 0x02060039[/SIZE]

Ultimately I'd like to hook my cablebox into the system, but for now I'm attempting the "simple" approach of just going from the cable coming out of the wall right into the co-ax connector on the PVR-150.

Presently I'm able to "Watch TV".  I.e. a signal comes through, I can change the volume using F10 and F11 (although it seems awfully low), I can tune channels when I press the numbers on the keyboard (I haven't wrangled with the remote/lirc yet -- not looking forward to it)

So although some things seem to be working fine, the real problem is that I just can't get anything going with SchedulesDirect.  When I scan channels, the scanner seems to recognize that there are signals coming through for channels 2-98 (which is what I'd expect for just being hooked in from the wall), but it doesn't bring down any channel names.  Instead, what I get is something to the effect of:
(Unamed : 1034)(34)(Schedules Direct)
(Unamed : 1035)(35)(Schedules Direct)
(Unamed : 1036)(36)(Schedules Direct)
(Unamed : 1037)(37)(Schedules Direct)
etc.  

Can anyone tell me why this might be happening?  

Any help greatly appreciated.  
Thanks,
Rob

---

### Post by newlinux on 2008-08-18
have you run mythfilldatabase? Have you gone to schedules direct and setup the appropriate lineup and selected the channels you receive?

---

### Post by boon2 on 2008-08-19
> Have you gone to schedules direct and setup the appropriate lineup and selected the channels you receive?

Thanks so much.  I'm embarrassed that I overlooked something so simple.  Just needed to log into schedulesdirect, pick a lineup, then went back into mythbuntu and the channels came down, then ran mythfilldatabase... everything seems to have gone well.

Now it's on to getting the cablebox into the mix and then getting the remote and IR blaster going.  Yikes!

Thanks again for the help.

Rob

---

### Post by newlinux on 2008-08-19
No problem. There are lots to things to keep track of and do. No need to be embarrased. The only thing that separates me from you in this is just that I've done it before  and made the mistakes and omissions already :)

---

