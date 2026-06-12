---
title: "No Sound - hda-intel nVidia MCP51 rev a2"
date: 2006-08-20
forum: Multimedia &amp; Video
---

### Post by Gnuklear on 2006-08-20
Hey guys, I've been messing with the sound system on my AMD64 install of Dapper on my Gateway MX3414 laptop for the past 2 days or so with no luck, so I figured it was time to call in the experts. First, getting straight to the point, some system info:

```
$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```
```
$ lsmod
Module                  Size  Used by
nls_utf8                3584  0
nls_cp437               8320  0
vfat                   16768  0
fat                    57136  1 vfat
rfcomm                 45600  0
l2cap                  30464  5 rfcomm
bluetooth              59268  4 rfcomm,l2cap
ppdev                  11400  0
powernow_k8            12992  1
cpufreq_userspace       9184  1
cpufreq_stats           8264  0
freq_table              6464  2 powernow_k8,cpufreq_stats
cpufreq_powersave       3328  0
cpufreq_ondemand        9768  0
cpufreq_conservative    10984  0
video                  18824  0
tc1100_wmi              9096  0
sony_acpi               7188  0
pcc_acpi               16128  0
hotkey                 13768  0
dev_acpi               15364  0
container               6272  0
button                  8864  0
acpi_sbs               24600  0
battery                12296  1 acpi_sbs
i2c_acpi_ec             7040  1 acpi_sbs
ac                      7176  1 acpi_sbs
sg                     43696  0
sd_mod                 21504  0
dm_mod                 63176  1
md_mod                 76792  0
parport_pc             40816  0
lp                     15040  0
parport                44172  3 ppdev,parport_pc,lp
ipv6                  300416  10
joydev                 13184  0
tsdev                  10240  0
snd_hda_intel          22176  1
snd_hda_codec         175560  1 snd_hda_intel
r818x                  97808  0
ieee80211_rtl          90384  1 r818x
snd_pcm_oss            48416  0
snd_mixer_oss          20480  1 snd_pcm_oss
snd_pcm               103560  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
psmouse                40324  0
pcspkr                  3592  0
snd_timer              29064  1 snd_pcm
serio_raw               9732  0
usb_storage            82112  0
nvidia               5433176  0
i2c_core               26624  2 i2c_acpi_ec,nvidia
snd                    70880  8 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              13216  1 snd
snd_page_alloc         13968  2 snd_hda_intel,snd_pcm
shpchp                 51360  0
pci_hotplug            33168  1 shpchp
af_packet              28172  4
evdev                  14464  1
ext3                  145936  1
jbd                    70952  1 ext3
ide_generic             2816  0
ehci_hcd               36232  0
ohci_hcd               23684  0
usbcore               147004  4 usb_storage,ehci_hcd,ohci_hcd
forcedeth              34444  0
ide_cd                 35744  0
cdrom                  41144  1 ide_cd
ide_disk               19456  3
generic                 7300  0
amd74xx                17072  0 [permanent]
sata_nv                12548  0
libata                 85536  1 sata_nv
scsi_mod              160504  4 sg,sd_mod,usb_storage,libata
thermal                16524  0
processor              29736  2 powernow_k8,thermal
fan                     6408  0
capability              7176  0
commoncap               9728  1 capability
vga16fb                15120  1
cfbcopyarea             5120  1 vga16fb
vgastate               10368  1 vga16fb
cfbimgblt               4224  1 vga16fb
cfbfillrect             5760  1 vga16fb
fbcon                  43136  72
tileblit                4096  1 fbcon
font                    9984  1 fbcon
bitblit                 7424  1 fbcon
softcursor              3712  1 bitblit

```
```
$ sudo lspci -v
0000:00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
        Subsystem: Gateway 2000: Unknown device 0317
        Flags: bus master, 66MHz, fast devsel, latency 0
        Capabilities: [44] #08 [01e0]
        Capabilities: [e0] #08 [a800]

0000:00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
        Subsystem: Gateway 2000: Unknown device 0317
        Flags: 66MHz, fast devsel

0000:00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
        Subsystem: Gateway 2000: Unknown device 0317
        Flags: 66MHz, fast devsel

0000:00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
        Subsystem: Gateway 2000: Unknown device 0317
        Flags: 66MHz, fast devsel

0000:00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
        Subsystem: Gateway 2000: Unknown device 0317
        Flags: bus master, 66MHz, fast devsel, latency 0

0000:00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
        Subsystem: Gateway 2000: Unknown device 0317
        Flags: bus master, 66MHz, fast devsel, latency 0
        Capabilities: [44] #00 [00fe]
        Capabilities: [fc] #00 [0000]

0000:00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
        Subsystem: Gateway 2000: Unknown device 0317
        Flags: 66MHz, fast devsel

0000:00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
        Subsystem: Gateway 2000: Unknown device 0317
        Flags: 66MHz, fast devsel

0000:00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=04, sec-latency=0
        I/O behind bridge: 00009000-00009fff
        Memory behind bridge: fa100000-fa8fffff
        Prefetchable memory behind bridge: 00000000bdf00000-00000000bfe00000
        Capabilities: [40] #0d [0000]
        Capabilities: [48] Power Management version 2
        Capabilities: [50] Message Signalled Interrupts: 64bit+ Queue=0/1 Enable+
        Capabilities: [60] #08 [a800]
        Capabilities: [80] #10 [0141]

0000:00:05.0 VGA compatible controller: nVidia Corporation C51 PCI Express Bridge (rev a2) (prog-if 00 [VGA])
        Subsystem: Gateway 2000: Unknown device 0317
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 217
        Memory at b2000000 (32-bit, non-prefetchable) [size=16M]
        Memory at c0000000 (64-bit, prefetchable) [size=256M]
        Memory at b1000000 (64-bit, non-prefetchable) [size=16M]
        Expansion ROM at 50000000 [disabled] [size=128K]
        Capabilities: [48] Power Management version 2
        Capabilities: [50] Message Signalled Interrupts: 64bit+ Queue=0/0 Enable-

0000:00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
        Subsystem: Gateway 2000: Unknown device 0317
        Flags: bus master, 66MHz, fast devsel, latency 0
        Capabilities: [44] #08 [01e9]
        Capabilities: [e0] #08 [a801]

0000:00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
        Subsystem: Gateway 2000: Unknown device 0317
        Flags: bus master, 66MHz, fast devsel, latency 0

0000:00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
        Subsystem: Gateway 2000: Unknown device 0317
        Flags: 66MHz, fast devsel, IRQ 10
        I/O ports at 3040 [size=64]
        I/O ports at 3000 [size=64]
        Capabilities: [44] Power Management version 2

0000:00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
        Subsystem: Gateway 2000: Unknown device 0317
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 10
        Memory at b0040000 (32-bit, non-prefetchable) [size=256K]

0000:00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3) (prog-if 10 [OHCI])
        Subsystem: Gateway 2000: Unknown device 0317
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 201
        Memory at b0004000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [44] Power Management version 2

0000:00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3) (prog-if 20 [EHCI])
        Subsystem: Gateway 2000: Unknown device 0317
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 209
        Memory at b0005000 (32-bit, non-prefetchable) [size=256]
        Capabilities: [44] #0a [2098]
        Capabilities: [80] Power Management version 2

0000:00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1) (prog-if 8a [Master SecP PriP])
        Subsystem: Gateway 2000: Unknown device 0317
        Flags: bus master, 66MHz, fast devsel, latency 0
        I/O ports at 3080 [size=16]
        Capabilities: [44] Power Management version 2

0000:00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2) (prog-if 01 [Subtractive decode])
        Flags: bus master, 66MHz, fast devsel, latency 0
        Bus: primary=00, secondary=06, subordinate=06, sec-latency=64
        I/O behind bridge: 00006000-00006fff
        Memory behind bridge: b3400000-b34fffff
        Capabilities: [b8] #0d [0000]
        Capabilities: [8c] #08 [a800]

0000:00:10.1 0403: nVidia Corporation MCP51 High Definition Audio (rev a2)
        Subsystem: Gateway 2000: Unknown device 0317
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 225
        Memory at b0000000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: [44] Power Management version 2
        Capabilities: [50] Message Signalled Interrupts: 64bit+ Queue=0/0 Enable-
        Capabilities: [6c] #08 [a802]

0000:00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
        Subsystem: Gateway 2000: Unknown device 0317
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 193
        Memory at b0006000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at 3090 [size=8]
        Capabilities: [44] #00 [0000]

0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
        Flags: fast devsel
        Capabilities: [80] #08 [2101]

0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
        Flags: fast devsel

0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
        Flags: fast devsel

0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
        Flags: fast devsel
        Capabilities: [f0] #0f [0010]

0000:06:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd.: Unknown device 8185 (rev 20)
        Subsystem: Realtek Semiconductor Co., Ltd.: Unknown device 8185
        Flags: bus master, medium devsel, latency 64, IRQ 11
        I/O ports at 6000 [size=256]
        Memory at b3400000 (32-bit, non-prefetchable) [size=512]
        Capabilities: [50] Power Management version 2

```
```
$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.11.
Compiled on Aug 19 2006 for kernel 2.6.15-26-amd64-generic (SMP).

```
Yes, that is a manually compiled version. Still no luck

All sound channels (that I can find anyway) are enabled and turned to full volume.

I've tried playing sound files with Totem (vorbis files, so I know they should play correctly on a default install) and the player seems to think everything is working. The ONLY visible sign that sound isn't working is that "vumeter" NEVER displays any change of volume - is always shows nothing playing.

I've tried compiling a newer version of ALSA (1.0.11 Final) with no improvement. Any help is appreciated. If at all possible, I'd like to avoid using nVidia's proprietary drivers.

---

### Post by alucinado on 2006-10-16
Hi Gnuklear,

I had a similar problem and it got resolved with the Alsa driver version 1.0.13.

You can see more information about here: [http://www.nvnews.net/vbulletin/showthread.php?p=979264](http://www.nvnews.net/vbulletin/showthread.php?p=979264) and here [https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2412](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2412) (login as Guest).

I have noticed something really strange. When I start with the Live CD, the audio is properly configured and everything works perfectly (different volume controls for the different outputs/inputs and even front headphones works). But the installation does not configure the front headphones properly and a single PCM volume control is shown :???: I compared the /etc/modprobe.d/alsa-base and they are the same! :-k

Good luck,
   Alucinado

---

### Post by svega85 on 2006-10-28
hi i'm new to ubuntu / linux and i have the exact same problem with the exact same laptop the gateway mx3414 but the only differance is that i have edgy eft and the sound card doesn't work at all i read the post above but i think edgy has the most current version of alsa so can anyone help please ](*,)

---

### Post by stryderjzw on 2006-10-29
edit

---

### Post by cisbrane on 2006-11-04
i have the same sound card, but i am on an hpdv2000z w/ a amd turion 64 x2.

I tried to install ALSA from source but now when i load ubuntu the little "drum beat" in edgy just keeps repeating, and i can't load my gnome session.

I had it fixed (some how) earlier, but then progarms like xmms could not access my sound card... so it was odd.

then i tried reinstalling and i guess i did the same thing again, and i don't know what i did to fix this even.

how did you go about installing it?

thanks

---

### Post by cheuschober on 2006-11-09
*throws another hat in the ring*

No sound here either. Clearly it's a growing problem. Anyone have any luck?

---

### Post by blk_jack on 2006-11-28
Same problem here with Edgy.  I've tried almost everything with alsa and figure at this point that it MUST be something with the alsa-drivers themselves.  Everything is detected fine, there are volume controls and nothing is muted.  I even get a little visual-sound thingy in totem... but no sound!

If anybody knows the solution to this problem please let us know, or at least point us in the right direction!

---

### Post by blk_jack on 2006-11-28
Also it should be noted that we have HDA NVidia cards, not the HDA Intel ones that you see solutions or semi-solutions to with google.  This is actually the first thread I've seen that specifically names the card I have and the problem I'm having, so hopefully we can narrow it down and fix it in this.

