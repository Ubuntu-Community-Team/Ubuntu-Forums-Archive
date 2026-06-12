---
title: "ATI TV Wonder no sound output"
date: 2006-03-06
forum: Multimedia &amp; Video
---

### Post by pak22884 on 2006-03-06
I was really hoping it wouldn't come to this, but after days of searching and experimenting (maybe I just suck at both), I still haven't been able to come up with a solution.

I have an ATI TV Wonder with a bt878 chip and when I run Tvtime (or any other tv program) I get picture, but no sound.  The tuner on the card no longer works, so I have a VCR plugged into the composite inputs on the card.  I have a set of speakers connected directly to the line out of the tv card, so I'm fairly certain it is not a problem with the sound card (I have also tested the line in on the sound card and it works fine).  If I boot into wIndows and start a tv program, I get sound output from the tv card, but I get no such luck in linux.

I'm guessing the problem is with the bttv or bt878 driver settings, but after trying a number of different settings, such as different cards and tuner types in the bttv options, I still get no sound.

I'm fairly new to linux, so this may very well have a simple solution that I'm overlooking.  I've found a number of other posts on various sites with similar problems, but most of them seem to be due to muted inputs or the like.

Any help would be greatly appreciated.

Thanks,
Deepak

PS - if there is a better place for me to post this, please let me know.

---

### Post by WebbyBabe on 2006-03-15
How did you get your ATI TV WONDER to work with Ubuntu? I looked everywhere and can't find a thing on how to install it on Ubuntu. Please help.

---

### Post by pak22884 on 2006-03-16
I think I've gotten close to getting my sound working, but I'm still not quite there yet.

If I have a coax cable connected from my vcr to the tv card, then I get sound out of the tv card's line out.  What's weird is that if I set tvtime to the composite input, I still get the sound from the tuner rather than the sound from the composite input.  This led me to believe that either tvtime or the bttv driver isn't changing the audio input.    To debug this, I unloaded the bttv driver and then reloaded it with these options in /etc/modprobe.d/bttv:

```
# i2c
alias char-major-89 i2c-devb
options i2c-algo-bit bit_test=1
# bttv
alias char-major-81 videodev
alias char-major-81-0 bttv
# My TV Card
options bttv automute=0 bttv_gpio=1

```

I cleared the kernel ring buffer and reloaded bttv using:

```
modprobe -v bttv
```

Which resulted in:

```
insmod /lib/modules/2.6.12-10-k7/kernel/drivers/media/video/bttv.ko automute=0 bttv_gpio=1
```

So far, so good, as far as I can tell.

Then I ran tvtime, switched through the inputs a few times and checked the result of dmesg:

