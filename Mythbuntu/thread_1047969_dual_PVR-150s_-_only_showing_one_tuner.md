---
title: "dual PVR-150s - only showing one tuner"
date: 2009-01-22
forum: Mythbuntu
---

### Post by 4ebees on 2009-01-22
Hi all.

I have the following setup:

Mythbuntu 8.04.1
P4 3Ghz
1.4G RAM
160G and 500G HDD
Two PVR-150 PCI Hauppauge tuners (though I think I've been sold a dud on one of them)
nVidia 128Mb RAM MX4000

TEAC TV - big bugger CRT

PAL (Australia) input

I get video to the telly through an s-video cable from the nVidia card to the RCA adapters on the telly. Sound is by an audio cable from the onboard sound-card to the RCA inputs on the telly.

I have an aerial splitter and have cable running to the aerial input for each of the tuners. However, I can only 'find' Tuner1 when I'm trying to set up the tuners themselves.

The tuners were installed prior to intalling M'bntu.

1. Would this appear to indicate that one of the tuners  (which I bought  off eBay) is dead, or is there some other way to tell what's going on?

2. Do I need an aerial for each tuner?

3. Can you only record one station per tuner?

Many thanks to anyone who can provide assistance or direct me to a thread I've missed which answers one or more of these questions.

Regards,

4ebees

---

### Post by ian dobson on 2009-01-23
Hi,

What do you see when you do lspci? You should see something along the line of this:-

```

00:00.0 Host bridge: Intel Corporation 82P965/G965 Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82P965/G965 PCI Express Root Port (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation Device 2833 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HB/HR (ICH8/R) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801H (ICH8 Family) 4 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801H (ICH8 Family) 2 port SATA IDE Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)]
01:00.1 Display controller: ATI Technologies Inc RV370 [Radeon X300SE]
02:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 03)
02:00.1 IDE interface: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 03)
03:00.0 Ethernet controller: Attansic Technology Corp. L1 Gigabit Ethernet Adapter (rev b0)
05:00.0 Multimedia controller: Philips Semiconductors SAA7146 (rev 01)
05:01.0 Multimedia controller: Philips Semiconductors SAA7146 (rev 01)
05:02.0 PCI bridge: Hint Corp HB6 Universal PCI-PCI bridge (non-transparent mode) (rev 11)
[B]06:08.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
06:09.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)[/B]

```

And a ls /dev/video* should show something like:-
```

/dev/video0  /dev/video1  /dev/video25  /dev/video26  /dev/video33  /dev/video34

```

Regards
Ian Dobson

---

### Post by 4ebees on 2009-01-23
Hi Ian,

Well: 
[B]01:00.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
01:01.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)[/B]


They're both here <scratches head>

ls /dev/video* provides:

**/dev/video0  /dev/video1  /dev/video24  /dev/video25  /dev/video32  /dev/video33**

It would appear I'm doing something wrong here. Unsurprisingly. This is my first successful - almost - Myth install and I've no idea about PVRs or tv tuners.

Any assistance/suggestions/mystical ;) incantations would be most appreciated :)

---

### Post by ian dobson on 2009-01-23
Hi,

OK you need to define a new MPEG-2 tuner (device number 1) and link it to your video input.

You can only record 1 channel per tuner, but when 2 tuners are installed you can record two channels at the same time.

Regards
Ian Dobson

---

### Post by dardack on 2009-01-23
There both there.  /dev/video0 and /dev/video1 are your 2 turners.  On pvr-150's you only get 1 channel per tuner, on pvr-500's you get 2 channels per tuner.  do :

```
cat /dev/video0 > file.mpg 
```

and let it run a few seconds and then view the mpg file, than do that for video1, should work (unless for some reason it's looking at composite and not the tuner but i think tuner is default).

[EDIT] Ian beat me to it.  In mythtv-setup define another tuner, you should already have one designated at either /dev/video0 or video1, make a new one that is the one you don't have defined.  What i think your getting confused with (and correct me if i'm wrong) is you see video0/1 and think video1 is the only one active, linux starts count at 0 not 1, so 0 is 1, 1 is 2nd tuner.  Anyways, hope you get it working, i have a machine with 2xpvr250,1xpvr500 so i actually have /dev/video0/1/2/3 and a hacked appletv as my frontend.  It rules.

---

### Post by 4ebees on 2009-01-23
Thanks Ian.

Please see my comment below.

---

### Post by 4ebees on 2009-01-23
Okely dokely you two.

Thanks for this. It's rather late here (kids in bed, wife going to bed, me finding time :))))

I'll run those commands and see what I get.

I'm not quite sure how to add the second tuner. What do I access to do this?

When I look in 'something' (can't recall, I'll have to get some time to look tomorrow) - the bit where you do the scanning for stations etc - I can only find tuner1

So tuner1 is assigned to /dev/video0 and video1 in my setup.

My apologies for being so unclear. Screenshots anyone? :)

I'll find some time tomorrow and get back to you both.

Your help is much appreciated.

---

### Post by dardack on 2009-01-23
Ok, in a terminal type:  mythtv-setup  then go to capture cards

[http://www.mythbuntu.org/files/images/7.10_mythtv-setup.preview.png]("http://www.mythbuntu.org/files/images/7.10_mythtv-setup.preview.png")

then click delete all capture cards (just so we can start fresh)

[http://img.photobucket.com/albums/v493/halo6819/Screenshot3.png]("http://img.photobucket.com/albums/v493/halo6819/Screenshot3.png")

Then click new capture card (same pic as above).

Card type select Mpeg-2 hardware or something like that (sorry i can't remember exact name).  Select video device as /dev/video0.

Click finish.

Click new capture card, select mpeg-2 hardware.  Select video device as /dev/video1.  

Click finish

Hit escape.

Now go to (if you already set up your video sources) input connections.  For the first one go to Tuner and set your tuner to your video source (need to do thise for both tuner's).  If you have cable (sorry not sure how aussie's work) you should set both tuners to the same source.

Click escape, click escape.  Run mythtvfilldatabase.  Then you should be all set.

---

### Post by 4ebees on 2009-01-24
Hokey, all done.

Can I ask one last question?

If I set up the box to record, say, Channel 10 and Channel 2 at the same time, it will do this without me choosing a tuner, no?

---

### Post by ian dobson on 2009-01-24
Hi,

As long as both tuners are in the same video input group then yes mythtv will pick the first available tuner.

Regards
Ian Dobson

---

### Post by 4ebees on 2009-01-24
> **ian dobson said:**
> Hi,

As long as both tuners are in the same video input group then yes mythtv will pick the first available tuner.

Regards
Ian Dobson

Thanks again, Ian. All appears good in the house of Mythbuntu :))


Many thanks to you and Dardack.

---

