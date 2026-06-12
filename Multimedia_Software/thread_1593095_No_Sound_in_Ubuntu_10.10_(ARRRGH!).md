---
title: "No Sound in Ubuntu 10.10 (ARRRGH!)"
date: 2010-10-11
forum: Multimedia Software
---

### Post by Castle_Romeo on 2010-10-11
I was hoping that the release of Ubuntu 10.10 would solve the fatal sound problems I've been having with Ubuntu 10.04 but no luck. C'MON, GUYS, WHAT ARE YA DOING?!?
 
Now what do I do?!?

---

### Post by Sub101 on 2010-10-11
What sound card are you using?

This is the first release where my sound works out of the box.

---

### Post by dominus_sapiens on 2010-10-11
I'm also having issues all of a sudden with sound in 10.10.

My sound card is the one packaged with the Acer Aspire 6920, though I cant seem to find the model number anywhere.

Everything was working perfectly fine yesterday, though something seems to have broken somewhere along the way, similar to as reported here: [http://ubuntuforums.org/showthread.php?t=1572272](http://ubuntuforums.org/showthread.php?t=1572272) .

This: [https://bugs.launchpad.net/system76/+bug/463874](https://bugs.launchpad.net/system76/+bug/463874) sounds like the right sort of thing, and may help others, though does not apply in my case.

I think it might be an issue with the kernel version, as solved here: [http://ubuntuforums.org/showthread.php?t=1316634](http://ubuntuforums.org/showthread.php?t=1316634) , though these instructions are obsolete for 10.10, especially taking into account GRUB 2.

In the mixer on the panel no hardware items are listed, lshw lists no sound devices and ubuntu-bug audio crashes on account of there being nothing in /proc/asound/cards.

This is bad.

I have now run out of ideas, short of rolling everything back to OSS (something I would very much rather not do), and am in a bit of a tight spot, having a mass of work to do already today. Any help would be greatly appreciated!

---

### Post by Yellow Pasque on 2010-10-11
> **dominus_sapiens said:**
> lshw lists no sound devices

It should list your sound card/chip regardless of whether a driver is loaded. Does lspci (or lsusb) show it? If not, make sure your sound card is enabled in the BIOS, and try a Linux LiveCD or other OS to rule out hardware failure.

Oh, and to the OP.. more info please.

---

### Post by MikeyDL on 2010-10-12
I've got the same problem with the 10.10 update.  I did the update then downloaded and testing with a live CD to see if a fresh build would havesudo  fixed the problem.  

You can list your specific sound info in a terminal with the following command:

```
sudo lshw -c sound
```

You mentioned that you didn't get any sound section but allot of info rolls if you don't provide some sort of filter. 

My info is as follows:

  *-multimedia            
       description: Audio device
       product: 82801I (ICH9 Family) HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0
       resources: irq:45 memory:f4700000-f4703fff

waiting to see if there is a fix in the next week otherwise I'll have to roll back to 10.04 :(

---

### Post by PtS on 2010-10-12
Hi.

I've been having this problem since the upgrade to 10.10 as well. I did a regular upgrade using the update manager. My sound system was working well on 10.04. Had some problems with skype though that I solved with an older version of skype and not using pulseaudio. Anyway... Since 10.10 my sound hasn't worked at all. I would prefer to use pulseaudio since that's ubuntu standard, but sound is kind of important...

The problem is that
[LIST]
[*]there is no sound
[*]sound options show "dummy output" as only output system
[*]after some fooling around the sound icon in the panel indicator disappeared
[/LIST]

Some info that might be of use:


```
$ sudo lshw -c sound
  *-multimedia UNCLAIMED  
       description: Audio device
       product: VT1708/A [Azalia HDAC] (VIA High Definition Audio Controller)
       vendor: VIA Technologies, Inc.
       physical id: 1
       bus info: pci@0000:80:01.0
       version: 10
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
```
```
$ cat /proc/asound/cards
--- no soundcards ---
```
```
$ cat /proc/asound/devices 
  2:        : timer
  3:        : sequencer
```

```
$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.23.
```
```
$ uname -a
Linux pontus-desktop 2.6.35-22-generic #34-Ubuntu SMP Sun Oct 10 09:24:00 UTC 2010 i686 GNU/Linux
```
```
$ aplay -l
aplay: device_list:235: no sound card found...
```


I hope this gets the attention it needs since we seem to be a bunch of people with similar problems.

---

### Post by Yellow Pasque on 2010-10-12
PtS: the driver didn't load. dmesg should tell you exactly why it didn't load. You may want to reinstall alsa-base package and your kernel package (linux-image-*something*) to make sure snd-hda-intel.ko hasn't been modified/corrupted.

---

### Post by MikeyDL on 2010-10-12
For me both the Acer main laptop and netbook sound went out.  However, I did get the netbook sound back.  Found that in System - Administration - Users and Groups.  Go to advanced settings and then User Privileges and make sure that "use audio device" is checked.  It wasn't for both my laptops and checking on the netbook fixed that one at least.

For my Acer it finds the device, just won't work.  Put in a bug report and have 13 hits with the same issue so maybe device specific.

---

### Post by MikeyDL on 2010-10-12
Finally got it working!

Had to follow a thread on the bug report for this.  Don't fully understand but somebody put together a deb to fix the issue.  The link to the bug post is as follows:

[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/617647]("https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/617647")

towards the end of the discussion is a link for the deb package.  Installing that fixed my Acer 7736z sound problem.

:)

---

### Post by peroludiarom on 2010-10-13
I think that there is some major problem, with pulse audio..
I make a post about Creative X-fi Xtreme audio - system recognize my sound card, everything looks working, but not... I was google-d for more than 4 hours, and no solution to me. Looks like we have to wait Ubuntu team to Fix this Issue...

---

### Post by PtS on 2010-10-13
> **Temüjin said:**
> PtS: the driver didn't load. dmesg should tell you exactly why it didn't load. You may want to reinstall alsa-base package and your kernel package (linux-image-*something*) to make sure snd-hda-intel.ko hasn't been modified/corrupted.

Well. I ran dmesg and this is as far as I know the part we're looking for.

```
$ dmesg

[...]

[   16.626584] HDA Intel 0000:80:01.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   16.626591] ------------[ cut here ]------------
[   16.626600] WARNING: at /build/buildd/linux-2.6.35/drivers/pci/pci.c:105 pci_ioremap_bar+0x4f/0x60()
[   16.626603] Hardware name: MS-7253
[   16.626605] Modules linked in: snd_hda_intel(+) snd_hda_codec snd_hwdep snd_pcm snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device snd ppdev joydev psmouse soundcore parport_pc amd64_agp serio_raw snd_page_alloc k8temp shpchp i2c_viapro agpgart lp parport hid_logitech ff_memless usbhid hid floppy sata_via via_rhine mii pata_via
[   16.626634] Pid: 487, comm: modprobe Tainted: P            2.6.35-22-generic #34-Ubuntu
[   16.626637] Call Trace:
[   16.626645]  [<c014ac52>] warn_slowpath_common+0x72/0xa0
[   16.626649]  [<c03696bf>] ? pci_ioremap_bar+0x4f/0x60
[   16.626653]  [<c03696bf>] ? pci_ioremap_bar+0x4f/0x60
[   16.626657]  [<c014aca2>] warn_slowpath_null+0x22/0x30
[   16.626660]  [<c03696bf>] pci_ioremap_bar+0x4f/0x60
[   16.626668]  [<f827b847>] azx_create+0x304/0x6bd [snd_hda_intel]
[   16.626677]  [<f80af822>] ? snd_card_create+0x182/0x360 [snd]
[   16.626683]  [<c027100a>] ? sysfs_addrm_finish+0x1a/0xb0
[   16.626688]  [<c05c79e9>] ? mutex_lock+0x19/0x40
[   16.626694]  [<f827bcac>] azx_probe+0xac/0x219 [snd_hda_intel]
[   16.626698]  [<c036b9d3>] local_pci_probe+0x13/0x20
[   16.626702]  [<c036c988>] pci_device_probe+0x68/0x90
[   16.626706]  [<c0400540>] really_probe+0x50/0x150
[   16.626710]  [<c0407bb7>] ? pm_runtime_barrier+0x57/0xb0
[   16.626714]  [<c040067c>] driver_probe_device+0x3c/0x60
[   16.626717]  [<c0400721>] __driver_attach+0x81/0x90
[   16.626720]  [<c03ffb43>] bus_for_each_dev+0x53/0x80
[   16.626724]  [<c040040e>] driver_attach+0x1e/0x20
[   16.626727]  [<c04006a0>] ? __driver_attach+0x0/0x90
[   16.626730]  [<c03ffdd5>] bus_add_driver+0xd5/0x280
[   16.626734]  [<c036c8c0>] ? pci_device_remove+0x0/0x40
[   16.626737]  [<c0400a1a>] driver_register+0x6a/0x130
[   16.626740]  [<c036cbc5>] __pci_register_driver+0x45/0xb0
[   16.626745]  [<f81a2017>] alsa_card_azx_init+0x17/0x19 [snd_hda_intel]
[   16.626749]  [<c0101132>] do_one_initcall+0x32/0x1a0
[   16.626754]  [<f81a2000>] ? alsa_card_azx_init+0x0/0x19 [snd_hda_intel]
[   16.626760]  [<c0180c2b>] sys_init_module+0x9b/0x1e0
[   16.626765]  [<c0218fa2>] ? sys_write+0x42/0x70
[   16.626769]  [<c05c9114>] syscall_call+0x7/0xb
[   16.626772] ---[ end trace 2e6d2d55650526b4 ]---
[   16.626774] hda-intel: ioremap error
[   16.626843] HDA Intel 0000:80:01.0: PCI INT A disabled

[...]

```

Is anyone able to find the problem in there? My knowledge when it comes to kernels and sound systems isn't that great.

I've tried reinstalling alsa-base before (along with every other alsa and pulseaudio package I found) and I believe that the kernel has been updated since the upgrade to maverick, but another re-install won't hurt so I'm gonna give it a shot.

EDIT:
Nope. Re-installation of alsa-base and the kernel didn't do anything. Yes, I rebooted afterwards.
During the re-install, however, I noticed that both linux-image-2.6.35-22-generic and linux-image-2.6.32-25-generic are installed. Should they be?

---

### Post by sunilvennala on 2010-10-14
*-multimedia            
       description: Audio device
       product: RS780 Azalia controller
       vendor: ATI Technologies Inc
       physical id: 5.1
       bus info: pci@0000:01:05.1
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list
       configuration: driver=HDA Intel latency=0
       resources: irq:19 memory:fbde8000-fbdebfff
  *-multimedia
       description: Audio device
       product: SBx00 Azalia (Intel HDA)
       vendor: ATI Technologies Inc
       physical id: 14.2
       bus info: pci@0000:00:14.2
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=HDA Intel latency=64
       resources: irq:16 memory:fbbf4000-fbbf7fff
Pls Help

---

### Post by fatwilly6 on 2010-10-14
> **PtS said:**
> During the re-install, however, I noticed that both linux-image-2.6.35-22-generic and linux-image-2.6.32-25-generic are installed. Should they be?I believe linux-image-2.6.32-25-generic is the newest 10.10 kernel so you should reboot into this from grub screen or else you may be updating software but using old (beta) 10.10 kernels and wondering why nothing has changed. When I have updated from 10.04 -> 10.10 beta then to the 10.10 distibution version all the old kernels remain on the grub screen.It may also be worth removing your soundcard, rebooting without it in, then replacving it & rebooting - this helped me & others struggling with sound issues after an upgrade to 10.10.

---

### Post by PtS on 2010-10-14
> **fatwilly6 said:**
> I believe linux-image-2.6.32-25-generic is the newest 10.10 kernel so you should reboot into this from grub screen or else you may be updating software but using old (beta) 10.10 kernels and wondering why nothing has changed. When I have updated from 10.04 -> 10.10 beta then to the 10.10 distibution version all the old kernels remain on the grub screen.It may also be worth removing your soundcard, rebooting without it in, then replacving it & rebooting - this helped me & others struggling with sound issues after an upgrade to 10.10.

Since I got grub2 and doesn't have another OS on this machine I've always booted without seeing the grub menu. Anyways, I went to the boot menu by holding shift and everything seemed to be fine. 2.6.32-25 was lighted and on top of the list. I went on to delete the old image to be sure. Still no sound.

[COLOR="Red"]However, if I go to the boot menu the system freezes, or at least no key I press does anything at all. I'll look into this as many seem to have problems with grub freezing. EDIT: This is solved. It had to do with the BIOS and my USB keyboard.[/COLOR]

About removing and reinstalling the sound card. It's a bit difficult since it's integrated in the motherboard. Thank's for the tip though.

Any other ideas? Somebody able to read the humbo jumbo that dmesg gave me?

---

### Post by m3ixa on 2010-10-15
Check 

[http://ubuntuforums.org/showthread.php?t=1316634&highlight=no+sound](http://ubuntuforums.org/showthread.php?t=1316634&highlight=no+sound)

It solved sound problem on my Acer 7736z

Mike

---

### Post by jesterthejedi on 2010-10-15
Saved my day with the launchpad fix thx :)

---

### Post by lidex on 2010-10-17
For those of you who lost sound after upgrading to maverick, try removing your old pulse config files first:
Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* ~/.pulse-cookie 
sudo rm /etc/asound.conf
```
**Logout/in.**

No help? 
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by PtS on 2010-10-17
> **lidex said:**
> No help? 
Use the alsa-info-script to provide detailed information.


Allright. I used the script and uploaded the information here: [http://www.alsa-project.org/db/?f=c9fa5f4c841677afe5087ff8f4a608472b3b4a08](http://www.alsa-project.org/db/?f=c9fa5f4c841677afe5087ff8f4a608472b3b4a08)

The script didn't find out what processor I'm using. It's an AMD Athlon 64 X2 Dual Core Processor 4000+, according to the system-monitor.

Also, the line ```
[   16.720127] hda-intel: ioremap error
``` shows during boot-up.

---

### Post by lidex on 2010-10-17
> **PtS said:**
> Allright. I used the script and uploaded the information here: [http://www.alsa-project.org/db/?f=c9fa5f4c841677afe5087ff8f4a608472b3b4a08](http://www.alsa-project.org/db/?f=c9fa5f4c841677afe5087ff8f4a608472b3b4a08)

The script didn't find out what processor I'm using. It's an AMD Athlon 64 X2 Dual Core Processor 4000+, according to the system-monitor.

Also, the line ```
[   16.720127] hda-intel: ioremap error
``` shows during boot-up.

Try re-installing alsa. 
Using a Terminal="Applications->Accessories->Terminal"
```
sudo apt-get update
sudo apt-get upgrade
```
```
sudo apt-get purge linux-sound-base alsa-base alsa-utils

```
```
sudo apt-get install linux-sound-base alsa-base alsa-utils gdm ubuntu-desktop

```
**Reboot.**
**gdm and ubuntu-desktop usually get taken out in the process, so we add them back**

---

### Post by PtS on 2010-10-17
> **lidex said:**
> Try re-installing alsa. 


Did that twice or thrice already but thought, why not try it again. A lot was updated during the update-upgrade steps, pulseaudio was one of the packages.
It didn't help though. Still got the ioremap error, still have no sound.

---

### Post by lidex on 2010-10-17
I'm thinking your kernel is the culprit. Try booting into an earlier version. From there you can try re-installing 2.6.35-22 (kernel and headers) to see if that fixes it. If not, I would just uninstall it and wait for the next one.

---

### Post by PtS on 2010-10-18
Thanks. Re-installing the kernel didn't work, but I've got sound with 2.6.32. I must admit that getting 2.6.32 installed wasn't as easy as I thought it'd be, since it wasn't in the repositories. Anyways, I've got a work-around that practically enables full use of the computer.

Thanks again. :)

---

### Post by shantiq on 2010-10-18
maybe reverting to 2.6.34  might help others       35 has only given me grief not sound but freezes     i would think it worth a shot


[COLOR=#000000][FONT=Times New Roman][FONT=Verdana]
[COLOR=#000000][SIZE=3][COLOR=DarkRed]**[Linux Kernel 2.6.34 installation guide for Ubuntu Linux 10.04]("http://www.ramoonus.nl/2010/05/linux-kernel-2-6-34-installation-guide-for-ubuntu-linux-10-04/") **[/COLOR][/SIZE]

Published on 19 May, 2010 in [Linux]("http://www.ramoonus.nl/category/projects/linux-projects/"). [19 Comments]("http://www.ramoonus.nl/2010/05/linux-kernel-2-6-34-installation-guide-for-ubuntu-linux-10-04/#comments") Tags: [Linux]("http://www.ramoonus.nl/tag/linux/"), [nVIDIA]("http://www.ramoonus.nl/tag/nvidia/"), [Ubuntu]("http://www.ramoonus.nl/tag/ubuntu/"). 

This short walkthrough describes how to get the latest linux kernel working under Ubuntu Linux without having to compile it yourself.
This tutorial should work with the latest version of Ubuntu Linux (10.04 ) and all distributions based on these versions of Ubuntu Linux like Mint.
The included kernel files have been compiled using the generic ubuntu configuration. 
**Note:** nVIDIA ForceWare drivers are automatically installed using DKMS
**Installation Guide**

[LIST=1]
[*]Download [linux-headers-2.6.34-020634_2.6.34-020634_all.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.34-lucid/linux-headers-2.6.34-020634_2.6.34-020634_all.deb")
[*]Download your kernel headers package;
I386: [linux-headers-2.6.34-020634-generic_2.6.34-020634_i386.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.34-lucid/linux-headers-2.6.34-020634-generic_2.6.34-020634_i386.deb")
AMD64: [linux-headers-2.6.34-020634-generic_2.6.34-020634_amd64.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.34-lucid/linux-headers-2.6.34-020634-generic_2.6.34-020634_amd64.deb")
[*]Download your kernel compile;
I386: [linux-image-2.6.34-020634-generic_2.6.34-020634_i386.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.34-lucid/linux-image-2.6.34-020634-generic_2.6.34-020634_i386.deb")
AMD64: [linux-image-2.6.34-020634-generic_2.6.34-020634_amd64.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.34-lucid/linux-image-2.6.34-020634-generic_2.6.34-020634_amd64.deb")
[*]Install the files in the same order (else it won`t work!)
[*]In the terminal run:
sudo update-grub
[*]Reboot and select the kernel from the bootloader menu
[/LIST]
[/COLOR]

which seems to be the best fit for lucid on my machine


if you want to revert or move about install

[COLOR=#000000][/COLOR]
[/FONT][/FONT][/COLOR]```
[COLOR=#000000] sudo aptitude install startupmanager[/COLOR]
```[COLOR=#000000][FONT=Times New Roman][FONT=Verdana]
gives you easy movement ====> default operating system

i ran [COLOR=#000000][/COLOR]
[/FONT][/FONT][/COLOR]```
[COLOR=#000000] sudo update-grub[/COLOR]
```[COLOR=#000000][FONT=Times New Roman][FONT=Verdana]
afterwards to make sure do not know if startupmanager does it automatically

to check what you have running after or before a change


[/FONT][/FONT][/COLOR]```
[COLOR=#000000] uname -r[/COLOR]
```[COLOR=#000000][FONT=Times New Roman][FONT=Verdana]


**also useful (to remove old kernels)**


Open the Synaptic package manager from the System->Administration menu.

Click the “Search” button on the tool bar and search for linux-image-2.

The results should show every available and installed kernel. A green box on the left indicates that the package is installed. The only linux-image you want installed is the latest one. Find the package corresponding to the kernel to you running currently (this is the kernel you found in the terminal window). Make sure you keep that one. Now you can uninstall the old kernels from the list by clicking their boxes and selecting “Mark for Removal”.

Caution! Be careful of what you remove. Ensure that you don’t remove your current kernel, or anything that is not a linux-image. It is possible to break Ubuntu if you remove the wrong kernel.

Click the apply button on the tool bar to complete the changes.

Your computer and Grub menu should now be free of old kernels.[/FONT][/FONT][/COLOR]

---

### Post by PtS on 2010-10-18
> **shantiq said:**
> maybe reverting to 2.6.34  might help others       35 has only given me grief not sound but freezes     i would think it worth a shot

I must say I don't know why I didn't think of installing 2.6.34, but seeing as I had had 2.6.32 before I just installed that one when I was given the advice to downgrade. I decided to install 2.6.34 as well and give it a shot. It didn't work. Apparently there's some problem with both 2.6.35 and 2.6.34. I'll go on running 2.6.32 but I thought you and others would like to know.

---

### Post by happyisland on 2010-10-18
> **lidex said:**
> Try re-installing alsa. 
Using a Terminal="Applications->Accessories->Terminal"
```
sudo apt-get update
sudo apt-get upgrade
```
```
sudo apt-get purge linux-sound-base alsa-base alsa-utils

```
```
sudo apt-get install linux-sound-base alsa-base alsa-utils gdm ubuntu-desktop

```
**Reboot.**
**gdm and ubuntu-desktop usually get taken out in the process, so we add them back**

Reinstalling Alsa as directed here solved my sound problems after upgrade to 10.10. Thanks!

---

### Post by lidex on 2010-10-19
> **PtS said:**
> Thanks. Re-installing the kernel didn't work, but I've got sound with 2.6.32. I must admit that getting 2.6.32 installed wasn't as easy as I thought it'd be, since it wasn't in the repositories. Anyways, I've got a work-around that practically enables full use of the computer.

Thanks again. :)

One reason to always keep at least one known-good kernel installed in addition to newest version.

---

### Post by lidex on 2010-10-19
> **shantiq said:**
> maybe reverting to 2.6.34  might help others       35 has only given me grief not sound but freezes     i would think it worth a shot


[COLOR=#000000][FONT=Times New Roman][FONT=Verdana]
[COLOR=#000000][SIZE=3][COLOR=DarkRed]**[Linux Kernel 2.6.34 installation guide for Ubuntu Linux 10.04]("http://www.ramoonus.nl/2010/05/linux-kernel-2-6-34-installation-guide-for-ubuntu-linux-10-04/") **[/COLOR][/SIZE]



which seems to be the best fit for lucid on my machine



Isn't 2.6.32 default in lucid? Maybe that's why 35 gave you issues. We're actually talking about maverick here, BTW.

---

### Post by jinliew on 2010-10-22
Having the same problem (no sound with creative X Fi Extreme Music) with Ubuntu 10.10 (kernel 2.6.35).

I tried reinstalling alsa to no avail.

I tried booting into my old kernel (2.6.32) from 10.4 but I can't seem to boot it up - I think it's because I have the proprietary Nvidia video drivers installed and they are compiled for 2.6.35.  

Right now, I'd prefer not to muck around with the video drivers (to boot into 2.6.32) in case this causes further problems.

Any other suggestions?  Thanks.

---

### Post by vpsanchez on 2010-10-22
> **lidex said:**
> Try re-installing alsa. 
Using a Terminal="Applications->Accessories->Terminal"
```
sudo apt-get update
sudo apt-get upgrade
```
```
sudo apt-get purge linux-sound-base alsa-base alsa-utils

```
```
sudo apt-get install linux-sound-base alsa-base alsa-utils gdm ubuntu-desktop

```
**Reboot.**
**gdm and ubuntu-desktop usually get taken out in the process, so we add them back**
[B]lidex:
Please accept my sincere gratitude for resolving this sound problem I was experiencing with my Ubuntu upgrade.  Keep up the _good_ work!
vpsanchez[/B]

---

### Post by lidex on 2010-10-22
> **vpsanchez said:**
> [B]lidex:
Please accept my sincere gratitude for resolving this sound problem I was experiencing with my Ubuntu upgrade.  Keep up the _good_ work!
vpsanchez[/B]

Please enjoy!!

---

### Post by Yellow Pasque on 2010-10-22
> **jinliew said:**
> Having the same problem (no sound with creative X Fi Extreme Music) with Ubuntu 10.10 (kernel 2.6.35).
Did the X-Fi work in Lucid with that kernel? Did you run the alsa-info script?

---

### Post by razeshkale on 2010-10-23
Holllla... here is another one...
 Sound Card details:

 *-multimedia            
       description: Multimedia audio controller
       product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller
       vendor: Intel Corporation
       physical id: 1f.5
       bus info: pci@0000:00:1f.5
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=Intel ICH latency=0
       resources: irq:10 ioport:1c00(size=256) ioport:18c0(size=64) memory:e0100c00-e0100dff memory:e0100800-e01008ff


let me know if there any solution// trying to install ALSA right now:popcorn:

---

### Post by oscarmeyer51 on 2010-10-24
Additional info that worked for me.

Adjusting the user under advanced to have access to pulse, then also selecting my user under both groups of pulse and pulse-access.

System/Administration/Users and Groups, then select the Manage Groups. Scroll through the listings to find pulse and pulse-access. Open each one individually and select your (or other) user id's that need to have sound working. After doing that for both, my sound was OK (along with the earlier post on adjusting my user access under the user/advanced settings.

Hope this helps some of you out there!

---

### Post by jinliew on 2010-10-25
> **Temüjin said:**
> Did the X-Fi work in Lucid with that kernel? Did you run the alsa-info script?

I think that kernel is new with Maverick - I only used Lucid very briefly to upgrade to Maverick.  The main version I used previously was Karmic and it worked fine on that until an update several weeks ago (possibly a kernel update??).

I tried booting into an old kernel, however, it would not load up, possibly because I have the proprietary Nvidia drivers installed and compiled under the latest kernel on my machine.  I will try booting into one of the old ones again and see if I have any luck, but I'm reluctant to muck around with my video drivers in case I muck that up too!


My alsa-info script output is linked below:
[http://www.alsa-project.org/db/?f=be...ee71ba639777c3]("http://www.alsa-project.org/db/?f=becf47fa2c1bdbf3a479d81145ee71ba639777c3")

---

### Post by lidex on 2010-10-25
> **jinliew said:**
> I think that kernel is new with Maverick - I only used Lucid very briefly to upgrade to Maverick.  The main version I used previously was Karmic and it worked fine on that until an update several weeks ago (possibly a kernel update??).

I tried booting into an old kernel, however, it would not load up, possibly because I have the proprietary Nvidia drivers installed and compiled under the latest kernel on my machine.  I will try booting into one of the old ones again and see if I have any luck, but I'm reluctant to muck around with my video drivers in case I muck that up too!


My alsa-info script output is linked below:
[http://www.alsa-project.org/db/?f=be...ee71ba639777c3]("http://www.alsa-project.org/db/?f=becf47fa2c1bdbf3a479d81145ee71ba639777c3")

May be defaulting to onboard audio. You can try disabling it in bios or see here:
[http://ubuntuforums.org/showthread.php?t=922860](http://ubuntuforums.org/showthread.php?t=922860)

---

### Post by iuuuuan on 2010-10-26
I had similar issues with my soundcard today.

I did the following :

1.) Reinstall alsa-base and linux-image (optional)
2.) Reboot - sound is still not working (optional)
3.) Find if lspci -v shows the soundcard from terminal :

sudo lscpi -v

.
.
.

00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
	Subsystem: Giga-byte Technology Device a002
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
	Memory at fc100000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	**Kernel modules: snd-hda-intel**

.
.
.

This shows that module **snd-hda-intel** should be loaded

4.) Load the module for soundcard from terminal :

sudo modprobe [soundcard driver] 

for example

sudo modprobe snd-hda-intel

5.) Find if module has loaded from terminal :

lsmod

Search for module [soundcard driver] you have loaded in 4.

6.) Check if sound is working now - It worked for me
7.) Add soundcard module into file /etc/modules (loads module at system startup) and save the file :

gksudo gedit /etc/modules

I have added snd-hda-intel as last line of line.

8.) Reboot
9.) Try if it is working

Don't know if option 1 and 2 are mandatory. If the sound was working and now it is not, you can try by starting with option 3.

Regards,
Ivan

:guitar:

---

### Post by sunilvennala on 2010-10-29
*-multimedia
description: Audio device
product: RS780 Azalia controller
vendor: ATI Technologies Inc
physical id: 5.1
bus info: pci@0000:01:05.1
version: 00
width: 32 bits
clock: 33MHz
capabilities: pm msi bus_master cap_list
configuration: driver=HDA Intel latency=0
resources: irq:19 memory:fbde8000-fbdebfff
*-multimedia
description: Audio device
product: SBx00 Azalia (Intel HDA)
vendor: ATI Technologies Inc
physical id: 14.2
bus info: pci@0000:00:14.2
version: 00
width: 64 bits
clock: 33MHz
capabilities: pm bus_master cap_list
configuration: driver=HDA Intel latency=64
resources: irq:16 memory:fbbf4000-fbbf7fff


00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge 
    Subsystem: ASUSTeK Computer Inc. Device 82f1 
00:01.0 PCI bridge: ASUSTeK Computer Inc. RS880 PCI to PCI bridge (int gfx) 
    Kernel modules: shpchp 
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1) 
    Kernel driver in use: pcieport 
    Kernel modules: shpchp 
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2) 
    Kernel driver in use: pcieport 
    Kernel modules: shpchp 
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode] 
    Subsystem: ASUSTeK Computer Inc. Device 82ef 
    Kernel driver in use: ahci 
    Kernel modules: ahci 
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller 
    Subsystem: ASUSTeK Computer Inc. Device 82ef 
    Kernel driver in use: ohci_hcd 
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller 
    Subsystem: ASUSTeK Computer Inc. Device 82ef 
    Kernel driver in use: ohci_hcd 
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller 
    Subsystem: ASUSTeK Computer Inc. Device 82ef 
    Kernel driver in use: ehci_hcd 
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller 
    Subsystem: ASUSTeK Computer Inc. Device 82ef 
    Kernel driver in use: ohci_hcd 
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller 
    Subsystem: ASUSTeK Computer Inc. Device 82ef 
    Kernel driver in use: ohci_hcd 
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller 
    Subsystem: ASUSTeK Computer Inc. Device 82ef 
    Kernel driver in use: ehci_hcd 
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a) 
    Subsystem: ASUSTeK Computer Inc. Device 82ef 
    Kernel modules: i2c-piix4 
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller 
    Subsystem: ASUSTeK Computer Inc. Device 82ef 
    Kernel driver in use: pata_atiixp 
    Kernel modules: pata_atiixp 
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) 
    Subsystem: ASUSTeK Computer Inc. Device 82fe 
    Kernel driver in use: HDA Intel 
    Kernel modules: snd-hda-intel 
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller 
    Subsystem: ASUSTeK Computer Inc. Device 82ef 
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge 
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller 
    Subsystem: ASUSTeK Computer Inc. Device 82ef 
    Kernel driver in use: ohci_hcd 
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration 
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map 
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller 
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control 
    Kernel modules: k10temp 
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control 
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon HD 3200 Graphics 
    Subsystem: ASUSTeK Computer Inc. Device 82f1 
    Kernel driver in use: fglrx_pci 
    Kernel modules: fglrx, radeon 
