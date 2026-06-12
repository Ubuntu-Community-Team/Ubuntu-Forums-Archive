---
title: "sound card problem es1869 armada 1700"
date: 2007-05-09
forum: Multimedia &amp; Video
---

### Post by toniju on 2007-05-09
Hi everybody,

I have tried to solve my sound card problems for a while now and do not have solved it. In the beginning I have to say, that I am an absolute beginner with Linux. I used Windows for about 10 years, so I am clumsy even with the basics :( 

When I switched from XP to Ubuntu with my old computer I thought it would not be so difficult, but just in the beginning the problems started: To find the right resolution took me nearly two weeks. Now I am battling with the sound card :( 

Basic dates: Compaq Armada 1700, sound card es1869

Here is what I have done so far:

- Went to the well written "Comprehensive Sound Problem Solutions Guide" from LordRaiden.

- Did the Basic Steps 1-4
-> (1) aplay -l   "aplay: device_list:222: no soundcards found..."
-> (2) lspci -v   NO SOUND CARD FOUND
-> (3)  ALSA driver exists
-> (4) sudo modprobe snd-  SOUND CARD FOUND IN THE LIST
* "...A success here means that your soundcard was installed, but it was not being loaded. Now you have loaded it for the current session..." HOW IS THAT POSSIBLE? DID NOT WORK EVEN WHEN I RESTARTED

*"...you will have to edit /etc/modules..." "...Add only the name of the module to be loaded at the end of the file..." WHERE IS THE END OF THE FILE. BEFORE THERE WAS "lp" STANDING

-> 
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
-> Tried every variation and added snd-es18xx

What are I missing? 
Code "...alsamixer..." do not work. 
Tried to install it (?) 
GStreamer?

"...No volume control GStreamer plugins and/or devices found..."

Hope you can help me.

Regards Toni:KS

---

### Post by LDRoamer on 2007-05-09
What version are you using. I had the sound working perfectly on my Armada 1750 with an es1869 chip under Edgy 6.10 but an upgrade to Feisty 7.04 has killed my sound. If your running Fiesty I haven't found a fix yet but there is a way to get it running under earlier versions by manually installing the driver. Try a search for es1869 on the forums and you should turn up some information on what you need to do. I don't have the information handy right now or would post it for you.

---

### Post by toniju on 2007-05-09
Thanks LDRoamer for your answer.

I actually have the Edgy 6.10 version and have not upgraded yet and as it look like I shouldn't do it at the moment if I want to have my sound card working.

Strange that the driver is working for your computer and not for mine as they are quite similar... Manually driver installing might be challenging in my Linux-stadium but I would be ready to learn it if ther are good instructions some were... :) 

I have still another computer with XP, so I do not depend on my laptop to hear music etc. but it would be nice to get it work, so that I can present Ubuntu also to my friends :) 

Toni

---

### Post by toniju on 2007-05-10
Tried now following:

~$ sudo modprobe snd-es18xx 
.bash_history              .gtk-bookmarks
.bash_logout               .gtkrc-1.2-gnome2
.bash_profile              .hwdb
.bashrc                    .ICEauthority
.config/                   .icons/
core.4832                  .macromedia/
core.4868                  .metacity/
Desktop/                   .mozilla/
DicOOo-1.7.sxw             .nautilus/
.dmrc                      .openoffice.org2/
es1869.odt                 .recently-used
.esd_auth                  .recently-used.xbel
.evolution/                snd-es18xx
Examples/                  .sudo_as_admin_successful
.fonts.cache-1             .themes/
.gconf/                    .thumbnails/
.gconfd/                   .Trash/
.gksu.lock                 .update-manager/
.gnome/                    .update-notifier/
.gnome2/                   .Xauthority
.gnome2_private/           .xmms/
.gstreamer-0.10/           .xsession-errors


-> es1869.odt recently used ?
-> .evolution/ snd-es18xx ?

Still unsure where to put snd-es18xx in /etc/modules... Now it took ip away:

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.
snd-es18xx

Computer is piiping on errors but that is no success (?). Can still not playing anything...:confused: ](*,) ](*,) ](*,)

---

### Post by toniju on 2007-05-10
I tried again a few things but it did not work. If I continue this way I have to reload Ubuntu again, as I do not really know what I am doing and maybe make it worse...

One more thing: With my Compaq I can not go to BIOS. I tried it with every possible method I could think of... When I looked up the net I got the impression that this is a common problem for this laptop (?)

Anyway... should the alsamixer come with the installation CD? With code it do not work for me. I downloaded GNOME ALSA mixer through add/remove application. Is this the same.?

I tried the Windows method and inserted the installation CD and hoped to find the missing driver... Everything stayed the same...

Should I try some ohter Linux release?

Sorry for this basic questions, but I am really NEW with Ubuntu and Linux. Windows is for beginners so much easier (?) Of course you never learn what you are actually doing and can not control anything...

Toni

I

---

### Post by LDRoamer on 2007-05-10
This link should help point you in the right direction.

