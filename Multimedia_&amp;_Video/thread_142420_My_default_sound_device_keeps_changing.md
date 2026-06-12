---
title: "My default sound device keeps changing"
date: 2006-03-10
forum: Multimedia &amp; Video
---

### Post by MrE on 2006-03-10
Hi,

I'm running Breezy and have the following problem:

I've got an AC97 integrated sound card, a SoundBlaster Live and a Logitech USB 350 headset in my PC (which I use only for Skype).

I have set Gnome to use the SoundBlaster Live as my default sound device. It is detected as /dev/dsp and the AC97 is /dev/dsp1. When I connect the Logitech USB headset, it gets detected as /dev/dsp2.

The problem is that sometimes, so not always, when I leave the Logitech headset connected to the PC, upon bootup it get detected as /dev/dsp and becomes the default sound device, forcing the SB Live to /dev/dsp2. This means that I have to go into the Skype settings and change the sound device from /dev/dsp2 to /dev/dsp.

I also  take this headset to work with me, so it often happens that I boot up Ubuntu and connect the headset much later, causing it to be detected as /dev/dsp2 again. This then of course means going back into Skype and changing the sound device to /dev/dsp2 again.

Furthermore, sometimes my default sound device changes to /dev/dsp1 (the AC97).

The most confusing of it all is that the above behaviour is not consistent e.g. there are times where I do leave the headset connected but at bootup is still gets detected as /dev/dsp2 (as opposed to the description above).

Is there a way to force the order in which the devices are detected? I'm getting pretty fed up with never knowing which sound card is which device, and constantly having to switch my default Gnome sound device to the SB Live.

The order I would like to have is 
/dev/dsp   SB Live
/dev/dsp1 AC97
/dev/dsp2 Logitech USB 350 headset (when connected)

I'm pretty sure there must be a simple way to configure this but I'm still quite new to Linux..

Cheers
Emile

---

### Post by hipsis on 2006-03-14
The same problem in dapper

---

### Post by KansasJoe on 2006-03-15
I have the exact same integrated and sb live card....you have to disable the onboard sound in your bios

---

### Post by MrE on 2006-03-21
The problem is that I use my SB Live for when I'm working on the PC, like listening to music or playing games, and the integrated sound card for playback via my hi-fi set for movies.

Surely there must be a way to bind each sound card to their own fixed device?

---

### Post by rcmn on 2006-03-21
i have the exact same problem sblive + nividia onboard.
i need both since share ressources doesn't work for every apps TS/VLC/games/etc...

---

### Post by MrE on 2006-04-21
[QUOTE=rcmn]i have the exact same problem sblive + nividia onboard.
i need both since share ressources doesn't work for every apps TS/VLC/games/etc...[/QUOTE]

Is there absolutely no-one who has come across this problem and knows how to get around it? I've got the feeling it's something quite simple, I just don't have a clue where to look...

I posted this question on the Gnome Forum too [http://gnomesupport.org/forums/viewtopic.php?t=10689]("http://gnomesupport.org/forums/viewtopic.php?t=10689") but even there, no reply...  :confused:

---

### Post by rcmn on 2006-04-21
I noticed some very strange behavior ,and to keep my cards recognize under the same sound device i have to do the following.
1)I plug my webcam after a reboot or boot.
2)i use KDE and i noticed that if i used Kmix to configure dsp1 and leave it selected if i reboot ,dsp1 became dsp. So i make sure that dsp is selected in Kmix when i reboot.

Since i didn't had any bad surprise...

---

### Post by MrE on 2006-05-01
It looks like the detection order can be fixed using udev rules. This article explains how it works: [Persistent Device Naming in User Space]("http://www.linuxjournal.com/article/7316")

I have created three custom rules and so far it seems to work.

Thanks to und0 on the Gnome Support Forum for the link to this article!

Read the original post [here]("http://gnomesupport.org/forums/viewtopic.php?p=51297#51297")

---

### Post by soze on 2006-05-12
Exactly how did you get this working?
Can you send an example of your rules file?

Also, the documentation seems to mention [FONT="Fixedsys"]udevstart,[/FONT] which does not exist in dapper.

Thanks.

---

### Post by MrE on 2006-05-30
I regret to inform you that all I got was a false sense of security :-?
After a couple of reboots, it appeared the problem hadn't gone away at all.

I guess I got the device identifiers wrong but I haven't had time to investigate further yet.

My udev.rules won't be any good as it didn't work but I have attached it so that you can take a look at how I tried it. Perhaps it'll get you in the right direction :)

Here you go!

# There are a number of modifiers that are allowed to be used in some
# of the different fields. They provide the following subsitutions:
#
# %n the "kernel number" of the device.
#    For example, 'sda3' has a "kernel number" of '3'
# %e the smallest number for that name which does not matches an existing node
# %k the kernel name for the device
# %M the kernel major number for the device
# %m the kernel minor number for the device
# %b the bus id for the device
# %c the string returned by the PROGRAM
# %s{filename} the content of a sysfs attribute
# %% the '%' char itself
#

# workaround for devices which do not report media changes
BUS=="ide", KERNEL=="hd[a-z]", SYSFS{removable}=="1", \
  PROGRAM="/etc/udev/scripts/ide-model.sh %k", RESULT=="IOMEGA ZIP *", \
					NAME="%k", OPTIONS+="all_partitions"

