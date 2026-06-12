---
title: "SIS 7012 sound distorted in breezy"
date: 2005-10-16
forum: Multimedia &amp; Video
---

### Post by shizow on 2005-10-16
i updated from hoary to breezy
but i have the same problem as before
the sound comes out very distorted

what can i do

---

### Post by kombipom on 2005-10-17
Sorry, I can't answer your question but are you getting sound in all your apps?  I've got the same card (onboard) and I've lost sound in a lot of games inc. Wesnoth but I still have it for Rhythmbox (no distortion).  Did you keep your old config files during the update or install the new ones?

---

### Post by shizow on 2005-10-17
[QUOTE=kombipom]Sorry, I can't answer your question but are you getting sound in all your apps?  I've got the same card (onboard) and I've lost sound in a lot of games inc. Wesnoth but I still have it for Rhythmbox (no distortion).  Did you keep your old config files during the update or install the new ones?[/QUOTE]

i dont know if i kept my config files, but i never had a undistorted sound in hoary or breezy

---

### Post by kombipom on 2005-10-18
Have you tried changing the settings in /etc/asound.conf?

Mine are:
          period_size 2048
          buffer_size 16384
          rate 48000

This seemed to stop 'jumping' in rhythmbox.  Still can't get sound for most stuff though.

---

### Post by mlomker on 2005-10-18
> i updated from hoary to breezy


Clean installs are usually better because updgrades don't overwrite a lot of the configuration files.  I get really odd warbling sounds when I try to use Gstreamer in amaroK (for audio streams) but Xine sounds fine.  I haven't figured that one out yet.  If your program has more than one engine/output option then I'd try another one.

---

### Post by metoo on 2005-10-19
You don't give much information on your system, i386, onboard?

If you never got a clean sound output, this could indicate, that you have an interrupt problem. Try placing any add-in card you may have into another PCI slot on your motherboard or look into you mainboard manual, with which PCI slot your onboard sound shares the interrupt and try to not use this PCI slot then.

Here a SIS 735 onboard sound (i8x0) plays nicely with an old Duron 600.

You can try my settings. Since a short time, alsa uses dmix (a software mixer) as default, if your audio hardware has no hardware mixer. Onboard sound does not have any. With this you can hear a system sound even if you listen to music.

Install mplayer (from marillat).
After install or after first start from console you get a ~/.mplayer directory in your home directory with one file 'config' in it.
Under the first line starting with '#', write another line:
ao=alsa:device=plug=dmix
Create an empty line below this and save.
Now you can change in a directory with some music files and enter:
mplayer music.file
Where music.file is the filename of, you know, the file you want to listen to. If the codecs for the file type are installed, it should play cleanly. That is, if everything is OK with your BIOS/interrupts.

Note: under a fresh install on i386, there is no file '/etc/asound.conf' .
May be it's worth to try without this (rename rather than delete).

If you use KDE and this works or even for the test, you may want to de-activate arts in the KDE control menu (kcontrol in a console).

---

### Post by khcf on 2005-10-20
Hey,

This seems kind of similar to my problem, though I'm using hoary and my sound card is the onboard SI7018. Basically, all sound, be it MP3 or from the CD player, gets distorted when I do, well, basically anything--type, move my mouse, doing things in terminal, etc. I don't know if this is some kind of conflict with my display card because I'm not sure how to check which one is currently in use--there's onboard VGA but I also have a an ATI All-in-wonder 128 in my PCI slot.

I've tried the fix that's given at ubuntuguide.org, no luck.

I've also poked around for sound drivers. The Trident 4Dwave is the one that's currently being used (I think it comes with the 2.6 kernel) and SI's has no linux driver for this sound card, though they do for another one.

Anyhoo. I'm happy to hand over any info if you can give me a hand. Cheers.

---

### Post by shizow on 2005-11-24
[QUOTE=metoo]

You can try my settings. Since a short time, alsa uses dmix (a software mixer) as default, if your audio hardware has no hardware mixer. Onboard sound does not have any. With this you can hear a system sound even if you listen to music.


If you use KDE and this works or even for the test, you may want to de-activate arts in the KDE control menu (kcontrol in a console).[/QUOTE]

where do i get dmix

i have kde

there are no cards in my motherboard
graphic and sound onboard


lspci
0000:00:00.0 Host bridge: Silicon Integrated Systems [SiS] 741/741GX/M741 Host (rev 03)
0000:00:01.0 PCI bridge: Silicon Integrated Systems [SiS]: Unknown device 0003
0000:00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 25)
0000:00:02.1 SMBus: Silicon Integrated Systems [SiS]: Unknown device 0016
0000:00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
0000:00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] Sound Controller (rev a0)
0000:00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
0000:00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
0000:00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
0000:00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)
0000:01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661FX/M661FX/M661MX/741/M741/760/M760 PCI/AGP

cat /proc/asound/cards
0 [SI7012         ]: ICH - SiS SI7012
                     SiS SI7012 with CMI9761 at 0xdc00, irq 18