[https://help.ubuntu.com/community/DebuggingSoundProblems](https://help.ubuntu.com/community/DebuggingSoundProblems)

I think you need to add a configuration file to etc/modprobe.d to pass the right options to the driver so it will load correctly. 

In terms of your bios - old Compaq aramada laptops access the bios via a piece of software. It came preloaded on a small partition on the hard drive. You would see a white flashing cursor during boot up and then you had to hit one of the F keys (I don't remember which one).  A lot of old compaqs had there hard drives formatted by people who didn't know this and erased the partition. However the software is availble from the HP website (HP bought Compaq).  Look up your computer on the web site and look for something with a name like setup disk for compaq portables or some such thing. You can download this and create a diskette. Boot from the diskette and it will give you access to the bios.

However I think if you are using edgy if you add the snd_es18xx to modules - just add it as the last line in the file - and then create a file in modprobe.d that contains the correct parameters I bet it would work. 

The weblink above uses the es1869 card as an example so it should help you. The only thing I had to change was in the example they indicated that dma2=5.  On my machine it is dma2=0.

Give that a try and see if it helps

---

### Post by toniju on 2007-05-12
Hi again and thanks for your replay LDRoamer,

Yes I heard about the software to get BIOS on Compaq. Unfortunately I do not have floppy drive on my laptop, so that makes it a little bit difficult... I hope I can solve the problem without to get to BIOS. A stupid idea to save the BIOS soft ware.....

So I visited your link and played around with some suggestions.

In the section "Manually installing sound drivers" was most interesting for me. I agonized e.g. that I wrote always snd-18xx instead of snd_18xx. This had some kind of effect as now I could get some modinfo, which I could not get before:

->
~$ modinfo snd_es18xx
filename:       /lib/modules/2.6.17-11-generic/updates/alsa/isa/snd-es18xx.ko
author:         Christian Fischbach <fishbach@pool.informatik.rwth-aachen.de>, Abramo Bagnara <abramo@alsa-project.org>
description:    ESS ES18xx AudioDrive
license:        GPL
vermagic:       2.6.17-11-generic SMP mod_unload 586 REGPARM gcc-4.1
depends:        snd-pcm,snd,snd,snd-opl3-lib,snd-mpu401-uart
alias:          pnp:cESS1868dESS1868dESS0000*
alias:          pnp:cESS1868dESS8601dESS8600*
alias:          pnp:cESS1868dESS8611dESS8610*
alias:          pnp:cESS0003dESS1869dESS0006*
alias:          pnp:cESS1869dESS1869dESS0006*
alias:          pnp:cESS1878dESS1878dESS0004*
alias:          pnp:cESS1879dESS1879dESS0009*
srcversion:     1A2A6AF73D4242CEFFD289F
parm:           dma2:DMA 2 # for ES18xx driver. (array of int)
parm:           dma1:DMA 1 # for ES18xx driver. (array of int)
parm:           irq:IRQ # for ES18xx driver. (array of int)
parm:           fm_port:FM port # for ES18xx driver. (array of long)
parm:           mpu_port:MPU-401 port # for ES18xx driver. (array of long)
parm:           port:Port # for ES18xx driver. (array of long)
parm:           isapnp:PnP detection for specified soundcard. (array of bool)
parm:           enable:Enable ES18xx soundcard. (array of bool)
parm:           id:ID string for ES18xx soundcard. (array of charp)
parm:           index:Index value for ES18xx soundcard. (array of int)

So how does this look like?

I also agonized that I had already some kind of sound card file installed on modprobe.d/soudncard/ snd-es18xx due to an suggestion of this forum...

Inside you find "... alias sound-slot-0 snd-card-0
alias snd-card-0 snd-es18xx
options snd-es18xx enable=1 isapnp=0 port=0x220 mpu_port=0x388 fm_port=0x330 irq=5 dma1=1 dma2=0..."
Nearly the same as you did mentioned...

Nevertheless I added, like your link described, a file named snd_es18xx in modprobe.d with the context: "...options snd_es18xx isapnp=0 port=0x220 mpu_port=0x330 dma1=1 dma2=0 irq=5 fm_port=0x388..."

The instructions of saving the parameters were a little bit confusing as there was no example: "...$ echo options [module-name] [module-options] | sudo tee /etc/modprobe.d/[module-name]..." I inserted the module name and module options (assumed this to be options: isapnp=0 port=0x220 mpu_port=0x330 dma1=1 dma2=5 irq=5 fm_port=0x388  as it look the same as the previously save file on modprobe.d/soundcards)

In the end following can be read in modprobe.d/snd_es18xx: "...options snd_es18xx isapnp=0 port=0x220 mpu_port=0x330 dma1=1 dma2=0 irq=5 fm_port=0x388..." 

If I want to run #aplay now this report appears:"... ALSA lib confmisc.c:670:(snd_func_card_driver) cannot find card '0'
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:391:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1070:(snd_func_refer) error evaluating name
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3947:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2146:(snd_pcm_open_noupdate) Unknown PCM default
aplay: main:547: audio open error: No such device..."

Here is interesting that card "0" is not  found and it came into my mind that maybe my pcmcia card is conflicting with the sound card?

When I try to run the speaker test following appears: "...~$ /usr/bin/speaker-test 

speaker-test 1.0.11

Playback device is default
Stream parameters are 48000Hz, S16_LE, 1 channels
Using 16 octaves of pink noise
ALSA lib confmisc.c:670:(snd_func_card_driver) cannot find card '0'
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:391:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1070:(snd_func_refer) error evaluating name
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3947:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2146:(snd_pcm_open_noupdate) Unknown PCM default
Playback open error: -19,No such device..."  100x :) 

Again card "0" not found...

So, am I already seeing the light in the end of the tunnel or is the black Linux hole sucking me up :confused: :) 

Toni  8-[

---

### Post by LDRoamer on 2007-05-12
I am not sure exactly what your problem is. Your machine and mine are very similar and it should work. Did you try using lspnp to try and detect your card? lspnp is not installed by default in Edgy so you need to manually install it. If you look at the link I gave you will see how it is used to detect the card. It, lspnp, will also show you what options you need to include in your snd_es18xx file in modprode.d.  If yours is like mine the bios has an alternate configuration which changes the settings. It is possible that yours are set to the alternate settings and you will need to change the options in the snd_es18xx file to match those of your machine. 

I think there is a trick to reset the bios to its defaults without  having the disk.  I don't remember it exactly but I reading about it. It is something like hold down the fn key and hit F11 repeatedly or maybe its just hit F11. You might find this site interesting:

[http://wireball.com/armada_1750_review.htm](http://wireball.com/armada_1750_review.htm)

It is a bunch of information on the Armada 1750 like I have . Some of this may be useful to you. I can't recall if the trick for resetting the bios is there or not though.

---

### Post by toniju on 2007-05-16
Hi,

Thanks LDRoamer again for your help. I am still at the same point as I was at the beginning :( :(  I am a little bit disappointed and surprised how hard it is to get a sound card working on Linux. I bought a UBS sound card for my desktop as the plugs are so hard to reach... I also had problems with XP to install the USB sound card, but I solved the problem in two hours... With this problem I have battled already over 40 hours. In that time I could have earned money for a new computer with Vista on it :( But I do not want to give up!!!!

I went to your link ( [https://help.ubuntu.com/community/DebuggingSoundProblems](https://help.ubuntu.com/community/DebuggingSoundProblems) ) and went through the steps, which were mentioned...

**"General Debugging"**

-> Can not check volume in alsamixer as it does not work... 
"Gnome Alsa Mixer" opens but is empty. 
"Alsamixergui" alsamixer: function snd_ctl_open failed for default: No such device.

-> ~$ cat /proc/asound/cards -> no soundcards 

-> Test different "Sound Servers": Go to System > Preferences > Multimedia Systems Selector. -> Multimedia Systems Selector is not at that place in my Ubuntu

-> If you can get absolutely no sound and you have an onboard sound chip you can try to disable it in the BIOS. This solves the problem is some cases. -> Can not get into BIOS

**"Manually installing sound drivers"**

[COLOR="Red"]~$ aplay --list-devices[/COLOR]
aplay: device_list:222: no soundcards found...

[COLOR="Red"]~$ lspci -v[/COLOR]
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (AGP disabled) (rev 02)
        Subsystem: Compaq Computer Corporation Armada 1700 Laptop System Chipset
        Flags: bus master, medium devsel, latency 64
        Memory at 50000000 (32-bit, prefetchable) [size=256M]

00:07.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
        Flags: bus master, medium devsel, latency 0

00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01) (prog-if 80 [Master])
        Flags: bus master, medium devsel, latency 64
        I/O ports at 1020 [size=16]

00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01) (prog-if 00 [UHCI])
        Flags: bus master, medium devsel, latency 64, IRQ 11
        I/O ports at 1000 [size=32]

00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
        Flags: medium devsel, IRQ 9

00:08.0 VGA compatible controller: Chips and Technologies F65555 HiQVPro (rev a8) (prog-if 00 [VGA])
        Subsystem: Compaq Computer Corporation Armada 1700 Laptop Display Controller
        Flags: stepping, medium devsel
        Memory at 40000000 (32-bit, non-prefetchable) [size=16M]
        [virtual] Expansion ROM at 18000000 [disabled] [size=256K]

00:11.0 CardBus bridge: Texas Instruments PCI1220 (rev 02)
        Subsystem: Compaq Computer Corporation Unknown device b047
        Flags: bus master, medium devsel, latency 168, IRQ 11
        Memory at 7fffe000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=00, secondary=01, subordinate=04, sec-latency=176
        Memory window 0: 10000000-11fff000 (prefetchable)
        Memory window 1: 12000000-13fff000
        I/O window 0: 00001400-000014ff
        I/O window 1: 00001800-000018ff
        16-bit legacy interface ports at 0001

00:11.1 CardBus bridge: Texas Instruments PCI1220 (rev 02)
        Subsystem: Compaq Computer Corporation Unknown device b047
        Flags: bus master, medium devsel, latency 168, IRQ 11
        Memory at 7ffff000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=00, secondary=05, subordinate=08, sec-latency=176
        Memory window 0: 14000000-15fff000 (prefetchable)
        Memory window 1: 16000000-17fff000
        I/O window 0: 00001c00-00001cff
        I/O window 1: 00002000-000020ff
        16-bit legacy interface ports at 0001

[COLOR="Red"]~$ lspnp -v[/COLOR]
01 PNP0401 ECP printer port
        irq 7
        dma 3
        io 0x0378-0x037f
        io 0x0778-0x077a

02 PNP0501 16550A-compatible COM port
        io 0x03f8-0x03ff
        irq 4

03 PNP0511 Generic IRDA-compatible device
        io 0x03e8-0x03ef
        irq 10

04 PNP0700 PC standard floppy disk controller
        irq 6
        dma 2
        io 0x03f0-0x03f5

05 ESS0006 multimedia controller: audio
        io 0x0250-0x0257

06 CPQb0ac multimedia controller: audio
        io 0x0220-0x022f
        io 0x0388-0x038b
        io 0x0330-0x0331
        irq 5
        dma 1
        dma 5

07 PNP0c01 System board
        mem 0x00000000-0x0009ffff
        mem 0x000f0000-0x000fffff
        mem 0x00100000-0x09ffffff

08 PNP0c04 Math coprocessor
        io 0x00f0-0x00ff
        irq 13

09 PNP0000 AT programmable interrupt controller
        io 0x0020-0x0021
        io 0x00a0-0x00a1
        irq 2

0a PNP0100 AT system timer
        io 0x0040-0x0043
        irq 0

0b PNP0200 AT DMA controller
        io 0x0000-0x000f
        io 0x0080-0x008f
        io 0x00c0-0x00df
        dma 4

0c PNP0800 AT-style speaker sound
        io 0x0061-0x0061

0d PNP0b00 AT real-time clock
        io 0x0070-0x0071
        io 0x0072-0x0073
        irq 8

0e PNP0303 IBM enhanced keyboard (101/102-key, PS/2 mouse support)
        io 0x0060-0x0060
        io 0x0064-0x0064
        irq 1

0f PNP0f13 PS/2 port for PS/2-style mice
        irq 12

10 PNP0a03 PCI bus
        io 0x0cf8-0x0cff

12 PNP0c02 Motherboard resources
        mem 0xfffc0000-0xffffffff
        mem 0x000cb000-0x000cbfff
        io 0x0022-0x003f
        io 0x0044-0x005f
        io 0x0062-0x0063
        io 0x0065-0x006f
        io 0x0074-0x0074
        io 0x0075-0x0075
        io 0x0076-0x0076
        io 0x0077-0x0077
        io 0x0090-0x0091
        io 0x0092-0x0092
        io 0x0093-0x009f
        io 0x00a2-0x00bf
        io 0x00e0-0x00e1
        io 0x00e2-0x00e3
        io 0x04d0-0x04d1
        io 0x0f00-0x0f3f
        io 0x0d00-0x0d0f

13 PNP0e03 Intel 82365-compatible CardBus controller
        io 0x03e0-0x03e1

-> If I interpreted this right my module-options are like in this example and not like yours (?)

-> Setup did not work and sound test did not funktion

**Aadebug**

Did not understand the instructions for the installation, as I am a **Linux beginner**
-> save it as aadebug, **w[COLOR="Red"]here? file? folder?[/COLOR]** then execute chmod +x aadebug. **[COLOR="Red"]execute??? what??? +x[/COLOR]**  Run the script by typing ./aadebug in a shell and send the result to the person who is going to help you. 
For a beginner a clearer description, with an example would be nice... 

**Reporting Sound Bugs**

1.) [COLOR="Red"]~$ tail -2 /proc/asound/oss/sndstat[/COLOR]

Mixers: NOT ENABLED IN CONFIG

2.) [COLOR="Red"]amixer[/COLOR] 
does not work; where is my amixer? 

[COLOR="Red"]~$  sudo apt-get install alsamixer[/COLOR]
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
juhapetersen@juhapetersen:~$ sudo apt-get install alsamixer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package alsamixer

[COLOR="Red"]~$ whereis alsamixer[/COLOR]
alsamixer: /usr/bin/alsamixer /usr/X11R6/bin/alsamixer /usr/bin/X11/alsamixer /usr/share/man/man1/alsamixer.1.gz

[COLOR="Red"]~$ apt-get install alsa-base alsa-oss alsa-utils [/COLOR]
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

[COLOR="Red"]~$ alsaconf [/COLOR]
bash: alsaconf: command not found

[COLOR="Red"]~$ alsamixer[/COLOR]
alsamixer: function snd_ctl_open failed for default: No such device

[COLOR="Red"]
~$ sudo apt-get install alsa-base alsa-oss alsa-utils[/COLOR]
Reading package lists... Done
Building dependency tree       
Reading state information... Done
alsa-base is already the newest version.
alsa-utils is already the newest version.
The following NEW packages will be installed:
  alsa-oss
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 49.0kB of archives.
After unpacking 221kB of additional disk space will be used.
Get:1 [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) edgy/universe alsa-oss 1.0.11-1 [49.0kB]
Fetched 49.0kB in 0s (88.6kB/s)
Selecting previously deselected package alsa-oss.
(Reading database ... 110274 files and directories currently installed.)
Unpacking alsa-oss (from .../alsa-oss_1.0.11-1_i386.deb) ...
Setting up alsa-oss (1.0.11-1) ...

[COLOR="Red"]~$ asoundconf [/COLOR]
Usage:
asoundconf is-active
asoundconf get|delete PARAMETER
asoundconf set PARAMETER VALUE
asoundconf list

Convenience macro functions:
asoundconf set-default-card CARD
asoundconf reset-default-card

3.) [COLOR="Red"]~$ lspci -nv
[/COLOR]
same as lspci -v

4.) [COLOR="Red"]~$ asoundconf list
Names of available sound cards:[/COLOR]
non...

5.) [COLOR="Red"]~$ cat /etc/asound.conf ~/.asoundrc*[/COLOR]
cat: /etc/asound.conf: No such file or directory
# ALSA library configuration file

# Include settings that are under the control of asoundconf(1).
# (To disable these settings, comment out this line.)
</home/:) /.asoundrc.asoundconf>