Also, in response to Gnuklear's comment, my "vumeter" shows "change" in volume even though I hear nothing.

---

### Post by yostral on 2006-12-04
Same problem here... sometimes.
Sometimes sound is working through the speakers, and sometimes through the headphone output !

And searching in google shows there are MANY people having these problem !
I hope it will be fix for feisty...

---

### Post by el_ave on 2006-12-31
I had exactly same problem with my HDA nVidia audio. I was able to fix it by running alsamixer  from console and by turning all volume settings to maximum and switching mute off (using "m" key).
Later I found out that "Surround" is what actually was responsible for my laptop speakers sound.

---

### Post by brandoncolorado on 2007-01-07
I am having the same problem, and I have not found an answer yet.  Is this something that I will have to wait until the next version for?  I would love to switch to Ubuntu and delete windows off my computer, but I need sound.  Any other help?

---

### Post by blk_jack on 2007-01-08
There is no solution for Gateway laptops with hda-intel nVidia nonsense.  Try on the nvidia forums, that's where another few threads are that have some good comments are.  It seems almost every hda-intel deal that's not a Gateway laptop has SOME kind of work-around or solution, but for myself (Gateway user), I'm SOL.

No sound since I bought the laptop in September, baby!  GO GO nVidia!!!!

---

### Post by brandoncolorado on 2007-01-13
> **blk_jack said:**
> There is no solution for Gateway laptops with hda-intel nVidia nonsense.  Try on the nvidia forums, that's where another few threads are that have some good comments are.  It seems almost every hda-intel deal that's not a Gateway laptop has SOME kind of work-around or solution, but for myself (Gateway user), I'm SOL.

No sound since I bought the laptop in September, baby!  GO GO nVidia!!!!

This is probably a stupid question, but could upgrading to the latest linux drivers from nvidia help?  I think now we are using 1.0-8xxx version drivers and the newest are 1.0-9xxx?  Would this help with our issue?

---

### Post by option94 on 2007-01-14
Bump....
Same card. No sound. It looks like the card is installed properly, just wont play any sound.

---

### Post by blk_jack on 2007-01-14
> **brandoncolorado said:**
> This is probably a stupid question, but could upgrading to the latest linux drivers from nvidia help?  I think now we are using 1.0-8xxx version drivers and the newest are 1.0-9xxx?  Would this help with our issue?

The nVidia video drivers have absolutely nothing to do with the intel hda [sound] drivers.

To my knowledge, nobody is really sure what's wrong.  Everything APPEARS to work perfectly.  I can play movies/mp3s/etc fine.  The visual audio effect shows the sound coming out, but my speakers get nothing and my headphones get nothing.  All volume levels are unmuted-turned up and still no dice.

---

### Post by brandoncolorado on 2007-01-14
Sorry, I was confused between different posts concerning the same laptop.  Same laptop also has problems with video and wireless.

---

### Post by pseudonym on 2007-01-14
My desktop has an nforce motherboard with an onboard HDA codec. The default ALSA config often won't detect the correct HD audio model, which is more than likely why you all don't have sound.

The solution, which btw is buried somewhere in the [Comprehensive Sound Guide]("http://www.ubuntuforums.org/showthread.php?t=205449"), is to do the following -

1. Extract /usr/share/doc/alsa-base/driver/ALSA-Configuration.txt.gz to your /home and open it up. This file contains extra config options for each ALSA module. Scroll down to ' Module snd-hda-intel' and read through this section. You may need to refer to your computer/motherboard's manual to find out which codec you have (ALC883, AD1988 etc). Then determine which of the model options applies to you - eg. you have an ASUS laptop, in which case you would choose the 'asus' option. Or you have a desktop with 5.1 or 7.1 onboard audio with digital out, in which case the right model is '6stack-digout'.

2. Once you have ascertained which HDA model applies to you, do this - ```
sudo gedit (or whichever editor you use) /etc/modprobe.d/snd-hda-intel.modprobe
add this line (it's a new file) -
options snd-hda-intel model=your-HDA-model
save and exit
```

3. Now do this - ```
sudo gedit /etc/modprobe.d/alsa-base
add this line at the end, with a two-line break from whatever is before -
options snd-hda-intel model=your-HDA-model
save and exit
```

4. Reboot, and you should now have sound :)

If this doesn't work you might also try using the OSS drivers from [Opensound]("http://www.opensound.com/"). I've since installed a dedicated sound card in my machine but I tested out Opensound's drivers first with the HD audio. This sound hardware seems to be better supported currently by Opensound and it is definitely worth considering installing their drivers.

---

### Post by brandoncolorado on 2007-01-14
> **pseudonym said:**
> My desktop has an nforce motherboard with an onboard HDA codec. The default ALSA config often won't detect the correct HD audio model, which is more than likely why you all don't have sound.

The solution, which btw is buried somewhere in the [Comprehensive Sound Guide]("http://www.ubuntuforums.org/showthread.php?t=205449"), is to do the following -

1. Extract /usr/share/doc/alsa-base/driver/ALSA-Configuration.txt.gz to your /home and open it up. This file contains extra config options for each ALSA module. Scroll down to ' Module snd-hda-intel' and read through this section.

2. Once you have ascertained which HDA model applies to you, do this - ```
sudo gedit (or whichever editor you use) /etc/modprobe.d/snd-hda-intel.modprobe
add this line (it's a new file) -
options snd-hda-intel model=your-HDA-model
save and exit
```

3. Now do this - ```
sudo gedit /etc/modprobe.d/alsa-base
add this line at the end, with a two-line break from whatever is before -
options snd-hda-intel model=your-HDA-model
save and exit
```

4. Reboot, and you should now have sound :)

If this doesn't work you might also try using the OSS drivers from [Opensound]("http://www.opensound.com/"). I've since installed a dedicated sound card in my machine but I tested out Opensound's drivers first with the HD audio. This sound hardware seems to be better supported currently by Opensound and it is definitely worth considering installing their drivers.

Now, can someone help me with my [xorg.conf]("http://www.ubuntuforums.org/showthread.php?t=338184") troubles? ;)

I can't find that MCP51 in the txt file that I extracted.  Am I missing something?

---

### Post by pseudonym on 2007-01-15
> **brandoncolorado said:**
> I can't find that MCP51 in the txt file that I extracted.  Am I missing something?
I don't think it will be listed as 'MCP51'. My mobo is MCP55, but the actual name of the sound chip is 'Realtek ALC883 HD Audio Codec'. I think yours will probably be similar ie. ALC882/3/5, but check your machine's documentation to be sure.

Once you know which codec it is, choose the model accordingly. Mine is a 7.1 setup with an optical S/PDIF out port, so I chose '6stack-dig'.

HTH

---

### Post by #Reistlehr- on 2007-02-06
i read somewhere else about compiling the new alsa drivers, and 90% success rate. 

but, so far, i have been unsuccessfull also.

---

### Post by brandoncolorado on 2007-02-12
I just read the 1.0.14rc2 change log at ALSA.  It looks like there is a partial fix already built in, and that they are working on this problem for 1.0.14 final release.  Hopefully my reading is right.

---

### Post by marcs on 2007-03-26
I'm using edgy latest kernel 2.6.17-11-generic on a core 2 duo (amd64 kernel)
but no sound at the first start.
then i've downloaded and compiled the stable alsa drivers, libs and utils (1.0.13) and do the things that this post is talking about (edit/modprobe.d/alsa-base etc... model=...)

I've got some type of sound now... 
i can hear some sound, but i hear also a lot of distortion rumor ( a lot of LOUD fzzzzzzzz shhhhh stuff) over the sound.

i got the nvidia MP51 high definition chip on a asus mainboard PNE-SLI (650i chipset).

Anyone with the same problem ?
Any solutions ?

---

### Post by Acglaphotis on 2007-04-02
I'll show ya how did i fixed my problem:

I had a problem with my HP Laptop (sound card MCP51 Nvidia HDA), the issue was that i wasn't able to hear music from the headphones, i could only hear the speaker.

I trie installing from source the latest version of ALSA (no 1.0.13), i tried the 1.0.14rc3 , and it worked (installed, rebooted), but then when i rebooted again (i needed to do something in windows) , the sound was gone AT ALL, so [i made a post about it ]("http://www.ubuntuforums.org/showthread.php?t=397999") and went to [this howto]("https://help.ubuntu.com/community/HdaIntelSoundHowto?highlight=%28hda%29") and as i said i installed the latest version of alsa, with no success :(  but then i got here and read a post in page 2 about models and stuff, i revisited the how-to, read it and did it, i tried about every model in the howto and 2 more from the alsa config.txt (i rebooted like 10 times  :evil: ) and then i re-read the post from page 2, i read something about OpenSoundSystem (an alternative for ALSA, dont you love free software and all its choices? :D) so i went searching for its [downloads site]("http://www.opensound.com/download.cgi") and installed it. Then i got an error telling me to erase a file from /usr/lib/oss/ (sorry i dont remember which file) and reboot and Voila! here am i (all of this was just 30 minutes ago :) .

Oh, and some other things:

The OSS mixer is ( on terminal ) 

```
ossmix
```

To change the volume (master) :

```
ossmix connector.speaker.function 51
```

where 51 is the wanted volume (1-100 only)

To change the volume (speaker):

```
ossmix connector.speaker 51
```

As of right now i haven't found a way to do this without the terminal, but i wanna write a small thing to do that. :) 


I also got beryl installed the day before yesterday (im getting less newbie :  D ).

I hope this was helpful ( i wonder if i should make a how-to).

-Acgla

-EDIT-

sound from youtube videos wont work. :x

--REDIT--

[This also works (better, as youtube works)]("http://www.ubuntuforums.org/showthread.php?t=322817")

---

### Post by farbird on 2007-04-16
very frustrating..
got myself a new hp laptop and it comes with the dreaded mcp51 nvidia hda soundcard...

have had already about 5 sleepless nites trying to configure this blardy card without sucess

patching 1.0.12, compiling 1.0.14rc3... tried with 1001 options and models in the modprobe snd-hda-intel commands..

Is there no solution?


I googled mcp51 nvidia hda alsa and tried all the guides provided here and everywhere else..

still no solution...

nvidia doesnt give nuts
frigging HP refuses to give support for linux drivers on their website..
Alsa doesnt care...
ubuntu repository&#347; alsa driver is of no use..

literally plucking out bunches of hair after about 200cups of coffee....
alsaconf
alsamixer
sudo modprobe etc etc etc

I´d been typing so many of these commands so tireless without solution...

really freaking giving up...

---

### Post by Acglaphotis on 2007-04-20
did you tried oss?

---

### Post by blk_jack on 2007-04-20
> **farbird said:**
> very frustrating..
got myself a new hp laptop and it comes with the dreaded mcp51 nvidia hda soundcard...

have had already about 5 sleepless nites trying to configure this blardy card without sucess

patching 1.0.12, compiling 1.0.14rc3... tried with 1001 options and models in the modprobe snd-hda-intel commands..

Is there no solution?


I googled mcp51 nvidia hda alsa and tried all the guides provided here and everywhere else..

still no solution...

nvidia doesnt give nuts
frigging HP refuses to give support for linux drivers on their website..
Alsa doesnt care...
ubuntu repository&#347; alsa driver is of no use..

literally plucking out bunches of hair after about 200cups of coffee....
alsaconf
alsamixer
sudo modprobe etc etc etc

I´d been typing so many of these commands so tireless without solution...

really freaking giving up...

It is frustrating and as of this version of alsa, there is *NO FIX* for our problem.  I am waiting too, following the bug on ALSA's bugzilla page..

No solution right now, so don't stress yourself out any more.

---

### Post by farbird on 2007-04-20
tried
oss...

works but doesnt allow me to run virtualbox coz of incompatibility.

---

### Post by svega85 on 2007-04-21
just installed feisty fawn 7.04 and sound still doesn't work :(

---

### Post by blk_jack on 2007-04-21
> **svega85 said:**
> just installed feisty fawn 7.04 and sound still doesn't work :(

It ain't up to feisty, it's up to ALSA.  Stay tuned, subscribe to the open bug, let the ALSA people know that there are quite a few of us with the problem.. that's all we can hope for. :(

---

### Post by svega85 on 2007-04-21
where is the open bug? and how do i contact the alsa ppl?

---

### Post by blk_jack on 2007-04-21
[https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2469](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2469)
[https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2948](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2948)

Two bugs open right now, but it's the same problem.

---

### Post by neocoretech on 2007-04-22
Hi there, i had the same problem's on an acer aspire with nvidia MCP51 sounddevice....

don't know if it helps someone here, but after playing around with alsa and the snd_hda_intel module with no luck if found out by chance that the master volume for the laptop speakers
are controled by the surround channel ???!!!
If I did note mute the other channels correctly i had these "crunchy" sounds....
I now changed my main channel in the gnome panel to sourround and can now "work"
as usually inclusive the key-shortcut's....

Didn't know I had a "surround-laptop" :D

hope this help's someone....

greetz

---

### Post by fairlie on 2007-04-23
I sure hope the guys at ALSA are working on this, it's the only thing stopping me use Linux properly now :(

---

### Post by swayze on 2007-04-24
hello to all. brand new around these parts.
has anyone ever figured out how to solve this nvidia mcp51 problem? 
when i was using opensuse, all i had to do was shut off the internal mic in alsamixer and my sound worked great. no such luck with alsa this time around.
 i just migrated to ubuntu feisty because suse is yucky, i may have to leave ubuntu out too though if i cant get this sound problem fixed.
 it would be a horrible shame though because i really like ubuntu now. can anyone help please?

Thanks.

using asus a8m notebook if its any help.

---

### Post by saurio33 on 2007-04-24
I have an Asus A7TC and now the sound work with ubuntu 7.04. The sound card is MCP51 High Definition Audio. The line is: 
options snd-hda-intel model=asus-dig

---

### Post by swayze on 2007-04-24
oh thanks for the reply.

solution that worked for me was adding

*options snd-hda-intel model=3stack*

to the end of my */etc/modprobe.d/alsa-base* file.

now a happy user.

curse of the dreaded nvidia mcp51 now over.

---

### Post by farbird on 2007-04-27
> **swayze said:**
> oh thanks for the reply.

solution that worked for me was adding

*options snd-hda-intel model=3stack*

to the end of my */etc/modprobe.d/alsa-base* file.

now a happy user.

curse of the dreaded nvidia mcp51 now over.

are your headphone jack/s working?

---

### Post by hardmax on 2007-04-29
I've a Laptop HP Pavilion tx1030la with Creative sound MCP51 and I've the same problem, but with 
*options snd-hda-intel model=3stack*
the sound works but no the headphone jacks but It's something. Can Anybody help Me?

---

### Post by farbird on 2007-04-29
> **hardmax said:**
> I've a Laptop HP Pavilion tx1030la with Creative sound MCP51 and I've the same problem, but with 
*options snd-hda-intel model=3stack*
the sound works but no the headphone jacks but It's something. Can Anybody help Me?

did u manage to get the touchscreen working with ubuntu?

---

### Post by Nicostarnux on 2007-05-06
> **saurio33 said:**
> I have an Asus A7TC and now the sound work with ubuntu 7.04. The sound card is MCP51 High Definition Audio. The line is: 
options snd-hda-intel model=asus-dig

Quite marvellous ... this is the line that got me out the silence ;) ;) ;)

