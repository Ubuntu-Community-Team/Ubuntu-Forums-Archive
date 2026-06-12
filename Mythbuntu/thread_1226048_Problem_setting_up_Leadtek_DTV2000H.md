---
title: "Problem setting up Leadtek DTV2000H"
date: 2009-07-29
forum: Mythbuntu
---

### Post by creeda on 2009-07-29
Hi all,
I finally bit the bullet and built a HTPC, running Mythbuntu. The machine works fine, but I'm having problems with setting up my TV tuner :(  I've spent AGES searching and reading, no luck.  I'm running the latest Jaunty Jackalope mythbuntu with the vista compatible Leadtek Winfast DTV2000H Plus.  All the info I can find on this card is for older versions of Mythbuntu.

What I have done is to add "cx88-dvb" to /etc/modules, and created "options.conf" in /etc/modprobe.d, containing the line "options cx88xx card=76" (previous advice has been to put the line "options cx88xx card=51" in the file "/etc/modprobe.doptions", but it appears that this version of ubuntu requires all files to have .conf extension, and that "card=51 " points to the old(I) revision of this tuner card, while "card=76" is the new (J) version).

After restarting, MythTV tuner card section offers me the card as an analogue choice, but when I select 'DVB DTV capture card (v3.x) as the card type, the DVB Device # field is blank, and the Frontend ID is "Could not get card info for card #0".

Here is relevant output from a few commands:
```
>lspci | grep -i cx
01:06.0 Multimedia video controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
01:06.1 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [Audio Port] (rev 05)
01:06.2 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)
```

```
>lsmod | grep -i cx
cx22702                15236  0 
cx88_vp3054_i2c        11264  0 
cx88_alsa              21384  0 
cx8800                 45036  0 
cx8802                 27012  0 
cx88xx                 88104  3 cx88_alsa,cx8800,cx8802
...
```

```
>dmesg
...
[    6.020975] cx88/2: cx2388x MPEG-TS Driver Manager version 0.0.6 loaded
[    6.021745] cx88[0]: subsystem: 107d:6f42, board: WinFast DTV2000 H ver. J (new) [card=76,insmod option], frontend(s): 1
[    6.021747] cx88[0]: TV tuner type 63, Radio tuner type -1
[    6.067473] cx88/0: cx2388x v4l2 driver version 0.0.6 loaded
[    6.118298] cx2388x alsa driver version 0.0.6 loaded
[    6.156333] tuner' 0-0061: chip found @ 0xc2 (cx88[0])
[    6.215398] tuner-simple 0-0061: creating new instance
[    6.215402] tuner-simple 0-0061: type set to 63 (Philips FMD1216ME MK3 Hybrid Tuner)
[    6.216725] input: cx88 IR (WinFast DTV2000 H ver. as /devices/pci0000:00/0000:00:08.0/0000:01:06.2/input/input6
[    6.244561] cx88[0]/2: cx2388x 8802 Driver Manager
[    6.245083] cx88-mpeg driver manager 0000:01:06.2: PCI INT A -> Link[LNKA] -> GSI 17 (level, low) -> IRQ 17
[    6.245090] cx88[0]/2: found at 0000:01:06.2, rev: 5, irq: 17, latency: 64, mmio: 0xfc000000
[    6.245114] cx8802_probe() allocating 1 frontend(s)
[    6.245139] cx8800 0000:01:06.0: PCI INT A -> Link[LNKA] -> GSI 17 (level, low) -> IRQ 17
[    6.245145] cx88[0]/0: found at 0000:01:06.0, rev: 5, irq: 17, latency: 64, mmio: 0xfa000000
[    6.245207] cx88[0]/0: registered device video0 [v4l2]
[    6.245246] cx88[0]/0: registered device vbi0
[    6.246172] cx88_audio 0000:01:06.1: PCI INT A -> Link[LNKA] -> GSI 17 (level, low) -> IRQ 17
[    6.246195] cx88[0]/1: CX88x/0: ALSA support for cx2388x boards
[    6.252997] cx88/2: cx2388x dvb driver version 0.0.6 loaded
[    6.253001] cx88/2: registering cx8802 driver, type: dvb access: shared
[    6.253004] cx88[0]/2: subsystem: 107d:6f42, board: WinFast DTV2000 H ver. J (new) [card=76]
[    6.253007] cx88[0]/2: cx2388x based DVB/ATSC card
[    6.265962] cx22702_readreg: readreg error (ret == -6)
[    6.266023] cx88[0]/2: frontend initialization failed
[    6.266025] cx88[0]/2: dvb_register failed (err = -22)
[    6.266027] cx88[0]/2: cx8802 probe failed, err = -22
...

```

It looks like modules are loaded and the card is detected, but having an error when loading.  I can't find anything on this readreg error or dvb_register failed (-22).

Has anyone got any advice on how to fix this, or pointers to some resources to help me understand what is going on?
Thanks to anyone who gets to the end of this long post, any help would be greatly appreciated :D

---

### Post by laffinet on 2009-07-29
I'm running 9.04 with two DTV2000H rev. J cards.

My "/etc/modules" file contains this line:

```
cx88-dvb
```

I don't have a "options.conf" file, only a "options.dpkg-bak", which is probably not used.
However, it contains 
```
"options cx88xx card=51"
```
not "76". I used the same when I was running 8.04 and 8.10 and everything worked fine.

---

### Post by creeda on 2009-07-30
Hey mate, thanks for your response.  What you've said is consistent with what I've read all over the place.  However, it doesn't seem to work for me.