01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller 
    Subsystem: ASUSTeK Computer Inc. Device 82f1 
    Kernel driver in use: HDA Intel

Pls Help No Sound...........

---

### Post by iuuuuan on 2010-10-29
> **sunilvennala said:**
> *-multimedia
description: Audio device
product: RS780 Azalia controller
vendor: ATI Technologies Inc
physical id: 5.1
bus info: pci@0000:01:05.1
version: 00
width: 32 bits
clock: 33MHz
capabilities: pm msi bus_master cap_list
configuration: driver=HDA Intel latency=0
resources: irq:19 memory:fbde8000-fbdebfff
*-multimedia
description: Audio device
product: SBx00 Azalia (Intel HDA)
vendor: ATI Technologies Inc
physical id: 14.2
bus info: pci@0000:00:14.2
version: 00
width: 64 bits
clock: 33MHz
capabilities: pm bus_master cap_list
configuration: driver=HDA Intel latency=64
resources: irq:16 memory:fbbf4000-fbbf7fff


00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge 
    Subsystem: ASUSTeK Computer Inc. Device 82f1 
00:01.0 PCI bridge: ASUSTeK Computer Inc. RS880 PCI to PCI bridge (int gfx) 
    Kernel modules: shpchp 
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1) 
    Kernel driver in use: pcieport 
    Kernel modules: shpchp 
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2) 
    Kernel driver in use: pcieport 
    Kernel modules: shpchp 
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode] 
    Subsystem: ASUSTeK Computer Inc. Device 82ef 
    Kernel driver in use: ahci 
    Kernel modules: ahci 
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller 
    Subsystem: ASUSTeK Computer Inc. Device 82ef 
    Kernel driver in use: ohci_hcd 
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller 
    Subsystem: ASUSTeK Computer Inc. Device 82ef 
    Kernel driver in use: ohci_hcd 
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller 
    Subsystem: ASUSTeK Computer Inc. Device 82ef 
    Kernel driver in use: ehci_hcd 
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller 
    Subsystem: ASUSTeK Computer Inc. Device 82ef 
    Kernel driver in use: ohci_hcd 
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller 
    Subsystem: ASUSTeK Computer Inc. Device 82ef 
    Kernel driver in use: ohci_hcd 
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller 
    Subsystem: ASUSTeK Computer Inc. Device 82ef 
    Kernel driver in use: ehci_hcd 
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a) 
    Subsystem: ASUSTeK Computer Inc. Device 82ef 
    Kernel modules: i2c-piix4 
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller 
    Subsystem: ASUSTeK Computer Inc. Device 82ef 
    Kernel driver in use: pata_atiixp 
    Kernel modules: pata_atiixp 
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) 
    Subsystem: ASUSTeK Computer Inc. Device 82fe 
    Kernel driver in use: HDA Intel 
    Kernel modules: snd-hda-intel 
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller 
    Subsystem: ASUSTeK Computer Inc. Device 82ef 
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge 
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller 
    Subsystem: ASUSTeK Computer Inc. Device 82ef 
    Kernel driver in use: ohci_hcd 
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration 
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map 
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller 
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control 
    Kernel modules: k10temp 
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control 
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon HD 3200 Graphics 
    Subsystem: ASUSTeK Computer Inc. Device 82f1 
    Kernel driver in use: fglrx_pci 
    Kernel modules: fglrx, radeon 
