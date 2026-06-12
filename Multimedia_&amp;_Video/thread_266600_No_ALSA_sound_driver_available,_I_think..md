---
title: "No ALSA sound driver available, I think."
date: 2006-09-27
forum: Multimedia &amp; Video
---

### Post by Tominator on 2006-09-27
This poor noob has struggled with sound issue for quite some time so effective help will be amazingly appreciated. The computer in question is an IBM PC300PL, (500MHZ, 512KB, 256MB, 6.4GB, HDD, IDE, PCV, 15A, 4X4, WIN 98), without theWin98, lol. I went to IBM's site and using the product code, (6862-V4U), find that this P3 has an onboard sound card. Crystal Audio seems to be the name and the driver is QD3Z12US. I have concluded that there is no ALSA module for this driver. Am I wrong? If I'm right, what do I do next? What follows is my output from the Comprehensive Sound Guide.
1. ltomdaniels@ltomdaniels:~$ aplay -l
aplay: device_list:221: no soundcards found...
ltomdaniels@ltomdaniels:~$

2. 

 ltomdaniels@ltomdaniels:~$ lspci -v
0000:00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
        Flags: bus master, medium devsel, latency 32
        Memory at ec000000 (32-bit, prefetchable) [size=64M]
        Capabilities: <available only to root>

0000:00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 64
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
        Memory behind bridge: f4000000-f7ffffff
        Prefetchable memory behind bridge: 20000000-200fffff

0000:00:02.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
        Flags: bus master, medium devsel, latency 0

0000:00:02.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01) (prog-if 80 [Master])
        Flags: bus master, medium devsel, latency 32
        I/O ports at fff0 [size=16]

0000:00:02.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01) (prog-if 00 [UHCI])
        Flags: bus master, medium devsel, latency 48, IRQ 11
        I/O ports at ff00 [size=32]

0000:00:02.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
        Flags: medium devsel, IRQ 9

0000:00:03.0 Ethernet controller: Intel Corporation 82557/8/9 [Ethernet Pro 100] (rev 05)
        Subsystem: IBM: Unknown device 00d7
        Flags: bus master, medium devsel, latency 64, IRQ 11
        Memory at f3eff000 (32-bit, prefetchable) [size=4K]
        I/O ports at 7c60 [size=32]
        Memory at f3f00000 (32-bit, non-prefetchable) [size=1M]
        Capabilities: <available only to root>

0000:01:01.0 VGA compatible controller: S3 Inc. Trio 64 3D (rev 01) (prog-if 00 [VGA])
        Subsystem: IBM Integrated Trio3D
        Flags: bus master, medium devsel, latency 32, IRQ 9
        Memory at f4000000 (32-bit, non-prefetchable) [size=64M]
        Expansion ROM at 20000000 [disabled] [size=64K]
        Capabilities: <available only to root>


3.I find nothing at the Alsa site about my sound card.
4.I have done that a few times. sudo modprobe snd-
5.I tried to get the ALSA drivers from a fresh kernal.
6.I compiled AlSA-project.org in the way reccomended, did not see my driver.
What's the verdict? Will I ever have sound, lol. Thanks all, Tom.](*,)

---

### Post by pseudonym on 2006-09-27
Hi,

I used to own a machine just like that. Your sound chip is manufactured by Cirrus Logic, and uses the ISA bus (so it won't show up under 'lspci'). 

The good news is that it is indeed supported by ALSA. The appropriate ALSA module is called snd-cs4236. 

The bad news is that it outputs sound in a quality best described as 'mildly execrable' :) 

I therefore highly recommend disbaling this audio chip in your BIOS and investing a very modest sum in a suitable PCI sound card. Anything Sound Blaster is good. Old 2-channel ones go for a song on ebay.

But if you would still like to get the Crystal chip working, just let me know and I can tell you what you'll need to do...

---

### Post by Tominator on 2006-09-27
Thanks for your help Psuedo. I have struggled with this for so long that I really would like to solve it. Then I'll take your advice and go get a decent card.

---

