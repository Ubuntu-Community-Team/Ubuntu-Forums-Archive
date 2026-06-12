---
title: "No sound from EV1938 - Gateway Solo 2150 (Edgy)"
date: 2007-01-27
forum: Multimedia &amp; Video
---

### Post by ftmichael on 2007-01-27
I'm running Ubuntu Feisty (upgraded from Edgy) on a Gateway Solo 2150 laptop.  My sound card is a Creative Labs Ectiva 1938.  I have no sound at all - the upgrade to Feisty didn't help at all.

When I go to System->Preferences-->Sound and try to test any of the devices, I get the same error:

> gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink
profile=chat: Could not open resource for writing.

When I switch to the Sounds tab in Sound Preferences, there are no options available for the default sound card.

**lsmod | grep snd** gives me:
> snd_ens1370            20256  0 
snd_ak4531_codec        9088  1 snd_ens1370
snd_ens1371            26272  0 
gameport               15368  2 snd_ens1370,snd_ens1371
snd_rawmidi            25600  2 snd_ens1370,snd_ens1371
snd_seq_device          8972  1 snd_rawmidi
snd_ac97_codec         96672  1 snd_ens1371
snd_ac97_bus            2432  1 snd_ac97_codec
snd_pcm_oss            46080  0 
snd_mixer_oss          18560  1 snd_pcm_oss
snd_pcm                80520  4 snd_ens1370,snd_ens1371,snd_ac97_codec,snd_pcm_oss
snd_timer              23172  1 snd_pcm
snd                    55428  10 snd_ens1370,snd_ak4531_codec,snd_ens1371,snd_rawmidi,snd_seq_device,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9952  1 snd
snd_page_alloc         10504  2 snd_ens1370,snd_pcm

**lspci** gives me:
> 00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
00:07.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 03)
00:08.0 CardBus bridge: Texas Instruments PCI1225 (rev 01)
00:08.1 CardBus bridge: Texas Instruments PCI1225 (rev 01)
00:09.0 Multimedia audio controller: Creative Labs Ectiva EV1938
00:0a.0 PCI bridge: Actiontec Electronics Inc Mini-PCI bridge (rev 11)
01:00.0 VGA compatible controller: ATI Technologies Inc Rage Mobility P/M AGP 2x (rev 64)
02:04.0 Ethernet controller: Intel Corporation 82557/8/9 [Ethernet Pro 100] (rev 08)
02:08.0 Communication controller: Agere Systems WinModem 56k (rev 01)

**modinfo snd-ens1371** gives me:
> filename:       /lib/modules/2.6.17-10-386/kernel/sound/pci/snd-ens1371.ko
author:         Jaroslav Kysela <perex@suse.cz>, Thomas Sailer <sailer@ife.ee.ethz.ch>
license:        GPL
description:    Ensoniq/Creative AudioPCI ES1371+
vermagic:       2.6.17-10-386 mod_unload 486 REGPARM gcc-4.1
depends:        snd-pcm,snd-rawmidi,snd,gameport,snd-ac97-codec
alias:          pci:v00001274d00001371sv*sd*bc*sc*i*
alias:          pci:v00001274d00005880sv*sd*bc*sc*i*
alias:          pci:v00001102d00008938sv*sd*bc*sc*i*
srcversion:     42F98C8B4D99DB1EDF461BB
parm:           lineio:Line In to Rear Out (0 = auto, 1 = force). (array of int)
parm:           spdif:S/PDIF output (-1 = none, 0 = auto, 1 = force). (array of int)
parm:           joystick_port:Joystick port address. (array of int)
parm:           enable:Enable Ensoniq AudioPCI soundcard. (array of bool)
parm:           id:ID string for Ensoniq AudioPCI soundcard. (array of charp)
parm:           index:Index value for Ensoniq AudioPCI soundcard. (array of int)


Help!

Michael

---

### Post by ftmichael on 2007-01-27
Bump.

Anyone have any thoughts?

---

### Post by ftmichael on 2007-08-16
Bump.

---

### Post by LinuxNewb_22 on 2007-10-03
ftmichael, I have the same problem with my desktop and Feisty.

