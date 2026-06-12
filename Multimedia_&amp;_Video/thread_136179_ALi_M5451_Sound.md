---
title: "ALi M5451 Sound"
date: 2006-02-25
forum: Multimedia &amp; Video
---

### Post by karld1 on 2006-02-25
Just installed ubuntu for the first time as a clean install on a laptop with ALi M451 Sound.  So far audio is the only thing not working.  I have looked at a number of other threads, including the troubleshooter in the sticky thread that was just posted.

Here's what I know:

When I go to System - Preferences - Sound, no sound cards show up.

Applications - Sound and Video - Volume Control produces:
No volume control elements and/or devices found.

All tests for Multimedia System Selector fail, whether ALSA, ESD, OSS

M5451 PCI AC-Link Controller Audio shows up in the Device Manager

lspci shows:
0000:00:08.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 01)

alsamixer shows:
alsamixer: function snd_ctl_open failed for default: No such file or directory

aplay -l
aplay: device_list:218: no soundcards found...

dmsg:
[4294724.740000] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 10
[4294724.740000] ACPI: PCI Interrupt 0000:00:08.0[A] -> Link [LNKH] -> GSI 10 (level, low) -> IRQ 10
[4294724.740000] PCI: Unable to reserve I/O region #1:100@1000 for device 0000:00:08.0
[4294724.740000] ACPI: PCI interrupt for device 0000:00:08.0 disabled
[4294724.740000] ALI 5451: probe of 0000:00:08.0 failed with error -16

lsmod
snd_ali5451            22596  0
snd_ac97_codec         72188  1 snd_ali5451
snd_pcm_oss            46368  0
snd_mixer_oss          16128  1 snd_pcm_oss
snd_pcm                78344  3 snd_ali5451,snd_ac97_codec,snd_pcm_oss
snd_timer              21764  1 snd_pcm
snd                    48644  6 snd_ali5451,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9184  1 snd
snd_page_alloc         10120  1 snd_pcm


esd:
ALSA lib confmisc.c:560:(snd_determine_driver) could not open control for card 0
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory
ALSA lib confmisc.c:955:(snd_func_refer) error evaluating name
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3948:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2090:(snd_pcm_open_noupdate) Unknown PCM default

---

### Post by DavidW2 on 2006-02-25
I noticed your thread heading and realized we have the same sound chip.  I never had a problem with sound on mine so I haven't had to investigate this but maybe we can compare setups and see what is different.

When I run lspci"
> 0000:00:06.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 02)
rev 01 vs. rev02 (not significant, I think)