# ALSA library configuration file managed by asoundconf(1).
#
# MANUAL CHANGES TO THIS FILE WILL BE OVERWRITTEN!
#
# Manual changes to the ALSA library configuration should be implemented
# by editing the ~/.asoundrc file, not by editing this file.
PARAMETER VALUE
:confused: 

6.) dmesg
a lot of stuff reading (will put it to the next post)

7.)  [COLOR="Red"]cat /proc/interrupts[/COLOR]
           CPU0       
  0:    9140178          XT-PIC  timer
  1:       9045          XT-PIC  i8042
  2:          0          XT-PIC  cascade
  3:      94442          XT-PIC  pcnet_cs
  7:          1          XT-PIC  parport0
  8:          7          XT-PIC  rtc
 11:     130561          XT-PIC  uhci_hcd:usb1, yenta, yenta
 12:     232475          XT-PIC  i8042
 14:     446925          XT-PIC  ide0
NMI:          0 
LOC:          0 
ERR:          0
MIS:          0
[B]
Automatic Sound Information Collection[/B]

Unofficial Alsa support: How to download and run the scripts?? I am a Linux beginner...:confused: 

A lot of stuff here I know...

Anyway if somebody likes to help me I would be very happy...

Otherwise I will put Ubuntu to the unsolved files until I will buy a new computer (which will be in 4 to 6 years)...

