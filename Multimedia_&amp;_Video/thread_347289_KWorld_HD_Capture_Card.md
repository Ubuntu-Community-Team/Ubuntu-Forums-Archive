---
title: "KWorld HD Capture Card"
date: 2007-01-27
forum: Multimedia &amp; Video
---

### Post by wiz561 on 2007-01-27
Hi!

    I picked up a Kworld ATSC-110 Digital/Analog HDTV Tuner PCI card tonight for my mythtv box.  I'm running Ubuntu 6.06 LTS with the AMD64-K8 kernel.  I chose this card because it sounded like it would be easy to install following the directions on the mythtv wiki.

    But...I'm having some problems.  I can't get it to work!  I *think* that my problem might be that the card comes up as '0' when I have read it should =90....but I don't know how to set it.  I tried to do it in the /etc/modules file with

saa7134 card=90
saa7134-dvb 
saa7134-alsa  

Here is the output of dmesg.  Also, I have a Hauppauge PVR card as well in the box.  I don't think this would matter, but maybe it does.  Any help is greatly appreciated.  


Thanks,
Mike

----dmesg----
   29.888870] Linux video capture interface: v1.00
[   29.989140] saa7130/34: v4l2 driver version 0.2.14 loaded
[   30.013953] input: PC Speaker as /class/input/input2
[   30.042861] ivtv: no version for "struct_module" found: kernel tainted.
[   30.044079] ivtv:  ==================== START INIT IVTV ====================
[   30.044082] ivtv:  version 0.4.6 (tagged release) loading
[   30.044084] ivtv:  Linux version: 2.6.15-27-amd64-k8 SMP preempt gcc-4.0
[   30.044086] ivtv:  In case of problems please include the debug info between
[   30.044087] ivtv:  the START INIT IVTV and END INIT IVTV lines, along with
[   30.044089] ivtv:  any module options, when mailing the ivtv-users mailinglist.
[   30.101083] nvidia: module license 'NVIDIA' taints kernel.
[   30.246442] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[   30.471076] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 19
[   30.471084] GSI 20 sharing vector 0x62 and IRQ 20
[   30.471092] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 19 (level, low) -> IRQ 98
[   30.471099] saa7133[0]: found at 0000:01:00.0, rev: 240, irq: 98, latency: 64, mmio: 0xfbfff800
[   30.471105] saa7133[0]: subsystem: 17de:7350, board: UNKNOWN/GENERIC [card=0,autodetected]
[   30.471120] saa7133[0]: board init: gpio is 100
[   30.602163] NET: Registered protocol family 17
[   30.609392] saa7133[0]: i2c eeprom 00: de 17 50 73 ff ff ff ff ff ff ff ff ff ff ff ff
[   30.609400] saa7133[0]: i2c eeprom 10: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   30.609407] saa7133[0]: i2c eeprom 20: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   30.609414] saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   30.609420] saa7133[0]: i2c eeprom 40: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   30.609427] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   30.609433] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   30.609439] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   30.609594] saa7133[0]: registered device video0 [v4l2]
[   30.609609] saa7133[0]: registered device vbi0
[   30.610014] ivtv0: Autodetected WinTV PVR 150 card (cx23416 based)
[   30.610586] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 18
[   30.610592] GSI 21 sharing vector 0x6A and IRQ 21
[   30.610598] ACPI: PCI Interrupt 0000:01:01.0[A] -> Link [LNKB] -> GSI 18 (level, low) -> IRQ 106
[   30.625019] saa7134 ALSA driver for DMA sound loaded
[   30.625049] saa7133[0]/alsa: saa7133[0] at 0xfbfff800 irq 98 registered as card -1
[   30.716753] tveeprom: ivtv version
[   30.716757] tveeprom: Hauppauge: model = 26132, rev = F0B2, serial# = 9405859
[   30.716760] tveeprom: tuner = TCL M2523_5N_E (idx = 112, type = 50)
[   30.716762] tveeprom: tuner fmt = NTSC(M) (eeprom = 0x08, v4l2 = 0x00001000)
[   30.716765] tveeprom: audio processor = CX25841 (type = 23)
[   30.716766] tveeprom: decoder processor = CX25841 (type = 1c)
[   30.716769] ivtv0: i2c attach to card #0 ok [client=tveeprom, addr=50]
[   30.766818] tuner (ivtv): chip found at addr 0xc2 i2c-bus ivtv i2c driver #0
[   30.766823] ivtv0: i2c attach to card #0 ok [client=(tuner unset), addr=61]
[   30.905000] cx25840 1-0044: ivtv driver
[   30.905003] cx25840 1-0044: cx25841-23 found @ 0x88 (ivtv i2c driver #0)

---

### Post by Vincent_Lin on 2007-01-29
Hi,

I have the same card.  It took me a while to have it working properly with mythtv. 

However, I am using 6.10 instead of 6.06.  For 6.10, the card driver is included in kernel.  So it is recognized right after 6.10 installation.  For me, all I need to add is putting saa7134-dvb in /etc/modules to enable ATSC receiving.  Oh, you still have to manual downlaod nxt2004 firmware as well(see documentation in linuxtv.org).  I do not care about NTSC recieving, so I do not include saa7134-alsa line in that file.

For 6.06, I think you have to download dvb driver and others from linuxtv.org, compile, and install it so that dvb driver of ATSC-110 is enabled.  Then it will be recognized during boot, and then do as I did/described above.

I don't know what motherboard/soundcard you have.  For them to work together, you might have to specify some options for alsa driver so that your actual hardware configuration(such as optical output) is recognized.  

After Kworld driver (from linuxtv.org) and audio driver (from alsa-project.org) are installed and configured properly, then all the setup steps in mythtv would work(would make sense).  

Another issue I had was VGA card and the link to TV.  It was resolved as well.  I am running latest NVidia driver for my 6800 with HDTV output (I use component dangle) 
connecting to my TV, which accepts only component input in HDTV.

My myth box only receives ATSC signals, therefore I don't load saa7134-alsa module.  This module enables receiving audio signals in NTSC broadcasting. 

I still have other issues, such as xvmc is not working at all for live TV/recorded TV, AC3 passthrough is broken, and TV program input is broken, etc...  I haven't tried QAM for my Comcast cable programs, since I believe saa7134-alsa is involved with QAM receiving.  But at least, I can watch live ATSC programs, record any of them ( by means of over-the-air program information, I think), and best yet, watch any video clips (from DV or ripped DVD), and photo slideshows.  That's GOOD ENOUGH for my kids and for my wife to justify the cost of this PC.

Vincent

---

### Post by wiz561 on 2007-01-29
Thanks for the information.  I upgraded to 6.10 and it did recognize the card and had no problems with it.  The hardest thing was figuring out that in order to pick up the HD on the cable end (with them using qam256), you had to plug it into the other coax connector on the card.

So far, things are running smooth, but I remember why I didn't upgrade to 6.10 earlier.  I had problems with my Hauppauge card always crashing myth.

I'm curious, I know this is slightly off-topic, but do you get regular cable (2- about 99) on your kworld card, or do you just use it for over the air.  Reason why I ask is because if I can do regular cable and hd cable with the kworld card, I might just yank my Haupaauge from the box so I don't have to go through the headaches of myth locking.

Also, another question, what sort of problems did you have with your video card?  I'm using a nvidia card with the HD dongle for the component cables.  So far, I haven't had a MAJOR problem.  Just wondering if you happened to run into any problems with it.

Thanks again for the info...
Mike

---

### Post by Vincent_Lin on 2007-01-30
Mike,

Looks like your setup is very similar to mine, except additional Hauppauge (that I don't have), and your intention to receive cable in qam256(which I have not).

My Comcast is for kids for their OnDemand kids stuff.  However, my wife does not like it becasue it gives them (4 and 2 years old girls) more programs than they should have spent time on.  Our intention is to stop Comcast cable service if over the air gives us "enough" kids programs.  Looks like it is happening.  Plus, we get some great HD programs through local NPR programing as bonus.

I think, though I did not thouroughly go though it, if you want ATSC-110 to receive NTSC(analog) programs with proper audio, you need to load saa7134-alsa.  OTA ATSC programs does not require loading of saa7134-alsa, which I don't have it in /etc/modules, as expected.

My problem with NVidia/xvmc is that, when enabled with bob deinterlace, I experience autio stutter and drop of frames all the time.  Audio sounds like fast-forwarding when not stuttered.   However, this "bad" behaviour only happens on live TV and recorded TV programs.  I have Core Duo 2.13GHz machine so I simply use Standard setting (which is xv video I believe) for Replay, with Kernel deinterlace.  The outcome 1920x1080 is perfect to my eyes anyway.  So, if you have a relatively fast machine, don't bother to try it, though there are some success stories out there.

yet, I can still enable xvmc for viewing regular mpeg2, vob, and others using mplayer with -vo xvmc -vc ffmpeg12mc (I think) options.  I also use -monitoraspect 16:9 option to specify TV aspect ratio so that all video clips are played with correct aspect ratio.

I use the same HD dangle with component out to connect to my TV, as what you are doing.  It took me awhile to figure out that I can simple specify "1920x1080" mode without modeline denifition in xorg.conf.  When it is correctly specified, it feels like miracle to me that "it works".

Overscan is another area that needs to be tweaked.  I know there is a way to change overscan on the TV itself by going into service menu of the TV set.  People say that after adjusting overscan (to reduce overscan so that the display image is smaller and the whole 1920x1080 is viewable on TV) the picture is actual much better since all dots are more compact/close together, but I will wait until I have time and TV is not going to be watched for a prolonged period of time (say wife and kids are on vacation without me).  NVidia driver simply ignores Overscan option in xorg.conf.  So the only solution for now is to adjust mythtv gui dimension and position.  I have to cut down gui size to ~1750x850 or so so that I almost get all the corners of images.  wiki pages in mythtv.org say that this setup would require some cpu burden - not a good setup if your cpu is not fast enough.  Also it might be related to my audio/stutter problem when xvmc is enabled.

As to how disabling AC3 passthrough but leaving DTS passthrough enabled works, I have not idea at this moment.  It might be related to alsa driver setup but I really have no intention to change anything at this moment, since everything audio related works - rear analog audio output to TV set itself, rear optical audio out to stereo receiver, and front haedphone jack to a wireless headphone (so that I can watch Jay Lenon QUIETLY without disturbing girls), I am pretty happy now.

That's about it.  Glad to know I am not the only one running mythtv on ubuntu with Kworld ATSC-110 and NVidia card using component output.

Vincent

---

### Post by wiz561 on 2007-02-01
Thanks for the responses.

I've been toying with the idea to go back to 6.06 LTS.  I'm starting to think that upgrading to 6.10 was a headache...and in another couple of months, I will just have to go through it all again.  So, I don't know if I should just continue forward to work through my 6.10 problems or go back to 6.06.

My main problem with 6.06 was that when I compiled the video4linux drivers in order to detect the KWorld card...because the v4l included in Dapper 6.06 isn't updated to detect the card.  But anyways, when I compiled it following these directions...

[http://www.linuxtv.org/v4lwiki/index.php/How_to_build_from_mercurial](http://www.linuxtv.org/v4lwiki/index.php/How_to_build_from_mercurial)

Ubuntu crashed and wouldn't boot back up.  I had to boot using the recovery kernel and make uninstall to remove v4l.  Rebooted and things were fine again.

Now I know people like logs and to see why it didn't work....but I just wiped my system and put edgy on.  Now that I'm there with edgy...i have an uneasy feeling about things.

I would like to get the remote for the kworld working...adn even though I haven't tried it, from what I read, it looks like I will have to compile from cvs/mercurial.   Or, go back to 6.06, have my PVR-150 tuner card working again, recompile v4l, and have two (or three) tuner cards available to me.  Right now, the PVR-150 doesn't work with edgy on amd64 dual-core.  But back in Dapper, it worked fine.

I hope you see my delimma.  Any help or guidance would be appreciated!!!


Thanks,
Mike

---

### Post by Vincent_Lin on 2007-02-01
Mike,

linuxtv.org has an email list called video4linux-list provided by redhat.  This list has a discussion lately(up to today) about our KWorld ATSC-110, as well as some more discussion about patch of Kworld ATSC-110 remote into dvb driver.

Sorry I could not even upderstand a bit about what they are talking about.  You might be able to google to get some sites that hosts the threads.  Or simply subscribe to it, if you are interested.  

However, reading through makes me appreciate their efforts, including general Open Source Community, even more.

Thanks to all these hard working guys!!


Vincent

---

### Post by wiz561 on 2007-02-02
Please help before I put my fist through the television!

I wiped everything and started from scratch again because I was having too many problems.  I ripped my Hauppauge PVR-150 out because it was giving me issues with the ivtv.ko driver.  When it would load, the box would crash.  But that's neither here nor there.

I would like to use the ATSC-110 card, both HD and Analog inputs for mythtv.  This is getting to be a rather huge challenge!  I got this working...to a degree...  My only last major issue is that the sound doesn't work.  

If I play something through the sound card, it works fine.  But as soon as I go into mythtv, it doesn't work at all.  I had it working so that it would output it through the sound card to my receiver for ac3...but now that doesn't even work since I re-installed everything.

Vincent, it sounds like we have extremely similar setups.  I have a 'card 0: NVidia [HDA NVidia], device 0: ALC883 Analog [ALC883 Analog]' sound card and trying to get everything to work correctly with Edgy now.

Is there a particular web site that you followed to set everything up correctly?  Also, I believe you said that you didn't use the analog cable part of the card.  Did you happen to set it up?  Also, in order to pass the soudn through the pci bus instead of the loop thing, do you have to connect any audio wires from the card inside the case to the soundcard, similar to how a cdrom works?

Thank you for any help.

Mike

---

### Post by Vincent_Lin on 2007-02-05
Mike,

I feel your pain.  Imagine I built this machine last June, and I only started enjoying what mythtv offers weeks ago.

Regarding your question:
1. I did not follow any specific howto to get everything going.  But, I followed many howtos to pick up some ideas here and there.
    I had a couple of false starts - 6.06 is one, mythtv 0.18, 0.19 are two more. 
    ivtv was another one when I did not know what driver I should pick, since 6.06 did not come with dvb driver for ATSC-110.
2. Since Edgy, mythtv is so easy to install.  I use Edgy repository's mythtv debs to install.
3. I frequently go to mythtv.org, alsa-project.org, linuxtv.org, linux1394.org mplayerhq.hu, and nvnews.net and their forums, just to pick up some in depth information.
4. But, boy, ubuntuforums.org is the best place where I get all the pointers and info that help greatly for my setup.
5. I did not even try to setup analog TV stuff, qam or NTSC.  I tried tvtime, but no audio.  It's analog NTSC.
6. There is no connecting wires from ATSC-110 to audio input port of my machine.
7. To make it clear, when I ran tvtime (no audio), I can get audio by connecting audio-out on ATSC-110 to audio-in port of of my Asus MB, using that short cable included in ATSC-110 box.

My setup - 
system/hardware --
Asus N4L-VM motherboard
                     Socket 478 (I use Core Duo T2600)
                     Realtek ALC 882M audio (also called Intel HDA) (rear 5.1 + Optical out, front headphone)
                     Intel GMA 950 not used, instead I put in NVidia 6800 with HDTV out dangle, I use component video
                     JMicron SATA controller - I had 300 GB HD, plan to add another 500GB HD
ubuntu 6.10 Edgy, ubuntu stock kernel
mythtv .020
Kworld ATSC-110 ( I actually bought 2 cards, but last time I tried to use both failed. )
                           (Not knowing what happened, I put 1 card in only this time.)
                           (Definitely I will try to put both cards in sometime in the future)
                           (As you already know, remote is not working yet.)  
                           (Don't mention what will happen with two cards and two remotes.)
mplayer - I downloaded source, and compiled it with xvmc support
NVidia - latest released driver, with xvmc support enabled. 
I used automatix to install all multimedia codecs.

Software configuration --
Your audio device is different from mine, I think you would have to do something about it.  
1 - I went to alsa-project.org downloaded alsa source, compiled and installed it.  
2 - In /etc/modules I have snd-hda-intel
3 - I put Options snd-hda-intel model=digital-3stack or something like that,in file /etc/modprobe.d/alsa-base.
     You can search ubuntuforums to find more information about this model.  Very critical step to get my sound working.
4 - Then I have to run alsamixer and unmute digital channel, escape, 
     and run $sudo alsactl store 0 to store the the setting, since alsa defaults to mute some channels of the output.

Finally, in mythtv, I have DTS passthrough checked, but leaving AC3 passthrough unchecked.  Internal mixer unchecked.
I also use mplayer for all video playing except DVD, which I use internal (myth DVD) player, for the purpose to get top menu.
mplayer is using -vo xvmc when playing mpeg2 files, including vob, mpeg, etc...
mplayer is using -vo xv when playing avi, divx, or dat (VCD stuff) files.
To be frank with you, I am not sure what mythtv is using to play live TV and recorded TV.  I don't think it is mplayer.
I enabled OpenGL effect so that photo slideshow transition effects make my girls very happy.


Vincent

---