I was having sound problems with my motherboard (M2N-E SLI) - couldn't figure out how to get that going at all. Then I decided to buy a cheap, older sound card that I thought would work - Creative Sound Blaster 16 PCI.

Everything showed up in lspci for me - I got the same name for Multimedia Audio Controller -- Creative Labs Ectiva EV1938.

I went on to the alsa-project site and configured, compiled and installed the drivers for SB 16 PCI (being ens1371)... and still nada.

I originally decided to go with an AMD processor and Linux OS because I thought it would end up being cheaper for a quick and powerful system than running and Intel processor and Windows OS. I've managed to get everything running except for sound. I'm really loving it, but just don't want to spend too much more money on the thing.

If anybody has an answer to or advice for this problem, ftmichael and I would really appreciate your help.

As a token of my appreciation for the many helpful people on this and similar forums, when I get the time in the next couple of days, I will post a HOW TO on running RAID 0 (which is what I've managed to set up just recently) with Feisty, an ATI graphics card (Sapphire Radeon X1650PRO), and Compiz Fusion from all of the sources that I've read.

I love the system, it works beautifully, Ubuntu is amazing and looks fantastic with Compiz Fusion... 

...if only I could get the sound working.

---

### Post by fissionmailed on 2007-10-07
*raises head*

I have the same computer and the same problem.  I've searched here before and saw a couple of threads about it.  I tried to do what they said in the threads but I'm such a n00b at linux I got lost rather easily. 
*facepalm*

---

### Post by wsmoser2004 on 2007-10-16
I might be able to help!  I have the Gateway Solo 2150 with the EV1938 that the original poster talked about.  At a high level, basically what I had to do to get this working was to use OSS for my sound driver, instead of ALSA.  I have a lot of annoying problems with OSS (my volume control doesn't work, for example :)) but at least I have sound.  Your mileage may vary.

Basically here's what you'll want to do.  You want to "blacklist" the ALSA kernel module so that Ubuntu doesn't try to use ALSA.  To do that, open a terminal and type

```

sudo gedit /etc/modprobe.d/blacklist

```

At the end of the file, add

```

snd_ens1371

```

Now you will want to "un-blacklist" the OSS module.  To do that, 

```

sudo gedit /etc/modprobe.d/blacklist-oss

```

in the terminal, find the line that says "es1371", and put a # in front of it.  Then you'll have 

```

#es1371

```

on that line in the file.  Finally, you'll want to tell Ubuntu to load that module when you boot, so open up 

```

sudo gedit /etc/modules

```

and add 

```

es1371

``` 

to the end of the file.  Then, reboot.  You should now have sound!  Hopefully the volume control will work for you, it doesn't work for me in Xubuntu.  I just use the volume control in whatever application I happen to be using at the moment.

I also don't know whether the desktop PCI card will work the same as the laptop card.  Let me know how it works!

---

### Post by fissionmailed on 2007-10-19
To wsmoser2004:

I tried that and it didn't work. :\  I'll have to try it again over the weekend to make sure I didn't screw things up somehow.

Edit.  During start up, I got a message. bad modprobe:warning ignoring.... .... snd_ens1371

All I had time to write down for it passed on the screen.  >_<

Edit2:  I fixed that problem, I forgot to write blacklist in front of snd_ens1371.  Sound still  doesn't  work though.

Edit3: Disregard that, youtube which I was testing it on didn't work but I can play CDs. *jumps up and down*

wsmoser2004, you're my hero.

---

### Post by Nunana on 2007-10-28
This machine I started with 7.04 (sound was working) then i upgraded to 7.10 sound was not working.When testing my sound I got something like:
*audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open resource for writing.*
Then It was working (I did so much  i can't remember, sorry)
After some updates my sound didn't work any more. Then I found out that the sound was very soft.
I had to open my volume on my Denon amplifier more than 50% to hear a very soft sound (i never open it more than 30% to get sore ears).
My sound card on the motherboard is disabled in the BIOS settings. When I was using ALSA it is recognized as a Ensoniq AudioPCI ens1371. So I did what wsmoser2004 suggested. Now i have the: * audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open resource for writing.* message back.
I'll try to fix it again but I wonder. This sound problem is very annoying. If i can't solve it this week I start again :( then I put Debian on it.

---

