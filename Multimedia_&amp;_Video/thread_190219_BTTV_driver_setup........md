---
title: "BTTV driver setup......."
date: 2006-06-06
forum: Multimedia &amp; Video
---

### Post by crispy_420 on 2006-06-06
OK first of all I have to admit I screwed up.

Recently I downloaded Mepis to try it out since it is now based on Ubuntu. So I decided to install it. This is where I messed up good. I had the wrong swappable drive in and wiped out my Ubuntu 5.10 install. I realized my error today when I came back to do an update to Dapper and saw the Mepis boot.

I almost soiled myself in anger. #&*!ing @^%$ (<- what would you say?).

I backed up most, but setting up my TV card and documents, I did not.

For my hardware I have a BTTV based card. It is a Leadtek WinFast TV 2000 XP with FM radio.

What files do I need to edit to my card to work correctly in NTSC? Or what commands do I need to issue?

Help Me and sorry for straying. I won't do it again.

---

### Post by crispy_420 on 2006-06-07
I solved it. No need to respond.

---

### Post by librano on 2006-06-09
yes there is a need to respond... we need to know how you solved it!... i am facing the same prob of configuring my tv card.... please explain how you did it..

lib.

---

### Post by tkman on 2006-06-12
Please respond.  This issue seems to be affecting a number of people with multiple answers being given as solutions.  Please help.

---

### Post by scxtt on 2006-06-12
[QUOTE=crispy_420]What files do I need to edit to my card to work correctly in NTSC?[/QUOTE]setting NTSC (or anything else) is generally done through the program you use to view (tvtime, xawtv, etc.), doesn't have anything to do w/ drivers ...

---

### Post by ianmac on 2006-06-15
I have the 2000 XP RM card (no tv tuner)...