The reason for 'card=76' rather than 'card=51' is that when I looked at the dmesg output the first time it listed a bunch of cards with their numbers, and the very last one was: 'card=76 -> WinFast DTV2000 H ver. J (new)'.  Anyway I tried card=51 as well and it made no difference.  I know the option is being applied because the correct value can be found in /sys/module/cx88xx/parameters.

It is this message "cx22702_readreg: readreg error (ret == -6)" that is where the problems all begin, and i can't find any info on it.  Further searches show some recent messages mentioning a Revision K of this card; is this true?  I know it is at least J because it has 'certified for Windows Vista' on the box.  So I'm either doing something basic wrong, or this version K exists and is incompatible :(

Any help is valued greatly, I'm at a dead end and seems like the only answer is back to Windows MCE, don't make me do that :P

---

### Post by laffinet on 2009-07-30
Have you checked the card itself ? I think mine had "rev. J" on the PCB somewhere. Maybe check for that, might tell you what version you have.

---

### Post by creeda on 2009-08-10
For completions sake I'll post the outcome of my problem.  The all important character here is the '+' at the end of the DTV2000H.  The DTV2000H+ / DTV2000H Plus is very different to the non-plus version.  From what I can find, the plus version is the new model which is phasing out the older version.  It uses a different tuner which is not yet supported. 

[DTV2000H]("http://www.leadtek.com/eng/tv_tuner/specification.asp?pronameid=252&lineid=6&act=2") uses the Philips FMD1216 tuner, while [DTV2000H+]("http://www.leadtek.com/eng/tv_tuner/specification.asp?pronameid=458&lineid=6&act=2") uses the Xceive XC4000 tuner 

See [this blog]("http://www.kernellabs.com/blog/?cat=20") for progress on someone who is working on support of the XC4000 for Linux- its getting there, but could still take some time.

I managed to find old stock of the DTV2000H rev. J and have successfully got this working on my new machine.

---

### Post by ziadnahas on 2009-08-15
Have you head much success since your endeavor. Cause i was advised that Leadtek was generally supported by linux and went on my merry way and bought the Dtv2000H+. Now i'm stuck in the same delema. Im currently using ubuntu 8.10 and only because i have an old ATI graphics card which after endless nights worked out that it has no support in the new ubuntu 9.04. So i've passed the first heardell and got myself in another herdell. 

Anyway would appreciate any feedback.

---

### Post by istvanv on 2010-02-15
There is an experimental driver for this card here: [http://www.spinics.net/lists/linux-media/msg15858.html](http://www.spinics.net/lists/linux-media/msg15858.html)

Only the analog TV, radio, and IR have been tested, and those generally work. Digital TV support is implemented, but not tested (it might work with some luck). Note that there are additional patches in the messages following up to the first one, although they are not essential to get the card working, and the first version was tested more.

As mentioned, this is experimental code, so use it at your own risk, and only if you are familiar with patching, compiling, and installing V4L drivers from source.

---

### Post by istvanv on 2010-02-20
An updated version with some documentation is now available here: [http://www.sharemation.com/IstvanV/v4l/xc4000.html](http://www.sharemation.com/IstvanV/v4l/xc4000.html). It will also detect a few other similar cards that use the XC4000 tuner chip.

---

### Post by mamammi on 2010-03-06
Hi all, I have the Leadtek DTV-2000H revision J (without the +). On the box there's written is Vista certified and in my understanding this says mine is the revision J. 
I've installed on Ubuntu 9.10 and from dmesg I understand it recognizes properly withouth error (except FM tuner). I am able to see digital TV.

However I am still not able to see analog TV that is the only thing I am interested.

When you say "everything works fine" you mean also analog TV and radio?
Looking on the web I lost any hope :(

Thanks in advance for your support

---

### Post by laffinet on 2010-03-09
> **mamammi said:**
> When you say "everything works fine" you mean also analog TV and radio?
Looking on the web I lost any hope :(

Thanks in advance for your support

I never looked into analog (all digital TV here). 

I briefly looked into radio, but that didn't seem to be supported very well.

---

### Post by istvanv on 2010-03-13
> **istvanv said:**
> An updated version with some documentation is now available here: [http://www.sharemation.com/IstvanV/v4l/xc4000.html](http://www.sharemation.com/IstvanV/v4l/xc4000.html). It will also detect a few other similar cards that use the XC4000 tuner chip.

This driver has also been tested with DVB-T now by an user, and it reportedly works. So, basically, the DTV2000 H Plus, and similar cards using the XC4000 tuner chip are fully supported by it (analog TV, digital TV, FM radio, and IR all work).

---

### Post by mamammi on 2010-03-14
Digital is ok also for me. I am also not able to use Radio tuner.

I was interested in S-Video input in order to grab my old VHS tapes but I am not able to make it works.:(
Any suggestion is more than welcome (I have the DTV2000h J version). 
I still have not tried the xc4000 driver here reported because I have the J version.

---

### Post by Cheifchimp on 2010-05-10
I'm not running ubuntu any more, (I now use archlinux) but I do have the same card.

Arch is up to kernel 2.6.33 and my card is being autodetected as card number 82 and found this in dmesg
cx88/2: cx2388x MPEG-TS Driver Manager version 0.0.7 loaded
cx88/0: cx2388x v4l2 driver version 0.0.7 loaded
cx88[0]: subsystem: 107d:6f2b, board: WinFast DTV2000 H rev. J [card=82,autodetected], frontend(s): 1
cx88[0]: TV tuner type 63, Radio tuner type -1

I haven't had any time to play with it recently and don't have a handy antenna lead ATM so I can't test it right now

---