dmesg:
> [4294714.090000] shpchp: shpc_init : shpc_cap_offset == 0
[4294714.090000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[4294714.307000] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 10
[4294714.307000] ACPI: PCI Interrupt 0000:00:06.0[A] -> Link [LNKH] -> GSI 10 (level, low) -> IRQ 10
Same IRQ here.

lsmod:
> snd_ali5451            22596  1
snd_ac97_codec         72188  1 snd_ali5451
snd_pcm_oss            46368  0
snd_mixer_oss          16128  1 snd_pcm_oss
snd_pcm                78344  3 snd_ali5451,snd_ac97_codec,snd_pcm_oss
snd_timer              21764  1 snd_pcm
snd                    48644  8 snd_ali5451,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9184  1 snd
snd_page_alloc         10120  1 snd_pcm
Looks almost the same here too.

A few questions for you.

When you go to System -> Preferences-> Multimedia Systems Selector is the Output set to ESD?

When you go to System -> Preferences-> Sound are both boxes checked under the General tab?

What are the modules in your /etc/modules file?

Have you tried rebooting with ACPI turned off?

---

### Post by karld1 on 2006-02-25
[COLOR="Silver"]A few questions for you.

When you go to System -> Preferences-> Multimedia Systems Selector is the Output set to ESD?[/COLOR]
It is now.  I had been trying various different settings.

[COLOR="Silver"]When you go to System -> Preferences-> Sound are both boxes checked under the General tab?[/COLOR]
Yes, they are.  However no sound card is shown in the drop down.

[COLOR="Silver"]What are the modules in your /etc/modules file?[/COLOR]
lp
mousedev
psmouse

[COLOR="Silver"]Have you tried rebooting with ACPI turned off?[/COLOR]
I will do that now.

---

### Post by karld1 on 2006-02-25
> [COLOR="Silver"]Have you tried rebooting with ACPI turned off?[/COLOR]
I will do that now.

I know what you mean about ACPI, I have seen that in other systems.  However this particular laptop's BIOS does not seem to have it as an option.  It's a KDS 6480.

Anyway, I rebooted after switching both source and default sink to ESD.  Still no sound.  When I test it reads "Failed to construct test pipeline for ESD."

Any other suggestions.  Should there be something in my modules file relating to the sound card?

---

### Post by DavidW2 on 2006-02-25
One other thing I wanted to ask.

When you type "dmesg | grep shar" do you get something like this?
[4294669.205000] Serial: 8250/16550 driver $Revision: 1.90 $ 54 ports, IRQ sharing enabled

Showing IRQ sharing is enabled.

As for your /etc/modules file I am wondering if you should have PIIX in there.
Here is my file contents:

lp
mousedev
psmouse
sbp2          <-SCSI Driver
sr_mod       <-CD-ROM driver using driver above in SCSI to IDE bridge
piix            <- PCI IDE/ISA Excellerator (Intel IC)
ide-core
ide-cd
ide-disk
ide-generic

---

### Post by karld1 on 2006-02-25
[4294673.257000] Serial: 8250/16550 driver $Revision: 1.90 $ 54 ports, IRQ sharing enabled

I could be overlooking something really basic here.  I am fairly new to ubuntu and linux.

---

### Post by DavidW2 on 2006-02-25
Sorry, I am not much help.  I am fairly new to Linux myself.  I have experience with UNIX but you don't have to get so involve in the hardware setup as you do with GNU/Linux.  Its all proprietary.  
   I was hoping some one would jump in with the information we've provided and help out.  Looks like everyone is opening a new post for the same/similar problem.  You might want to try the "acpi_irq_isa=7" option in grub that is mentioned in this post.
[http://www.ubuntuforums.org/showthread.php?t=4258&highlight=5451](http://www.ubuntuforums.org/showthread.php?t=4258&highlight=5451)

I can't help thinking that your system just ran out of resources to load the sound module.  Otherwise it looks like everything is setup correctly.  That's why I was wonder if you disable something or move it, that may free up the resources the module needs.

---

### Post by karld1 on 2006-02-25
Thanks for your help.  I tried adding that entry to my grub menu.  I succesfully changed it a few different times with the entry from that thread, as well as some stuff re: APCI that I found elsewhere.  None of the changes made any difference.

Still no sound, 

I agree, it appears to be some type of IRQ conflict or something, but I don't have time to research it any further.

I went with ubuntu because I wanted something I could just install and go.  It worked well for the most part, but not having sound kind of sucks.

---

### Post by DavidW2 on 2006-02-25
I understand.  I played around with Ubuntu for a few weeks to get my screen resolution problem fixed.  It was easier to fix the wireless networking, only because I stumbled on the clue I needed.
I tried out a lot of distros before deciding on Ubuntu.  Usually LiveCDs.  After I installed Ubuntu I found another one that is based on Debian but with Enlightment window manager called Elive ([www.elivecd.com](www.elivecd.com))  I played with it as a live cd for months before I decided to install it on this laptop.  I now remember it was after I lost my sound in Ubuntu I made the switch.  It's pretty slick but it wasn't as easy to work with and doesn't have the community that this one does so I came back.  When I reloaded Ubuntu I made sure to tweak my repostories and do a "apt-get update"  and "apt-get dist-upgrade"  That will pull in any changes that have been made to your installed programs along with any new or updated dependencies.

You might want to try updating as I mentioned above or reloading altogether.  You'll want to make sure you have all the necessary repositories if you update.  I can give you a copy of mine.  Or you can wait for the Final Release of Dapper to come in.  Its very easy to upgrade versions with a CD.  Just boot Ubuntu and put in the CD.  Its pretty much automatic from there.

---

### Post by karld1 on 2006-02-28
Got it!!! I never thought the sound coming out of those tiny laptop speakers could be so beautiful....

This is the kernel line from menu.lst that finally got it working for me...  I needed all 4 of these options to make my sound chip work.  I had tried different ones and different combinations, but never all together.

/vmlinuz-2.6.12-9-386 root=/dev/mapper/Ubuntu-root ro noapic nolapic pci=noacpi acpi=off quiet splash

If you aren't sure how to change these, I think the proper way to do it is:
edit your /boot/grub/menu.lst file

change the # kopt line adding all the options after the ro separated by a space.

then use update-grub command to make the change active and re-boot.

No to find out why I have to manually enable my network card each time I boot up....

---

