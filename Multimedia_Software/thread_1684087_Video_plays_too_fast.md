---
title: "Video plays too fast"
date: 2011-02-08
forum: Multimedia Software
---

### Post by Leezer on 2011-02-08
Ever since I upgraded to Ubuntu 10.10, I have had trouble playing sound and video.

Videos play too fast for me.  I don't think it's a Flash problem because it occurs no matter what kind of video I play:  Browser-based videos like YouTube, or Totem with .wmv files , .avi files, etc.

Recently I discovered something interesting:  In my sound preferences, if I switch the output from "[SB Live! Value] EMU10k1X Analog Stereo" to "Internal Audio Analog Stereo", then videos play at normal speed, but with no sound.  So, I have a choice between too-fast videos with sound or normal speed videos with no sound.  Obviously, neither of these is acceptable.  Again, I never had this problem until I upgraded to Ubuntu 10.10.

Any help?  I know nothing about this stuff so please explain what to do as if you were talking to a beginner.

---

### Post by brslade on 2011-02-21
I have the very same issue, I've tried lots of solutions from lots of threads. I haven't had any luck yet. Along with the video playback issues i have no sound over hdmi.

---

### Post by jordie9 on 2011-02-23
same problem. With firefox, chromium, opera. used  many flash plugins nothing works. I'm reduced to downloading and viewing later. Plays fast, no sound.

---

### Post by rare HERO on 2012-04-06
I was able to figure it out. Looked at a few different threads and saw that it was either a Flash Plugin issue or a sound issue. 
I tried using the Firefox Add-on Flash-Aid ([https://addons.mozilla.org/en-US/firefox/addon/flash-aid/]("https://addons.mozilla.org/en-US/firefox/addon/flash-aid/")) but that didn't fix my problem.
Then I went into my sound settings and made changes so that the selected hardware would then be correct. (I changed from digital HDMI output to the analog speakers - I don't use the HDMI in my set-up).
Fixed everything. Videos play normal speed with sound.

---

### Post by MikesFrance on 2012-12-12
Hello there!

I have the exact same problem, and no solution working. Thing is, Pavucontrol only shows the HDMI output, which I don't use, and with that videos are running way too fast anyway (any kind of videos, from flash ones to VLC.) So I shut it down, now videos are running well, but still witout any sound, as ubuntu can't see my analog output (or maybe it sees it, I hope so anyway, but I don't have it in my sound options.)

I ran many commands I've found in some various forums and so.

lspci | grep -i audio

```
00:14.2 Audio device: Advanced Micro Devices [AMD] nee ATI SBx00 Azalia (Intel HDA)
01:05.1 Audio device: Advanced Micro Devices [AMD] nee ATI RS780 HDMI Audio [Radeon HD 3000-3300 Series] 
```

sudo lshw | grep -i audio --after-context=12

```
[sudo] password for michael: 
                description: Audio device
                produit: RS780 HDMI Audio [Radeon HD 3000-3300 Series]
                fabriquant: Advanced Micro Devices [AMD] nee ATI
                identifiant matériel: 5.1
                information bus: pci@0000:01:05.1
                version: 00
                bits: 32 bits
                horloge: 33MHz
                fonctionnalités: pm msi bus_master cap_list
                configuration: driver=snd_hda_intel latency=0
                ressources: irq:19 mémoire:feae8000-feaebfff
        *-pci:1
             description: PCI bridge
             produit: RS780 PCI to PCI bridge (PCIE port 3)
--
             description: Audio device
             produit: SBx00 Azalia (Intel HDA)
             fabriquant: Advanced Micro Devices [AMD] nee ATI
             identifiant matériel: 14.2
             information bus: pci@0000:00:14.2
             version: 00
             bits: 64 bits
             horloge: 33MHz
             fonctionnalités: pm cap_list
             configuration: latency=64
             ressources: mémoire:fe8f4000-fe8f7fff
        *-isa
             description: ISA bridge
--
             fonctionnalités: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
     *-scsi:2
          identifiant matériel: 3
          information bus: usb@2:6
          nom logique: scsi6
          fonctionnalités: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             identifiant matériel: 0.0.0
             information bus: scsi@6:0.0.0
             nom logique: /dev/sdb 
```

cat /proc/asound/cards

```
0 [HDMI           ]: HDA-Intel - HDA ATI HDMI
                      HDA ATI HDMI at 0xfeae8000 irq 19 
```

I'm sorry it's in french, I tried in the french forum, but got no answer. Maybe someone can help here...

I'm using Ubuntu 12.10 64 bits. The audio/video outputs are all integretad on an Asus M5A78L-M/USB 3.0 motherboard...

---

