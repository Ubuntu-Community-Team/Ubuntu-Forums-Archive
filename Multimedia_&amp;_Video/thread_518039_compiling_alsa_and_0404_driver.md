---
title: "compiling alsa and 0404 driver"
date: 2007-08-05
forum: Multimedia &amp; Video
---

### Post by BryceCovert on 2007-08-05
Hello, 

I've recently reinstalled linux on my main machine as I've heard there is finally alsa support for my soundcard, the emu 0404.

I've read a lot of people say it's been available since 1.0.14, so I checked my version.:
```

$ apt-cache show alsa-base
...
Source: alsa-driver
Version: 1.0.13-3ubuntu1

```

So I grabbed the source for 1.0.14, and tried to follow this tutorial::

[http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Creative+Labs&card=E-MU+1212m.&chip=CA0102%2C+FPGA&module=emu10k1-fpga](http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Creative+Labs&card=E-MU+1212m.&chip=CA0102%2C+FPGA&module=emu10k1-fpga)

And I get a configure error stating there is no card called emu10k1-fpga. So I do a cvs checkout of the latest bits and try it.... No luck either. Still statements that no such card exists.

The creative matrix says that it's not coming until 1.0.15, but there are a number of sites stating that it's working for them with 1.0.14. 

Unfortunately, I can't use my system without audio. I'd be willing to finish the driver if that's what it takes. It's worth it to me to be able to use my card.

Question 1, does anybody have any luck with emu 0404 or 1212m cards?

Question 2, if you are having luck, are you using emu10k1-fpga?

Thanks,

Bryce

---

### Post by caramelsoul on 2007-08-08
I would also like to know this as well.

---

### Post by tesoke on 2007-08-09
I hope the driver will be working. 
Want to switch to linux but there isn't a driver for my 0404.

---

### Post by geeve420 on 2007-12-05
I am going to bump this, I hope someone can get this to work. My EMU-0404 is the final piece of the get rid of Windows puzzle.:)Thanks 

Geeve

---

### Post by hektorr on 2008-01-19
i am also in need of emu 0404 alsa support.  please offer any updates / ideas that you may have regarding this!

---

### Post by Hobnobb on 2008-01-24
The emu 0404 pci -card is finally working :cool: for me with the latest alsa-driver-1.0.16rc1 ( jan 22 2008 ). It worked for some people earlier, It seems that these cards have different ID's depending on the produkction date. In the alsa-driver-1.0.16 they have updated this and now it works with more/all 0404 cards.
Thank You  ALSA-Project !  HALLELUJAA !!!!!

Only 44100 and 48000 sampling supported
If the sound crackles or plays back too fast; change base sampling to 44100 in alsamixer