I have xawtv working with this card (tvtime doesn't work for me...  hopefully yet...)

To get this card to work, I added a file to my /etc/modprobe.d folder with the following line:
options bttv tuner=43

you may also have a card that needs tuner=2

Ian


The previous poster is correct...  setting the NTSC is dependent on your software, HOWEVER, you have to tell the driver which tuner to use...  different cards use different tuner hardware.

---

### Post by vyruss on 2006-06-17
[QUOTE=crispy_420]I solved it. No need to respond.[/QUOTE]

Now that is not very helpful, and certainly not in the spirit of Ubuntu. Why don't you let the other people who might have the same problem know what you did to solve it for yourself? :(

---

### Post by crispy_420 on 2006-07-02
Sorry I forgot to post. When I boot up my desktop I look at what I did a post, I'm on my laptop right know having issues with network manager.

I've been away from these forums for a bit. Just give a few hours and I'll get that answer for you.

And on a side note about NTSC support. Yes you can change it to NTSC in the program but channels will be off by one and color is very dull. This is a known problem listed on tvtime's page.

[channels off and black and white]("http://tvtime.sourceforge.net/problems.html#tvwonder")

I'll be back in a few.

---

### Post by crispy_420 on 2006-07-02
Here is listing of BTTV tuner types: [HERE]("http://www.die.net/doc/linux/HOWTO/mini/BTTV-4.html")

Near the end of the page is a list of tuner models and their corresponding tuner types.

And here is a better listing. [HERE]("http://linuxtv.org/v4lwiki/index.php/Main_Page")

One of the things I did was add this in my /etc/modules

> # TV
alias   char-major-81   bttv
pre-install bttv        modprobe -k tuner; modprobe -k msp3400
options bttv            radio=1 card=34
options tuner           type=2


*** Try this and do a reboot and tell if that worked. If not look at my next post. ***

Not sure if that did it or something else that I'm looking for. I'll post back again soon when I find it.

On a side note, I have both functional TV and FM radio.

---

### Post by crispy_420 on 2006-07-02
I did some digging and found this file:

/etc/modprobe.d/bttv       (another bttv reference)

This is a copy of that file for me:

> # i2c
alias char-major-89 i2c-devb
options i2c-algo-bit bit_test=1
# bttv
alias char-major-81 videodev
alias char-major-81-0 bttv
# Askey TV Capturer
options bttv card=34 tuner=2 radio=1 pll=1 adc_crush=0


This is what might have done it for me, after a reboot. I did this all really late at night the first time. Be patient, I will have the answer soon.

---

### Post by fragos on 2006-07-02
If your running Ubuntu 6.06, ignore zapping and install tvtime.  When it start it asks some questions and you'll be watching TV in no time.  The choice of tuner is critcle but Ubuntu picked the right one for my TV card.  No divers to modprobe or .conf files to edit unless that gives you pleasure.  The big trick seems to be tvtime for a TV viewer.

---

### Post by crispy_420 on 2006-07-03
So did anyone give my examples a try, I'm sure which one worked. 

Also I forgot to mention for FM radio I'm using GnomeRadio. For that I just switched the FM tuner from radio1 to radio0.

---

### Post by MistaED on 2006-08-08
Hey guys, what if you have two tv tuner cards but both use the same bttv/bt878 chipset?

This pc has a DVB high definition bt878 twinhan which ubuntu detects nicely (just needs dvb-bt8xx and dst added to /etc/modprobe) but the analog prolink pixelview playtv pro needs manual intervention (dmesg lists it as unknown/generic with card=0 and tuner=-1 status).

I unload all the modules which stack onto each other for both cards, but how do I set modprobe options for the one particular card and not the other? the digital card is bttv0 and the analog card is bttv1 but I only want to pass options over to bttv1, how do I do it? I set it manually but it just locks up the computer (I'm guessing because it's setting options to both cards).

Cheers
-MistaED

---

### Post by babis85 on 2006-08-15
> **crispy_420 said:**
> So did anyone give my examples a try, I'm sure which one worked. 

Also I forgot to mention for FM radio I'm using GnomeRadio. For that I just switched the FM tuner from radio1 to radio0.

I tried your first example, the one in which edit the /etc/modules and it solved my problem only with the sound. The problem now is that except i don't have a tv signal, when i open any tv application it closes the sound of the radio. If i close and re-open the gnomeradio things don't come back only until i restart the whole system.
Any idea?

---

### Post by crispy_420 on 2006-08-18
The radio and TV are both on the same card so I think it is one or the other. I don't see both working since audio shares the same output. Did watching TV work out well for you? Colors OK? Channels listed correctly?

As far as messing up and rebooting, I personally not had that problem. I have had some other issues with closing a TV app only to have the sound continue until after a reboot. My less that educated guess to solve your problem is simple: choose TV or radio, don't try both at the same time. Maybe this causes a conflict with the drivers that throws them into chaos. But I will try to duplicate the problem you are having later, I'm on my WinXP machine trying to do a remote setup of MythTV over network and it's not going to well.

MistaED: can't help you. Try starting a new thread or checking the bttv driver projects main page.

---

### Post by babis85 on 2006-08-19
> 
The radio and TV are both on the same card so I think it is one or the other. I don't see both working since audio shares the same output. Did watching TV work out well for you? Colors OK? Channels listed correctly?


Thanks for your reply. I don't mind if i can't have both working. I do mind for the tv to be working. I get no signal and have probably configure right the needed files. I quote them:

```

/etc/modules

# TV
alias   char-major-81    bttv
pre-install bttv        modprobe -k tuner; modprobe -k msp3400
options                 bttv               radio=1  card=34
options tuner           type=5

```

```

/etc/modprobe.d/bttv

# i2c
alias char-major-89 i2c-devb
options i2c-algo-bit bit_test=1
# bttv
alias char-major-81 videodev
alias char-major-81-0 bttv
# Askey TV Capturer
options bttv card=34 tuner=5 radio=1 pll=1 adc_crush=0

```

I am not sure for the pll's value. I took that segment from a previous post of yours.
In file /etc/modprobe.conf i have commented all the lines relevant with bttv, which are quite the same with the above, because it didn't ever work.


Thanks, i am waiting for your reply...

---

### Post by crispy_420 on 2006-09-26
Two questions:

Is this the same card as mine? (LeadTek WinFast 2000 Deluxe?)

Do you live in the US? (NTSC?)

---

### Post by babis85 on 2006-09-26
> **crispy_420 said:**
> Two questions:

Is this the same card as mine? (LeadTek WinFast 2000 Deluxe?)

Do you live in the US? (NTSC?)
Hello, my friend. Thanks foy your reply even lately. I appreciate that much.
No, it isn't. It's a LeadTek WinFast 2000/XP
No, i live in Europe, in Greece. But, i don't think that this is the point, because i am enough sure that i have made the right configration.
Any, idea left?

---

### Post by crispy_420 on 2006-09-26
is it the bt878 based card? leadtek changed chipsets somewhere along the way

post the section of dmesg concerning the card.

---

### Post by babis85 on 2006-09-26
Yes it is.
> 
[17179588.656000] bttv: driver version 0.9.16 loaded
[17179588.656000] bttv: using 8 buffers with 2080k (520 pages) each for capture
[17179588.656000] bttv: Bt8xx card found (0).
[17179588.656000] bttv0: Bt878 (rev 17) at 0000:00:0c.0, irq: 193, latency: 32, mmio: 0xdddfe000
[17179588.656000] bttv0: detected: Leadtek WinFast TV 2000 [card=34], PCI subsystem ID is 107d:6606
[17179588.656000] bttv0: using: Leadtek WinFast 2000/ WinFast 2000 XP [card=34,insmod option]
[17179588.656000] bttv0: gpio: en=00000000, out=00000000 in=00bff707 [init]
[17179588.656000] bttv0: using tuner=5
[17179588.656000] bttv0: i2c: checking for MSP34xx @ 0x80... not found
[17179588.660000] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[17179588.660000] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[17179588.664000] bttv0: i2c: checking for TDA9887 @ 0x86... not found
[17179588.720000] bttv0: registered device video0
[17179588.720000] bttv0: registered device vbi0
[17179588.720000] bttv0: registered device radio0
[17179588.720000] bttv0: PLL: 28636363 => 35468950 .. ok
[17179588.752000] bttv0: add subdevice "remote0"


---

### Post by crispy_420 on 2006-09-27
My dmesg looks the same almost:

> [17179594.648000] Linux video capture interface: v1.00
[17179594.860000] bttv: driver version 0.9.16 loaded
[17179594.860000] bttv: using 8 buffers with 2080k (520 pages) each for capture
[17179594.860000] bttv: Bt8xx card found (0).
[17179594.860000] ACPI: PCI Interrupt 0000:02:0d.0[A] -> GSI 21 (level, low) -> IRQ 201
[17179594.860000] bttv0: Bt878 (rev 17) at 0000:02:0d.0, irq: 201, latency: 32, mmio: 0xf6afe000
[17179594.860000] bttv0: detected: Leadtek WinFast TV 2000 [card=34], PCI subsystem ID is 107d:6606
[17179594.860000] bttv0: using: Leadtek WinFast 2000/ WinFast 2000 XP [card=34,insmod option]
[17179594.860000] bttv0: gpio: en=00000000, out=00000000 in=00bf7707 [init]
[17179594.860000] i2c-algo-bit.o: (0) scl=1, sda=1
[17179594.860000] i2c-algo-bit.o: (1) scl=1, sda=0
[17179594.860000] i2c-algo-bit.o: (2) scl=1, sda=1
[17179594.860000] i2c-algo-bit.o: (3) scl=0, sda=1
[17179594.860000] i2c-algo-bit.o: (4) scl=1, sda=1
[17179594.860000] i2c-algo-bit.o: bt878 #0 [sw] passed test.
[17179594.860000] bttv0: using tuner=2
[17179594.860000] bttv0: i2c: checking for MSP34xx @ 0x80... not found
[17179594.880000] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[17179594.880000] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[17179594.884000] bttv0: i2c: checking for TDA9887 @ 0x86... not found
[17179594.952000] Floppy drive(s): fd0 is 1.44M
[17179594.976000] FDC 0 is a post-1991 82077
[17179594.976000] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 3 if 0 alt 0 proto 2 vid 0x04E8 pid 0x326C
[17179594.976000] usbcore: registered new driver usblp
[17179594.976000] drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
[17179595.852000] parport: PnPBIOS parport detected.
[17179595.852000] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
[17179596.320000] tuner 0-0061: chip found @ 0xc2 (bt878 #0 [sw])
[17179596.320000] tuner 0-0061: type set to 2 (Philips NTSC (FI1236,FM1236 and compatibles))
[17179596.352000] bttv0: registered device video0
[17179596.352000] bttv0: registered device vbi0
[17179596.352000] bttv0: registered device radio0
[17179596.352000] bttv0: PLL: 28636363 => 35468950 .. ok
[17179596.388000] bttv0: add subdevice "remote0"
[17179596.436000] bt878: AUDIO driver version 0.0.0 loaded
[17179596.436000] bt878: Bt878 AUDIO function found (0).
[17179596.436000] ACPI: PCI Interrupt 0000:02:0d.1[A] -> GSI 21 (level, low) -> IRQ 201
[17179596.436000] bt878(0): Bt878 (rev 17) at 02:0d.1, irq: 201, latency: 32, memory: 0xf6aff000


Another idea:

Is your graphics card set up correcting? And what happens when you launch tvtime from terminal? Any errors there?

---

### Post by babis85 on 2006-09-27
I think that it is.
When i start tvtime from console i get nosignal at the Xwindow and at the console an error such:
"videoinput: Cannot open capture device /dev/video1: No such file or directory"

---

### Post by crispy_420 on 2006-09-27
Do you have two tv cards?

Usually if you have one it would be "video0" (video zero). Could this be the likely culprit? I will look into this in a bit, I'm on my WinXP machine now. But starting to think it may have something to with that.

---

### Post by babis85 on 2006-09-28
I don't think that could be the culprit. I changed /dev/video1 in my ~/.tvtime/tvtime.xml to /dev/video which is a soft link to /dev/video0 and i got no errors at console and "No signal" at tvtime's window.
I can't understand, why does this happen. I am using Ubuntu exclusively and that is the only barrier that i can't get over.

---

### Post by crispy_420 on 2006-09-28
I'm not too familiar with PAL tv format but you have a few options:

tuner=1
tuner=3
tuner=5

look [here]("http://www.tldp.org/HOWTO/BTTV/modprobe.html")

---

### Post by babis85 on 2006-10-08
As i see i will never have my tv working. What a pity...
I had already tried these options and that link before i posted in this thread. Be that as it may, i still appreciate your effort and patience.Thank you.

---

### Post by crispy_420 on 2006-10-10
try reposting that may help...

---

### Post by babis85 on 2006-10-10
> **crispy_420 said:**
> try reposting that may help...
I simply said that i have done all these you've told me to do at your previous post and that i appreciate very much your effort and patience.

---

### Post by crispy_420 on 2006-10-10
It was no problem for me, I was just trying to help. In the how-to section there is a discussion on setting up the bt878 based cards and they may have more experience with me. [HERE IS THAT LINK]("http://ubuntuforums.org/showthread.php?t=153935&highlight=bt878")

I'm no linux pro (just a relative noob, less than 2 years), but you may have more luck here.

Good luck and I'll bump into you sooner or later.

---

### Post by Kross on 2006-12-07
> **crispy_420 said:**
> It was no problem for me, I was just trying to help. In the how-to section there is a discussion on setting up the bt878 based cards and they may have more experience with me. [HERE IS THAT LINK]("http://ubuntuforums.org/showthread.php?t=153935&highlight=bt878")

I'm no linux pro (just a relative noob, less than 2 years), but you may have more luck here.

Good luck and I'll bump into you sooner or later.



Try This 
[http://ubuntuforums.org/showthread.php?t=300228&highlight=bttv]("http://ubuntuforums.org/showthread.php?t=300228&highlight=bttv")

It work for me..
Let Me know if it works for you..

<=Kross=>

---