```
[4307531.063000] bttv: driver version 0.9.15 loaded
[4307531.063000] bttv: using 8 buffers with 2080k (520 pages) each for capture
[4307531.063000] bttv: Host bridge needs ETBF enabled.
[4307531.063000] bttv: pci latency fixup [10]
[4307531.071000] bttv: Bt8xx card found (0).
[4307531.071000] ACPI: PCI Interrupt 0000:00:0b.0[A] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[4307531.071000] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[4307531.071000] bttv0: Bt878 (rev 17) at 0000:00:0b.0, irq: 11, latency: 64, mmio: 0xd7000000
[4307531.072000] bttv0: detected: ATI TV Wonder [card=63], PCI subsystem ID is 1002:0001
[4307531.072000] bttv0: using: ATI TV-Wonder [card=63,autodetected]
[4307531.072000] bttv0: enabling ETBF (430FX/VP3 compatibilty)
[4307531.072000] bttv0: setting pci timer to 10
[4307531.072000] bttv0: gpio: en=00000000, out=00000000 in=00ffffff [pre-init]
[4307531.073000] bttv0: gpio: en=00000000, out=00000000 in=00ffffff [init]
[4307531.073000] i2c-algo-bit.o: (0) scl=1, sda=1
[4307531.073000] i2c-algo-bit.o: (1) scl=1, sda=0
[4307531.073000] i2c-algo-bit.o: (2) scl=1, sda=1
[4307531.073000] i2c-algo-bit.o: (3) scl=0, sda=1
[4307531.073000] i2c-algo-bit.o: (4) scl=1, sda=1
[4307531.073000] i2c-algo-bit.o: bt878 #0 [sw] passed test.
[4307531.142000] msp34xx: init: chip=MSP3445G-B8 +nicam +simple +simpler +radio mode=simpler
[4307531.159000] msp34xxg: daemon started
[4307531.196000] bttv0: using tuner=19
[4307531.196000] bttv0: i2c: checking for MSP34xx @ 0x80... found
[4307531.212000] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[4307531.214000] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[4307531.216000] bttv0: i2c: checking for TDA9887 @ 0x86... not found
[4307531.269000] tuner 0-0060: chip found @ 0xc0 (bt878 #0 [sw])
[4307531.269000] tuner 0-0060: type set to 19 (Temic PAL* auto (4006 FN5))
[4307531.335000] bttv0: registered device video0
[4307531.337000] bttv0: registered device vbi0
[4307531.337000] bttv0: gpio: en=0000f03f, out=0000b03e in=00ff0fc0 [audio: off]
[4307531.348000] bttv0: gpio: en=0000f03f, out=0000b03e in=00ff0fc0 [audio: off]
[4307531.348000] bttv0: PLL: 28636363 => 35468950 .. ok
[4307531.516000] bt878: AUDIO driver version 0.0.0 loaded
[4307531.524000] bt878: Bt878 AUDIO function found (0).
[4307531.524000] ACPI: PCI Interrupt 0000:00:0b.1[A] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[4307531.524000] bt878(0): Bt878 (rev 17) at 00:0b.1, irq: 11, latency: 32, memory: 0xd6800000
[4307536.016000] bttv0: gpio: en=0000f03f, out=0000b03e in=00ff0fc0 [audio: off]
[4307536.028000] bttv0: PLL can sleep, using XTAL (28636363).
[4307536.076000] bttv0: gpio: en=0000f03f, out=0000b03e in=00ff0fc0 [audio: off]
[4307536.389000] bttv0: gpio: en=0000f03f, out=0000b03f in=00ff0fc0 [audio: extern]
[4307541.828000] bttv0: gpio: en=0000f03f, out=0000b03f in=00ff0fc0 [audio: extern]
[4307543.063000] bttv0: gpio: en=0000f03f, out=0000b03e in=00ff0fc0 [audio: tuner]
[4307543.103000] bttv0: gpio: en=0000f03f, out=0000b03e in=00ff0fc0 [audio: off]
[4307543.466000] bttv0: gpio: en=0000f03f, out=0000b03e in=00ff0fc0 [audio: tuner]
[4307545.350000] bttv0: gpio: en=0000f03f, out=0000b03f in=00ff0fc0 [audio: extern]
[4307547.568000] bttv0: gpio: en=0000f03f, out=0000b03f in=00ff0fc0 [audio: extern]
[4307548.769000] bttv0: gpio: en=0000f03f, out=0000b03e in=00ff0fc0 [audio: tuner]
[4307548.814000] bttv0: gpio: en=0000f03f, out=0000b03e in=00ff0fc0 [audio: off]
[4307549.147000] bttv0: gpio: en=0000f03f, out=0000b03e in=00ff0fc0 [audio: tuner]
[4307550.002000] bttv0: gpio: en=0000f03f, out=0000b03f in=00ff0fc0 [audio: extern]
``` 

According to the last few lines, something changes when I switch inputs, but I'm not really sure how to interpret it.

As I said before, it works fine under Windows, so it must be some setting with bttv (or at least linux related).  If anyone can make any sense of this, I'd really appreciate some help.

Thanks,
Deepak

---

### Post by WebbyBabe on 2006-03-17
How do you even get  a picture? I have ATI TV WONDER USB 2.0 and can't get it to work in Ubuntu.

