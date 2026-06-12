---
title: "Sound troubleshooting"
date: 2011-11-22
forum: Multimedia Software
---

### Post by mörgæs on 2011-11-22
These two manuals give advice for solving sound problems:

[Sound Troubleshooting Guide]("https://docs.google.com/document/d/1iTlJ8BfqXUjaHO__TEdlkvuqB1WLOkGaudngc5SFLMI/edit")
(by Lkjoel and Wildmanne39)


[Sound Troubleshooting Procedure]("https://help.ubuntu.com/community/SoundTroubleshootingProcedure")
(by Mark Rijckenberg)


If you have tried the two links without result, feel free to ask in this thread.

---

### Post by bpoppe on 2011-12-03
I recently installed mythbuntu on an older PC I had lying around.  Everything seems to be working great, I can play video in HD, but can't get any sound out of my onboard sound.  I followed both guides, as well as tried several other things from google searching to no avail.  My speakers are on and working - I plugged them into my phone and got sound immediately. 

I did have another sound card that I blacklisted - it was for HDMI out from my video card - which is weird because it doesn't have HDMI out (RADEON HD 2600 PRO)

As far as I can tell, everything is configured and recognized, there's just no output coming from my sound card.  Super frustrating!

here's my alsa output:
[http://www.alsa-project.org/db/?f=b9a9a621b8f1598c5c033e52e7fcc53a1ecfbd95](http://www.alsa-project.org/db/?f=b9a9a621b8f1598c5c033e52e7fcc53a1ecfbd95)

I'm a relative noob, but I'm pretty committed to this as I really want to drop satellite and cable and switch to OTA and Boxee. Any suggestions are greatly appreciated.

---

### Post by MoreOrLess on 2011-12-04
Try playing with some of the controls in alsamixer: 
[http://alsa.opensrc.org/FAQ004](http://alsa.opensrc.org/FAQ004)

---

### Post by zenonez on 2011-12-13
So here is my problem ( I tried the troubleshooting but didn't help me out): 
I am running Ubuntu 10.4 lucid lynx on my sony vaio vgn-fw11m laptop, and since a long time the internal jack plug is broken (fysically broken, nothing to do about it). So I have bought an external USB audio device, the steelseries siberia. 

Now this usb device used to work perfectly, ubuntu inmediately recognised it and it was fully functional untill...
It wasn't anymore. the connected usb device is now not recognised anymore by my laptop, I mean it isn't visible in sound devices (output) anymore. When I disconnect and reconnect the thing a few times it seems to pop up in output-devices, but a second after it pops up the computers' screen goes black, and the only thing left to see is the cursor. basically my computer completely freezes and I have to restart it. 
Of course when restarted, the usb sound device is nowhere to be seen. 

This sucks. my laptops speakers are crap (only one is working properly anyway) and as for now I have no way to play something on my laptop and listen to it. 

anyone have an idea what the problem/solution could be? 

Thanks a lot!

---

### Post by mörgæs on 2011-12-14
Hi, welcome to the fora.

We need a few more data points here. Do you get sound in a live boot of 11.10?

---

### Post by zenonez on 2011-12-14
Thanks mörgæs, for your fast answer and the welcoming words :)
I'm kind of ashamed to say this but thought it could prevent another idiot from making the same mistake: 
It wasn't a software problem! 
The cable connecting the usb device to my pc was broken it seems, nothing on the outside but a bad connection. Now using a different one and everything works fine again. 
Only question that remains is why, after de- and reconnecting the usbdevice with the broken cable a few times, my computer would freeze into black screen.. This still kind of bugs me.. 
but hey, I can listen to music again so I guess my worries are over. 
Thanks very much anyway, I'll be sure to make a better troubleshooting next time before posting here :)

---

### Post by mörgæs on 2011-12-14
You are welcome. Good that you got it solved.

---

### Post by aledan on 2011-12-14
After installing Ubuntu 11.10 there is no sound.
Sound card is detected, listed and selected.

I followed guides and at some point I ended without sound card recognized, so I run command to reinstall sound drivers.

Nothing is solved.

[http://www.alsa-project.org/db/?f=c52c096c3a62d6ce7f9f7d6fc4eb83109419bb7c](http://www.alsa-project.org/db/?f=c52c096c3a62d6ce7f9f7d6fc4eb83109419bb7c)

---

### Post by Achillean on 2011-12-15
Hi!

I've started using Ubuntu 11.10 recently (i.e, this morning) and iI'm having issues with the sound as well.

I have sound if I boot from the live cd, but if I boot from the hard drive it can't find a soundcard. I have onboard audio enabled in the BIOS and when i run lspci it sees it just fine.


The audio device listed under lspci is "nVidia Corporation MCP51 High Definition Audio". I googled it and it seems to be an issue that a bunch of people have, and I followed the guides in the first post but they either didnt work or didnt follow through.

Thanks in advance!

---

### Post by lkjoel on 2011-12-16
> **Achillean said:**
> Hi!

I've started using Ubuntu 11.10 recently (i.e, this morning) and iI'm having issues with the sound as well.

I have sound if I boot from the live cd, but if I boot from the hard drive it can't find a soundcard. I have onboard audio enabled in the BIOS and when i run lspci it sees it just fine.


The audio device listed under lspci is "nVidia Corporation MCP51 High Definition Audio". I googled it and it seems to be an issue that a bunch of people have, and I followed the guides in the first post but they either didnt work or didnt follow through.

Thanks in advance!
You followed procedure Ae right?

---

### Post by Achillean on 2011-12-19
> **lkjoel said:**
> You followed procedure Ae right?

i don't remember exactly what i used, but my other thread is [http://ubuntuforums.org/showthread.php?t=1895861](http://ubuntuforums.org/showthread.php?t=1895861) <--there with the solution i used. thanks for your help everyone!

---

### Post by Jaykos on 2011-12-28
Hey everyone, I'm still a newbie to linux and recently am getting acclimated to the new Ubuntu 11.10 (ocelot) downloaded on my old IBM desktop. I finally configured my wireless to work and I've downloaded all the updates. I do have some questions regarding sound though. The internal speaker within the tower is recognized and outputs sound whenever I listen to music but when I plug in my Bose companion 2 Speakers into the jack, the internal speaker wont disable. I just want sound to be coming from my external speakers and not through my internal speaker. Is there any way to do this? I do music editing and this is pretty important to me so I can get a clear crisp sound from my bose speakers. I did the  alsa project thing and here's the URL:

[http://www.alsa-project.org/db/?f=223ee3bb0d1a4a8599db05426acf37d964704123](http://www.alsa-project.org/db/?f=223ee3bb0d1a4a8599db05426acf37d964704123)

Any help would be great!
Thanks:)

---

### Post by lkjoel on 2011-12-28
> **Jaykos said:**
> Hey everyone, I'm still a newbie to linux and recently am getting acclimated to the new Ubuntu 11.10 (ocelot) downloaded on my old IBM desktop. I finally configured my wireless to work and I've downloaded all the updates. I do have some questions regarding sound though. The internal speaker within the tower is recognized and outputs sound whenever I listen to music but when I plug in my Bose companion 2 Speakers into the jack, the internal speaker wont disable. I just want sound to be coming from my external speakers and not through my internal speaker. Is there any way to do this? I do music editing and this is pretty important to me so I can get a clear crisp sound from my bose speakers. I did the  alsa project thing and here's the URL:

[http://www.alsa-project.org/db/?f=223ee3bb0d1a4a8599db05426acf37d964704123](http://www.alsa-project.org/db/?f=223ee3bb0d1a4a8599db05426acf37d964704123)

Any help would be great!
Thanks:)
Run a Terminal (Dash->Terminal) window, and maximize it. Then run this command:
```
alsamixer
```
Then could you give us a screenshot?

---

### Post by Jaykos on 2011-12-28
Heres the shot. Thanks!

---

### Post by Jaykos on 2011-12-28
and another

---

### Post by MoreOrLess on 2011-12-28
@jaykos: I think your headphone jack sense is off by default. Turn it on by selecting the "headphone" item in alsamixer (third one in the left screenshot) and pressing the spacebar.

---

### Post by lkjoel on 2011-12-28
> **Jaykos said:**
> and another
Could you first maximize the terminal window, then run alsamixer, pressing F3?
And could you take another shot apart from that, pressing F6 on alsamixer?

---

### Post by lferner on 2012-01-02
Hi guys,
 
do you think you could help me out with [this]("http://ubuntuforums.org/showthread.php?t=1902423") problem. I worked through your manuals, but didn't manage to play sound from my FHEM server (perl script).
 
It all works fine for root and regular users, I just can't get the daemon process to play sound.
 
I have attached the output of the alsa-info.sh script called from within the shell script which was called by the daemon process.
 
I use the analog Intel sound device (not the Nvidia HDMI one). I have a small PA hooked up to the front left/right jack.
 
The necessary drivers are compiled into the kernel (-> no modules).
 
PulseAudio is not installed, so no pulse* groups in /etc/group. 'fhem' user is member of 'audio' group.
 
I really appreciate your help.
 
Thanks
 
   Lars

---

### Post by robn30 on 2012-01-05
I have a thread going in a different area for my current issue [http://ubuntuforums.org/showthread.php?t=1901598](http://ubuntuforums.org/showthread.php?t=1901598).
 
Figured I would post here as well.  I can't get sound working with my Asus P5N-E SLI MB.  It uses the Nvidia MCP51 and ALC883 codec.  Here is the link to my Alsa Info as well [http://www.alsa-project.org/db/?f=f431aa0f76bf4232f6edfa0e4444b75f4dc2422c](http://www.alsa-project.org/db/?f=f431aa0f76bf4232f6edfa0e4444b75f4dc2422c). 
 
Using the Try Ubuntu option on my Flash Drive works fine.  When I first have Ubuntu 11.10 installed and before performing the 280+ updates, the sound works.  After the updates it's a no go, sound is completely broken.  My hardware is perfectly detected but no sound at all.  You can review the thread that I started and see if there is anything I have not done yet.  Thanks.

---

### Post by iljajj on 2012-01-06
Hi, I'm running 11.10 on a Panasonic CF-30, and recently upgraded from 11.04. However, I'm still quite new to Ubuntu, having migrated from OS X.

My problem isn't so much with the sound drivers (tried that): sound in general is fine. However, where in 11.04 I could choose between 'analog output' and 'analog headphones' in the output tab of the sound control panel. After upgrading, the only option left is 'analog headphones' which controls both speaker and headphones. Muting either headphones or front speaker in Alsamixer will result in killing sound altogether. It would of course be ideal if the OS would sense whether I've plugged in my headphones and mute the speaker then, but I could live with the 11.04 solution of having to choose the sound output.

Any help would be greatly appreciated, since I've run out of steam on my own.

Link to Alsa project log file: [https://www.fontfont.com/news/join-our-hardworking-funloving-team](https://www.fontfont.com/news/join-our-hardworking-funloving-team) (originally forgot, thanks for reminding)

Screenshot from Alsamixer:
[IMG]http://dl.dropbox.com/u/314182/alsascreenshot.png[/IMG]

p.s. I should mention that I also uninstalled PulseAudio after upgrading since it continued to crash. The server's still running by the looks of it.

---

### Post by MoreOrLess on 2012-01-06
> **iljajj said:**
> Hi, I'm running 11.10 on a Panasonic CF-30, and recently upgraded from 11.04. However, I'm still quite new to Ubuntu, having migrated from OS X.
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by iljajj on 2012-01-06
> **MoreOrLess said:**
> [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

Ah yes, I KNEW I'd forgotten something (sorry):
[http://www.alsa-project.org/db/?f=3526a4ea1c9c1bb67b29d5c3af49e224b5acf3ee](http://www.alsa-project.org/db/?f=3526a4ea1c9c1bb67b29d5c3af49e224b5acf3ee)

---

### Post by iljajj on 2012-01-06
Moved this thread outside this sticky, where it didn't belong in the first place - apologies for that:

[http://ubuntuforums.org/showthread.php?t=1905254](http://ubuntuforums.org/showthread.php?t=1905254)

---

### Post by MoreOrLess on 2012-01-06
I would file a bug on Launchpad, since this is a regression.

---

### Post by iljajj on 2012-01-07
> **MoreOrLess said:**
> I would file a bug on Launchpad, since this is a regression.

I see a number of similar bugs filed already, so I don't think I'll bother. That probably means that no one is able to solve it; regretfully, that also means that Ubuntu's probably out of the door for me, since I can't really work with the speaker blaring all the time.

---

### Post by mörgæs on 2012-01-07
You could also continue with 11.04 for as long as it is supported. It is not uncommon that the second-latest Buntu release is superiour to the latest.

---

### Post by iljajj on 2012-01-07
> **mörgæs said:**
> You could also continue with 11.04 for as long as it is supported. It is not uncommon that the second-latest Buntu release is superiour to the latest.

I might do that if the rollback isn't too complicated. However, after a bit of getting used to I rather like Unity in 11.10 - more than either Unity in 11.04 or Gnome 2, to be honest. I'm wondering if upgrading to a beta of 12.04 might be worth a try, though.

The key might be in editing the [alsa-base.conf file]("http://ubuntuforums.org/showthread.php?t=1043568"), but the problem is finding the right definition. I've posted a similar question in the Panasonic Toughbook forums, will report here if that produces anything.

---

### Post by mörgæs on 2012-01-07
> **iljajj said:**
> I'm wondering if upgrading to a beta of 12.04 might be worth a try

12.04 is in Alpha now. I would recommend that you do a parallel install and not an upgrade, since it is ... well, an Alpha.

If you report a bug against 12.04, it is more likely that it gets fixed than for 11.10.

---

### Post by iljajj on 2012-01-07
> **mörgæs said:**
> 12.04 is in Alpha now. I would recommend that you do a parallel install and not an upgrade, since it is ... well, an Alpha.

If you report a bug against 12.04, it is more likely that it gets fixed than for 11.10.

Thanks for that. I might tough it out until 12.04 beta becomes available. The point is that 11.10 is quite a bit snappier both in booting the system and in starting applications, than 11.04 used to be. And I've actually come to appreciate unity now that I can use the Equinox theme (yes, aesthetics ARE important to me). 

Unless I can find a solution, I may restort to cutting the speaker altogether by disconnecting it (not too hard in a Toughbook) and reconnecting it once it's possible. I don't like audio feedback anyway, and I rarely use it for other purposes.

---

### Post by iljajj on 2012-01-07
Desperate times call for desperate measures, so I disconnected the speaker. The problem is gone for now, but so is my speaker. I'll return to the issue it when I move to 12.04, because a solution for 11.10 doesn't look likely in the near future.

---

### Post by Tk007LwZFJW5ej on 2012-01-25
I made it to the second part of step one in the Sound Troubleshooting Procedure: "[B]If you upgraded ALSA using the command above...." and after rebooting, I found that I can no longer access alsamixer, whether from the command line or gnome mixer, and the sound still doesn't work. ALSA is installed and updated to the latest version.

Here's what I got after executing
[/B]```
wget -O alsa-info.sh http://www.alsa-project.org/alsa-info.sh; chmod +x ./alsa-info.sh; ./alsa-info.sh
```[B]
It looks like some drivers or something are missing here, but I don't know what to download to get them:

[/B]```

!!DMI Information !!---------------  Manufacturer:      Dell Inc.          Product Name:      Dell System XPS L702X Product Version:      !!Kernel Information !!------------------  Kernel release:    3.0.0-15-generic Operating System:  GNU/Linux Architecture:      x86_64 Processor:         x86_64 SMP Enabled:       Yes   !!ALSA Version !!------------  Driver version:      Library version:    1.0.24.1 Utilities version:  1.0.24.2   !!Loaded ALSA modules !!-------------------    !!Sound Servers on this system !!----------------------------  Pulseaudio:       Installed - Yes (/usr/bin/pulseaudio)       Running - Yes  ESound Daemon:       Installed - Yes (/usr/bin/esd)       Running - No   !!Soundcards recognised by ALSA !!-----------------------------    !!PCI Soundcards installed in the system !!--------------------------------------  00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)   !!Advanced information - PCI Vendor/Device/Subsystem ID's !!--------------------------------------------------------  00:1b.0 0403: 8086:1c20 (rev 05)     Subsystem: 1028:0571   !!Modprobe options (Sound related) !!--------------------------------  snd-atiixp-modem: index=-2 snd-intel8x0m: index=-2 snd-via82xx-modem: index=-2 snd-usb-audio: index=-2 snd-usb-caiaq: index=-2 snd-usb-ua101: index=-2 snd-usb-us122l: index=-2 snd-usb-usx2y: index=-2 snd-cmipci: mpu_port=0x330 fm_port=0x388 snd-pcsp: index=-2 snd-usb-audio: index=-2   !!Loaded sound module options !!--------------------------   !!ALSA Device nodes !!-----------------  crw-rw---- 1 root audio 116,  1 Jan 25 11:33 /dev/snd/seq crw-rw---- 1 root audio 116, 33 Jan 25 11:33 /dev/snd/timer   !!Aplay/Arecord output !!------------  APLAY  aplay: device_list:240: no soundcards found...  ARECORD  arecord: device_list:240: no soundcards found...  !!Amixer output !!-------------   !!Alsactl output !!-------------  --startcollapse-- --endcollapse--   !!All Loaded Modules !!------------------  Module bnep rfcomm pci_stub vboxpci vboxnetadp vboxnetflt vboxdrv parport_pc ppdev binfmt_misc ip6t_LOG xt_hl ip6t_rt nf_conntrack_ipv6 nf_defrag_ipv6 ipt_REJECT ipt_LOG uvcvideo videodev xt_limit xt_tcpudp xt_addrtype v4l2_compat_ioctl32 xt_state ip6table_filter ip6_tables nf_conntrack_netbios_ns nf_conntrack_broadcast nf_nat_ftp nf_nat nf_conntrack_ipv4 joydev nf_defrag_ipv4 nf_conntrack_ftp nf_conntrack arc4 i915 iwlagn nouveau iptable_filter ip_tables x_tables dell_wmi mac80211 cfg80211 btusb dell_laptop ttm drm_kms_helper dcdbas psmouse sparse_keymap serio_raw mei drm soundcore bluetooth mxm_wmi wmi i2c_algo_bit video lp parport r8169 ahci xhci_hcd libahci   !!ALSA/HDA dmesg !!------------------ 
```

---

### Post by Tk007LwZFJW5ej on 2012-01-25
Wow, previous output is hard to read. Let me try just posting a link:

[http://www.alsa-project.org/db/?f=c5496d56319d70323a4ad3e496c3f18f9a311736](http://www.alsa-project.org/db/?f=c5496d56319d70323a4ad3e496c3f18f9a311736)

---

### Post by orange_roughy on 2012-02-05
Hi,

When I change the mic levels on the HDA Intel (ALSA mixer) Recording tab, the changes are not retained. Meaning, when I re-open the Volume Control, the levels are right where they were before (at zero).

Help!

---

### Post by MoreOrLess on 2012-02-05
It seems that a lot of folks who follow the Sound Troubleshooting Guide end up with missing/borken kernel module..

---

### Post by torberry on 2012-02-15
I've just installed 11.10 and can't get audio working.  Tried it with a 11.10 live CD and it wasn't working either.  I've also maxed out the volume in ALSA mixer.

My ALSA info:
[http://www.alsa-project.org/db/?f=9f3da726e71e4421edae01f7e5125efeecd9942c](http://www.alsa-project.org/db/?f=9f3da726e71e4421edae01f7e5125efeecd9942c)

What can I do to fix this?

---

### Post by tirant on 2012-02-17
Well... I just lost my audio. Followed both guides, but nothing worked.

[http://ubuntuforums.org/showthread.php?t=1926030](http://ubuntuforums.org/showthread.php?t=1926030)

---

### Post by mark768 on 2012-02-19
Hi,
I'd appreciate help getting my Delta 1010LT card recognised by ALSA, running Ubuntu 11.10.
When I first installed the card, ubuntu hung and wouldn't start, including the live CD.
Sound card is working under Windows 7.
So far I've tried disabling motherboard sound in BIOS and disabling serial port in BIOS in case of conflicts.
Now Unbuntu will start, but it seems card is not recognised by ALSA.
Running Envy24control gives No ICE1712 card detected.

Please see info here:    	 	 	 	 	
[http://www.alsa-project.org/db/?f=ed394992cb2412b217c8278f3294050ec839d8b7](http://www.alsa-project.org/db/?f=ed394992cb2412b217c8278f3294050ec839d8b7)

The sound card is not recognised by ALSA
I tried to get it to load the module snd_ice1712, but no difference.
Any ideas?
Thanks
Mark


[URL="http://www.alsa-project.org/db/?f=ed394992cb2412b217c8278f3294050ec839d8b7"]
[/URL]

---

### Post by esrom02 on 2012-02-25
```
/sbin/alsactl: save_state:1519: No soundcards found...
cat: /tmp/alsa-info.6fyj6ZYueG/alsactl.tmp: No such file or directory
upload=true&script=true&cardinfo=
!!################################
!!ALSA Information Script v 0.4.60
!!################################

!!Script ran on: Sat Feb 25 08:55:31 UTC 2012


!!Linux Distribution
!!------------------

Ubuntu 10.04.4 LTS \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 10.04.4 LTS"


!!DMI Information
!!---------------

Manufacturer:      Sony Corporation
Product Name:      PCV-LX55_BP
Product Version:    


!!Kernel Information
!!------------------

Kernel release:    2.6.32-38-generic
Operating System:  GNU/Linux
Architecture:      i686
Processor:         unknown
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     1.0.24
Library version:    1.0.24.1
Utilities version:  1.0.24.2


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

00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio Controller (rev 05)


!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!--------------------------------------------------------

00:1f.5 0401: 8086:2445 (rev 05)
	Subsystem: 104d:80e4
--
	Subsystem: 13e0:0401
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-


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


!!ALSA Device nodes
!!-----------------

crw-rw----+ 1 root audio 116,  1 Feb 25 16:54 /dev/snd/seq
crw-rw----+ 1 root audio 116, 33 Feb 25 16:54 /dev/snd/timer


!!Aplay/Arecord output
!!------------

APLAY

aplay: device_list:240: no soundcards found...

ARECORD

arecord: device_list:240: no soundcards found...

!!Amixer output
!!-------------


!!Alsactl output
!!-------------

--startcollapse--
--endcollapse--


!!All Loaded Modules
!!------------------

Module
binfmt_misc
ppdev
snd_intel8x0
snd_ac97_codec
ac97_bus
snd_pcm_oss
snd_mixer_oss
snd_pcm
snd_seq_dummy
snd_seq_oss
snd_seq_midi
snd_rawmidi
snd_seq_midi_event
snd_seq
snd_timer
snd_seq_device
pcmcia
snd
yenta_socket
rsrc_nonstatic
soundcore
pcmcia_core
joydev
snd_page_alloc
nvidia
serio_raw
intel_agp
shpchp
agpgart
lp
parport
8139too
ohci1394
8139cp
ieee1394
mii
usbhid
hid


!!ALSA/HDA dmesg
!!------------------

[   19.653856] ppdev: user-space parallel port driver
[   20.212122] ALSA intel8x0.c:2447: codec_ready: codec is not ready [0x300000]
[   20.212261] Intel ICH 0000:00:1f.5: PCI INT B disabled
```

Please help me, sound card works fine with Puppy Linux.. :/

---

### Post by IgnisK on 2012-02-25
Hey, ive been having some audio trouble with my onboard audio.

Using Ubuntu 10.04LTS
The mainboard in question is MSI K8N Neo4 Platinum (PCB 1.0)

As attachment ive added some off the command returns.

The problem is that ive got simply no audio whatsoever, when trying the guides at the start of this thread i run into the problem that it the package linux-alsa-driver-modules-2.6.32-38-generic-pae cant be found.

---

### Post by Nu2ubun on 2012-02-26
I was going through the trouble shooting guide and i got to the point where it told me to follow procedure X. if i got now output but when i went to look for procedure x i couldn't find it. can you help me please and thank you.

---

### Post by Silviugdr on 2012-03-01
hello..i`m on ubuntu 11.10 x64, i`m using a 5.1 system and i don`t have bass coming from the subwoofer when playing stereo music, when playing music in 6 channels the subwoofer works but barely(low bass). at the sound settings evrything looks ok, i`ve selected 5.1 output, the test comes out ok. in alsamixer i`ve turned the subwoofer and LFE volume to max, and still i get weak or not at all bass from the subwoofer. The weird part is, if i play a music in banshee(or any other music player), during the play, i change the settings from analog 5.1 output to any other analog output setings, the bass blows off really loud like it should, and if a change it back to analog 5.1 output it remains ok, with bass..but this is only during the song. when i close or change the song it`s back again with no bass, really crappy sound. i don`t know what to do:(..and i can`t find the problem on the internet. i`m using a hd intel ich9 adi1988B soundcard(soundsupreme fx2)..please help..thank you
(sorry for the spelling errors)

---

### Post by xjmcgowanx on 2012-03-05
So I downloaded Ardor and its amazing, for the most part. I can record and it doesn't lag or anything like it is on Windows 7 for me, but when I plug my amp in I don't get any playback at all, how can I fix this?

---

### Post by cnek on 2012-03-12
Hello, 

I'm having trouble with my ubuntu installation, as the sound isn't  working. I've tried going through the usual guides found through google  but nothing I've done seems to work permanently. I've run the alsa info  script and the output is here:

[http://www.alsa-project.org/db/?f=d8...b9f4f21db24ac2]("http://www.alsa-project.org/db/?f=d8b5e597ba02fecb510f013074b9f4f21db24ac2")

---

### Post by flacone on 2012-03-14
My sound playback is jerky, blubbery, snatchy, choppy, like if there is a timing issue (like it makes some wrong synchronizations). This happend at fullscreen videos in Ubuntu 10.04. After upgrading from 11.04 to 11.10 my sound playback got worse, and all audio playback is in this way. This includes .ogg files played with movieplayer, Banshee; gst-launch audiotestsrc ! autoaudiosink. Interestingly the playback is okay after a fresh reboot, but after some browsing in the web or just Using Banshee for a while the sound becomes horrible (2 minutes or so). 
I followed the procedures with updating everything. I also tried a live-CD with the same effect. Run from the live-CD i got the following ALSA infos:

[http://www.alsa-project.org/db/?f=64c4c6b633e3d0d619140d9c36ac25180ca9207f](http://www.alsa-project.org/db/?f=64c4c6b633e3d0d619140d9c36ac25180ca9207f)

The machine is a Lenovo T60 with 4GB RAM, 2GHz Dual Core. 
Running Ubuntu 11.04 or Windows 7 from an external disk, the sound is fine.

What can I do? Pleas some Help. Please. I donno what to do.

---

### Post by the_real_bubba on 2012-03-15
> **mörgæs said:**
> 
If you have tried the two links without result, feel free to ask in this thread.

SoundTroubleshootingProcedure: step 1 fails with:
E: Unable to locate package linux-alsa-driver-modules-3.0.0-16-generic-pae
E: Couldn't find any package by regex 'linux-alsa-driver-modules-3.0.0-16-generic-pae'

(FWIW: my underlying problem is no analog phono output, seems like only HDMI output is working, Realtek ALC888 seems not to be recognized or loaded or something)

grep "Codec:" /proc/asound/card*/codec*
/proc/asound/card0/codec#2:Codec: Realtek ALC888
/proc/asound/card1/codec#0:Codec: ATI R6xx HDMI

---

### Post by dadexix86 on 2012-03-17
Hi! I'm on Ubuntu 11.10, kernel 3.0.0-17.
I've got a big problem with my microphones and [FONT="Courier New"]00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)[/FONT]

I experience the problem with both the internal microphone and one part of a headset.

When using them to record sound with Sound Recorder or Cheese or when using them to talk in GTalk or Skype I experience a lot annyoing of noise.

I try to follow some guide on the internet, in fact all are like the answer here: [http://askubuntu.com/questions/8269/microphone-alsa-noise](http://askubuntu.com/questions/8269/microphone-alsa-noise) and it doesn't work.

I tried to troubleshoot following the second guide on the first post but it says me
```
E: Unable to locate package linux-alsa-driver-modules-3.0.0-17-generic
E: Couldn't find any package by regex 'linux-alsa-driver-modules-3.0.0-17-generic'
```

Please can anyone help me? What else can I do? Should I provide more informations?

Many thanks

---

### Post by cyril.godart on 2012-03-18
I have lost the sound in Ubuntu since 11.04. I have been trying on and off various paths, including a complete re-install. I have just bumped onto the     
[LIST]
[*][SoundTroubleshootingProcedure]("https://help.ubuntu.com/community/SoundTroubleshootingProcedure?action=fullsearch&context=180&value=linkto%3A%22SoundTroubleshootingProcedure%22")
[/LIST]
and am trying the first advice. I being thrown an error though:
E: Unable to locate package linux-alsa-driver-modules-3.0.0-17-generic
I guess this is because the the kernel has been upgraded recently and the package has not been yet compiled for this. 

Besides, I have a Sonar STX card for which the appropriate module seems to be virtuoso which is delivered with a newer version of Alsa than the one provided with 11.10 apparently. I am trying to compile the alsa drivers but something goes wrong.
Here is what configure gives me:
```
checking for gcc... gcc
checking for C compiler default output... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for ranlib... ranlib
checking for a BSD-compatible install... /usr/bin/install -c
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking whether time.h and sys/time.h may both be included... yes
checking whether gcc needs -traditional... no
checking for current directory... /usr/src/alsa/alsa-driver-1.0.9rc4a
checking cross compile... 
checking for directory with kernel source... /lib/modules/3.0.0-17-generic/build
checking for directory with kernel build... 
checking for kernel version... 0.0.0
checking for GCC version... ./configure: eval: line 3568: syntax error near unexpected token `)'
./configure: eval: line 3568: `my_compiler_version=4.6.1-9ubuntu3)'
cyrilgodart@cyrilgodart-Linux-Ubuntu-Maingear:/usr/src/alsa/alsa-driver-1.0.9rc4
```
And here is what make gives me
```

[B]make all-deps
make[1]: Entering directory `/usr/src/alsa/alsa-driver-1.0.9rc4a'
make[1]: Nothing to be done for `all-deps'.
make[1]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.9rc4a'

Please, run the configure script as first...
[/B]
```

Any help would be appreciated. 

Best

---

### Post by Yellow Pasque on 2012-03-19
You're trying to compile an ancient version of ALSA. There's an easier way: [http://ubuntuforums.org/showthread.php?t=1681577](http://ubuntuforums.org/showthread.php?t=1681577)

---

### Post by jimbean on 2012-03-24
no sound on a asus monitor, monitor sound works in windows vista

---

### Post by jimbean on 2012-03-24
solved wrong jack and analog settings in sound preferences

---

### Post by Chris Weaver on 2012-04-04
I'm loath to post asking for help but I seem to of hit a brick wall with recording on my sound card. Playback is fine and oddly enough I can hear the input (i.e the signal I want to record) mirrored in my output. I'm using an Realtek ALC269 VB on a Dell Optiplex 980 running 10.10.I've upgraded to the latest version of Alas and have tried many settings in the Alsamixer. Any pointers would be appreciated!

cheers,

Chris

---

### Post by takka360 on 2012-04-17
I have just installed backtrack 5r2 and the audio is very distorted on playback of anything.
Can anybody advice please?

---

### Post by takka360 on 2012-04-17
Hi i am new to linux and have tried backtrack from 4 to 5r2 but i seem to
have distorted sound on playback be it youtube i player etc
Can anybody help on this one?
Thanks

---

### Post by mörgæs on 2012-04-17
1) Please don't double-post
2) The thread is meant for questions relating to one or both of the guides in the first post. It is expected that you first try troubleshooting as much as you can based on the guides.

---

### Post by takka360 on 2012-04-17
I will now be leaving the forum i don't need this petty rubbish

---

### Post by MrWeeds on 2012-04-18
hi there.

I am running an HP Pavilion Desktop system. After losing my hdd to a power supply death I am now running a Linux only system, using 11.10
I am a linux noob, but have had success in fixing a few other bugs out, via reading the forums, and a few other helpful sites. However my sound issue is driving me nuts. After going through both methods twice, i still have no sound. 
Here is my alsa info.
[http://www.alsa-project.org/db/?f=2a16057bf1d6c39874773a15e4955d3edd607330](http://www.alsa-project.org/db/?f=2a16057bf1d6c39874773a15e4955d3edd607330)
And after reading through this thread to see if any of the comments matched my problem i saw that my alsamixer does not show what the other's show.
Screen shots are attached.

Basically, I am trying to get ubuntu to use my ONBOARD sound in lieu of trying to use my ati radeon hd5770 graphics card. I think hope this may fix my problem, but not sure, so any help is greatly appreciated.
if any other info is needed, i will provide it. 

Thanx,

MrW

---

### Post by Yellow Pasque on 2012-04-18
@MrWeeds: See if using the latest version of ALSA helps: [https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS)

---

### Post by takka360 on 2012-04-18
This is what i done and it works fantastic now.

The first thing you'll have to do is get rid of PulseAudio:

 	Code:
 	sudo apt-get install gstreamer0.10-alsa gnome-alsamixer sudo apt-get purge pulseaudio gstreamer0.10-pulseaudio vlc-plugin-pulse 
Then you'll need to put the following configuration file into your user home directory. Save it as ".asoundrc":
 	Code:
 	pcm.!default {     type plug     slave.pcm {         type asym         playback.pcm {             type route             slave.pcm "dmix:0"             ttable.0.0 0.66             ttable.0.1 0.33             ttable.1.0 0.33             ttable.1.1 0.66         }         capture.pcm "hw:0"     } } 
Log out and log in again, then open a terminal window and run the following test:

 	Code:
 	speaker-test -t wav -c 2 
This will play back two sound clips ("front left" and "front  right"). You should be able to hear both clips on either channel, with  one being slightly louder than the other.

---

### Post by MrWeeds on 2012-04-18
> **Temüjin said:**
> @MrWeeds: See if using the latest version of ALSA helps: [https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS)

I downloaded the drivers, and when the software center opened up, it stated that that the latest drivers were already installed. I reinstalled them, rebooted, and no sound..
:confused:

I noticed that the drivers were written? for the i386 architecture, when my computer is 1686. I wonder if this may be part of the problem.

thanks for your help):P

MrW

---

### Post by MrWeeds on 2012-04-18
> **takka360 said:**
> This is what i done and it works fantastic now.

The first thing you'll have to do is get rid of PulseAudio:

 	Code:
 	sudo apt-get install gstreamer0.10-alsa gnome-alsamixer sudo apt-get purge pulseaudio gstreamer0.10-pulseaudio vlc-plugin-pulse 
Then you'll need to put the following configuration file into your user home directory. Save it as ".asoundrc":
 	Code:
 	pcm.!default {     type plug     slave.pcm {         type asym         playback.pcm {             type route             slave.pcm "dmix:0"             ttable.0.0 0.66             ttable.0.1 0.33             ttable.1.0 0.33             ttable.1.1 0.66         }         capture.pcm "hw:0"     } } 
Log out and log in again, then open a terminal window and run the following test:

 	Code:
 	speaker-test -t wav -c 2 
This will play back two sound clips ("front left" and "front  right"). You should be able to hear both clips on either channel, with  one being slightly louder than the other.

I did the first step, and it said that it was unable to locate package apt-get and purge (see screen shot)

so i went to the second command, and got an "event not found" message. (see scree shot)  

ugh, this is frustrating. While I LOVE linux, and LOVE trouble shooting, i am becoming a defeatist. lol Thank you for your assistance. ):P

---

### Post by takka360 on 2012-04-18
The first thing you'll have to do is get rid of PulseAudio:

Code:

sudo apt-get install gstreamer0.10-alsa gnome-alsamixer
sudo apt-get purge pulseaudio gstreamer0.10-pulseaudio vlc-plugin-pulse

Then you'll need to put the following configuration file into your user home directory. Save it as ".asoundrc":
Code:

pcm.!default {
    type plug
    slave.pcm {
        type asym
        playback.pcm {
            type route
            slave.pcm "dmix:0"
            ttable.0.0 0.66
            ttable.0.1 0.33
            ttable.1.0 0.33
            ttable.1.1 0.66
        }
        capture.pcm "hw:0"
    }
}

Log out and log in again, then open a terminal window and run the following test:

Code:

speaker-test -t wav -c 2

---

### Post by takka360 on 2012-04-18
[U][I]Code:

sudo apt-get install gstreamer0.10-alsa gnome-alsamixer
sudo apt-get purge pulseaudio gstreamer0.10-pulseaudio vlc-plugin-pulse

Then you'll need to put the following configuration file into your user home directory. Save it as ".asoundrc":
Code:

pcm.!default {
    type plug
    slave.pcm {
        type asym
        playback.pcm {
            type route
            slave.pcm "dmix:0"
            ttable.0.0 0.66
            ttable.0.1 0.33
            ttable.1.0 0.33
            ttable.1.1 0.66
        }
        capture.pcm "hw:0"
    }
}

Log out and log in again, then open a terminal window and run the following test:

Code:

speaker-test -t wav -c 2

This will play back two sound clips ("front left" and "front right"). You should be able to hear both clips on either channel, with one being slightly louder than the other.[/I][/U]

---

### Post by takka360 on 2012-04-18
_[http://ubuntuforums.org/showthread.php?t=1384860](http://ubuntuforums.org/showthread.php?t=1384860)_

Look here this is where i got it,im having trouble to copy this you might have more luck
it worked for me first time.

---

### Post by MrWeeds on 2012-04-18
@ takka

nope didn't work

I am thinking that maybe if i switch to Ubuntu 12.04, or even Debian 6 (squeeze) it may potentially solve my problems.
any thoughts on this, or am i just potentially perpetuating the problem?

thanks

MrW

---

### Post by takka360 on 2012-04-18
".asoundrc": are you saving to root with gedit exactly how its written here with symbols?

---

### Post by Yellow Pasque on 2012-04-18
@takka360: advising people to remove pulseaudio is probably a bad idea in general (though it may work in some cases).

---

### Post by MrWeeds on 2012-04-19
> **takka360 said:**
> ".asoundrc": are you saving to root with gedit exactly how its written here with symbols?

yes, i am.

fun times. lol

---

### Post by Pednick on 2012-04-19
I have a suggestion if it hasn't been implemented in the new release of Ubuntu; get rid of pulseaudio altogether, it's inferior to Alsa and that Alsa should be the default system for Ubuntu. I'm sick of purging pulseaudio and it's elements every time I have to install a new version of Ubuntu and I'm sure that the majority of Linux users are too.

---

### Post by Yellow Pasque on 2012-04-19
> **Pednick said:**
> I have a suggestion if it hasn't been implemented in the new release of Ubuntu; get rid of pulseaudio altogether, it's inferior to Alsa and that Alsa should be the default system for Ubuntu. I'm sick of purging pulseaudio and it's elements every time I have to install a new version of Ubuntu and I'm sure that the majority of Linux users are too.
Use Lubuntu or find another distro, because Ubuntu devs aren't dropping pulseaudio.

---

### Post by Pednick on 2012-04-19
> **Temüjin said:**
> Use Lubuntu or find another distro, because Ubuntu devs aren't dropping pulseaudio.

So Libuntu doesn't put even a little trace of pulseaudio? I guess I could try that. anything to get rid of that crappy pulseaudio.

---

### Post by CJ_Hudson on 2012-04-21
Bug reported [here]("https://bugs.launchpad.net/ubuntu/+source/gnome-media/+bug/775345") as regressed in 11.10 also affects me.
If I disable pulse audio will I lose any other sound functionality too? I like to switch between speakers and USB headset.
I heard elsewhere this bug might be fixed in 12.04, perhaps I should just waitfor the rollout. Comments please?:confused:

---

### Post by mörgæs on 2012-04-21
> **MogBug said:**
> 
I heard elsewhere this bug might be fixed in 12.04, perhaps I should just waitfor the rollout. Comments please?:confused:

You don't need to wait. You can test now in a live boot.

---

### Post by Normand on 2012-04-22
I just upgraded yesterday from 11.04 via 11.10 to 12.04
And now have no sound.

Did the relevant stuff in the 'guide' - no result
Now with the SoundTroubleshootingProcedure:

System recognises the sound carda and all is on in Alsa.

Result below from one of the tests shows the Driver version different from the Library and Utility version which might be the problem.

How can I get the right version

Thanks in advance.

norman@norman-desktop:~$ bash alsa-info.sh --stdout
upload=true&script=true&cardinfo=
!!################################
!!ALSA Information Script v 0.4.60
!!################################

!!Script ran on: Sun Apr 22 09:57:09 UTC 2012


!!Linux Distribution
!!------------------

Ubuntu 12.04 LTS \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 12.04 LTS"


!!DMI Information
!!---------------

Manufacturer:      To Be Filled By O.E.M.
Product Name:      To Be Filled By O.E.M.
Product Version:   To Be Filled By O.E.M.


!!Kernel Information
!!------------------

Kernel release:    3.2.0-23-generic
Operating System:  GNU/Linux
Architecture:      x86_64
Processor:         x86_64
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     1.0.24
Library version:    1.0.25
Utilities version:  1.0.25


!!Loaded ALSA modules
!!-------------------

snd_hda_intel


!!Sound Servers on this system
!!----------------------------

Pulseaudio:
      Installed - Yes (/usr/bin/pulseaudio)
      Running - Yes

ESound Daemon:
      Installed - Yes (/usr/bin/esd)
      Running - No

Jack:
      Installed - Yes (/usr/bin/jackd)
      Running - No


!!Soundcards recognised by ALSA
!!-----------------------------

 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfde38000 irq 41

---

### Post by strask on 2012-04-23
Hello. I'm having trouble following the instructions in the sound troubleshooting guide under procedure Ae: Make NVIDIA HDMI audio work.

I've got the NVIDIA proprietary drivers installed, and 'aplay -l' output looks correct, but the next step in the guide says to do this```
grep "eld_valid *1" /proc/asound/NVidia/eld*
``` and that produced no output for me. So I tried this```
trask@reptoid:~$ grep eld_valid /proc/asound/NVidia/eld*
/proc/asound/NVidia/eld#0.0:eld_valid        0
/proc/asound/NVidia/eld#1.0:eld_valid        0
/proc/asound/NVidia/eld#2.0:eld_valid        0
/proc/asound/NVidia/eld#3.0:eld_valid        0
trask@reptoid:~$ 
```The rest of the procedure in the guide assumes that one of those lines should have a 1, rather than a 0, so I don't know how to proceed.

As a side note, I had some display problems after installing the NVIDIA drivers until I discovered the NVIDIA X Server config tool (see [http://ubuntuforums.org/showthread.php?t=1963767](http://ubuntuforums.org/showthread.php?t=1963767)) so whoever maintains the troubleshooting guide might want to add a clue about that. :)


EDIT: Solved! Upgraded to 12.04 and problem went away, now have full use of HDMI audio.

---

### Post by Normand on 2012-04-28
As described Previously: I got alsamixer and found my sound card, but without having sound.

Now my situation has got worse:
- I have retried the steps in both the 'guide' and the 'procedure' many times, before and then after ...
- instalation of the DKMS

Now in the terminal:
- alsamixer is not recognised
- aplay -l   says no sound cards found
There seems to bre no Alsa driver installed

I'm really stuck ... help !

---

### Post by GuiGuy on 2012-04-28
None of the advice offered here helped. I have installed mythbuntu 12.04.

Sound works fine in mythtv live, mythvideo and mythmusic. 

Sound works in VLC as you'd expect. 

SOund **does not work** in

[LIST]
[*]External audio players (banshee etc)
[*]external video players, other than VLC
[*]mythweb
[*]firefox, chrome etc browsers
[/LIST]

Any helpful advice gratefully acknowledged...

NB: Sound is over HDMI (SPDIF). I suspect that those players not working are using the analogue card rather than HDMI.


Thanks

---

### Post by waxcan on 2012-04-28
Arrive in silence
Read
Apply
Win
Leave blastin metal!
I LOVE the forums!!!!:guitar:

---

### Post by Normand on 2012-04-29
Thanks Waxcan for the reminder.

I did the Upgrade Alsa scripts on   [http://ubuntuforums.org/showthread.php?t=1681577](http://ubuntuforums.org/showthread.php?t=1681577)    (Thanks Temüjin)

Now:
- The driver, libraries and utilities versions of alsa are all 1.0.25
- Running alsamixer only brings up the master slider column, nothing else
- Running aplay ... it just hangs there and does nothing
- aplay -l    shows the sound card is being recognised
- I still have no sound

---

### Post by SPARTAN-118 on 2012-04-29
Really odd stuff going around here...
Fresh install of 12.04. Sound seemed to work perfectly the first time I booted, though I wasn't really paying attention.

Here are my issues:

[LIST]
[*]5.1 setup, front left/right speakers dead, all sound directed through the centre speaker.
[*]Random, frequent, loud popping/crackling noises coming from speakers when music is playing in Rhythmbox.
[*]Tried the very first Terminal command in the first guide linked, ```
speaker-test
``` but when it started the front left test, the static came out of the centre speaker.
[/LIST]
I will edit this post if more issues come up (from doing the tests in the guides).

EDIT: Okay, sometime during the second guide I noticed that my front speakers were working again. Playing some music, I didn't notice any more popping. That may change, but the important thing is, my speakers work again. And the sound isn't getting shoved to the centre speaker.

Why is it that, when posting here, I almost invariably find the answer on my own?

EDIT 1: **Crackling/popping still occurs while playing music.** It was fine after a reboot, but after watching a few episodes of a TV show on VLC (which, I might add, went rather smoothly) I played some songs in Rhythmbox... and it's back.

Anybody know a solution? Besides giving up on Linux, because it lacks proper support from manufacturers?

---

### Post by Normand on 2012-05-09
To close my bits for now:

I have done a clean install yesterday of 12.04 with all updates and going through these guides again

Alsamixer works ... soundcard recognised in aplay -l

BUT !!ALSA Version
!!------------

Driver version: 1.0.24
Library version: 1.0.25
Utilities version: 1.0.25

No sound on front jack but I have it on the back panel.

I can live happily with this. Thanks to all working on these things.

---

### Post by aim2help on 2012-05-09
I had a really great and stable sound system on 10.10 and then I had an issue with my boot block so I put in a new drive and upgraded to 11.10 ... BIG MISTAKE!

I've spent a week going through every forum and fix ... nothing works! Yes I have sound but it is broken and distorted. Video software also doesn't work (which used to be great) :(Not happy! 

I'm considering dumping Ubuntu and going back to another flavour of Linux:(

---

### Post by mörgæs on 2012-05-09
It's always good to try more than one distro, but before deciding what to do you should test a live boot of one of the 12.04 Buntus.

---

### Post by lnxChoBo on 2012-05-10
I just installed 12.04 clean on my computer.  I have video, but no sound.  When the computer is booting there are a few audio pops through the speaker but no sound at all after that.

I am running hdmi cable from video card (nvidia geforce 9800 GTX) into my receiver, and a hdmi cable to my tv.

I do not get any option in my sound settings to choose HDMI output.  It looks like it is set to use the build in Realtek audio from my motherboard, but doesn't give an option to set as hdmi.

not sure what to do next :(  thanks for any help!

Edit:  Reading through some posts on here I think I may not have connected the SPDIF header from video card to mobo.  will try that tonight and hope to see HDMI options in sound prefs.

---

### Post by khairulnizam on 2012-05-11
Sorry if out of topic.

When I connect a jack and run Rakarrack, the sound distort. I open Gnome-Alsa Mixer to check the sound and increased the Mic volume but then the sound distort. Please help to fix this. thanks.

---

### Post by BrelpBapeSort on 2012-05-11
Hi,i have a problem with my new graphic-card Club3d-GT240.I connected a Samsung TV via HDMI and i cant activate sound via the HDMI-Interface.I tried GnomePlayer and VLC and set the audio output to alsa, because this option provides HDMI in the settings only.I enabled the "High Definition Audio Controller" in the sound preferences instead of the internal sound card.Is there any idea what the reason could be?thank you for your helpsorry, i forgot : i use mint 10 with gnome

---

### Post by SPARTAN-118 on 2012-05-13
By the way, I did end up fixing my sound issues.

The solution is this: fiddle around with your sound levels in Sound Preferences, selecting different output devices (preferably one that doesn't actually do anything, like an S/PDIF output if your mobo doesn't actually have one) until the settings reset. Then you just double-check to make sure you've selected the device you actually **want**, check again that the volume isn't above "Unamplified", and presto! Your crackling issues are fixed! For a while, anyway...

Sound in Linux is never simple, but hey, at least it works!

---

### Post by Graham C Williams on 2012-05-18
Ubuntu 12.04 64bit on Acer Aspire 8930G and Aspire 8935G.

Sound from:
1) the Headphone socket only - nothing from the speakers
or
2) (8935G Only) Sound from everything at once.

I have the systems setup for the first option.

Both systems use the GNOME3 frontend.
Since the initial setup I have taken the 8935g back to ubuntu 11.10 64bit. The 8930G remains with 12.04 64bit.

Many people are having similar problems so I guess work is being done and we'll see a resolution in the near future.

Graham

---

### Post by SPARTAN-118 on 2012-05-20
Had to install a new motherboard yesterday and when I boot into Ubuntu (after trying to fix problems caused by updates) the left speaker is the only one out of my 5.1 setup that works. That is, the sound for the right and left front speakers is channelled into the left one. The centre and rear speakers don't work at all.

Tried the troubleshooting guides listed in OP but they didn't work, or at least, the first one listed didn't (tried some of the second guide, but can't do it all right now).

Anyone have a suggestion?

**EDIT: **Well, that was embarrassing. Turns out the green jack wasn't fully plugged in all the way, which is why the right speaker wasn't working.
But that still doesn't explain why neither the rear nor centre speakers are working. Is it something I have to change in my BIOS settings? Shouldn't it automatically switch to outputting surround sound instead of using those ports as inputs?

---

### Post by AbeFM on 2012-05-20
I've given a quick look at the guides in this thread, if you think I need to run through them to give you more info, say the word and I'll run them... But perhaps something will sound familiar enough to you.

My system started as 10.04 and has followed the routine upgrades to 12.04. The system was built for this, a intel i3 with a Zotac H67ITX-C-E (H67 chipset). I've done several fresh installs, and always have the same issue:

After some indeterminate amount of time/interaction/sounds, I'll find the LFE (the .1 from my 5.1) channel no longer playing. Going into the sound controls and selecting most anything (even a non- bass channel system like 4.0) will instantly find the sub-woofer working again. As you can imagine, the ultimate home theater isn't that great when I have to get up and tweak the settings twice a night.

Anyway, now on the fresh 12.04 install, I'm also getting very high frequency noise, like when WINE used to have ALSA issues on my other desktop. I could believe it to be bit shifting on the outputs - least significant bits making a high frequency output on the highest volumes - but it could be something else entirely. 

This kinda sneaks in, and sometimes muting and unmuting fixes it. If not, even running alsamixer won't fix it. Interestingly, switching to 4.0 (which gives me 4.1 sound) does fix it, going back to 5.1 restores everything.

Does anyone have any suggestions? This issue has been going on for years, but as it was only dropping base, I didn't care. Now that it's endangering my speakers and my relationships, I need to do something. It seems to happen after a couple hours of listening to music.

--> If this has been covered and I missed it, please point me to where I can read up on it. Thank you.

THANKS!!!
            -Abe.
__________
System Summary:
Ubuntu 12.04 (clean install, issues present before)
Intel i3 2600t
Zotac H67ITX-C-E (H67 chipset, 2nd motherboard, same symptoms)
5.1 sound hooked up through analog outs

The closest I could find was [http://www.thinkwiki.org/wiki/Problem_with_audio_clipping](http://www.thinkwiki.org/wiki/Problem_with_audio_clipping) about Z68 boards, but it's not really clipping per se.

---

### Post by Yellow Pasque on 2012-05-21
> **SPARTAN-118 said:**
> Shouldn't it automatically switch to outputting surround sound instead of using those ports as inputs?

You may have to use: [http://voices.canonical.com/david.henningsson/2011/11/29/turn-your-mic-jack-into-a-headphone-jack/](http://voices.canonical.com/david.henningsson/2011/11/29/turn-your-mic-jack-into-a-headphone-jack/)

---

### Post by AbeFM on 2012-05-21
Any suggestions at all? Installing 11.10 again seems like a kinda ridiculous answer, but I can't just listen to music anymore and that's unacceptable as well.  PLEASE HELP!

---

### Post by SPARTAN-118 on 2012-05-21
> **Temüjin said:**
> You may have to use: [http://voices.canonical.com/david.henningsson/2011/11/29/turn-your-mic-jack-into-a-headphone-jack/](http://voices.canonical.com/david.henningsson/2011/11/29/turn-your-mic-jack-into-a-headphone-jack/)

Hi, thanks for the suggestion. I tried it, but I can only get Centre/LFE to work, not the rear channels, and the front speakers are considerably louder than the centre one. Not sure if that's intended behaviour, but nonetheless, my problem is still not resolved.

I also tried changing stuff around in alsamixer, but the only thing I could do was make the front speakers quieter by lowering the PCM volume.

@AbeFM: Sorry to hear you're having all those troubles, unfortunately, I've found sound in Linux to always be an issue for me, at least on my desktop, whether it's crackling like you seem to be having (old mobo) or some speakers flat out not working (new mobo).

I wish I could help, really, I do, but I just don't have enough experience.

---

### Post by AbeFM on 2012-05-21
Out of curiosity, have you messed much with the GUI part of the set up? In the distant past I had to resort to the commandline, but as silly as it sounds, just selecting and reselecting items in the GUI sometimes makes them work - in the 11.xx system, there were overlapping settings, at times trying them all made it work. Anyway, you might just want to step through "2.0, 2.1, 4.0, 4.1, 5.0, 5.1" until you get some love? There are also independant volumes for each channel (I read somewhere the LFE has 10db taken out of it in some places, I just turn it all the way up in the GUI's mixer and it's fine).

The "crackling" is some of that, but also very, very loud beeping, short, >5khz bursts perhaps 250-700ms long. Certainly a "digital" sound if you know what I mean.

I guess what bothers me are the people who tell me it's fine - I'm all for supporting open source software, but don't tell me it's BETTER than windoze if it can't do basic things. Bring up that it doesn't work and people ignore it. I'm willing to put in some effort in fixing it, but pretending my problem doesn't exist is a disservice to the cause. Keeping my fingers crossed.

You're sure you're in the right ports, and other simple stuff?

---

### Post by GuiGuy on 2012-05-22
> **AbeFM said:**
> 
Does anyone have any suggestions? 


Sorry, not me; my mythtv box sound went down yesterday. I spent the best part of 20 hours trawling, reading, removing, installing, purging, re-installing, tolerating the fanbois, all to no avail.

In the end, yet another clean install. As usual the useless linux back up files failed, but at least I have sound back.

**I suspect there are a bunch of masochists in the linux backrooms working out yet more ways of making our lives a misery with the useless sound software... I need to open a Window...:( **

I despair.

---

### Post by AbeFM on 2012-05-22
Maybe break it down:
Has anyone seen the LFE channel in 5.1 analog out shut off, only to come back when one selects "4.0" from the sound setup dialog, and what does that tell me this is doing?

If you need more information, please just ask.

---

### Post by SPARTAN-118 on 2012-05-24
Sorry, forgot to check back here as I've been busy and I guess I turned off email notifications. :-/

Anyway, yes, I "messed around in the GUI" as you put it, in fact that's all I did. The Advanced panel looks too complicated and I'm scared of changing stuff and making it worse than it already is, so I'll just wait until somebody tells me to go in there.

As for CLI, I'm still learning to do more basic stuff (like batch moving files) that way, I'm starting to get the hang of it, but of course being a longtime Windows user (I've used Linux on/off for many years, but who can escape the ever-reaching grasp of M$?) I never really needed to do stuff with command line, only when I was messing around with replacing system files (for theming, etc.) and had to close explorer while doing so.

As for sound in Linux... as a good friend of mine put it, Linux has such a small market share compared to Windows that it's often not worth a manufacturer's time to provide support for it. That, and there are just so many distributions it'd be far too much effort to even try. (Okay, I'm paraphrasing him here, but you get the point.)

> **GuiGuy said:**
> **I suspect there are a bunch of masochists in the linux backrooms  working out yet more ways of making our lives a misery with the useless  sound software... I need to open a Window...:sad: **
  
Just FYI, masochist is someone who enjoys receiving pain, while sadist refers to someone who enjoys inflicting pain on others. So, the correct term would be sadist. I realize it's extremely nitpicky and off-topic, but I often can't help it. Sorry.
Also, I See What You Did There.

---

### Post by GuiGuy on 2012-05-24
> **SPARTAN-118 said:**
> 

Just FYI, masochist is someone who enjoys receiving pain, while sadist refers to someone who enjoys inflicting pain on others. So, the correct term would be sadist. I realize it's extremely nitpicky and off-topic, but I often can't help it. Sorry.
Also, I See What You Did There.

My bad and it serves me right. I can be the worst of pedants ;)

BTW, while my problems haven't gone away (I only have sound in mythtv, nothing else), I came across an interesting issue;

My screen which receives the HDMI input provides for Dolby Digital and PCM audio. To get the sound to work at all out of mythtv I need to set the screen's audio to Dolby Digital and in MythTV Frontend > Setup > Audio enable Dolby Digital.

If the screen's audio is PCM it works but at very low gain. 

So with HDMI it seems that the receiver's settings may also impact. 

Cheers

---

### Post by AbeFM on 2012-05-25
GUI:
Now that I definitely saw - complaints about the sub coming out 10db quieter than everything else. Apparently there's a disagreement over the standard for who's supposed to set the volume of that - the amplifier is supposed to, but not everyone does. Whatever. Even in analog, I just go into settings and put the woofer up to near max.

Which of course makes it more frustrating that it's often not present. Well, I've tried to get "support", time to report a bug. Hopefully those people actually care.

---

### Post by SPARTAN-118 on 2012-05-25
Well, once I finally figure out how to burn files split using the  "split" command to multiple DL discs, I'm going to reinstall Ubuntu  (fresh install) to my other, 500 GB hard drive. Perhaps that'll be what I  need to get everything working again. I don't know if Ubuntu keeps anything in the system that may affect it if hardware is swapped out (like Windows does, only it breaks if you change a key component like, say... a mobo) but I have to do it anyway so fingers crossed!

AbeFM, good to hear you filed a bug, while the forums are often a great source of help, sometimes you just need a developer to look at this stuff...
out of curiosity, have you tried Ask Ubuntu yet? I think you may have mentioned it earlier but I'm not entirely sure and I'm too busy right now to check :D

---

### Post by AbeFM on 2012-05-26
Haven't tried it yet. My glitching sound didn't happen all day yesterday (not sure what sets it off. Perhaps it's running wine applications since the last reboot?) but the bass channel still disappeared on me, several times during a single movie. I feel this information separates two effects and makes it easier to diagnose....

...but I also feel no one with the faintest clue what's going on is reading here. The blind leading the blind.

---

### Post by GuiGuy on 2012-05-27
> **SPARTAN-118 said:**
>  I don't know if Ubuntu keeps anything in the system that may affect it if hardware is swapped out (like Windows does, only it breaks if you change a key component like, say... a mobo) but I have to do it anyway so fingers crossed!


I have changed MOBOs in the past without too many problems and rebooted from existing hard disk drives. The main trick is to drop the video display back to something basic before making the change. My most recent upgrade was a couple of weeks ago when I swapped the boards on my file server running soft RAID. Everything bounced back fine, except....

... audio. It is always the audio :(

---

### Post by AbeFM on 2012-05-27
> **GuiGuy said:**
> My most recent upgrade was a couple of weeks ago when I swapped the boards on my file server running soft RAID. Everything bounced back fine, except....

... audio. It is always the audio :(

When installing a windows machine for some workstation programs, I couldn't download the network drivers since the network wasn't working. Solution? Boot off ubuntu install from another machine. Worked fine.

The sound for me is consistently bad. Not random, it's been repeatable for years across several versions of the OS and hardware.

It's funny all this work goes into making GUI candy when basics like "I turn on computer, can't get sound working" keeps the OS from wide distribution.

Really, would you recommend a car to a friend where the parking brake just never worked? It's a basic thing, and getting the bare essentials working should be a requirement.... ESPECIALLY when people like us are willing to put in the hours to provide developers with ANY information they need.

---

### Post by SPARTAN-118 on 2012-05-27
> **AbeFM said:**
> When installing a windows machine for some workstation programs, I couldn't download the network drivers since the network wasn't working. Solution? Boot off ubuntu install from another machine. Worked fine.

The sound for me is consistently bad. Not random, it's been repeatable for years across several versions of the OS and hardware.

It's funny all this work goes into making GUI candy when basics like "I turn on computer, can't get sound working" keeps the OS from wide distribution.

Really, would you recommend a car to a friend where the parking brake just never worked? It's a basic thing, and getting the bare essentials working should be a requirement.... ESPECIALLY when people like us are willing to put in the hours to provide developers with ANY information they need.

I agree. Speaking of the GUI, I had to switch to Lubuntu because Unity (Compiz) kept crashing with the Nvidia drivers *that came with the install CD.*
And they call 12.04 a long-term support distro? You're gonna need it.
(I have no idea if sound works right yet, as there's no control panel to test the speakers from like in Ubuntu. I'll have to use VLC or something to test it out.)

---

### Post by Inglonias on 2012-06-16
Motherboard: Gigabyte EP-35-DS3L

I just installed the latest version of Ubuntu (12.04) on this computer, and I am not getting any kind of sound. I have tried going through the stickied sound troubleshooting procedure with no luck. Does anybody have any idea what might be wrong?

---

### Post by Superserial on 2012-07-04
Sound support as far as I am concerned in Linux is absolutely awful. Someone broke it in one of the updates in 11.10 and several months later nothing changed.

I tried 3 different soundcards on 2 machines. One is some several year old AC97 (prolly Via or Realtek), works fine on vanilla 11.10 but as soon as I do update sound degrades, starts crackling and is overall terrible.

Second machine has intergrated Realtek ALC850 which gets no sound and no ammount of trying to edit helps it.

The same machine also has SBLive 5.1, same poor crackling, low volume, terrible sound after one of the updates in 11.10.

So 3 out of 3 soundcards = fail.
I tried Lubuntu/Xubuntu and the awful Ubuntu. I removed pulseaudio entirely, edited various config files. Played with mixers. Nothing helps.

---

### Post by AbeFM on 2012-07-04
You'd think they'd just put the old code back in. While there's lots of eye candy, my computer is less functional as a computer with each release. Drives don't spin down, sound doesn't work, cd tray cycles randomly, pinching discs... I remember back in the old days where the computer just sorta worked.

All I want to do is serve files and show my friends movies once in a while, instead I'm constantly monkeying around like it's a classic car broken down on the side of the road.

Take the stuff that's known broken and necessary for a computer to be considered "functional" and just fix it. I've offered time after time to spend as much time as it takes to do diagnostics to help the people writing the code figure it out, but it falls on deaf ears.

---

### Post by GuiGuy on 2012-07-05
> **AbeFM said:**
> You'd think they'd just put the old code back in. While there's lots of eye candy, my computer is less functional as a computer with each release. Drives don't spin down, sound doesn't work, cd tray cycles randomly, pinching discs... I remember back in the old days where the computer just sorta worked.

Maybe try another distro? I've dropped 'ubuntu in favour of Linux Mint & its cinnamon desktop. WHile LM is, AFAIK, based on Ubuntu, it seems to do everything just so much better. Audio works, it boots smartly, seems well behaved. And oddly, I am getting proper USB2 throughput speed for the first time since Karmic Koala. 

That said, you're right about the poor power management. Given the times, it is pathetic.

---

### Post by javimixet on 2012-07-06
Hi everyone... not sure if my problem fits here, so please redirect me if it's the case.

I have sound, my problem is that one of my devices (vx222) freezes completely the computer (no keyboard response, no caps/nums bloq response) when i run jack with it as device. The card was not recognized out of the box by ubuntu studio 12.04, i had to install alsa-firmware, and alsa-drivers, alsa-tools, etc... and after doing that and reboot, the system freezed just after login... searching I found that deactivating pulseaudio (via ~/pulse/client.conf ospawn=noaut) could help, and it do, now I can use the device for listen audio and control it via alsa-mixer, but when I try to use it with jack, or reactivate pulseaudio, all get freezed.

Thanks for your help and sorry for my poor english.

---

### Post by dewdrop_world on 2012-07-12
I woke up my computer this morning to find that the built-in audio output was not making any sound, both using headphones plugged into the phone out and also with everything unplugged trying to use the laptop speakers. It was fine yesterday. After a reboot, it was still broken.

The first troubleshooting guide had nothing relevent. I had already tried all that. I have a USB soundcard and I *can* do aplay -d hw:1 something.wav - but -d hw:0 is silent.

So I'm starting on the second troubleshooting guide. That's rather invasive, isn't it? Reinstall a boatload of packages, which has the chance of breaking who-knows-what?

Is there any harm in keeping the PPA versions of these packages? The guide doesn't say.

If it's better to use the standard packages, the guide doesn't have instructions to revert.

Nonetheless, I'm trusting... and desperate to figure out why the built-in sound is fubarred.

Will post the debugging info from the second guide when I have it.

James

---

### Post by dewdrop_world on 2012-07-12
> **dewdrop_world said:**
> I woke up my computer this morning to find that the built-in audio output was not making any sound, both using headphones plugged into the phone out and also with everything unplugged trying to use the laptop speakers. It was fine yesterday. After a reboot, it was still broken.

False alarm -- somehow the speaker got muted, and didn't un-mute after pulling out the headphone jack. That's fixed now and the audio is working as I expect.

The one thing that doesn't make sense is that I still didn't get sound through the headphones, even though the headphone channel was not muted. But it's working now, so I'm prepared to let that question go.

The second troubleshooting guide asked me to install a lot of packages, which I did. Should I just leave those packages in place, or would it be better to roll back to the packages that were there before?

James

---

### Post by adelattre on 2012-07-17
I'm trying to use a Logitech H530 usb headset on my Thinkpad Edge13 running ubuntu 12.04 64 bit, and the automatic mic gain keeps pushing the mic volume to 100% [so, the volume is WAY too loud and picks up lots of background noise etc], even as I've turned it down in alsamixer and pulseaudio.  I've searched, but been unable to find anything about how to disable the auto mic gain or otherwise fix this problem.  
sound card is:
andre@andre-ThinkPad-Edge:~$ lspci | grep -i audio
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)

Any advice would be appreciated.
Thanks.

---

### Post by Anivair on 2012-08-03
Much like many folks on ye olde internets, I seem to have no sound at all.  I'm running Ubuntu 12.04 and I just updated it today to the most recent packages. 

My sound card is recognized just fine (Creative Labs CA0106 Soundblaster).  Alsamixer runs and nothing is muted (everything is at 100%.  there is no auto-mute option on my version).  aplay -l shows my card just fine and it seems to be okay. pavucontrol runs fine and i see my stuff. Under configuration I've tried all the potions.  I tend to stick with Amalog Stero Duplex for testing (I'm using logitech sl21 speakers). 

Everything seems to be as it should. Yes no sound. 

The speakers work fine (tested on my phone, they sound great).  I can get sound just fine out of usb speakers, but I'd rather use my actual sound card (it's a card, not on board.  my mobo has no on board sound).  

It's never worked on 12.04.  

Suggestions?

---

### Post by redsprite on 2012-08-05
hey everyone,
 
I recently upgraded to ubuntu 12.04 but  just after updating  grub i lost sound so
i have tried theese 2 links :

[https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)
[https://docs.google.com/document/d/1iTlJ8BfqXUjaHO__TEdlkvuqB1WLOkGaudngc5SFLMI/edit?pli=1](https://docs.google.com/document/d/1iTlJ8BfqXUjaHO__TEdlkvuqB1WLOkGaudngc5SFLMI/edit?pli=1)

without result 

 Accordingly  to second link i found that the 
/etc/asound.conf was empty then i paste this code
----     code  -------
 pcm.!default {  
[LIST]
[*]type plug slave.pcm { 
[LIST]
[*]type hw card 0 device 1
[/LIST]
}
[/LIST]
 }
 --------------------------------------------
  where i have the crad and device numbres  ( card 0 device 1 )from this comand : aplay-l 
  
 but without result.
 

 My  ALSA information is located at [http://www.alsa-project.org/db/?f=09dcab500ad7ce35734659ea1779dc09209d35cf](http://www.alsa-project.org/db/?f=09dcab500ad7ce35734659ea1779dc09209d35cf)
 

 and here is the full terminal output for this command : 

 

 "cat /proc/asound/{version,cards,devices,hwdep,pcm,seq/clients}; sudo  rm /etc/asound.conf; sudo rm -r ~/.pulse ~/.asound* ;sudo rm  ~/.pulse-cookie; sudo apt-get update; sudo apt-get install aptitude;  sudo aptitude install paman gnome-alsamixer libasound2-plugins  padevchooser libsdl1.2debian-pulseaudio; sudo lshw -short;ls -lart  /dev/snd;  cat /dev/sndstat; lspci -nn; lsusb; sudo which alsactl; sudo  fuser -v /dev/dsp /dev/snd/* ; dpkg -S bin/slmodemd; dmesg | egrep  'EMU|probe|emu|ALSA|alsa|ac97|udi|snd|ound|irmware'; sudo  /etc/init.d/sl-modem-daemon status; sudo grep model /etc/modprobe.d/* ;  sudo dmidecode|egrep 'anufact|roduct|erial|elease'; lsmod | egrep  'snd|usb|midi|udio'; aplay -l; sudo alsa force-reload; sudo lshw -C  sound"
 

 terminal output :
 

 H/W path               Device     Class       Description
=========================================================
                                  system      Desktop Computer
/0                                bus         945GCM-S2L
/0/0                              memory      128KiB BIOS
/0/4                              processor   Intel(R) Pentium(R) 4 CPU 3.00GHz
/0/4/8                            memory      16KiB L1 cache
/0/4/9                            memory      1MiB L2 cache
/0/4/1.1                          processor   Logical CPU
/0/4/1.2                          processor   Logical CPU
/0/17                             memory      3GiB System Memory
/0/17/0                           memory      2GiB DIMM 667 MHz (1,5 ns)
/0/17/1                           memory      1GiB DIMM 667 MHz (1,5 ns)
/0/100                            bridge      82945G/GZ/P/PL Memory Controller Hub
/0/100/2                          display     82945G/GZ Integrated Graphics Controller
/0/100/1b                         multimedia  N10/ICH 7 Family High Definition Audio Controller
/0/100/1c                         bridge      N10/ICH 7 Family PCI Express Port 1
/0/100/1c.1                       bridge      N10/ICH 7 Family PCI Express Port 2
/0/100/1c.1/0          eth0       network     RTL8111/8168B PCI Express Gigabit Ethernet controller
/0/100/1d                         bus         N10/ICH 7 Family USB UHCI Controller #1
/0/100/1d.1                       bus         N10/ICH 7 Family USB UHCI Controller #2
/0/100/1d.2                       bus         N10/ICH 7 Family USB UHCI Controller #3
/0/100/1d.3                       bus         N10/ICH 7 Family USB UHCI Controller #4
/0/100/1d.7                       bus         N10/ICH 7 Family USB2 EHCI Controller
/0/100/1e                         bridge      82801 PCI Bridge
/0/100/1f                         bridge      82801GB/GR (ICH7 Family) LPC Interface Bridge
/0/100/1f.2            scsi0      storage     N10/ICH7 Family SATA Controller [IDE mode]
/0/100/1f.2/0.0.0      /dev/sda   disk        164GB Hitachi HDS72161
/0/100/1f.2/0.0.0/1    /dev/sda1  volume      98GiB Extended partition
/0/100/1f.2/0.0.0/1/5  /dev/sda5  volume      52GiB HPFS/NTFS partition
/0/100/1f.2/0.0.0/1/6  /dev/sda6  volume      45GiB Linux filesystem partition
/0/100/1f.2/0.0.0/2    /dev/sda2  volume      2863MiB Linux swap volume
/0/100/1f.2/0.0.0/3    /dev/sda3  volume      52GiB EXT3 volume
/0/100/1f.3                       bus         N10/ICH 7 Family SMBus Controller
/0/1                   scsi2      storage     
/0/1/0.0.0             /dev/sdb   disk        4004MB SCSI Disk
/0/1/0.0.0/1           /dev/sdb1  volume      3818MiB Windows FAT volume
total 0
crw-rw---T+  1 root audio 116, 33 août   5 23:28 timer
crw-rw---T+  1 root audio 116,  1 août   5 23:28 seq
crw-rw---T+  1 root audio 116,  2 août   5 23:28 pcmC0D2c
crw-rw---T+  1 root audio 116,  6 août   5 23:28 hwC0D2
crw-rw---T+  1 root audio 116,  7 août   5 23:28 controlC0
drwxr-xr-x   2 root root       60 août   5 23:28 by-path
drwxr-xr-x   3 root root      220 août   5 23:28 .
crw-rw---T+  1 root audio 116,  4 août   6 00:16 pcmC0D0p
crw-rw---T+  1 root audio 116,  5 août   6 00:16 pcmC0D0c
crw-rw---T+  1 root audio 116,  3 août   6 00:16 pcmC0D1p
drwxr-xr-x  16 root root     4280 août   6 00:18 ..
cat: /dev/sndstat: No such file or directory
00:00.0 Host bridge [0600]: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub [8086:2770] (rev 02)
00:02.0 VGA compatible controller [0300]: Intel Corporation 82945G/GZ Integrated Graphics Controller [8086:2772] (rev 02)
00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 01)
00:1c.0 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 1 [8086:27d0] (rev 01)
00:1c.1 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 2 [8086:27d2] (rev 01)
00:1d.0 USB controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 [8086:27c8] (rev 01)
00:1d.1 USB controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 [8086:27c9] (rev 01)
00:1d.2 USB controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 [8086:27ca] (rev 01)
00:1d.3 USB controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 [8086:27cb] (rev 01)
00:1d.7 USB controller [0c03]: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller [8086:27cc] (rev 01)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev e1)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge [8086:27b8] (rev 01)
00:1f.2 IDE interface [0101]: Intel Corporation N10/ICH7 Family SATA Controller [IDE mode] [8086:27c0] (rev 01)
00:1f.3 SMBus [0c05]: Intel Corporation N10/ICH 7 Family SMBus Controller [8086:27da] (rev 01)
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd.  RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev  02)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0781:5567 SanDisk Corp. Cruzer Blade
/sbin/alsactl
Specified filename /dev/dsp does not exist.
                     USER        PID ACCESS COMMAND
/dev/snd/controlC0:  sssf       3197 F.... pulseaudio
/dev/snd/pcmC0D1p:   sssf       3197 F...m pulseaudio
dpkg-query: no path found matching pattern *bin/slmodemd*.
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000] found SMP MP-table at [c00f4c70] f4c70
[    0.211679] ACPI: No dock devices found.
[    0.211712] HEST: Table not found.
[    0.342219] pnp: PnP ACPI: found 15 devices
[    0.396278] audit: initializing netlink socket (disabled)
[    0.396341] type=2000 audit(1344209244.392:1): initialized
[    0.551806] ERST: Table is not found!
[    0.916899] isapnp: No Plug & Play device found
[    1.283502] Fixed MDIO Bus: probed
[    1.284078] ehci_hcd 0000:00:1d.7: using broken periodic workaround
[    1.300262] hub 1-0:1.0: USB hub found
[    1.300822] hub 2-0:1.0: USB hub found
[    1.301291] hub 3-0:1.0: USB hub found
[    1.301769] hub 4-0:1.0: USB hub found
[    1.302271] hub 5-0:1.0: USB hub found
[    1.328229] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   48.750267] lp: driver loaded but no devices found
[   48.964335] leds_ss4200: no LED devices found
[   49.134686] type=1400 audit(1344205694.301:2): apparmor="STATUS"  operation="profile_load" name="/sbin/dhclient" pid=597  comm="apparmor_parser"
[   49.137697] type=1400 audit(1344205694.305:3): apparmor="STATUS"  operation="profile_load"  name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=597  comm="apparmor_parser"
[   49.139072] type=1400 audit(1344205694.305:4): apparmor="STATUS"  operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script"  pid=597 comm="apparmor_parser"
[   50.051667] snd_hda_intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   50.051763] snd_hda_intel 0000:00:1b.0: irq 43 for MSI/MSI-X
[   50.051812] snd_hda_intel 0000:00:1b.0: setting latency timer to 64
[   50.138538] input: HDA Intel Line as /devices/pci0000:00/0000:00:1b.0/sound/card0/input3
[   50.155202] input: HDA Intel Front Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input4
[   50.155396] input: HDA Intel Rear Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input5
[   50.161843] input: HDA Intel Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input6
[   50.164791] input: HDA Intel Line Out as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
[   64.949377] type=1400 audit(1344205710.117:5): apparmor="STATUS"  operation="profile_replace" name="/sbin/dhclient" pid=1321  comm="apparmor_parser"
[   64.950367] type=1400 audit(1344205710.117:6): apparmor="STATUS"  operation="profile_replace"  name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1321  comm="apparmor_parser"
[   64.951582] type=1400 audit(1344205710.117:7): apparmor="STATUS"  operation="profile_replace"  name="/usr/lib/connman/scripts/dhclient-script" pid=1321  comm="apparmor_parser"
[   64.957701] type=1400 audit(1344205710.125:8): apparmor="STATUS"  operation="profile_load"  name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=1320  comm="apparmor_parser"
[   64.984754] type=1400 audit(1344205710.153:9): apparmor="STATUS"  operation="profile_load" name="/usr/bin/evince" pid=1322  comm="apparmor_parser"
[   65.002998] type=1400 audit(1344205710.169:10): apparmor="STATUS"  operation="profile_load" name="/usr/lib/firefox/firefox{,*[^s][^h]}"  pid=1323 comm="apparmor_parser"
[   65.010902] type=1400 audit(1344205710.177:11): apparmor="STATUS"  operation="profile_load" name="/usr/bin/evince//launchpad_integration"  pid=1322 comm="apparmor_parser"
[   65.012146] type=1400 audit(1344205710.181:12): apparmor="STATUS"  operation="profile_load"  name="/usr/lib/firefox/firefox{,*[^s][^h]}//browser_java" pid=1323  comm="apparmor_parser"
[   65.014493] type=1400 audit(1344205710.181:13): apparmor="STATUS"  operation="profile_load" name="/usr/bin/evince//sanitized_helper"  pid=1322 comm="apparmor_parser"
[   65.017056] type=1400 audit(1344205710.185:14): apparmor="STATUS"  operation="profile_load"  name="/usr/lib/firefox/firefox{,*[^s][^h]}//browser_openjdk" pid=1323  comm="apparmor_parser"
[   65.418985] apm: BIOS not found.
[   77.205110] vboxdrv: Found 2 processor cores.
[   77.269497] vboxpci: IOMMU not found (not registered)
sudo: /etc/init.d/sl-modem-daemon: command not found
    Release Date: 12/27/2007
        Serial services are supported (int 14h)
    Manufacturer: Gigabyte Technology Co., Ltd.
    Product Name: 945GCM-S2L
    Serial Number:  
    Manufacturer: Gigabyte Technology Co., Ltd.
    Product Name: 945GCM-S2L
    Serial Number:  
    Manufacturer: Gigabyte Technology Co., Ltd.
    Serial Number:  
    Manufacturer: Intel
    Serial Number:  
    Port Type: Serial Port 16450 Compatible
    Port Type: Serial Port 16450 Compatible
    Manufacturer: None
    Serial Number: None
    Manufacturer: None
    Serial Number: None
snd_seq_dummy          12686  0 
snd_hda_codec_realtek    63371  1 
snd_hda_intel          32364  5 
snd_hda_codec         111551  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  3 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  3 snd_seq_dummy,snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  4 snd_seq_dummy,snd_seq_midi,snd_rawmidi,snd_seq
snd                    62064  18  snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              14635  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
usb_storage            39646  1 
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC662 rev1 Digital [ALC662 rev1 Digital]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
Unloading ALSA sound driver modules: snd-seq-dummy snd-hda-codec-realtek  snd-hda-intel snd-hda-codec snd-hwdep snd-pcm snd-seq-midi snd-rawmidi  snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc  (failed: modules still loaded: snd-hda-codec-realtek snd-hda-intel  snd-hda-codec snd-hwdep snd-pcm snd-timer snd-page-alloc).
Loading ALSA sound driver modules: snd-seq-dummy snd-hda-codec-realtek  snd-hda-intel snd-hda-codec snd-hwdep snd-pcm snd-seq-midi snd-rawmidi  snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc.
  *-multimedia            
       description: Audio device
       product: N10/ICH 7 Family High Definition Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=snd_hda_intel latency=0
       resources: irq:43 memory:d11c0000-d11c3fff
 
 Any help is much appreciated!

---

### Post by redsprite on 2012-08-05
now sound works like a charme on kernel 3.0.0.16 but still didn't work on kernel 3.2.0-29

---

### Post by blackflame0729 on 2012-08-09
Thank you so much for this, got my sound working again from this :D

---

### Post by geekymaestro on 2012-08-16
I tried the troubleshooting but it didn't seem to fix my issue and (sorry if this is noobish) trying to copy a file into /etc only yielded an error message, so I couldn't make an asound.conf file.  Ok, that being said, here's my issue.

I have a Sound Blaster X-Fi Titanium card and am running 12.04 LTS 64-bit. At the login screen the bongos play and the audio shows that it's working.  After logging in the sound stops working, and I have to type the following in the terminal:

```
gstreamer-properties
```

Which then brings up a box where I can select "ALSA" or "Pulse Audio" as the driver and then manually select "Front/WaveIn" for the device. This works and I am able to get audio from the card.  Additionally, if I right click on Sound Settings, the Sound Blaster X-Fi is there once again.  If I look at Sound Settings before I use the gstreamer command, it's blank. Problem is, I'm having to do this EVERY time I log in. There has to be a better way. I'm not a noob with Linux, but I'm not a superuser either. Any help on how I can get these values to load at startup would be appreciated.

---

### Post by nightfever on 2012-08-28
I'm having sound issues with 12.04 as well.
I have no output at all in sound settings.
Alsamixer gives me only the build in chip with HDMI output, while gstreamer-properties and pulseaudio volume control gives me the other sound card I have, but still no output. What the hell happened?

---

### Post by Dettus on 2012-08-29
I followed several problem solving guides but anything seems to work. I've been looking for someone with my same problem for two days, but i didn't find anything similar. I installed Ubuntu 12.04 two days ago and i had only an audio problem.  When i start my pc i can hear music and watch videos for a while, but after a minute or two,  Rhythmbox, Amarok, VLC, or any music reader stops working, and i cannot watch videos on youtube because the slide stops (neither on dailymotion). But the strangest thing is that all seemed to be all right when i tried to use the terminal commands to check the sound card and alsamixer.

Is there anyone that could help me to solve the problem? 

P.S. Sorry for my bad english, i'm italian

---

### Post by Yellow Pasque on 2012-08-31
> **Dettus said:**
> I followed several problem solving guides but anything seems to work. I've been looking for someone with my same problem for two days, but i didn't find anything similar. I installed Ubuntu 12.04 two days ago and i had only an audio problem.  When i start my pc i can hear music and watch videos for a while, but after a minute or two,  Rhythmbox, Amarok, VLC, or any music reader stops working, and i cannot watch videos on youtube because the slide stops (neither on dailymotion). But the strangest thing is that all seemed to be all right when i tried to use the terminal commands to check the sound card and alsamixer.

Is there anyone that could help me to solve the problem? 

P.S. Sorry for my bad english, i'm italian
Post a bug and make a verbose pulseaudio log: [https://wiki.ubuntu.com/PulseAudio/Log](https://wiki.ubuntu.com/PulseAudio/Log)

---

### Post by bashologist on 2012-09-01
No audio HDMI. GEFORCE GTX 660Ti from MSI. It just came out so, not sure if it's supported yet. Any ideas? hdmi audio is my only option for sound. I tried reading through those pdf files but could never get aplay to recognize the device or card or whatever.

```

% aplay -l
**** List of PLAYBACK Hardware Devices ****

```

[http://www.alsa-project.org/db/?f=48ad4e344739822db3f05e07ae6519dfb4feb6c2](http://www.alsa-project.org/db/?f=48ad4e344739822db3f05e07ae6519dfb4feb6c2)

Edit: Also note that there were no hardware drivers available so I installed them manually from Nvidia's site, which worked great for video over hdmi, but no audio yet.

---

### Post by stamati76 on 2012-09-18
Hi, I've been having sound issues on a new install of Ubuntu 12.04.  My sound works for a while and then cuts off

If, for example, i am watching or listening to something continuously it is fine.  However if i open another file, and close the previous one, to watch or listen to something, my sound stops working.

I am using a digital co-axial cable from built in sound card to my Logitech Z5500 speakers.  I can see from the Logitech Z5500 display panel that it is not receiving any sound signal.


The device i am using is [AD198x Digital]

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by SoggyCornflake on 2012-09-19
I was following the sound trouble shooting guide because of my Nvidia Geforce card  

[PHP]grep "eld_valid *1" /proc/asound/NVidia/eld*
You should see something like this:
/proc/asound/NVidia/eld#X.0:eld_valid        1
[/PHP]

When I tried >  sudo grep "eld_valid *1" /proc/asound/NVidia/eld*   I got nothing.


When I tried >  sudo grep "eld_valid *" /proc/asound/NVidia/eld*   I got this > /proc/asound/NVidia/eld#0.0:eld_valid		0
/proc/asound/NVidia/eld#0.1:eld_valid		0


I am unsure where to go from here.  Any help would be greatly appreciated.

---

### Post by iamsamami on 2012-10-13
[B]Thanks U-forum for this posting.
I followed the links, followed through a couple of the CLIs and now my audio is working again.
Just marked this post "Still can't hear audio after upgrade" as Solved.

Thanks,
IamSamAmI


[/B]

---

### Post by Perronah on 2012-10-24
Hi,
I am running 12.04 server on a headless system.  I realize the server edition doesn't include any sound options/drivers.  I've read through the trouble shooting guides and have tried some of their suggestions, but since they are written for a desktop environment, I'm not getting anywhere with them.  I would like to keep my headless setup but with sound playback so I can run an MPD server and control it from my mobile telephone.  

When I VNC into a virtual desktop and I look under sound settings there isn't anything listed under the hardware and the setup lists a "Dummy Output." 

For regular use, I use the command line. I've setup VNC for the times my CLI knowledge doesn't match the level of sophistication needed to troubleshoot my issues.

Thanks for any suggestions.

---

### Post by vivekJohn on 2012-10-25
> **Achillean said:**
> Hi!

I've started using Ubuntu 11.10 recently (i.e, this morning) and iI'm having issues with the sound as well.

I have sound if I boot from the live cd, but if I boot from the hard drive it can't find a soundcard. I have onboard audio enabled in the BIOS and when i run lspci it sees it just fine.


The audio device listed under lspci is "nVidia Corporation MCP51 High Definition Audio". I googled it and it seems to be an issue that a bunch of people have, and I followed the guides in the first post but they either didnt work or didnt follow through.

Thanks in advance!
hope this helps
[https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules](https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules)
:)

---

### Post by vivekJohn on 2012-10-25
Cheers to this awesome forum :)

---

### Post by cw84 on 2012-10-28
Since I upgraded from 12.04 to 12.10, my USB sound device is not working anymore. Headphone sound using the sound device integrated in the chipset is still working correct.
This are the two devices:
```

c_w@Thomas-Ubuntu:~$ cat /proc/asound/cards
 0 [Intel ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xeea20000 irq 48
 1 [Speaker ]: USB-Audio - USB Speaker
                      GENERIC USB Speaker at usb-0000:00:1d.7-2.3, full speed
c_w@Thomas-Ubuntu:~$ lspci | grep -i audio
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
c_w@Thomas-Ubuntu:~$ lsusb
Bus 001 Device 002: ID 05ca:18b0 Ricoh Co., Ltd Sony Vaio Integrated Webcam
Bus 002 Device 002: ID 0409:005a NEC Corp. HighSpeed Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 046d:c01d Logitech, Inc. MX510 Optical Mouse
Bus 002 Device 004: ID 046d:c326 Logitech, Inc.
Bus 002 Device 005: ID 0c45:1b19 Microdia

```

The USB device is the last line in the lsusb output.

If I use the aplay command to play a sound file, the output looks fine, using both sound devices. The only difference is that I don't hear any sound if I use the USB device ;-)

In the alsamixer, there is only the PCM mixer for the USB device and this is not muted.

The only further indicator that something is not working with the USB device is that it is marked with a red circle with a line in it in the audio configuration:
[http://dl.dropbox.com/u/16335670/audio.png](http://dl.dropbox.com/u/16335670/audio.png)

Does anyone know what the symbol infront og the USB device means?

I tried to use the trouble shooting guide, but the google docs guide is not dealing with USB devices (right?) and the I performed the steps in the other one, but it is not helping...

edit:
I also tried both 12.04 and 12.10 live CD and it is NOT working with both. But it was working with 12.04, before I upgraded to 12.10.

I also tried the USB device with Windows 7 to check if it might be broken, but it's still working there.

I have no clue what's wrong...

---

### Post by OrionXIII on 2012-10-30
Have a nice brand new ASUS P8Z77-V LE Plus motherboard with built in sound card. I think it's too new for Ubuntu 10.04.4 - I tried 12.04 and 12.10 and the sound card worked fine (all 64-bit).

But the OS was a piece of garbage and Unity was a nightmare.

Unfortunately, with 10.04.4 64-bit OS, I only get the sounds of silence...I've gone through the troubleshooting steps but the summary is they all reported 'Sound card not found' - I can post the output if desired.

Any suggestions or ideas?

---

### Post by Yellow Pasque on 2012-10-31
Use Lubuntu/Xubuntu 12.10, or switch to Linux Mint's "Cinnamon" desktop. Trying to run an old release isn't the right way to go about finding a replacement for Unity, IMHO.

---

### Post by OrionXIII on 2012-10-31
Thanks - I tried 12.10 and it crashed regularly, so I went with 12.04 LTS - I'm using it as a wrapper for my VMware player anyway, so I just boot into 2D mode and leave it alone.

I tried the Xubuntu desktop (which I really enjoyed), but it doesn't seem to work well with VMware...C'est la vie!

Thank you for your help and advice. :) Problem solved!

Orion

---

### Post by Pavonis on 2012-11-02
I got stuck on the guide :(. I am a newbie so bear with me.

**step 12**
$ aplay -l
aplay: device_list:223: no soundcards found...

**Aa**
$ sudo aplay -l
[sudo] password for Pavonis: 
aplay: device_list:223: no soundcards found...

**Ac**
 echo "Sound cards recognized by the system:"; lspci -nn | grep --color=none '\[04[80][13]\]'; echo "Sound cards recognized by ALSA:"; lspci -nn | grep '\[04[80][13]\]' | while read line; do lspci -nnk | grep -A 3 '\[04[80][13]\]' | grep -e 'Kernel modules: ..*' -e '\[40[80][13]\]' | grep --color=none -F "$line"; done; echo "Sound cards recognized by ALSA, and activated:"; lspci -nn | grep '\[04[80][13]\]' | while read line; do lspci -nnk | grep -A 3 '\[04[80][13]\]' | grep -e 'Kernel drivers in use: ..*' -e '\[04[80][13]\]' | grep --color=none -F "$line"; done
Sound cards recognized by the system:
00:1b.0 Audio device [0403]: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller [8086:1e20] (rev 04)
Sound cards recognized by ALSA:
Sound cards recognized by ALSA, and activated:
00:1b.0 Audio device [0403]: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller [8086:1e20] (rev 04)

So as far as I can tell, my sound care is activated but then why doesn't aplay see it? What do I do now? I have Ubuntu 10.04 on a VAIO SVE151B11N.

---

### Post by Yellow Pasque on 2012-11-02
@Pavonis, please give your Alsa Info: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by Pavonis on 2012-11-02
Here's my alsa info,
[http://www.alsa-project.org/db/?f=d95c4a576407cc2c00c34e72d5d4da8d84045967](http://www.alsa-project.org/db/?f=d95c4a576407cc2c00c34e72d5d4da8d84045967)

---

### Post by Another Monkey on 2012-12-03
Thank you very much for this thread and the links in the first post.  I only had front sound coming out of my front-left speaker.  Following the first guide and it suggested checking the plugs.  My problem wasn't going to be that dumb, surely?

Well, it was and I am now a happy bunny.

---

### Post by em wai zee on 2012-12-12
> **mörgæs said:**
> These two manuals give advice for solving sound problems:

[Sound Troubleshooting Guide]("https://docs.google.com/document/d/1iTlJ8BfqXUjaHO__TEdlkvuqB1WLOkGaudngc5SFLMI/edit")
(by Lkjoel and Wildmanne39)


[Sound Troubleshooting Procedure]("https://help.ubuntu.com/community/SoundTroubleshootingProcedure")
(by Mark Rijckenberg)


If you have tried the two links without result, feel free to ask in this thread.

I believe I'd solve the mystery of "Dummy Output" in my Acer Travelmate 6292, running Ubuntu 12.10, upgraded from 10.04, if there are tips for Ubuntu 12.10! Any tips guys??? Thank you for helping me; I feel so much muted now without THE sound!:popcorn:

---

### Post by nikotiini3 on 2012-12-15
I have a problem getting sound from Youtube. I'm using 12.10 and the latest flash. I also use ALSA (no pulse audio) and Turtle Beach PX21 usb headset. 

The sound works perfectly in Skype and VLC. I've made the headset into my default audio device (at least VLC sees it as that and it works). This is the same setup that worked with my old Sony Wireless Stereo 7.1 headset on Youtube also.

What could be wrong?

Edit: I added this: 
options snd-usb-audio index=1,2 vid=0x0ccd,0x0d8c pid=0x0028,0x000c 
into my modprobe.d/alsa-base.conf.

Now I can get audio from my usb headset from flash videos BUT only after I make my onboard soundcard busy. I tried to change the index to 0 but that made it not work again....

Edit2: Nope lost it again for some reason..

---

### Post by mihnea13 on 2013-01-02
I have a problem when connecting my laptop to the TV via HDMI cable...in the Sound Settings window the only device available device for output is for the internal speakers. 

The thing is it worked at the beginning (I`m a newbie to Linux, running Ubuntu 12.04) but after I plugged the laptop to the TV a few times, the default sound output disappeared from Sound Settings (internal speakers weren`t working, nor headphones, only via HDMI). 

While trying to search for a fix, I found this page: 

[https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure) and I executed the huge command written there at Step 1 and then rebooted. And it worked (sound was coming just fine from internal speakers or headphones...but now I can`t get it to work via HDMI...which sucks.

I`ve tried logging off/on, booting with the cable attached or attaching it aftewards, connecting the cable with the TV on and off, everything looks fine in alsamixer (I`ve tried muting and the unmuting S/PDFI), I`ve also installed pavucontrol and changed the configuration to a HDMI one (tried all of them, nothing worked). This is the output from ```
aplay -l
```:

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


If you need to look at some config files or the output of other commands, please let me know.

---

### Post by nochtavio on 2013-01-07
I've just installed Lubuntu 12.10 (i'm using old netbook). Everything works, except built-in speaker. I've tried many solution found by googling, but no luck.

Of course i tried OP troubleshooting, but still no sound. Alsa recognize my sound card, and everything seems normal in alsamixer (tried to mute and unmute again).


Thanks for any help.

[http://www.alsa-project.org/db/?f=a59c5f2edf8a61119a94d34a5d8afc13703f0b71](http://www.alsa-project.org/db/?f=a59c5f2edf8a61119a94d34a5d8afc13703f0b71)

---

### Post by Tolobán on 2013-01-17
> **em wai zee said:**
> I believe I'd solve the mystery of "Dummy Output" in my Acer Travelmate 6292, running Ubuntu 12.10, upgraded from 10.04, if there are tips for Ubuntu 12.10! Any tips guys??? Thank you for helping me; I feel so much muted now without THE sound!:popcorn:
I upgraded from Kubuntu 10.04 to 12.04 and the frustrating "Dummy Output" problem started.

There were some files related to oss4 sitting in /etc/modprobe.d which did't exist on a second PC with working sound using the same sound card. I removed the oss4 package from the first one and sound works fine now.

So, in my case, oss4 got installed somehow and got in the way after upgrading.

---

### Post by mikebailey on 2013-01-18
I posted this problem first back in 2008 about my old x-fi xtreme gamer pci card. i figured, hey, they should have this problem fixed, its been 4 years, but, alas, was i ever wrong.

i have a creative labs xtremem music pci-e version. i am attempting to get my optical INPUT to play through my analog 5.0 OUTPUT. or even the line INPUT working, as that is not working either. i can get the sound to work with aplay | arecord with the right variables in there, but it is horrifically lagged and gets worse the longer i use it. i am attempting to use the optical spdif input on my soundcard and have the sound loop out to my analog 5.0 output on the same card. i have tried many articles and the help they have provided, but am still at the same place i was in the beginning, and that is i cannot get it to loop through with no lag. this seems to be a very common issue, and yet, there is very little help in the community on how to resolve this issue. i would love to use ubuntu full time, but with this one issue nagging me, i cannot use it full time yet. i hope that a resolution to this issue could come quickly. i know this post is over 2 years old, but the person who originally asked the question had not been answered yet. thank you for your time, and i will post anything that needs to be posted, just help a fellow out here, throw me a bone or something!!

aplay -l

$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Generic [HD-Audio Generic], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Creative [HDA Creative], device 0: CA0110 Analog [CA0110 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Creative [HDA Creative], device 1: CA0110 Digital [CA0110 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by mikebailey on 2013-01-21
still, no help on this matter? it seems that no one knows how to fix it, as it is a very very very very common issue with sound in ubuntu. or, people know how to fix it, but are too damn lazy to bother to try and contribute back to the community.

---

### Post by mörgæs on 2013-01-22
I can promise you one thing: A post like this will not get you further. Please calm down if you want to continue posting here.

Not all hardware vendors are eager to support Linux, so the task of writing a driver can be big. It is not a question of being lazy.

---

### Post by Yellow Pasque on 2013-01-22
Creative Labs is one of the worst contributors to the Linux community and is just a litigious hornets nest. They're more interested in making money with patents/lawyers than with advancing technology because their relevancy is rapidly decreasing.

---

### Post by Simeo on 2013-01-23
Ok, I know  it's been hashed over and over but.... I did all the searched. Checked  google. Ran through a few troubleshooting but still nothing.
 
I'm not getting any audio now and I was before. I have a dual boot  aspire timeline laptop. I usually boot into ubuntu 12.10 but I needed to  get into Win7 to run my Maxtor Blackarmor Harddrive.

Now I'm back in Ubuntu and have no sound. I've run several tests,  checked alsamixer, etc. Nothing is muted. What outputs do y'all need to  help?

Edit: Just logged out of Ubuntu, to Win7 and audio works in Win7, then back to Ubuntu and no audio.

Made this a new thread under "Audio Not Working After Boot Ubuntu 12.10". Please feel free to delete it. Thank you and sorry.

---

### Post by cu_ on 2013-02-02
Gurus.  Does anyone here has a reliable script to mute/unmute microphone?
I found one at [http://ubuntuforums.org/showthread.php?t=1977064](http://ubuntuforums.org/showthread.php?t=1977064), but it does not mute my usb logitech micrphone.

---

### Post by curiousapprentice on 2013-02-03
Hi ! Im also having huge difficulties on configuring the sound system on Ubuntu 12.04 and get it to work properly.

I need Jack and Pulseaudio work side by side or switch between them. I found a solution by installing Pulseaudio-module-jack. But this technique is not good for me. I cant see my hardware devices, and moreover many applications stopped working. For example "Desktop Recorder" could not record Jack/audio streams. I have tried selecting various channels in the "Advanced -> Sound" , but it is always resulting in crash with various error codes.
I have also posted three more questions regarding to this same issue. Please have a look at them -

[http://askubuntu.com/questions/250960/sound-is-unbalanced-on-both-speakers-i-am-hearing-loud-sound-from-the-left-and](http://askubuntu.com/questions/250960/sound-is-unbalanced-on-both-speakers-i-am-hearing-loud-sound-from-the-left-and)

[http://askubuntu.com/questions/250697/how-do-i-switch-between-pulseaudio-and-jack-on-ubuntu-12-04-lts-x86-linux](http://askubuntu.com/questions/250697/how-do-i-switch-between-pulseaudio-and-jack-on-ubuntu-12-04-lts-x86-linux)

[http://askubuntu.com/questions/250508/unable-to-start-jack-server-service-is-available-org-jackaudio-service-aka-ja](http://askubuntu.com/questions/250508/unable-to-start-jack-server-service-is-available-org-jackaudio-service-aka-ja)

But still no replies. Please help.

---

### Post by Flipflop McFly on 2013-02-06
Hi helpful folks.

I've tried many of the suggestions listed in those two guides, but nothing has helped. I also asked this question yesterday in the Absolute Beginners category. I've gotten no response yet, so I thought I'd see if one of the 'heroes' lodging in this forum could stop me from feeling so low... there's a lot of scary monsters in my terminal now...

Here's my original question

I just upgraded (complete reboot, backing up my files) from Ubuntu 10.04 to Lubuntu 12.10. I have an older laptop, and finally realized that the Xub/Lub series is the series for me.

HOWEVER I have not yet gotten any sound out of my laptop. I first tried Xubuntu 12.10 - everything was a little slow (again: it's an older laptop), and there was no sound. So then I installed Lubuntu 12.10, which seems to run GREAT, except STILL no sound.

I've followed many threads of advice, given to me by the Great Googlegod, but nothing has helped. Sometimes, when muting/unmuting via alsamixer, the speaker will pop/click, but no satisfaction.

I've been using Ubuntu on this for a few years, with no real issues (except an increasing sluggishness, hence my upgrading to Lubuntu 12.10).

This seems to be an issue with Xub and Lub 12.10, maybe even 12.04 (based on my googling), and maybe Ubuntu, as well. I actually put Xubuntu 12.10 on a hand-me-down EVEN OLDER Sony Vaio laptop, and it seemed to work fine... so it's something particular with this model, maybe?

My computer is a Sony Vaio PCG-792L.

now, for some newer info, from working on it tonight:

result of aplay -l:
card 0: Intel [HDA Intel], device 0: ALC260 Analog [ALC260 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC260 Digital [ALC260 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

And then there's this:

Your ALSA information is located at [http://www.alsa-project.org/db/?f=9c5f7c05a4464f179ca20b787f8b23db37514e8a](http://www.alsa-project.org/db/?f=9c5f7c05a4464f179ca20b787f8b23db37514e8a)

THANK YOU so much, in advance, for whatever you can do.

---

### Post by mörgæs on 2013-02-08
It seems like a regression bug, which should be fixed.

Have you tried 13.04 (alpha)? If this one is also failing you could post a question in the [development forum]("http://ubuntuforums.org/forumdisplay.php?f=427"). People there can help you check if it's a true bug, which should be reported to the developers.

---

### Post by Flipflop McFly on 2013-02-08
Thanks for the tip, Morgaes (I don't know how to find umlauts on my keyboard)

I tried Lub 13.04 from a live CD, and a speaker-test still got me nothing. So, with a heavy heart, I re-installed Ub 10.04, and was greeted by the cheery drums and choir I know so well.

I will post my stats in the development forum, but mostly for the developers' sakes, since I'm afraid that whatever fix I'd have to do is beyond my abilities.

(I suppose I actually don't know if the problem is the 12.x/13.x series, or something Xub/Lub, since I never tried Ub 12.x/13.x on my laptop - but I know Unity would make it break down in tears).

-FFMcF

---

### Post by mörgæs on 2013-02-09
In case people are following, here is the thread for 13.04:

[http://ubuntuforums.org/showthread.php?t=2113961](http://ubuntuforums.org/showthread.php?t=2113961)

---

### Post by GuiGuy on 2013-02-09
> **mörgæs said:**
> It seems like a regression bug, which should be fixed.

Have you tried 13.04 (alpha)? If this one is also failing you could post a question in the [development forum]("http://ubuntuforums.org/forumdisplay.php?f=427"). People there can help you check if it's a true bug, which should be reported to the developers.

The poster has admitted he's reasonbly new to all this and you're telling him to enter a bear pit of manic fanbois? ;)

---

### Post by mörgæs on 2013-02-10
I tend to toss them some freshmeat once a week, else they rip each other to pieces :-)

---

### Post by Cpierce on 2013-02-11
So that I didn't add to this long forum, I started my own thread outlining my issues. Could some of you sound guru's take a peek ? I would sure appreciate it

[http://ubuntuforums.org/showthread.php?t=2114985](http://ubuntuforums.org/showthread.php?t=2114985)

---

### Post by Refon_oSu on 2013-02-12
I've found an old thread mentioning the VIA VT1802 chip, but there was no solution for it. Then I found that topic and read the troubleshooting guides but they didn't help me too.  I've used the utility from **lidex** and it gave me that: [http://www.alsa-project.org/db/?f=eb7a8161de174183a4806648aafed4f4c3636660](http://www.alsa-project.org/db/?f=eb7a8161de174183a4806648aafed4f4c3636660)

As far as I can say, my laptops chip is recognised and activated by ALSA, but the speakers don't do any sound at all and headphones only make the noise if connected.

Would you help me, please?

---

### Post by Yellow Pasque on 2013-02-12
> **Refon_oSu said:**
> I've found an old thread mentioning the VIA VT1802 chip, but there was no solution for it. Then I found that topic and read the troubleshooting guides but they didn't help me too.  I've used the utility from **lidex** and it gave me that: [http://www.alsa-project.org/db/?f=eb7a8161de174183a4806648aafed4f4c3636660](http://www.alsa-project.org/db/?f=eb7a8161de174183a4806648aafed4f4c3636660)

As far as I can say, my laptops chip is recognised and activated by ALSA, but the speakers don't do any sound at all and headphones only make the noise if connected.

Would you help me, please?
Upgrade the ALSA driver. A lot of VIA codec issues have been fixed since the time when Ubuntu 12.04 came out: [https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS)

---

### Post by Xarcon on 2013-02-12
Hi, I'm new to Ubuntu and I'm having a problem with my volume level.  Whenever it drops below 16%, the sound disappears.  It doesn't technically show that the volume is muted until the volume level hits 0%, but there's no sound anyway.  When the volume is at or above 16%, it works fine.  Thanks for any help with this.

---

### Post by redroserade on 2013-02-15
Greetings everyone, I posted previously on a separate thread about my sound issues here: [http://ubuntuforums.org/showthread.php?t=2112597](http://ubuntuforums.org/showthread.php?t=2112597) (same old sound clicks problem), and after trying some more, I still can't figure out what went wrong. I tried purging alsa and pulseaudio and reinstalling (which did work), but after rebooting, the problem came back.

Relevant information is in that post, and if you need more, ask me, please, because I'm really tired of this.

---

### Post by Simeo on 2013-02-16
Hello. My audio woes are odd and usually only seem to come after a  long visit to Windows 7. They "fixed themselves" before but now it's  happened again. 

Alsa output: [http://www.alsa-project.org/db/?f=209dec06141b60a3bf78b15faa0f36a5f80df43e](http://www.alsa-project.org/db/?f=209dec06141b60a3bf78b15faa0f36a5f80df43e)

Edit: Sorry. Running Acer Aspire TimelineX 4830TG-6808. Ubuntu 12.10 Dual-boot w/ Win7. Audio icon not showing up in upper right either. Tried posting pulseverbose.log but I think it was 'too long'. Browser kept crashing when I did. Issues seem to happen only on reboot. I've tried to 'troubleshoot' a LOT so not sure if any fixes are conflicting because the issue seems to be evolving. Is there a way I could "start fresh" with Pulseaudio/Alsa and troubleshoot from there? I love Ubuntu, can't wait for 13.04 to come out and I use/need it for work purposes. Having no audio makes my work very stressful :(

If you need any more info please let me know.

Extra Edit for more Info:

lspci output: ```
Aspire:~$ lspci | grep Audio
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 04)
```

aplay-l output: ```
Aspire:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: CX20588 Analog [CX20588 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 1: CX20588 Digital [CX20588 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

---

### Post by mörgæs on 2013-02-16
> **Simeo said:**
> ...can't wait for 13.04 to come out and I use/need it for work purposes...

Then please begin testing it, at least in a live boot. Now is your best chance to isolate bugs in order to get them fixed.

---

### Post by Simeo on 2013-02-16
> **mörgæs said:**
> Then please begin testing it, at least in a live boot. Now is your best chance to isolate bugs in order to get them fixed.

Do you think upgrading to beta may fix my audio issues? I have no issues testing to help contribute. I've been using Ubuntu since 10.04. It was a small learning curve when I first started (and a bigger one with the intro of Unity) but now I find I'm more productive with Ubuntu than Win or Mac. I don't mind contributing to the community at all. You guys have helped so much in the past 3 years.

PS I added more info to my last post lspci and aplay outputs. Hope it helps.

---

### Post by mörgæs on 2013-02-16
> **Simeo said:**
> Do you think upgrading to beta may fix my audio issues? 

I can't say if it works better, worse or the same. Again: Testing and reporting bugs is the only way to go.

---

### Post by Simeo on 2013-02-16
> **mörgæs said:**
> I can't say if it works better, worse or the same. Again: Testing and reporting bugs is the only way to go.

I have a TimelineX so I would be able to contribute to the power consumption plus any other issues and if I have any audio bugs it will be closely looked into..... How do I go about updating? I see the [daily build]("http://cdimage.ubuntu.com/daily-live/current/") but how do I get started?

PS Do you see anything in my previous troubleshooting posts.... any idea to fix?

---

### Post by avitriumph on 2013-02-18
My audio device doesn't work in ubuntu 10.04. But, it works fine with windows. I have uploaded the information about my audio device  as listed in some posts.

[http://www.alsa-project.org/db/?f=17b8e52a8e80e2e86ad3195b77cca5ab47b1c811](http://www.alsa-project.org/db/?f=17b8e52a8e80e2e86ad3195b77cca5ab47b1c811)


Please help me with this problem

---

### Post by mörgæs on 2013-02-18
> **Simeo said:**
> I see the [daily build]("http://cdimage.ubuntu.com/daily-live/current/") but how do I get started?

PS Do you see anything in my previous troubleshooting posts.... any idea to fix?

Just create a bootable USB stick from the ISO and boot. Works like any other Buntu release.

I didn't see anything strange, but then again I'm not expert in sound.

---

### Post by mörgæs on 2013-02-18
> **avitriumph said:**
> My audio device doesn't work in ubuntu 10.04. But, it works fine with windows. I have uploaded the information about my audio device  as listed in some posts.

[http://www.alsa-project.org/db/?f=17b8e52a8e80e2e86ad3195b77cca5ab47b1c811](http://www.alsa-project.org/db/?f=17b8e52a8e80e2e86ad3195b77cca5ab47b1c811)


Please help me with this problem

Old software and new hardware don't mix. Best you can do is a fresh install of 12.10.

---

### Post by Simeo on 2013-02-20
My audio is still not working after booting from Win7. It works perfectly fine in Windows but going back to Ubuntu doesn't work. Audio works in Live USB and audio works after a fresh install BEFORE trying to dual boot to Windows but after one visit to Win7 and back to Ubuntu, my audio is gone.

Filed a bug report: [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/1130410](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/1130410)

---

### Post by lordcantafford on 2013-03-08
:)hello everyone! probably not the right place, but please help me anyway. can i enable front panel audio-in-n-out. while using the rear simultaniously? How? Im using Ubuntu 12.10 please teach me how to do thesame on linux puppy. and oh, plese tell me how to autohide top panel 12.10.

---

### Post by onlyunless on 2013-03-12
Hopefully someone can help me out here. I'm running an HP dv7t-3300 with Ubuntu 12.10 installed. My audio plays fine out of the speakers, but when I plug in headphones, sound plays through both the speakers and the headphones at the same time. I wasn't too sure as to where I could post, and this seemed to be a somewhat appropriate thread.

My information as according to alsa-info.sh is here: [http://www.alsa-project.org/db/?f=5ac74ef4d48ebd96ff15f1dbab28dafb035f35db](http://www.alsa-project.org/db/?f=5ac74ef4d48ebd96ff15f1dbab28dafb035f35db)

Any and all help is appreciated.

---

### Post by mörgæs on 2013-03-13
This problem has been haunting Buntu for a long time, and unfortunately the solution is different for each brand of computers. Here is one which is close to yours:

[http://ubuntuforums.org/showthread.php?t=1658689](http://ubuntuforums.org/showthread.php?t=1658689)

Also, have you tried if the problem is solved in 13.04?

---

### Post by onlyunless on 2013-03-13
Ahh! Thank you mörgæs! This fixed the problem! I seem to have the same issue as the other user with the subwoofer no longer working, but this is a fair compromise. Thanks again for your help!

(I haven't tried running 13.04 yet, I'll have to prepare for a clean install, I've been meaning to do one for a while now anyways.)

---

### Post by ibchristie on 2013-03-26
I have been struggling to get the sound working on my machine for about 18 months now.
I have a Gigabyte motherboard (GA P67A-UD3R-B3) with inbuilt sound (HDA Intel PCH using a Realtek ALC889 chipset) and an i5 CPU. I am running Ubuntu 12.10
I have tried so many different tutorials/how tos/trouble shooting guides that I have lost track. Tonight I carefully worked my way through the trouble shooting guide by Lkjoel and Wildmanne39 which is listed at the start of this thread. Still no success. All I want is bog-standard stereo in and out. I have a pile of vinyl, a very good turntable and a pre-amp which I would like to use to convert my record collection into OGG Vorbis files. Frustratingly I have a very cheap netbook with Ubuntu 12.04 which works fine with Audacity, it just sounds lousy.
I have tried LinuxMint, bootable CDS, bootable USBs all with no success.
Is there something about the Gigabyte motherboard which makes it impossible to get sound from Linux?

In desperation...
Cheers
Ian

---

### Post by DoItYourSelfer on 2013-03-27
I am using the ATI HD 6790 2x cards   I have the correct open source  default driver in ubuntu 12.10 gullium 0.4? Bunt.  I have done sound-test in  comand terminal  it showing sound  setting and such.  So I am assuming  in my case sound works.

speaker-test 1.0.25

Playback device is default
Stream parameters are 48000Hz, S16_LE, 1 channels
Using 16 octaves of pink noise
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 192 to 2097152
Period size range from 64 to 699051
Using max buffer size 2097152
Periods = 4
was set period_size = 524288
was set buffer_size = 2097152



Yet  doesn't    under system UI for sound it does not give me the option to  send sound through the HDMI passthrough to the big screen vizio 37in. I  am assuming either I have to add the option somehow or I am not  allowed.  meaning I will have no sound and Will be forced back to  windows.

Under windows installing ATI drivers and CCC  also  installed a sound option to send sound through the HDMI connector. you  were also given the option of telling it which cards HDMI you wanted to  send it through under sound device manager.    Why doesn't the opensource do the same thing since  lot of us use our tvs as both screen and sound and do not have extra  speakers to plug into the sound card jacks. 

ATI installer didn't  work and corupted the desktop forcing me to reinstall ubuntu 12.10  each  attempt took 2 hours(watched a 2 hour movie on PS3.) for the ATI to go  through install proccess only to say at the end ubuntu didn't recognize  some of the fonts and gave me only 2 choices in changes to retry with.   your not given the choice beforehand. of which font type you wanted to try.

I also have a desktop larger than screen issue on the same vizio 37 in tv this is for another thread.  have a 21 in weshinghouse no issues with size larger than screen.

I  thanks in advance any help that would help get me up and running .   Oh  I am not familiar with command terminal   command terminal is going to  be difficult for me period,  I am visually spacially oriented   intellegent      (different skill set due to type of dyslexia with short  term memory )   You give me a complicated visual UI  and I will figure  out on my own even though I never used it before, as long as it actually  works correctly.  Give me a book of commands of ubuntu and I will be  lost for a year problably.     

Doityourselfer   
 thanks. 

PS.  I gave  the heads up on me as a means to let you know how My brain works  so  that your not wasting time trying to tell be to do something  that   preys on my weaknesses.    If it is comand related I will need direct  copy and paste  options and how to undo it without having to uninstall  everything and start over  for the 14th time in 3 days at about 16 hrs a  day.

---

### Post by k-laminero on 2013-05-02
[COLOR=#222222][FONT=Verdana][SIZE=2]Sound not working suddenly for movies and music, but works for chrome[/SIZE][/FONT][/COLOR]


[COLOR=#222222][FONT=Verdana][SIZE=2]MamboJumbo,[/SIZE][/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana][SIZE=2]Ubuntu13.04[/SIZE][/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana][SIZE=2]VLC,Banshee[/SIZE][/FONT][/COLOR]

[COLOR=#222222][FONT=Verdana][SIZE=2]Helloall,[/SIZE][/FONT][/COLOR]

[COLOR=#222222][FONT=Verdana][SIZE=2]Iam having an issue where my sound stopped working on a new session. Ihad had a few sessions under 13.04 already and sound was fine. Now,the sound settings will crash right away if i launch it, and I willhear nothing if I launch any movie on "Movie" or VLC, samefor music on banshee. However, sound on youtube or other video siteswork fine. I have tried starting VLC first after reboot and it didnot make a difference. I also tried changing the audio engine in VLCand that did not help either (alsa, pulse, etc...)[/SIZE][/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana][SIZE=2]Ilooked online quite a bit and did not find anything similar to myissue but did find some troubleshooting clues

I did run things such as alsamixer etc and other scripts included in this thread but it did not help.
Trying to launch "gnome-control-center sound" in terminal gives me a [/SIZE][/FONT][/COLOR] "Segmentation fault (core dumped)"


And here is the alsa info txt output
> !!Soundcards recognised by ALSA
!!-----------------------------


 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfdff8000 irq 44
 1 [MobilePre      ]: USB-Audio - MobilePre
                      M Audio MobilePre at usb-0000:00:1a.7-5.4, full speed




!!PCI Soundcards installed in the system
!!--------------------------------------


00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)


When I first set up ubuntu, i tested every speaker of my 5.1 system via the sound settings menu. Now if i do a 5.1 system test in terminal (since my sound settings crashes) it times out.

What should I do?
Thanks

[COLOR=#222222][FONT=Verdana][SIZE=2]

[/SIZE][/FONT][/COLOR]

---

### Post by Yellow Pasque on 2013-05-02
@k-laminero: try resetting your pulseaudio settings:
```
rm -r ~/.pulse*; pulseaudio -k
```

---

### Post by k-laminero on 2013-05-02
> **Temüjin said:**
> @k-laminero: try resetting your pulseaudio settings:
```
rm -r ~/.pulse*; pulseaudio -k
```
 
Thank you for your answer.
I did try that before and here is what I get

> rm -r ~/.pulse*; pulseaudio -krm: cannot remove ‘/home/iohan/.pulse*’: No such file or directory




I have no idea why.

---

### Post by k-laminero on 2013-05-03
Should I be posting this somewhere else?

---

### Post by Yellow Pasque on 2013-05-03
That probably means pulseaudio isn't starting at all. Maybe delete the configuration and try again:
```
sudo rm -r /etc/pulse
sudo apt-get install --reinstall pulseaudio libasound2
pulseaudio -k
```

If that doesn't work, you can make a log file: [https://wiki.ubuntu.com/PulseAudio/Log](https://wiki.ubuntu.com/PulseAudio/Log)

---

### Post by k-laminero on 2013-05-03
That worked!!! Didnt even need to reboot! :)
Thank you Temujin :) What does pulseaudio -k do?

---

### Post by Raynor_ni on 2013-05-16
No sound working here at all, aplay -l finds no sound cards, alsamixer won't run at all "cannot open mixer: No such file or directory" yet it is installed.

I had sound until there was a Kernel upgrade.. running Ringtail here.  Any help would be appreciated

---

### Post by Yellow Pasque on 2013-05-16
> **Raynor_ni said:**
> I had sound until there was a Kernel upgrade.. running Ringtail here.

Sounds like it could very well be: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1169984](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1169984)
Try the workaround: [https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS)

---

### Post by Raynor_ni on 2013-05-16
I've tried that but I get:
```
Error!  The dkms.conf for this module includes a BUILD_EXCLUSIVE directive which 
does not match this kernel/arch.  This indicates that it should not be built.
```

Any other ideas?

---

### Post by faust99 on 2013-05-21
I hope I'm not repeating anybody else's problem that has already been covered....I searched and couldn't find it. Anyhow, the problem is that after a certain amount of time of playing sound my speakers stop working (but sound can still be heard through the headphones). If I put the computer to sleep or reboot the speakers work again but fail again after some time (anything from 2 seconds to 15 minutes). I have tried the following to no avail: 

1. unmuting and disabling automute in alsa mixer
2. reloading alsa
3. reinstalling alsa
4. installing new kernel
5. installing old kernel
6. installing alsa development ppa

None of these work. The only way to continue using sound is to insert headphones or reboot/sleep.

Most frustrating perhaps, is the fact that I had exactly the same problem some months ago in 12.10 and then in 13.04 and both times it disappeared after some time. But now its back with a venegance. Please advise.

---

### Post by kevin34ct on 2013-05-23
Ok so I read the guides, and it doesn't have anything on my problem.  When I am playing back sound, any sound, be it games, music or movies, my sound randomly gets loud then it will get soft.  It happens with my speakers.  I am using on-board sound which uses the ALC888 sound device.  (Nvidia chipset).  I haven't tried it with headphones plugged into the speaker jacks because I use Bluetooth headphones which don't have this problem.   I'm still new at Linux so I will need some instructions on what to get for you, and what to do.

---

### Post by spiritofcat on 2013-05-27
I've just bought a new PC and I'm trying to migrate my Ubuntu 10.04 installation over to it.
I've chosen to do this instead of just starting with a fresh 12.04 install since I've got a lot of things already set up the way I want them on 10.04 and I don't want to go through the drama of getting everything set up from scratch again.

I've used Clonezilla to clone the hard drive from the old machine to the new one, and for the most part it's working well.

The only problem I've noticed is that the onboard sound card of the new machine is not reporting for duty.

I've read through both the guides linked at the start of this thread, and followed the first one but with no success. The second one seems to be only for 12.04 so I'm not sure how much help it can be to me.

Working with the first guide, I've become stuck with
```
sudo aplay -l
```
always returning
```
aplay: device_list:223: no soundcards found...
```

I've run the big command in procedure Ac:
```
echo "Sound cards recognized by the system:"; lspci -nn | grep --color=none '\[04[80][13]\]'; echo "Sound cards recognized by ALSA:"; lspci -nn | grep '\[04[80][13]\]' | while read line; do lspci -nnk | grep -A 3 '\[04[80][13]\]' | grep -e 'Kernel modules: ..*' -e '\[04[80][13]\]' | grep --color=none -F "$line"; done; echo "Sound cards recognized by ALSA, and activated:"; lspci -nn | grep '\[04[80][13]\]' | while read line; do lspci -nnk | grep -A 3 '\[04[80][13]\]' | grep -e 'Kernel drivers in use: ..*' -e '\[04[80][13]\]' | grep --color=none -F "$line"; done
```
And received this output:
```
Sound cards recognized by the system:00:1b.0 Audio device [0403]: Intel Corporation Device [8086:1e20] (rev 04)
Sound cards recognized by ALSA:
00:1b.0 Audio device [0403]: Intel Corporation Device [8086:1e20] (rev 04)
Sound cards recognized by ALSA, and activated:
00:1b.0 Audio device [0403]: Intel Corporation Device [8086:1e20] (rev 04)
```

but when I run
```
sudo aplay -l
```
I still get:
```
aplay: device_list:223: no soundcards found...
```

I've tried rebooting, I've tried removing, purging and reinstalling alsa and pulse. Nothing has worked.
I've used the Try Ubuntu feature from a 12.04 installation USB stick, and sound works there, so there's nothing wrong with my sound card or my speakers.

Anyone got any more things for me to try?


Edit: Solved it!

> **Temüjin said:**
> 10.04 is EOL and relatively ancient compared to your hardware. You need to try a newer kernel for updated sound modules: [http://askubuntu.com/questions/47796/can-i-update-the-kernel-of-my-10-04-lts-to-the-latest-kernel#47797](http://askubuntu.com/questions/47796/can-i-update-the-kernel-of-my-10-04-lts-to-the-latest-kernel#47797)
Thanks!

I ran
```
[FONT=Ubuntu Mono]sudo apt-get install linux-image-generic-lts-backport-oneiric[/FONT]
```[FONT=Ubuntu Mono]
and
```
sudo apt-get install linux-headers-generic-lts-backport-oneiric
```[/FONT][FONT=Ubuntu Mono]
[FONT=Verdana]And once those were complete an Update Manager popped up with a bunch of packages to update.
I let it update all those packages and now I'm going to reboot and see if I've got sound.

Edit:
I'm back after rebooting, aplay -l now lists some devices, and after I un-muted it in the mixer, my speakers work!
Thanks for the help!
[/FONT][/FONT]


[COLOR=#222222][FONT=Times New Roman]> **kevin34ct said:**
> Ok so I read the guides, and it doesn't have anything on my problem. When I am playing back sound, any sound, be it games, music or movies, my sound randomly gets loud then it will get soft. It happens with my speakers. I am using on-board sound which uses the ALC888 sound device. (Nvidia chipset). I haven't tried it with headphones plugged into the speaker jacks because I use Bluetooth headphones which don't have this problem. I'm still new at Linux so I will need some instructions on what to get for you, and what to do.
This happened to me on my windows PC and it turned out that it was a problem with my speakers. The volume control hardware of my speakers was dying and the way I solved it was by buying a new set of speakers.[/FONT][/COLOR]

---

### Post by marinecomm on 2013-06-06
I was troubleshooting my sound issues with spotify when all of a sudden the pulseaudio button disappeared. When I go to Applications Menu -> Multimedia -> Pulseaudio Volume Control I get the following error message:

Fatal Error: Unable to connect to Pulseaudio: OK

I have verified that pulseaudio is installed but is not running. How do I get pulseaudio up and running again?

---

### Post by Yellow Pasque on 2013-06-06
Sometimes, the pulse configuration gets screwed up. Try:
```
rm -r ~/.pulse*; pulseaudio -k
```

---

### Post by marinecomm on 2013-06-06
I get the following error message:

E: [pulseaudio] main.c: Failed to kill daemon: No such process

---

### Post by Yellow Pasque on 2013-06-06
@marinecomm: i'm just going to use your thread since you started one.

---

### Post by marinecomm on 2013-06-06
I can get sound in my headphones and that it. Besies, it's shoddy quality at that.

---

### Post by marinecomm on 2013-06-07
Update: I have sound now even in Spotify. Now my only issue is that whenever I restart the computer the sound volume starts out really low and I have to open the Pulseaudio Volume Control to turn it up.

---

### Post by sb1966 on 2013-06-07
Hi all, I have a similar problem. I had Ubuntu 10.04 in Dell inspiron N5010 and both my built-in speakers were working perfectly. Yesterday I have installed Ubuntu 12.04LTs and now my left speaker is not working at all. I have tried all the alsa plugins from software center and synaptic manager, but not getting any result. Pl. help. Thanks in advance.

---

### Post by HousieMousie2 on 2013-06-16
Some strangeness here:

Installed fresh 13.04 from cd.  No sound.
Deleted . files in home dir.  No sound.
Booted to Guest log in... sound ONCE (the start-up tones - Kubuntu.)  No other sounds and none since, including the start-up tones.

I have run through a few different guides, and out-puts look fine (to my untrained eye anyway).
I have no idea where to go from here.

```
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

```
lspci -v | grep -A7 -i "audio"
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
        Subsystem: Toshiba America Info Systems Device ff1e
        Flags: bus master, fast devsel, latency 0, IRQ 44
        Memory at d6700000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: snd_hda_intel

00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03) (prog-if 00 [Normal decode])

```

```
pacmd
Welcome to PulseAudio! Use "help" for usage information.
>>> list-sinks
1 sink(s) available.
  * index: 0
        name: <alsa_output.pci-0000_00_1b.0.analog-stereo>
        driver: <module-alsa-card.c>
        flags: HARDWARE HW_MUTE_CTRL HW_VOLUME_CTRL DECIBEL_VOLUME LATENCY DYNAMIC_LATENCY
        state: SUSPENDED
        suspend cause: IDLE 
        priority: 9959
        volume: 0: 100% 1: 100%
                0: 0.00 dB 1: 0.00 dB
                balance 0.00
        base volume: 100%
                     0.00 dB
        volume steps: 65537
        muted: no
        current latency: 0.00 ms
        max request: 0 KiB
        max rewind: 0 KiB
        monitor source: 0
        sample spec: s16le 2ch 48000Hz
        channel map: front-left,front-right
                     Stereo
        used by: 0
        linked by: 0
        configured latency: 0.00 ms; range is 0.50 .. 341.33 ms
        card: 0 <alsa_card.pci-0000_00_1b.0>
        module: 4
        properties:
                alsa.resolution_bits = "16"
                device.api = "alsa"
                device.class = "sound"
                alsa.class = "generic"
                alsa.subclass = "generic-mix"
                alsa.name = "CONEXANT Analog"
                alsa.id = "CONEXANT Analog"
                alsa.subdevice = "0"
                alsa.subdevice_name = "subdevice #0"
                alsa.device = "0"
                alsa.card = "0"
                alsa.card_name = "HDA Intel"
                alsa.long_card_name = "HDA Intel at 0xd6700000 irq 44"
                alsa.driver_name = "snd_hda_intel"
                device.bus_path = "pci-0000:00:1b.0"
                sysfs.path = "/devices/pci0000:00/0000:00:1b.0/sound/card0"
                device.bus = "pci"
                device.vendor.id = "8086"
                device.vendor.name = "Intel Corporation"
                device.product.name = "82801I (ICH9 Family) HD Audio Controller"
                device.form_factor = "internal"
                device.string = "front:0"
                device.buffering.buffer_size = "65536"
                device.buffering.fragment_size = "32768"
                device.access_mode = "mmap+timer"
                device.profile.name = "analog-stereo"
                device.profile.description = "Analog Stereo"
                device.description = "Built-in Audio Analog Stereo"
                alsa.mixer_name = "Conexant CX20585"
                alsa.components = "HDA:14f15069,1179fde0,00100302"
                module-udev-detect.discovered = "1"
                device.icon_name = "audio-card-pci"
        ports:
                analog-output: Analog Output (priority 9900, latency offset 0 usec, available: unknown)
                        properties:

        active port: <analog-output>
>>> 

```

```
speaker-test

speaker-test 1.0.25

Playback device is default
Stream parameters are 48000Hz, S16_LE, 1 channels
Using 16 octaves of pink noise
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 192 to 2097152
Period size range from 64 to 699051
Using max buffer size 2097152
Periods = 4
was set period_size = 524288
was set buffer_size = 2097152
 0 - Front Left
Time per period = 11.367240

```
^It goes on for a while, repeating the Front Left... but there is no sound.

I would be grateful for any help!

---

### Post by Fred Le Rouge on 2013-06-22
Hello everyone,
I recently installed Lubuntu 13.04 64 bits on a friend's laptop HP  Compaq 6735s but there is no sound. There is sound from the headphones  but not from the integrated speakers. We found a lot of similar problems  on the internet but the proposed solutions did not work for his laptop.  Indeed most of the solutions date back from Ubuntu 8.04 or 8.10.
Here are some informations about the sound card :

HDA ATI SB
AD198x Analog
AD1984A
SBx00 Azalia (Intel HDA)
Analog Devices ID 194a
LSI ID 1040

Could you help us please?

---

### Post by Yellow Pasque on 2013-06-22
^Perhaps this is related: [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1100010](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1100010)

---

### Post by Fred Le Rouge on 2013-06-23
This is not precesely my problem : I have sound through mini-jeck but not through integrated speakers.
I tried what is explained here [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto) but it did not work.
I modified the file /etc/modprobe.d/alsa-base.conf by adding  ```
options snd-hda-intel model=mobile
``` or ```
options  snd-hda-intel model=laptop
``` at the end, I rebooted but it did not  work.
Any idea?

---

### Post by alexftw. on 2013-07-02
I have a rather rare problem: I only get mono sound on the headphones  jack, the built-in notebook speakers are working just fine.

```
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
```

```
[alexander@alexander-p6634 ~]$ LANG=C aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: CX20585 Analog [CX20585 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 1: CX20585 Digital [CX20585 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

EDIT: fixed after a reboot. don't know if it's fixed with jackd too.
edit2: fixed with jackd too. strange.

---

### Post by Fred Le Rouge on 2013-07-03
Problem solved ! I installed Lubuntu 12.04 and then updated to 12.10 and 13.04 and it worked ! I remembered that the parameters worked in 12.04 so I updated gradually to 13.04 so that the sound parameters would not change.

---

### Post by alexftw. on 2013-07-03
The same problem with mono sound came back again when I used jack today. Strange...

---

### Post by Yellow Pasque on 2013-07-03
> **alexftw. said:**
> The same problem with mono sound came back again when I used jack today. Strange...

[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by alexftw. on 2013-07-04
```
!!################################
!!ALSA Information Script v 0.4.62
!!################################

!!Script ran on: Thu Jul  4 08:21:55 UTC 2013


!!Linux Distribution
!!------------------

Arch Linux \r (\l) NAME="Arch Linux" ID=arch PRETTY_NAME="Arch Linux" HOME_URL="https://www.archlinux.org/" SUPPORT_URL="https://bbs.archlinux.org/" BUG_REPORT_URL="https://bugs.archlinux.org/"


!!DMI Information
!!---------------

Manufacturer:      Medion
Product Name:      P6634
Product Version:   1.0       
Firmware Version:  202


!!Kernel Information
!!------------------

Kernel release:    3.9.8-1-ARCH
Operating System:  GNU/Linux
Architecture:      x86_64
Processor:         unknown
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     k3.9.8-1-ARCH
Library version:    1.0.27.1
Utilities version:  1.0.27.1


!!Loaded ALSA modules
!!-------------------

snd_hda_intel


!!Sound Servers on this system
!!----------------------------

Pulseaudio:
      Installed - Yes (/usr/bin/pulseaudio)
      Running - No


!!Soundcards recognised by ALSA
!!-----------------------------

 0 [PCH            ]: HDA-Intel - HDA Intel PCH
                      HDA Intel PCH at 0xf7000000 irq 49


!!PCI Soundcards installed in the system
!!--------------------------------------

00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)


!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!-------------------------------------------------------

00:1b.0 0403: 8086:1c20 (rev 05)
    Subsystem: 1b0a:20b2


!!Loaded sound module options
!!---------------------------

!!Module: snd_hda_intel
    align_buffer_size : -1
    bdl_pos_adj : 1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
    beep_mode : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
    enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
    enable_msi : -1
    id : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
    index : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
    jackpoll_ms : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
    model : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
    patch : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
    position_fix : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
    power_save : 0
    power_save_controller : Y
    probe_mask : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
    probe_only : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
    single_cmd : N
    snoop : Y


!!HDA-Intel Codec information
!!---------------------------
--startcollapse--

Codec: Conexant CX20585
Address: 0
AFG Function Id: 0x1 (unsol 1)
Vendor Id: 0x14f15069
Subsystem Id: 0x1b0a20b2
Revision Id: 0x100302
No Modem Function Group found
Default PCM:
    rates [0x160]: 44100 48000 96000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
State of AFG node 0x01:
  Power states:  D0 D1 D2 D3 D3cold CLKSTOP
  Power: setting=D0, actual=D0
GPIO: io=4, o=0, i=0, unsolicited=1, wake=0
  IO[0]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[1]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[2]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[3]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
Node 0x10 [Audio Output] wcaps 0xc1d: Stereo Amp-Out R/L
  Control: name="Headphone Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Control: name="Headphone Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Device: name="CX20585 Analog", type="Audio", device=0
  Amp-Out caps: ofs=0x4a, nsteps=0x4a, stepsize=0x03, mute=1
  Amp-Out vals:  [0x46 0x46]
  Converter: stream=8, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
Node 0x11 [Audio Output] wcaps 0xc1d: Stereo Amp-Out R/L
  Control: name="Speaker Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Control: name="Speaker Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x4a, nsteps=0x4a, stepsize=0x03, mute=1
  Amp-Out vals:  [0x80 0x80]
  Converter: stream=8, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
Node 0x12 [Audio Output] wcaps 0x611: Stereo Digital
  Control: name="IEC958 Playback Con Mask", index=16, device=0
  Control: name="IEC958 Playback Pro Mask", index=16, device=0
  Control: name="IEC958 Playback Default", index=16, device=0
  Control: name="IEC958 Playback Switch", index=16, device=0
  Control: name="IEC958 Default PCM Playback Switch", index=0, device=0
  Device: name="CX20585 Digital", type="SPDIF", device=1
  Converter: stream=8, channel=0
  Digital: Enabled
  Digital category: 0x0
  IEC Coding Type: 0x0
  PCM:
    rates [0x160]: 44100 48000 96000
    bits [0xe]: 16 20 24
    formats [0x5]: PCM AC3
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
Node 0x13 [Beep Generator Widget] wcaps 0x70000c: Mono Amp-Out
  Control: name="Beep Playback Volume", index=0, device=0
    ControlAmp: chs=1, dir=Out, idx=0, ofs=0
  Control: name="Beep Playback Switch", index=0, device=0
    ControlAmp: chs=1, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x07, nsteps=0x07, stepsize=0x0f, mute=0
  Amp-Out vals:  [0x00]
Node 0x14 [Audio Input] wcaps 0x100d1b: Stereo Amp-In R/L
  Control: name="Capture Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Control: name="Capture Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Device: name="CX20585 Analog", type="Audio", device=0
  Amp-In caps: ofs=0x4a, nsteps=0x50, stepsize=0x03, mute=1
  Amp-In vals:  [0x50 0x50] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Converter: stream=4, channel=0
  SDI-Select: 0
  PCM:
    rates [0x160]: 44100 48000 96000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
  Connection: 4
     0x17* 0x18 0x23 0x24
Node 0x15 [Audio Input] wcaps 0x100d1b: Stereo Amp-In R/L
  Amp-In caps: ofs=0x4a, nsteps=0x50, stepsize=0x03, mute=1
  Amp-In vals:  [0x4a 0x4a] [0x4a 0x4a] [0x4a 0x4a] [0x4a 0x4a]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x160]: 44100 48000 96000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
  Connection: 4
     0x17* 0x18 0x23 0x24
Node 0x16 [Audio Input] wcaps 0x100d1b: Stereo Amp-In R/L
  Amp-In caps: ofs=0x4a, nsteps=0x50, stepsize=0x03, mute=1
  Amp-In vals:  [0x4a 0x4a] [0x4a 0x4a] [0x4a 0x4a] [0x4a 0x4a]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x160]: 44100 48000 96000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
  Connection: 4
     0x17* 0x18 0x23 0x24
Node 0x17 [Audio Selector] wcaps 0x30050d: Stereo Amp-Out
  Control: name="Mic Boost Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x00, nsteps=0x04, stepsize=0x27, mute=0
  Amp-Out vals:  [0x00 0x00]
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
  Connection: 4
     0x1a* 0x1b 0x1d 0x1e
Node 0x18 [Audio Selector] wcaps 0x30050d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x04, stepsize=0x27, mute=0
  Amp-Out vals:  [0x00 0x00]
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
  Connection: 4
     0x1a* 0x1b 0x1d 0x1e
Node 0x19 [Pin Complex] wcaps 0x400581: Stereo
  Control: name="Headphone Jack", index=0, device=0
  Pincap 0x0000001c: OUT HP Detect
  Pin Default 0x04211040: [Jack] HP Out at Ext Right
    Conn = 1/8, Color = Black
    DefAssociation = 0x4, Sequence = 0x0
  Pin-ctls: 0xc0: OUT HP
  Unsolicited: tag=01, enabled=1
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
  Connection: 2
     0x10* 0x11
Node 0x1a [Pin Complex] wcaps 0x400481: Stereo
  Control: name="Internal Mic Phantom Jack", index=0, device=0
  Pincap 0x00001324: IN Detect
    Vref caps: HIZ 50 80
  Pin Default 0x90a70120: [Fixed] Mic at Int N/A
    Conn = Analog, Color = Unknown
    DefAssociation = 0x2, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
Node 0x1b [Pin Complex] wcaps 0x400581: Stereo
  Control: name="Mic Jack", index=0, device=0
  Pincap 0x00011334: IN OUT EAPD Detect
    Vref caps: HIZ 50 80
  EAPD 0x2: EAPD
  Pin Default 0x04a11030: [Jack] Mic at Ext Right
    Conn = 1/8, Color = Black
    DefAssociation = 0x3, Sequence = 0x0
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=02, enabled=1
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
  Connection: 2
     0x10* 0x11
Node 0x1c [Pin Complex] wcaps 0x400581: Stereo
  Pincap 0x00000014: OUT Detect
  Pin Default 0x400001f0: [N/A] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
  Connection: 2
     0x10* 0x11
Node 0x1d [Pin Complex] wcaps 0x400581: Stereo
  Pincap 0x00010034: IN OUT EAPD Detect
  EAPD 0x2: EAPD
  Pin Default 0x400001f0: [N/A] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
  Connection: 2
     0x10* 0x11
Node 0x1e [Pin Complex] wcaps 0x400481: Stereo
  Pincap 0x00000024: IN Detect
  Pin Default 0x400001f0: [N/A] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
Node 0x1f [Pin Complex] wcaps 0x400501: Stereo
  Control: name="Speaker Phantom Jack", index=0, device=0
  Pincap 0x00000010: OUT
  Pin Default 0x90170110: [Fixed] Speaker at Int N/A
    Conn = Analog, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
  Connection: 2
     0x10 0x11*
Node 0x20 [Pin Complex] wcaps 0x400781: Stereo Digital
  Control: name="SPDIF Phantom Jack", index=0, device=0
  Pincap 0x00000010: OUT
  Pin Default 0x044511f0: [Jack] SPDIF Out at Ext Right
    Conn = Optical, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
  Connection: 1
     0x12
Node 0x21 [Audio Output] wcaps 0x611: Stereo Digital
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  IEC Coding Type: 0x0
  PCM:
    rates [0x160]: 44100 48000 96000
    bits [0xe]: 16 20 24
    formats [0x5]: PCM AC3
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
Node 0x22 [Pin Complex] wcaps 0x400781: Stereo Digital
  Pincap 0x00000010: OUT
  Pin Default 0x400001f0: [N/A] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
  Connection: 1
     0x21
Node 0x23 [Pin Complex] wcaps 0x40040b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x04, stepsize=0x2f, mute=0
  Amp-In vals:  [0x00 0x00]
  Pincap 0x00000020: IN
  Pin Default 0x400001f0: [N/A] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
Node 0x24 [Audio Mixer] wcaps 0x20050b: Stereo Amp-In
  Amp-In caps: ofs=0x4a, nsteps=0x4a, stepsize=0x03, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
  Connection: 2
     0x10 0x11
Node 0x25 [Vendor Defined Widget] wcaps 0xf00000: Mono
Codec: Intel CougarPoint HDMI
Address: 3
AFG Function Id: 0x1 (unsol 0)
Vendor Id: 0x80862805
Subsystem Id: 0x1b0a204a
Revision Id: 0x100000
No Modem Function Group found
Default PCM:
    rates [0x0]:
    bits [0x0]:
    formats [0x0]:
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
State of AFG node 0x01:
  Power states:  D0 D3 CLKSTOP EPSS
  Power: setting=D0, actual=D0, Clock-stop-OK
GPIO: io=0, o=0, i=0, unsolicited=0, wake=0
Node 0x02 [Audio Output] wcaps 0x6611: 8-Channels Digital
  Converter: stream=0, channel=0
  Digital: Enabled
  Digital category: 0x0
  IEC Coding Type: 0x0
  PCM:
    rates [0x7f0]: 32000 44100 48000 88200 96000 176400 192000
    bits [0x1e]: 16 20 24 32
    formats [0x5]: PCM AC3
  Power states:  D0 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x03 [Audio Output] wcaps 0x6611: 8-Channels Digital
  Converter: stream=0, channel=0
  Digital: Enabled
  Digital category: 0x0
  IEC Coding Type: 0x0
  PCM:
    rates [0x7f0]: 32000 44100 48000 88200 96000 176400 192000
    bits [0x1e]: 16 20 24 32
    formats [0x5]: PCM AC3
  Power states:  D0 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x04 [Audio Output] wcaps 0x6611: 8-Channels Digital
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  IEC Coding Type: 0x0
  PCM:
    rates [0x7f0]: 32000 44100 48000 88200 96000 176400 192000
    bits [0x1e]: 16 20 24 32
    formats [0x5]: PCM AC3
  Power states:  D0 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x05 [Pin Complex] wcaps 0x40778d: 8-Channels Digital Amp-Out CP
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x80]
  Pincap 0x09000094: OUT Detect HBR HDMI DP
  Pin Default 0x58560010: [N/A] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x02
Node 0x06 [Pin Complex] wcaps 0x40778d: 8-Channels Digital Amp-Out CP
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x80]
  Pincap 0x09000094: OUT Detect HBR HDMI DP
  Pin Default 0x58560020: [N/A] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x2, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x03
Node 0x07 [Pin Complex] wcaps 0x40778d: 8-Channels Digital Amp-Out CP
  Control: name="HDMI/DP,pcm=3 Jack", index=0, device=0
  Control: name="IEC958 Playback Con Mask", index=0, device=0
  Control: name="IEC958 Playback Pro Mask", index=0, device=0
  Control: name="IEC958 Playback Default", index=0, device=0
  Control: name="IEC958 Playback Switch", index=0, device=0
  Control: name="ELD", index=0, device=3
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x09000094: OUT Detect HBR HDMI DP
  Pin Default 0x18560030: [Jack] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x3, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=01, enabled=1
  Power states:  D0 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x04
Node 0x08 [Vendor Defined Widget] wcaps 0xf00000: Mono
--endcollapse--


!!ALSA Device nodes
!!-----------------

crw-rw----+ 1 root audio 116,  8 Jul  4 09:48 /dev/snd/controlC0
crw-rw----+ 1 root audio 116,  7 Jul  4 09:48 /dev/snd/hwC0D0
crw-rw----+ 1 root audio 116,  6 Jul  4 09:48 /dev/snd/hwC0D3
crw-rw----+ 1 root audio 116,  5 Jul  4 10:18 /dev/snd/pcmC0D0c
crw-rw----+ 1 root audio 116,  4 Jul  4 10:19 /dev/snd/pcmC0D0p
crw-rw----+ 1 root audio 116,  3 Jul  4 10:18 /dev/snd/pcmC0D1p
crw-rw----+ 1 root audio 116,  2 Jul  4 09:49 /dev/snd/pcmC0D3p
crw-rw----+ 1 root audio 116,  1 Jul  4 10:18 /dev/snd/seq
crw-rw----+ 1 root audio 116, 33 Jul  4 09:48 /dev/snd/timer

/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root  60 Jul  4 09:48 .
drwxr-xr-x 3 root root 240 Jul  4 09:48 ..
lrwxrwxrwx 1 root root  12 Jul  4 09:48 pci-0000:00:1b.0 -> ../controlC0


!!ALSA configuration files
!!------------------------

!!User specific config file (~/.asoundrc)

pcm.snd_card {
        type hw
        card 0
        device 0
    channels 2
}

ctl.snd_card {
        type hw
        card 0
        device 0
    channels 2
}


!!System wide config file (/etc/asound.conf)

# Use PulseAudio by default
pcm.!default {
  type pulse
  fallback "sysdefault"
  hint {
    show on
    description "Default ALSA Output (currently PulseAudio Sound Server)"
  }
}

ctl.!default {
  type pulse
  fallback "sysdefault"
}


# vim:set ft=alsaconf:


!!Aplay/Arecord output
!!--------------------

APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: CX20585 Analog [CX20585 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 1: CX20585 Digital [CX20585 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

ARECORD

**** List of CAPTURE Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: CX20585 Analog [CX20585 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

!!Amixer output
!!-------------

!!-------Mixer controls for card 0 [PCH]

Card hw:0 'PCH'/'HDA Intel PCH at 0xf7000000 irq 49'
  Mixer name    : 'Intel CougarPoint HDMI'
  Components    : 'HDA:14f15069,1b0a20b2,00100302 HDA:80862805,1b0a204a,00100000'
  Controls      : 34
  Simple ctrls  : 12
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 74
  Mono: Playback 70 [95%] [-4.00dB] [on]
Simple mixer control 'Headphone',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 74
  Mono:
  Front Left: Playback 74 [100%] [0.00dB] [on]
  Front Right: Playback 74 [100%] [0.00dB] [on]
Simple mixer control 'Speaker',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 74
  Mono:
  Front Left: Playback 0 [0%] [-74.00dB] [off]
  Front Right: Playback 0 [0%] [-74.00dB] [off]
Simple mixer control 'PCM',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 254 [100%] [0.20dB]
  Front Right: Playback 254 [100%] [0.20dB]
Simple mixer control 'Mic Boost',0
  Capabilities: volume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 4
  Front Left: 0 [0%] [0.00dB]
  Front Right: 0 [0%] [0.00dB]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'IEC958 Default PCM',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'IEC958',16
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Beep',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 7
  Mono: Playback 0 [0%] [-28.00dB] [off]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 80
  Front Left: Capture 80 [100%] [6.00dB] [on]
  Front Right: Capture 80 [100%] [6.00dB] [on]
Simple mixer control 'Auto-Mute Mode',0
  Capabilities: enum
  Items: 'Disabled' 'Enabled'
  Item0: 'Enabled'
Simple mixer control 'Digital',0
  Capabilities: cvolume
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 120
  Front Left: Capture 120 [100%] [30.00dB]
  Front Right: Capture 120 [100%] [30.00dB]


!!Alsactl output
!!--------------

--startcollapse--
state.PCH {
    control.1 {
        iface MIXER
        name 'Headphone Playback Volume'
        value.0 74
        value.1 74
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 74'
            dbmin -7400
            dbmax 0
            dbvalue.0 0
            dbvalue.1 0
        }
    }
    control.2 {
        iface MIXER
        name 'Headphone Playback Switch'
        value.0 true
        value.1 true
        comment {
            access 'read write'
            type BOOLEAN
            count 2
        }
    }
    control.3 {
        iface MIXER
        name 'Speaker Playback Volume'
        value.0 0
        value.1 0
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 74'
            dbmin -7400
            dbmax 0
            dbvalue.0 -7400
            dbvalue.1 -7400
        }
    }
    control.4 {
        iface MIXER
        name 'Speaker Playback Switch'
        value.0 false
        value.1 false
        comment {
            access 'read write'
            type BOOLEAN
            count 2
        }
    }
    control.5 {
        iface MIXER
        name 'Auto-Mute Mode'
        value Enabled
        comment {
            access 'read write'
            type ENUMERATED
            count 1
            item.0 Disabled
            item.1 Enabled
        }
    }
    control.6 {
        iface MIXER
        name 'Capture Volume'
        value.0 80
        value.1 80
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 80'
            dbmin -7400
            dbmax 600
            dbvalue.0 600
            dbvalue.1 600
        }
    }
    control.7 {
        iface MIXER
        name 'Capture Switch'
        value.0 true
        value.1 true
        comment {
            access 'read write'
            type BOOLEAN
            count 2
        }
    }
    control.8 {
        iface MIXER
        name 'Mic Boost Volume'
        value.0 0
        value.1 0
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 4'
            dbmin 0
            dbmax 4000
            dbvalue.0 0
            dbvalue.1 0
        }
    }
    control.9 {
        iface MIXER
        name 'IEC958 Playback Con Mask'
        index 16
        value '0fff000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
        comment {
            access read
            type IEC958
            count 1
        }
    }
    control.10 {
        iface MIXER
        name 'IEC958 Playback Pro Mask'
        index 16
        value '0f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
        comment {
            access read
            type IEC958
            count 1
        }
    }
    control.11 {
        iface MIXER
        name 'IEC958 Playback Default'
        index 16
        value '0400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
        comment {
            access 'read write'
            type IEC958
            count 1
        }
    }
    control.12 {
        iface MIXER
        name 'IEC958 Playback Switch'
        index 16
        value true
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.13 {
        iface MIXER
        name 'IEC958 Default PCM Playback Switch'
        value true
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.14 {
        iface MIXER
        name 'Master Playback Volume'
        value 70
        comment {
            access 'read write'
            type INTEGER
            count 1
            range '0 - 74'
            dbmin -7400
            dbmax 0
            dbvalue.0 -400
        }
    }
    control.15 {
        iface MIXER
        name 'Master Playback Switch'
        value true
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.16 {
        iface CARD
        name 'Headphone Jack'
        value true
        comment {
            access read
            type BOOLEAN
            count 1
        }
    }
    control.17 {
        iface CARD
        name 'Speaker Phantom Jack'
        value true
        comment {
            access read
            type BOOLEAN
            count 1
        }
    }
    control.18 {
        iface CARD
        name 'Mic Jack'
        value false
        comment {
            access read
            type BOOLEAN
            count 1
        }
    }
    control.19 {
        iface CARD
        name 'Internal Mic Phantom Jack'
        value true
        comment {
            access read
            type BOOLEAN
            count 1
        }
    }
    control.20 {
        iface CARD
        name 'SPDIF Phantom Jack'
        value true
        comment {
            access read
            type BOOLEAN
            count 1
        }
    }
    control.21 {
        iface MIXER
        name 'Beep Playback Volume'
        value 0
        comment {
            access 'read write'
            type INTEGER
            count 1
            range '0 - 7'
            dbmin -2800
            dbmax 0
            dbvalue.0 -2800
        }
    }
    control.22 {
        iface MIXER
        name 'Beep Playback Switch'
        value false
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.23 {
        iface PCM
        name 'Playback Channel Map'
        value.0 0
        value.1 0
        comment {
            access read
            type INTEGER
            count 2
            range '0 - 36'
        }
    }
    control.24 {
        iface PCM
        name 'Capture Channel Map'
        value.0 0
        value.1 0
        comment {
            access read
            type INTEGER
            count 2
            range '0 - 36'
        }
    }
    control.25 {
        iface PCM
        device 1
        name 'Playback Channel Map'
        value.0 0
        value.1 0
        comment {
            access read
            type INTEGER
            count 2
            range '0 - 36'
        }
    }
    control.26 {
        iface CARD
        name 'HDMI/DP,pcm=3 Jack'
        value false
        comment {
            access read
            type BOOLEAN
            count 1
        }
    }
    control.27 {
        iface MIXER
        name 'IEC958 Playback Con Mask'
        value '0fff000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
        comment {
            access read
            type IEC958
            count 1
        }
    }
    control.28 {
        iface MIXER
        name 'IEC958 Playback Pro Mask'
        value '0f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
        comment {
            access read
            type IEC958
            count 1
        }
    }
    control.29 {
        iface MIXER
        name 'IEC958 Playback Default'
        value '0400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
        comment {
            access 'read write'
            type IEC958
            count 1
        }
    }
    control.30 {
        iface MIXER
        name 'IEC958 Playback Switch'
        value false
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.31 {
        iface PCM
        device 3
        name ELD
        value ''
        comment {
            access 'read volatile'
            type BYTES
            count 0
        }
    }
    control.32 {
        iface PCM
        device 3
        name 'Playback Channel Map'
        value.0 0
        value.1 0
        value.2 0
        value.3 0
        value.4 0
        value.5 0
        value.6 0
        value.7 0
        comment {
            access 'read write'
            type INTEGER
            count 8
            range '0 - 36'
        }
    }
    control.33 {
        iface MIXER
        name 'PCM Playback Volume'
        value.0 254
        value.1 254
        comment {
            access 'read write user'
            type INTEGER
            count 2
            range '0 - 255'
            tlv '0000000100000008ffffec1400000014'
            dbmin -5100
            dbmax 0
            dbvalue.0 -20
            dbvalue.1 -20
        }
    }
    control.34 {
        iface MIXER
        name 'Digital Capture Volume'
        value.0 120
        value.1 120
        comment {
            access 'read write user'
            type INTEGER
            count 2
            range '0 - 120'
            tlv '0000000100000008fffff44800000032'
            dbmin -3000
            dbmax 3000
            dbvalue.0 3000
            dbvalue.1 3000
        }
    }
}
--endcollapse--


!!All Loaded Modules
!!------------------

Module
snd_hrtimer
snd_seq_dummy
snd_seq
snd_seq_device
fuse
bbswitch
btusb
bluetooth
uvcvideo
videobuf2_vmalloc
videobuf2_memops
videobuf2_core
videodev
media
joydev
intel_powerclamp
coretemp
kvm_intel
kvm
crc32_pclmul
crc32c_intel
snd_hda_codec_hdmi
snd_hda_codec_conexant
snd_hda_intel
ghash_clmulni_intel
arc4
cryptd
microcode
iwldvm
snd_hda_codec
mac80211
snd_hwdep
mxm_wmi
mperf
iTCO_wdt
iTCO_vendor_support
atl1c
lpc_ich
mei
snd_pcm
snd_page_alloc
snd_timer
snd
soundcore
psmouse
thermal
serio_raw
iwlwifi
cfg80211
rfkill
i2c_i801
processor
evdev
wmi
battery
ac
vboxdrv
ext4
crc16
mbcache
jbd2
hid_generic
hid_cherry
usbhid
hid
sr_mod
sd_mod
cdrom
ata_generic
pata_acpi
ata_piix
libata
ehci_pci
xhci_hcd
ehci_hcd
scsi_mod
usbcore
usb_common
i915
video
button
i2c_algo_bit
intel_agp
intel_gtt
drm_kms_helper
drm
i2c_core


!!Sysfs Files
!!-----------

/sys/class/sound/hwC0D0/init_pin_configs:
0x19 0x04211040
0x1a 0x90a70120
0x1b 0x04a11030
0x1c 0x400001f0
0x1d 0x400001f0
0x1e 0x400001f0
0x1f 0x90170110
0x20 0x044511f0
0x22 0x400001f0
0x23 0x400001f0

/sys/class/sound/hwC0D0/driver_pin_configs:

/sys/class/sound/hwC0D0/user_pin_configs:

/sys/class/sound/hwC0D0/init_verbs:

/sys/class/sound/hwC0D0/hints:

/sys/class/sound/hwC0D3/init_pin_configs:
0x05 0x58560010
0x06 0x58560020
0x07 0x18560030

/sys/class/sound/hwC0D3/driver_pin_configs:

/sys/class/sound/hwC0D3/user_pin_configs:

/sys/class/sound/hwC0D3/init_verbs:

/sys/class/sound/hwC0D3/hints:


!!ALSA/HDA dmesg
!!--------------

[    7.020035] systemd-udevd[161]: renamed network interface wlan0 to wlp3s0
[    7.039537] snd_hda_intel 0000:00:1b.0: irq 49 for MSI/MSI-X
[    7.108808] hda_codec: CX20585: BIOS auto-probing.
[    7.110309] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input9
[    7.184868] input: HDA Intel PCH HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[    7.186359] input: HDA Intel PCH Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[    7.186922] input: HDA Intel PCH Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[    7.485891] psmouse serio2: synaptics: Touchpad model: 1, fw: 7.5, id: 0x1c0b1, caps: 0xf00033/0x240000/0xa2400, board id: 1192, fw id: 833639



```

....and one night later, it's fixed again. I'm going to try to figure out what the cause of it is and run speaker-test every few minutes.

---

### Post by Yellow Pasque on 2013-07-04
You're using Arch Linux and posting in ubuntu forums? That's... odd.

---

### Post by alexftw. on 2013-07-04
It's because the problem is neither ubuntu nor arch linux related.

(I had the exact same problem on ubuntu too)

---

### Post by alexftw. on 2013-07-06
It went away a while ago and came back in the last few hours. Tried rebooting, but no luck. I don't know how to reproduce it, or what the cause is. I also tried booting the laptop without starting a loginmanager/xserver, and "speaker-test -c 2 -t wav" but no difference.

---

### Post by HavingFun on 2013-07-08
I'm new to Ubuntu, hope I'm posting in the right place!

I have an Emachines (PC) T5010.  Upgraded  to 13.04 and lost sound.  I completed all steps of the Ubuntu sound  troubleshooting guide here:  [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

One thing that stood out:  When executing this particular tip:


sudo aplay -l

I understand the output of that command should look something like this: 

```
**** List of PLAYBACK Hardware Devices **** card 0: Intel [HDA Intel],  device 0: ALC861VD Analog [ALC861VD Analog]   Subdevices: 0/1    Subdevice #0: subdevice #0
```

I only received this:
```
**** List of PLAYBACK Hardware Devices ****
```


Didn't list the card.  But when I execute this:  lspci -v | grep -A7 -i "audio", 

I do get -

```
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
    Subsystem: Gateway, Inc. Device 4040
    Flags: bus master, fast devsel, latency 0, IRQ 44
    Memory at b01c0000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel

00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6  Family) PCI Express Port 1 (rev 03) (prog-if 00 [Normal decode])
```

Some system info:

uname -a
     
```
Linux emachine-desktop 3.8.0-25-generic #37-Ubuntu SMP Thu Jun 6 20:47:30 UTC 2013 i686 i686 i686 GNU/Linux
```

     
 
lsb_release -a
     ```

No LSB modules are available. Distributor ID:    Ubuntu Description:    Ubuntu 13.04 Release:    13.04 Codename:    raring
```      



ps -ef | grep pulseaudio
     
```

emachine  3149     1  0 08:16 ?        00:00:00 /usr/bin/pulseaudio --start --log-target=syslog emachine  3193  3043  0 08:21 pts/1    00:00:00 grep --color=auto pulseaudio
```     

 
In this case, 3149 process is pulse audio and is taking Very High Priority
3043 process is bash.  

I'm assuming the "?" means I have a Pulseaudio problem?  But I haven't been able to get further.  Any help appreciated.

---

### Post by Yellow Pasque on 2013-07-08
> I'm assuming the "?" means I have a Pulseaudio problem? But I haven't been able to get further. Any help appreciated. 
If aplay doesn't list devices, then your problem runs deeper than Pulseaudio. Give alsa info: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by HavingFun on 2013-07-08
Thank you Temujin with umlauts

Alsa Info here:  [http://www.alsa-project.org/db/?f=4ab88e284bf3a577b7d73fbc8b49c0a35308c50d](http://www.alsa-project.org/db/?f=4ab88e284bf3a577b7d73fbc8b49c0a35308c50d)

---

### Post by Yellow Pasque on 2013-07-08
> **HavingFun said:**
> Alsa Info here:  [http://www.alsa-project.org/db/?f=4ab88e284bf3a577b7d73fbc8b49c0a35308c50d](http://www.alsa-project.org/db/?f=4ab88e284bf3a577b7d73fbc8b49c0a35308c50d)

That's odd that the driver loads, but aplay doesn't show a device. I would file a bug. It might show the problem in the dmesg logs.

you could also try to purge and restore alsa-utils:
```
sudo apt-get purge alsa-utils
sudo apt-get install alsa-utils
```

---

### Post by HavingFun on 2013-07-09
> **Temüjin said:**
>  I would file a bug. 

Thank you Temujin.  Filing a bug

---

### Post by Happy Prancer on 2013-09-07
Hello,

I have a Toshiba S50D-A laptop with Ubuntu 13.04 and there is no sound from the speakers or the headphones. I have been through the two trouble shooting guides listed in this thread as well as several others throughout the web and to my untrained eyes, everything seems to be set up correctly. The sound cards are detected and active. The devices are not muted. The volumes are turned up. I'm not sure what else I can try.

This us a dual-boot system with Windows 8. The sound works fine in Windows 8, but there is no sound whatsoever from the Ubuntu live CD or the Ubuntu installation.

I have pasted my alsa info output here:
[http://paste.ubuntu.com/6075458/](http://paste.ubuntu.com/6075458/)

If someone with more experience would kindly take a look, I would be very grateful. I'm also happy to provide any additional information that might help.

Cheers,

Dan

---

### Post by Yellow Pasque on 2013-09-07
@Happy Prancer:a few suggestions..
- First, since you have relatively new hardware, update the PCI/USB ID databases (replaces numeric's with human readable names):
```
sudo update-pciids
sudo update-usbids
```

- Second, the open-source radeon driver doesn't yet support HDMI audio on newer cards (including Trinity APU), so if you're trying to use HDMI audio, you have to use fglrx/Catalyst driver.

Third, try the latest driver: [https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS)
If it's still not working after a restart, file a bug:
```
ubuntu-bug audio
```

---

### Post by Happy Prancer on 2013-09-07
Hi Temüjin,

Thank you for your fast response!

I tried your suggestions and the sound is still not working with the latest databases and drivers, unfortunately. The problem is with the built-in sound card and built-in speakers. I have not tested the HDMI audio because I don't have a suitable device to test it on.

I have submitted a bug report.

Please let me know if there are any more suggestions.

Cheers,

Dan

---

### Post by mörgæs on 2013-09-07
Please link to the bug report. It will help other users with the same problem.

---

### Post by Happy Prancer on 2013-09-08
Here is the link to the bug report:

[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1222249](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1222249)

No sound from Toshiba Satellite S50D-A laptop with Ubuntu 13.04. HDA Intel.

-Dan

---

### Post by Pablo_Sanabria_M. on 2013-09-10
Hi I've recently upgraded to ubuntu 12.04 and I've sound porblems as well, I've no sound no where whatsoever at my PC. 

I'm using Multimedia audio controller: Silicon Integrated Systems [SiS] SiS7012 AC'97 Sound Controller (rev a0) at a n AMD mother board, my ALSA project is : [http://www.alsa-project.org/db/?f=331987e1ffbb299aeeb80113cb0935ec25a0bd6f](http://www.alsa-project.org/db/?f=331987e1ffbb299aeeb80113cb0935ec25a0bd6f)

Thanks in advance for the help !

---

### Post by Grekkostas on 2013-09-11
Here is my problem . I am using ubuntu 12.04 . I use Rythmbox (the pre-installed player) . Since today when I try to turn the volume up or down -with the sound icon next to the date icon , up and right in the screen- the volume stays the same .. what should i do ? Thanks


Also when i play videos from the internet ,there is no sound

---

### Post by Kreazulle on 2013-11-13
Hello!

I am some sort of a noob in Linux Audio so I`m hoping that my answer will be found among u people.
First of all, I am running Ubuntu 12.04 32 bit (3.8.0-33-generic) on a DELL Optiplex 755 machine (Intel Core 2 Duo, CPU E8400 @ 3.00Ghz x2 with 2Gb of Memory).

On this configuration I have plugg-ed an Yamaha 01v96i audio mixer. My problem is that the system recognizes the device (on [*lsusb]* command, the output is: Bus 002 Device 003: ID 0499:5500 Yamaha Corp., and  [*sudo lsusb -v | less*] outputs even more precise info about the device), but does not recognize it (in Jack or the system for that matter) as audio device nor a midi device. ([*cat /proc/asound/cards*] outputs only the internal sound devive).

Does anyone know if the device I am trying to connect is supported and if it is not, do I have the slightest chance to make it work.

I thank you in advance for your time.

---

### Post by Pablo_Sanabria_M. on 2014-01-17
NOTHING STILL NO SOUND !!! 

 			 				[INDENT] 					Hi I've recently upgraded to ubuntu 12.04 and I've sound porblems as well, I've no sound no where whatsoever at my PC. 

I'm using Multimedia audio controller: Silicon Integrated Systems [SiS]  SiS7012 AC'97 Sound Controller (rev a0) at a n AMD mother board, my ALSA  project is : [http://www.alsa-project.org/db/?f=33...0935ec25a0bd6f]("http://www.alsa-project.org/db/?f=331987e1ffbb299aeeb80113cb0935ec25a0bd6f")

Thanks in advance for the help ! 				

ANY ONE CAN HELP !!
[/INDENT]

---

### Post by juan_pablo3 on 2014-01-21
I have no sound and alsa made this diagnosis [http://ubuntuforums.org/showthread.php?t=1744966](http://ubuntuforums.org/showthread.php?t=1744966) Please help!

---

### Post by teal2 on 2014-01-22
Ubuntu 12.04.4 LTS \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 12.04.4 LTS" NAME="Ubuntu" ID=ubuntu ID_LIKE=debian PRETTY_NAME="Ubuntu precise (12.04.4 LTS)"


!!DMI Information
!!---------------

Manufacturer:      Alienware
Product Name:      M14xR2
Product Version:   A11
Firmware Version:  A11
=======================


No audio from built in speakers. See attachments for terminal outputs

edit: [http://www.alsa-project.org/db/?f=d9cc6676cfc725292b684e7ac6d331371d4a7ea4](http://www.alsa-project.org/db/?f=d9cc6676cfc725292b684e7ac6d331371d4a7ea4)

[ATTACH]249669[/ATTACH][ATTACH]249670[/ATTACH][ATTACH]249671[/ATTACH][ATTACH]249673[/ATTACH]

---

### Post by jawknee530 on 2014-02-14
Ran the whole troubleshooting procedure. 

Alsa info:
[http://www.alsa-project.org/db/?f=9db10d155de2d310919f2a6b2ed6577c96bbad6b](http://www.alsa-project.org/db/?f=9db10d155de2d310919f2a6b2ed6577c96bbad6b)

---

### Post by german3 on 2014-02-24
I have Ubuntu 12.04 LTS installed. The sound worked just fine until Rhythmbox appeared for no reason in the sound panel. After it's appearance the sound disappearad! aplay -l shows this:
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: VT1705 Analog [VT1705 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 2: VT1705 HP [VT1705 HP]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
Does it mean that the sound is just muted somehow? alsamixer has everything unmuted and with volume. I didn't update anything! How could sound disappear and Rhythmbox appear on their own!? I didn't run Rhythmbox! Running of programs on their own is unacceptable.

---

### Post by german3 on 2014-02-24
*

---

### Post by Peter_Brandon on 2014-04-05
New Zen Koan:  What is the sound of ALSA?

I've run into audio problems more than a half dozen times from 12.04 to 13.10 (to which I just upgraded):  My system freezes (typically on a suspend), I hard reboot, I no longer have sound, I spend hours to days trying various things to make the sound work again and have in the past, but usually not with the same method twice in a row.  In 13.10, I just had this happen and I've tried everything fix-related on the two community audio pages and a dozen other help pages, and now nothing works.

The usual stream of advice, which I've just tried to no avail, is:  check if your system recognizes your sound cards (this time it does), make sure sound is on in alsamixer and pavucontrol, try a force restart for alsa / pulseaudio, erase pulse files in /run and .config, try purging and reinstalling all audio related software and system kernel and kernel modules followed by reboot, try installing an audio ppa.  Would think that something is being corrupted by the hard reboot, likely run / config files, but deleting the ones I know about isn't making a difference.

I've tried all of this.  Am open to suggestions.

---

### Post by Peter_Brandon on 2014-04-06
Looks like reinstalling all my audio software and audio ppa a second time did the trick--my audio is back.  I made one small change this time:  13.10 no longer has linux-ubuntu-modules, so I asked for a reinstall for linux-image-extra instead.  It is odd how it's always sound that seems to get knocked out when I hard reboot.  Would be nice if they made the sound system more robust to the inevitable system freeze.

Anyway, what I do to get sound working again, in case it's helpful for anyone (NOTE THIS IS FOR 13.10, not earlier versions):

```

#Purge just the audio ppa software:
sudo dpkg -r --force-depends libpulse-mainloop-glib0 libpulse-mainloop-glib0:i386 libpulse0 libpulse0:i386 libpulsedsp libpulsedsp:i386 pulseaudio pulseaudio-module-gconf pulseaudio-module-bluetooth pulseaudio-module-x11 pulseaudio-utils
#Clean out leftover files:
sudo apt-get autoclean
#install base audio software
sudo apt-get install -f


#Make really sure:
sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-image-extra-`uname -r` libasound2


#REBOOT SYSTEM
#reinstall audio ppa and audio systems:
sudo add-apt-repository ppa:ubuntu-audio-dev/alsa-daily; sudo apt-get update;sudo apt-get dist-upgrade; sudo apt-get install pavucontrol linux-sound-base alsa-base alsa-utils lightdm ubuntu-desktop  linux-image-`uname -r` libasound2; sudo apt-get -y --reinstall install linux-sound-base alsa-base alsa-utils lightdm ubuntu-desktop  linux-image-`uname -r` libasound2; killall pulseaudio; rm -r ~/.pulse*; ubuntu-support-status; sudo usermod -aG `cat /etc/group | grep -e '^pulse:' -e '^audio:' -e '^pulse-access:' -e '^pulse-rt:' -e '^video:' | awk -F: '{print $1}' | tr '\n' ',' | sed 's:,$::g'` `whoami`


#NOTE!!!:  saucy doesn't have a ppa:ubuntu-audio-dev/ppa; but there is a ppa:ubuntu-audio-dev/alsa-daily; so i've put alsa-daily above
#Reboot
#You can test along the way:  just use audio ctrl panel and click on Sound Effects




```

---

### Post by tjqt06 on 2014-04-06
I try all these guide but no luck on my Asus X450L on Ubuntu 12.04 x64. Can you help me to solve this problem? Thanks

---

### Post by Ayeshah on 2014-04-07
Hi,

I am relatively new and am trying to get perfect sound.  I have multiboot options on my laptop and am unable to get the sound/audio working correctly on Ubuntu and Linux - though it is fine in WinXP.

I have tried the various model configurations, position fixes and even changed the loading setting (I think in pulseaudio daemon) - in all honestly the last one I can't remember what I did apart from changing numbers to 5 and 8.

I did one time get perfect audio with no stuttering/choppiness on Linux and haven't been able to since.  The problem is concurrent using different sites and playing objects on the desktop itself through software or my USB dongle.

I have posted my desktop outputs and looked at various forums and cannot muster how I did it?  Can you help seriously please it's been so long........

---

### Post by tjqt06 on 2014-04-09
my problem was solved. it's just a hardware problem. I have replace the whole unit. Thank you.

---

### Post by ganymede62 on 2014-04-18
I just did a fresh install of Kubuntu 14.04 and my sound on the CA0106 device is outputing mono on the left speaker only.  The right speaker is dead silent and I have confirmed it's not a hardware issue. 

I've gone through the sound troubleshooting pages and I didn't find anything related to my problem. 

Is anyone else having a similar issue? 

$ lspci | grep -i Audio
01:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] RV710/730 HDMI Audio [Radeon HD 4000 series]
03:02.0 Multimedia audio controller: Creative Labs CA0106 Soundblaster

---

### Post by ganymede62 on 2014-04-19
> **ganymede62 said:**
> I just did a fresh install of Kubuntu 14.04 and my sound on the CA0106 device is outputing mono on the left speaker only.  The right speaker is dead silent and I have confirmed it's not a hardware issue. 

I've gone through the sound troubleshooting pages and I didn't find anything related to my problem. 

Is anyone else having a similar issue? 

$ lspci | grep -i Audio
01:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] RV710/730 HDMI Audio [Radeon HD 4000 series]
03:02.0 Multimedia audio controller: Creative Labs CA0106 Soundblaster

I found this and it resolved my issue.

[https://bbs.archlinux.org/viewtopic.php?pid=1258381#p1258381](https://bbs.archlinux.org/viewtopic.php?pid=1258381#p1258381)

---

### Post by wmstrome on 2014-05-07
Thanks for this post. With XUbuntu 14.04 I got sound working again after Step #1B in the procedure outlined in the second link you gave:
SoundTroubleshootingProcedure
[https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)

---

### Post by elgalinero on 2014-05-25
Hello people, I have recently installed ubuntu 14.04 on my new desktop. I have an asus xonar dx soundcard with a pair of stereo speakers attached to the output jack and a DAC attached to the optical ouput.
Unfortunately, I have not been able to switch between them so far. In the sound settings, whether I select the analogue or the digital output,  all I get is sound through both the speakers and the DAC.

This is what aplay -l outputs:

```
card 0: PCH [HDA Intel PCH], device 0: ALC1150 Analog [ALC1150 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 1: ALC1150 Digital [ALC1150 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: DX [Xonar DX], device 0: Multichannel [Multichannel]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: DX [Xonar DX], device 1: Digital [Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: HDMI [HDA ATI HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: HDMI [HDA ATI HDMI], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: HDMI [HDA ATI HDMI], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: HDMI [HDA ATI HDMI], device 9: HDMI 3 [HDMI 3]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: HDMI [HDA ATI HDMI], device 10: HDMI 4 [HDMI 4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: HDMI [HDA ATI HDMI], device 11: HDMI 5 [HDMI 5]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

I have tried to fiddle with the settings in the pulseaudio volume control application, but still could not get my system to work properly.

---

### Post by e-San on 2014-06-30
**Disabled ALC662 digital out.**

Hi!

I'm trying to solve problem with my snd-hda-intel based on ALC662.
I have motherboard called 945GCD-CL. It is propably Elitegroup model based on Intel's one.

Due to Intel's limitations manufacturers are prohibited for installing coax/optical S/PDIF out on their motherboards.
So i soldered one straight to chipset pins ;).
This modification is known to work, see  [http://www.bloguemos.com/?p=46](http://www.bloguemos.com/?p=46) or  [http://techieventures.blogspot.com/2010/09/solved-realtek-alc662-on-linux.html](http://techieventures.blogspot.com/2010/09/solved-realtek-alc662-on-linux.html)
And i did this on two other simillar devices, both worked.

So, i have this modification and I'm trying to put my sound out on this device throught S/PDIF.
But it does not work, possibly due to something weird...

According to sources i mention, i tried various *model*:```
options snd-hda-intel power_save=0 
options snd-hda-intel power_save_controller=N 
options snd-hda-intel model=3stack-dig
```

But there is no S/PDIF swich on alsamixer.

Looking deeper i've found *aplay -l* giveing:
```
**** List of PLAYBACK Hardware Devices ****card 0: Intel [HDA Intel], device 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

while this should be:
```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC662 rev1 Digital [ALC662 rev1 Digital]
  Subdevices: 1/1   Subdevice #0: subdevice #0
```

Some info from dmesg:
```
[   26.717792] snd_hda_intel 0000:00:1b.0: irq 41 for MSI/MSI-X
[   26.812993] SKU: Nid=0x1d sku_cfg=0x4004c601
[   26.813003] SKU: port_connectivity=0x1
[   26.813008] SKU: enable_pcbeep=0x0
[   26.813013] SKU: check_sum=0x00000004
[   26.813018] SKU: customization=0x000000c6
[   26.813022] SKU: external_amp=0x0
[   26.813027] SKU: platform_type=0x0
[   26.813031] SKU: swap=0x0
[   26.813036] SKU: override=0x1
[   26.813301] autoconfig: line_outs=1 (0x14/0x0/0x0/0x0/0x0) type:line
[   26.813308]    speaker_outs=1 (0x15/0x0/0x0/0x0/0x0)
[   26.813314]    hp_outs=1 (0x1b/0x0/0x0/0x0/0x0)
[   26.813319]    mono: mono_out=0x0
[   26.813323]    inputs:
[   26.813330]      Front Mic=0x19
[   26.813335]      Rear Mic=0x18
[   26.813341]      Line=0x1a
[   26.813347] realtek: No valid SSID, checking pincfg 0x4004c601 for NID 0x1d
[   26.813353] realtek: Enabling init ASM_ID=0xc601 CODEC_ID=10ec0662
[   26.828688] input: HDA Intel Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card1/input9
[   26.829402] input: HDA Intel Line Out as /devices/pci0000:00/0000:00:1b.0/sound/card1/input8
[   26.830069] input: HDA Intel Line as /devices/pci0000:00/0000:00:1b.0/sound/card1/input7
[   26.830758] input: HDA Intel Rear Mic as /devices/pci0000:00/0000:00:1b.0/sound/card1/input6
[   26.831424] input: HDA Intel Front Mic as /devices/pci0000:00/0000:00:1b.0/sound/card1/input5
```

Adding options snd-hda-intel model=auto enable_msi=0

 eliminates only firs line.

Any idea?

This pc is for server purpose, it is 24h online, but i see no problem with any suggestions - even trying another distro.

```
Linux xn--zabaaganionemiejsce-8fd.pl 3.13.0-30-generic #54~precise2-Ubuntu SMP Wed Jun 11 16:14:21 UTC 2014 i686 i686 i386 GNU/Linux
```

```
pdate; sudo apt-get install aptitude; sudo aptitude install paman gnome-alsamixer libasound2-plugins padevchooser libsdl1.2debian-pulseaudio; sudo lshw -short;ls -lart /dev/snd;  cat /dev/sndstat; lspci -nn; lsusb; sudo which alsactl; sudo fuser -v /dev/dsp /dev/snd/* ; dpkg -S bin/slmodemd; dmesg | egrep 'EMU|probe|emu|ALSA|alsa|ac97|udi|snd|ound|irmware'; sudo /etc/init.d/sl-modem-daemon status; sudo grep model /etc/modprobe.d/* ; sudo dmidecode|egrep 'anufact|roduct|erial|elease'; lsmod | egrep 'snd|usb|midi|udio'; pacmd list-sinks; aplay -l; sudo alsa force-reload;  ubuntu-support-status ; sudo lshw -C sound
Advanced Linux Sound Architecture Driver Version k3.13.0-30-generic.
 0 [XFi            ]: SB-XFi - Creative X-Fi
                      Creative X-Fi 20K1 Unknown
 1 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xf7e38000 irq 16
  1:        : sequencer
  2: [ 0- 4]: digital audio playback
  3: [ 0- 3]: digital audio playback
  4: [ 0- 2]: digital audio playback
  5: [ 0- 1]: digital audio playback
  6: [ 0- 0]: digital audio playback
  7: [ 0- 0]: digital audio capture
  8: [ 0]   : control
  9: [ 1- 2]: digital audio capture
 10: [ 1- 0]: digital audio playback
 11: [ 1- 0]: digital audio capture
 12: [ 1- 0]: hardware dependent
 13: [ 1]   : control
 33:        : timer
01-00: HDA Codec 0
00-00: ctxfi : Front/WaveIn : playback 256 : capture 1
00-01: ctxfi : Surround : playback 256
00-02: ctxfi : Center/LFE : playback 256
00-03: ctxfi : Side : playback 256
00-04: ctxfi : IEC958 Non-audio : playback 1
01-00: ALC662 rev1 Analog : ALC662 rev1 Analog : playback 1 : capture 1
01-02: ALC662 rev1 Alt Analog : ALC662 rev1 Alt Analog : capture 1
Client info
  cur  clients : 2
  peak clients : 2
  max  clients : 192

Client   0 : "System" [Kernel]
  Port   0 : "Timer" (Rwe-)
  Port   1 : "Announce" (R-e-)
Client  14 : "Midi Through" [Kernel]
  Port   0 : "Midi Through Port-0" (RWe-)
rm: cannot remove `/etc/asound.conf': No such file or directory
rm: cannot remove `/home/san/.asound*': No such file or directory
rm: cannot remove `/home/san/.pulse-cookie': No such file or directory
H/W path        Device      Class       Description
===================================================
                            system      EL1600 (To Be Filled By O.E.M.)
/0                          bus         E945GCU
/0/0                        memory      64KiB BIOS
/0/4                        processor   Intel(R) Atom(TM) CPU  230   @ 1.60GHz
/0/4/5                      memory      24KiB L1 cache
/0/4/6                      memory      512KiB L2 cache
/0/4/0.1                    processor   Logical CPU
/0/4/0.2                    processor   Logical CPU
/0/11                       memory      1GiB System Memory
/0/11/0                     memory      1GiB DIMM DDR2 Synchronous 667 MHz (1,5 ns)
/0/100                      bridge      82945G/GZ/P/PL Memory Controller Hub
/0/100/2                    display     82945G/GZ Integrated Graphics Controller
/0/100/1b                   multimedia  NM10/ICH7 Family High Definition Audio Controller
/0/100/1c                   bridge      NM10/ICH7 Family PCI Express Port 1
/0/100/1c/0     eth0        network     RTL8101E/RTL8102E PCI Express Fast Ethernet controller
/0/100/1d                   bus         NM10/ICH7 Family USB UHCI Controller #1
/0/100/1d.1                 bus         NM10/ICH7 Family USB UHCI Controller #2
/0/100/1d.2                 bus         NM10/ICH7 Family USB UHCI Controller #3
/0/100/1d.3                 bus         NM10/ICH7 Family USB UHCI Controller #4
/0/100/1d.7                 bus         NM10/ICH7 Family USB2 EHCI Controller
/0/100/1e                   bridge      82801 PCI Bridge
/0/100/1e/1                 multimedia  SB X-Fi
/0/100/1f                   bridge      82801GB/GR (ICH7 Family) LPC Interface Bridge
/0/100/1f.1                 storage     82801G (ICH7 Family) IDE Controller
/0/100/1f.2                 storage     NM10/ICH7 Family SATA Controller [IDE mode]
/0/100/1f.3                 bus         NM10/ICH7 Family SMBus Controller
/0/1            scsi0       storage     
/0/1/0.0.0      /dev/cdrom  disk        DVDRAM GSA-4163B
/0/2            scsi2       storage     
/0/2/0.0.0      /dev/sda    disk        500GB ST500LT012-9WS14
/0/2/0.0.0/1    /dev/sda1   volume      10GiB EXT4 volume
/0/2/0.0.0/2    /dev/sda2   volume      10236MiB Linux filesystem partition
/0/2/0.0.0/3    /dev/sda3   volume      445GiB Extended partition
/0/2/0.0.0/3/5  /dev/sda5   volume      89GiB Linux filesystem partition
/0/2/0.0.0/3/6  /dev/sda6   volume      300GiB Linux filesystem partition
/0/2/0.0.0/3/7  /dev/sda7   volume      40GiB Linux filesystem partition
/0/2/0.0.0/3/8  /dev/sda8   volume      15GiB Linux swap / Solaris partition
/0/3            scsi4       storage     
/0/3/0.0.0      /dev/sdb    disk        SCSI Disk
/0/3/0.0.1      /dev/sdc    disk        SCSI Disk
/0/3/0.0.2      /dev/sdd    disk        SCSI Disk
/0/3/0.0.3      /dev/sde    disk        SCSI Disk
total 0
crw-rw---T  1 root audio 116, 33 cze 30 20:42 timer
crw-rw---T  1 root audio 116,  4 cze 30 20:42 pcmC0D2p
crw-rw---T  1 root audio 116,  2 cze 30 20:42 pcmC0D4p
crw-rw---T  1 root audio 116,  3 cze 30 20:42 pcmC0D3p
crw-rw---T  1 root audio 116,  7 cze 30 20:42 pcmC0D0c
crw-rw---T  1 root audio 116,  8 cze 30 20:42 controlC0
crw-rw---T  1 root audio 116,  5 cze 30 20:42 pcmC0D1p
crw-rw---T  1 root audio 116,  6 cze 30 20:43 pcmC0D0p
crw-rw---T  1 root audio 116,  1 cze 30 21:20 seq
drwxr-xr-x  3 root root      340 cze 30 21:20 .
crw-rw---T  1 root audio 116,  9 cze 30 21:20 pcmC1D2c
crw-rw---T  1 root audio 116, 10 cze 30 21:20 pcmC1D0p
crw-rw---T  1 root audio 116, 13 cze 30 21:20 controlC1
drwxr-xr-x  2 root root       80 cze 30 21:20 by-path
crw-rw---T  1 root audio 116, 12 cze 30 21:20 hwC1D0
crw-rw---T  1 root audio 116, 11 cze 30 21:20 pcmC1D0c
drwxr-xr-x 17 root root     4460 cze 30 21:25 ..
cat: /dev/sndstat: No such file or directory
00:00.0 Host bridge [0600]: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub [8086:2770] (rev 02)
00:02.0 VGA compatible controller [0300]: Intel Corporation 82945G/GZ Integrated Graphics Controller [8086:2772] (rev 02)
00:1b.0 Audio device [0403]: Intel Corporation NM10/ICH7 Family High Definition Audio Controller [8086:27d8] (rev 01)
00:1c.0 PCI bridge [0604]: Intel Corporation NM10/ICH7 Family PCI Express Port 1 [8086:27d0] (rev 01)
00:1d.0 USB controller [0c03]: Intel Corporation NM10/ICH7 Family USB UHCI Controller #1 [8086:27c8] (rev 01)
00:1d.1 USB controller [0c03]: Intel Corporation NM10/ICH7 Family USB UHCI Controller #2 [8086:27c9] (rev 01)
00:1d.2 USB controller [0c03]: Intel Corporation NM10/ICH7 Family USB UHCI Controller #3 [8086:27ca] (rev 01)
00:1d.3 USB controller [0c03]: Intel Corporation NM10/ICH7 Family USB UHCI Controller #4 [8086:27cb] (rev 01)
00:1d.7 USB controller [0c03]: Intel Corporation NM10/ICH7 Family USB2 EHCI Controller [8086:27cc] (rev 01)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev e1)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge [8086:27b8] (rev 01)
00:1f.1 IDE interface [0101]: Intel Corporation 82801G (ICH7 Family) IDE Controller [8086:27df] (rev 01)
00:1f.2 IDE interface [0101]: Intel Corporation NM10/ICH7 Family SATA Controller [IDE mode] [8086:27c0] (rev 01)
00:1f.3 SMBus [0c05]: Intel Corporation NM10/ICH7 Family SMBus Controller [8086:27da] (rev 01)
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
02:01.0 Multimedia audio controller [0401]: Creative Labs SB X-Fi [1102:0005]
Bus 001 Device 004: ID 058f:6362 Alcor Micro Corp. Flash Card Reader/Writer
Bus 002 Device 002: ID 0ac8:305b Z-Star Microelectronics Corp. ZC0305 Webcam
Bus 003 Device 002: ID 0ac8:305b Z-Star Microelectronics Corp. ZC0305 Webcam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
/sbin/alsactl
Specified filename /dev/dsp does not exist.
dpkg-query: no path found matching pattern *bin/slmodemd*.
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000] found SMP MP-table at [mem 0x000ff780-0x000ff78f] mapped at [c00ff780]
[    0.131639] ACPI: No dock devices found.
[    0.177983] Found 1 acpi root devices
[    0.211175] pnp: PnP ACPI: found 17 devices
[    1.079579] audit: initializing netlink socket (disabled)
[    1.079613] type=2000 audit(1404153714.076:1): initialized
[    1.541162] libphy: Fixed MDIO Bus: probed
[    1.588572] isapnp: No Plug & Play device found
[    1.715482] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    1.988036] hub 1-0:1.0: USB hub found
[    2.124276] usb usb2: New USB device found, idVendor=1d6b, idProduct=0001
[    2.190616] hub 2-0:1.0: USB hub found
[    2.253838] usb usb3: New USB device found, idVendor=1d6b, idProduct=0001
[    2.318685] hub 3-0:1.0: USB hub found
[    2.383966] usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
[    2.448953] hub 4-0:1.0: USB hub found
[    2.511097] usb usb5: New USB device found, idVendor=1d6b, idProduct=0001
[    2.575712] hub 5-0:1.0: USB hub found
[    3.011730] usb 1-7: New USB device found, idVendor=058f, idProduct=6362
[    3.032220] IMA: No TPM chip found, activating TPM-bypass!
[    3.112177] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    3.721239] usb 2-1: New USB device found, idVendor=0ac8, idProduct=305b
[    4.229776] usb 3-1: New USB device found, idVendor=0ac8, idProduct=305b
[   23.097255] lp: driver loaded but no devices found
[   23.410282] it87: Found IT8718F chip at 0xa10, revision 4
[   23.492776] lpc_ich: Resource conflict(s) found affecting gpio_ich
[   23.676204] type=1400 audit(1404153737.141:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=701 comm="apparmor_parser"
[   23.676233] type=1400 audit(1404153737.141:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=701 comm="apparmor_parser"
[   23.676256] type=1400 audit(1404153737.141:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=701 comm="apparmor_parser"
[   23.680571] type=1400 audit(1404153737.145:5): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=701 comm="apparmor_parser"
[   23.680602] type=1400 audit(1404153737.145:6): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=701 comm="apparmor_parser"
[   23.681862] type=1400 audit(1404153737.145:7): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=701 comm="apparmor_parser"
[   23.846271] leds_ss4200: no LED devices found
[   24.860302] ctxfi: chip 20K1 model Unknown (1102:0026) is found
[   25.922859] input: HDA Intel Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card1/input9
[   25.923804] input: HDA Intel Line Out as /devices/pci0000:00/0000:00:1b.0/sound/card1/input8
[   25.925065] input: HDA Intel Line as /devices/pci0000:00/0000:00:1b.0/sound/card1/input7
[   25.926276] input: HDA Intel Rear Mic as /devices/pci0000:00/0000:00:1b.0/sound/card1/input6
[   25.927205] input: HDA Intel Front Mic as /devices/pci0000:00/0000:00:1b.0/sound/card1/input5
[   48.331052] type=1400 audit(1404153761.793:8): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=1208 comm="apparmor_parser"
[   48.331086] type=1400 audit(1404153761.793:9): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1208 comm="apparmor_parser"
[   48.331112] type=1400 audit(1404153761.793:10): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=1208 comm="apparmor_parser"
[   48.333101] type=1400 audit(1404153761.797:11): apparmor="STATUS" operation="profile_load" profile="unconfined" name="system_tor" pid=1209 comm="apparmor_parser"
[   48.334113] type=1400 audit(1404153761.797:12): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1208 comm="apparmor_parser"
[   48.334139] type=1400 audit(1404153761.797:13): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=1208 comm="apparmor_parser"
[   48.335393] type=1400 audit(1404153761.797:14): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=1208 comm="apparmor_parser"
[   48.344352] type=1400 audit(1404153761.809:15): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/freshclam" pid=1210 comm="apparmor_parser"
[   48.346282] type=1400 audit(1404153761.809:16): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/clamd" pid=1211 comm="apparmor_parser"
[   48.355598] type=1400 audit(1404153761.817:17): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/mysqld" pid=1212 comm="apparmor_parser"
[ 2321.534202] input: HDA Intel Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card1/input16
[ 2321.534675] input: HDA Intel Line Out as /devices/pci0000:00/0000:00:1b.0/sound/card1/input15
[ 2321.534989] input: HDA Intel Line as /devices/pci0000:00/0000:00:1b.0/sound/card1/input14
[ 2321.535300] input: HDA Intel Rear Mic as /devices/pci0000:00/0000:00:1b.0/sound/card1/input13
[ 2321.535585] input: HDA Intel Front Mic as /devices/pci0000:00/0000:00:1b.0/sound/card1/input12
sudo: /etc/init.d/sl-modem-daemon: command not found
/etc/modprobe.d/alsa-base.conf:#options snd-hda-intel model=3stack-dig
/etc/modprobe.d/alsa-base.conf:#options snd-hda-intel model=6stack-dig
/etc/modprobe.d/alsa-base.conf:#options snd-hda-intel model=alc662
/etc/modprobe.d/alsa-base.conf:options snd-hda-intel model=auto enable_msi=0
        Release Date: 07/06/2009
                Serial services are supported (int 14h)
        Manufacturer: eMachines
        Product Name: EL1600
        Serial Number:                       
        Manufacturer: eMachines
        Product Name: E945GCU
        Serial Number:                       
        Manufacturer: eMachines
        Serial Number:                       
        Manufacturer: Intel            
        Serial Number: To Be Filled By O.E.M.
        Manufacturer: CE000000000000
        Serial Number: 781ABDD8
snd_hda_intel          43398  0 
snd_seq_dummy          12686  0 
snd_seq_midi           13132  0 
snd_rawmidi            25198  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                55716  3 snd_seq_dummy,snd_seq_midi,snd_seq_midi_event
snd_seq_device         14137  4 snd_seq_dummy,snd_seq_midi,snd_rawmidi,snd_seq
snd_hda_codec_realtek    59883  1 
snd_hda_codec         169779  2 snd_hda_intel,snd_hda_codec_realtek
snd_hwdep              13276  1 snd_hda_codec
snd_ctxfi              92364  0 
snd_pcm                90501  3 snd_hda_intel,snd_hda_codec,snd_ctxfi
snd_timer              28971  2 snd_seq,snd_pcm
snd                    61351  12 snd_hda_intel,snd_seq_dummy,snd_seq_midi,snd_rawmidi,snd_seq,snd_seq_device,snd_hda_codec_realtek,snd_hda_codec,snd_hwdep,snd_ctxfi,snd_pcm,snd_timer
soundcore              12600  1 snd
snd_page_alloc         18398  3 snd_hda_intel,snd_ctxfi,snd_pcm
usb_storage            48754  0 
No PulseAudio daemon running, or not running as session daemon.
Unloading ALSA sound driver modules: snd-hda-intel snd-seq-dummy snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-seq-device snd-hda-codec-realtek snd-hda-codec snd-hwdep snd-ctxfi snd-pcm snd-timer snd-page-alloc.
Loading ALSA sound driver modules: snd-hda-intel snd-seq-dummy snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-seq-device snd-hda-codec-realtek snd-hda-codec snd-hwdep snd-ctxfi snd-pcm snd-timer snd-page-alloc.
Support status summary of 'xn--zabaaganionemiejsce-8fd.pl':

You have 934 packages (71.6%) supported until kwiecie&#324; 2017 (5y)
You have 20 packages (1.5%) supported until grudzie&#324; 2015 (18m)
You have 82 packages (6.3%) supported until pa&#378;dziernik 2013 (18m)
You have 2 packages (0.2%) supported until czerwiec 2019 (5y)

You have 5 packages (0.4%) that can not/no-longer be downloaded
You have 261 packages (20.0%) that are unsupported

Run with --show-unsupported, --show-supported or --show-all to see more details
  *-multimedia            
       description: Audio device
       product: NM10/ICH7 Family High Definition Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=snd_hda_intel latency=0
       resources: irq:16 memory:f7e38000-f7e3bfff
  *-multimedia
       description: Multimedia audio controller
       product: SB X-Fi
       vendor: Creative Labs
       physical id: 1
       bus info: pci@0000:02:01.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list
       configuration: driver=snd_ctxfi latency=64 maxlatency=5 mingnt=4
       resources: irq:18 ioport:ec00(size=32) memory:fea00000-febfffff memory:f8000000-fbffffff


```

Removed apt-get messages and aplay -l since it output is already here.
Please ignore Sound Blaster info, it is here until problem is solved.

Sorry for poor eanglish

Anything else i can put here?

---

### Post by lidex on 2014-07-01
Perhaps try this option in alsa-base.conf:
```
options snd-hda-intel model=asus-mode3
```
Make sure you remove anything else you added and reboot

Another possibility:
```
options snd-hda-intel model=6stack-dig
```

---

### Post by e-San on 2014-07-02
I'm out of luck.
None did work. Should i check all models?

```

ALC66x/67x/892
==============
  mario            Chromebook mario model fixup
  asus-mode1        ASUS
  asus-mode2        ASUS
  asus-mode3        ASUS
  asus-mode4        ASUS
  asus-mode5        ASUS
  asus-mode6        ASUS
  asus-mode7        ASUS
  asus-mode8        ASUS
  inv-dmic        Inverted internal mic workaround
  dell-headset-multi    Headset jack, which can also be used as mic-in
```

Tried all. With asus-* it gave fallback to default config. 

Here is something more (hwinfo --sound):
```
10: PCI 1b.0: 0403 Audio device                                 
  [Created at pci.318]
  Unique ID: u1Nb.baJFjQ+W1p7
  SysFS ID: /devices/pci0000:00/0000:00:1b.0
  SysFS BusID: 0000:00:1b.0
  Hardware Class: sound
  Model: "Intel 82801G (ICH7 Family) High Definition Audio Controller"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x27d8 "82801G (ICH7 Family) High Definition Audio Controller"
  SubVendor: pci 0x1025 "Acer Incorporated [ALI]"
  SubDevice: pci 0x0255 
  Revision: 0x01
  Driver: "snd_hda_intel"
  Driver Modules: "snd_hda_intel"
  Memory Range: 0xf7e38000-0xf7e3bfff (rw,non-prefetchable)
  IRQ: 41 (1022 events)
  Module Alias: "pci:v00008086d000027D8sv00001025sd00000255bc04sc03i00"
  Driver Info #0:
    Driver Status: snd_hda_intel is active
    Driver Activation Cmd: "modprobe snd_hda_intel"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
```

---

### Post by lidex on 2014-07-02
@e-San
Did you try:
```
options snd-hda-intel model=3stack-6ch
```

You do know you need to reboot or reload alsa for each change?
Then use alsamixer to select the correct sound card and unmute digital out.
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.

---

### Post by e-San on 2014-07-03
Checked.

Yes, i do reboot pc, check dmesg, check aplay -l and check if there is any new control in alsamixer.

Thanks for Your help!

---

### Post by nick130 on 2014-07-12
> **takka360 said:**
> This is what i done and it works fantastic now.

The first thing you'll have to do is get rid of PulseAudio:

     Code:
     sudo apt-get install gstreamer0.10-alsa gnome-alsamixer sudo apt-get purge pulseaudio gstreamer0.10-pulseaudio vlc-plugin-pulse 
Then you'll need to put the following configuration file into your user home directory. Save it as ".asoundrc":
     Code:
     pcm.!default {     type plug     slave.pcm {         type asym         playback.pcm {             type route             slave.pcm "dmix:0"             ttable.0.0 0.66             ttable.0.1 0.33             ttable.1.0 0.33             ttable.1.1 0.66         }         capture.pcm "hw:0"     } } 
Log out and log in again, then open a terminal window and run the following test:

     Code:
     speaker-test -t wav -c 2 
This will play back two sound clips ("front left" and "front  right"). You should be able to hear both clips on either channel, with  one being slightly louder than the other.

My audio quit working suddenly.  I read around and tried a few things, and this worked.  That is, the speaker-test command gave me sound.  But when I try to watch a video or test my speakers in the GNOME audio settings GUI, I hear nothing.  What should I do?

---

### Post by lookit on 2014-08-04
Found the solution. For some reason, it seems RB's super-secret spy volume was turned all the way down. This is how I solved it: turned on RB, played a file. Then went to sound settings, and there, in the tab "applications", RB had magically appeared, and I could turn the volume up. I have absolutely no idea why it works like this.


I have this weird problem, which just appeared the other day. (I'm running ubuntu 14.04 LTS on a Lenovo Ideapad, and it's been running smoothly for the few months since I got it.) Until all of a sudden rhythmbox stopped outputting sound. 
- It seems to be playing the mp3:s ok, there's just no actual sound. But only in RB, all my other sound is working ok. 
- The same mp3s played back in e.g. VLC work just fine. 
- Speaker test gives output.
- aplay -l gives the following output in terminal, but I can't really interpret it.
> aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: HDMI [HDA Intel HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: HDMI [HDA Intel HDMI], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: HDMI [HDA Intel HDMI], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: PCH [HDA Intel PCH], device 0: ALC283 Analog [ALC283 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0




I'm stumped. Help would be much appreciated.

---

### Post by Ashrael on 2014-08-19
Just bought a Toshiba Satellite L50-B-145 and immediatly formatted the drive to get rid of a serious virus called win8.
Installed ubuntu 12.04, I know there are newer ones, sound worked for a few days, now i got a problem:

When I start up, I get the drumroll sound, so far so good.
Then I log in and start up some music, no sound from the speakers?!? I do get sound from the headphones.
I open > Sound Settings, all seems to be okay here.
I open Pulseaudio volume control, all seems well here too.
Opened alsamixer in terminal and all seems well here too...
When I plug in the headphones I see the change, from (speakers - built in audio) to (Headphones - built in audio), and back when I unplug.

Some posts on the net suggest its a jack-sensing issue.

To me it seems that there is some setting that needs fixing...

Any clues as to why this is? Question me for details if needed.

THX!

---

### Post by mörgæs on 2014-08-22
New hardware and old software is a bad combination. I suggest a fresh install of 14.04.1. 
Please write again if you are still having trouble.

---

### Post by Yuliyan_Hristov on 2014-08-24
Hi!

Idecided not to open another topic and to write here. So here is my problem. Is there a way to manually configure the bands (for example: bass, trebles and so on) without installing PulseAudio equalizer? I want to do that because the sound coming out from my aduio jack is very muffled when playing a song for example from YouTube? Im sorry if this is not the right place for my question and for my bad english! 

Greetings!

---

### Post by pawe3pl on 2014-09-18
Hello. I have a little problem on my Lenovo G50-30 laptop with Ubuntu  14.04.1. My HDMI audio output is not listed in sound menu.

```
**** [COLOR=#000000]*List of PLAYBACK Hardware Devices *[/COLOR]****
card 0: PCH [HDA Intel PCH], device 0: CX20751/2 Analog [CX20751/2 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

---

### Post by IanKoro on 2014-10-30
My audio recently stopped working. I upgraded from 13.04 to 14.04 about a week ago, and everything was working fine. 
Yesterday I was using Rhythmbox (which I don't normally use) to listen to some music. I was adding a bunch of files to Rhythmbox's library, and the audio suddenly stopped working. Rhythmbox froze, so I closed it, (I think I may have gotten an error message related to Pulseaudio around this time, but didn't think to take note), and when I reopened it the sound still didn't work. Sound also stopped working in VLC. I figured I had just crashed Pulseaudio, and that a reboot would fix it, but still nothing.

I went through the troubleshooting steps posted above with no luck. 

Here's the output of running the alsa information script, if that helps: 
[http://www.alsa-project.org/db/?f=3b98f5c8ab0f5076c661e486c2656798562de125](http://www.alsa-project.org/db/?f=3b98f5c8ab0f5076c661e486c2656798562de125)

---

### Post by javiert on 2014-12-18
Looks like same problem I'm facing. I post mine here

http://[ubuntuforums.org/showthread.php?t=2257306]("http://ubuntuforums.org/showthread.php?t=2257306")

I tried the second manual in the first post but nothing happen. :(

---

### Post by taserian on 2014-12-24
I've installed Ubuntu 14.10 on a Toshiba Satellite P50-BBT2G22, but I can't get the sound to work. I've kept the Windows 8 partition alive for warranty purposes, and sound works perfectly there. Using "ubuntu-bug -s audio" in the Terminal, it said that PulseAudio was not configured to use the card I want output from (Built-In Audio - HDA Intel HDMI), but pavucontrol hasn't helped anyway (in pavucontrol, under Configuration tab, all options under Built-In Audio claim that they are unplugged [ 3 options say "Digital Stereo (HDMI) Output (unplugged)", 3 more options say "Digital Surround 5.1 (HDMI) output (unplugged)" and an "Off" option]).

Data on alsainfo and other files are at [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1404589](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1404589) . I submitted it as a bug a few days ago, but it hasn't had any action since then.

Can anyone help?

- - - -

EDIT: Going through the troubleshooting at [https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)

I came across this (during Step 3):

[FONT=courier new]!!ALSA Version
!!------------

Driver version:     k3.16.0-29-generic
Library version:    1.0.28
Utilities version:  1.0.28[/FONT]

Is it a problem that they're not all the same?

---

### Post by Colonelguf on 2015-03-30
I have been running Mythbuntu for several years, and I recently did a clean install of 14.04.
HDMI audio works fine in Mythtv, but I can't get it to work with anything else. I want to use VLC, XBMC, etc in addition to Mythtv.
I have a NVidia 610 video card.

In Mythtv setup, the audio device that works is ALSA:hdmi:CARD=NVidia,DEV=1

When I was running 12.04, I got all the audio working by setting the default audio device by using:
pacmd list-sinks
pacmd set-default-sink

When I run pacmd list-sinks in 14.04 i get
```

Welcome to PulseAudio! Use "help" for usage information.
>>> 3 sink(s) available.
  * index: 1
        name: <combined>
        driver: <module-combine-sink.c>
        flags: DECIBEL_VOLUME LATENCY
        state: IDLE
        suspend cause:
        priority: 1000
        volume: 0: 101% 1: 101%
                0: 0.26 dB 1: 0.26 dB
                balance 0.00
        base volume: 100%
                     0.00 dB
        volume steps: 65537
        muted: no
        current latency: 19.86 ms
        max request: 3 KiB
        max rewind: 0 KiB
        monitor source: 3
        sample spec: s16le 2ch 44100Hz
        channel map: front-left,front-right
                     Stereo
        used by: 0
        linked by: 2
        fixed latency: 20.00 ms
        module: 11
        properties:
                device.class = "filter"
                device.description = "Simultaneous output to Built-in Audio Analog Stereo, GF119 HDMI Audio Controller Digital Stereo (HDMI)"
                device.icon_name = "audio-card"
    index: 4
        name: <alsa_output.pci-0000_00_1b.0.analog-stereo>
        driver: <module-alsa-card.c>
        flags: HARDWARE HW_MUTE_CTRL HW_VOLUME_CTRL DECIBEL_VOLUME LATENCY DYNAMIC_LATENCY
        state: RUNNING
        suspend cause:
        priority: 9959
        volume: 0: 100% 1: 100%
                0: 0.00 dB 1: 0.00 dB
                balance 0.00
        base volume: 100%
                     0.00 dB
        volume steps: 65537
        muted: no
        current latency: 19.37 ms
        max request: 3 KiB
        max rewind: 64 KiB
        monitor source: 7
        sample spec: s16le 2ch 44100Hz
        channel map: front-left,front-right
                     Stereo
        used by: 1
        linked by: 5
        configured latency: 20.00 ms; range is 0.50 .. 371.52 ms
        card: 0 <alsa_card.pci-0000_00_1b.0>
        module: 5
        properties:
                alsa.resolution_bits = "16"
                device.api = "alsa"
                device.class = "sound"
                alsa.class = "generic"
                alsa.subclass = "generic-mix"
                alsa.name = "ALC892 Analog"
                alsa.id = "ALC892 Analog"
                alsa.subdevice = "0"
                alsa.subdevice_name = "subdevice #0"
                alsa.device = "0"
                alsa.card = "0"
                alsa.card_name = "HDA Intel PCH"
                alsa.long_card_name = "HDA Intel PCH at 0xf7510000 irq 44"
                alsa.driver_name = "snd_hda_intel"
                device.bus_path = "pci-0000:00:1b.0"
                sysfs.path = "/devices/pci0000:00/0000:00:1b.0/sound/card0"
                device.bus = "pci"
                device.vendor.id = "8086"
                device.vendor.name = "Intel Corporation"
                device.product.id = "1e20"
                device.product.name = "7 Series/C210 Series Chipset Family High Definition Audio Controller"
                device.form_factor = "internal"
                device.string = "front:0"
                device.buffering.buffer_size = "65536"
                device.buffering.fragment_size = "32768"
                device.access_mode = "mmap+timer"
                device.profile.name = "analog-stereo"
                device.profile.description = "Analog Stereo"
                device.description = "Built-in Audio Analog Stereo"
                alsa.mixer_name = "Realtek ALC892"
                alsa.components = "HDA:10ec0892,10197c48,00100302"
                module-udev-detect.discovered = "1"
                device.icon_name = "audio-card-pci"
        ports:
                analog-output: Analog Output (priority 9900, latency offset 0 usec, available: unknown)
                        properties:

                analog-output-headphones: Headphones (priority 9000, latency offset 0 usec, available: unknown)
                        properties:
                                device.icon_name = "audio-headphones"
        active port: <analog-output>
    index: 5
        name: <alsa_output.pci-0000_01_00.1.hdmi-stereo-extra1>
        driver: <module-alsa-card.c>
        flags: HARDWARE DECIBEL_VOLUME LATENCY DYNAMIC_LATENCY
        state: RUNNING
        suspend cause:
        priority: 9050
        volume: 0: 105% 1: 105%
                0: 1.27 dB 1: 1.27 dB
                balance 0.00
        base volume: 100%
                     0.00 dB
        volume steps: 65537
        muted: no
        current latency: 17.26 ms
        max request: 3 KiB
        max rewind: 64 KiB
        monitor source: 8
        sample spec: s16le 2ch 44100Hz
        channel map: front-left,front-right
                     Stereo
        used by: 1
        linked by: 5
        configured latency: 20.00 ms; range is 0.50 .. 371.52 ms
        card: 3 <alsa_card.pci-0000_01_00.1>
        module: 24
        properties:
                alsa.resolution_bits = "16"
                device.api = "alsa"
                device.class = "sound"
                alsa.class = "generic"
                alsa.subclass = "generic-mix"
                alsa.name = "HDMI 1"
                alsa.id = "HDMI 1"
                alsa.subdevice = "0"
                alsa.subdevice_name = "subdevice #0"
                alsa.device = "7"
                alsa.card = "1"
                alsa.card_name = "HDA NVidia"
                alsa.long_card_name = "HDA NVidia at 0xf7080000 irq 17"
                alsa.driver_name = "snd_hda_intel"
                device.bus_path = "pci-0000:01:00.1"
                sysfs.path = "/devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1"
                device.bus = "pci"
                device.vendor.id = "10de"
                device.vendor.name = "NVIDIA Corporation"
                device.product.id = "0e08"
                device.product.name = "GF119 HDMI Audio Controller"
                device.string = "hdmi:1,1"
                device.buffering.buffer_size = "65536"
                device.buffering.fragment_size = "32768"
                device.access_mode = "mmap+timer"
                device.profile.name = "hdmi-stereo-extra1"
                device.profile.description = "Digital Stereo (HDMI)"
                device.description = "GF119 HDMI Audio Controller Digital Stereo (HDMI)"
                alsa.mixer_name = "Nvidia GPU 1c HDMI/DP"
                alsa.components = "HDA:10de001c,00000000,00100100"
                module-udev-detect.discovered = "1"
                device.icon_name = "audio-card-pci"
        ports:
                hdmi-output-1: HDMI / DisplayPort 2 (priority 5800, latency offset 0 usec, available: yes)
                        properties:
                                device.icon_name = "video-display"
                                device.product.name = "E650i-A2
    "
        active port: <hdmi-output-1>

```
Then I used 

pacmd set-default-sink 5

to set the default

aplay -L gives me this
```

default
    Playback/recording through the PulseAudio sound server
null
    Discard all samples (playback) or generate zero samples (capture)
pulse
    PulseAudio Sound Server
sysdefault:CARD=PCH
    HDA Intel PCH, ALC892 Analog
    Default Audio Device
front:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    Front speakers
surround40:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Digital
    IEC958 (S/PDIF) Digital Audio Output
dmix:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    Direct sample mixing device
dmix:CARD=PCH,DEV=1
    HDA Intel PCH, ALC892 Digital
    Direct sample mixing device
dsnoop:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    Direct sample snooping device
dsnoop:CARD=PCH,DEV=1
    HDA Intel PCH, ALC892 Digital
    Direct sample snooping device
hw:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    Direct hardware device without any conversions
hw:CARD=PCH,DEV=1
    HDA Intel PCH, ALC892 Digital
    Direct hardware device without any conversions
plughw:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    Hardware device with all software conversions
plughw:CARD=PCH,DEV=1
    HDA Intel PCH, ALC892 Digital
    Hardware device with all software conversions
hdmi:CARD=NVidia,DEV=0
    HDA NVidia, HDMI 0
    HDMI Audio Output
hdmi:CARD=NVidia,DEV=1
    HDA NVidia, HDMI 1
    HDMI Audio Output
dmix:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    Direct sample mixing device
dmix:CARD=NVidia,DEV=7
    HDA NVidia, HDMI 1
    Direct sample mixing device
dsnoop:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    Direct sample snooping device
dsnoop:CARD=NVidia,DEV=7
    HDA NVidia, HDMI 1
    Direct sample snooping device
hw:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    Direct hardware device without any conversions
hw:CARD=NVidia,DEV=7
    HDA NVidia, HDMI 1
    Direct hardware device without any conversions
plughw:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    Hardware device with all software conversions
plughw:CARD=NVidia,DEV=7
    HDA NVidia, HDMI 1
    Hardware device with all software conversions


```
I have made sure nothing is muted in alsamixer, I have tried many different setting combinations in PulseAudio volume control and still can't get this to work.
Weird thing is, 2 different times I got audio in XBMC and thought I had it fixed, but the next time I opened it I had no sound. I don't want to wreck the audio in Mythtv, so I hate to change much without getting some advice first. Can anyone help me troubleshoot this problem?

---

### Post by piscvau on 2015-03-31
Hello
I have carefully followed all the sound troubleshooting procédure. 
I am in Xubuntun 14.04. As a consequence of following the multiple advices in these procedures, I have many new things in my menu, no more access to synaptic and many other problems. 
Then I found on Internet the following page written by canonical whose title is "top-five-wrong-ways-to-fix-your-audio"
dhttp://voices.canonical.com/david.henningsson/2012/07/13/top-five-wrong-ways-to-fix-your-audio/o. 

Almost all these things are included in the troubleshooting procedure. It seems to me it is a real problem.
My configuration is broken. I am going to re-instal it from scratch and I will not follow the troubleshootingprocedures.

---

### Post by Colonelguf on 2015-03-31
> **Colonelguf said:**
> I have been running Mythbuntu for several years, and I recently did a clean install of 14.04.
HDMI audio works fine in Mythtv, but I can't get it to work with anything else. I want to use VLC, XBMC, etc in addition to Mythtv.
I have a NVidia 610 video card.

In Mythtv setup, the audio device that works is ALSA:hdmi:CARD=NVidia,DEV=1

...
I have made sure nothing is muted in alsamixer, I have tried many different setting combinations in PulseAudio volume control and still can't get this to work.
Weird thing is, 2 different times I got audio in XBMC and thought I had it fixed, but the next time I opened it I had no sound. I don't want to wreck the audio in Mythtv, so I hate to change much without getting some advice first. Can anyone help me troubleshoot this problem?

I think I got my problem solved.
I disabled PulseAudio
```

echo autospawn=no > ~/.pulse/client.conf
pulseaudio -k

```
I seem to be getting audio everywhere I need it now
I have no idea if this breaks something else, but it works for me so far

---

### Post by ludo6 on 2015-07-15
Hi there.

I've followed the guide at the start of this thread but whatever I do I can't get my Traktor Audio 6 card to work since installing 15.04 (it worked with no special setup in 14.10).

I posted on AskUbuntu here, [http://askubuntu.com/questions/645537/native-instruments-traktor-audio-6-stopped-working-on-15-04-upgrade](http://askubuntu.com/questions/645537/native-instruments-traktor-audio-6-stopped-working-on-15-04-upgrade)

Sound is fine via the onboard card, but not via my external. If I run `pactl list` I see all my cards listed, and if I run `aplay -l` I see my cards correctly, but they don't show up in the sound selection app on the system menu bar.

If I  run [COLOR=#111111][FONT=Consolas]alsamixer[/FONT][/COLOR] and select the card I want to use, all channels for the card are shown as disabled. See screenshot below.

I tried creating an /etc/asound.conf file as per the sticky guide but that didn't help.

I'm not sure where to go next. Any ideas?

Thanks!

Ludo

 [IMG]http://i.stack.imgur.com/AT7Lg.png[/IMG]

---

### Post by arno48 on 2015-08-05
Hello,
Pronunciation sounds of both online dictionaries "www.wordreference.com" and "thefreedictionary.com" stopped working  a few months ago. Other media (e.g. Youtube) are going on working.
Might it be caused by Ubuntu versions 14.10 and 15.4?  I have Installed OpenJDK Java Runtime instead of Java downloaded from Orange? Might it matter?

---

### Post by arno48 on 2015-08-26
Now sound is working again.
Yesterday I installed some Ubuntu updates, I suppose this is the reason

---

### Post by tarek09 on 2015-12-25
my latitude D630 dell  sound icon show but naver sound how to solve plz tell me

---

### Post by dangmanhtruong on 2016-04-25
I just clean installed Ubuntu 16.04 but now the external speaker is not  recognized, only the internal one is used, even though I've been using  the external speaker for a very long time before installing Ubuntu.
Here are the results of "wget -O alsa-info.sh [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh) && chmod +x ./alsa-info.sh && ./alsa-info.sh
" [http://www.alsa-project.org/db/?f=64fcb4c7da31310ad2043bd8aa5aa480dfd02421](http://www.alsa-project.org/db/?f=64fcb4c7da31310ad2043bd8aa5aa480dfd02421)"
Please help me, thank you very much!

---

### Post by jvglynnjr on 2017-01-04
As far as I can tell, those troubleshooting links pertain to a situation in which sound does not work at all.  What about when sound works but has flaws?

Specifically, I am hearing a lot of front-end clipping in all of my audio applications. That is, whether using vlc or gplayer or a web browser, I get the first half-second or so of the sound cut off. So, an mp3 song will begin a little after the first beat. It seems especially bad in audio books, where almost every sentence starts late. 

I know it's not the files, because they work fine under <gasp!> micro$oft OSs. 

Can someone point me in the direction to address this issue?  Do you need specifics of my Ubuntu setup? (16.04) soundcard? what else?

[just found out it was my blue tooth device! It only works right in "headphone" mode, not in "audio sink" mode]

---

### Post by roblr on 2017-01-05
hello and good day to you fellow ubuntu-ers!

i have an acer aspire one a0751h netbook/laptop and  have recently installed the newest version of ubuntu 

i have a problem when i play back music no matterer what the playback  program whether its firefox, music, rhythm box, VLC player etc...

my issue is that the music is choppy and the second by second speed is way too fast this happens on all of the above programs

it is driving me nuts - i just want to listen to some music!

i have tried various solutions with no remedy, iu have tried to install  the realtek codecs, the alsa drivers and some others that i found from  google

to recap: TLDR;

music choppy and sped up
adcer aspire one a0751h netbook/laptop
fresh install of ubuntu latest version  16.10 (updated today 5th jan 2017)
GNOME ALSA mixer PCM slider does nothing to help 
GNOME ALSA mixer states "Realtek ALC272X" 


thankyou in advance

---

### Post by mörgæs on 2017-01-06
> **jvglynnjr said:**
> 
just found out it was my blue tooth device! It only works right in "headphone" mode, not in "audio sink" mode

Thanks for posting the solution. I had not guessed that.

---

### Post by marginal39 on 2017-07-27
> **MoreOrLess said:**
> Try playing with some of the controls in alsamixer: 
[http://alsa.opensrc.org/FAQ004](http://alsa.opensrc.org/FAQ004)

I get a "404 Page Not Found" when I click on this link.

---

### Post by omeko on 2017-08-16
Hi all,

I recentely decided to install ubuntu on an Acer Aspire Switch 10E SW3-013. I used the image provided with the Acerium project which uses kernel 4.8.4 and that gets most of the neat stuff working that won't in any way if I do an upgrade to a more recent kernel. Unfortunately there remains a soundproblem which boils down to "no sound at all". Pulseaudio seems to be doing okay, but I'm not able to increase the volume for Speaker Channel, Speaker L and Speaker R in Alsamixer. Yes, they are unmuted.
There's another weird problem when I unmute all options with amixer: the laptop reaches meltdown temperatures while spreading a profound smell of burning plastic.

It didn't act that weird on Bill Gates' OS that came preinstalled with this hardware, so this seems to be an Ubuntuissue of sorts.
My output is on [http://www.alsa-project.org/db/?f=23e36a991a22b29ddb6bf1061aa57efb3ebf4055](http://www.alsa-project.org/db/?f=23e36a991a22b29ddb6bf1061aa57efb3ebf4055)

Any help welcome.

Marko

---

### Post by hsimic on 2018-03-11
I've installed Ubuntu 17.10 on new hardware (ASUS Prime B350M-E with AMD Ryzen 2200G), connected it to TV via HDMI. There is no sound over HDMI.

[LIST]
[*]upgraded kernel all the way through 4.16-rc4, nothing
[*]line out audio works fine
[*]cable is fine
[*]I think I've tried everything from the troubleshooting guides in this thread, and everywhere else that I could find - nothing
[/LIST]

Furthest that I came towards the root of the problem: PulseAudio shows that **all HDMI outputs are "unplugged"** (even though I'm seeing that information through a plugged-in HDMI cable). Switching default output to HDMI does nothing.

My ALSA info script output is at [http://www.alsa-project.org/db/?f=26681a0ebd08c5de5509377ff5e7f0e76039d653](http://www.alsa-project.org/db/?f=26681a0ebd08c5de5509377ff5e7f0e76039d653)

Does anyone have a hint on how to debug this further? I've been at it for a week now :(

---

### Post by enigma9o7 on 2018-05-28
Clean install of lubuntu-18.04-desktop-i386 and no sound from the internal speaker, which works fine under XP & Xenail Pup.  Note headphones do work.   I installed the 60mb automatic updates immediately after install and haven't installed anything else.

Under sound settings by clicking on the speaker on the taskbar (PulseAudio), I have  two output device ports - headphones/Amplifier and Headphones/No  Amplifier.  Tried both.  On the playback tab, when sound is playing it shows the firefox  audiostream or ALSA plug-in [speaker-test] doing it's thing.

Alsamixer had "Master Mono" set to zero, but maxing that out doesn't do anything and it identifies Intel ICH5 / Analog Devices AD1981B

PC Model: HP-d530-CMT

---

### Post by svyr on 2018-10-12
hello,  can anyone think of what the issue might be for the clevo rebrand here  and ubuntu sound (live or installed , vs working in windows) or have any  suggested ways of troubleshooting it. [https://ubuntuforums.org/showthread.php?t=2403327](https://ubuntuforums.org/showthread.php?t=2403327)

basically it appears that the speaker and headphone outs are in Alsamixer and pulse and I can see ubuntu thinks pulse is getting output in pulse control panel (the orange sound indicator thing), but there's no output from either headphones or speakers

my alsa info output is here [http://www.alsa-project.org/db/?f=23dc54d8214dff59af255aac661a31e2be286af5](http://www.alsa-project.org/db/?f=23dc54d8214dff59af255aac661a31e2be286af5)

---

### Post by svyr on 2018-10-19
> **svyr said:**
> hello,  can anyone think of what the issue might be for the clevo rebrand here  and ubuntu sound (live or installed , vs working in windows) or have any  suggested ways of troubleshooting it. [https://ubuntuforums.org/showthread.php?t=2403327](https://ubuntuforums.org/showthread.php?t=2403327)

basically it appears that the speaker and headphone outs are in Alsamixer and pulse and I can see ubuntu thinks pulse is getting output in pulse control panel (the orange sound indicator thing), but there's no output from either headphones or speakers

my alsa info output is here [http://www.alsa-project.org/db/?f=23dc54d8214dff59af255aac661a31e2be286af5](http://www.alsa-project.org/db/?f=23dc54d8214dff59af255aac661a31e2be286af5)

here's the pulseaudio -vvvv outputs with a couple of apps - still not working please help. 
[https://paste.ubuntu.com/p/7DBmfBVqkH/](https://paste.ubuntu.com/p/7DBmfBVqkH/)

---

### Post by svyr on 2018-10-19
[INDENT] 					 					hmmm it looks like maybe it's already fixed in the new alsa builds. 
basically nothing worked and I nearly gave up but found this guide
[https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure) 

step 4 and just adding the ppa and installing the hda audio daily build works

sudo apt-add-repository ppa:ubuntu-audio-dev/alsa-daily

sudo apt-get update

sudo apt-get install oem-audio-hda-daily-dkms

reboot

then both alsa and pulse audio outputs work 					 
 				[/INDENT]

---

### Post by alin742 on 2018-10-23
Thank you so much... I had this problem were alsa mixer displayed pcm but not the speakers or the headphones and there was no auto mute option

---

### Post by yazdzik-k on 2018-10-26
Dear friends,

Using the procedure in [https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure),  I can achieve working sound.

Problems:

This does not last across reboots.  (laptop,  so often rebooted)
Pavucontrol does not mute system sounds.  (for anyone coming across this, one can kill the sounds in dconf,  so this much solved)

Running mate desktop on upgrade from  18.04.  (not ubuntu mate the distro)  

there were a number of vicious problems with update,  but now all is running smoothly except for sound.

It is a nuisance to have the noise,  and worse,  to have to execute that command every time I reboot,  as i travel a lot.

Any suggestions?


after running the command from the link above:


```
cat /proc/asound/{version,cards,devices,hwdep,pcm,seq/clients}; ls -l /usr/share/pulseaudio/alsa-mixer/paths/; sudo rm /etc/asound.conf; sudo rm -r ~/.pulse ~/.asound* ;sudo rm ~/.pulse-cookie; sudo apt-get update; sudo apt-get install aptitude; sudo aptitude install paman gnome-alsamixer libasound2-plugins padevchooser libsdl1.2debian-pulseaudio; sudo lshw -short;ls -lart /dev/snd; find /lib/modules/`uname -r` | grep snd ;cat /dev/sndstat; lspci -nn; lsusb; sudo which alsactl; sudo fuser -v /dev/dsp /dev/snd/* ; dpkg -S bin/slmodemd; dmesg | egrep 'EMU|probe|emu|ALSA|alsa|ac97|udi|snd|ound|irmware'; sudo /etc/init.d/sl-modem-daemon status; sudo grep model /etc/modprobe.d/* ; sudo dmidecode|egrep 'anufact|roduct|erial|elease'; lsmod | egrep 'snd|usb|midi|udio'; pacmd list-sinks; aplay -l; sudo alsa force-reload;  ubuntu-support-status ; sudo lshw -C sound
```







 reading the output,  it appears that timidity daemon races with pulse.   Thus,  the most practical solution is to purge timidity for the time being,  since there are other ways of playing midi right now. 

This is written to help anyone searching for what may not be an obvious problem.


Best,
M

---

### Post by Yardstick on 2018-12-08
I think I have a new and interesting sound failure in Ubuntu 18.04 on an Intel Nuc hooked up to my TV via HDMI.  Sometimes there is sound, sometimes there is no sound.  I have gone through several troubleshooting guides and still haven't figured it out.  I have narrowed it down to a problem with certain videos on YouTube and certain songs on Pandora/Slacker/Spotify.  Netflix and Amazon Video both play sound consistently.  I am primarily using Firefox, but I have verified the no-sound problem with Chrome as well.  I thought it could be a licensing issue, but it happens sometimes with YouTube videos that have no music.  Any ideas?

---

### Post by nlona on 2019-03-31
[https://ubuntuforums.org/showthread.php?t=2415634](https://ubuntuforums.org/showthread.php?t=2415634)
Huge problem no sound at all and would really needs a step by step how to get my alc662 rev1 analog work

---

### Post by mmmoshko-8 on 2019-08-27
hi Ubuntu Gurus ... 
I am a rookie at this ... I have been using ubuntu for 10 years nearly trouble free ... this is the first major problem I have had in that time. first of all let me start with the issue, then I will go into the hardware etc ... then hopefully you can help so bare with me I am about to give you tons of info in hopes to expand the help.

Section 1.
the Hardware
MSI motherboard Z370-A Pro
Realtek ALC892 Soundcard
Nvidia G710 Video card
6 Screens (yes between the onboard and Nvidia I have 6 outputs, 2 HDMI, 2 DVI, 1 DP, 1VGA)
HDMI screens are Lenovo LEN LT2223zwC


Section 2.
Software/OS
Ubuntu 18: Kernel 4.15.0-58 Generic
Nvidia 390 installed directly from nvidia

Section 3.
```
Firehose output for information for techies to help troubleshoot
modinfo snd-hda-intel
filename:       /lib/modules/4.15.0-58-generic/updates/dkms/snd-hda-intel.ko
description:    Intel HDA driver
license:        GPL
srcversion:     EAB27AC36BCDA02A3A68431
alias:          pci:v00001022d*sv*sd*bc04sc03i00*
alias:          pci:v00001002d*sv*sd*bc04sc03i00*
alias:          pci:v000015ADd00001977sv*sd*bc*sc*i*
alias:          pci:v000017F3d00003010sv*sd*bc*sc*i*
alias:          pci:v000013F6d00005011sv*sd*bc*sc*i*
alias:          pci:v00001102d00000009sv*sd*bc*sc*i*
alias:          pci:v00001102d00000012sv*sd*bc*sc*i*
alias:          pci:v00001102d00000010sv*sd*bc*sc*i*
alias:          pci:v00006549d00002200sv*sd*bc*sc*i*
alias:          pci:v00006549d00001200sv*sd*bc*sc*i*
alias:          pci:v000010DEd*sv*sd*bc04sc03i00*
alias:          pci:v000010B9d00005461sv*sd*bc*sc*i*
alias:          pci:v00001039d00007502sv*sd*bc*sc*i*
alias:          pci:v00001106d00009140sv*sd*bc*sc*i*
alias:          pci:v00001106d00009170sv*sd*bc*sc*i*
alias:          pci:v00001106d00003288sv*sd*bc*sc*i*
alias:          pci:v00001002d0000AAF0sv*sd*bc*sc*i*
alias:          pci:v00001002d0000AAE0sv*sd*bc*sc*i*
alias:          pci:v00001002d0000AAE8sv*sd*bc*sc*i*
alias:          pci:v00001002d0000AAD8sv*sd*bc*sc*i*
alias:          pci:v00001002d0000AAC8sv*sd*bc*sc*i*
alias:          pci:v00001002d0000AAC0sv*sd*bc*sc*i*
alias:          pci:v00001002d0000AAB0sv*sd*bc*sc*i*
alias:          pci:v00001002d0000AAA8sv*sd*bc*sc*i*
alias:          pci:v00001002d0000AAA0sv*sd*bc*sc*i*
alias:          pci:v00001002d00009902sv*sd*bc*sc*i*
alias:          pci:v00001002d0000AA98sv*sd*bc*sc*i*
alias:          pci:v00001002d0000AA90sv*sd*bc*sc*i*
alias:          pci:v00001002d0000AA88sv*sd*bc*sc*i*
alias:          pci:v00001002d0000AA80sv*sd*bc*sc*i*
alias:          pci:v00001002d0000AA68sv*sd*bc*sc*i*
alias:          pci:v00001002d0000AA60sv*sd*bc*sc*i*
alias:          pci:v00001002d0000AA58sv*sd*bc*sc*i*
alias:          pci:v00001002d0000AA50sv*sd*bc*sc*i*
alias:          pci:v00001002d0000AA48sv*sd*bc*sc*i*
alias:          pci:v00001002d0000AA40sv*sd*bc*sc*i*
alias:          pci:v00001002d0000AA38sv*sd*bc*sc*i*
alias:          pci:v00001002d0000AA30sv*sd*bc*sc*i*
alias:          pci:v00001002d0000AA28sv*sd*bc*sc*i*
alias:          pci:v00001002d0000AA20sv*sd*bc*sc*i*
alias:          pci:v00001002d0000AA18sv*sd*bc*sc*i*
alias:          pci:v00001002d0000AA10sv*sd*bc*sc*i*
alias:          pci:v00001002d0000AA08sv*sd*bc*sc*i*
alias:          pci:v00001002d0000AA00sv*sd*bc*sc*i*
alias:          pci:v00001002d00009840sv*sd*bc*sc*i*
alias:          pci:v00001002d0000970Fsv*sd*bc*sc*i*
alias:          pci:v00001002d0000960Fsv*sd*bc*sc*i*
alias:          pci:v00001002d00007919sv*sd*bc*sc*i*
alias:          pci:v00001002d0000793Bsv*sd*bc*sc*i*
alias:          pci:v00001002d000015B3sv*sd*bc*sc*i*
alias:          pci:v00001002d0000157Asv*sd*bc*sc*i*
alias:          pci:v00001002d00001308sv*sd*bc*sc*i*
alias:          pci:v00001002d00000002sv*sd*bc*sc*i*
alias:          pci:v00001022d000015E3sv*sd*bc*sc*i*
alias:          pci:v00001022d0000157Asv*sd*bc*sc*i*
alias:          pci:v00001022d0000780Dsv*sd*bc*sc*i*
alias:          pci:v00001002d00004383sv*sd*bc*sc*i*
alias:          pci:v00001002d0000437Bsv*sd*bc*sc*i*
alias:          pci:v00008086d*sv*sd*bc04sc03i00*
alias:          pci:v00008086d00003A6Esv*sd*bc*sc*i*
alias:          pci:v00008086d00003A3Esv*sd*bc*sc*i*
alias:          pci:v00008086d0000293Fsv*sd*bc*sc*i*
alias:          pci:v00008086d0000293Esv*sd*bc*sc*i*
alias:          pci:v00008086d0000284Bsv*sd*bc*sc*i*
alias:          pci:v00008086d0000269Asv*sd*bc*sc*i*
alias:          pci:v00008086d000027D8sv*sd*bc*sc*i*
alias:          pci:v00008086d00002668sv*sd*bc*sc*i*
alias:          pci:v00008086d00002284sv*sd*bc*sc*i*
alias:          pci:v00008086d00000F04sv*sd*bc*sc*i*
alias:          pci:v00008086d0000080Asv*sd*bc*sc*i*
alias:          pci:v00008086d0000811Bsv*sd*bc*sc*i*
alias:          pci:v00008086d00003B56sv*sd*bc*sc*i*
alias:          pci:v00008086d0000160Csv*sd*bc*sc*i*
alias:          pci:v00008086d00000D0Csv*sd*bc*sc*i*
alias:          pci:v00008086d00000C0Csv*sd*bc*sc*i*
alias:          pci:v00008086d00000A0Csv*sd*bc*sc*i*
alias:          pci:v00008086d00003198sv*sd*bc*sc*i*
alias:          pci:v00008086d00001A98sv*sd*bc*sc*i*
alias:          pci:v00008086d00005A98sv*sd*bc*sc*i*
alias:          pci:v00008086d000034C8sv*sd*bc*sc*i*
alias:          pci:v00008086d000006C8sv*sd*bc*sc*i*
alias:          pci:v00008086d000002C8sv*sd*bc*sc*i*
alias:          pci:v00008086d00009DC8sv*sd*bc*sc*i*
alias:          pci:v00008086d0000A348sv*sd*bc*sc*i*
alias:          pci:v00008086d0000A2F0sv*sd*bc*sc*i*
alias:          pci:v00008086d00009D71sv*sd*bc*sc*i*
alias:          pci:v00008086d0000A171sv*sd*bc*sc*i*
alias:          pci:v00008086d00009D70sv*sd*bc*sc*i*
alias:          pci:v00008086d0000A170sv*sd*bc*sc*i*
alias:          pci:v00008086d00009CA0sv*sd*bc*sc*i*
alias:          pci:v00008086d00009C21sv*sd*bc*sc*i*
alias:          pci:v00008086d00009C20sv*sd*bc*sc*i*
alias:          pci:v00008086d0000A270sv*sd*bc*sc*i*
alias:          pci:v00008086d0000A1F0sv*sd*bc*sc*i*
alias:          pci:v00008086d00008D21sv*sd*bc*sc*i*
alias:          pci:v00008086d00008D20sv*sd*bc*sc*i*
alias:          pci:v00008086d00008CA0sv*sd*bc*sc*i*
alias:          pci:v00008086d00008C20sv*sd*bc*sc*i*
alias:          pci:v00008086d00001E20sv*sd*bc*sc*i*
alias:          pci:v00008086d00001D20sv*sd*bc*sc*i*
alias:          pci:v00008086d00001C20sv*sd*bc*sc*i*
depends:        snd-hda-core,snd-hda-codec,snd-pcm,snd
retpoline:      Y
name:           snd_hda_intel
vermagic:       4.15.0-58-generic SMP mod_unload 
parm:           index:Index value for Intel HD audio interface. (array of int)
parm:           id:ID string for Intel HD audio interface. (array of charp)
parm:           enable:Enable Intel HD audio interface. (array of bool)
parm:           model:Use the given board model. (array of charp)
parm:           position_fix:DMA pointer read method.(-1 = system default, 0 = auto, 1 = LPIB, 2 = POSBUF, 3 = VIACOMBO, 4 = COMBO, 5 = SKL+). (array of int)
parm:           bdl_pos_adj:BDL position adjustment offset. (array of int)
parm:           probe_mask:Bitmask to probe codecs (default = -1). (array of int)
parm:           probe_only:Only probing and no codec initialization. (array of int)
parm:           jackpoll_ms:Ms between polling for jack events (default = 0, using unsol events only) (array of int)
parm:           single_cmd:Use single command to communicate with codecs (for debugging only). (bint)
parm:           enable_msi:Enable Message Signaled Interrupt (MSI) (bint)
parm:           patch:Patch file for Intel HD audio interface. (array of charp)
parm:           beep_mode:Select HDA Beep registration mode (0=off, 1=on) (default=1). (array of bool)
parm:           power_save:Automatic power-saving timeout (in second, 0 = disable). (xint)
parm:           pm_blacklist:Enable power-management blacklist (bool)
parm:           power_save_controller:Reset controller in power save mode. (bool)
parm:           align_buffer_size:Force buffer and period sizes to be multiple of 128 bytes. (bint)
parm:           snoop:Enable/disable snooping (bint)

modinfo soundcore
filename:       /lib/modules/4.15.0-58-generic/kernel/sound/soundcore.ko
alias:          char-major-14-*
license:        GPL
author:         Alan Cox
description:    Core sound module
srcversion:     243B76FF0432C637D451917
depends:        
intree:         Y
vermagic:       4.2.0-42-generic SMP mod_unload modversions 
signat:         X509
signer:         Build time autogenerated kernel key
sig_key:        71:38:F1:4B:5C:C6:26:BA:6E:4B:75:86:0A:1E:E2:08:2D:E8:20:E2
sig_hashalgo:   sha512
parm:           preclaim_oss:int


lsmod | grep snd_hda_intel


lspci -nnk | grep -A2 Audio
01:00.1 Audio device [0403]: NVIDIA Corporation GK208 HDMI/DP Audio Controller [10de:0e0f] (rev a1)
	Subsystem: ASUSTeK Computer Inc. GK208 HDMI/DP Audio Controller [1043:85f7]
	Kernel modules: snd_hda_intel
03:00.0 RAID bus controller [0104]: Adaptec AAC-RAID [9005:0285] (rev 09)


dkms status
nvidia, 390.129, 4.15.0-58-generic, x86_64: installed
oem-audio-hda-daily, 0.201905191531~ubuntu18.04.1, 4.15.0-58-generic, x86_64: installed




upload=true&script=true&cardinfo=
!!################################
!!ALSA Information Script v 0.4.64
!!################################


!!Script ran on: Tue Aug 27 17:32:40 UTC 2019




!!Linux Distribution
!!------------------


Ubuntu 18.04.3 LTS \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 18.04.3 LTS" NAME="Ubuntu" ID=ubuntu ID_LIKE=debian PRETTY_NAME="Ubuntu 18.04.3 LTS" HOME_URL="https://www.ubuntu.com/" SUPPORT_URL="https://help.ubuntu.com/" BUG_REPORT_URL="https://bugs.launchpad.net/ubuntu/" PRIVACY_POLICY_URL="https://www.ubuntu.com/legal/terms-and-policies/privacy-policy" UBUNTU_CODENAME=bionic




!!DMI Information
!!---------------


Manufacturer:      Micro-Star International Co., Ltd.
Product Name:      MS-7B48
Product Version:   1.0
Firmware Version:  2.60




!!Kernel Information
!!------------------


Kernel release:    4.15.0-58-generic
Operating System:  GNU/Linux
Architecture:      x86_64
Processor:         x86_64
SMP Enabled:       Yes




!!ALSA Version
!!------------


Driver version:     
Library version:    1.1.9
Utilities version:  1.1.3




!!Loaded ALSA modules
!!-------------------






!!Sound Servers on this system
!!----------------------------


Pulseaudio:
      Installed - Yes (/usr/bin/pulseaudio)
      Running - Yes




!!Soundcards recognised by ALSA
!!-----------------------------






!!PCI Soundcards installed in the system
!!--------------------------------------


01:00.1 Audio device: NVIDIA Corporation GK208 HDMI/DP Audio Controller (rev a1)




!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!-------------------------------------------------------


01:00.1 0403: 10de:0e0f (rev a1)
	Subsystem: 1043:85f7




!!Modprobe options (Sound related)
!!--------------------------------


snd_pcsp: index=-2
snd_usb_audio: index=-2
snd_atiixp_modem: index=-2
snd_intel8x0m: index=-2
snd_via82xx_modem: index=-2
snd_hda_intel: model=auto
snd_atiixp_modem: index=-2
snd_intel8x0m: index=-2
snd_via82xx_modem: index=-2
snd_usb_audio: index=-2
snd_usb_caiaq: index=-2
snd_usb_ua101: index=-2
snd_usb_us122l: index=-2
snd_usb_usx2y: index=-2
snd_cmipci: mpu_port=0x330 fm_port=0x388
snd_pcsp: index=-2
snd_usb_audio: index=-2
snd_hda_intel: model=generic
snd_hda_intel: model=auto
snd_hda_intel: model=basic
snd_hda_intel: probe_mask=1
snd_hda_intel: probe_mask=2
snd_hda_intel: model=generic
snd_hda_intel: model=auto
snd_hda_intel: model=auto
snd_hda_intel: model=generic
snd_hda_intel: id=Generic_1 index=0
snd_hda_intel: id=Generic index=1
snd_hda_intel: single_cmd=1
snd_hda_intel: probe_mask=1
snd_hda_intel: enable_msi=1




!!Loaded sound module options
!!---------------------------




!!ALSA Device nodes
!!-----------------


crw-rw----+ 1 root audio 116,  1 Aug 26 21:25 /dev/snd/seq
crw-rw----+ 1 root audio 116, 33 Aug 26 21:25 /dev/snd/timer




!!ALSA configuration files
!!------------------------


!!System wide config file (/etc/asound.conf)


pcm.!default {
    type hw
    card 1
}


ctl.!default {
    type hw           
    card 1
}




!!Aplay/Arecord output
!!--------------------


APLAY


aplay: device_list:270: no soundcards found...


ARECORD


arecord: device_list:270: no soundcards found...


!!Amixer output
!!-------------




!!Alsactl output
!!--------------


--startcollapse--
--endcollapse--




!!All Loaded Modules
!!------------------


Module
btrfs
zstd_compress
ufs
qnx4
hfsplus
hfs
minix
ntfs
msdos
jfs
xfs
nls_utf8
isofs
xfrm_user
xfrm4_tunnel
tunnel4
ipcomp
xfrm_ipcomp
esp4
ah4
af_key
xfrm_algo
uvcvideo
videobuf2_vmalloc
videobuf2_memops
videobuf2_v4l2
videobuf2_core
videodev
media
l2tp_ppp
l2tp_netlink
l2tp_core
ip6_udp_tunnel
udp_tunnel
pppox
oss_usb
osscore
pci_stub
vboxpci
vboxnetadp
vboxnetflt
vboxdrv
nvidia_uvm
nvidia_drm
nvidia_modeset
nvidia
joydev
intel_wmi_thunderbolt
mxm_wmi
input_leds
i915
mei_me
intel_rapl
x86_pkg_temp_thermal
intel_powerclamp
coretemp
kvm_intel
kvm
irqbypass
crct10dif_pclmul
crc32_pclmul
ghash_clmulni_intel
pcbc
aesni_intel
aes_x86_64
crypto_simd
glue_helper
cryptd
intel_cstate
intel_rapl_perf
wmi
drm_kms_helper
drm
ipmi_devintf
ipmi_msghandler
i2c_algo_bit
fb_sys_fops
syscopyarea
sysfillrect
sysimgblt
acpi_pad
mei
video
shpchp
mac_hid
sch_fq_codel
parport_pc
ppdev
lp
parport
ip_tables
x_tables
autofs4
raid10
raid456
async_raid6_recov
async_memcpy
async_pq
async_xor
async_tx
xor
uas
usb_storage
raid6_pq
libcrc32c
raid1
raid0
multipath
linear
dm_mirror
dm_region_hash
dm_log
hid_generic
usbhid
hid
r8169
aacraid
ahci
mii
libahci




!!ALSA/HDA dmesg
!!--------------


[    0.049009] ACPI: Added _OSI(Linux-Dell-Video)
[    0.049009] ACPI: Added _OSI(Linux-Lenovo-NV-HDMI-Audio)
[    0.049009] ACPI: Added _OSI(Linux-HPI-Hybrid-Graphics)
--
[   55.222257] usb 1-11.4: SerialNumber: 000000000000
[   55.222804] New audioctl device 11.4/0 - USB sound device
[   55.222824] ------------[ cut here ]------------
--
[   55.223241] ---[ end trace f9a10ddce7d392b5 ]---
[   55.223298] New audio streaming device 11.4/1 - USB sound device
[   55.223356] New audio streaming device 11.4/2 - USB sound device
[   55.340277] input: Lenovo LT2223Z as /devices/pci0000:00/0000:00:14.0/usb1/1-11/1-11.4/1-11.4:1.3/0003:0572:1415.0005/input/input8

```

yet with all this ... I have no audio ... 

I have tried to purge alsa and pulse, I have tried reinstalling the nvidia card and purge dkms, I have tried purge the kernel and reinstall it,  I have rebooted multiple times after each change ... I even removed the nvidia card and its drivers and go with only 3 screens and still no luck,

anyone have any ideas.  I am ready for the questions .... help please.

Matee Moshkovits

---

### Post by wildmanne39 on 2019-08-27
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by mmmoshko-8 on 2019-08-27
thank you for the correction ... 

Matee

---

### Post by mrsean on 2020-03-16
Here is my alsa setup, please advise as I have removed and reinstalled ALSA and also installed generic sound drivers for ubuntu:

[http://alsa-project.org/db/?f=508f122eccfc3630e4428f07787429dd21ed8501](http://alsa-project.org/db/?f=508f122eccfc3630e4428f07787429dd21ed8501)

Now ubuntu 18.04 not seeing my built in sound card on ASRock FM2A55M-DGS (5.1 CH HD Audio (Realtek ALC662 Audio Codec))
Problem started because I could only get stereo 2 channel with default ubuntu install, so tried to get Realtek drivers so I could access full 5.1 surround sound.

---

### Post by gleedadswell on 2020-05-01
Sound on my current laptop has been dicey for a long time.  But it was more of less working as recently as last night.  This morning, no sound at all (no speakers working, no microphones working, no devices showed up in the Sound Settings).  I did a purge/reinstall of alsa and pulseaudio.  That got me back **partial** functionality sound so that the current situation is as follows:

With no devices (headphones/mics) plugged in the Sound Settings only list the dreaded "Dummy Output" and nothing is listed for input devices.  If I plug headphones in using a usb adaptor or plug in a usb mic then those show up in Sound settings and sound mostly works in them (both left and right speaker output get sent to both speakers in the headphones, but other than that it seems to be working).  Plugging in to the headphone jack gets me nothing.

I've looked at a lot of places such as

[https://docs.google.com/document/d/1iTlJ8BfqXUjaHO__TEdlkvuqB1WLOkGaudngc5SFLMI/edit](https://docs.google.com/document/d/1iTlJ8BfqXUjaHO__TEdlkvuqB1WLOkGaudngc5SFLMI/edit) 
[https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)
[https://wiki.archlinux.org/index.php/PulseAudio/Troubleshooting](https://wiki.archlinux.org/index.php/PulseAudio/Troubleshooting)

and done all the usual things such as killing and restarting pulseaudio, killing and restarting alsa, etc.  I've also tried some advice from the third link above to edit the /etc/pulse/default.pa to add lines to get it to manually find the sound card.  That involves adding a line

```
load-module module-alsa-sink device=hw:0,0
```

That just makes pulseaudio fail to launch.

Here is some diagnostic info, using the very helpful command from the first link above:

```
echo "Sound cards recognized by the system:"; lspci -nn | grep --color=none '\[04[80][13]\]'; echo "Sound cards recognized by ALSA:"; lspci -nn | grep '\[04[80][13]\]' | while read line; do lspci -nnk | grep -A 3 '\[04[80][13]\]' | grep -e 'Kernel modules: ..*' -e '\[04[80][13]\]' | grep --color=none -F "$line"; done; echo "Sound cards recognized by ALSA, and activated:"; lspci -nn | grep '\[04[80][13]\]' | while read line; do lspci -nnk | grep -A 3 '\[04[80][13]\]' | grep -e 'Kernel drivers in use: ..*' -e '\[04[80][13]\]' | grep --color=none -F "$line"; doneSound cards recognized by the system:
00:1f.3 Audio device [0403]: Intel Corporation CM238 HD Audio Controller [8086:a171] (rev 31)
Sound cards recognized by ALSA:
00:1f.3 Audio device [0403]: Intel Corporation CM238 HD Audio Controller [8086:a171] (rev 31)
Sound cards recognized by ALSA, and activated:
00:1f.3 Audio device [0403]: Intel Corporation CM238 HD Audio Controller [8086:a171] (rev 31)
```

So, the system sees the sound card, ALSA sees the sound card and it claims it is activated.  However, aplay -l says

```
aplay -l
aplay: device_list:268: no soundcards found...
```  

which confuses me since I thought that was the list of what alsa could see. So it seem to disagree with the previous command's output.  Clearly one of those commands doesn't do what I think it does.  If I plug in my headphones using a usb adaptor then it shows up:

```
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 1: Device [Plugable USB Audio Device], device 0: USB Audio [USB Audio]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
```

hwinfo tells me the soundcard is not active

```
hwinfo --sound
20: PCI 1f.3: 0403 Audio device                                 
  [Created at pci.366]
  Unique ID: nS1_.qYoboy2l6HD
  SysFS ID: /devices/pci0000:00/0000:00:1f.3
  SysFS BusID: 0000:00:1f.3
  Hardware Class: sound
  Model: "Intel Audio device"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0xa171 
  SubVendor: pci 0x1028 "Dell"
  SubDevice: pci 0x07e1 
  Revision: 0x31
  Memory Range: 0xdf328000-0xdf32bfff (rw,non-prefetchable)
  Memory Range: 0xdf300000-0xdf30ffff (rw,non-prefetchable)
  IRQ: 11 (no events)
  Module Alias: "pci:v00008086d0000A171sv00001028sd000007E1bc04sc03i00"
  Driver Info #0:
    Driver Status: snd_hda_intel is not active
    Driver Activation Cmd: "modprobe snd_hda_intel"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
```

Trying modprobe fails to load snd_hda_intel

```
sudo modprobe -v snd_hda_intel
insmod /lib/modules/4.4.0-178-generic/updates/dkms/snd-hda-codec.ko 
modprobe: ERROR: could not insert 'snd_hda_intel': Invalid argument
```

I speculate that this is the crux of the problem.  Doing a search on this error message hasn't turned up anything that has worked.  The only advice I've found is reinstalling alsa and pulseaudio (already done) and adding the ppa to the ubuntu-audio-dev/alsa-daily and updating, which I've also done.  Neither of those have worked.  I've tried a bunch of other things but this post is probably long enough already.

Next steps?

Edit: I should probably mention that I'm running Ubuntu 16.04.
Further update: Even with usb headphones where sound sort of works something is definitely strange.  If I listen to music the vocals are very muted compared to everything else.  If I fiddle with the left/right balance then they come back.  But with the balance in the centre sound is definitely strange.  Putting the balance all the way L or all the way R seems to make things sound more normal.  Odd...

---

### Post by gleedadswell on 2020-05-01
I seem to have fixed it.  On this page

[https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/191603](https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/191603)

the poster found that they had multiple copies of  [COLOR=#333333][FONT=Ubuntu]snd-hda-codec.ko and of [/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]snd-hda-[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]intel.ko and that manually loading some worked while others did not.  The issue seemed to be that the ones from the [/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]ubuntu-[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]audio-dev ppa didn't work and those were what was being loaded.  On that theory I removed the [/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]ubuntu-[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]audio-dev package.  This seems to have fixed my sound (.  That still leaves me confused since I *think* I installed those in the process of trying to fix this.  But it's possible I had already installed them during some earlier round of sound problems and a recent  update rendered them broken for my system.  Anyway, the problem seems to have been the incorrect snd-hda-codec which caused modprobe to fail to load snd-hda-intel.

My microphone jack and my internal microphone don't work, but they haven't worked for a long time.  I think I just need to fiddle with my pin assignments using hdajackretask until I find a setup that works.

Cheers!
[/FONT][/COLOR]

---

### Post by Jim_Lynch on 2020-10-19
I'm running a MQTT app that I would like to be able to play .mp3 files.  I attempted to simply run mpg321 but that fails with  

Playing MPEG stream from 192.168.2.55 ...MPEG 1.0 layer III, 56 kbit/s, 44100 Hz stereo
Error opening unknown libao pulse driver. (Is device in use?)

Running mpg321 from the console works fine.  And no, the device isn't in use.  There isn't anyone logged into the console normally but I did try it both ways.

Running 20.04


```
 cat /proc/asound/cards
 0 [NVidia_1       ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xdeef4000 irq 22
 1 [NVidia         ]: HDA-Intel - HDA NVidia
                    HDA NVidia at 0xdef7c000 irq 18


```
Thanks,
Jim

---

### Post by gus_zernial on 2021-03-08
I have an AMD X570 mobo, 5600X CPU, Kubuntu 21.04 development latest with all updates, kernel 5.10.0-14-generic, and Nvidia GTX 1650 graphics card. Generally working well, but no sound.

Card 0 is NVidia HDA HDMI (I've turned off NVIDIA HDMI in System Settings audio settings)
Card 1 is Generic [HD-Audio Generic], device 0: Realtek ALCS1200A Analog

The ACLS1200A uses snd_hda_intel and snd_hda_codec_realtek, the correct sound modules seem to be loaded, and both sound device show up in System Settings

The sound works using my Windows 10 "Win2go" (live image) USB stick, and the NVIDIA HDA HDMI using an audio splitter, but not on hirsute 21.04 thru mobo audio output jacks.

I've set the volumes in alsamixer and I've tried "lots of things" to fix, no joy. 

My alsa-info script output is at [http://alsa-project.org/db/?f=b66fb682eb5ec70083bba7442096442b5499c4d8](http://alsa-project.org/db/?f=b66fb682eb5ec70083bba7442096442b5499c4d8)

Appreciate help -  Gus

---

