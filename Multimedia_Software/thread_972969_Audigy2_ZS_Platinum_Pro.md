---
title: "Audigy2 ZS Platinum Pro"
date: 2008-11-06
forum: Multimedia Software
---

### Post by Yashiro on 2008-11-06
I am currently using one of these on Ubuntu 8.04.
[http://www.tomshardware.com/reviews/dts-7,691.html](http://www.tomshardware.com/reviews/dts-7,691.html)

I have sound but to be honest it's very basic and the volume even at max is pretty quiet. 
The operating system mixers (alsa and gnome gui) seem to list the vast majority of the ports it provides.


Are there any ways to fix the following:

1 - Low volume. Even with all outputs on Max.
2 - The hardware volume knob on the break out box. And it's mute function.
3 - The infra-red sensor and remote control on the break out box.
4 - The CMSS 3D enable/disable button on the break out box, and the associated audio effects.


Specific fixes for these, or some pointers on where I could possibly get more audigy related help would be appreciated.

Thanks.

---

### Post by tinman6700 on 2008-12-06
I am having the same problem. I have run UUE1.4 on a dell laptop for a long time, with few issues. Now I have installed 1.8 on my main desktop, and I am having a horrible time with it. I have the audigy 2zs, with breakout box, I also have Hauppauge wintv-radio.(I went to 1.8 'cause I couldn't find 1.4 for download) My computer is my bedroom TV, and the sound system for my entire apt, so needless to say, I REALLY want ho get this stuff working. If I can't get this stuff worked out, I'll be switching back to XP.

---

### Post by Yashiro on 2009-01-15
Small bump.

---

### Post by Yashiro on 2009-02-03
Anyone with any pointers on enabling the external volume control on the break out box?

---

### Post by Yashiro on 2009-04-02
> Audigy 2 Platinum EX

Infrared remote control and MIDI in/out on Audigy 2 ZS pro and Audigy 4 pro.

There is an issue with the Audigy 2 Platinum Ex soundcard and the Audigy 4 pro (and probably some other Audigy 2 cards as well), whereas the IR sensor, MIDI and the buttons on the LiveDrive do NOT work at all until the LiveDrive is initialized by sending the sequence of '0xf0, 0x00, 0x20, 0x21, 0x61, 0x0, 0x00, 0x00, 0x7f, 0x0, 0xf7' to the MIDI port. Before doing this, even the LED on the LiveDrive won't blink, as it usually does when a button on the remote is pressed. As far as I know, this behaviour is different than with most LiveDrives manufactured by Creative. For more information see this link. The easiest workaround to this is to add the following line to /etc/modules.conf

post-install snd-emu10k1

echo -e '\360\000\040\041\141\000\000\000\177\000\367' > /dev/snd/midiC0D1

If it doesn't work, try

echo -en "\xf0\x00\x20\x21\x61\x00\x00\x00\x7f\x00\xf7" > /dev/snd/midiC0D1

It works for me and it should be distribution-independent (with exception to Debian, where you change /etc/modutils/alsa and run update-modules afterwards, Debian users will know anyway).
Has anyone had any success with this method?

---

### Post by timos_m on 2009-11-02
> I am currently using one of these on Ubuntu 8.04.
[http://www.tomshardware.com/reviews/dts-7,691.html](http://www.tomshardware.com/reviews/dts-7,691.html)

I have sound but to be honest it's very basic and the volume even at max is pretty quiet.
The operating system mixers (alsa and gnome gui) seem to list the vast majority of the ports it provides.


Are there any ways to fix the following:

1 - Low volume. Even with all outputs on Max.
2 - The hardware volume knob on the break out box. And it's mute function.
3 - The infra-red sensor and remote control on the break out box.
4 - The CMSS 3D enable/disable button on the break out box, and the associated audio effects.


Specific fixes for these, or some pointers on where I could possibly get more audigy related help would be appreciated.

Thanks. 

I would really like to use Ubuntu but I am prevented from doing this because of the problem mentioned in this topic.Since I use my computer mostly for music listening and related tasks, and am very used to the CMSS 3D option, is there any possibility that the above mentioned things will be fixed? Is anybody working on them? After a search I've done I've seen that people who would be grateful if this was fixed are a lot. Is there any other place where I can  ask to know at least that it will never be fixed?

Thanks!

---

### Post by Menthu_Rae on 2009-11-19
Hey guys,

I have an Audigy2 ZS Platinum Pro, I've been using it since 8.10 Intrepid and it has worked fine (currently running 9.10 Karmic).

I do NOT use the IR remote, breakout box controls or CMSS3D... The remote would be handy but I'm not really fussed.

However, for everything else (5.1 output, AC3/DTS/DD5.1 output via SPDIF) it works superbly. Volume levels are fine in my experience.

I know this probably won't help anyone - but yeah - in my experience, the volume levels are fine (I output to a set of Logitech Z-680s) and all of the functionality I need (analogue and digital output, and analogue recording input) works fine. ;)

---

### Post by griadooss on 2009-11-22
Audigy Platinum eX -- I cannot record from the Line IN 2 / MIC 2 or AUX IN 2 jacks on the breakout box .... I have gone from Ubuntu 9.10 to Ubuntu-Studio 9.10 with no difference!!!

I can only find scant reference to this problem in google and in this forum .. and am wondering if it is just me!!!

The said jack ports are available in gnome-alsa-mixer and the sliders actually control output volume and balance when i either use a mic or guitar in either of the jack ports  ...... HOWEVER, these sources cannot be recored from as I cannot get any levels from them!!!

Can ANYBODY ..[somebody] ... give me the drum on this!! 

Help ... i am gonig nuts ... just about to give up!!!

Thnx 

GR

########################

System information report, generated by Sysinfo: 23/11/2009 12:07:31 AM
[http://sourceforge.net/projects/gsysinfo](http://sourceforge.net/projects/gsysinfo)

SYSTEM INFORMATION
    Running Ubuntu Linux, the Ubuntu 9.10 (karmic) release.
    GNOME: 2.28.1 (Ubuntu 2009-11-03)
    Kernel version: 2.6.31-9-rt (#152-Ubuntu SMP PREEMPT RT Thu Oct 15 05:01:14 UTC 2009)
    GCC: 4.4.1 (i486-linux-gnu)
    Xorg: unknown (26 October 2009  05:15:02PM)
    Hostname: bntws02
    Uptime: 0 days 1 h 28 min

CPU INFORMATION
    AuthenticAMD, AMD Athlon(TM) XP 3000+
    Number of CPUs: 1
    CPU clock currently at 2166.786 MHz with 512 KB cache
    Numbering: family(6) model(10) stepping(0)
    Bogomips: 4333.57
    Flags: fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mmxext 3dnowext 3dnow up

MEMORY INFORMATION
    Total memory: 1497 MB
    Total swap: 1655 MB

STORAGE INFORMATION
    SCSI device -  scsi0
        Vendor:  ATA      
        Model:  IC35L040AVVN07-0 
    SCSI device -  scsi0
        Vendor:  ATA      
        Model:  IC35L080AVVA07-0 
    SCSI device -  scsi1
        Vendor:  HL-DT-ST 
        Model:  DVDRAM GSA-H42N  
    SCSI device -  scsi1
        Vendor:  ATA      
        Model:  ST380011A        

HARDWARE INFORMATION
MOTHERBOARD
    Host bridge
        VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333]
        Subsystem: ASUSTeK Computer Inc. Device 807f
    PCI bridge(s)
        VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333 AGP]
    USB controller(s)
        VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 23)
        VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 23)
    ISA bridge
        VIA Technologies, Inc. VT8233A ISA Bridge
        Subsystem: ASUSTeK Computer Inc. Device 808c
    IDE interface
        VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06) (prog-if 8a [Master SecP PriP])
        Subsystem: ASUSTeK Computer Inc. Device 808c