01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller 
    Subsystem: ASUSTeK Computer Inc. Device 82f1 
    Kernel driver in use: HDA Intel

Pls Help No Sound...........

Have you tried 
[B]
sudo modprobe snd-hda-intel[/B]

Add **snd-hda-intel** to file /etc/modules and reboot computer.

Regards,
Ivan

---

### Post by mjones1984 on 2010-10-29
I have had the same problem where my sound worked fine after installation of Ubuntu 10.04 but didn't with 10.10.  I have a Realtek ALC883 and use Digital Out for my audio to a reciever which detected no input audio signal (so not just a volume issue).  I adjusted all the volume settings in AlsaMixer as suggested earlier in this thread but that did not work.

However, I fixed the issue by going into Sound Preferences -> Hardware and selecting a different device profile (in my case analog stereo duplex).  Then I adjusted the output volume for it, up and down and ticking and unticking the Mute checkbox.  Suddenly sound started coming out of my headphones and once I changed the hardware profile back to Digial Stereo Output it worked as per usual.

My opinion is that there could  be some uninitialised volume or mute values that can be corrected by simply playing around with the output options, volume levels and mute checkbox.

Hopefully this helps someone who is also having this issue.  I know it sounds a bit too simple but it worked and was a lot easier than reinstalling packages.

---

### Post by odzk on 2010-10-31
i have the same problem, i tried all the steps above but nothing seems to work. im been working with this for almost 4 hours already, I dont have much time left but to switch back to windows xp. Can anyone please help?

Thanks.

This is the result from the script.

