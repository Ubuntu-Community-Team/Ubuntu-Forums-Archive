---
title: "Hauppauge HVR 1600 remote control?"
date: 2009-01-18
forum: Mythbuntu
---

### Post by Ioky on 2009-01-18
I just got a Hauppauge HVR 1600 model 1199. It seem working well? (doesn't use it long enough to say how well it actually is.) 

However, My problem is the remote Control come with the Card, it doesn't seem working at all. I just wonder how can I make it work.

I have no knowledge on IR remote under Linux, so. 

Thanks.

---

### Post by uMuppet on 2009-01-19
What does the remote look like?  Can you post a pic somewhere?

---

### Post by Ioky on 2009-01-20
[IMG]http://lirc.sourceforge.net/remotes/hauppauge/PVR-350.jpg[/IMG]

I try to use mode2, it say "error oepn" /dev/lirc, no such file or directory. 

any idea?

Thanks

---

### Post by sniperbob on 2009-01-30
Last I searched around, the driver for the card supports all the video functions, but the infared port on the card is not supported yet.

I wasted an evening or two trying to force drivers to work for it with lirc, ended up giving up and just ordering a serial port IR receiver, hope to get it in the mail shortly. Generic serial IR units are much better supported.

---

### Post by psuprogrammer on 2009-02-01
> **sniperbob said:**
> ended up giving up and just ordering a serial port IR receiver, hope to get it in the mail shortly. Generic serial IR units are much better supported.

Can you post a few links to well supported serial IR units?
I'm looking for something easy to setup.

I've been working on this 1600 remote for several hours today and am lost.

---

### Post by sniperbob on 2009-02-11
If you search for "mythtv blaster" or something of the sort, you can come across several commercial offerings.

I would point you in a more specific direction - but I didnt end up buying one, I ordered parts and am making my own - so I don't know any more than you.

---

### Post by appsmanster on 2009-03-17
At least I am not the only one having issues with the remote. As much as I love Ubuntu, running on everything I can, an easier temporary solution would be Knoppmyth or Mythdora. I am still trying to get the remote to work with Mythbuntu. When I got my HVR-1600 card I decided to try Knoppmyth as I had some experience with it. Got needed drivers from V4L/DVB and it all worked. Tried Mythdora and it worked. But I like Ubuntu. Still working on Mythbuntu. Its just another learning curve. So I am now running Mythdora as primary and Mythbuntu as secondary. Once the remote issue is done and I will figure this out, I will switch to it. I know its not the thing to point out in this forum but looking at what works in one will help to figure out what to change in the other.

---

### Post by humdrim on 2009-03-25
Did you do something specific to get your remote working with knoppmyth, as it's not working for me I'm stuck at the same setup as with mythbuntu. I don't know if it's the placement of the port that's grounding it to the computer case or something else. Your input would be well appreciated. Thanks.

 I even tried the ir_kbd_i2c workaround from mark lord found here [http://rtr.ca/hvr1600/](http://rtr.ca/hvr1600/). The problem with that was that my r/c port is not seen as an input device so I couldn't use that.

---

### Post by Weidbrewer on 2009-04-02
I have the same card, but mine came with a different remote.  I am actually trying to use that remote on a different frontend, but am not having much luck setting it up.   Here is the remote that mine came with:

[IMG]http://www.mythtv.org/w/images/b/b2/MCE-Remote-2-v1069.jpg[/IMG]

That picture is from the MythTV wiki.  I am running Mythbuntu 8.10, and the install section simply says:  

>   Ubuntu 8.10

Ubuntu 8.10 ("Intrepid Ibex") has out of the box kernel modules for the MCE remotes. All that is required is to install lirc (as noted above), and follow the prompts. 

Lirc is installed...but I don't know where to go next.  What are the other steps to get this remote to work.

Again, for clarification, this remote and USB IR sensor are being used independently of the tuner card.  Thanks for any help.

---

### Post by MythAaron on 2009-04-02
I have a 1600 with Ioki's remote and it works fine here.

I'll throw this out there since this where I was tripped up.  Make sure the IR blaster/receiver is plugged ALL THE WAY into the card.  The plug will go so far, then it will "click" into place.

---

### Post by Weidbrewer on 2009-04-02
I installed Mythbuntu-Control Center and installed the remote from there...so far so good.  I'm having some play-back troubles (another thread) so I can't test the FF, RW, etc yet.   However, what I've tried worked.

---

### Post by dealcorn on 2009-06-14
Within Mythbuntu Control Center, what selections worked for remote name and IR transmitter?  HVR-1600 is not listed as a selection and the IR transmitter is not obvious.

---

### Post by uMuppet on 2009-06-14
Try Windows Media Centre (new) for both

---

### Post by Weidbrewer on 2009-06-14
That's exactly what I used.  Popped "new version" in, and I was good to go.

---

### Post by fermulator on 2009-09-03
So .. does anyone have the remote working in Ubuntu 9.04?

I'm a complete newb with this TV Tuner and IR Remote Control stuff.

I tried lirc, but there's no explicit options for the HVR-1600, and the gnome-lirc-properties window doesn't show it either.

---

### Post by Weidbrewer on 2009-09-03
The main thing is that there isn't an entry for that remote itself, but it uses one of the two MCE entries (The newer one, I believe.)  Try them both and one should work out of the box.  I'm still running 8.10 on most of my boxes, but there was one that I briefly had on 9.04 (there were graphics card issues, so I had to revert.)

---

### Post by tmkt on 2009-10-10
the grey remote used to work for me with 9.04..then I upgraded to 9.10..and can't get it to work...going to try the media centre option next.

---

### Post by JMcFly on 2009-10-10
My HVR-1600 came with the grey remote (not the MCE remote), and it works when I set 9.04 for HVR-1300's remote. You will hear a definitely click when the plug is inserted all of the way, its a little tougher than a normal stereo plug to insert due to how close it can be to the case frame.

But, I cant figure out how to set the red, green, yellow and blue buttons on the remote to key presses in Myth.  I'd like to set one to 100% fill (for when an analog source is broadcast in letterbox), but I cant find a line in the Myth frontend key menu to set that or cycle through the fill levels?

---

### Post by tmkt on 2009-10-10
No go using the windows MCE...went back to Ubuntu 9.04..working great again....using Hauppauge TV Card setting

---

### Post by telseth on 2009-10-11
I just upgraded to 9.10 and have been using the grey hauppauge hvr 1600 remote happily.  Now it doesn't work.  It doesn't create /dev/lirc0 and doesn't use the correct lirc_i2c module (it is trying to use lirc_mceusb2, which is wrong) anyone know how to fix this?  I cannot downgrade to 9.04 and my wife won't run this thing without a remote.

---

### Post by tacman2k on 2009-10-11
I am having the same problem.

I was able to use my remote control and IR blaster using this tutorial:

[http://www.blushingpenguin.com/mark/blog/?p=24](http://www.blushingpenguin.com/mark/blog/?p=24)


Unfortunately lirc0.8.5 does not compile with the current kernel.

I tried booting into the old jaunty kernel (2.6.29) but it does not boot up.

LIRC 0.8.6 is out now and compiles with the new kernel for Karmic, but I have not found a patch for it.

I tried contacting the guy who made the tutorial, but so far no response.

I would like to get this remote working.


Im considering getting a new remote if I can't. Any suggestions?

---

### Post by bsntech on 2009-10-17
I just built a new box with 64-bit on it and finished setting stuff up today.  The remote worked for me as well using 9.04 Jaunty, but now in 9.10 Karmic with all of the updates as of today, it is not working.

I opened a bug for this as I hope it will be fixed soon.  I don't want to have to put my old PVR-150 card in just to use it for the remote - but heck, it may not even work in Karmic either!

[https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/454371]("https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/454371")

---

### Post by telseth on 2009-10-19
Yeah, I had to throw my old PVR-250 back in there.  Lucky I didn't toss it.

---

### Post by bsntech on 2009-10-19
This does suck - why all of a sudden did 9.10 break the HVR-1600 and WinTV-Go Plus IR receivers/transmitters?

I've ordered an HVR-1250 to put in this computer so I have two digital cards since I'm Finding that I'm recording everything on the digital OTA now - and will eventually get rid of our basic cable and save $15 a month.  So, now I'm going to have three TV tuner cards in the system when only two are used for capture.

Add this on top of an add-in USB PCI card that I'm going to have to put in now because of either a hardware or software bug in Ubuntu causing the MCP78S chipset USB ports to not work after an intermittent period of time or unless they are plugged in prior to Ubuntu booting up.  I just got this ECS GF8200A motherboard with a built-in GeForce 8200 video card to make use of VDPAU - and now I've got more problems to circumvent.

Also the GeForce 8200 card with 512 MB shared memory works very well with VDPAU and the 180.x.36 nVidia drivers in Ubuntu.  There is a little bit of tearing, but it isn't all that terrible on 720p and 1080p broadcasts.  I have the VDPAU profiles setup accordingly:

< (less than) W: 1080     H: 720    - Use Advanced 2x deinterlacer
>= (greater than or equal to) W: 0 H: 720 - Use Temporal 2x deinterlacer

Order is important with the above.

---

### Post by gordon ottershaw on 2009-10-25
Hello All,

After about a week of reading forum posts, the Hvr-1600 model 1199 grey remote finally generates output to a terminal window using the irw command.

No luck at all getting a working channel changing script or blaster function.  The only good news is that I know for a fact that the hardware works because I configured all of it in XP before I tried to run Mythbuntu.  IF its any consolation, Hauppauge's software is only marginally better than linux.  I just took out the XP hard drive and installed a new drive to load Mythbuntu.  BTW the IR Blaster has a red led that flashes when it is working(at least on this unit).  So IF the driver EVER starts working, I'll be able to see it.

The remote still won't change channels on my Motorola 2244 cable box, but at least it does something.

Configuring the Blaster should not be this difficult.  Isn't the Hvr-1600 a popular card?

---

### Post by resolost on 2009-10-30
how were you able to get the remote to work in irw?

---

### Post by Indi.N on 2009-11-06
The breakage of the lirc_i2c module happens at a kernel >= 2.6.28, where 0.8.4a (old default 9.04 package) is no longer usable, due to i2c changes in the kernel mainline.  
I've been following this issue for several months as I moved to a >= 2.6.30 kernel quite a while back for various other reasons.  The actual IR sensor driver resides in cx18_i2c, which is part of the V4L-DVB subsystem.



It seems that there has been a flurry of changes surrounding i2c drivers in both the kernel, in lirc, and in the v4l-dvb code, but I was surprised to find that I could avoid the nonfunctional lirc_i2c/i2c_dev issues by running ir-kbd-i2c instead. 

I have not tried 9.10, and all the shiny new (more) up to date packages, so it might be worth trying a modprobe ir-kbd-i2c and checking your dmesg etc.

The following worked for me:


1. Get a 2.6.31 kernel loaded (possible a 2.6.30 would work; have not tried)[INDENT][http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.31.5/ ]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.31.5/")

or do whatever you prefer to update your kernel.
Reboot
 
[/INDENT]2. Get the latest version of v4l-dvb[INDENT]hg clone [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb)
cd v4l-dvb
make
make install

I should note that to get a full compilation of all the v4l modules, I needed to go comment out some entries for a firedtv module (in a makefile) that was failing to build. I've not pulled any updates for a few days so perhaps that is fixed? YMMV with code pulled from live repos.

[/INDENT]3. Get 0.8.6 lirc source installed.[INDENT][http://prdownloads.sourceforge.net/lirc/lirc-0.8.6.tar.bz2](http://prdownloads.sourceforge.net/lirc/lirc-0.8.6.tar.bz2)
I have 0.8.6 installed via apt, and you should too.

[/INDENT][INDENT]If you're going to be running setup.sh (yes you probably will) you're going to want to edit it to change line 338 to "    echo ./configure --prefix=/usr \\" >>$START so that you don't end up with the complied version ending up in the lirc default (/usr/local).


When you configure LIRC, you will want to choose "Linux input layer (/dev/input/
eventX)" (indicated by driver:devinput). Complete the build process via the script, make, sudo make install etc..


[/INDENT]So, go ahead and load ir-kbd-i2c and check it out.

 
 ```

indi@indulgent:~$sudo modprobe ir-kbd-i2c
Nov  3 21:10:45 indulgent kernel: [ ] input: i2c IR (CX23418 Z8F0811 Hauppau as /devices/virtual/input/input7
Nov 3 21:10:45 indulgent kernel: [ ] ir-kbd-i2c: i2c IR (CX23418 Z8F0811 Hauppau detected at i2c-0/0-0071/ir0 [cx18 i2c driver #0-0]
indi@indulgent:/etc/lirc$ cat /proc/bus/input/devices | grep -A6 "i2c IR"
N: Name="i2c IR (CX23418 Z8F0811 Hauppau"
P: Phys=i2c-0/0-0071/ir0
S: Sysfs=/devices/virtual/input/input6
U: Uniq=
H: Handlers=kbd event6 
B: EV=100003
B: KEY=10..

```Note the device node - /devices/virtual/input/input6
Stop lircd if you've got it running (sudo /etc/init.d/lirc stop, whatever)


```

indi@indulgent:sudo lircd -n --device=/dev/input/event6 --output=/var/run/lirc/lircd
lircd-0.8.6[]: lircd(devinput) ready, using /var/run/lirc/lircd
lircd-0.8.6[]: accepted new client on /var/run/lirc/lircd
lircd-0.8.6[]: initializing '/dev/input/event6'
indi@indulgent:~$irw
0000000080010161 00 Go HVR-1100
 
```Well, that would be mostly working. 

I changed my /etc/lirc/hardware.conf a little, and by adding ir-kbd-i2c to the lirc list of modules you get it to load on restart.  

```
REMOTE_MODULES="ir-kbd-i2c"
REMOTE_DEVICE="/dev/input/event6"

```Notes:  ir-kbd-i2c does not autoload (by previous design to prevent device conflicts), I seem to get incorrectly identified as a 1100, but I don't care, it works.  I did end up re-tweaking my ~/.lircrc slightly and modified the /usr/share/lirc/extras/more_remotes/hauppauge/lircd.conf.hauppauge a bit too.  I have not tried 9.10, but imagine that a similar process should work out, as the kernel versions/lirc/v4l stuff should all be similar.

---

### Post by dealcorn on 2009-11-21
When I run the command make in step 2, I get the error:

dea@e5300:~/v4l-dvb$ make
make -C /home/dea/v4l-dvb/v4l 
make[1]: Entering directory `/home/dea/v4l-dvb/v4l'
creating symbolic links...
make -C firmware prep
make[2]: Entering directory `/home/dea/v4l-dvb/v4l/firmware'
make[2]: Leaving directory `/home/dea/v4l-dvb/v4l/firmware'
make -C firmware
make[2]: Entering directory `/home/dea/v4l-dvb/v4l/firmware'
make[2]: Nothing to be done for `default'.
make[2]: Leaving directory `/home/dea/v4l-dvb/v4l/firmware'
Kernel build directory is /lib/modules/2.6.28-11-generic/build
make -C /lib/modules/2.6.28-11-generic/build SUBDIRS=/home/dea/v4l-dvb/v4l  modules
make: Entering an unknown directory
make: *** /lib/modules/2.6.28-11-generic/build: No such file or directory.  Stop.
make: Leaving an unknown directory
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/dea/v4l-dvb/v4l'
make: *** [all] Error 2

Am I in the correct Kernel build directory and how do I configure it properly?

---

### Post by bnhrobotics on 2010-03-24
Is the kernel problem still around? I just got an HVR-1600. I am hoping to get the remote working, but I dont want to waste time if its not possible. Thanks

---

### Post by joejoe148 on 2010-04-27
I have just set up an ubuntu/myth box with 9.10 64bit and my remote doesnt work.  I always seem to find out about problems after I experience them...I need be able to see the future a little better.  I see that it is broken in this release but I am not clear if it is fixed in 10.04 or works in 9.04.  I briefly had 9.04 working but the hardware wasnt robust enough...so I built this amd64 box and went ahead and put 9.10 on it.  

Any advice on the best way to resolve the remote issue?  buy a separate remote and dump the included one?  downgrade to 9.04? upgrade to 10.04? or sit tight for a bit and wait on a fix?

---

### Post by Weidbrewer on 2010-04-29
This thread is about to become important to me again...I'm going to be upgrading my backend to 10.04, which means I'll need to do it to my other machines using Myth...fantastic.  I'm just hoping my remote will still work.  It's going to be a week or two, but when I do it, I'll let you know what I experience on 10.04.

---

### Post by telseth on 2010-04-30
I have officially given up, I have my old pvr-350 in there for the IR.  But, after the upgrade to 10.04 that too died.

My suggestion is to do what I did and buy [a media center remote like this]("http://www.newegg.com/Product/Product.aspx?Item=N82E16880101003") and never have to worry about upgrading again.

---

### Post by Swegononego on 2010-05-04
I just edited my hardware.conf file as per this thread (Kevin Worth 2010-05-03) and my remote worked after reboot:

[https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/454371](https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/454371)

Mythbuntu 10.04 64bits with latest updates.

I have the grey top HVR1600 remote. arrows, enter, volume, mute and the numbers work; other buttons don't work.

---

### Post by azmanam on 2010-05-09
confirmed.

Grey Hauppauge remote works with 1600 tuner card following the instructions in post #21 at:

[https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/454371](https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/454371)

in short:

```
$ sudo gedit /etc/lirc/hardware.conf
```

change settings to match following:

```
My new config (that works now on 10.04)
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Hauppauge TV card"
REMOTE_MODULES="ir_kbd_i2c lirc_dev lirc_i2c"
REMOTE_DRIVER="dev/input"
REMOTE_DEVICE="/dev/input/event<#>"
REMOTE_LIRCD_CONF="hauppauge/lircd.conf.hauppauge"
REMOTE_LIRCD_ARGS=""
```

**note: make the <#> in REMOTE_DEVICE the same as the highest number listed after event in /dev/input**

If working, should get dmesg output similar to the following 

```
$ dmesg | grep i2c
[ 1257.753138] input: i2c IR (CX23418 Z8F0811 Hauppau as /devices/virtual/input/input6
[ 1257.753306] ir-kbd-i2c: i2c IR (CX23418 Z8F0811 Hauppau detected at i2c-0/0-0071/ir0 [cx18 i2c driver #0-0]
```

reboot and your remote should work.  I did have to remap a few keys, but remote works!  (to remap, Frontend:Utilities/Setup:Edit Keys:TV Playback)

---

### Post by pwhalley on 2010-05-25
Azmanam,

I hope you (and others) are still watching this thread.  I need some guidance.  

I have struggled to get the analog and ir portions of this card working for some time with myth with limited success.  ATSC was less a problem.

I now have both sides recording simultaneously without apparent issues. But I am fairly lost on the IR side.  Once I get to the place where I can detect any IR reliably and send out what I need to I think I will be fairly ok getting some kind of remote properly config'd in LIRC but I need some guidance to get there (if I am going to get it to work this year that is)! 

I installed CX18 via mercurial (latest I think).

This is what dmesg is telling me now.  See after for what I had before reboot.

Note Green sections in code.

```
 dmesg | grep i2c
[   22.837036] i2c i2c-0: nForce2 SMBus adapter at 0x5000
[   22.837062] i2c i2c-1: nForce2 SMBus adapter at 0x5100
[   24.559175] tuner 3-0061: chip found @ 0xc2 (cx18 i2c driver #0-1)
[COLOR="Green"][   24.621219] cs5345 2-004c: chip found @ 0x98 (cx18 i2c driver #0-0)[/COLOR]

```

and 

```
dmesg | grep cx18
[   23.489466] cx18:  Start initialization, version 1.4.0
[   23.489531] cx18-0: Initializing card 0
[   23.489536] cx18-0: Autodetected Hauppauge card
[   23.526166] cx18 0000:02:06.0: PCI INT A -> Link[APC3] -> GSI 18 (level, low) -> IRQ 18
[   23.526177] cx18-0: Unreasonably low latency timer, setting to 64 (was 32)
[   23.527781] cx18-0: cx23418 revision 01010000 (B)
[   24.069534] cx18-0: Autodetected Hauppauge HVR-1600
[   24.069537] cx18-0: Simultaneous Digital and Analog TV capture supported
[   24.349002] IRQ 18/cx18-0: IRQF_DISABLED is not guaranteed on shared IRQs
[   24.559175] tuner 3-0061: chip found @ 0xc2 (cx18 i2c driver #0-1)
[COLOR="Green"][   24.621219] cs5345 2-004c: chip found @ 0x98 (cx18 i2c driver #0-0)[/COLOR]
[   24.670835] cx18-0: Registered device video0 for encoder MPEG (64 x 32.00 kB)
[   24.670839] DVB: registering new adapter (cx18)
[   24.986395] cx18-0: DVB Frontend registered
[   24.986398] cx18-0: Registered DVB adapter0 for TS (32 x 32.00 kB)
[   24.986435] cx18-0: Registered device video32 for encoder YUV (20 x 101.25 kB)
[   24.986464] cx18-0: Registered device vbi0 for encoder VBI (20 x 51984 bytes)
[   24.986492] cx18-0: Registered device video24 for encoder PCM audio (256 x 4.00 kB)
[   24.986496] cx18-0: Initialized card: Hauppauge HVR-1600
[   24.986527] cx18:  End initialization
[   25.056697] cx18 0000:02:06.0: firmware: requesting v4l-cx23418-cpu.fw
[   25.224859] cx18-0: loaded v4l-cx23418-cpu.fw firmware (158332 bytes)
[   25.271231] cx18-alsa: module loading...
[   25.486492] cx18 0000:02:06.0: firmware: requesting v4l-cx23418-apu.fw
[   25.615455] cx18-0: loaded v4l-cx23418-apu.fw firmware V00120000 (141200 bytes)
[   25.621780] cx18-0: FW version: 0.0.74.0 (Release 2007/03/12)
[   25.952035] cx18 0000:02:06.0: firmware: requesting v4l-cx23418-cpu.fw
[   26.179906] cx18 0000:02:06.0: firmware: requesting v4l-cx23418-apu.fw
[   26.509698] cx18 0000:02:06.0: firmware: requesting v4l-cx23418-dig.fw
[   26.831059] cx18-0 843: loaded v4l-cx23418-dig.fw firmware (16382 bytes)
[   26.855035] cx18-0 843: verified load of v4l-cx23418-dig.fw firmware (16382 bytes)
```

This is what I had before editing my /lirc/hardware.config to your post.  Another possibly notable difference is that when I rebooted after the edit the system hung (I think on shutdown but can't be certain).  There was no disk activity for many minutes so I killed power...  [COLOR="DeepSkyBlue"]The following dmesg is from before the edit. [/COLOR]

```
[COLOR="Red"][/COLOR]

[84930.003381] IR NEC protocol handler initialized
[84930.070251] IR RC5(x) protocol handler initialized
[84930.088918] IR RC6 protocol handler initialized
[84930.108018] Registered IR keymap rc-hauppauge-new
[84930.108056] BUG: unable to handle kernel NULL pointer dereference at (null)
[84930.108062] IP: [<fd60fd7e>] ir_register_class+0x3e/0x190 [ir_core]
[84930.108071] *pde = 00000000 
[84930.108075] Oops: 0000 [#1] SMP 
[84930.108078] last sysfs file: /sys/module/ir_core/initstate
[84930.108081] Modules linked in: ir_rc6_decoder rc_hauppauge_new ir_rc5_decoder ir_kbd_i2c(+) ir_nec_decoder ir_common ir_core binfmt_misc cx18_alsa mxl5005s snd_intel8x0 snd_ac97_codec s5h1409 ac97_bus tuner_simple tuner_types snd_pcm_oss nfsd cs5345 snd_mixer_oss exportfs tuner snd_pcm fbcon tileblit font bitblit softcursor nfs vga16fb snd_seq_dummy lockd nfs_acl vgastate snd_seq_oss auth_rpcgss snd_seq_midi cx18 snd_rawmidi sunrpc snd_seq_midi_event dvb_core snd_seq cx2341x snd_timer v4l2_common snd_seq_device nouveau ttm videodev v4l1_compat drm_kms_helper ppdev snd tveeprom drm i2c_algo_bit lp parport_pc parport psmouse soundcore nvidia_agp serio_raw snd_page_alloc shpchp agpgart i2c_nforce2 e1000 sata_nv pata_amd floppy
[84930.108130] 
[84930.108134] Pid: 7998, comm: modprobe Not tainted (2.6.32-21-generic #32-Ubuntu)  
[84930.108137] EIP: 0060:[<fd60fd7e>] EFLAGS: 00010246 CPU: 0
[84930.108141] EIP is at ir_register_class+0x3e/0x190 [ir_core]
[84930.108144] EAX: 00000000 EBX: ef429c00 ECX: 00000000 EDX: 00000100
[84930.108147] ESI: f5481000 EDI: 00000000 EBP: d7bb7dd4 ESP: d7bb7da8
[84930.108149]  DS: 007b ES: 007b FS: 00d8 GS: 00e0 SS: 0068
[84930.108153] Process modprobe (pid: 7998, ti=d7bb6000 task=f2e84ce0 task.ti=d7bb6000)
[84930.108155] Stack:
[84930.108156]  00000246 fd60fa47 c24054e0 fd60fa47 00bb7dc0 00000170 f5481000 0000003d
[84930.108163] <0> fd40e068 00000030 f5481000 d7bb7e0c fd60fb7c 00000074 00000000 fe8e3f6b
[84930.108169] <0> c0588f42 fd610c11 00000292 ef429d3c ef429d20 ef429c00 f6903b40 f6903b4c
[84930.108175] Call Trace:
[84930.108181]  [<fd60fa47>] ? __ir_input_register+0x167/0x350 [ir_core]
[84930.108186]  [<fd60fa47>] ? __ir_input_register+0x167/0x350 [ir_core]
[84930.108191]  [<fd60fb7c>] ? __ir_input_register+0x29c/0x350 [ir_core]
[84930.108200]  [<c0588f42>] ? printk+0x1d/0x23
[84930.108206]  [<fe8e39cc>] ? ir_probe+0x37c/0x568 [ir_kbd_i2c]
[84930.108215]  [<c04728a4>] ? i2c_device_probe+0xb4/0xd0
[84930.108219]  [<fe8e3650>] ? ir_probe+0x0/0x568 [ir_kbd_i2c]
[84930.108227]  [<c03e684d>] ? really_probe+0x4d/0x140
[84930.108233]  [<c03ed15e>] ? pm_runtime_barrier+0x4e/0xc0
[84930.108237]  [<c03e697c>] ? driver_probe_device+0x3c/0x60
[84930.108241]  [<c03e6a21>] ? __driver_attach+0x81/0x90
[84930.108245]  [<c03e5e63>] ? bus_for_each_dev+0x53/0x80
[84930.108250]  [<c03e671e>] ? driver_attach+0x1e/0x20
[84930.108253]  [<c03e69a0>] ? __driver_attach+0x0/0x90
[84930.108257]  [<c03e60e5>] ? bus_add_driver+0xd5/0x280
[84930.108262]  [<c0472570>] ? i2c_device_remove+0x0/0x60
[84930.108266]  [<c03e6d1a>] ? driver_register+0x6a/0x130
[84930.108270]  [<c047389f>] ? i2c_register_driver+0x2f/0x90
[84930.108274]  [<f81e7012>] ? ir_init+0x12/0x14 [ir_kbd_i2c]
[84930.108278]  [<c0101131>] ? do_one_initcall+0x31/0x190
[84930.108282]  [<f81e7000>] ? ir_init+0x0/0x14 [ir_kbd_i2c]
[84930.108289]  [<c0182340>] ? sys_init_module+0xb0/0x210
[84930.108293]  [<c01033ec>] ? syscall_call+0x7/0xb
[84930.108295] Code: 00 89 c6 8d 80 a0 07 00 00 e8 7f 67 dd c2 ba 00 01 00 00 89 c3 b8 0c 14 61 fd e8 6e ac d3 c2 89 c7 85 ff 78 6f 8b 83 44 01 00 00 <8b> 08 85 c9 74 74 c7 43 30 2c 12 61 fd c7 83 10 01 00 00 e0 11 
[84930.108325] EIP: [<fd60fd7e>] ir_register_class+0x3e/0x190 [ir_core] SS:ESP 0068:d7bb7da8
[84930.108331] CR2: 0000000000000000
[84930.108408] ---[ end trace dc44f6554b08e598 ]---
[84930.162777] IR JVC protocol handler initialized
[84930.211154] IR Sony protocol handler initialized
```

Can anyone offer any insights?  Again, IR send is more important to me on the backend but having receive will be useful and there is no point in getting send working only to break it getting receive to work...

If I don't need to use mercurial for cx18 to get all this working, ok but how do I go back?  

Thanks to all who take the time to read and a double portion for any replies.

Peter

---

### Post by kpl388 on 2010-06-04
Peter, 

I am having the exact same problem you are. Have you made any progress getting this to work?

Best,
Kyle

---

### Post by Swegononego on 2010-06-05
I don't know if it's the same problem I had at some point but maybe this will help.

When I first tried to change the hardware .conf I put in event3 cause I though it was my IR event. On reboot I had a conflict between my keyboard and remote and neither would work. So I plugged in a PS2 keyboard from another computer and it worked. I managed to change the hardware.conf to event5, rebooted and everything worked fine, almost all the buttons on my remote worked too.

use this command to find out what event"n" you should use:

cat /proc/bus/input/devices

look for lines similar to these

I: Bus=0018 Vendor=0000 Product=0000 Version=0000
N: [COLOR=Red]**Name="i2c IR (CX23418 Z8F0811 Hauppau"**[/COLOR]
P: Phys=i2c-1/1-0071/ir0
S: Sysfs=/devices/virtual/input/input5
U: Uniq=
H: Handlers=kbd[COLOR=Red] **event5 **[/COLOR]
B: EV=100003
B: KEY=100fc312 214a80200000000 0 18000 41a800004801 9e168000000000 10000ffc

hope this helps

---

### Post by TwiztedMatt1007 on 2010-06-07
I have tried to do the above tutorial but, it appears the system is not detecting the receiver? Do I need to install some firmware or something? I do have the latest v4l drivers installed through another tutorial. I am running a fresh install, aka no upgrade, of Mythbuntu 10.04 64-Bit and have not done any fumbling with any of the stuff talked about above outside of, well, what was said above to do. I have since put my hardware.config file back to what it was before editing it just to be sure I start with default settings. I did install gedit so the above sudo command does work. I don't know if the system is just not seeing the receiver or what but, this is what I get with: cat /proc/bus/input/devices

```
matthew@Matthew-DVR:~$ cat /proc/bus/input/devices

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=PNP0C0C/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
U: Uniq=
H: Handlers=kbd event0 
B: EV=3
B: KEY=10000000000000 0

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=LNXPWRBN/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
U: Uniq=
H: Handlers=kbd event1 
B: EV=3
B: KEY=10000000000000 0

I: Bus=0017 Vendor=0001 Product=0001 Version=0100
N: Name="Macintosh mouse button emulation"
P: Phys=
S: Sysfs=/devices/virtual/input/input2
U: Uniq=
H: Handlers=mouse0 event2 
B: EV=7
B: KEY=70000 0 0 0 0
B: REL=3

I: Bus=0003 Vendor=062a Product=0201 Version=0110
N: Name="USB-compliant keyboard"
P: Phys=usb-0000:00:13.0-1/input0
S: Sysfs=/devices/pci0000:00/0000:00:13.0/usb5/5-1/5-1:1.0/input/input3
U: Uniq=
H: Handlers=kbd event3 
B: EV=120013
B: KEY=1000000000007 ff9f207ac14057ff febeffdfffefffff fffffffffffffffe
B: MSC=10
B: LED=7

I: Bus=0003 Vendor=062a Product=0201 Version=0110
N: Name="USB-compliant keyboard"
P: Phys=usb-0000:00:13.0-1/input1
S: Sysfs=/devices/pci0000:00/0000:00:13.0/usb5/5-1/5-1:1.1/input/input4
U: Uniq=
H: Handlers=kbd mouse1 event4 
B: EV=1f
B: KEY=fe00000 0 0 877fff002c3027 bf00444400000000 1 c040a27c000 267bfad941dfed 9e000000000000 0
B: REL=143
B: ABS=100000000
B: MSC=10

I: Bus=0003 Vendor=15d9 Product=0a4c Version=0111
N: Name=" USB OPTICAL MOUSE"
P: Phys=usb-0000:00:13.0-2/input0
S: Sysfs=/devices/pci0000:00/0000:00:13.0/usb5/5-2/5-2:1.0/input/input5
U: Uniq=
H: Handlers=mouse2 event5 
B: EV=17
B: KEY=70000 0 0 0 0
B: REL=103
B: MSC=10

I: Bus=0001 Vendor=10ec Product=0885 Version=0001
N: Name="HDA Digital PCBeep"
P: Phys=card0/codec#0/beep0
S: Sysfs=/devices/pci0000:00/0000:00:14.2/input/input6
U: Uniq=
H: Handlers=kbd event6 
B: EV=40001
B: SND=6
```No, I am not running a Mac mouse so I don't know if that is just what normally starts up for everyone or that is what the system is recognizing my remote receiver as. I tried events 2-6 with no success. Any ideas? As a note, I am very new to Linux so if I am told to do something, please make it as newb friendly as possible.


Hardware:

Motherboard: GIGABYTE GA-MA785GM-US2H Version 1.1 Using the integrated  graphics with ATI proprietary drivers. The integrated graphics is a  Radeon HD 4200.

Tuner Card: Hauppauge HVR-1600

Ram: 2GB A-DATA AD2U800B1G5-DRH

Processor: 2.9GHz Athlon II X3 ADX435WFGIBOX

---

### Post by killsforpie on 2010-06-09
Hey Twisted, I think I am almost exactly where you are. I followed step 6 here: [http://www.blushingpenguin.com/mark/blog/?p=24](http://www.blushingpenguin.com/mark/blog/?p=24) and then when I rebooted I could run "modprobe ir-kbd-i2c &". This takes two tries, first produces a bunch of errors:
```
Message from syslogd@linux-xpsr at Jun  9 14:08:33 ...
 kernel:[   52.522351] Oops: 0000 [#1] PREEMPT SMP    

Message from syslogd@linux-xpsr at Jun  9 14:08:33 ...
 kernel:[   52.522366] last sysfs file: /sys/module/ir_core/initstate

Message from syslogd@linux-xpsr at Jun  9 14:08:33 ...
 kernel:[   52.522815] Process modprobe (pid: 3858, ti=eb930000 task=eb49a670 task.ti=eb930000)                                           

Message from syslogd@linux-xpsr at Jun  9 14:08:33 ...
 kernel:[   52.522830] Stack:                         

Message from syslogd@linux-xpsr at Jun  9 14:08:33 ...
 kernel:[   52.522925] Call Trace:                    

Message from syslogd@linux-xpsr at Jun  9 14:08:33 ...
 kernel:[   52.523006] Code: 05 d1 8b 55 d8 e9 a8 fd ff ff 8b 55 dc 8b 45 e0 e8 7b ef 3d d1 89 f8 e8 54 f8 29 d1 85 c0 89 c2 78 ad 8b 55 e8 8b 82 e0 00 00 00 <83> 38 01 74 4b 31 d2 83 3d a0 a6 2b ef 00 0f 8e 73 fd ff ff 8b                                                      

Message from syslogd@linux-xpsr at Jun  9 14:08:33 ...
 kernel:[   52.523006] EIP: [<ef2b791b>] __ir_input_register+0x2ab/0x3c0 [ir_core] SS:ESP 0068:eb931d70                                   

Message from syslogd@linux-xpsr at Jun  9 14:08:33 ...
 kernel:[   52.523006] CR2: 0000000000000000          

[1]+  Killed                  modprobe ir-kbd-i2c

```

Then I ran it again and was able to get the event number (8 in my case). Rebooted, ran "modprobe ir-kbd-i2c &" twice more and I get more info:

```
# dmesg | grep i2c
[    5.894085] cx18 i2c driver #0-0: Test OK
[    5.894169] cx18 i2c driver #0-1: Test OK
[    6.075329] tuner 1-0061: chip found @ 0xc2 (cx18 i2c driver #0-1)
[    6.077692] cs5345 0-004c: chip found @ 0x98 (cx18 i2c driver #0-0)
[   52.522040] input: i2c IR (Hauppauge HVR-1600) as /devices/virtual/input/input8
[   52.522381] Modules linked in: rc_hauppauge_new ir_kbd_i2c(+) ir_common ir_core ip6t_LOG xt_tcpudp xt_pkttype xt_physdev ipt_LOG xt_limit rfcomm sco bridge stp llc bnep l2cap snd_pcm_oss snd_mixer_oss snd_seq snd_seq_device edd af_packet cpufreq_conservative cpufreq_userspace cpufreq_powersave powernow_k8 ip6t_REJECT nf_conntrack_ipv6 ip6table_raw xt_NOTRACK ipt_REJECT xt_state iptable_raw iptable_filter ip6table_mangle nf_conntrack_netbios_ns nf_conntrack_ipv4 nf_conntrack nf_defrag_ipv4 ip_tables ip6table_filter ip6_tables x_tables fuse loop dm_mod uinput cx18_alsa mxl5005s s5h1409 tuner_simple tuner_types cs5345 tuner snd_hda_codec_realtek ohci1394 snd_hda_intel cx18 dvb_core i2c_algo_bit cx2341x v4l2_common videodev v4l1_compat tveeprom usblp btusb ati_agp r8169 i2c_piix4 bluetooth snd_hda_codec snd_hwdep snd_pcm snd_timer ieee1394 nvidia(P) rfkill snd snd_page_alloc pcspkr sg wmi floppy button serio_raw ext4 jbd2 crc16 fan processor ide_pci_generic atiixp ide_core ata_generic pata_atiixp thermal thermal_sys [last unloaded: preloadtrace]
[   52.522962]  [<ef2e23cc>] ir_probe+0x37c/0x5a0 [ir_kbd_i2c]
[   52.522987]  [<c056cb9d>] i2c_device_probe+0xbd/0x120
[   52.523006]  [<c056dd83>] i2c_register_driver+0x33/0xd0
[   52.523006]  [<ef2b2020>] ir_init+0x20/0x33 [ir_kbd_i2c]

```

But running irw doesn't find any buttons. 

I actually don't care that much about the remote anymore as I got a bluetooth adapter and am just trying to see if I can get the infrared part of the blaster to broadcast for my wiimote. The wiimote configuration has been WAY easier than the hauppauge remote. The IR bar that came with the Wii works but requires the wii to be on.

---