GRAPHIC CARD
    VGA controller
        nVidia Corporation G73 [GeForce 7600 GS] (rev a2)

SOUND CARD
    Multimedia controller
        Creative Labs SB Audigy (rev 03)
        Subsystem: Creative Labs Device 0051

NETWORK
    Ethernet controller
        Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
        Subsystem: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+

NVIDIA GRAPHIC CARD INFORMATION
    Model name: GeForce 7600 GS
    Card Type: AGP 4x
    Video RAM: 512 MB
    GPU Frequency: 400 MHz
    Driver version: NVIDIA UNIX x86 Kernel Module  185.18.36  Fri Aug 14 17:18:04 PDT 2009

---

### Post by BobbyS on 2009-12-06
Hello,


Does anyone know how to connect the breakout box to the card? I have the breakout box with no instructions.


Thanks
BobbyS

---

### Post by kuritsubaji on 2010-01-21
>BobbyS,

You should have a long ribbon cable, similar to an IDE cable, that connects the front panel to the card.  The card should have only one connector with that architecture.  Match the red side of the connector to the arrows on the board/front panel and you should be in business.

...but that's not why I'm posting to this thread.

I too, have an Audigy2 ZS Platinum, and a clean install of 9.10 and I **had** output at the speakers and the front headphone jack, but just now, I booted up and silence.  So, I rebooted and I've got sound back. Doubleyoutee-EFF!?!  I had 8.10 on this machine (BYO) before and everything was working great.  I'm going to try and re-seat the card, but if this problem persists, I'll post back.

System:
EVGA nForce 750i SLI
Wolfdale E8400 3.0Ghz ~ OC'd @ 4.2Ghz
4Gb DDR2/1066Mhz ~ OC'd @ 1266Mhz
(2)BFG GTS 250 1Gb ~ SLI
(4)320Gb SATA 3.0Gb/s running Linux MD RAID 1+0

---

### Post by gkh73 on 2010-03-16
Would also love to get some answers to this!
I had 8.04 and the breakout box worked perfectly.  Now I can't use the headphones or mic output.  Le Sigh.

---

### Post by tinman6700 on 2012-09-11
> **Yashiro said:**
> Has anyone had any success with this method?

sorry noob question but how would one do this? is it a matter of simply running the script in a console?

---