To install you basicly can follow the instuctions on this page
[http://www.alsa-project.org/main/index.php/Matrix:Module-emu10k1-fpga](http://www.alsa-project.org/main/index.php/Matrix:Module-emu10k1-fpga)
Install the firmware package too before you do  'modprobe'

Good luck !

---

### Post by thierry13 on 2008-01-25
Hi,
Are you able to change the DSP options of the card to use the different effects? does it work?

Thanks
Regards,
Thierry

---

### Post by Hobnobb on 2008-01-28
Hi Thierry
Haven't had the time yet to test that but I saw that the firmware package had some effect modules like Chorus. I dunno how to get sound effects working in Linux but I'll play around with it this week and post an update.
I saw there is a multichannel mixerprogram called Rosegarden I'll install it and see if it can use effects and route in-and output-channel.

---

### Post by strawberryjam on 2008-03-02
I suppose this driver will work for my 1212m PCI too. I dont have the MicroDock so i guess it should. Problem is everytime i install this driver my entire installation gets messed. 

I am new to Linux but good at following orders and instructions.
Any advice on what to look out for?

Thanks

---

### Post by gladstone on 2008-04-28
I'm a 1616m PCMCIA user here and have been trying to get this working since Gutsy. Apparently ALSA now supports these cards and Hardy includes Alsa 1.0.16, but it doesn't work out-of-the-box for me still. Can anyone help?

---

### Post by zob on 2008-04-28
gladstone. If you want you can post the outputs of the commands that I refer to here:
[http://ubuntuforums.org/showthread.php?t=768934](http://ubuntuforums.org/showthread.php?t=768934)
You can post youre outputs in my post if you want. That way we can collect experiences and info in that place.

---

### Post by gladstone on 2008-05-05
Cheers zob, I managed to get it working in the end. Seems following [the same steps]("http://ubuntuforums.org/showthread.php?t=579548") as I tried for alsa v1.0.15 now work fine for v1.0.16!!

---

### Post by gladstone on 2008-05-08
Argh, just as I thought it was going well... I was fiddling around with the volume levels with the "volume control" item for XFCE panel and now I have no sound at all. I've tried adjusting in alsamixer and even recompiled but no sound :( any ideas? Modules are correctly loaded and alsamixer detects the card

---

### Post by sanus|art on 2008-06-01
> **gladstone said:**
> Argh, just as I thought it was going well... I was fiddling around with the volume levels with the "volume control" item for XFCE panel and now I have no sound at all. I've tried adjusting in alsamixer and even recompiled but no sound :( any ideas? Modules are correctly loaded and alsamixer detects the card

I use this script to install alsa for e-mu (0404 in my case):

** Here is the script **(and the instructions)**:**

[COLOR=Red]**[EDIT]**[/COLOR] - The script is in post [#22]("http://ubuntuforums.org/showpost.php?p=5236403&postcount=22").

[[COLOR=Red]*[/COLOR]] - Save it as 'E-MU.sh'
[[COLOR=Red]*[/COLOR]] - set permitions to execute 'sudo chmod 777 /path/to/script/E-MU.sh'
[[COLOR=Red]*[/COLOR]] - Run it as super user 'sudo sh /path/to/script/E-MU.sh'

---

### Post by ernix on 2008-06-21
I'm using ubuntustudio 8.04.
I tried to install alsa with the script posted by sanus|art and my emu 0404 PCI sound card works on Ubuntu login window.
But after login, I have no sounds on desktop.
Curious to say, only K3b plays sounds when I burn a CD.

Does anyone know how to fix it?

---

### Post by sanus|art on 2008-06-21
> **ernix said:**
> I'm using ubuntustudio 8.04.
I tried to install alsa with the script posted by sanus|art and my emu 0404 PCI sound card works on Ubuntu login window.
But after login, I have no sounds on desktop.
Curious to say, only K3b plays sounds when I burn a CD.

Does anyone know how to fix it?
Hi, apparently, I had a syntax error in the URL of alsa-driver - so while you ran the script - the old driver actualy was used.

I now fixed the script and the mirrors (the old mirrors are dead now).

Sorry for that.  

P.S.
There are also alsa-*-1.0.17rc2 versions - but I did not tried them out yet.

---

### Post by ernix on 2008-06-21
> **sanus|art said:**
> Hi, apparently, I had a syntax error in the URL of alsa-driver - so while you ran the script - the old driver actualy was used.

I now fixed the script and the mirrors (the old mirrors are dead now).

Sorry for that.  

P.S.
There are also alsa-*-1.0.17rc2 versions - but I did not tried them out yet.

Thank you for your kindness. :-)
But I still have same issue after I tried your new script.
would you tell me how to check versions of my alsa driver, lib, util, firmware?

It's least some applications can play sounds, so I think this issue is caused by alsa driver itself and all I have to do is try development version.

---

### Post by sanus|art on 2008-06-21
To check alsa version:
```
cat /proc/asound/version
```

However I have the same issue with Ubuntu studio right now. It was working fine for me in Ubuntu. I have sound for several application - but not all, weird ! 
Maybe it is something to do with the real-time kernel.

I am trying to figure it out now too, I am not a big expert on the matter so if you find something let me know.

---

### Post by sanus|art on 2008-06-21
Ok, I've got sound on ubuntu studio. This is no way a good solution - but it worked for me.

Steps:


[LIST]
[*]Unload alsa:
[/LIST]
```
sudo /sbin/alsa unload
```
[LIST]
[*]Run the script
[/LIST]

Reboot.


[LIST]
[*]List cards:
[/LIST]
```
asoundconf list
```
[LIST]
[*]Set default card (from the the command above I've got "EMU0404"):
[/LIST]
```
asoundconf set-default-card EMU0404
```
[LIST]
[*]Set system link for /usr/share
[/LIST]
```
sudo ln -s /usr/local/share/alsa/firmware /usr/share/alsa
```Reboot.

Hope it helps.

---

### Post by ernix on 2008-06-21
It still doesn't work for me.:(

When I unloaded alsa, my terminal warned me some processes was using alsa.
Must I kill these processes before unloading?

---

### Post by sanus|art on 2008-06-21
try to stop them with
```
sudo /etc/init.d/alsa-utils stop <card_name_here>
```

---

### Post by sanus|art on 2008-06-22
Ok, this script supposed to work fine, tested 3 times (don't) forget to unmute the mixer at:

```
gnome-volume-control
```Here is the script:
[ATTACH]74918[/ATTACH]

[[COLOR=Red]*[/COLOR]] - Rename to 'E-MU.sh'
[[COLOR=Red]*[/COLOR]] - set permitions to execute 'sudo chmod 777 /path/to/script/E-MU.sh'
[[COLOR=Red]*[/COLOR]] - Run it as super user 'sudo sh /path/to/script/E-MU.sh'

---

### Post by ernix on 2008-06-28
Yeah!  I tried the script with development versions of alsa and Amarok played back perfectly!:)
Thanks, sanus|art!

---

### Post by sanus|art on 2008-06-28
> **ernix said:**
> yeah!  I Tried The Script With Development Versions Of Alsa And Amarok Played Back Perfectly!:)
Thanks, Sanus|art!
Great!

---

### Post by darkblane on 2008-07-04
Hi sanus|art,

I tried running E-MU.sh and ran into a few problems. The script completed without error but as it finished and I was instructed to reboot my system would freeze completely. The only way I could restart was to reset power. On reboot my system would fail to boot, it just hang on the Ununtu loading screen and stayed there. Un-deterred I tried again, reinstalling Ubuntu, doing all updates and once again ran the script, same happened.
I then decided to retry using the i386 disc rather than amd64 to see if that made any difference so I reinstalled again and the same thing has happened. I've reinstalled 7 times now and in the process 2 sata drives have started failing from having to hard reset the system. I'm down to my last spare drive so would appreciate some advice on what might be causing this. I'm desperate to use my emu0404 :(

My last attempt at running E-MU.sh caused the obligatory system crash but I decided to write down the error on reboot to see if it might mean something to you;

```
loading, please wait...
kinit: name_to_dev_t(/dev/disk/by-uuid/aeee45a59-f91a-4ddd-97f1-076b0865b6bf) = hdb5(3,69)
kinit: trying to resume from /dev/disk/by-uuid/aeee45a59-f91a-4ddd-97f1-076b0865b6bf
kinit: No resume image, doing normal boot...
[   56.186379] aliasx3_smdus 0000:00:1e.1: ALI5x3_smb region uninitialized - upgrade BIOS or use force_addr=0xaddr
[   56.186379] aliasx3_smdus 0000:00:1e.1: ALI5x3 not detected, module not inserted.
_

```

At this point the keyboard is completely unresponsive and the only method of resetting the system is by using the case button.

It may be worth noting that on 1 of my many attempts I edited the script, basically splitting it in two so that everything prior to the insertion of the module into the kernel was in emu1.sh and the rest in emu2.sh. When using this method the script ran fine, no problems until I ran the 2nd portion, inserting the module and straight away the system hung.

Do you have any ideas? My system works flawlessly in XP, Vista with the Emu card. It works perfectly in Ubuntu with the onboard sound enabled and doesn't hang when compiling anything else, it just seems the moment the emu10k1 module is passed into the kernel everything dies!

---

### Post by darkblane on 2008-07-04
Ok, I've solved the boot problems and I think I've got to the bottom of why the emu0404 isn't working.
I enabled boot logging to find out what was going wrong and found this;

```
[   45.231123] ACPI: PCI Interrupt Link [LNKG] enabled at IRQ 11
[   45.231127] ACPI: PCI Interrupt 0000:00:1d.0[C] -> Link [LNKG] -> GSI 11 (level, low) -> IRQ 11
[   45.231242] ALSA /usr/src/modules/alsa-driver/pci/hda/../../alsa-kernel/pci/hda/hda_intel.c:1838: chipset global capabilities = 0x6501
[   45.261987] ALSA /usr/src/modules/alsa-driver/pci/hda/../../alsa-kernel/pci/hda/hda_intel.c:739: codec_mask = 0x1
[   45.264067] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:2346: hda_codec: model 'laptop' is selected for config 1043:818f (ASUS P5)
[   45.591264] ACPI: PCI Interrupt 0000:02:12.0[A] -> Link [LNKD] -> GSI 3 (level, low) -> IRQ 3
[   45.591278] ALSA /usr/src/modules/alsa-driver/pci/emu10k1/emu10k1_main.c:1760: vendor=0x1102, device=0x8, subsystem_vendor_id=0x40021102, subsystem_id=0x4002
[   45.591282] ALSA /usr/src/modules/alsa-driver/pci/emu10k1/emu10k1_main.c:1785: Sound card name=E-mu 0404b [4002]
[   45.591383] ALSA /usr/src/modules/alsa-driver/pci/emu10k1/emu10k1_main.c:822: emu1010: Special config.
[   45.591450] ALSA /usr/src/modules/alsa-driver/pci/emu10k1/emu10k1_main.c:847: reg1=0x3f
[   45.591475] ALSA /usr/src/modules/alsa-driver/pci/emu10k1/emu10k1_main.c:855: reg2=0x3f
[   45.591477] ALSA /usr/src/modules/alsa-driver/pci/emu10k1/emu10k1_main.c:861: emu1010: EMU_HANA_ID=0x3f
[   45.591479] ALSA /usr/src/modules/alsa-driver/pci/emu10k1/emu10k1_main.c:880: emu1010: filename emu/emu0404.fw testing
[   45.644281] ALSA /usr/src/modules/alsa-driver/pci/emu10k1/emu10k1_main.c:681: firmware: emu/emu0404.fw not found. Err=-2
[   45.644392] ALSA /usr/src/modules/alsa-driver/pci/emu10k1/emu10k1_main.c:885: emu1010: Loading Firmware file emu/emu0404.fw failed
[   45.645284] ACPI: PCI interrupt for device 0000:02:12.0 disabled
[   45.645301] EMU10K1_Audigy: probe of 0000:02:12.0 failed with error -2
```

It appears there is no firmware for my card. Should this come with the asla source?
I compiled the latest asla source using;

1.```
sudo apt-get install build-essential linux-headers-$(uname -r) module-assistant alsa-source
```
2.```
sudo dpkg-reconfigure alsa-source
```
3.```
sudo module-assistant a-i   alsa-source
```

Then I ran
```
sudo nano /etc/modules
```
And added the entry for at the bottom of the file
```
snd-emu10k1
```

Any ideas on why this error is appearing?
```
[   45.644281] ALSA /usr/src/modules/alsa-driver/pci/emu10k1/emu10k1_main.c:681: firmware: emu/emu0404.fw not found. Err=-2
[   45.644392] ALSA /usr/src/modules/alsa-driver/pci/emu10k1/emu10k1_main.c:885: emu1010: Loading Firmware file emu/emu0404.fw failed
[   45.645284] ACPI: PCI interrupt for device 0000:02:12.0 disabled
[   45.645301] EMU10K1_Audigy: probe of 0000:02:12.0 failed with error -2
```

Any help would be greatly appreciated :)

---

### Post by sanus|art on 2008-07-05
@darkblane
Is your 0404 is PCI or USB ?
And is it detected by Windows (if you have any)?
As far as I see - the alsa should not run while recompiling/reinstalling.

I'm not much of an expert here at all, just found this tread and posted my way of alsa compiling so don't expect much.
Anyway I'll try to help as much as I can, bumping this tread might get someones attention too.

---

### Post by darkblane on 2008-07-06
> **sanus|art said:**
> @darkblane
Is your 0404 is PCI or USB ?
And is it detected by Windows (if you have any)?

My card is an e-mu0404 PCI.
It works flawlessly in XP & Vista.
It appears it is being disabled on startup.

```
[   45.591479] ALSA /usr/src/modules/alsa-driver/pci/emu10k1/emu10k1_main.c:880: emu1010: filename emu/emu0404.fw testing
[   45.644281] ALSA /usr/src/modules/alsa-driver/pci/emu10k1/emu10k1_main.c:681: firmware: emu/emu0404.fw not found. Err=-2
[   45.644392] ALSA /usr/src/modules/alsa-driver/pci/emu10k1/emu10k1_main.c:885: emu1010: Loading Firmware file emu/emu0404.fw failed
[   45.645284] ACPI: PCI interrupt for device 0000:02:12.0 disabled
[   45.645301] EMU10K1_Audigy: probe of 0000:02:12.0 failed with error -2

```

Going to post here, [https://bugtrack.alsa-project.org/wiki/wikka.php?wakka=emu&show_comments=1#comments](https://bugtrack.alsa-project.org/wiki/wikka.php?wakka=emu&show_comments=1#comments) , and see if I get any joy. Thanks for replying :)

---

### Post by darkblane on 2008-07-06
Ok, I tired compiling the alsa firmware to see if it helped;

$ wget [ftp://ftp.alsa-project.org/pub/firmware/alsa-firmware-1.0.16.tar.bz2](ftp://ftp.alsa-project.org/pub/firmware/alsa-firmware-1.0.16.tar.bz2)
$ tar -jxvf alsa-firmware-1.0.16.tar.bz2
$ cd alsa-firmware-1.0.16
$ ./configure
$ sudo make install

Then rebooted.
The previous message has gone, instead I get this error;
```
darkblane@darkblane-desktop:~$ sudo dmesg | grep EMU
[   48.455510] EMU10K1_Audigy: probe of 0000:02:12.0 failed with error -12

```

Any ideas??? I think this is progress, kinda :)

---

### Post by sanus|art on 2008-07-08
Do you know why is it appears as "Audigy"? Supposed to be 
EMU10K1_0404b or something like that. Is your second card is from creative too?

---