BTW, I got an Asus A7T, Feisti brought me the air network with the Atheros chipset and I've almost all my hardware supported by now !!!!!

Thanks a lot

---

### Post by TecnoVM64 on 2007-05-06
I found the solution a few weeks ago, sorry for not helping here before.

So ok:
1. Get the latest alsa snapshot from here: 
[ftp://ftp.suse.com/pub/projects/alsa/snapshot/driver](ftp://ftp.suse.com/pub/projects/alsa/snapshot/driver)
2. Extract and go to the folder
3. do ./configure --with-oss=yes --with-sequencer=yes --with-cards=hda-intel ; make
4. sudo make install

Reboot and that's it you should have all your problems solved :) let me know if it works for you.

---

### Post by farbird on 2007-05-06
> **TecnoVM64 said:**
> I found the solution a few weeks ago, sorry for not helping here before.

So ok:
1. Get the latest alsa snapshot from here: 
[ftp://ftp.suse.com/pub/projects/alsa/snapshot/driver](ftp://ftp.suse.com/pub/projects/alsa/snapshot/driver)
2. Extract and go to the folder
3. do ./configure --with-oss=yes --with-sequencer=yes --with-cards=hda-intel ; make
4. sudo make install

Reboot and that's it you should have all your problems solved :) let me know if it works for you.

what is your laptop make/model?

---

### Post by TecnoVM64 on 2007-05-07
Compaq Presario V3000

---

### Post by farbird on 2007-05-07
> **TecnoVM64 said:**
> Compaq Presario V3000

no dice for me still

tried your method..


hp tablet tx1005au

---

### Post by Acglaphotis on 2007-05-09
Does this fix the headphone jack?

-Acgla

---

### Post by farbird on 2007-05-09
didnt work for me though

---

### Post by penvzila on 2007-05-09
Installing the latest alsa drivers via the wiki guide WORKED!!!  Between rc3 and rc4 they must have fixed my problem.

I have an hp dv2000t, btw.  Running 64bit edgy.

---

### Post by Acglaphotis on 2007-05-14
Via the wiki guide? what wiki guide? can you give us a link, please?

-acgla

---

### Post by fairlie on 2007-05-26
Yeah, where is this Wiki guide? :)

---

### Post by lexarrow on 2007-05-26
The wiki is [here]("https://wiki.ubuntu.com/UbuntuStudio/HowToInstallTheLastAlsaDriverForProSoundCard?highlight=%28alsa%29")
For a more detailed howto you can go [here]("http://ubuntuforums.org/showthread.php?t=455147")

---

### Post by rikardocarvajal on 2007-05-28
I have a problem with hda intel nVidia MCP51 rev a2 headphones jak, i installed the alsa 1.04-rc4 driver but mi headphone doesnt work,

I have a tx1000 pavilio hp laptop..


Thanks

---

### Post by hiazle on 2007-05-30
> **rikardocarvajal said:**
> I have a problem with hda intel nVidia MCP51 rev a2 headphones jak, i installed the alsa 1.04-rc4 driver but mi headphone doesnt work,

I have a tx1000 pavilio hp laptop..


Thanks

Try [this]("http://ubuntuforums.org/showthread.php?t=455147") thread.
Or [this]("http://ubuntuforums.org/showpost.php?p=2741606&postcount=30") post.

You may also want to add the following line to /etc/modprobe.d/alsa-base

```
 options snd-hda-intel index=0 model=3stack-dig
```

or

```
 options snd-hda-intel index=0 model=3stack
```

---

### Post by farbird on 2007-05-31
yea..
i tried and the headphones still doesnt work..
the laptop speakers work though... just that the headphone jack no audio..

already unmuted the alsamixer headphones switch

---

### Post by fairlie on 2007-06-03
People are reporting that it's working for some people now. Are any of the people who've got it working **Gateway** owners, we seem to be having the most problems with it.

---

### Post by svega85 on 2007-06-03
i'm a gateway owner (MX3414) and it doesn't work for me

---

### Post by farbird on 2007-06-03
theres a patch somewhere which patches for conexant chips...

but it doesnt work for mine is mine isnt the conexant variant..

---

### Post by exspiro on 2007-06-03
do you have this patch for conexant chips? i have one. and i get no sound.

thanks a lot

---

### Post by Sean K on 2007-06-03
I'm having a similar issue.. same sound card (integraded) and same driver (hda-intel), but I only get sound out of one speaker... would this problem be related in any way? I've tried the new alsa drivers and everything.. still no luck.

---

### Post by farbird on 2007-06-04
its in this thread

[http://ubuntuforums.org/showthread.php?t=455147](http://ubuntuforums.org/showthread.php?t=455147)

> **exspiro said:**
> do you have this patch for conexant chips? i have one. and i get no sound.

thanks a lot

---

### Post by CDNdevil on 2007-06-04
Alsa 1.0.14 stable released today (2007-06-04), just install it because the change log shows fixes to the hda_intel stac92XX, and some Ubuntu fixes, but I still don't have it working :(.
I'm going to keep playing around with it to see I can hopefully get it to work.

Edit: dmesg show this ([   24.912000] ALSA /home/chris/alsa/alsa-driver-1.0.14/pci/hda/../../alsa-kernel/pci/hda/patch_si3054.c:244: si3054: cannot initialize. EXT MID = 0000)
Also I added  options snd-hda-intel index=0 model=ref
Still no luck so far.

---

### Post by rikardocarvajal on 2007-06-04
I have two added the lates patches about realtek, and conexant but my headphones doesnt work, i've tested with model 3 stack, model 3, lenovo, model 6 stack, model 5 stack, etc. any suggestion, my laptop is a HP Pavilion tx1000, thanks

---

### Post by farbird on 2007-06-05
i also got the tx1000,

got speakers working but not the headphone jacks with the new drivers from alsa..

also skype says I have problems with sound device when i try to make a call

---

### Post by rikardocarvajal on 2007-06-08
i have 1 month searching for my tx1000 hp laptop headphones fix, but noting, i have test with all models in /etc/modprobe.d and nothing, some body can help me,,


Tanks,

---

### Post by farbird on 2007-06-09
no fix yet....

i think it is somethng to do with the dsdt acpi config which is not friendly with linux..

i bought a cheap usb soundcard in singapore to use as a temp solution until this is fixed..
the tx series is growing in popularity ... hope more experts can help...
did u get your touchscreen up yet?

see here for the touchscreen guide

[http://ubuntuforums.org/showthread.php?t=442483&page=2](http://ubuntuforums.org/showthread.php?t=442483&page=2)

---

### Post by krsnendu on 2007-06-09
I have an ASUS M2NPV-VM motherboard with onboard MCP51 soundcard (HDA-intel) .
I have installed Ubuntu Feisty Fawn 64 bit.
I would like to have 5.1 surround sound.

At present I get sound from the pink Center/Bass port. Other ports have produced some sound but there in a very annoying high pitched squeal coming form them. So at present I only have center and bass.

I have tried the line in alsa-base:

options snd-hda-intel index=0 model=6stack position_fix=0 single_cmd=0

I've also tried with 3stack and I get the hum both ways.

I also have the bug that sound stops when I change anything using the alsa mixer.

I tried to install the latest alsa (.14) it installed base. But I got an error trying to install utils.

Any help would be appreciated.

I also tried to install oss, but then I had no mixer in my sound settings gui and I couldn't figure out how to use the oss mixer. Some applications also stopped producing sound too.

Any tips where to start?

---

### Post by krsnendu on 2007-06-09
This is they output I get when trying to compile alsa utils.

```
Making all in alsactl
make[1]: Entering directory `/home/krsnendu/SoundFlashetc/alsa-utils-1.0.14rc4/alsactl'
if gcc -DHAVE_CONFIG_H -I. -I. -I../include     -g -O2 -MT alsactl.o -MD -MP -MF ".deps/alsactl.Tpo" -c -o alsactl.o alsactl.c; \
        then mv -f ".deps/alsactl.Tpo" ".deps/alsactl.Po"; else rm -f ".deps/alsactl.Tpo"; exit 1; fi
alsactl.c:123: fatal error: opening dependency file .deps/alsactl.Tpo: Permission denied
compilation terminated.
make[1]: *** [alsactl.o] Error 1
make[1]: Leaving directory `/home/krsnendu/SoundFlashetc/alsa-utils-1.0.14rc4/alsactl'
make: *** [all-recursive] Error 1

```

---

### Post by marcs on 2007-06-15
> **krsnendu said:**
> This is they output I get when trying to compile alsa utils.

```
Making all in alsactl
make[1]: Entering directory `/home/krsnendu/SoundFlashetc/alsa-utils-1.0.14rc4/alsactl'
if gcc -DHAVE_CONFIG_H -I. -I. -I../include     -g -O2 -MT alsactl.o -MD -MP -MF ".deps/alsactl.Tpo" -c -o alsactl.o alsactl.c; \
        then mv -f ".deps/alsactl.Tpo" ".deps/alsactl.Po"; else rm -f ".deps/alsactl.Tpo"; exit 1; fi
alsactl.c:123: fatal error: opening dependency file .deps/alsactl.Tpo: Permission denied
compilation terminated.
make[1]: *** [alsactl.o] Error 1
make[1]: Leaving directory `/home/krsnendu/SoundFlashetc/alsa-utils-1.0.14rc4/alsactl'
make: *** [all-recursive] Error 1

```

Remember to install alsa-driver and alsa-libs first or you cannot compile alsa-utils.

------------------------------------------
My Experience:

I got sound on the MCP51 ALC883 sound chip, but is covered by A DAMN PITCHED NOISE that never ends.

I hear music and all but over sound there's a lot of scratchy rumors!

I dunno what to do, i've also tried oss... and i got the same result...

I've tried position_fix and single_cmd stuff...

no luck... 

note : on MCP51 ALC883
the only model options are : 3stack-dig, 6stack-dig, auto

from the docs :
ALC882/883/885
 3stack-dig	3-jack with SPDIF I/O
 6stack-dig	6-jack digital with SPDIF I/O
auto		auto-config reading BIOS (default)

---

### Post by krsnendu on 2007-06-15
[QUOTE=marcs;2849896]Remember to install alsa-driver and alsa-libs first or you cannot compile alsa-utils.

Yes. I have installed alsa-driver and alsa-libs already. Have you managed to install the latest version of alsa-utils? Are the same problems still present?

---

### Post by farbird on 2007-06-15
try muting the input channels and see if it helps?

> **krsnendu said:**
> I have an ASUS M2NPV-VM motherboard with onboard MCP51 soundcard (HDA-intel) .
I have installed Ubuntu Feisty Fawn 64 bit.
I would like to have 5.1 surround sound.

At present I get sound from the pink Center/Bass port. Other ports have produced some sound but there in a very annoying high pitched squeal coming form them. So at present I only have center and bass.

I have tried the line in alsa-base:

options snd-hda-intel index=0 model=6stack position_fix=0 single_cmd=0

I've also tried with 3stack and I get the hum both ways.

I also have the bug that sound stops when I change anything using the alsa mixer.

I tried to install the latest alsa (.14) it installed base. But I got an error trying to install utils.

Any help would be appreciated.

I also tried to install oss, but then I had no mixer in my sound settings gui and I couldn't figure out how to use the oss mixer. Some applications also stopped producing sound too.

Any tips where to start?

---

### Post by krsnendu on 2007-06-15
> **farbird said:**
> try muting the input channels and see if it helps?
Changing anything in the mixer makes the sound stop completely.

---

### Post by saikat on 2007-06-16
**Thanks a lot. I've fixed the sound problem using your method.**

I'm using:

AMD Athlon64 X2 Dual-core 3600+
Biostar NF61V MicroAM2 mother board
1 GB DDR2 533 RAM
nVidia GeForce 6200 256MB PCIe graphics card
160 GB Seagate SATA + 40 GB Seagate IDE HDD
IEEE1394 Fireware Card
Windows XP Home
Kubuntu 7.04

---

### Post by saikat on 2007-06-16
> **pseudonym said:**
> My desktop has an nforce motherboard with an onboard HDA codec. The default ALSA config often won't detect the correct HD audio model, which is more than likely why you all don't have sound.

The solution, which btw is buried somewhere in the [Comprehensive Sound Guide]("http://www.ubuntuforums.org/showthread.php?t=205449"), is to do the following -

1. Extract /usr/share/doc/alsa-base/driver/ALSA-Configuration.txt.gz to your /home and open it up. This file contains extra config options for each ALSA module. Scroll down to ' Module snd-hda-intel' and read through this section. You may need to refer to your computer/motherboard's manual to find out which codec you have (ALC883, AD1988 etc). Then determine which of the model options applies to you - eg. you have an ASUS laptop, in which case you would choose the 'asus' option. Or you have a desktop with 5.1 or 7.1 onboard audio with digital out, in which case the right model is '6stack-digout'.

2. Once you have ascertained which HDA model applies to you, do this - ```
sudo gedit (or whichever editor you use) /etc/modprobe.d/snd-hda-intel.modprobe
add this line (it's a new file) -
options snd-hda-intel model=your-HDA-model
save and exit
```

3. Now do this - ```
sudo gedit /etc/modprobe.d/alsa-base
add this line at the end, with a two-line break from whatever is before -
options snd-hda-intel model=your-HDA-model
save and exit
```

4. Reboot, and you should now have sound :)

If this doesn't work you might also try using the OSS drivers from [Opensound]("http://www.opensound.com/"). I've since installed a dedicated sound card in my machine but I tested out Opensound's drivers first with the HD audio. This sound hardware seems to be better supported currently by Opensound and it is definitely worth considering installing their drivers.


**Thanks a lot. I've fixed the sound problem using your method.**

I'm using:

AMD Athlon64 X2 Dual-core 3600+
Biostar NF61V MicroAM2 mother board
1 GB DDR2 533 RAM
nVidia GeForce 6200 256MB PCIe graphics card
160 GB Seagate SATA + 40 GB Seagate IDE HDD
IEEE1394 Fireware Card
Windows XP Home
Kubuntu 7.04
:popcorn:

---

### Post by farbird on 2007-06-16
any updates?

---

### Post by fairlie on 2007-06-17
Anybody got this fixed on a Gateway laptop yet? Really want to ditch Windows for Ubuntu but can't until sound works :(

---

### Post by svega85 on 2007-06-17
no fix yet but i have joined two bug reports yesterday and suggest  you do the same here are the links 
[https://bugs.launchpad.net/ubuntu/+bug/57065](https://bugs.launchpad.net/ubuntu/+bug/57065) 
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/117246](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/117246)

---

### Post by fairlie on 2007-06-18
Thanks, I've done as you suggested :)

---

### Post by marcs on 2007-06-18
> **krsnendu said:**
> [QUOTE=marcs;2849896]Remember to install alsa-driver and alsa-libs first or you cannot compile alsa-utils.

Yes. I have installed alsa-driver and alsa-libs already. Have you managed to install the latest version of alsa-utils? Are the same problems still present?

I've compiled the latest new stable drivers (driver,libs and utils) from ALSA, all compiled without problems, but for me the problem of scratchy rumors over the sound remain... :( 

You can also try the linuxsound pack from realtek:
[ftp://202.65.194.212/pc/audio/realtek-linux-audiopack-4.06a.tar.bz2](ftp://202.65.194.212/pc/audio/realtek-linux-audiopack-4.06a.tar.bz2)

Contains driver, libs and utils and a script for compiling and installation.

I've tried it but i got the same problem of the scratchy sound.

p.s. I've tried also on gentoo (i'm on gentoo now)

---

### Post by Sean K on 2007-06-18
> **krsnendu said:**
> Changing anything in the mixer makes the sound stop completely.

I had this problem as well. I could get sound, but there would be a loud screeching noise accompanying whatever I would listen to. Changing anything in the mixer would make the sound completely stop. I changed to using the OSS drivers, but there are serious issues with that as well. Sound only from one app, no mixer, and only the front left/right channels work, plus bass.

I'm seriously surprised a fix for this hasn't been officially released yet. Lack of any sound whatsoever is a serious bug in **any** OS.

---

### Post by FloSynergy on 2007-06-22
hey folks,

way to go...
this solution is excellent!

i've been struggling for 3 days to get my sound to work...

then, sd-plissken pointed out this thread and the wiki.

now, i'm rocking to my favourite marley-tunes 

get-up - stand-up!

gigathanks,

flo

---

### Post by krsnendu on 2007-06-22
How do I post a bug report. I have a desktop computer with ASUS M2nPV-VM motherboard running AMD64 Feisty. I can only get clean audio from the center and bass speaker. All the other speakers (including headphones) produce an unpleasant high pitched squeal. When I change the volume using alsa mixer all the sound mutes until I reboot. I have tried the fixes mentioned in this thread (except I can get alsa-utils to upgrade) and no improvement. I would also like to get 5.1 sound, although stereo would be an improvement at this stage.



> **svega85 said:**
> no fix yet but i have joined two bug reports yesterday and suggest  you do the same here are the links 
[https://bugs.launchpad.net/ubuntu/+bug/57065](https://bugs.launchpad.net/ubuntu/+bug/57065) 
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/117246](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/117246)

---

### Post by Sean K on 2007-06-23
> **krsnendu said:**
> How do I post a bug report. I have a desktop computer with ASUS M2nPV-VM motherboard running AMD64 Feisty. I can only get clean audio from the center and bass speaker. All the other speakers (including headphones) produce an unpleasant high pitched squeal. When I change the volume using alsa mixer all the sound mutes until I reboot. I have tried the fixes mentioned in this thread (except I can get alsa-utils to upgrade) and no improvement. I would also like to get 5.1 sound, although stereo would be an improvement at this stage.

You're using ALSA drivers, right? The high pitched squealing noise is often just because of one speaker.. systematically unplug speaker by speaker from your bass, until the noise disappears.

Right now I'm using the OSS drivers, but this is even worse. It chooses to "selectively" work.. currently, I **only** have sound on Amarok.

Can anyone explain why this is the situation, and who is to blame for it?

---

### Post by krsnendu on 2007-06-23
I now have 3stack sound by plugging from the computer to the amp in the regular way then pluging the FR in its usual socket, and plugging FR into the SR socket. Any other plugs make the high pitched squeal. 

I would really like to get the 5.1 sound going and I want to be able to use the mixer without sound stopping altogether.

---

### Post by fairlie on 2007-06-25
Is anybody who has fixed the problems using a Gateway laptop/notebook?

---

### Post by svega85 on 2007-06-25
i'm using a gateway MX3414 but it dosn't work. the closest I've got was disabling the on board sound and buying some usb speakers :(

---

### Post by farbird on 2007-06-25
i tried a relatively low cost usb sound card that will work..
anyone interested?

i dun mind buying and shipping it out from spore.

---

### Post by fairlie on 2007-06-26
Sounds like a good solution until the internal sound card is working, I wonder if it'll be fixed in time for Gutsy Gibbon, would be nice to install with sound automatically working. Theres about 4 months to go so there could be a chance :)

---

### Post by JustBrowsing on 2007-06-28
Wow - I have a Gateway MT3418 laptop; just decided to try Ubuntu again after screwing up my partitions last week and completely having to re-do my Windows XP installation.

I tried "Wubi" for the first time last night, and was one of the most painless operating system installations I've ever seen ... unfortunately while getting Wireless working and hell even my NVidia video card -- sound still doesn't operate correctly.

Completely ridiculous ... this is insane. So, I have to quit Ubuntu and go to my Windows boot just to listen to music. Ugh. Give me a break. I can't believe this hasn't been fixed yet.

---

### Post by fairlie on 2007-06-30
Feel your pain mate, to me - sound is invaluable, I need it and I also need it to be with me, I cant take a usb speaker wherever I go - its inconvinient. For now I'm using Windows XP and popping back to Ubuntu every once and a while to try new "fixes".

I was wondering about an NDISWrapper style system for Sound drivers, obviously as a second choice to ALSA but it could be there for backup purposes. Is anyone aware of such a system?

---

### Post by brandoncolorado on 2007-07-09
We are coming up on the year anniversary of me announcing this problem with the MX3414.  I have posted in many places, informed many people.  ALSA knows, Ubuntu knows.  I don't know what else to do.  They say we can't complain because it is free, but how long should we wait before we complain.  I thought open source was supposed to be reactive and quick.  This is a problem on a year old laptop.

---

### Post by JustBrowsing on 2007-07-09
This has taken a year to fix? Welp, that answered my issue. I've uninstalled Wubi/Ubuntu ... looks like there is no fix for us Gateway users. Shame, Ubuntu is a fun Operating System to tinker with. Eh, oh well -- atleast there's always Windows XP and Vista. 

I'm trying PCLinuxOS as it's been far and away one of the easiest Linux setups around. Shame that this problem has been ignored for this long. I have to have some audio from my Operating System, can't do without it.... and many people are in the same situation as me.:(

---

### Post by brandoncolorado on 2007-07-09
Just to give you an idea of my frustration.....

Not only has this been a recognized issue for a year, the wireless on this laptop doesn't work correctly (no signal strength) and the correct video driver doesn't install on the mx3414 still.  A year!  I want to sit in my class of 80 students with Ubuntu, so I can help spread the word, and I can't find anyone to help with this issue.

---

### Post by svega85 on 2007-07-09
the video card works for me using a clean install of the i386 version of feisty faun, and i have the mx3414 too. but i didn't work for me when i had the amd64 version.

---

### Post by borris.morris on 2007-07-10
IT MAKES ME MAD!!! oh well, havent used the laptop much to begin with. if i got this working it would replace my 600 mhz thinkpad.

---

### Post by fairlie on 2007-07-11
Is anybody actually working on this? If so, will it be done for the 7.10 release?

---

### Post by JustBrowsing on 2007-07-11
> **fairlie said:**
> Is anybody actually working on this? If so, will it be done for the 7.10 release?
Doubt it. It's been a year and nothing really changed for at least Gateway users. Some Compaq users have their sound working, I'll be surprised if this will be fixed for 7.10.

---

### Post by fairlie on 2007-07-15
I'll buy an external one as a temp. solution. I'm really loving ubuntu right now but I miss my youtubing ;)

---

### Post by gaelfx on 2007-07-15
You guys, this is not part of the responsibility of Ubuntu staff to fix this problem, it has to do with ALSA not having enough separate drivers to deal with the multitude of cards that are used by numerous manufacturers. You shouldn't be asking "Is anybody even working on this?" or "Will it be better in the next release?" because it has nothing to do with what the people at Ubuntu are doing. Ubuntu, like most other OSes, just packages software together for people to use on their computers. Do you think M$ writes all those drivers for these cards if you're running Windows?

---

### Post by JustBrowsing on 2007-07-15
> **gaelfx said:**
> You guys, this is not part of the responsibility of Ubuntu staff to fix this problem, it has to do with ALSA not having enough separate drivers to deal with the multitude of cards that are used by numerous manufacturers. You shouldn't be asking "Is anybody even working on this?" or "Will it be better in the next release?" because it has nothing to do with what the people at Ubuntu are doing. Ubuntu, like most other OSes, just packages software together for people to use on their computers. Do you think M$ writes all those drivers for these cards if you're running Windows?

Wow man, calm down - I think a lot of people are speaking out of frustration. A bug that has been around for over a year and still hasn't even come close to working, I can see how it would frustrate the hell out of some users here.

---

### Post by fairlie on 2007-07-15
> **gaelfx said:**
> You guys, this is not part of the responsibility of Ubuntu staff to fix this problem, it has to do with ALSA not having enough separate drivers to deal with the multitude of cards that are used by numerous manufacturers. You shouldn't be asking "Is anybody even working on this?" or "Will it be better in the next release?" because it has nothing to do with what the people at Ubuntu are doing. Ubuntu, like most other OSes, just packages software together for people to use on their computers. Do you think M$ writes all those drivers for these cards if you're running Windows?

Sorry to cause offense but you have taken it way out of proportion. We've been discussing the issue as Ubuntu users, when we ask if any one is working on it - we ask generally, not just at Ubuntu developers. And the question of will it be better for the next release is very valid... as you said yourself, "Ubuntu, like most other OSes, just packages software together for people to use on their computers" - precisely mate, we wanted to know if they will ship it with a working package.

We also only ask because it's a fundamental part of any OS and daily computer usage. We like Ubuntu, that's why we've waited over a year for a fix.

And finally, "M$" - you're the kind of people who give the Linux userbase a bad reputation with those oh-so-witty remarks. Remember, Ubuntu is a community. Microsoft is a company. The primary aim of any company is to make profit - you have to respect that.

---

### Post by borris.morris on 2007-07-16
> **fairlie said:**
> Sorry to cause offense but you have taken it way out of proportion. We've been discussing the issue as Ubuntu users, when we ask if any one is working on it - we ask generally, not just at Ubuntu developers. And the question of will it be better for the next release is very valid... as you said yourself, "Ubuntu, like most other OSes, just packages software together for people to use on their computers" - precisely mate, we wanted to know if they will ship it with a working package.

We also only ask because it's a fundamental part of any OS and daily computer usage. We like Ubuntu, that's why we've waited over a year for a fix.

And finally, "M$" - you're the kind of people who give the Linux userbase a bad reputation with those oh-so-witty remarks. Remember, Ubuntu is a community. Microsoft is a company. The primary aim of any company is to make profit - you have to respect that.


Wow! Very well said. I am in almost total agrement. I am really frustrated that ALSA is doing nothing/very little to get this fixed! There must be some *EASY* way to get this working. Some ndiswrapper type util, but for audio. Like I said before, I'd love to replace this old thinkpad, but I HAVE to have my music. I was able to get beeps, i.e. in the terminal to work, so I was getting close.

---

### Post by cmat on 2007-07-16
Compile and install the latest RCs of ALSA. Fixed my problem with the same hardware.

---

### Post by borris.morris on 2007-07-16
When and what version? I have a Gateway MX1000??? Laptop.

---

### Post by gaelfx on 2007-07-16
I'm not trying to say that I'm offended or anything like that, I'm sorry if it came off as such. I know that Ubuntu should go out with working packages, but the issue is that there is not a working package solution to the problem for the moment, at least, not one that I've heard of. These kinds of problems are happening across many distros, if you look at google results for the topics on most of these threads you will find that Suse Fedora Gentoo, whatever flavor you pick has the problem.

What I'm trying to say is that these problems need to be directed at the people that are likely to solve them. I think it would be a good idea to try to figure out how we can help ALSA get this kind of stuff done so that ALL Linux distros can solve this problem. Sorry if I came off as snobbish or terse or "tsk, tskish" but I just think this is a major problem that needs a more direct path towards venting the frustration so that frustration can produce something.

Has anyone ever had success in aiding/communicating with ALSA people? I'd like to help if I could, but I'm not really sure where to go or what to do.

---

### Post by gaelfx on 2007-07-16
Also, out of curiosity about you Gateway users - Does your hardware information also list a C51 PCI Express Bridge in addition to the MCP51 SMBus and LPC Bridge? I just wonder about how similar our systems are because I'm on a Compaq Presario V3000 and have had no trouble getting sound, but loads of trouble figuring out what is going on with my mics. I've tried posting my (what seems to me) unique problem, but no one seems to look at the threads that I start.

---

### Post by JustBrowsing on 2007-07-16
> **fairlie said:**
> 

And finally, "M$" - you're the kind of people who give the Linux userbase a bad reputation with those oh-so-witty remarks. Remember, Ubuntu is a community. Microsoft is a company. The primary aim of any company is to make profit - you have to respect that.

I completely agree with the above remark. The one thing that I don't like about the Open Source community is that type of attitude. Not everyone has it, but it is there it's defiantly prevalent. I hate the little "$" that people put there. If it wasn't for Microsoft, computers and their mass apeall wouldn't be what it is today.

While Ubuntu is free as well as every other linux platform out there, it's still not nearly as easy to start up and install for many users. While many laptops work without a hitch, not all of them are like that. Even getting drivers working sometimes within Linux isn't nearly as easy as double clicking an application and it works. Ubuntu or Linux is a lot more user involved. 

Then there's the applications in Linux, there's many that just pale in comparison in the Windows or Mac field. In terms of photography and especially movies - Linux is a dead field in. It just gripes my *** when i see people bash Microsoft all that bad, they're a company they're there to make their shareholders happy.

---

### Post by fairlie on 2007-07-21
[Edited]

---

### Post by Jhongy on 2007-07-23
Just wanted to let you know that the solution on page 2 of this thread worked fine for me -- Asus laptop with AMD MCP51 audio. Through trial-n-error, the mode that worked was '3stack' (I want to try laptop'... '3stack' was the first that worked. 'asus' wasn't the right choice).

If you do it like I did, and you've turned all your volume sliders way up while fiddling with the modes, be prepared for a huge feedback whistle between the mic and the speakers the first time it springs into life.... this means it is working :-)

---

### Post by force4 on 2007-08-01
Fairlie...what would help the rest of us would be for you to edit your post and include it as a text file or link or anything else that would be a lot shorter than what it is.

To everyone else...Hi all.

I'm new to linux...2 weeks at fedora7 and now another 2 weeks with Ubuntu which I really like on my desktop...so I thought I'd install 7.04 on my laptop [hp dv2313ci].

And for me also...no sound. I have the same CARD = NVidia - CHIP = Conexant CX20549 (Venice)  that most of you have written about...so probably the same issue. I've read all the threads about this and tried everything I am experienced enough to risk...to no avail.

:idea: However...I think I have stumbled onto something that might help if only I could figure out why.

I have No sound with the default set to alsa in sound preferences. My other choices are:
Auto detect
Conexant Digital
Conexant Analog
ESD - enlightened sound deamon
OSS - open sound system

None of which seem to work. :(

However...in Ekiga in the preferences>general>sound events tab there is a popup for "Alternative  output device" with two options...[Default] which I assume points to what alsa is using and doesn't play sounds and [HDA NVidia] which works just fine and plays any sound I throw at it in both my speakers and headphones. :)

In the alsa configuration.txt there is only a section for hda-intel [which is what ubuntu set during the install] and no HDA NVidia section.

Can someone who is way more experienced moving around in linux [than I am] please tell me how [and where] to look to see what Ekiga is using to make the sound work in their package. They have found this HDA NVidia [thing] that alsa is thinking is hda-intel.

Maybe If I can set my snd configs to HDA NVidia I could get all my sound to work in the rest of my packages.

---

### Post by fairlie on 2007-08-28
Anybody had any more luck with this yet?

---

### Post by brandoncolorado on 2007-08-28
> **fairlie said:**
> Anybody had any more luck with this yet?

[https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2948](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2948)

Track the status of the attempts there.

---

### Post by FriedChips on 2007-09-09
I too am the proud owner of a deaf/dumb Gateway (mt3422). I am going to be trying out the new OSS drivers, when I can get them installed right, and will post back with the results. Right now I have not seen any gateway owners with working sound. I have seen several with ASUS and HP laptops get theirs mostly working with the exception of maybe, mic or headphone jacks. ( Boy would I love to be in their situation.)

I bought this laptop just yesterday wth mindset that nVidia was the best way to go. Boy was that a mistake. Let me say that nVidia did not cause this issue, but they sure as hell are doing a pretty good job of ignoring it. ALSA has made some progress on these cards it seems but not anything to help me. If I can't get this sound working my brand new laptop WILL be going on ebay.:confused:

---

### Post by natrix77 on 2007-09-26
I have a Acer AMD Turion 64 with nVidia MCP51 rev a2 audio device and I've just installed Feisty with dual boot with winXP, and of course I have NO SOUND!!!!!!!

I've seen there is a LOT of HELP but is there ANY solution to fix that problem??

I've tried most of the recommended posts but no luck so far.

Can anyone advised me what would be the correct steps from the scratch...

Right now, I don't know how the audio device is not recognised by the ubuntu...in XP the card is playing well.

PLEASE HELP!!!

---

### Post by FriedChips on 2007-09-27
Sorry man, I would help, but I just returned my laptop and got a different one. I really hope that get that bug fixed soon though. I'd hate to wind up with another one. The best I can say is make sure your whole system is up to date, try a few different distros and hope for one that works. You may also try to get the OSS drivers to work they supposedly support that card but I never had any luck. Good luck.

:guitar: <------ no sound?

---

### Post by dumshi on 2007-09-28
> **JustBrowsing said:**
> I completely agree with the above remark. The one thing that I don't like about the Open Source community is that type of attitude. Not everyone has it, but it is there it's defiantly prevalent. I hate the little "$" that people put there. If it wasn't for Microsoft, computers and their mass apeall wouldn't be what it is today.

While Ubuntu is free as well as every other linux platform out there, it's still not nearly as easy to start up and install for many users. While many laptops work without a hitch, not all of them are like that. Even getting drivers working sometimes within Linux isn't nearly as easy as double clicking an application and it works. Ubuntu or Linux is a lot more user involved. 

Then there's the applications in Linux, there's many that just pale in comparison in the Windows or Mac field. In terms of photography and especially movies - Linux is a dead field in. It just gripes my *** when i see people bash Microsoft all that bad, they're a company they're there to make their shareholders happy.

Hi,
I just would like to say that, people who have knowledge, pretends they don't know anything and move away from the whole TOPIC about MS and Linux. For rest of the people who just learned to type a command and saw it do something magical creates the TOPIC.

It's a show off world and people loves to show what they know, no matter how little it might be.

I don't know if m' making sence here.. just wrote to wrote... sorrie if i indirectly hurt someone..

Good Luck..

---

### Post by dumshi on 2007-09-28
DId you guys try this solution ??

[http://ubuntuforums.org/showthread.php?t=561576&highlight=intel+HDA+solved](http://ubuntuforums.org/showthread.php?t=561576&highlight=intel+HDA+solved)

Cheers.

---

### Post by aggieml on 2007-09-30
I finally got my sound working after a month of searching various posts!

I have the NVidia MCP51 High Definition Audio with the Sigmatel STAC 9200 chip on it.  It came with my Gateway MT3421 laptop.

I had given up on sound because everyone on forums had given up, but there's a patch for fixing this sound card on the alsa-bugs site!

Just go here and look for the post with the patch and follow the instructions:
[http://forums.fedoraforum.org/showthread.php?p=868053](http://forums.fedoraforum.org/showthread.php?p=868053)

A couple things:
1...you don't have to remove all alsa packages like he said in step 1.  All I did was remove alsa-lib and alsa-utils.
2...the patch file is at the bottom of the post as an attachment.

I hope this works for some of you!

Mike

---

### Post by borris.morris on 2007-10-02
HUZAH!!!! IT WORKED!!! Confirmed on a Gateway MT3418! Like a charm! I thank you! You are the biggest life saver!

---

### Post by svega85 on 2007-10-02
someone tell me when you got it working on a gateway mx3414

---

### Post by dutchcow on 2007-10-07
Im having the exact same problems as others describe here and i dont multi boot my laptop. It has one OS; ubuntu. Im getting pretty frustrated by the lack of action this problem seems to get, its not ubuntu, its alsa. Many (mostly) laptop users of different brands are suffering from dodgy, buggy or like in my case sometimes getting working sound but no sound most of the times. Even tho everything seems to work fine like VU meters moving just no sound coming out the speakers or headphone output. I've put in the chipset in many distro forums searches and found the same sort of problems for almost every distro out there, just not much action and no real fixes, rebooting without powerchord and things like that are just silly, blaming windows is silly too.

I guestimate that there are over 100 different people who took the time to report this problem, which means there's a bigger number of people who has no sound but isnt finding their way onto forums or irc or might switched back to another OS even. Maybe developers of the major distro's could pressure the alsa folks a bit, clearly something broke between the latest versions and the versions used in ubuntu 6.x (my sound is fine in there). Anyways, personally ive given up hope on this, first reports of this bug have been almost a year ago, i know i shouldnt complain about free software and all that. Im just venting my frustrations with this. If i wouldve gotten errors or something it wouldnt be a problem, the fact everything seems to work just no sound is coming out is the problem, i dont think im expected o reboot my laptop until i got working sound, its not very productive.

Before you ask, yes i've tried all the mixer settings and tips given in this thread and also other threads here and on other forums. I've signed up here just to tell my story. Im not a forum animal really. I've been using linux for a very long time and i've never had these kind of weird (almost windows like) problems where somethign works on some boots and doesnt on other boots. I want my dmesg to report errors or my mixer to stop working. I dont want xmms to show the vu meters as if sound is playing when i cant hear it.

Maybe starting a prayer circle could solve this, its clearly we need some divine intervention to get the alsa guys on this case.

--
HP/Compaq v3010au (v3000 series)
Conexant CX20549 (Venice) / nVidia Corporation MCP51 High Definition Audio (rev a2)

---

### Post by borris.morris on 2007-10-07
> **dutchcow said:**
> Im having the exact same problems as others describe here and i dont multi boot my laptop. It has one OS; ubuntu. Im getting pretty frustrated by the lack of action this problem seems to get, its not ubuntu, its alsa. Many (mostly) laptop users of different brands are suffering from dodgy, buggy or like in my case sometimes getting working sound but no sound most of the times. Even tho everything seems to work fine like VU meters moving just no sound coming out the speakers or headphone output. I've put in the chipset in many distro forums searches and found the same sort of problems for almost every distro out there, just not much action and no real fixes, rebooting without powerchord and things like that are just silly, blaming windows is silly too.

I guestimate that there are over 100 different people who took the time to report this problem, which means there's a bigger number of people who has no sound but isnt finding their way onto forums or irc or might switched back to another OS even. Maybe developers of the major distro's could pressure the alsa folks a bit, clearly something broke between the latest versions and the versions used in ubuntu 6.x (my sound is fine in there). Anyways, personally ive given up hope on this, first reports of this bug have been almost a year ago, i know i shouldnt complain about free software and all that. Im just venting my frustrations with this. If i wouldve gotten errors or something it wouldnt be a problem, the fact everything seems to work just no sound is coming out is the problem, i dont think im expected o reboot my laptop until i got working sound, its not very productive.

Before you ask, yes i've tried all the mixer settings and tips given in this thread and also other threads here and on other forums. I've signed up here just to tell my story. Im not a forum animal really. I've been using linux for a very long time and i've never had these kind of weird (almost windows like) problems where somethign works on some boots and doesnt on other boots. I want my dmesg to report errors or my mixer to stop working. I dont want xmms to show the vu meters as if sound is playing when i cant hear it.

Maybe starting a prayer circle could solve this, its clearly we need some divine intervention to get the alsa guys on this case.

--
HP/Compaq v3010au (v3000 series)
Conexant CX20549 (Venice) / nVidia Corporation MCP51 High Definition Audio (rev a2)

I totally agree with you, but it seems like they have finally started coming trough. I got it working thanks to aggieml!

---

### Post by TheCelloFellow on 2007-10-18
> **aggieml said:**
> I finally got my sound working after a month of searching various posts!

I have the NVidia MCP51 High Definition Audio with the Sigmatel STAC 9200 chip on it.  It came with my Gateway MT3421 laptop.

I had given up on sound because everyone on forums had given up, but there's a patch for fixing this sound card on the alsa-bugs site!

Just go here and look for the post with the patch and follow the instructions:
[http://forums.fedoraforum.org/showthread.php?p=868053](http://forums.fedoraforum.org/showthread.php?p=868053)

A couple things:
1...you don't have to remove all alsa packages like he said in step 1.  All I did was remove alsa-lib and alsa-utils.
2...the patch file is at the bottom of the post as an attachment.

I hope this works for some of you!

Mike

I've tried to get this working, but an not very good at translating between Fedora and Ubuntu. I also don't know how to remove the alsa packages without causing dependancy issues.

Could you please post exactly what you did? I'm really lost and my silent computer is making me rather crazy. (A silent computer drove me crazy in Windows too.)

Thank you for providing this information, it appears to have helped some, but I'm out of it.

Oh, and I'm using Gutsy, not Feisty, which strangely doesn't even *have* an alsa-lib package.

-Josh

---

### Post by dutchcow on 2007-10-23
> **daizone88 said:**
> I just got my sound to work on my Gateway MT 3422 laptop.  Just follow the link and the intsructions.  also the Alsa drivers are no longer rc's just the the 1.0.15 drivers for all and it works fine. [website removed] 

Too bad your page contains no help at all, anything you mention is already mentioned in this thead e.g. installing latest alsa, which isnt workign for all of us. Also your page reaks of advertising for another distro and you kinda "diss" ubuntu without any proper backing, no flame intented. If you want visitors on your boring blog please spam somewhere else. Like me there are people who want sound to work out of the box. I dont feel like manualy installing something from source or patch about on a system when i might have todo it on several laptops. Lets hope ubuntu will process the new alsa drivers and put them in the repo's asap.

---

### Post by Paradoxfox93 on 2007-11-19
> **TheCelloFellow said:**
> I've tried to get this working, but an not very good at translating between Fedora and Ubuntu. I also don't know how to remove the alsa packages without causing dependancy issues.

Could you please post exactly what you did? I'm really lost and my silent computer is making me rather crazy. (A silent computer drove me crazy in Windows too.)

Thank you for providing this information, it appears to have helped some, but I'm out of it.

Oh, and I'm using Gutsy, not Feisty, which strangely doesn't even *have* an alsa-lib package.

-Josh

Yes, translation please,  THough I am using feisty (Gusty crashes from networking on my MT3422). 

OR
*Bump*

---

### Post by MyR on 2007-11-21
[http://ubuntuforums.org/showthread.php?t=614903](http://ubuntuforums.org/showthread.php?t=614903)

---

### Post by Paradoxfox93 on 2007-11-21
> **dutchcow said:**
> Too bad your page contains no help at all, anything you mention is already mentioned in this thead e.g. installing latest alsa, which isnt workign for all of us. Also your page reaks of advertising for another distro and you kinda "diss" ubuntu without any proper backing, no flame intented. If you want visitors on your boring blog please spam somewhere else. Like me there are people who want sound to work out of the box. I dont feel like manualy installing something from source or patch about on a system when i might have todo it on several laptops. Lets hope ubuntu will process the new alsa drivers and put them in the repo's asap.

Actually I just got my audio working last night.  Still a few kinks trying to install utils but I have sound since the alsa drivers are what are patched.  The patch does work and I believe MyR linked to his translation of the instructions for us Ubuntu Newbies.  Thanks MyR!!

---

### Post by dutchcow on 2007-11-23
Don't know why abose poster quoted me :KS On my hardy-testing install still no sound, and also a clean install with the official 7.10 cd's gives no sound, even not after updating everything. Sound is fine in 6.xx. As others and myself described in previous posts, sometimes sound works, and then out of the blue it stops working. I'm running hardy along side 7.10, both have the same issues. Sometimes when i boot into slackware and reboot back into any of my ubuntu's the sound is working, one reboot later without going to slackware first et voila; no more sound, it must have something todo with alsa drivers used by slackware and some other distro's that do have working sound (eg elive). Hope this issue will be solved or i'm forced to quit using ubuntu as my main OS on my notebook, which would be a pitty cuz apart form sound everything works like a charm; 3d desktop, nvidia drivers, broadcom bcm43xx, card reader, firewire, etc, etc, all out of the box, it's just the sound that is dodgy :(

PS: I'm still using my HP/Compaq v3010AU with the "doomed"  Conexant CX20549 (Venice) / nVidia Corporation MCP51 High Definition Audio (rev a2)

---

### Post by skychen1900 on 2007-11-24
> **Gnuklear said:**
> Hey guys, I've been messing with the sound system on my AMD64 install of Dapper on my Gateway MX3414 laptop for the past 2 days or so with no luck, so I figured it was time to call in the experts. First, getting straight to the point, some system info:

```
$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```
```
$ lsmod
Module                  Size  Used by
nls_utf8                3584  0
nls_cp437               8320  0
vfat                   16768  0
fat                    57136  1 vfat
rfcomm                 45600  0
l2cap                  30464  5 rfcomm
bluetooth              59268  4 rfcomm,l2cap
ppdev                  11400  0
powernow_k8            12992  1
cpufreq_userspace       9184  1
cpufreq_stats           8264  0
freq_table              6464  2 powernow_k8,cpufreq_stats
cpufreq_powersave       3328  0
cpufreq_ondemand        9768  0
cpufreq_conservative    10984  0
video                  18824  0
tc1100_wmi              9096  0
sony_acpi               7188  0
pcc_acpi               16128  0
hotkey                 13768  0
dev_acpi               15364  0
container               6272  0
button                  8864  0
acpi_sbs               24600  0
battery                12296  1 acpi_sbs
i2c_acpi_ec             7040  1 acpi_sbs
ac                      7176  1 acpi_sbs
sg                     43696  0
sd_mod                 21504  0
dm_mod                 63176  1
md_mod                 76792  0
parport_pc             40816  0
lp                     15040  0
parport                44172  3 ppdev,parport_pc,lp
ipv6                  300416  10
joydev                 13184  0
tsdev                  10240  0
snd_hda_intel          22176  1
snd_hda_codec         175560  1 snd_hda_intel
r818x                  97808  0
ieee80211_rtl          90384  1 r818x
snd_pcm_oss            48416  0
snd_mixer_oss          20480  1 snd_pcm_oss
snd_pcm               103560  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
psmouse                40324  0
pcspkr                  3592  0
snd_timer              29064  1 snd_pcm
serio_raw               9732  0
usb_storage            82112  0
nvidia               5433176  0
i2c_core               26624  2 i2c_acpi_ec,nvidia
snd                    70880  8 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              13216  1 snd
snd_page_alloc         13968  2 snd_hda_intel,snd_pcm
shpchp                 51360  0
pci_hotplug            33168  1 shpchp
af_packet              28172  4
evdev                  14464  1
ext3                  145936  1
jbd                    70952  1 ext3
ide_generic             2816  0
ehci_hcd               36232  0
ohci_hcd               23684  0
usbcore               147004  4 usb_storage,ehci_hcd,ohci_hcd
forcedeth              34444  0
ide_cd                 35744  0
cdrom                  41144  1 ide_cd
ide_disk               19456  3
generic                 7300  0
amd74xx                17072  0 [permanent]
sata_nv                12548  0
libata                 85536  1 sata_nv
scsi_mod              160504  4 sg,sd_mod,usb_storage,libata
thermal                16524  0
processor              29736  2 powernow_k8,thermal
fan                     6408  0
capability              7176  0
commoncap               9728  1 capability
vga16fb                15120  1
cfbcopyarea             5120  1 vga16fb
vgastate               10368  1 vga16fb
cfbimgblt               4224  1 vga16fb
cfbfillrect             5760  1 vga16fb
fbcon                  43136  72
tileblit                4096  1 fbcon
font                    9984  1 fbcon
bitblit                 7424  1 fbcon
softcursor              3712  1 bitblit

```
```
$ sudo lspci -v
0000:00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
        Subsystem: Gateway 2000: Unknown device 0317
        Flags: bus master, 66MHz, fast devsel, latency 0
        Capabilities: [44] #08 [01e0]
        Capabilities: [e0] #08 [a800]

0000:00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
        Subsystem: Gateway 2000: Unknown device 0317
        Flags: 66MHz, fast devsel

0000:00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
        Subsystem: Gateway 2000: Unknown device 0317
        Flags: 66MHz, fast devsel

0000:00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
        Subsystem: Gateway 2000: Unknown device 0317
        Flags: 66MHz, fast devsel

0000:00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
        Subsystem: Gateway 2000: Unknown device 0317
        Flags: bus master, 66MHz, fast devsel, latency 0

0000:00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
        Subsystem: Gateway 2000: Unknown device 0317
        Flags: bus master, 66MHz, fast devsel, latency 0
        Capabilities: [44] #00 [00fe]
        Capabilities: [fc] #00 [0000]

0000:00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
        Subsystem: Gateway 2000: Unknown device 0317
        Flags: 66MHz, fast devsel

0000:00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
        Subsystem: Gateway 2000: Unknown device 0317
        Flags: 66MHz, fast devsel

0000:00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=04, sec-latency=0
        I/O behind bridge: 00009000-00009fff
        Memory behind bridge: fa100000-fa8fffff
        Prefetchable memory behind bridge: 00000000bdf00000-00000000bfe00000
        Capabilities: [40] #0d [0000]
        Capabilities: [48] Power Management version 2
        Capabilities: [50] Message Signalled Interrupts: 64bit+ Queue=0/1 Enable+
        Capabilities: [60] #08 [a800]
        Capabilities: [80] #10 [0141]

0000:00:05.0 VGA compatible controller: nVidia Corporation C51 PCI Express Bridge (rev a2) (prog-if 00 [VGA])
        Subsystem: Gateway 2000: Unknown device 0317
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 217
        Memory at b2000000 (32-bit, non-prefetchable) [size=16M]
        Memory at c0000000 (64-bit, prefetchable) [size=256M]
        Memory at b1000000 (64-bit, non-prefetchable) [size=16M]
        Expansion ROM at 50000000 [disabled] [size=128K]
        Capabilities: [48] Power Management version 2
        Capabilities: [50] Message Signalled Interrupts: 64bit+ Queue=0/0 Enable-

0000:00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
        Subsystem: Gateway 2000: Unknown device 0317
        Flags: bus master, 66MHz, fast devsel, latency 0
        Capabilities: [44] #08 [01e9]
        Capabilities: [e0] #08 [a801]

0000:00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
        Subsystem: Gateway 2000: Unknown device 0317
        Flags: bus master, 66MHz, fast devsel, latency 0

0000:00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
        Subsystem: Gateway 2000: Unknown device 0317
        Flags: 66MHz, fast devsel, IRQ 10
        I/O ports at 3040 [size=64]
        I/O ports at 3000 [size=64]
        Capabilities: [44] Power Management version 2

0000:00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
        Subsystem: Gateway 2000: Unknown device 0317
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 10
        Memory at b0040000 (32-bit, non-prefetchable) [size=256K]

0000:00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3) (prog-if 10 [OHCI])
        Subsystem: Gateway 2000: Unknown device 0317
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 201
        Memory at b0004000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [44] Power Management version 2

0000:00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3) (prog-if 20 [EHCI])
        Subsystem: Gateway 2000: Unknown device 0317
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 209
        Memory at b0005000 (32-bit, non-prefetchable) [size=256]
        Capabilities: [44] #0a [2098]
        Capabilities: [80] Power Management version 2

0000:00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1) (prog-if 8a [Master SecP PriP])
        Subsystem: Gateway 2000: Unknown device 0317
        Flags: bus master, 66MHz, fast devsel, latency 0
        I/O ports at 3080 [size=16]
        Capabilities: [44] Power Management version 2

0000:00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2) (prog-if 01 [Subtractive decode])
        Flags: bus master, 66MHz, fast devsel, latency 0
        Bus: primary=00, secondary=06, subordinate=06, sec-latency=64
        I/O behind bridge: 00006000-00006fff
        Memory behind bridge: b3400000-b34fffff
        Capabilities: [b8] #0d [0000]
        Capabilities: [8c] #08 [a800]

0000:00:10.1 0403: nVidia Corporation MCP51 High Definition Audio (rev a2)
        Subsystem: Gateway 2000: Unknown device 0317
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 225
        Memory at b0000000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: [44] Power Management version 2
        Capabilities: [50] Message Signalled Interrupts: 64bit+ Queue=0/0 Enable-
        Capabilities: [6c] #08 [a802]

0000:00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
        Subsystem: Gateway 2000: Unknown device 0317
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 193
        Memory at b0006000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at 3090 [size=8]
        Capabilities: [44] #00 [0000]

0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
        Flags: fast devsel
        Capabilities: [80] #08 [2101]

0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
        Flags: fast devsel

0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
        Flags: fast devsel

0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
        Flags: fast devsel
        Capabilities: [f0] #0f [0010]

0000:06:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd.: Unknown device 8185 (rev 20)
        Subsystem: Realtek Semiconductor Co., Ltd.: Unknown device 8185
        Flags: bus master, medium devsel, latency 64, IRQ 11
        I/O ports at 6000 [size=256]
        Memory at b3400000 (32-bit, non-prefetchable) [size=512]
        Capabilities: [50] Power Management version 2

```
```
$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.11.
Compiled on Aug 19 2006 for kernel 2.6.15-26-amd64-generic (SMP).

```
Yes, that is a manually compiled version. Still no luck

All sound channels (that I can find anyway) are enabled and turned to full volume.

I've tried playing sound files with Totem (vorbis files, so I know they should play correctly on a default install) and the player seems to think everything is working. The ONLY visible sign that sound isn't working is that "vumeter" NEVER displays any change of volume - is always shows nothing playing.

I've tried compiling a newer version of ALSA (1.0.11 Final) with no improvement. Any help is appreciated. If at all possible, I'd like to avoid using nVidia's proprietary drivers.

I hava same problem at first ,  just add this to the file /etc/modprobe.d/alsa-base

```
options snd-hda-intel index=0 model=3stack-dig
```

---

### Post by aggieml on 2007-12-03
OK apparently people were confused about my previous post (about 8 posts ago) in which I described how I patched the NVidia MCP51 (Sigmatel STAC 9200 chip), so I'll try and be more specific here.  

Let me start off by saying that I was able to use this method to get my sound working on PCLinuxOS2007 (which makes me think it should also work in Mandriva) and on Mepis (which makes me think it should also work on Debian).  Since Ubuntu is based on Debian, I assume this should work for Ubuntu but I have not tested it.However, I could not get it to fix my sound on OpenSuse 10.3.

Here's what I did:

1...open synaptic and search for 'alsa'.  Uninstall alsa-driver, alsa-utils, and alsa-lib if they're installed.
2...download the latest versions of alsa-driver, alsa-utils, and alsa-lib from alsa-project.org (for this example, I've downloaded them to my desktop)
3...create a folder 'alsa' in /usr/local/src. (type sudo mkdir /usr/local/src/alsa from terminal).
4...then in terminal change to the alsa directory (type cd /usr/local/src/alsa).  Not sure if you'll need to use sudo for this.  
4...Untar all 3 downloaded alsa tar files into the alsa folder (in terminal, type: tar xjvf /home/mikael/Desktop/alsa-utils-1.0.15.tar.bz2 and then do the same for alsa-lib and alsa-driver)
5...go to [https://bugtrack.alsa-project.org/alsa-bug/view.php?id=3036](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=3036).  Click on 'guest view only' so you can get to the posts.  There's a really long post there that has the sigmatel patch attached.  Download the patch called  patch_sigmatel.c.patch-1.0.15rc1-simple and save it to the alsa folder above.
6...type patch alsa-driver-1.0.15rc1/alsa-kernel/pci/hda/patch_sigmatel.c < patch_sigmatel.c.patch-1.0.15rc1-simple.  You should see a success message.
7... cd into the alsa-lib folder of that directory (cd alsa-lib....) then type ./configure then make then make install (you need sudo for make install).
8...then cd into the alsa-utils folder of that directory (cd ../alsa-utils...) then type ./configure then make then make install (you need sudo for make install).
9...then cd into the alsa-driver folder of that directory (cd ../alsa-driver...) then type ./configure then make then make install
10... you may get build errors (for example, you may need to download and install kernel-headers or kernel-source or ncurses-dev).  If so, go install those and then continue.
11...then restart and your sound should work.  When you boot back up, make sure your volume isn't muted by opening kmix.


Hope this works, and hope my steps were clear enough.  

Mike

---

### Post by Blehhh on 2007-12-06
I have the solution!

I googled till i gone mad, but finally i found it:)

You can find it on my how-to website.

[http://www.tellmehow.nl/?p=8]("http://www.tellmehow.nl/?p=8")

Hope this will help you guys. I had the same problem and it took me more than 2 week of intensive trying and googling. So i hope i helped you out with this.

Please 

Greetings

---

### Post by dutchcow on 2007-12-08
> **Blehhh said:**
> I have the solution!
I googled till i gone mad, but finally i found it:)
You can find it on my how-to website.
Hope this will help you guys. I had the same problem and it took me more than 2 week of intensive trying and googling. So i hope i helped you out with this.
Please 
Greetings

I'm glad that worked for you, not to sound sarcastic but if you would have spend an hour reading trough the 13 pages of this thread you would've saved yourself 2 weeks of time.

The "model=" part in /etc/modprobe.d/alsa-base has been discussed many times and while it works for some it does not work for everybody, I have tried every single option, whether or not it is supported by my card, and I'm still without sound, sound only works when using a trick like booting up without the AC plugged in. 

Also i find it annoying people don't post the actual procedure here but try to drive traffic to their site, that is how i see it. Someone did the same a few posts up and got their post removed. In my opinion before posting in a thread you should read it fully and when you post include details and not a link to your own site. This will seem like you want to attract people to your site instead of participating in the thread. As i said i'm glad it worked for you, but it doesn't work for many which you would known if you read the entire thread.

In my case my chipset is not even in the list, and all 3 Conexant chipsets options do not work for my laptop. I'm using a HP laptop with an nVidia Conexant CX20549 Venice. It is used in most HP and Compaq laptops, v3000 series and many dvXXXX series. Anyways, the problem is not ubuntu but the alsa developers which has been explained  in detail in this thread.

---

### Post by czelusniak11 on 2008-01-05
1) Right click the speaker on panel, choose "Open Volume Control"
2) Click "Options" tab. If you don't see the options tab, edit preferences and enable "Digital input source", this will make it appear.
3) Change the "Digital Input Source" to "Digital Mic 1" from "Analog Inputs".

---

### Post by svega85 on 2008-01-05
ok for everyone with sound issues especially gatways mx3414 the new ubuntu hardy heron alpha 2 fixes the sound issues of course it's still an alpha but it works

---

### Post by TheCelloFellow on 2008-01-05
hooray!

---

### Post by brandoncolorado on 2008-01-05
I wouldn't recommend upgrading to Hardy Heron yet, stick with 7.10 (Gutsy).  Just upgrade to the lastest version of ALSA and your problems will be solved.  In hardy, they just used this latest version (.15).

---

### Post by dutchcow on 2008-01-12
I can also report fixed sound on the latest daily hardy builds, woohoo! I did some testing, a lot of rebooting with and without AC connected and the sound keeps working. Lets hope they don't break it again ;) Also i hope they merge the latest alsa stuff into gutsy for the faint of heart or those who don't want to risk their stable system running pre-release software.

---

### Post by zirtik on 2008-01-13
Do I have to install the latest hardy release or is there an easier workaround to get those drivers without having to install hardy? I am on a 7.10 Gutsy and have the exact same problem, going nuts!!!

---

### Post by dutchcow on 2008-01-13
You don't have to install hardy, you can get the working alsa version and compile/install it from source, or wait until it gets on the gutsy repo's. The vesion hardy is using is 1.0.15. Good luck!

---

### Post by zirtik on 2008-01-13
> **dutchcow said:**
> You don't have to install hardy, you can get the working alsa version and compile/install it from source, or wait until it gets on the gutsy repo's. The vesion hardy is using is 1.0.15. Good luck!

I couldn't wait for that and tried to install hardy using Synaptic last night. The result was that I got sound working however now I can't make ubuntu detect my Nvidia 7150m graphics card so I need to install Gutsy again and wait for ALSA 1.0.15. 

About compiling from the source, I tried that already but ended up with an x sign on the right bottom corner telling me that no sound card is detected. I dunno what I did wrong though, all I did was installing all the ALSA drivers, tools and utils via configure, make, make install steps.

The strange thing is that sound was working when I first installed Gutsy on my laptop but after I did all the updates and rebooted I couldn't get it to work again. 

I wish there was another solution other than waiting. Any ideas?

PS: I will try to install Gutsy tonight so can you tell me to avoid any suspicious updates that can lead to problems with sound, such as Kernel maybe?

---

### Post by dutchcow on 2008-01-13
I've had the same with my gutsy install, sometimes sound would just work, for example when booting up without the AC plugged in. And at other times the sound was just dead (most of the times). It is a known "bug" at the part of alsa, and as it seems they have fixed it in 10.0.15.

About your nvidia not being detected, on my hardy the restricted driver manager was not automaticly installed, maybe that is why your nvidia is not detected, you can install the restricted driver manager via synatic or on the console "sudo apt-get install restricted-manager" which should give you the restricted manager link back in the System -> Administration menu's. You might need to reboot to make it work, i recall after i installed it only asked for my password and then never show me the driver list inside the manager, a reboot fixed that. 

You can also install the nvidia driver manualy by installing the nvidia-glx package via synaptics or the console and then run "sudo nvidia-xconfig" on the console, to setup xorg. It will backup your old xorg.conf, don't worry. I hope ubuntu devs will put the 10.0.15 alsa drivers in to the repo's asap. Let me know if you run into any problems with nvidia.

Edit:
If after running nvidia-xconfig you have no borders on the windows whilst running compiz/desktop effects, you need edit your xorg.conf by hand and add these 2 lines to the device section of Nvidia card:
```
Option "AddARGBVisuals" "True"
Option "AddARGBGLXVisuals" "True"
```Be sure to make a backup of your xorg.conf like this: "sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf-mybackup"
Then on the console run "sudo gedit /etc/X11/xorg.conf" to edit X's config. Scroll down or search on "nvidia" to find the right device section and paste in those 2 lines.
If anything goes wrong or if you want to restore the backup simply do: "sudo cp /etc/X11/xorg.conf-mybackup /etc/X11/xorg.conf"

My device section for my gefoce 6150 go looks like this:
```
Section "Device"
        Identifier  "Card0"
        Driver      "nvidia"
        VendorName  "nVidia Corporation"
        BoardName   "C51 [Geforce 6150 Go]"
        BusID       "PCI:0:5:0"
        Option      "AddARGBVisuals"    "True"
        Option      "AddARGBGLXVisuals" "True"
        Option      "NoLogo"            "True"
EndSection
```

---

### Post by lzfy on 2008-01-14
> **zirtik said:**
> I couldn't wait for that and tried to install hardy using Synaptic last night. The result was that I got sound working however now I can't make ubuntu detect my Nvidia 7150m graphics card so I need to install Gutsy again and wait for ALSA 1.0.15. 

About compiling from the source, I tried that already but ended up with an x sign on the right bottom corner telling me that no sound card is detected. I dunno what I did wrong though, all I did was installing all the ALSA drivers, tools and utils via configure, make, make install steps.


Same here. :(

---

### Post by Yellow Pasque on 2008-01-14
Don't upgrade to hardy just for ALSA 1.0.15
YOu can probably get it through linux-backports-modules or just build it yourself with directions here (scroll down to "Method B"): [https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller)
Use 1.0.15 instead of 1.0.15rc1 in the filename

---

### Post by zirtik on 2008-01-15
> **dutchcow said:**
> I've had the same with my gutsy install, sometimes sound would just work, for example when booting up without the AC plugged in. And at other times the sound was just dead (most of the times). It is a known "bug" at the part of alsa, and as it seems they have fixed it in 10.0.15.

About your nvidia not being detected, on my hardy the restricted driver manager was not automaticly installed, maybe that is why your nvidia is not detected, you can install the restricted driver manager via synatic or on the console "sudo apt-get install restricted-manager" which should give you the restricted manager link back in the System -> Administration menu's. You might need to reboot to make it work, i recall after i installed it only asked for my password and then never show me the driver list inside the manager, a reboot fixed that. 

You can also install the nvidia driver manualy by installing the nvidia-glx package via synaptics or the console and then run "sudo nvidia-xconfig" on the console, to setup xorg. It will backup your old xorg.conf, don't worry. I hope ubuntu devs will put the 10.0.15 alsa drivers in to the repo's asap. Let me know if you run into any problems with nvidia.

Edit:
If after running nvidia-xconfig you have no borders on the windows whilst running compiz/desktop effects, you need edit your xorg.conf by hand and add these 2 lines to the device section of Nvidia card:
```
Option "AddARGBVisuals" "True"
Option "AddARGBGLXVisuals" "True"
```Be sure to make a backup of your xorg.conf like this: "sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf-mybackup"
Then on the console run "sudo gedit /etc/X11/xorg.conf" to edit X's config. Scroll down or search on "nvidia" to find the right device section and paste in those 2 lines.
If anything goes wrong or if you want to restore the backup simply do: "sudo cp /etc/X11/xorg.conf-mybackup /etc/X11/xorg.conf"

My device section for my gefoce 6150 go looks like this:
```
Section "Device"
        Identifier  "Card0"
        Driver      "nvidia"
        VendorName  "nVidia Corporation"
        BoardName   "C51 [Geforce 6150 Go]"
        BusID       "PCI:0:5:0"
        Option      "AddARGBVisuals"    "True"
        Option      "AddARGBGLXVisuals" "True"
        Option      "NoLogo"            "True"
EndSection
```

Thank you for your reply. I installed the restricted drivers manager but when I launch it I can't see the NVidia Drivers listed! I tried  sudo apt-get install nvidia-glx and it gives me:


```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
nvidia-glx is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
```

so when I type 

sudo nvidia-xconfig

```
Using X configuration file: "/etc/X11/xorg.conf".

VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.
                  Device section "Configured Video Device" must have a Driver
                  line.

Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

```

Suggestions?

---

### Post by zirtik on 2008-01-15
Ok I fixed it by installing nvidia-glx-new drivers. A simple reboot and bingo! Now I have both sound and graphics. One final question is that the refresh rate for my laptop seems to be 50 Hz and I was wondering if there is a way to increase it to 60 Hz just like it was in Gutsy? Thanks...

---

### Post by silver-city-productions on 2008-03-05
This is kind of a long thread.  Is there anyone out there who could summarize (like, one line step descriptions is all) what needs doing from scratch to get sound going on the MCP51 HDA?  I was hoping to put together a page showing the steps to get the Gateway MT3422 fully linux-ized.  (There are two issues; the wireless adapter and the soundcard.  I am still working the soundcard myself.)

So far, updated ALSA to 1.0.16 level, installed nvidia-glx-new.  I rebooted, but no Bingo! for me yet.  I am guessing there is an intermediate step or two I missed.

thanks!

---

### Post by wandalalakers on 2008-03-06
> **svega85 said:**
> ok for everyone with sound issues especially gatways mx3414 the new ubuntu hardy heron alpha 2 fixes the sound issues of course it's still an alpha but it works

My Dell still doesn't have sound when I upgraded to heron.  I guess I'll have to reinstall 7.10 because now my network connection doesn't work.  I guess I won't do anymore updates until April.

---

### Post by silver-city-productions on 2008-03-06
> **silver-city-productions said:**
> This is kind of a long thread.  Is there anyone out there who could summarize (like, one line step descriptions is all) what needs doing from scratch to get sound going on the MCP51 HDA?  I was hoping to put together a page showing the steps to get the Gateway MT3422 fully linux-ized.  (There are two issues; the wireless adapter and the soundcard.  I am still working the soundcard myself.)

So far, updated ALSA to 1.0.16 level, installed nvidia-glx-new.  I rebooted, but no Bingo! for me yet.  I am guessing there is an intermediate step or two I missed.

thanks!

Played some more last night and got farther along.  Presently, the sound card is there, all the software says its up and running, mixers show output going to the card, I don't see any indication of it being muted, and I hear nothing.  Progress is being made, and I will get this laptop up to speed totally!

I did in fact miss some of the steps in the Comprehensive Sound Guide; I had to install the snd-hda-intel alsa driver to get where I'm at presently.  I advise if you are reading this thread to look at that first.  Link at the beginning of this thread.

---

### Post by grooveman on 2008-03-08
> **Nicostarnux said:**
> Quite marvellous ... this is the line that got me out the silence ;) ;) ;)

BTW, I got an Asus A7T, Feisti brought me the air network with the Atheros chipset and I've almost all my hardware supported by now !!!!!

Thanks a lot

Hi.  I have an asus A7T as well... I added the magic line to the end of my /etc/moprobe.d/alsa-base... but it still does not work.  I get nothing from my speakers.  All channels are unmuted... I don't get it.

Any chance someone can post their entire alsa-base file so I can see?

Thanks.

G

---