### Post by pseudonym on 2006-09-27
OK, as you may already know, ISA devices don't usually get configured automatically at bootup. You need to assign system resources to them manually. To do this, start by finding out what settings Ubuntu detects the card at. Open up a terminal and ```
sudo gedit /var/log/syslog
``` This is the log of system events. Scroll through and find a section dealing with 'isapnp' - this is the (misnamed) linux ISA plug and pl(r)ay system. You should see some settings which look something like 'io=0x220 irq=10 dma=1' . These are settings which you will need to get your card working. Write them down.

Close syslog and now type ```
sudo gedit /etc/modules
```. This file is used to load some drivers at bootup time. After any lines beginning with 'ide-' you need to add a line like this - ```
snd-cs4236 io=0x220 irq=10 dma=1
``` , bearing in mind that your numbers may vary from mine.

Now, save, exit, and reboot. Once you get back into Ubuntu, hopefully your sound chip will be recognized and ready to use. If not, post back and report your results. ALSA configuration has changed slightly since I last used Ubuntu, so there may be another step you need to do...

On another note, I recommend using Xubuntu on the type of machine you have (in fact I recommend it on any machine :) ). Its XFCE desktop is much less resource-intensive than the Gnome-based Ubuntu, and should perform really well on your hardware. It's something to think about, anyway.

---

### Post by Tominator on 2006-09-27
Card 'Crystal Audio'
Sep 27 12:15:53 ltomdaniels kernel: [  193.335830] isapnp: 1 Plug & Play card detected total
Sep 27 12:15:53 ltomdaniels kernel: [  193.411479] PNP: PS/2 Controller [PNP0303,PNP0f13] at 0x60,0x64 irq 1,12
Sep 27 12:15:53 ltomdaniels kernel: [  193.412909] serio: i8042 AUX port at 0x60,0x64 irq 12
Sep 27 12:15:53 ltomdaniels kernel: [  193.413137] serio: i8042 KBD port at 0x60,0x64 irq 1
Sep 27 12:15:53 ltomdaniels kernel: [  193.413325] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
Sep 27 12:15:53 ltomdaniels kernel: [  193.413609] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A

I think that is the relevant section, but I cannot discern for sure the exact part I need to record. Thanks again for all your help, Tom.](*,)

---

### Post by pseudonym on 2006-09-27
You'll need to post more of the log. It's not uncommon for messages relating to one thing to be split up over different parts. Look for the part which mentions 'Crystal Audio' or 'Cirrus Logic' or similar.

If you can't find it you may need to adjust your BIOS. Was this sound chip working when you had windows installed (assuming it was)?

---

### Post by Tominator on 2006-09-27
Thanks again Psuedo. Here is a lot more, it was too long to post it all. I like this machine for me. Thanks for the tip, Xubuntu will be my next project. I'll edit the extraneous after I learn what is that. Sorry for posting so much. I am not sure if the chip worked or not, I bought the thing with a wiped hard drive and installed Ubuntu.                 Restarting tasks... done Scanning for PnP cards...
Sep 27 12:15:53 ltomdaniels kernel: [  193.335818] isapnp: Card 'Crystal Audio'
Sep 27 12:15:53 ltomdaniels kernel: [  193.335830] isapnp: 1 Plug & Play card detected total
Sep 27 12:15:53 ltomdaniels kernel: [  193.411479] PNP: PS/2 Controller [PNP0303,PNP0f13] at 0x60,0x64 irq 1,12
Sep 27 12:15:53 ltomdaniels kernel: [  193.412909] serio: i8042 AUX port at 0x60,0x64 irq 12
Sep 27 12:15:53 ltomdaniels kernel: [  193.413137] serio: i8042 KBD port at 0x60,0x64 irq 1
Sep 27 12:15:53 ltomdaniels kernel: [  193.413325] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
Sep 27 12:15:53 ltomdaniels kernel: [  193.413609] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Sep 27 12:15:53 ltomdaniels kernel: [  193.413874] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
Sep 27 12:15:53 ltomdaniels kernel: [  193.422834] 00:12: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Sep 27 12:15:53 ltomdaniels kernel: [  193.423364] 00:13: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
Sep 27 12:15:53 ltomdaniels kernel: [  193.425741] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Sep 27 12:15:53 ltomdaniels kernel: [  193.425961] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Sep 27 12:15:53 ltomdaniels kernel: [  193.425976] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Sep 27 12:15:53 ltomdaniels kernel: [  193.426460] mice: PS/2 mouse device common for all mice
Sep 27 12:15:53 ltomdaniels kernel: [  193.427035] EISA: Probing bus 0 at eisa.0
Sep 27 12:15:53 ltomdaniels kernel: [  193.427095] Cannot allocate resource for EISA slot 7

---

### Post by pseudonym on 2006-09-27
Tom, your card isn't being detected properly, so the syslog just reports that it 'cannot allocate resources' blah blah.

But you're in luck. I dug out the settings on some notes I scrawled when I owned a similar machine. Your line in /etc/modules should read as follows -

snd-cs4236 io=0x534 irq=5 dma=1,3 mpu_io=0x330

If this doesn't work you could try and use the snd-cs4232 module instead. Sometimes linux detects things a little differently to what you think your hardware should be.

One other thing I used to do when I owned a PII was duplicate these settings in the BIOS, which can help linux hardware detection of ISA devices. If you don't know already, press F1 during boot to get to the BIOS setup screen. There is a section called 'ISA Legacy Resources', which has subsections for IO, IRQ, and DMA (don't worry about what these mean if you don't know). Enter your values accordingly (mpu_io can go in IO too).

Save, exit, and reboot, and post back your results.

---

### Post by Tominator on 2006-09-27
Well Psuedo, That's a lot for me to study and chew on, Thanks for the assignment, lol. I might not get it done this afternoon but I'll keep posting as I accomplish. Thanks again for your help, Tom.

---

### Post by Tominator on 2006-09-28
After i input this command >sudo gedit /etc/modules< I got the following output.......
ltomdaniels@ltomdaniels:~$ sudo gedit /etc/modules
Password:
ALSA lib confmisc.c:672:(snd_func_card_driver) cannot find card '0'
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1072:(snd_func_refer) error evaluating name
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3962:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2102:(snd_pcm_open_noupdate) Unknown PCM default
ltomdaniels@ltomdaniels:~$
Also, another window pops up entitled >modules (/etc) - gedit< the output of that window is as follows....
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
psmouse

I don't know what to make of it so I'm gonna wait for some advice.
Thanks Psuedo and any other contributers, Tom

---

### Post by pseudonym on 2006-09-28
Hi Tom,

I don't know why ALSA is spitting that stuff out, but the second thing that popped up (...lp, psmouse etc) is the file you you have to edit. By way of explanation, /etc/modules is a file which can be used to specify modules to load at bootup. Sometimes the system does this automatically - 'lp' is your parallel port driver, and psmouse is for your PS-2 connected mouse). I think by specifying modules in this folder they get given a certain priority.

But this need not detain us.

What you need to do is insert your 'snd-cs4236 ...' line above the line which says 'lp'. Then save the file and exit gedit. This is telling the system to load this module with the parameters I gave you above. Then try a reboot to see if your sound works.

---

### Post by Tominator on 2006-09-28
Hey, thanks for the quick reply. That does not seem to do it. I thought about trying that other number you suggested. Seems a good idea to share those last two outputs with you again first, here they are.....

ltomdaniels@ltomdaniels:~$ sudo gedit /etc/modules
Password:
ALSA lib confmisc.c:672:(snd_func_card_driver) cannot find card '0'
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1072:(snd_func_refer) error evaluating name
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3962:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2102:(snd_pcm_open_noupdate) Unknown PCM default

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.
snd-cs4236 io=0x534 irq=5 dma=1,3 mpu_io=0x330

lp
psmouse

---

### Post by Tominator on 2006-09-28
Ok, i went ahead and inserted a 2nd line with the 4232 module number. Still no sound though. Last night I bought a soundblaster card on ebay. So if this doesn't work out, that should. Do you think it will be detected automatically? Thanks again for all your efforts, Tom.

---

### Post by pseudonym on 2006-09-29
Yeah, it should, as long as it's a PCI one. If you bought an ISA sound blaster you're no better off ;)

I remember that Crystal Audio gave me a hell of a time with linux, too. More trouble than it's worth, TBH. But the ALSA that I used on Debian had a utility called 'alsaconf' which sets up the right config files. That doesn't seem to be in the Ubuntu ALSA.

One last step. From a terminal, run - ```
sudo gedit /etc/modules
``` and remove everything from the above line except the module name 'snd-cs4236' (or *4232). Save the file and exit gedit.

Now run - ```
sudo gedit /etc/modprobe.d/sound
``` and insert these lines - ```
options snd-cs4236 index=0
options snd-cs4236 isapnp=0 port=0x534 irq=5 dma8=1 dma16=3 mpu_port=0x330
``` Save and exit gedit.

Now run - ```
sudo update-modules
``` and then reboot.

Still not working? Then remove the above file, and return /etc/modules to its original state. Ensure the Crystal Audio is disabled in your BIOS, and install your new PCI Sound Blaster. Enjoy!

BTW, I just noticed this [sound help guide]("http://www.ubuntuforums.org/showthread.php?t=205449") as one of the stickies in this forum (doh!). It's packed with info and should be able to answer any queries you may have in the future.

:)

---

### Post by Tominator on 2006-09-30
Well Psuedo you gave it one hell of a try. I tried the above steps twice, once for each module, separately. It still does not recognize either module. I practically lived in that Comprehensive Sound Guide for two afternoons, I think it probably has helped a lot of people, it did me no good however.
The card I ordered is purported to be a PCI, the seller did not ship until Sat., I'll install it and let you know how it turns out. Thanks for all your time. Tom](*,)

---

### Post by Tominator on 2006-10-05
Well I solved my problem, I bought a used Sound Blaster PCI card off Ebay and It was recognized and operated properly at the first start up. Thanks for the help, Psuedonym.

---