Hope to hear from anyone...

Toni:KS

---

### Post by toniju on 2007-05-16
Hi,

Here is the **[COLOR="Red"]dmesg[/COLOR]**
[17179569.184000] Linux version 2.6.17-11-generic (root@terranova) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Tue Mar 13 23:32:38 UTC 2007 (Ubuntu 2.6.17-11.37-generic)
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[17179569.184000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000000a000000 (usable)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 160MB LOWMEM available.
[17179569.184000] On node 0 totalpages: 40960
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   Normal zone: 36864 pages, LIFO batch:7
[17179569.184000] DMI not present or invalid.
[17179569.184000] ACPI: Unable to locate RSDP
[17179569.184000] Allocating PCI resources starting at 10000000 (gap: 0a000000:f6000000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hda1 ro quiet splash
[17179569.184000] Local APIC disabled by BIOS (or by default) -- you can enable it with "lapic"
[17179569.184000] mapped APIC to ffffd000 (01149000)
[17179569.184000] Enabling fast FPU save and restore... done.
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 1024 (order: 10, 4096 bytes)
[    0.000000] Detected 300.073 MHz processor.
[  330.266046] Using tsc for high-res timesource
[  330.268821] Console: colour VGA+ 80x25
[  330.270012] Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
[  330.270933] Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
[  330.301763] Memory: 152700k/163840k available (1911k kernel code, 10596k reserved, 1073k data, 308k init, 0k highmem)
[  330.301789] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[  330.381839] Calibrating delay using timer specific routine.. 601.30 BogoMIPS (lpj=1202616)
[  330.382087] Security Framework v1.0.0 initialized
[  330.382130] SELinux:  Disabled at boot.
[  330.382230] Mount-cache hash table entries: 512
[  330.383008] CPU: After generic identify, caps: 0183f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[  330.383056] CPU: After vendor identify, caps: 0183f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[  330.383114] CPU: L1 I cache: 16K, L1 D cache: 16K
[  330.383132] CPU: L2 cache: 512K
[  330.383149] CPU: After all inits, caps: 0183f9ff 00000000 00000000 00000040 00000000 00000000 00000000
[  330.383264] Checking 'hlt' instruction... OK.
[  330.397978] SMP alternatives: switching to UP code
[  330.398582] Freeing SMP alternatives: 16k freed
[  330.399277] checking if image is initramfs... it is
[  333.545079] Freeing initrd memory: 5327k freed
[  333.545116] CPU0: Intel Pentium II (Deschutes) stepping 02
[  333.545149] SMP motherboard not detected.
[  333.545166] Local APIC not detected. Using dummy APIC emulation.
[  333.545538] Brought up 1 CPUs
[  333.545650] migration_cost=0
[  333.547412] NET: Registered protocol family 16
[  333.547598] EISA bus registered
[  333.563658] PCI: PCI BIOS revision 2.10 entry at 0xf046a, last bus=0
[  333.563691] PCI: Using configuration type 1
[  333.563705] Setting up standard PCI resources
[  333.565639] ACPI: Interpreter disabled.
[  333.565665] Linux Plug and Play Support v0.97 (c) Adam Belay
[  333.565746] pnp: PnP ACPI: disabled
[  333.565763] PnPBIOS: Scanning system for PnP BIOS support...
[  333.565890] PnPBIOS: Found PnP BIOS installation structure at 0xc00fb2a0
[  333.565914] PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0x4a38, dseg 0xf0000
[  333.571903] PnPBIOS: 18 nodes reported by PnP BIOS; 18 recorded by driver
[  333.572226] PCI: Probing PCI hardware
[  333.572247] PCI: Probing PCI hardware (bus 00)
[  333.572861] PCI: Ignoring BAR0-3 of IDE controller 0000:00:07.1
[  333.573193] PCI quirk: region 0f00-0f3f claimed by PIIX4 ACPI
[  333.573214] PCI quirk: region 0d00-0d0f claimed by PIIX4 SMB
[  333.573344] Boot video device is 0000:00:08.0
[  333.576580] PCI: Using IRQ router PIIX/ICH [8086/7110] at 0000:00:07.0
[  333.602026] PCI: Bus 1, cardbus bridge: 0000:00:11.0
[  333.602046]   IO window: 00001400-000014ff
[  333.602066]   IO window: 00001800-000018ff
[  333.602086]   PREFETCH window: 10000000-11ffffff
[  333.602105]   MEM window: 12000000-13ffffff
[  333.602123] PCI: Bus 5, cardbus bridge: 0000:00:11.1
[  333.602138]   IO window: 00001c00-00001cff
[  333.602155]   IO window: 00002000-000020ff
[  333.602174]   PREFETCH window: 14000000-15ffffff
[  333.602193]   MEM window: 16000000-17ffffff
[  333.602246] PCI: Found IRQ 11 for device 0000:00:11.0
[  333.602282] PCI: Sharing IRQ 11 with 0000:00:11.1
[  333.602327] PCI: Found IRQ 11 for device 0000:00:11.1
[  333.602361] PCI: Sharing IRQ 11 with 0000:00:11.0
[  333.602487] NET: Registered protocol family 2
[  333.637340] IP route cache hash table entries: 2048 (order: 1, 8192 bytes)
[  333.637934] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
[  333.638386] TCP bind hash table entries: 4096 (order: 3, 32768 bytes)
[  333.638624] TCP: Hash tables configured (established 8192 bind 4096)
[  333.638643] TCP reno registered
[  333.643238] audit: initializing netlink socket (disabled)
[  333.643294] audit(1179302187.564:1): initialized
[  333.644142] VFS: Disk quotas dquot_6.5.1
[  333.644278] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[  333.644601] Initializing Cryptographic API
[  333.644630] io scheduler noop registered
[  333.644674] io scheduler anticipatory registered
[  333.644721] io scheduler deadline registered
[  333.644802] io scheduler cfq registered (default)
[  333.644831] Limiting direct PCI/PCI transfers.
[  333.646050] isapnp: Scanning for PnP cards...
[  334.001373] isapnp: No Plug & Play device found
[  334.208500] Real Time Clock Driver v1.12ac
[  334.209070] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[  334.209513] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[  334.210787] serial8250: ttyS2 at I/O 0x3e8 (irq = 4) is a 16550A
[  334.213029] 00:02: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[  334.215550] mice: PS/2 mouse device common for all mice
[  334.220109] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[  334.220956] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[  334.220984] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[  334.222011] PNP: PS/2 Controller [PNP0303,PNP0f0e] at 0x60,0x64 irq 1,12
[  334.227676] serio: i8042 AUX port at 0x60,0x64 irq 12
[  334.227923] serio: i8042 KBD port at 0x60,0x64 irq 1
[  334.229358] EISA: Probing bus 0 at eisa.0
[  334.229394] Cannot allocate resource for EISA slot 1
[  334.229413] Cannot allocate resource for EISA slot 2
[  334.229484] EISA: Detected 0 cards.
[  334.230011] TCP bic registered
[  334.230063] NET: Registered protocol family 1
[  334.230098] NET: Registered protocol family 8
[  334.230113] NET: Registered protocol family 20
[  334.230236] Using IPI No-Shortcut mode
[  334.232389] Freeing unused kernel memory: 308k freed
[  334.276006] input: AT Translated Set 2 keyboard as /class/input/input0
[  335.850174] Capability LSM initialized
[  338.388142] PIIX4: IDE controller at PCI slot 0000:00:07.1
[  338.388205] PIIX4: chipset revision 1
[  338.388220] PIIX4: not 100% native mode: will probe irqs later
[  338.388254]     ide0: BM-DMA at 0x1020-0x1027, BIOS settings: hda:DMA, hdb:DMA
[  338.388310] Probing IDE interface ide0...
[  338.675606] hda: IBM-DADA-25400, ATA DISK drive
[  339.123405] hdb: UJDA150, ATAPI CD/DVD-ROM drive
[  339.184057] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[  339.228131] hda: max request size: 128KiB
[  339.565268] hda: 10553760 sectors (5403 MB) w/460KiB Cache, CHS=11168/15/63, UDMA(33)
[  339.565312] hda: cache flushes not supported
[  339.565487]  hda: hda1 hda2 < hda5 >
[  339.687672] hdb: ATAPI 24X CD-ROM drive, 128kB Cache, DMA
[  339.687718] Uniform CD-ROM driver Revision: 3.20
[  340.603907] usbcore: registered new driver usbfs
[  340.605680] usbcore: registered new driver hub
[  340.619532] USB Universal Host Controller Interface driver v3.0
[  340.621379] PCI: Found IRQ 11 for device 0000:00:07.2
[  340.621457] uhci_hcd 0000:00:07.2: UHCI Host Controller
[  340.622962] uhci_hcd 0000:00:07.2: new USB bus registered, assigned bus number 1
[  340.623049] uhci_hcd 0000:00:07.2: irq 11, io base 0x00001000
[  340.624312] usb usb1: configuration #1 chosen from 1 choice
[  340.625132] hub 1-0:1.0: USB hub found
[  340.625210] hub 1-0:1.0: 2 ports detected
[  340.826867] Probing IDE interface ide1...
[  341.473525] Attempting manual resume
[  341.584718] kjournald starting.  Commit interval 5 seconds
[  341.584786] EXT3-fs: mounted filesystem with ordered data mode.
[  378.649897] piix4_smbus 0000:00:07.3: Found 0000:00:07.3 device
[  378.649941] piix4_smbus 0000:00:07.3: Host SMBus controller not enabled!
[  379.586804] irda_init()
[  379.586872] NET: Registered protocol family 23
[  382.526875] parport: PnPBIOS parport detected.
[  382.526936] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
[  382.830744] logips2pp: Detected unknown logitech mouse model 1
[  383.526881] PCI: Found IRQ 11 for device 0000:00:11.0
[  383.526931] PCI: Sharing IRQ 11 with 0000:00:11.1
[  383.526972] Yenta: CardBus bridge found at 0000:00:11.0 [0e11:b047]
[  383.527013] Yenta: Using CSCINT to route CSC interrupts to PCI
[  383.527028] Yenta: Routing CardBus interrupts to PCI
[  383.527049] Yenta TI: socket 0000:00:11.0, mfunc 0x01001c72, devctl 0x64
[  383.564599] Floppy drive(s): fd0 is 1.44M
[  383.580234] FDC 0 is a post-1991 82077
[  383.581383] input: PS/2 Logitech Mouse as /class/input/input1
[  383.758784] Yenta: ISA IRQ mask 0x0618, PCI irq 11
[  383.758805] Socket status: 30000010
[  383.759459] PCI: Found IRQ 11 for device 0000:00:11.1
[  383.759501] PCI: Sharing IRQ 11 with 0000:00:11.0
[  383.759555] Yenta: CardBus bridge found at 0000:00:11.1 [0e11:b047]
[  383.759598] Yenta: Using CSCINT to route CSC interrupts to PCI
[  383.759613] Yenta: Routing CardBus interrupts to PCI
[  383.759635] Yenta TI: socket 0000:00:11.1, mfunc 0x01001c72, devctl 0x64
[  384.102780] Yenta: ISA IRQ mask 0x0618, PCI irq 11
[  384.102802] Socket status: 30000006
[  384.243081] input: PC Speaker as /class/input/input2
[  384.449874] pccard: PCMCIA card inserted into slot 0
[  386.091650] cs: IO port probe 0x100-0x3af: excluding 0x220-0x22f 0x250-0x257 0x330-0x337 0x388-0x38f
[  386.094297] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[  386.095483] cs: IO port probe 0x820-0x8ff: clean.
[  386.096550] cs: IO port probe 0xc00-0xcf7: clean.
[  386.098466] cs: IO port probe 0xa00-0xaff: clean.
[  386.099625] cs: memory probe 0xa0000000-0xa0ffffff: clean.
[  386.107564] pcmcia: registering new device pcmcia0.0
[  386.195532] cs: IO port probe 0x100-0x3af: excluding 0x220-0x22f 0x250-0x257 0x330-0x337 0x388-0x38f
[  386.198214] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[  386.199401] cs: IO port probe 0x820-0x8ff: clean.
[  386.200466] cs: IO port probe 0xc00-0xcf7: clean.
[  386.202226] cs: IO port probe 0xa00-0xaff: clean.
[  386.285048] ts: Compaq touchscreen protocol output
[  387.770923] eth0: NE2000 Compatible: io 0x300, irq 3, hw_addr 00:13:F7:0E:BC:C7
[  388.337056] lp0: using parport0 (interrupt-driven).
[  388.955324] BUG: unable to handle kernel paging request at virtual address 07400041
[  388.955359]  printing eip:
[  388.955371] c01e1da6
[  388.955381] *pde = 00000000
[  388.955398] Oops: 0000 [#1]
[  388.955408] SMP 
[  388.955423] Modules linked in: snd_timer snd_hwdep snd_mpu401_uart snd_rawmidi snd_seq_device snd soundcore lp pcnet_cs 8390 tsdev serio_raw pcmcia pcspkr evdev floppy yenta_socket rsrc_nonstatic pcmcia_core parport_pc parport psmouse irtty_sir sir_dev irda crc_ccitt i2c_piix4 i2c_core ext3 jbd ide_generic uhci_hcd usbcore ide_cd cdrom ide_disk piix generic processor fbcon tileblit font bitblit softcursor vesafb capability commoncap
[  388.955596] CPU:    0
[  388.955602] EIP:    0060:[<c01e1da6>]    Not tainted VLI
[  388.955612] EFLAGS: 00010286   (2.6.17-11-generic #2) 
[  388.955657] EIP is at kref_get+0x6/0x40
[  388.955675] eax: 07400041   ebx: 07400041   ecx: 00000005   edx: 00000000
[  388.955698] esi: c31d7b60   edi: 00000000   ebp: ca9d0288   esp: c442fe14
[  388.955716] ds: 007b   es: 007b   ss: 0068
[  388.955735] Process modprobe (pid: 2852, threadinfo=c442e000 task=c4429ab0)
[  388.955750] Stack: 00000003 c4429bbc c9f2e580 c9f2e580 07400029 c01e118f c31d7be0 c0246ace 
[  388.955796]        c0246f5c 00000014 c31d7be0 c0380694 c31dc3e0 c31d7b68 ffffffea 00000001 
[  388.955841]        c31d7b60 c31d7b60 fffffff4 c31dc3e0 ca9d0288 c02472cd c442fe98 c442fe98 
[  388.955888] Call Trace:
[  388.955916]  <c01e118f> kobject_get+0xf/0x20  <c0246ace> class_device_get+0xe/0x20
[  388.955988]  <c0246f5c> class_device_add+0x5c/0x330  <c02472cd> class_device_create+0x8d/0xc0
[  388.956074]  <ca9b142f> snd_register_device+0x24f/0x260 [snd]  <ca8c816b> alsa_timer_init+0x16b/0x205 [snd_timer]
[  388.956287]  <c012f880> blocking_notifier_call_chain+0x30/0x60  <c013cda8> sys_init_module+0x148/0x19c0
[  388.956428]  <c012bc00> __mod_timer+0x0/0xd0  <c0102fbb> sysenter_past_esp+0x54/0x79
[  388.956565] Code: 08 35 00 00 00 c7 44 24 04 77 ce 2f c0 c7 04 24 b3 14 2f c0 e8 ec 10 f4 ff e8 97 30 f2 ff eb 80 90 8d 74 26 00 53 89 c3 83 ec 10 <8b> 00 85 c0 74 08 90 ff 03 83 c4 10 5b c3 c7 44 24 0c f9 38 2e 
[  388.956755] EIP: [<c01e1da6>] kref_get+0x6/0x40 SS:ESP 0068:c442fe14
[  388.956788]  <6>Adding 248968k swap on /dev/disk/by-uuid/adf2931d-5487-43ed-8a14-c9eecc210483.  Priority:-1 extents:1 across:248968k
[  389.219073] NET: Registered protocol family 17
[  389.350356] EXT3 FS on hda1, internal journal
[  391.362841] NET: Registered protocol family 10
[  391.363359] lo: Disabled Privacy Extensions
[  391.364357] IPv6 over IPv4 tunneling driver
[  418.451147] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[  433.173408] Bluetooth: Core ver 2.8
[  433.173439] NET: Registered protocol family 31
[  433.173452] Bluetooth: HCI device and connection manager initialized
[  433.173520] Bluetooth: HCI socket layer initialized
[  433.317730] Bluetooth: L2CAP ver 2.8
[  433.317755] Bluetooth: L2CAP socket layer initialized
[  433.345101] Bluetooth: RFCOMM socket layer initialized
[  433.345179] Bluetooth: RFCOMM TTY layer initialized
[  433.345194] Bluetooth: RFCOMM ver 1.7
[ 1204.601298] usb 1-1: new full speed USB device using uhci_hcd and address 2
[ 1204.768710] usb 1-1: configuration #1 chosen from 1 choice
[ 1207.765324] usbcore: registered new driver libusual
[ 1208.009975] SCSI subsystem initialized
[ 1208.215185] Initializing USB Mass Storage driver...
[ 1208.217463] scsi0 : SCSI emulation for USB Mass Storage devices
[ 1208.219654] usb-storage: device found at 2
[ 1208.219672] usb-storage: waiting for device to settle before scanning
[ 1208.219729] usbcore: registered new driver usb-storage
[ 1208.219749] USB Mass Storage support registered.
[ 1213.216204] usb-storage: device scan complete
[ 1213.221171]   Vendor: WDC WD80  Model: 0BB-00JHC0        Rev: 0000
[ 1213.221253]   Type:   Direct-Access                      ANSI SCSI revision: 00
[ 1213.674626] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[ 1213.690891] sda: Write Protect is off
[ 1213.690929] sda: Mode Sense: 27 00 00 00
[ 1213.690945] sda: assuming drive cache: write through
[ 1213.726625] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[ 1213.746856] sda: Write Protect is off
[ 1213.746897] sda: Mode Sense: 27 00 00 00
[ 1213.746912] sda: assuming drive cache: write through
[ 1213.747982]  sda: sda1
[ 1213.766689] sd 0:0:0:0: Attached scsi disk sda
[ 1213.842961] sd 0:0:0:0: Attached scsi generic sg0 type 0
[ 1219.070016] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[ 1753.117852] usb 1-1: USB disconnect, address 2
[13510.199109] pnp: Device 00:02 disabled.
[13510.199776] pnp: Device 00:01 disabled.
[    6.326238] pnp: Device 00:01 activated.
[    6.326739] pnp: Device 00:02 activated.
[    6.327102] pnp: Device 00:0e does not support activation.
[    6.327569] pnp: Device 00:0f does not support activation.
[    6.328069] PM: Writing back config space on device 0000:00:00.0 at offset 4 (was 8, writing 50000008)
[    6.328954] PCI: Found IRQ 11 for device 0000:00:07.2
[    6.329586] PM: Writing back config space on device 0000:00:11.0 at offset 1 (was 2100003, writing 2100007)
[    6.329643] PCI: Found IRQ 11 for device 0000:00:11.0
[    6.405584] PCI: Sharing IRQ 11 with 0000:00:11.1
[    6.409884] eth0: trigger_send() called with the transmitter busy.
[    7.829913] PM: Writing back config space on device 0000:00:11.1 at offset 1 (was 2100003, writing 2100007)
[    7.829989] PCI: Found IRQ 11 for device 0000:00:11.1
[    7.830029] PCI: Sharing IRQ 11 with 0000:00:11.0
[    8.952883] logips2pp: Detected unknown logitech mouse model 1
[18588.798467] usb 1-1: new low speed USB device using uhci_hcd and address 3
[18588.967139] usb 1-1: configuration #1 chosen from 1 choice
[18593.042180] usbcore: registered new driver hiddev
[18593.064007] input: USB Optical Mouse as /class/input/input3
[18593.067853] input: USB HID v1.10 Mouse [USB Optical Mouse] on usb-0000:00:07.2-1
[18593.068682] usbcore: registered new driver usbhid
[18593.069257] drivers/usb/input/hid-core.c: v2.6:USB HID core driver

---

### Post by toniju on 2007-05-17
Hi again,

I updated my 6.10 to Ubuntu 7.04 and many things became better and I could finally find the Alsa mixer. In addition the sound card and even the UBS sound card was found. But now the computer slowed down and I decided to upload Xubuntu. So thanks for your help... Maybe I try Ubuntu when I have a newer computer (in some years I hope...)

Best to you all.

Toni:KS

---

### Post by toniju on 2007-05-22
Hello again,

I have been active again...
I tried several other distributions (Opensuse, Debian, Xubuntu...) but the problem stayed. Opensuse detected the sound card but could not install es1869 for some reason... The rest did not recognize the sound card at all. All distributions could detect my cheap usb sound card though... Now I am back to use Ubuntu and managed to hear some internet radio with my usb sound card. Yes... :p
Nevertheless it would be nice to have the original sound card working as the usb can cause some  speed problems (?) At least I can not listen to CD's as it breaks stream every two seconds...
Now I am trying to install some program, which could play mp3... Will look in the forum for some comments about this subject to get a good and simple player...

If someone finds some solution for the es1869 sound card, let me know ;)

All the best,

Toni :KS

---

### Post by toniju on 2007-05-22
Moi,

Now I have the xmms installed and after I changed the plugins to the usb sound card I CAN HEAR MUSIC :p:p:p

YES :p

Maybe I will solve the es1869 problem some other day... I can recommend to buy a cheap usb sound card. My usb card costs only 15€ and is working now quite fine ...

Toni :KS

---