modprobe -l | grep snd | grep pci
/lib/modules/2.6.12-9-386/kernel/sound/pci/ymfpci/snd-ymfpci.ko
/lib/modules/2.6.12-9-386/kernel/sound/pci/vx222/snd-vx222.ko
/lib/modules/2.6.12-9-386/kernel/sound/pci/trident/snd-trident.ko
/lib/modules/2.6.12-9-386/kernel/sound/pci/trident/snd-trident-synth.ko
/lib/modules/2.6.12-9-386/kernel/sound/pci/snd-via82xx.ko
/lib/modules/2.6.12-9-386/kernel/sound/pci/snd-sonicvibes.ko
/lib/modules/2.6.12-9-386/kernel/sound/pci/snd-rme96.ko
/lib/modules/2.6.12-9-386/kernel/sound/pci/snd-rme32.ko
/lib/modules/2.6.12-9-386/kernel/sound/pci/snd-maestro3.ko
/lib/modules/2.6.12-9-386/kernel/sound/pci/snd-intel8x0m.ko
/lib/modules/2.6.12-9-386/kernel/sound/pci/snd-intel8x0.ko
/lib/modules/2.6.12-9-386/kernel/sound/pci/snd-fm801.ko
/lib/modules/2.6.12-9-386/kernel/sound/pci/snd-es1968.ko
/lib/modules/2.6.12-9-386/kernel/sound/pci/snd-es1938.ko
/lib/modules/2.6.12-9-386/kernel/sound/pci/snd-ens1371.ko
/lib/modules/2.6.12-9-386/kernel/sound/pci/snd-ens1370.ko
/lib/modules/2.6.12-9-386/kernel/sound/pci/snd-cs4281.ko
/lib/modules/2.6.12-9-386/kernel/sound/pci/snd-cmipci.ko
/lib/modules/2.6.12-9-386/kernel/sound/pci/snd-bt87x.ko
/lib/modules/2.6.12-9-386/kernel/sound/pci/snd-azt3328.ko
/lib/modules/2.6.12-9-386/kernel/sound/pci/snd-atiixp.ko
/lib/modules/2.6.12-9-386/kernel/sound/pci/snd-atiixp-modem.ko
/lib/modules/2.6.12-9-386/kernel/sound/pci/snd-via82xx-modem.ko
/lib/modules/2.6.12-9-386/kernel/sound/pci/rme9652/snd-rme9652.ko
/lib/modules/2.6.12-9-386/kernel/sound/pci/rme9652/snd-hdsp.ko
/lib/modules/2.6.12-9-386/kernel/sound/pci/rme9652/snd-hdspm.ko
/lib/modules/2.6.12-9-386/kernel/sound/pci/nm256/snd-nm256.ko
/lib/modules/2.6.12-9-386/kernel/sound/pci/mixart/snd-mixart.ko
/lib/modules/2.6.12-9-386/kernel/sound/pci/snd-als4000.ko
/lib/modules/2.6.12-9-386/kernel/sound/pci/ice1712/snd-ice1724.ko
/lib/modules/2.6.12-9-386/kernel/sound/pci/ice1712/snd-ice1712.ko
/lib/modules/2.6.12-9-386/kernel/sound/pci/ice1712/snd-ice17xx-ak4xxx.ko
/lib/modules/2.6.12-9-386/kernel/sound/pci/hda/snd-hda-intel.ko
/lib/modules/2.6.12-9-386/kernel/sound/pci/hda/snd-hda-codec.ko
/lib/modules/2.6.12-9-386/kernel/sound/pci/emu10k1/snd-emu10k1x.ko
/lib/modules/2.6.12-9-386/kernel/sound/pci/emu10k1/snd-emu10k1.ko
/lib/modules/2.6.12-9-386/kernel/sound/pci/emu10k1/snd-emu10k1-synth.ko
/lib/modules/2.6.12-9-386/kernel/sound/pci/cs46xx/snd-cs46xx.ko
/lib/modules/2.6.12-9-386/kernel/sound/pci/ca0106/snd-ca0106.ko
/lib/modules/2.6.12-9-386/kernel/sound/pci/au88x0/snd-au8830.ko
/lib/modules/2.6.12-9-386/kernel/sound/pci/au88x0/snd-au8820.ko
/lib/modules/2.6.12-9-386/kernel/sound/pci/au88x0/snd-au8810.ko
/lib/modules/2.6.12-9-386/kernel/sound/pci/ali5451/snd-ali5451.ko
/lib/modules/2.6.12-9-386/kernel/sound/pci/ac97/snd-ak4531-codec.ko
/lib/modules/2.6.12-9-386/kernel/sound/pci/ac97/snd-ac97-codec.ko
/lib/modules/2.6.12-9-386/kernel/sound/pci/korg1212/snd-korg1212.ko

---

### Post by shizow on 2005-11-24
[QUOTE=mlomker]Clean installs are usually better because updgrades don't overwrite a lot of the configuration files.  I get really odd warbling sounds when I try to use Gstreamer in amaroK (for audio streams) but Xine sounds fine.  I haven't figured that one out yet.  If your program has more than one engine/output option then I'd try another one.[/QUOTE]

i already had this problem in hoary

---

### Post by shizow on 2005-11-24
[QUOTE=kombipom]Have you tried changing the settings in /etc/asound.conf?

Mine are:
          period_size 2048
          buffer_size 16384
          rate 48000

This seemed to stop 'jumping' in rhythmbox.  Still can't get sound for most stuff though.[/QUOTE]

i dont have this file

---