---

### Post by pak22884 on 2006-03-18
I have the actual card version, so I'm not sure about the USB version.  I would think the USB version would require the bttv driver as well, but I'm not sure.  What program are you using to watch tv?

---

### Post by WebbyBabe on 2006-03-18
I'm trrying to use Zapping TV to view to on Ubuntu. But I get a /dev/video0 error.

---

### Post by pak22884 on 2006-03-18
Have you checked to make sure you have a video0 device in /dev?  Also, have you tried other programs like tvtime and xawtv?

-Deepak

---

### Post by WebbyBabe on 2006-03-19
Yes, I have video0 in the /dev/ directory. I tried other programs like TVTime, MythTV, and XawTV and they all give me the same error about the /dev/video0 missing.

---

### Post by Argon Sloth on 2006-04-10
Deepak, 
Have you found a solution to your input and tuner sharing sound problem?

I seem to be having the same problem. From the random information I've been able to find, an external cable may work. But I haven't tried this yet.

---

### Post by pak22884 on 2006-04-10
Unfortunately, I have not come up with a solution.  An external cable didn't help my situation at all...hopefully it'll work for you.  I've pretty much given up on the problem for the time being.  Either people here are unwilling to help or they just plain don't know.  If it's the latter, then there would be very little chance that I would have any idea on how to fix the problem, considering my newbie status in linux.

Let me know if you figure something out.

-Deepak

---

### Post by Mustach on 2006-04-18
It's too bad that you've given up, because I've been having the same symptom with the same TV card (although the tuner on my card works).  Only I don't have a clue where to even start looking in my setup for a solution.

---

### Post by pak22884 on 2006-04-18
I haven't given up entirely...I'm more or less on sabbatical from the problem.  I've exhausted pretty much every resource I could find, so I figure I'd stop worrying about it until I learn more about Linux in general.

Are you having problems with getting sound from the line input, or from the tuner?

---

### Post by Stolie on 2006-10-03
I myself have a tv wonder pro with the cx23880 chipset. I can't seem to get sound to come from the tuner card at all...

---

### Post by elf@whoever.com on 2006-11-02
I was looking into installing an old ATI tv card that I have kicking around into my linux box. Figured I would check and see if anyone had any success with getting it working. So far no go for me as of yet... 

But I think I have the odd sound problem of the sound with cable, and cable sound with the composite input which pak22884 was experiencing.

I have a ATI TV Wonder VE. Its has the same Bt878 chipset. I was looking through the winblows install cd for it and found a pdf manual. On using the composite in connection it says:

"In order to capture streaming video and audio, you will need to use the Composite In connector on the back of your ATI-TV Wonder VE card.
1 Looking at the back of the ATI-TV Wonder VE card, connect one end of the composite cable to the Composite In on the back of the ATI TV-Wonder VE card.
2 Connect the other end of the composite cable to the Composite Out of your video device such as a camcorder or VCR.
3 Connect one end of the audio cable from the Audio Out on the back of your video device (camcorder or VCR).
4 Connect the other end of the audio cable to the Audio In on your sound card."

Done a lot of work with home theater stuff, and cable connections are the only one mentioned that inherently carry audio with the video. S-video, component, and composite are all just video connections (checked on composite at Wikipedia to make sure before posting). So if you were Looking at the composite input with no cable connection, no sound. Cable connected, you would see whatever the composite is hooked to but with the audio of whatever cable channel you happened to be tuned to at the time.

I think there is a solution wiring wise to this situation :-k , if you have a tv card that has internal audio connections. In otherwords the old cd audio cable bogarted for the cable tv sound inside the computer to the sound card. Sound for the composite would be like the pdf said, an audio input from whatever video source you are using to the line in on the sound card.

I did this with my TV card when I did use it the first time under win98. It worked so long as you pointed to which audio you wanted to be the one you are hearing. Not sure how to set it up software wise in Ubuntu, but will find out soon as I start ripping into my puter in the near future.:mrgreen:

---