# SCSI devices
BUS=="scsi", KERNEL=="sr[0-9]*",	NAME="scd%n", SYMLINK+="sr%n"

# USB devices
BUS=="usb", KERNEL=="hiddev*",		NAME="usb/%k"
BUS=="usb", KERNEL=="auer[0-9]*",	NAME="usb/%k"
BUS=="usb", KERNEL=="legousbtower*",	NAME="usb/%k"
BUS=="usb", KERNEL=="dabusb*",		NAME="usb/%k"
BUS=="usb", KERNEL=="cpad[0-9]*",	NAME="usb/%k"
BUS=="usb", KERNEL=="lp[0-9]*",		NAME="usb/%k"
BUS=="usb", KERNEL=="ttyUSB*", SYSFS{product}=="Palm Handheld*", \
					SYMLINK+="pilot"

# serial devices
KERNEL=="capi",			NAME="capi20", SYMLINK+="isdn/capi20"
KERNEL=="capi[0-9]*",		NAME="capi/%n"

# video devices
KERNEL=="dvb*",			PROGRAM="/etc/udev/scripts/dvb.sh %k", \
				NAME="%c"
KERNEL=="card[0-9]*",		NAME="dri/%k"

# misc devices
KERNEL=="hw_random",		NAME="hwrng"
KERNEL=="tun",			NAME="net/%k"

KERNEL=="cdemu[0-9]*",		NAME="cdemu/%n"
KERNEL=="pktcdvd[0-9]*",	NAME="pktcdvd/%n"
KERNEL=="pktcdvd",		NAME="pktcdvd/control"

KERNEL=="cpu[0-9]*",		NAME="cpu/%n/cpuid"
KERNEL=="msr[0-9]*",		NAME="cpu/%n/msr"
KERNEL=="microcode",		NAME="cpu/microcode"

KERNEL=="umad*",		NAME="infiniband/%k"
KERNEL=="issm*",		NAME="infiniband/%k"

# ALSA devices
KERNEL=="controlC[0-9]*",	NAME="snd/%k"
KERNEL=="hwC[D0-9]*",		NAME="snd/%k"
KERNEL=="pcmC[D0-9cp]*",	NAME="snd/%k"
KERNEL=="midiC[D0-9]*",		NAME="snd/%k"
KERNEL=="timer",		NAME="snd/%k"
KERNEL=="seq",			NAME="snd/%k"

# ieee1394 devices       
KERNEL=="dv1394*",		NAME="dv1394/%n"
KERNEL=="video1394*",		NAME="video1394/%n"

# input devices
KERNEL=="mice",			NAME="input/%k"
KERNEL=="mouse[0-9]*",		NAME="input/%k"
KERNEL=="event[0-9]*",		NAME="input/%k"
KERNEL=="js[0-9]*",		NAME="input/%k", SYMLINK+="%k"
KERNEL=="ts[0-9]*",		NAME="input/%k"
KERNEL=="uinput",		NAME="input/%k"

# Zaptel
KERNEL=="zapctl",		NAME="zap/ctl"
KERNEL=="zaptimer",		NAME="zap/timer"
KERNEL=="zapchannel",		NAME="zap/channel"
KERNEL=="zappseudo",		NAME="zap/pseudo"
KERNEL=="zap[0-9]*",		NAME="zap/%n"

# AOE character devices
SUBSYSTEM=="aoe", KERNEL=="discover",	NAME="etherd/%k"
SUBSYSTEM=="aoe", KERNEL=="err",	NAME="etherd/%k"
SUBSYSTEM=="aoe", KERNEL=="interfaces",	NAME="etherd/%k"

# device mapper creates its own device nodes, so ignore these
KERNEL=="dm-[0-9]*",		OPTIONS+="ignore_device"
KERNEL=="device-mapper",	NAME="mapper/control"

# sound card with PCI bus id 00:0c.0 to be called dsp (SB Live!)
BUS=="pci", ID="00:0c.0", 	NAME="dsp"

# sound card with PCI bus id 00:11.5 to be called dsp (AC97)
BUS=="pci", ID="00:11.5", 	NAME="dsp1"

# sound card with PCI bus id 00:10.1 to be called dsp (Logitech USB Headset)
BUS=="pci", ID="00:0c.0", 	NAME="dsp2"

---

### Post by Gabriele Persia on 2006-06-11
Hi all,

you may try editing /etc/modprobe.d/alsa-base (I solved appending the following lines)

options snd_ens1371 index=0
options snd_via82xx index=1
options snd_usb_audio index=2


apply (reboot) and check /dev/sndstat.

Hope this may be of some help.

Bye
GP

---

### Post by ro314 on 2006-07-12
I had exactely the same problem and it seems I have solved it by following section "Configuring default soundcards / stopping multiple soundcards from switching" from that great guide:
[http://www.ubuntuforums.org/showthread.php?t=205449](http://www.ubuntuforums.org/showthread.php?t=205449)

This forum is great!

ro314

---

### Post by medya on 2007-03-12
I have the same problem , I have an on board sound card and also a TV tuner, it keeps on changin to TV-Tuner's sound card , it is making me angry

---