[http://www.alsa-project.org/db/?f=3344d7d4da79f09aa51c5194624a046c17644c11](http://www.alsa-project.org/db/?f=3344d7d4da79f09aa51c5194624a046c17644c11)

---

### Post by lidex on 2010-10-31
> **odzk said:**
> i have the same problem, i tried all the steps above but nothing seems to work. im been working with this for almost 4 hours already, I dont have much time left but to switch back to windows xp. Can anyone please help?

Thanks.

This is the result from the script.

[http://www.alsa-project.org/db/?f=3344d7d4da79f09aa51c5194624a046c17644c11](http://www.alsa-project.org/db/?f=3344d7d4da79f09aa51c5194624a046c17644c11)

What is the output of this command:
```
cat /etc/modprobe.d/alsa-base.conf
```

---

### Post by Dudutzu on 2010-10-31
> **lidex said:**
> Try re-installing alsa. 
Using a Terminal="Applications->Accessories->Terminal"
```
sudo apt-get update
sudo apt-get upgrade
```
```
sudo apt-get purge linux-sound-base alsa-base alsa-utils

```
```
sudo apt-get install linux-sound-base alsa-base alsa-utils gdm ubuntu-desktop

```
**Reboot.**
**gdm and ubuntu-desktop usually get taken out in the process, so we add them back**


Thx , reinstalling solved the problem for me.

---

### Post by odzk on 2010-10-31
Nevermind, I have it resolved, its a kernel problem. Im using lucid kernel now and its working got it from here.

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32.25-lucid/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32.25-lucid/)

---

### Post by gfajdi on 2010-10-31
Well, I officially give up

I have the same problem in maverick: no sound, but kernel modules are loaded.

I have tried reinstalling Alsa.
I tried custom-compiled kernel (latest git as of Nov 1 00:00 GMT+1
I tried 2.6.32 from the following ppa 
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32.25-lucid/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32.25-lucid/)
I added myself to groups sound, pulse and pulse-access. Nothing helps.

Here are my sound card specs:

[http://www.alsa-project.org/db/?f=0d676d7bf058e25660f97c4cd0269b99377fa03a](http://www.alsa-project.org/db/?f=0d676d7bf058e25660f97c4cd0269b99377fa03a)

Hope anyone can help :-)

---

### Post by gfajdi on 2010-11-01
I also tried the following:

apt-get remove pulse-audio
rm -rf ~/.pulse*
apt-get pulse-audio ubuntu-desktop
reboot


No dice.
Couriously enough sound does work on the original 10.10 liveCD.

---

### Post by PMahoney on 2010-11-01
I had no sound either after recently upgrading to 10.10 netbook...I tried all of the suggestions provided throughout the thread and all to no avail. After playing with the settings in Sound Preferences as suggested by another poster, I turned off the amplifier using the drop-down connector menu in the Output Tab within 'Sound Preferences'.  The sound is now playing, but have yet to 'quality' test with better speakers...
P

---

### Post by odzk on 2010-11-02
> **gfajdi said:**
> Well, I officially give up

I have the same problem in maverick: no sound, but kernel modules are loaded.

I have tried reinstalling Alsa.
I tried custom-compiled kernel (latest git as of Nov 1 00:00 GMT+1
I tried 2.6.32 from the following ppa 
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32.25-lucid/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32.25-lucid/)
I added myself to groups sound, pulse and pulse-access. Nothing helps.

Here are my sound card specs:

[http://www.alsa-project.org/db/?f=0d676d7bf058e25660f97c4cd0269b99377fa03a](http://www.alsa-project.org/db/?f=0d676d7bf058e25660f97c4cd0269b99377fa03a)

Hope anyone can help :-)

Have this problem started after the upgrade or just newly installed 10.10? Took me almost a day to figure out my problem also, i tried 6 kernels to be exact, 5 of them didnt work, only this one works..

---

### Post by odzk on 2010-11-02
looking at the results from 
[http://www.alsa-project.org/db/?f=0d676d7bf058e25660f97c4cd0269b99377fa03a](http://www.alsa-project.org/db/?f=0d676d7bf058e25660f97c4cd0269b99377fa03a)

looks like your card was detected. have you tried adding your card to
/etc/modprobe.d/alsa-base.conf

options snd-hda-intel probe_mask=1 model=(your model)

see here

check this

[http://ubuntuforums.org/showthread.php?t=1316634&highlight=no+sound](http://ubuntuforums.org/showthread.php?t=1316634&highlight=no+sound)

---

### Post by lidex on 2010-11-02
> **gfajdi said:**
> I also tried the following:

apt-get remove pulse-audio
rm -rf ~/.pulse*
apt-get pulse-audio ubuntu-desktop
reboot


No dice.
Couriously enough sound does work on the original 10.10 liveCD.

This, perhaps:
> Audigy
If your Creative Audigy card is not giving you any sound, make sure the analog/digital check box in your sound mixer is unchecked. Updates seem to reset this switch regularly so keep this in mind.

---

### Post by burymeinblack907 on 2010-11-03
I have had the same problem with an Audigy SE and tried all the suggestions in the thread but still had no audio whatsoever.  Then I tried 

```
sudo alsa-utils restart ca0106
```and it worked for me, but I have to do it every new session. This blows.

---

### Post by bfromcolo on 2010-11-07
I did a fresh install of 10.10 with an ISO I downloaded today and ran updates, but no sound, I have tried a number of the things in this thread without any luck.  System dual boots to XP and sound is fine there.  Note I am trying to use the on board sound, not the HDMI built into the video card.  Any help would be appreciated.

Thanks


ALSA Information Script v 0.4.59
--------------------------------

This script visits the following commands/files to collect diagnostic
information about your ALSA installation and sound related hardware.

  dmesg
  lspci
  lsmod
  aplay
  amixer
  alsactl
  /proc/asound/
  /sys/class/sound/
  ~/.asoundrc (etc.)

See 'alsa-info.sh --help' for command line options.

/sbin/alsactl: get_control:239: Cannot read control info '2,0,0,Front Playback Volume,0': Invalid argument
cat: /tmp/alsa-info.KmM1rFJbUa/alsactl.tmp: No such file or directory
Automatically upload ALSA information to [www.alsa-project.org?](www.alsa-project.org?) [y/N] : y
Uploading information to [www.alsa-project.org](www.alsa-project.org) ...  Done!

Your ALSA information is located at [http://www.alsa-project.org/db/?f=aecd47734fd5d34c5e17b13e22422d9b72e314eb](http://www.alsa-project.org/db/?f=aecd47734fd5d34c5e17b13e22422d9b72e314eb)

---

### Post by lidex on 2010-11-08
> **bfromcolo said:**
> I did a fresh install of 10.10 with an ISO I downloaded today and ran updates, but no sound, I have tried a number of the things in this thread without any luck.  System dual boots to XP and sound is fine there.  Note I am trying to use the on board sound, not the HDMI built into the video card.  Any help would be appreciated.

Thanks


ALSA Information Script v 0.4.59
--------------------------------

This script visits the following commands/files to collect diagnostic
information about your ALSA installation and sound related hardware.

  dmesg
  lspci
  lsmod
  aplay
  amixer
  alsactl
  /proc/asound/
  /sys/class/sound/
  ~/.asoundrc (etc.)

See 'alsa-info.sh --help' for command line options.

/sbin/alsactl: get_control:239: Cannot read control info '2,0,0,Front Playback Volume,0': Invalid argument
cat: /tmp/alsa-info.KmM1rFJbUa/alsactl.tmp: No such file or directory
Automatically upload ALSA information to [www.alsa-project.org?](www.alsa-project.org?) [y/N] : y
Uploading information to [www.alsa-project.org](www.alsa-project.org) ...  Done!

Your ALSA information is located at [http://www.alsa-project.org/db/?f=aecd47734fd5d34c5e17b13e22422d9b72e314eb](http://www.alsa-project.org/db/?f=aecd47734fd5d34c5e17b13e22422d9b72e314eb)

Another gigabyte board. We need you to submit a bug report please. Start here. Try running this command in a terminal for 10.04 or later:
```
ubuntu-bug audio
```
Reference the Ubuntu-Bug Audio link in my sig.

After that try using a different kernel.

---

### Post by bfromcolo on 2010-11-08
> **lidex said:**
> Another gigabyte board. We need you to submit a bug report please. Start here. Try running this command in a terminal for 10.04 or later:
```
ubuntu-bug audio
```
Reference the Ubuntu-Bug Audio link in my sig.

After that try using a different kernel.

I have submitted the bug report.  Is there an easy reference somewhere for how to replace just the kernel with an older one?  I am running 2.6.35-22-generic currently.

---

### Post by lidex on 2010-11-10
If you haven't removed them, the old ones should still be there and can be selected in the grub screen. I'm seeing some issues with your kernel version (2.6.35-22) and xx-23 is out so an update may be useful as well. You may need to enable the proposed and/or backports repos though.

Can you post a link to that bug report?

---

### Post by bfromcolo on 2010-11-10
> **lidex said:**
> If you haven't removed them, the old ones should still be there and can be selected in the grub screen. I'm seeing some issues with your kernel version (2.6.35-22) and xx-23 is out so an update may be useful as well. You may need to enable the proposed and/or backports repos though.

Can you post a link to that bug report?

This was a fresh install, so I think it only has one kernel.  I can try an update.

Bug report link is below.

[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/672568](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/672568)

Thanks

---

### Post by smurfgod on 2010-11-15
> **MikeyDL said:**
> Finally got it working!

Had to follow a thread on the bug report for this.  Don't fully understand but somebody put together a deb to fix the issue.  The link to the bug post is as follows:

[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/617647]("https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/617647")

towards the end of the discussion is a link for the deb package.  Installing that fixed my Acer 7736z sound problem.

:)

Worked for me. Added the PPS thru command line, rebooted and I've got working sound.

*-multimedia            
       description: Multimedia audio controller
       product: CK804 AC'97 Audio Controller
       vendor: nVidia Corporation
       physical id: b
       bus info: pci@0000:00:04.0
       version: a2
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list
       configuration: driver=Intel ICH latency=0 maxlatency=5 mingnt=2
       resources: irq:22 ioport:f000(size=256) ioport:ec00(size=256) memory:fe02d000-fe02dfff


Thanks man,

---

### Post by bfromcolo on 2010-12-03
Just an update.  My issue has been resolved in the latest ALSA driver modules.  Details on where to get the fixes are in the bug report.

[https://bugs.launchpad.net/ubuntu/+s...er/+bug/672568](https://bugs.launchpad.net/ubuntu/+s...er/+bug/672568)

---

### Post by gloscherrybomb on 2010-12-09
> **PtS said:**
> Hi.

I've been having this problem since the upgrade to 10.10 as well. I did a regular upgrade using the update manager. My sound system was working well on 10.04. Had some problems with skype though that I solved with an older version of skype and not using pulseaudio. Anyway... Since 10.10 my sound hasn't worked at all. I would prefer to use pulseaudio since that's ubuntu standard, but sound is kind of important...

The problem is that
[LIST]
[*]there is no sound
[*]sound options show "dummy output" as only output system
[*]after some fooling around the sound icon in the panel indicator disappeared
[/LIST]

Some info that might be of use:


```
$ sudo lshw -c sound
  *-multimedia UNCLAIMED  
       description: Audio device
       product: VT1708/A [Azalia HDAC] (VIA High Definition Audio Controller)
       vendor: VIA Technologies, Inc.
       physical id: 1
       bus info: pci@0000:80:01.0
       version: 10
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
```
```
$ cat /proc/asound/cards
--- no soundcards ---
```
```
$ cat /proc/asound/devices 
  2:        : timer
  3:        : sequencer
```

```
$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.23.
```
```
$ uname -a
Linux pontus-desktop 2.6.35-22-generic #34-Ubuntu SMP Sun Oct 10 09:24:00 UTC 2010 i686 GNU/Linux
```
```
$ aplay -l
aplay: device_list:235: no sound card found...
```


I hope this gets the attention it needs since we seem to be a bunch of people with similar problems.

I have the exact same card and problem as this guy. Unfortunately I cant rollback to .22 as I only have .24 and .23. 

Frustrating! Tried everything in every guide. Positive its a kernel bug.

---

### Post by lidex on 2010-12-12
@gloscherrybomb
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by gloscherrybomb on 2010-12-12
> **lidex said:**
> @gloscherrybomb
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]


Here you go: (Just for reference Im pretty confident with the terminal and fixes for these sort of probs on Ubuntu as I've overcome many similar problems in the last 6 or so year, but this one has perplexed me!

```

!!################################
!!ALSA Information Script v 0.4.59
!!################################

!!Script ran on: Mon Dec 13 00:06:49 UTC 2010


!!Linux Distribution
!!------------------

Ubuntu 10.10 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 10.10"


!!DMI Information
!!---------------

Manufacturer:      MICRO-STAR INTERNATIONAL CO., LTD
Product Name:      MS-7253


!!Kernel Information
!!------------------

Kernel release:    2.6.35-24-generic
Operating System:  GNU/Linux
Architecture:      i686
Processor:         unknown
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     1.0.23
Library version:    1.0.23
Utilities version:  1.0.23


!!Loaded ALSA modules
!!-------------------



!!Sound Servers on this system
!!----------------------------

Pulseaudio:
      Installed - Yes (/usr/bin/pulseaudio)
      Running - Yes

ESound Daemon:
      Installed - Yes (/usr/bin/esd)
      Running - No


!!Soundcards recognised by ALSA
!!-----------------------------

--- no soundcards ---


!!PCI Soundcards installed in the system
!!--------------------------------------

80:01.0 Audio device: VIA Technologies, Inc. VT1708/A [Azalia HDAC] (VIA High Definition Audio Controller) (rev 10)


!!Advanced information - PCI Vendor/Device/Susbsystem ID's
!!--------------------------------------------------------

80:01.0 0403: 1106:3288 (rev 10)
	Subsystem: 1462:7253


!!Modprobe options (Sound related)
!!--------------------------------

snd-atiixp-modem: index=-2
snd-intel8x0m: index=-2
snd-via82xx-modem: index=-2
snd-usb-audio: index=-2
snd-usb-caiaq: index=-2
snd-usb-ua101: index=-2
snd-usb-us122l: index=-2
snd-usb-usx2y: index=-2
snd-cmipci: mpu_port=0x330 fm_port=0x388
snd-pcsp: index=-2
snd-usb-audio: index=-2
snd-hda-intel: probe_mask=1 model=auto


!!Loaded sound module options
!!--------------------------


!!ALSA Device nodes
!!-----------------

crw-rw----  1 root audio 116, 3 Dec 12 12:37 /dev/snd/seq
crw-rw----  1 root audio 116, 2 Dec 12 12:37 /dev/snd/timer


!!Aplay/Arecord output
!!------------

APLAY

aplay: device_list:235: no soundcards found...

ARECORD

arecord: device_list:235: no soundcards found...

!!Amixer output
!!-------------


!!Alsactl output
!!-------------

--startcollapse--
--endcollapse--


!!All Loaded Modules
!!------------------

Module
aes_i586
aes_generic
binfmt_misc
arc4
lm63
snd_hda_intel
snd_hda_codec
snd_hwdep
radeon
snd_pcm
zd1211rw
snd_seq_midi
snd_rawmidi
mac80211
snd_seq_midi_event
ttm
snd_seq
drm_kms_helper
ppdev
cfg80211
snd_timer
snd_seq_device
drm
joydev
parport_pc
psmouse
i2c_viapro
k8temp
serio_raw
snd
amd64_agp
shpchp
i2c_algo_bit
agpgart
soundcore
snd_page_alloc
lp
parport
usbhid
hid
floppy
pata_via
via_rhine
sata_via
mii


!!ALSA/HDA dmesg
!!------------------

[   14.298983]   alloc kstat_irqs on node -1
[   14.298994] HDA Intel 0000:80:01.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   14.299001] ------------[ cut here ]------------
--
[   14.299015] Hardware name: MS-7253
[   14.299017] Modules linked in: snd_hda_intel( ) snd_hda_codec snd_hwdep radeon( ) snd_pcm zd1211rw( ) snd_seq_midi snd_rawmidi mac80211 snd_seq_midi_event ttm snd_seq drm_kms_helper ppdev cfg80211 snd_timer snd_seq_device drm joydev parport_pc psmouse i2c_viapro k8temp serio_raw snd amd64_agp shpchp i2c_algo_bit agpgart soundcore snd_page_alloc lp parport usbhid hid floppy pata_via via_rhine sata_via mii
[   14.299052] Pid: 480, comm: modprobe Not tainted 2.6.35-24-generic #42-Ubuntu
--
[   14.299080]  [<c0369ccf>] pci_ioremap_bar 0x4f/0x60
[   14.299088]  [<f814c847>] azx_create 0x304/0x6bd [snd_hda_intel]
[   14.299100]  [<f822b822>] ? snd_card_create 0x182/0x360 [snd]
--
[   14.299112]  [<c05c8599>] ? mutex_lock 0x19/0x40
[   14.299118]  [<f814ccac>] azx_probe 0xac/0x219 [snd_hda_intel]
[   14.299123]  [<c036bfe3>] local_pci_probe 0x13/0x20
--
[   14.299166]  [<c036d1d5>] __pci_register_driver 0x45/0xb0
[   14.299171]  [<f805d017>] alsa_card_azx_init 0x17/0x19 [snd_hda_intel]
[   14.299175]  [<c0101132>] do_one_initcall 0x32/0x1a0
[   14.299180]  [<f805d000>] ? alsa_card_azx_init 0x0/0x19 [snd_hda_intel]
[   14.299187]  [<c0180d1b>] sys_init_module 0x9b/0x1e0
--
[   14.299199] ---[ end trace 95ae7db10b1135bd ]---
[   14.299201] hda-intel: ioremap error
[   14.299263] HDA Intel 0000:80:01.0: PCI INT A disabled
[   14.339322] [drm] Possible lm63 thermal controller at 0x4c


```

---

### Post by lidex on 2010-12-12
Is this a homegrown system? If not, what is make/model? Are you using a PCI card with internal disabled?
Can you post this info please:
```
sudo lshw -C multimedia
```

---

### Post by fly2k on 2010-12-13
same problem here :(
just installed fresh ubuntu 10.10 from CD.
I have all "visual" sound features: I see the right device at sound preferences, I able to set volume, mute/unmute, select output, etc. I see volume control in mplayer/rhytmbox and able to adjust it. All fine, just no sound :(

I added the user to audio group via System->Administration->User and Groups.

```

root@fly-ws:~# lshw -C multimedia
  *-multimedia            
       description: Multimedia audio controller
       product: VT1720/24 [Envy24PT/HT] PCI Multi-Channel Audio Controller
       vendor: VIA Technologies Inc.
       physical id: 6
       bus info: pci@0000:05:06.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=ICE1724 latency=32
       resources: irq:16 ioport:8000(size=32) ioport:8400(size=128)

``````

upload=true&script=true&cardinfo=
!!################################
!!ALSA Information Script v 0.4.59
!!################################

!!Script ran on: Mon Dec 13 12:27:23 UTC 2010


!!Linux Distribution
!!------------------

Ubuntu 10.10 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 10.10"


!!DMI Information
!!---------------

Manufacturer:      System manufacturer
Product Name:      System Product Name


!!Kernel Information
!!------------------

Kernel release:    2.6.35-23-generic
Operating System:  GNU/Linux
Architecture:      i686
Processor:         unknown
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     1.0.23
Library version:    1.0.23
Utilities version:  1.0.23


!!Loaded ALSA modules
!!-------------------

snd_ice1724


!!Sound Servers on this system
!!----------------------------

Pulseaudio:
      Installed - Yes (/usr/bin/pulseaudio)
      Running - Yes

ESound Daemon:
      Installed - Yes (/usr/bin/esd)
      Running - No


!!Soundcards recognised by ALSA
!!-----------------------------

 0 [Revolution51   ]: ICE1724 - M Audio Revolution-5.1
                      M Audio Revolution-5.1 at 0x8000, irq 16


!!PCI Soundcards installed in the system
!!--------------------------------------

05:06.0 Multimedia audio controller: VIA Technologies Inc. VT1720/24 [Envy24PT/HT] PCI Multi-Channel Audio Controller (rev 01)


!!Advanced information - PCI Vendor/Device/Susbsystem ID's
!!--------------------------------------------------------

05:06.0 0401: 1412:1724 (rev 01)
    Subsystem: 1412:3631


!!Modprobe options (Sound related)
!!--------------------------------

snd-atiixp-modem: index=-2
snd-intel8x0m: index=-2
snd-via82xx-modem: index=-2
snd-usb-audio: index=-2
snd-usb-caiaq: index=-2
snd-usb-ua101: index=-2
snd-usb-us122l: index=-2
snd-usb-usx2y: index=-2
snd-cmipci: mpu_port=0x330 fm_port=0x388
snd-pcsp: index=-2
snd-usb-audio: index=-2


!!Loaded sound module options
!!--------------------------

!!Module: snd_ice1724
    enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
    id : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
    index : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
    model : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)


!!ALSA Device nodes
!!-----------------

crw-rw----+ 1 root audio 116, 8 Dec 13 15:22 /dev/snd/controlC0
crw-rw----+ 1 root audio 116, 7 Dec 13 15:23 /dev/snd/pcmC0D0c
crw-rw----+ 1 root audio 116, 6 Dec 13 15:23 /dev/snd/pcmC0D0p
crw-rw----+ 1 root audio 116, 5 Dec 13 15:23 /dev/snd/pcmC0D1p
crw-rw----+ 1 root audio 116, 4 Dec 13 15:22 /dev/snd/pcmC0D2p
crw-rw----+ 1 root audio 116, 3 Dec 13 15:22 /dev/snd/seq
crw-rw----+ 1 root audio 116, 2 Dec 13 15:22 /dev/snd/timer

/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root  60 Dec 13 15:22 .
drwxr-xr-x 3 root root 200 Dec 13 15:22 ..
lrwxrwxrwx 1 root root  12 Dec 13 15:22 pci-0000:05:06.0 -> ../controlC0


!!Aplay/Arecord output
!!------------

APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: Revolution51 [M Audio Revolution-5.1], device 0: ICE1724 [ICE1724]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Revolution51 [M Audio Revolution-5.1], device 1: ICE1724 IEC958 [ICE1724 IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Revolution51 [M Audio Revolution-5.1], device 2: ICE1724 Surrounds [ICE1724 Surround PCM]
  Subdevices: 3/3
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2

ARECORD

**** List of CAPTURE Hardware Devices ****
card 0: Revolution51 [M Audio Revolution-5.1], device 0: ICE1724 [ICE1724]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

!!Amixer output
!!-------------

!!-------Mixer controls for card 0 [Revolution51]

Card hw:0 'Revolution51'/'M Audio Revolution-5.1 at 0x8000, irq 16'
  Mixer name    : 'ICE1724 - multitrack'
  Components    : ''
  Controls      : 32
  Simple ctrls  : 25
Simple mixer control 'PCM',0
  Capabilities: pvolume cvolume cswitch cswitch-joined penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 127 Capture 0 - 152
  Front Left: Playback 127 [100%] [0.00dB] Capture 122 [80%] [-2.50dB] [on]
  Front Right: Playback 127 [100%] [0.00dB] Capture 122 [80%] [-2.50dB] [on]
Simple mixer control 'PCM Center',0
  Capabilities: pvolume pvolume-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 127
  Mono: Playback 0 [0%] [-99999.99dB]
Simple mixer control 'PCM Headphone',0
  Capabilities: volume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 127
  Front Left: 0 [0%] [-99999.99dB]
  Front Right: 0 [0%] [-99999.99dB]
Simple mixer control 'PCM LFE',0
  Capabilities: pvolume pvolume-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 127
  Mono: Playback 0 [0%] [-99999.99dB]
Simple mixer control 'PCM Rear',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 127
  Mono:
  Front Left: Playback 0 [0%] [-99999.99dB]
  Front Right: Playback 0 [0%] [-99999.99dB]
Simple mixer control 'Line Loopback',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 79
  Mono:
  Front Left: Playback 79 [100%] [0.00dB]
  Front Right: Playback 79 [100%] [0.00dB]
Simple mixer control 'CD Loopback',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 79
  Mono:
  Front Left: Playback 79 [100%] [0.00dB]
  Front Right: Playback 79 [100%] [0.00dB]
Simple mixer control 'Mic Loopback',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 79
  Mono:
  Front Left: Playback 79 [100%] [0.00dB]
  Front Right: Playback 79 [100%] [0.00dB]
Simple mixer control 'IEC958',0
  Capabilities: penum
  Items: 'PCM Out' 'H/W In 0' 'H/W In 1' 'IEC958 In L' 'IEC958 In R'
  Item0: 'PCM Out'
Simple mixer control 'IEC958 Output',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'IEC958',1
  Capabilities: penum
  Items: 'PCM Out' 'H/W In 0' 'H/W In 1' 'IEC958 In L' 'IEC958 In R'
  Item0: 'PCM Out'
Simple mixer control 'Capture Channel',0
  Capabilities: enum
  Items: 'Mic' 'Line' 'CD'
  Item0: 'Mic'
Simple mixer control 'Deemphasis',0
  Capabilities: enum
  Items: '44.1kHz' 'Off' '48kHz' '32kHz'
  Item0: 'Off'
Simple mixer control 'H/W',0
  Capabilities: penum
  Items: 'PCM Out' 'H/W In 0' 'H/W In 1' 'IEC958 In L' 'IEC958 In R'
  Item0: 'PCM Out'
Simple mixer control 'H/W',1
  Capabilities: penum
  Items: 'PCM Out' 'H/W In 0' 'H/W In 1' 'IEC958 In L' 'IEC958 In R'
  Item0: 'PCM Out'
Simple mixer control 'H/W',2
  Capabilities: penum
  Items: 'PCM Out' 'H/W In 0' 'H/W In 1' 'IEC958 In L' 'IEC958 In R'
  Item0: 'PCM Out'
Simple mixer control 'H/W',3
  Capabilities: penum
  Items: 'PCM Out' 'H/W In 0' 'H/W In 1' 'IEC958 In L' 'IEC958 In R'
  Item0: 'PCM Out'
Simple mixer control 'H/W',4
  Capabilities: penum
  Items: 'PCM Out' 'H/W In 0' 'H/W In 1' 'IEC958 In L' 'IEC958 In R'
  Item0: 'PCM Out'
Simple mixer control 'H/W',5
  Capabilities: penum
  Items: 'PCM Out' 'H/W In 0' 'H/W In 1' 'IEC958 In L' 'IEC958 In R'
  Item0: 'PCM Out'
Simple mixer control 'H/W',6
  Capabilities: penum
  Items: 'PCM Out' 'H/W In 0' 'H/W In 1' 'IEC958 In L' 'IEC958 In R'
  Item0: 'PCM Out'
Simple mixer control 'H/W',7
  Capabilities: penum
  Items: 'PCM Out' 'H/W In 0' 'H/W In 1' 'IEC958 In L' 'IEC958 In R'
  Item0: 'PCM Out'
Simple mixer control 'Loopback',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Multi Track Internal Clock',0
  Capabilities: enum
  Items: '8000' '9600' '11025' '12000' '16000' '22050' '24000' '32000' '44100' '48000' '64000' '88200' '96000' '176400' '192000' 'IEC958 In'
  Item0: '44100'
Simple mixer control 'Multi Track Rate Locking',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Multi Track Rate Reset',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]


!!Alsactl output
!!-------------

--startcollapse--
state.Revolution51 {
    control.1 {
        comment.access read
        comment.type BYTES
        comment.count 52
        iface CARD
        name 'ICE1724 EEPROM'
        value '3631141213024280f8c1fa004005ffbff0000000000000000000000000000000000000000000000005ffbf00f0000000fa004000'
    }
    control.2 {
        comment.access 'read write'
        comment.type ENUMERATED
        comment.count 1
        comment.item.0 '8000'
        comment.item.1 '9600'
        comment.item.2 '11025'
        comment.item.3 '12000'
        comment.item.4 '16000'
        comment.item.5 '22050'
        comment.item.6 '24000'
        comment.item.7 '32000'
        comment.item.8 '44100'
        comment.item.9 '48000'
        comment.item.10 '64000'
        comment.item.11 '88200'
        comment.item.12 '96000'
        comment.item.13 '176400'
        comment.item.14 '192000'
        comment.item.15 'IEC958 In'
        iface MIXER
        name 'Multi Track Internal Clock'
        value '44100'
    }
    control.3 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'Multi Track Rate Locking'
        value false
    }
    control.4 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'Multi Track Rate Reset'
        value true
    }
    control.5 {
        comment.access 'read write'
        comment.type ENUMERATED
        comment.count 1
        comment.item.0 'PCM Out'
        comment.item.1 'H/W In 0'
        comment.item.2 'H/W In 1'
        comment.item.3 'IEC958 In L'
        comment.item.4 'IEC958 In R'
        iface MIXER
        name 'H/W Playback Route'
        value 'PCM Out'
    }
    control.6 {
        comment.access 'read write'
        comment.type ENUMERATED
        comment.count 1
        comment.item.0 'PCM Out'
        comment.item.1 'H/W In 0'
        comment.item.2 'H/W In 1'
        comment.item.3 'IEC958 In L'
        comment.item.4 'IEC958 In R'
        iface MIXER
        name 'H/W Playback Route'
        index 1
        value 'PCM Out'
    }
    control.7 {
        comment.access 'read write'
        comment.type ENUMERATED
        comment.count 1
        comment.item.0 'PCM Out'
        comment.item.1 'H/W In 0'
        comment.item.2 'H/W In 1'
        comment.item.3 'IEC958 In L'
        comment.item.4 'IEC958 In R'
        iface MIXER
        name 'H/W Playback Route'
        index 2
        value 'PCM Out'
    }
    control.8 {
        comment.access 'read write'
        comment.type ENUMERATED
        comment.count 1
        comment.item.0 'PCM Out'
        comment.item.1 'H/W In 0'
        comment.item.2 'H/W In 1'
        comment.item.3 'IEC958 In L'
        comment.item.4 'IEC958 In R'
        iface MIXER
        name 'H/W Playback Route'
        index 3
        value 'PCM Out'
    }
    control.9 {
        comment.access 'read write'
        comment.type ENUMERATED
        comment.count 1
        comment.item.0 'PCM Out'
        comment.item.1 'H/W In 0'
        comment.item.2 'H/W In 1'
        comment.item.3 'IEC958 In L'
        comment.item.4 'IEC958 In R'
        iface MIXER
        name 'H/W Playback Route'
        index 4
        value 'PCM Out'
    }
    control.10 {
        comment.access 'read write'
        comment.type ENUMERATED
        comment.count 1
        comment.item.0 'PCM Out'
        comment.item.1 'H/W In 0'
        comment.item.2 'H/W In 1'
        comment.item.3 'IEC958 In L'
        comment.item.4 'IEC958 In R'
        iface MIXER
        name 'H/W Playback Route'
        index 5
        value 'PCM Out'
    }
    control.11 {
        comment.access 'read write'
        comment.type ENUMERATED
        comment.count 1
        comment.item.0 'PCM Out'
        comment.item.1 'H/W In 0'
        comment.item.2 'H/W In 1'
        comment.item.3 'IEC958 In L'
        comment.item.4 'IEC958 In R'
        iface MIXER
        name 'H/W Playback Route'
        index 6
        value 'PCM Out'
    }
    control.12 {
        comment.access 'read write'
        comment.type ENUMERATED
        comment.count 1
        comment.item.0 'PCM Out'
        comment.item.1 'H/W In 0'
        comment.item.2 'H/W In 1'
        comment.item.3 'IEC958 In L'
        comment.item.4 'IEC958 In R'
        iface MIXER
        name 'H/W Playback Route'
        index 7
        value 'PCM Out'
    }
    control.13 {
        comment.access read
        comment.type INTEGER
        comment.count 22
        comment.range '0 - 255'
        iface PCM
        name 'Multi Track Peak'
        value.0 180
        value.1 180
        value.2 0
        value.3 0
        value.4 0
        value.5 0
        value.6 0
        value.7 0
        value.8 180
        value.9 0
        value.10 11
        value.11 11
        value.12 0
        value.13 0
        value.14 0
        value.15 0
        value.16 0
        value.17 0
        value.18 0
        value.19 0
        value.20 0
        value.21 0
    }
    control.14 {
        comment.access 'read write'
        comment.type ENUMERATED
        comment.count 1
        comment.item.0 'PCM Out'
        comment.item.1 'H/W In 0'
        comment.item.2 'H/W In 1'
        comment.item.3 'IEC958 In L'
        comment.item.4 'IEC958 In R'
        iface MIXER
        name 'IEC958 Playback Route'
        value 'PCM Out'
    }
    control.15 {
        comment.access 'read write'
        comment.type ENUMERATED
        comment.count 1
        comment.item.0 'PCM Out'
        comment.item.1 'H/W In 0'
        comment.item.2 'H/W In 1'
        comment.item.3 'IEC958 In L'
        comment.item.4 'IEC958 In R'
        iface MIXER
        name 'IEC958 Playback Route'
        index 1
        value 'PCM Out'
    }
    control.16 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'IEC958 Output Switch'
        value true
    }
    control.17 {
        comment.access 'read write'
        comment.type IEC958
        comment.count 1
        iface PCM
        device 1
        name 'IEC958 Playback Default'
        value '0000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
    }
    control.18 {
        comment.access read
        comment.type IEC958
        comment.count 1
        iface PCM
        device 1
        name 'IEC958 Playback Con Mask'
        value '3fff000f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
    }
    control.19 {
        comment.access read
        comment.type IEC958
        comment.count 1
        iface PCM
        device 1
        name 'IEC958 Playback Pro Mask'
        value df00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000
    }
    control.20 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 127'
        comment.dbmin -6350
        comment.dbmax 0
        iface MIXER
        name 'PCM Playback Volume'
        value.0 127
        value.1 127
    }
    control.21 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 1
        comment.range '0 - 127'
        comment.dbmin -6350
        comment.dbmax 0
        iface MIXER
        name 'PCM Center Playback Volume'
        value 0
    }
    control.22 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 1
        comment.range '0 - 127'
        comment.dbmin -6350
        comment.dbmax 0
        iface MIXER
        name 'PCM LFE Playback Volume'
        value 0
    }
    control.23 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 127'
        comment.dbmin -6350
        comment.dbmax 0
        iface MIXER
        name 'PCM Rear Playback Volume'
        value.0 0
        value.1 0
    }
    control.24 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 127'
        comment.dbmin -6350
        comment.dbmax 0
        iface MIXER
        name 'PCM Headphone Volume'
        value.0 0
        value.1 0
    }
    control.25 {
        comment.access 'read write'
        comment.type ENUMERATED
        comment.count 1
        comment.item.0 '44.1kHz'
        comment.item.1 Off
        comment.item.2 '48kHz'
        comment.item.3 '32kHz'
        iface MIXER
        name Deemphasis
        value Off
    }
    control.26 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 152'
        comment.dbmin -6350
        comment.dbmax 1250
        iface MIXER
        name 'PCM Capture Volume'
        value.0 122
        value.1 122
    }
    control.27 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'PCM Capture Switch'
        value true
    }
    control.28 {
        comment.access 'read write'
        comment.type ENUMERATED
        comment.count 1
        comment.item.0 Mic
        comment.item.1 Line
        comment.item.2 CD
        iface MIXER
        name 'Capture Channel'
        value Mic
    }
    control.29 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 79'
        comment.dbmin -7900
        comment.dbmax 0
        iface MIXER
        name 'Mic Loopback Playback Volume'
        value.0 79
        value.1 79
    }
    control.30 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 79'
        comment.dbmin -7900
        comment.dbmax 0
        iface MIXER
        name 'Line Loopback Playback Volume'
        value.0 79
        value.1 79
    }
    control.31 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 79'
        comment.dbmin -7900
        comment.dbmax 0
        iface MIXER
        name 'CD Loopback Playback Volume'
        value.0 79
        value.1 79
    }
    control.32 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'Loopback Switch'
        value false
    }
}
--endcollapse--


!!All Loaded Modules
!!------------------

Module
binfmt_misc
nls_iso8859_1
nls_cp437
vfat
fat
snd_ice1724
snd_ice17xx_ak4xxx
snd_ac97_codec
radeon
ac97_bus
snd_ak4xxx_adda
snd_ak4114
snd_pt2258
snd_i2c
snd_ak4113
snd_pcm
snd_seq_midi
snd_rawmidi
ttm
snd_seq_midi_event
drm_kms_helper
snd_seq
snd_timer
snd_seq_device
drm
ppdev
snd
parport_pc
k8temp
soundcore
snd_page_alloc
agpgart
asus_atk0110
i2c_algo_bit
i2c_nforce2
lp
parport
usbhid
hid
firewire_ohci
floppy
skge
sata_sil
sata_nv
forcedeth
firewire_core
crc_itu_t
pata_amd


!!ALSA/HDA dmesg
!!------------------


```

Help me plz!

---

### Post by fly2k on 2010-12-14
just noticed, the sound goes to headphones ok, just no sound to speakers... how can I fix it?

---

### Post by gloscherrybomb on 2010-12-14
> **lidex said:**
> Is this a homegrown system? If not, what is make/model? Are you using a PCI card with internal disabled?
Can you post this info please:
```
sudo lshw -C multimedia
```

Its a home built box. Thanks for the help by the way...

```
 *-multimedia UNCLAIMED  
       description: Audio device
       product: VT1708/A [Azalia HDAC] (VIA High Definition Audio Controller)
       vendor: VIA Technologies, Inc.
       physical id: 1
       bus info: pci@0000:80:01.0
       version: 10
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0

```

---

### Post by lidex on 2010-12-14
> **gloscherrybomb said:**
> Its a home built box. Thanks for the help by the way...

```
 *-multimedia UNCLAIMED  
       description: Audio device
       product: VT1708/A [Azalia HDAC] (VIA High Definition Audio Controller)
       vendor: VIA Technologies, Inc.
       physical id: 1
       bus info: pci@0000:80:01.0
       version: 10
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0

```
Try removing the switch you added to alsa-base.conf and reboot into a lower number kernel, .23 if you have it. Then run aplay:
```
aplay -l
```

---

### Post by gloscherrybomb on 2010-12-14
> **lidex said:**
> Try removing the switch you added to alsa-base.conf and reboot into a lower number kernel, .23 if you have it. Then run aplay:
```
aplay -l
```

In .23 this still doesnt work, with our without the alsa base info. When I had .22 (which I dont any more) if I booted to this and went to preferences/sound, it would hang. After that it would revert to the same problem.

  ```
aplay: device_list:235: no soundcards found...

```

---

### Post by lidex on 2010-12-14
@gloscherrybomb
Try booting into .23 then purge .24 and re-install.
Reference this thread:
[http://ubuntuforums.org/showthread.php?p=10239273#post10239273](http://ubuntuforums.org/showthread.php?p=10239273#post10239273)

---

### Post by gloscherrybomb on 2010-12-17
> **lidex said:**
> @gloscherrybomb
Try booting into .23 then purge .24 and re-install.
Reference this thread:
[http://ubuntuforums.org/showthread.php?p=10239273#post10239273](http://ubuntuforums.org/showthread.php?p=10239273#post10239273)

Thanks Lidex,

Did this but still the same situation.

Initially I did an automatic upgrade, but as I thought that may be the problem I then did a clean install. (but maintaining home partition). Still no success.

Could there be a file in my home directory that is causing a conflict somewhere? Or is this a kernel bug?

---

### Post by Flos Headford on 2011-02-05
Can someone remind me - what was the thinking behind the idea of releasing an OS with the sound facilities MUTED by default? Somehow the brilliance of the concept has escaped my meagre mental faculties. I would have thought this might be a bit of a turn-off for people we've just persuaded to try Linux. Or am I the only one who thinks that?
Phil

---

### Post by ng0ofy on 2011-02-12
> **Flos Headford said:**
> Can someone remind me - what was the thinking behind the idea of releasing an OS with the sound facilities MUTED by default? Somehow the brilliance of the concept has escaped my meagre mental faculties. I would have thought this might be a bit of a turn-off for people we've just persuaded to try Linux. Or am I the only one who thinks that?
Phil

I love the silence when I'm install the system on the sixth computer...


Any progress with the internal audio speakers? 
For understanding: In 10.10 newest distro some laptops built-in speakers don't working but the external audio devices do.

---

### Post by jason.b.c on 2011-02-24
> **peroludiarom said:**
> I think that there is some major problem, with pulse audio..
 **Looks like we have to wait Ubuntu team to Fix this Issue.**..

:lolflag:  :lolflag:

good luck with that...

---

### Post by ekrus on 2011-03-08
FWIW.

AMD PHENOM II x4 955 3.2gz
ASUS M4A88TD-V EVO/USB3 

Linux Mint 10 initially installed with SATA in IDE mode.  Sound worked just fine.

Reinstalled with SATA in AHCI mode.  Sound doesn't work.

[   16.241493] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   16.429402] hda_codec: ALC892: BIOS auto-probing.
[   16.435621] Too many connections
[   16.436898] HDA Intel 0000:01:05.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[   16.436937] HDA Intel 0000:01:05.1: setting latency timer to 64

AHCI made a very noticeable improvement in system performance.  Guess I'm going to have to twiddle the bios and reboot if I want to listen to tunes :(

Ken

---

### Post by lidex on 2011-03-09
Try this using a Terminal="Applications->Accessories->Terminal"
```
echo "options snd-hda-intel model=asus" | sudo tee -a /etc/modprobe.d/alsa-base.conf
``` **Reboot**

Did you try updating your alsa-driver modules?

This may be useful also:
[http://black-pixel.net/alc892realtek-id-892-on-mint-linuxubuntu.html](http://black-pixel.net/alc892realtek-id-892-on-mint-linuxubuntu.html)
Patch:
[http://kerneltrap.org/mailarchive/linux-kernel/2010/11/26/4651508](http://kerneltrap.org/mailarchive/linux-kernel/2010/11/26/4651508)

---

### Post by immaculance on 2011-03-09
OK.  10.10 here and having the same issue.  For some time sound would come on and then disappear mid-stream.  Now, it seems that after some update, sound is totally gone, and I've not been successful in restoring it.

[SIZE="4"][COLOR="Red"]**@lidex**[/COLOR][/SIZE]

Ran your recommended commands to re-install alsa, but to no avail.  I then tried booting into an older kernel, but that didn't resolve the issue either.

```
uname -a
Linux Jason-Ubuntu 2.6.32-27-generic #49-Ubuntu SMP Wed Dec 1 23:52:12 UTC 2010 i686 GNU/Linux
```

I also tried removing the old pulse config files, but ran into some unexpected responses:

```
rm -r ~/.pulse ~/.asound* ~/.pulse-cookie
rm: cannot remove `/home/jason/.asound*': No such file or directory
```

```
sudo rm /etc/asound.conf
rm: cannot remove `/etc/asound.conf': No such file or directory
```

I ran the alsa-info-script as well, and my report is at the following URL:

[COLOR="Blue"][CLICK ME! - ALSA Information Script v 0.4.60 | For 2.6.**32**-27-generic kernel]("http://www.alsa-project.org/db/?f=4aa93b525a6b15033913ccd36ae3e353ce9816e2")[/COLOR]

```
uname -a
Linux Jason-Ubuntu 2.6.**35**-27-generic #48-Ubuntu SMP Tue Feb 22 20:25:29 UTC 2011 i686 GNU/Linux
```

[CLICK ME! - ALSA Information Script v 0.4.60 | For 2.6.**35**-27-generic kernel]("http://www.alsa-project.org/db/?f=7594e032c4ef08620a60949f44f00bb7e318213d")

---

### Post by immaculance on 2011-03-10
@lidex:  How does one go about updating their alsa-driver modules?

---

### Post by mcsj on 2011-03-10
My Compaq Presario has no sound too. I tried some of the steps but didnt work. Can someone help?

00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
Subsystem: Hewlett-Packard Company Device 1425
Flags: bus master, fast devsel, latency 0, IRQ 11
Memory at 94400000 (64-bit, non-prefetchable) [size=16K]
Capabilities: <access denied>
Kernel modules: snd-hda-intel


*-multimedia UNCLAIMED  
       description: Audio device
       product: 5 Series/3400 Series Chipset High Definition Audio
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 05
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:94400000-94403fff

---

### Post by lidex on 2011-03-17
> **immaculance said:**
> @lidex:  How does one go about updating their alsa-driver modules?

What do you get for this:
```
dpkg -l | grep "alsa"
```

---

### Post by lidex on 2011-03-17
> **mcsj said:**
> My Compaq Presario has no sound too. I tried some of the steps but didnt work. Can someone help?

00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
Subsystem: Hewlett-Packard Company Device 1425
Flags: bus master, fast devsel, latency 0, IRQ 11
Memory at 94400000 (64-bit, non-prefetchable) [size=16K]
Capabilities: <access denied>
Kernel modules: snd-hda-intel


*-multimedia UNCLAIMED  
       description: Audio device
       product: 5 Series/3400 Series Chipset High Definition Audio
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 05
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:94400000-94403fff
Run the alsa-info script please. Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by immaculance on 2011-03-20
**[COLOR="Red"][SIZE="2"]@ Lidex[/SIZE][/COLOR]**:  Here's what I get :)

```
dpkg -l | grep "alsa"
ii  alsa-base                             1.0.23+dfsg-1ubuntu4                              ALSA driver configuration files
ii  alsa-utils                            1.0.23-2ubuntu3.4                                 Utilities for configuring and using ALSA
ii  bluez-alsa                            4.69-0ubuntu2                                     Bluetooth audio support
ii  gstreamer0.10-alsa                    0.10.30-2                                         GStreamer plugin for ALSA
rc  libsdl1.2debian-alsa                  1.2.13-4ubuntu4                                   Simple DirectMedia Layer (with X11 and ALSA options)
```

---

### Post by immaculance on 2011-03-20
Also, here is **the bug I filed with bugs.launchpad.net** on 03-08-2011. Unfortunately it is still unassigned, and I don't see any movement on it since then, but want to reference it here just in case it adds value to getting my issue resolved.

[INDENT]**Click This --> **[[Ubuntu 10.10 0 - Soundblaster CA0106] ALSA test tone not correctly played back & no sound playing in any application, including system sounds]("https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/731660")[/INDENT]

There appears to be a handful of other individuals filing similar bugs as mine, including generic bugs where sound is just no longer available, some after upgrading to 10.10 (like me).  An important thing to note is that none of the related issues (tickets) appear to be resolved right now, only the best are confirmed & triaged (1):

[INDENT]**Search results for "CA0106 alsa" bugs: **[https://bugs.launchpad.net/bugs/+bugs?field.searchtext=CA0106+alsa&search=Search+Bug+Reports&field.scope=all&field.scope.target=](https://bugs.launchpad.net/bugs/+bugs?field.searchtext=CA0106+alsa&search=Search+Bug+Reports&field.scope=all&field.scope.target=)[/INDENT]

Here is the link to the **Sound Troubleshooting Procedure** page in the **Ubuntu Community Documentation** online:

[INDENT][https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)[/INDENT]

Really hoping this issue gets resolved soon, if not, then hopefully with the next LTS release of Ubuntu, which doesn't look like it will be coming until April of 2012.  We'll wait and see how things turn out with April 2011 (Natty Narwhal), unless some miracle happens and someone is able to help me troubleshoot the issue.

---

### Post by immaculance on 2011-03-20
This is at the bottom of the Sound Troublshooting Procedure in the Ubuntu Community Documentat:

> The following string needs to be added to the /etc/modprobe.d/alsa-base.conf file

options snd-hda-intel model=YOUR_MODEL 
Valid model names (that replace YOUR_MODEL) depending on the codec chip, can be found in "HD-Audio-Models ALSA documentation".

You can find your audio CODEC chip name by running this Terminal command:

```
cat /proc/asound/car*/co*/*|head
```

I ran that last command and wasn't able to get any feedback on it.  I can't determine my CODEC unless I can get this command to return output.

I have two card* directories in my /proc/asound directory, but neither of those directories have a 'co*' directory within them.. ???  Working is this is a problem, but don't know.

---

### Post by immaculance on 2011-03-20
```
**cat /proc/asound/cards**

 0 [HDMI           ]: HDA-Intel - HDA ATI HDMI
                      HDA ATI HDMI at 0xfeaec000 irq 43
 1 [CA0106         ]: CA0106 - CA0106
                      Audigy SE [SB0570] at 0xe800 irq 21
```

---
> [https://wiki.ubuntu.com/DebuggingSoundProblems](https://wiki.ubuntu.com/DebuggingSoundProblems)

Checking permissions and resources
Make sure that all users needing access to the Sound Device can "Use audio devices" in the "User Privileges" tab of users-admin (System->Administration->Users and Groups).

For some reason "Use audio devices" was unchecked for my own admin account.  I checked it.

---

### Post by immaculance on 2011-03-20
Man, this is aweful... I got pretty confused with these instructions...

[https://help.ubuntu.com/community/DebuggingSoundProblemsMisc](https://help.ubuntu.com/community/DebuggingSoundProblemsMisc)

The instructions simply are not clear and explicit enough for me to try to manually install my sound driver/module - I'm pretty much a Linus noob, so I try to work my way through it, but just don't have enough knowledge to apply this stuff.  But I see my module already installed, so I don't think it's a problem of not having the correct driver/module on file:

```
**modinfo snd_ca0106**
filename:       /lib/modules/2.6.35-27-generic/kernel/sound/pci/ca0106/snd-ca0106.ko
license:        GPL
description:    CA0106
author:         James Courtier-Dutton <James@superbug.demon.co.uk>
srcversion:     E698DEACD62919ACB9450B1
alias:          pci:v00001102d00000007sv*sd*bc*sc*i*
depends:        snd,snd-pcm,snd-page-alloc,snd-rawmidi,snd-ac97-codec
vermagic:       2.6.35-27-generic SMP mod_unload modversions 686 
parm:           index:Index value for the CA0106 soundcard. (array of int)
parm:           id:ID string for the CA0106 soundcard. (array of charp)
parm:           enable:Enable the CA0106 soundcard. (array of bool)
parm:           subsystem:Force card subsystem model. (array of uint)
```

This is just getting frustrating at this point - certain documentation is clearly not authored for those that lack extensive Linux/Unix/Ubuntu experience :-x

---

### Post by immaculance on 2011-03-20
OK ... Here's my codec information, but I can only seem to get it back for my on-board HDMI sound ... For some reason I can't get it back for my card1, which is my PCI Soundblaster Audigy SE card:

From HdaIntelSoundHowto
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

```
cat /proc/asound/card0/codec#* | grep Codec
Codec: ATI ID aa01
cat /proc/asound/card1/codec#* | grep Codec
cat: /proc/asound/card1/codec#*: No such file or directory
```

Why can't I get the codec info. for card1?  Is this part of my problem?

---

### Post by lidex on 2011-03-20
@immaculance
You're not using the 2.6.32 kernel on maverick, are you? Stick with 35 for now. To upgrade alsa-modules:
Using a Terminal="Applications->Accessories->Terminal"
Add the ubuntu-audio-dev ppa:
```
sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update
```
Now install:
```
sudo apt-get install linux-alsa-driver-modules-$(uname -r)
```
**Reboot**
Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab. 
On the output tab choose the correct device.

---

### Post by immaculance on 2011-03-20
Thank-you for your quick reply, Lidex.  This issue has become quite frustrating, and I appreciate all the help I can get.

I am not using 2.6.32 kernel - I only manually booted into that once or twice for troubleshooting purposes, but 99% of the time, I'm booting into the following, with no sound:

```
uname -a
Linux Jason-Ubuntu 2.6.35-27-generic #48-Ubuntu SMP Tue Feb 22 20:25:29 UTC 2011 i686 GNU/Linux
```

I performed all steps you instructed of me in your last post.  I successfully added the audio-dev PPA just as instructed, and I installed the alsa driver modules successfully, just as instructed.

My levels all look fine in alsamixer, and I double-checked everything in the sound preferences and everything looks to be set properly.

**[COLOR="Red"]But I still have no sound.  Not even normal system sounds :([/COLOR]**

With the proper driver installed on my Windows 7 OS, I am still experiencing audio just fine.  I still think there is a driver/module/config issue existing here.  Any additional assistance would be greatly appreciated!

---

### Post by lidex on 2011-03-20
@immaculance
Try this to force alsa to recognize the audigy as default. You'll need to edit alsa-base.conf as root.
```
gksu gedit /etc/modprobe.d/alsa-base.conf
```

Add (copy and paste) this text at the end of the file:
```
# ALSA portion
options snd cards_limit=2
alias snd-card-0 snd-ca0106
alias snd-card-1 snd-hda-intel
options snd-ca0106 index=0
options snd-hda-intel index=1
# OSS/Free portion
alias sound-slot-0 snd-ca0106
alias sound-slot-1 snd-hda-intel
```

Now save, close and reboot.

---

### Post by immaculance on 2011-03-21
Thanks, Lidex.  Again, I appreciate your assistance.

I successfully applied the additions to my alsa-base.conf file, saved, and rebooted, but unfortunately I'm [COLOR="Red"]**still not getting any sound output from my Soundblaster Audigy card/device**[/COLOR] :(  I hate to disappoint after applying these possible solutions.

Just to illustrate that I was able to apply the changes successfully, here is a dump of my current alsa-base.conf file after rebooting:

> # autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-caiaq index=-2
options snd-usb-ua101 index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
# Keep snd-usb-audio from beeing loaded as first soundcard
options snd-usb-audio index=-2
#
# ALSA portion - Added 03/21/2011 by JRW per Lidex in Sound Help Thread
options snd cards_limit=2
alias snd-card-0 snd-ca0106
alias snd-card-1 snd-hda-intel
options snd-ca0106 index=0
options snd-hda-intel index=1
# OSS/Free portion
alias sound-slot-0 snd-ca0106
alias sound-slot-1 snd-hda-intel

---

### Post by lidex on 2011-03-21
@immaculance
OK, now this:
```
aplay -l
```

---

### Post by immaculance on 2011-03-22
K ... Got it.  I ran this previously, but never thought to post it here.  Should've done that.  Here ya go :)

```
**aplay -l**
**** List of PLAYBACK Hardware Devices ****
card 0: CA0106 [CA0106], device 0: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 1: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 2: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 3: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

---

### Post by lidex on 2011-03-22
Well that worked -- alsa sees the audigy as default now. What is your sound setup? What outputs are you using? Analog, digital, hdmi?

> Audigy
If your Creative Audigy card is not giving you any sound, make sure the analog/digital check box in your sound mixer is unchecked. Updates seem to reset this switch regularly so keep this in mind.

---

### Post by immaculance on 2011-03-23
1)  I have guayadeque music player installed 0.2.7-1227.  No audio out of it, or when trying to play system sounds or using the stock Rhythmbox music player.

2) My output is an analog 5.1 surround sound system that I got with my Dell computer.  It's comprised of 5 different speakers (F-right, F-left, B-right, B-left, center) and a sub-woofer.  Audio is coming out of this hardware just fine in Windows 7.

3) I set my [Profile] in the Sound Preferences tool, under Hardware tab, to [Analog Surround 5.1 Output], and that seemed to work OK before, except sound wasn't being directed to the right speakers, oddly, so this isn't the beginning of my problems (no sound).  I've tried all the other Profile options, but still nothing comes out.

[IMG]http://i51.tinypic.com/fcp9gk.png[/IMG]
[IMG]http://i56.tinypic.com/cngwz.png[/IMG]



4)  Going into the [GNOME ALSA Mixer], there are four check-boxes at the bottom of the CA0106 tab (for that device)... When I opened it, they are as follows:

[IMG]http://i54.tinypic.com/etifk9.jpg[/IMG]

So, it doesn't look like I have either the Analog or Digital check-boxes checked, and that seems correct to me.  I un-checked the [IEC958] box and played around with it, rebooted after doing so, but still no sound - no difference.

---

### Post by lidex on 2011-03-23
@immaculance
What about the 'Edit -> Sound Card Properties' menu? Any elements not selected there?

---

### Post by immaculance on 2011-03-24
**[COLOR="Red"][SIZE="4"]MY SOUND IS BACK!!![/SIZE][/COLOR]**

I installed some system updates last night, and I noticed that there were quite a bit of audio / ALSA updates coming in.

I also noticed that I appear to have been upgraded to a new kernel version.  If you look at my older posts, I was running 2.6.35-27.

```
Linux Jason-Ubuntu 2.6.35-28-generic #49-Ubuntu SMP Tue Mar 1 14:40:58 UTC 2011 i686 GNU/Linux
```

My money's on that update fixing my issue, but who knows.  Perhaps it took several reboots..

No ...... That can't be it ... I just figured it out!!!  Well, maybe..  Un-checking the IEC958 check-box on my GNOME ALSA Mixer for CA0106 brought my sound back!  I just toggled it un-checked to checked, while playing an MP3, and the audio cut out when checked, but came right back when I un-checked it again.  Before it wasn't doing this - or I wasn't testing it properly.

So, perhaps it took a few reboots to get that to stick when it was un-checked before reboot... And perhaps the ALSA and audio & kernel updates had some factor to play in it as well.  Not really sure.

I do know that [IEC958] will remain un-checked!!!

**[COLOR="Red"]THANKS LIDEX FOR ALL YOUR HELP! PROBLEM SOLVED![/COLOR]**

Now if I can just get my MP3s to stop restarting in Guayadeque & Rhythmbox in the middle of a song, or just stopping all together, I'll be set! Ha #-o

My faith in Linux & Ubuntu has been restored! And, again, Lidex: thanks for taking the time and assisting me; truly appreciate your help.

---

### Post by srlake314 on 2011-04-05
Ok I will feel a little stupid here, but with all the other issues that I have been facing with compatibility I want to make sure I dont blow anything up.

I realize that it's my video card that is listed for the audio device.  Well I have the 
M4A89GTD PRO USB 3.0 MB and I have the speakers hooked up to that.  Those are the connections that I need to use, I dont see any audio connections on the back of the video card :).

I cant find drivers for my MB either, especially on the Asus site, been a real pain on the note.  However, I know there are alot of resourceful people out there that can help point me in the right direction.

below is pasted my sound info via 
sudo lshw - c sound 

 *-multimedia            
       description: Audio device
       product: Juniper HDMI Audio [Radeon HD 5700 Series]
       vendor: ATI Technologies Inc
       physical id: 0.1
       bus info: pci@0000:01:00.1
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi bus_master cap_list
       configuration: driver=HDA Intel latency=0
       resources: irq:46 memory:fe6bc000-fe6bffff
  *-multimedia
       description: Audio device
       product: SBx00 Azalia (Intel HDA)
       vendor: ATI Technologies Inc
       physical id: 14.2
       bus info: pci@0000:00:14.2
       version: 40
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=HDA Intel latency=64
       resources: irq:16 memory:fe5f8000-fe5fbfff

I might point out, i ALSO have Ubuntu Studio 10.10 running.

Ty 

Sean

---

### Post by lidex on 2011-04-05
@srlake314
Your video card uses hdmi for audio output, so no regular jacks.
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by srlake314 on 2011-04-05
[http://www.alsa-project.org/db/?f=105013591f2463cfbc2ef36d353fa5b05575575c](http://www.alsa-project.org/db/?f=105013591f2463cfbc2ef36d353fa5b05575575c)

is the source :).

Ty.

Sean

---

### Post by lidex on 2011-04-05
> **srlake314 said:**
> [http://www.alsa-project.org/db/?f=105013591f2463cfbc2ef36d353fa5b05575575c](http://www.alsa-project.org/db/?f=105013591f2463cfbc2ef36d353fa5b05575575c)

is the source :).

Ty.

Sean

Run alsamixer:
```
alsamixer
```
Press <F3> and scroll over to element 'Front' using L/R arrow keys.
Press the <M> key to unmute. Now raise level with scroll wheel or Up/Dn keys.

---

### Post by addman3 on 2011-04-07
[SIZE=2]Hi, I'm having the same problem, it is recognising a sound card, and in all media players there volume slider is as if it is working. But there just is no sound.

I tried this:

[/SIZE]
Quote:
                                                                      Originally Posted by **lidex**                     [[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=9985546#post9985546")                 
                 [I]Try re-installing alsa. 
Using a Terminal="Applications->Accessories->Terminal"
     Code:
     sudo apt-get update
sudo apt-get upgrade 
     Code:
     sudo apt-get purge linux-sound-base alsa-base alsa-utils 
     Code:
     sudo apt-get install linux-sound-base alsa-base alsa-utils gdm ubuntu-desktop 
**Reboot.**
**gdm and ubuntu-desktop usually get taken out in the process, so we add them back**


I also had this problem when trying to remove pulse audio
rm -r ~/.pulse ~/.asound* ~/.pulse-cookie
rm: cannot remove `/home/adam/.asound*': No such file or directory
This is the alsa info

Your ALSA information is located at [http://www.alsa-project.org/db/?f=22eaa6a1fed2f4e3302b0f4ce0de2c6f954bac57](http://www.alsa-project.org/db/?f=22eaa6a1fed2f4e3302b0f4ce0de2c6f954bac57)


Many Thanks,
Adam
[/I]

---

### Post by lidex on 2011-04-09
> **addman3 said:**
> [SIZE=2]Hi, I'm having the same problem, it is recognising a sound card, and in all media players there volume slider is as if it is working. But there just is no sound.


This is the alsa info

Your ALSA information is located at [http://www.alsa-project.org/db/?f=22eaa6a1fed2f4e3302b0f4ce0de2c6f954bac57](http://www.alsa-project.org/db/?f=22eaa6a1fed2f4e3302b0f4ce0de2c6f954bac57)


Many Thanks,
Adam
[/I]
That looks fine. What profile do you have selected in 'Sound Preferences'?

---

### Post by Compfix101 on 2011-04-11
Hi folks,
      I'm no guru or anything, but I had a similar problem with my sound and I think I might have found a temporary fix until the developers have a chance to investigate this further.

The issue: No sound, no device shown in sound preferences other than the "dummy" device.

What I did:

I went to System>Administration>Synaptic Package Manager
I typed "oss" in the search area and removed ALL packages from the selections listed.
I restarted - Now I knew that the sound shouldn't be there.
I went back into the Package Manager and did a pulseaudio search.
I selected all the Ubuntu emblem marked selections that apply to my system. - after all, doesn't that indicate that those are the ones that should be there?
After applying my selections I rebooted again and my sound was back.
Then I went into the Package Manager one last time and selected the alasa-utils package and applied.
I opened a terminal and ran alsamixer from the terminal and turned the master volume down to about 74% - In some cases, you might need to go down further - and the rest, I turned up (as they applied). It makes little sense to turn up surround speakers if they are not attached, huh?

Well, that's it. I haven't had an issue with it since. Good luck!!

---

