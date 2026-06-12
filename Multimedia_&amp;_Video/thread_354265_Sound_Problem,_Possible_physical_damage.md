---
title: "Sound Problem, Possible physical damage?"
date: 2007-02-05
forum: Multimedia &amp; Video
---

### Post by ReapingWildOats on 2007-02-05
Long Story Short:  Mysterious burn mark appears on my laptop around the same time Windows permanently crashes after itunes tells me all playback is disabled.  Install ubuntu 6.06 LTS and have perfect use except for sound.  I used the Comprehensive Sound Guide to install ATI IXP SB400 sound drive because of my lspci output:

```
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:04.0 PCI bridge: ATI Technologies Inc Unknown device 5a36
00:05.0 PCI bridge: ATI Technologies Inc Unknown device 5a37
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 83)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI (rev 80)
00:14.2 Audio device: ATI Technologies Inc Unknown device 437b (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS482 [Radeon Xpress 200M]
06:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
06:02.0 Ethernet controller: Atheros Communications, Inc. AR5005G 802.11abg NIC (rev 01)
06:04.0 CardBus bridge: ENE Technology Inc CB-712/4 Cardbus Controller (rev 10)
06:04.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller (rev 01)
06:04.2 Class 0805: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (rev 01)
06:04.3 FLASH memory: ENE Technology Inc FLASH memory: ENE Technology Inc: (rev 01)
06:04.4 FLASH memory: ENE Technology Inc Unknown device 0551 (rev 01)

```

Currently I have the 64bit version of ubuntu, edgy eft

any general help to figure out if it is physically damaged??

Pretty lost at the moment:confused:


computer: acer aspire 5002wlmi
1gig ddr2
120 gig hd

don't know much else that could help

---

### Post by glotz on 2007-02-05
I have no clue about anything whatsoever but just read on another laptop/sound issue thread that you're supposed to boot with ACPI=off

To turn ACPI off edit the /boot/grub/grub.conf file and add ``acpi=off'' at the end of the kernel line that you'll be using.

EDIT: whoopsie, I meant menu.lst naturally! (should never trust copy paste...)

---

### Post by ReapingWildOats on 2007-02-05
I do not have a grub.conf file, should I create one?

I have: default     
e2fs_stage1_5 
installed-version
menu.lst   
minix_stage1_5  
stage1  xfs_stage1_5
device.map
 fat_stage1_5   
jfs_stage1_5     
 menu.lst~ 
 reiserfs_stage1_5 
 stage2

I now also remember something about this laptop having HD audio which, on the ALSA page, seems to indicate I need the sb450 drivers.  But now it says I don't have module assistant package. argh.

Thanks all.

---

### Post by kevinatkins on 2007-02-05
The 'mysterious burn mark' doesn't sound so good, but could you just clarify: do you have any sound in Windows? If there's no sound in Windows, even with correct drivers, then it could well be a hardware problem.

As for ACPI.. that's more to do with power management and it may or may not affect sound - still worth trying booting without ACPI, but my hunch is that your problem lies elsewhere. I've installed a few versions of Ubuntu on a couple of laptops and sound has never been an issue - it 'just works'....

---

### Post by ReapingWildOats on 2007-02-05
Not quite sure about sound in windows.  I booted it up once and launched itunes and immedietly got the error about playback being disabled.  From there it never successfully booted up again into windows.  With ubuntu, however, it boots just fine.  But with no sound.  The burn mark is really minor, no discoloration, just a small 3mm indent with hardly any bubbling at all.  It could be just a easy scapegoat for this problem.  And I am not even sure where the soundcard is located.  The burn is about 1/2 an inch from the windows key, about an inch and a half to the left of the touchpad.

Any other info needed?

---

### Post by glotz on 2007-02-05
Whereas Kev might be right about this all, it was wrong file. The correct one is menu.lst, of course. :)

---

### Post by ReapingWildOats on 2007-02-05
UPDATE: system beeps (I pushed the down arrow key in console this time, don't know what else to call them) can be heard coming from my speakers, meanwhile I get this error message:
```

ALSA lib confmisc.c:670:(snd_func_card_driver) cannot find card '0'
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:391:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1070:(snd_func_refer) error evaluating name
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3947:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2146:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib confmisc.c:670:(snd_func_card_driver) cannot find card '0'
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:391:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1070:(snd_func_refer) error evaluating name
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3947:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2146:(snd_pcm_open_noupdate) Unknown PCM default

```
I don't know what any of this means!

---

### Post by kevinatkins on 2007-02-05
Hi,

OK, got to admit I'm not sure on this one. But I have done a quick Google on 'Audio device: ATI Technologies Inc Unknown device 437b (rev 01)' which looks like it might turn up a few leads for you. If you can determine what sort of sound hardware is fitted (looks like Intel High Definition Audio), you could take a look at the ALSA website and see what's what there.

Sorry can't be much more help.

---

### Post by ReapingWildOats on 2007-02-05
Ok so using the comprehensive sound guide I compiled the alsa driver using module-assistant and used the atiixp-modem driver which is for HD audio cards (i think I have this?) but on running this: ```
sudo module-assistant a-i   alsa-source
``` It began to load but then failed.  I have three options: VIEW (Examine the build log file), CONTINUE, or STOP.  I clicked view but the error message is far too long to copy over here.  Any ideas?

---

### Post by ReapingWildOats on 2007-02-05
going through that entire error log I found:```
make[6]: *** [/usr/src/modules/alsa-driver/drivers/serialmidi.o] Error 1   &#9618;                                        
                                       &#9474; make[5]: *** [/usr/src/modules/alsa-driver/drivers] Error 2                &#9618;                                        
                                       &#9474; make[4]: *** [_module_/usr/src/modules/alsa-driver] Error 2                &#9618;                                        
                                       &#9474; make[3]: *** [modules] Error 2                                             &#9618;                                        
                                       &#9474; make[3]: Leaving directory `/usr/src/linux-headers-2.6.17-10-generic'      &#9618;                                        
                                       &#9474; make[2]: *** [compile] Error 2                                             &#9618;                                        
                                       &#9474; make[2]: Leaving directory `/usr/src/modules/alsa-driver'                  &#9618;                                        
                                       &#9474; make[1]: *** [build-stamp] Error 2                                         &#9618;                                        
                                       &#9474; make[1]: Leaving directory `/usr/src/modules/alsa-driver'                  &#9646;                                        
                                       &#9474; make: *** [kdist_image] Error 2  
```

---

### Post by ReapingWildOats on 2007-02-05
seems this is an on-going issue? [http://www.ubuntuforums.org/archive/index.php/t-251123.html](http://www.ubuntuforums.org/archive/index.php/t-251123.html)

---

### Post by ReapingWildOats on 2007-02-06
BUMP

from my research this seems a somewhat common problem, anyone have any ideas?

edit: a common problem with no common solution.

---

