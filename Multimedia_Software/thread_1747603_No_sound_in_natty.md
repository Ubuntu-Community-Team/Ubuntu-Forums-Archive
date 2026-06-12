---
title: "No sound in natty"
date: 2011-05-02
forum: Multimedia Software
---

### Post by carfield on 2011-05-02
After I upgrade to Natty my sound card cannot be identified and there is no sound on my system....

I am using Asus P5KR onboard sound card. It was using "snd-hda-intel" module. From ```
lspci -v
```
, I can see kernal module actually can detect the sound card. However, form ```
aplay -l
``` It say ```
aplay: device_list:221: no soundcard found...
```

I've tried to change the file  /etc/modprobe.d/alsa-base to have ```
options snd-hda-intel model=3stack
```, and reload the module. But it doesn't help....

Anything I can do to solve the problem? I've checked [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449) but still don't have hint

---

### Post by ivanxx on 2011-05-03
same problem here,

lspci correctly identifies the card as an ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)

but the corresponding module fails to register with the following messages:
```
FATAL: Error inserting snd (/lib/modules/2.6.38-8-generic/kernel/sound/acore/snd.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd
WARNING: Error inserting snd_pcm (/lib/modules/2.6.38-8-generic/kernel/sound/acore/snd-pcm.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_hwdep (/lib/modules/2.6.38-8-generic/kernel/sound/acore/snd-hwdep.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_hda_codec (/lib/modules/2.6.38-8-generic/kernel/sound/pci/hda/snd-hda-codec.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_hda_intel (/lib/modules/2.6.38-8-generic/kernel/sound/pci/hda/snd-hda-intel.ko): Unknown symbol in module, or unknown parameter (see dmesg)

```

The module was compiled and installed from the latest package available at [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=14&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false#2]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=14&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false#2"), which is dated 28th april 2011.

Any help will be extremely appreciated ):P

---

### Post by carfield on 2011-05-04
Cool, so once there is kernal update, it should be fixed, right?

---

### Post by ivanxx on 2011-05-04
Hope so!,

in the meantime, I followed the instructions given [here]("http://ubuntuforums.org/showthread.php?t=1681577") to download/compile/install the 1.0.24 version of Alsa... aaand I've got sound back!!. 

Lots of trouble though. Had to install another soundcard (old SB0040 emu10k) in order to make the system bring snd drivers to life. After booting with both cards present I've got audio in the intel-hda (optical output in this case), but no control with the sliders in alsamixer, being pulseaudio's controls the only way to handle the output volume...

Give it a try, maybe you'll get better results... :)

---

### Post by lidex on 2011-05-04
@carfield
Try resetting your pulse configuration.
Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* ~/.pulse-cookie 
sudo rm /etc/asound.conf
```
**Reboot**
* Ignore any 'No such file or directory' errors*

---

### Post by carfield on 2011-05-06
> **lidex said:**
> @carfield
Try resetting your pulse configuration.
Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* ~/.pulse-cookie 
sudo rm /etc/asound.conf
```
**Reboot**
* Ignore any 'No such file or directory' errors*
Thanks, but no, it doesn't help... btw, there is no /etc/asound.conf at my system.... do you know why?

---

### Post by carfield on 2011-05-06
> **ivanxx said:**
> same problem here,

lspci correctly identifies the card as an ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)

but the corresponding module fails to register with the following messages:
```
FATAL: Error inserting snd (/lib/modules/2.6.38-8-generic/kernel/sound/acore/snd.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd
WARNING: Error inserting snd_pcm (/lib/modules/2.6.38-8-generic/kernel/sound/acore/snd-pcm.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_hwdep (/lib/modules/2.6.38-8-generic/kernel/sound/acore/snd-hwdep.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_hda_codec (/lib/modules/2.6.38-8-generic/kernel/sound/pci/hda/snd-hda-codec.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_hda_intel (/lib/modules/2.6.38-8-generic/kernel/sound/pci/hda/snd-hda-intel.ko): Unknown symbol in module, or unknown parameter (see dmesg)

```

The module was compiled and installed from the latest package available at [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=14&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false#2]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=14&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false#2"), which is dated 28th april 2011.

Any help will be extremely appreciated ):P
Doesn't look exactly same, I can install those modules


carfield@carfield-P5KR:~$ sudo modprobe snd_hda_intel
May  7 02:25:35 carfield-P5KR kernel: [517083.893090] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
May  7 02:25:35 carfield-P5KR kernel: [517083.893090] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
May  7 02:25:35 carfield-P5KR kernel: [517083.893142] HDA Intel 0000:00:1b.0: irq 43 for MSI/MSI-X
May  7 02:25:35 carfield-P5KR kernel: [517083.893142] HDA Intel 0000:00:1b.0: irq 43 for MSI/MSI-X
May  7 02:25:35 carfield-P5KR kernel: [517083.893167] HDA Intel 0000:00:1b.0: setting latency timer to 64
May  7 02:25:35 carfield-P5KR kernel: [517083.893167] HDA Intel 0000:00:1b.0: setting latency timer to 64
May  7 02:25:35 carfield-P5KR kernel: [517083.957632] hda_codec: ALC883: BIOS auto-probing.
May  7 02:25:35 carfield-P5KR kernel: [517083.957632] hda_codec: ALC883: BIOS auto-probing.
May  7 02:25:35 carfield-P5KR kernel: [517083.967480] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input17
May  7 02:25:35 carfield-P5KR kernel: [517083.967480] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input17
carfield@carfield-P5KR:~$ lsmod|grep snd
snd_hda_codec_realtek   255820  1 
snd_hda_intel          24140  0 
snd_hda_codec          90901  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80244  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55295  9 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm

---

### Post by carfield on 2011-05-06
> **ivanxx said:**
> Hope so!,

in the meantime, I followed the instructions given [here]("http://ubuntuforums.org/showthread.php?t=1681577") to download/compile/install the 1.0.24 version of Alsa... aaand I've got sound back!!. 

Lots of trouble though. Had to install another soundcard (old SB0040 emu10k) in order to make the system bring snd drivers to life. After booting with both cards present I've got audio in the intel-hda (optical output in this case), but no control with the sliders in alsamixer, being pulseaudio's controls the only way to handle the output volume...

Give it a try, maybe you'll get better results... :)
Thanks a lot.... but it look very complicated.... hope there is new version of linux kernel soon....

---

### Post by lidex on 2011-05-06
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by carfield on 2011-05-06
> **lidex said:**
> Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]
Thanks a lot, here is the detail 

[http://www.alsa-project.org/db/?f=08fb0ea5526f29525bd98a7c94a368d388b180e1](http://www.alsa-project.org/db/?f=08fb0ea5526f29525bd98a7c94a368d388b180e1)

---

### Post by lidex on 2011-05-06
You have some serious issues apart from audio:
```
[ 1679.291297] Xorg[1670]: segfault at 8a17720 ip 08a17720 sp bff59cdc error 15
--
[ 4140.347839] CPU0: Core temperature above threshold, cpu clock throttled (total events = 1)
```
Also, what is this:
```
Elite Silicon USB Audio Device]
```

Try re-installing alsa. 
Using a Terminal="Applications->Accessories->Terminal"
```
sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2
```
**Reboot.**

For a 'command not found' error simply install aptitude:
```
sudo apt-get install aptitude
```

---

### Post by carfield on 2011-05-07
Thanks a lot, here is the result after running aptitude command:

[http://www.alsa-project.org/db/?f=88fd06ae669c130ef132355e332f2e4b3e261ee3](http://www.alsa-project.org/db/?f=88fd06ae669c130ef132355e332f2e4b3e261ee3)

About [Elite Silicon USB Audio Device], it is the speaker that get power from USB

---

### Post by Occi on 2011-05-07
> **ivanxx said:**
> same problem here,

lspci correctly identifies the card as an ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)

but the corresponding module fails to register with the following messages:
```
FATAL: Error inserting snd (/lib/modules/2.6.38-8-generic/kernel/sound/acore/snd.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd
WARNING: Error inserting snd_pcm (/lib/modules/2.6.38-8-generic/kernel/sound/acore/snd-pcm.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_hwdep (/lib/modules/2.6.38-8-generic/kernel/sound/acore/snd-hwdep.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_hda_codec (/lib/modules/2.6.38-8-generic/kernel/sound/pci/hda/snd-hda-codec.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_hda_intel (/lib/modules/2.6.38-8-generic/kernel/sound/pci/hda/snd-hda-intel.ko): Unknown symbol in module, or unknown parameter (see dmesg)

```The module was compiled and installed from the latest package available at [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=14&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false#2](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=14&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false#2), which is dated 28th april 2011.

Any help will be extremely appreciated ):P
I too get an error message like this (and lspci says I don't have any soundcard). The exact message I get after doing [FONT=Courier New]sudo modprobe snd-hda-intel ; sudo modprobe snd-pcm-oss ; sudo modprobe snd-mixer-oss ; sudo modprobe snd-seq-oss[/FONT] [FONT=Verdana]is:
[/FONT]```
FATAL: Error inserting snd (/lib/modules/2.6.38-8-generic/kernel/sound/acore/snd.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd
WARNING: Error inserting snd_pcm (/lib/modules/2.6.38-8-generic/kernel/sound/acore/snd-pcm.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_hwdep (/lib/modules/2.6.38-8-generic/kernel/sound/acore/snd-hwdep.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_hda_codec (/lib/modules/2.6.38-8-generic/kernel/sound/pci/hda/snd-hda-codec.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_hda_intel (/lib/modules/2.6.38-8-generic/kernel/sound/pci/hda/snd-hda-intel.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd (/lib/modules/2.6.38-8-generic/kernel/sound/acore/snd.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd
WARNING: Error inserting snd_page_alloc (/lib/modules/2.6.38-8-generic/kernel/sound/acore/snd-page-alloc.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_timer (/lib/modules/2.6.38-8-generic/kernel/sound/acore/snd-timer.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_pcm (/lib/modules/2.6.38-8-generic/kernel/sound/acore/snd-pcm.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_pcm_oss (/lib/modules/2.6.38-8-generic/kernel/sound/acore/oss/snd-pcm-oss.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd (/lib/modules/2.6.38-8-generic/kernel/sound/acore/snd.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd
FATAL: Error inserting snd_mixer_oss (/lib/modules/2.6.38-8-generic/kernel/sound/acore/oss/snd-mixer-oss.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd (/lib/modules/2.6.38-8-generic/kernel/sound/acore/snd.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd
WARNING: Error inserting snd_timer (/lib/modules/2.6.38-8-generic/kernel/sound/acore/snd-timer.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_seq (/lib/modules/2.6.38-8-generic/kernel/sound/acore/seq/snd-seq.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_seq_midi_event (/lib/modules/2.6.38-8-generic/kernel/sound/acore/seq/snd-seq-midi-event.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_seq_oss (/lib/modules/2.6.38-8-generic/kernel/sound/acore/seq/oss/snd-seq-oss.ko): Unknown symbol in module, or unknown parameter (see dmesg)
```The guide I'm following is [this]("http://www.alsa-project.org/main/index.php/Matrix:Module-hda-intel").

I can't find anything else than this thread on google, seems like the newest kernel og ubuntu release screwed something up :confused: I installed my Ubuntu just before 11.04 was launched, so I can't say exactly, but I think the driver was working as intended before I upgraded, but I just didn't use it. 

Suggestions on what to do next is appriciated!

---

### Post by lidex on 2011-05-08
@carfield 
Your usb device is showing up now. Try switching to it in 'Sound Preferences'

---

### Post by carfield on 2011-05-09
> **lidex said:**
> @carfield 
Your usb device is showing up now. Try switching to it in 'Sound Preferences'
I am using xfce but not gnome, there is no "sound preference" which package I should install in order to use that?

---

### Post by Yellow Pasque on 2011-05-09
Since your sound is already messed up, try the alsa "upgrade" script in lidex's sig. It won't really uprade, but it should build a loadable kernel module.

---

### Post by 4Orbs on 2011-05-09
This is what I had to do to get sound working on Xubuntu Natty. The xfce mixer has only one option to select the audio device, but the gnome mixer provides two options, so you can choose to disable the device not being used... and that is what made the sound work.

So to get the gnome mixer and its dependencies:
```
sudo apt-get install gnome-media
```
after installing and reboot, you'll have two volume applets on the xfce panel. You can remove one of those by going to menu, Settings Mgr, Sessions and Startup, Applications Startup, and uncheck the Volume Control on Desktop option.

Don't know if this really is related to your problem. Hope so.

---

### Post by carfield on 2011-05-11
> **Temüjin said:**
> Since your sound is already messed up, try the alsa "upgrade" script in lidex's sig. It won't really uprade, but it should build a loadable kernel module.
Just try but when I run: "sudo ./AlsaUpgrade-1.0.23-2.sh -c", I get following error 

> /usr/src/Alsa-1.0.23/alsa-driver-1.0.23/include/config1.h:175:0: warning: "CONFIG_SND_HDA_INPUT_BEEP_MODE" redefined
./include/generated/autoconf.h:2390:0: note: this is the location of the previous definition
/usr/src/Alsa-1.0.23/alsa-driver-1.0.23/acore/pcm_native.c: In function &#8216;snd_pcm_hw_params&#8217;:
/usr/src/Alsa-1.0.23/alsa-driver-1.0.23/acore/pcm_native.c:489:2: error: implicit declaration of function &#8216;pm_qos_remove_requirement&#8217;
/usr/src/Alsa-1.0.23/alsa-driver-1.0.23/acore/pcm_native.c:492:3: error: implicit declaration of function &#8216;pm_qos_add_requirement&#8217;
make[3]: *** [/usr/src/Alsa-1.0.23/alsa-driver-1.0.23/acore/pcm_native.o] Error 1
make[2]: *** [/usr/src/Alsa-1.0.23/alsa-driver-1.0.23/acore] Error 2
make[1]: *** [_module_/usr/src/Alsa-1.0.23/alsa-driver-1.0.23] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.38-8-generic-pae'
make: *** [compile] Error 2


---

### Post by carfield on 2011-05-11
> **4Orbs said:**
> This is what I had to do to get sound working on Xubuntu Natty. The xfce mixer has only one option to select the audio device, but the gnome mixer provides two options, so you can choose to disable the device not being used... and that is what made the sound work.

So to get the gnome mixer and its dependencies:
```
sudo apt-get install gnome-media
```
after installing and reboot, you'll have two volume applets on the xfce panel. You can remove one of those by going to menu, Settings Mgr, Sessions and Startup, Applications Startup, and uncheck the Volume Control on Desktop option.

Don't know if this really is related to your problem. Hope so.
thanks, I tried this also... but even after I switch to USB sound device, there is no sound, I think the speak really just use USB as power source, notthing more.

---

### Post by 4Orbs on 2011-05-11
I didn't make one thing clear in my other post. In order to make my chosen device work, it was necessary to turn the other device off. To do this, select the device you are not using and in the dropdown menu below it select the option "Off".

Two years ago I was using some USB speakers (Logitech) and they did use the USB for power, but they also had their own soundcard built into the speakers. They were very cheap and sounded terrible.

---

### Post by carfield on 2011-05-15
Thanks for update, but after I try alsa update script, my sound device are totally broken and I can see any device at gnome-sound-preference any more....

Hope next kernel update will solve my problem....

---

### Post by lidex on 2011-05-15
> **carfield said:**
> Thanks for update, but after I try alsa update script, my sound device are totally broken and I can see any device at gnome-sound-preference any more....

Hope next kernel update will solve my problem....
There may be an issue with that pae kernel. Try booting into the non-pae kernel.

---

### Post by carfield on 2011-05-16
> **lidex said:**
> There may be an issue with that pae kernel. Try booting into the non-pae kernel.
Thanks a lot for suggestion, really, but non-pae also have problem ....

---

### Post by carfield on 2011-05-29
Waited for a long time and there is still no Kernel update.... will anyone have more idea about this issue?

---

### Post by carfield on 2011-06-17
Waited for so long and there is still no kernal update.... any suggestion? I even buy a new sound card with creative chip, but it still doesn't work....

---

### Post by Yellow Pasque on 2011-06-17
Well, I just noticed you're trying to build 1.0.23. Get the latest version of the script and make sure you run that: [http://ubuntuforums.org/showthread.php?t=1681577](http://ubuntuforums.org/showthread.php?t=1681577)

---

### Post by carfield on 2011-06-18
Thanks a lot for replying, in fact I tried that before and I try that again, it helped to update the driver but aplay still say no sound card find.... will you have any idea?

[http://www.alsa-project.org/db/?f=fcfa1897dc0c55e4e67ac5f2c291781dd267f7ca](http://www.alsa-project.org/db/?f=fcfa1897dc0c55e4e67ac5f2c291781dd267f7ca)

And I found one strangle thing, if I run "also-info.sh" without xserver started, APLAY can detect there is sound card: [http://www.carfield.com.hk/alsa-info.txt](http://www.carfield.com.hk/alsa-info.txt)

But after I startx, APLAY say no soundcard....

[http://www.alsa-project.org/db/?f=fcfa1897dc0c55e4e67ac5f2c291781dd267f7ca](http://www.alsa-project.org/db/?f=fcfa1897dc0c55e4e67ac5f2c291781dd267f7ca)

Any xconfig will affect aplay??

---

### Post by Je Et on 2011-06-18
I got an older computer with AMD Athlon(tm) XP2600+ processer, don't know what that is, that had XP on it. Well, right away the first thing I did was to install Ubuntu 11.04 on it and there was no sound. There was a dummy out-put in sound preferences and I tried everything and read all the 'no sound' posts here, but to no avail. Then I was doing something in BIOS and something caught my eye. THE AUDIO WAS TURNED OFF!  I turned the audio on and BAMM... sound. Check it out, it may solve your problem.

---

### Post by lidex on 2011-06-18
> **carfield said:**
> Thanks a lot for replying, in fact I tried that before and I try that again, it helped to update the driver but aplay still say no sound card find.... will you have any idea?

[http://www.alsa-project.org/db/?f=fcfa1897dc0c55e4e67ac5f2c291781dd267f7ca](http://www.alsa-project.org/db/?f=fcfa1897dc0c55e4e67ac5f2c291781dd267f7ca)

And I found one strangle thing, if I run "also-info.sh" without xserver started, APLAY can detect there is sound card: [http://www.carfield.com.hk/alsa-info.txt](http://www.carfield.com.hk/alsa-info.txt)

But after I startx, APLAY say no soundcard....

[http://www.alsa-project.org/db/?f=fcfa1897dc0c55e4e67ac5f2c291781dd267f7ca](http://www.alsa-project.org/db/?f=fcfa1897dc0c55e4e67ac5f2c291781dd267f7ca)

Any xconfig will affect aplay??

Your alsa update was successful and your onboard sound is being recognized by alsa in both of those outputs. What is not being detected in the first one is a usb device. 
Also the model quirk you selected for snd-hda-intel is incorrect.

What are these outputs:
```
sudo dmidecode -t bios
sudo dmidecode -t baseboard

```

EDIT:
The snd-usb-audio module is being loaded in both instances, but with x running it
gets deactivated for some reason:
```
[  604.936871] usbcore: deregistering interface driver snd-usb-audio
```

---

### Post by carfield on 2011-06-18
Thanks for remind, but that one is turned on

---

### Post by carfield on 2011-06-18
Thanks a lot, Here are the output of the dmi commands:


carfield@carfield-P5KR:~$ sudo dmidecode -t bios
[sudo] password for carfield: 
# dmidecode 2.9
SMBIOS 2.4 present.

Handle 0x0000, DMI type 0, 24 bytes
BIOS Information
	Vendor: American Megatrends Inc.
	Version: 0605   
	Release Date: 03/05/2008
	Address: 0xF0000
	Runtime Size: 64 kB
	ROM Size: 1024 kB
	Characteristics:
		ISA is supported
		PCI is supported
		PNP is supported
		APM is supported
		BIOS is upgradeable
		BIOS shadowing is allowed
		ESCD support is available
		Boot from CD is supported
		Selectable boot is supported
		BIOS ROM is socketed
		EDD is supported
		5.25"/1.2 MB floppy services are supported (int 13h)
		3.5"/720 KB floppy services are supported (int 13h)
		3.5"/2.88 MB floppy services are supported (int 13h)
		Print screen service is supported (int 5h)
		8042 keyboard services are supported (int 9h)
		Serial services are supported (int 14h)
		Printer services are supported (int 17h)
		CGA/mono video services are supported (int 10h)
		ACPI is supported
		USB legacy is supported
		LS-120 boot is supported
		ATAPI Zip drive boot is supported
		BIOS boot specification is supported
		Targeted content distribution is supported
	BIOS Revision: 8.12

Handle 0x0038, DMI type 13, 22 bytes
BIOS Language Information
	Installable Languages: 1
		en|US|iso8859-1
	Currently Installed Language: en|US|iso8859-1

carfield@carfield-P5KR:~$ sudo dmidecode -t baseboard
# dmidecode 2.9
SMBIOS 2.4 present.

Handle 0x0002, DMI type 2, 15 bytes
Base Board Information
	Manufacturer: ASUSTeK Computer INC.
	Product Name: P5KR
	Version: Rev 1.xx
	Serial Number: MS6C78B11600170
	Asset Tag: To Be Filled By O.E.M.
	Features:
		Board is a hosting board
		Board is replaceable
	Location In Chassis: To Be Filled By O.E.M.
	Chassis Handle: 0x0003
	Type: Motherboard
	Contained Object Handles: 0

Handle 0x0035, DMI type 10, 6 bytes
On Board Device Information
	Type: Ethernet
	Status: Enabled
	Description:  Onboard Ethernet

carfield@carfield-P5KR:~$

---

### Post by lidex on 2011-06-18
OK I missed the part about aplay not seeing the card, I saw that alsa recognized it and assumed it was ok. I have not seen that before, very odd. The model name you have selected in alsa-base.conf is incorrect, so remove it. Then re-install alsa:
Using a Terminal="Applications->Accessories->Terminal"
```
sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2
```
**Reboot.**

For a 'command not found' error simply install aptitude:
```
sudo apt-get install aptitude
```

No joy? Update your bios.

---

### Post by carfield on 2011-06-19
Thanks, but I tried to run "sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2" to reinstall packages for few times but all doesn't help :-(

How to update bios is another question, but if that really related? Because if I exit to console , my system can detect the sound card, ( I don't use xdm so I can do that ). But after I run startx to start x windows, aplay cannot detect sound card anymore....

---

### Post by Je Et on 2011-06-19
> How to update bios is another question, but if that really related?  Because if I exit to console , my system can detect the sound card, ( I  don't use xdm so I can do that ). But after I run startx to start x  windows, aplay cannot detect sound card anymore....


Google <your computer> support. example(Dell support) then go to drivers download section, then BIOS. The file is usually a DOS file, but follow the instructions for your machine.

Je Et

---

### Post by carfield on 2011-06-20
> **Je Et said:**
> Google <your computer> support. example(Dell support) then go to drivers download section, then BIOS. The file is usually a DOS file, but follow the instructions for your machine.

Je Et

I've googled and try out method mentioned in this link before posting that reply:

[http://vip.asus.com/forum/view.aspx?id=20070215223109668&board_id=1&model=P5B+Deluxe](http://vip.asus.com/forum/view.aspx?id=20070215223109668&board_id=1&model=P5B+Deluxe)

However that doesn't work. 

BTW, I don't really feel this is BIOS issue, because before my update, it work fine; and before I start XWin, it can also detect the sound card. It look like something about my XWindows setting.

I am using xfce4.

---

### Post by Yellow Pasque on 2011-06-20
This is the first time I've heard of that (X/aplay conflict). I would try modprobing the snd-hda-intel module after X starts, and then looking at dmesg. I looked at available BIOS updates and none mention audio fixes, only CPU support updates.

---

### Post by carfield on 2011-06-21
Thanks a lot, I first "rmmod snd-hda-intel", then I see this message:

[174634.996196] HDA Intel 0000:00:1b.0: PCI INT A disabled

Then I run "modprobe snd-hda-intel", then I see this message:

[174672.813680] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[174672.813749] HDA Intel 0000:00:1b.0: irq 43 for MSI/MSI-X
[174672.813779] HDA Intel 0000:00:1b.0: setting latency timer to 64
[174672.847636] hda_codec: ALC883: BIOS auto-probing.
[174672.848969] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input7
[174672.852558] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8


Will you have any hint?

---

### Post by lidex on 2011-06-25
> **carfield said:**
> Thanks a lot, I first "rmmod snd-hda-intel", then I see this message:

[174634.996196] HDA Intel 0000:00:1b.0: PCI INT A disabled

Then I run "modprobe snd-hda-intel", then I see this message:

[174672.813680] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[174672.813749] HDA Intel 0000:00:1b.0: irq 43 for MSI/MSI-X
[174672.813779] HDA Intel 0000:00:1b.0: setting latency timer to 64
[174672.847636] [COLOR="Red"]hda_codec: ALC883: BIOS auto-probing[/COLOR].
[174672.848969] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input7
[174672.852558] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8


Will you have any hint?

Did you remove the modification from alsa-base.conf? Your model selection- 3stack- is wrong. Reboot after.

---

### Post by Veritas_08 on 2011-06-26
Same issue here. No sound trough an intel_hda card. It shows up on the diagnostics but no sound comes through. Ran all the diagnostics, alsamixer, pavucontrol, purged and reinstalled sound programs. Just a lot of silence.

I haven't given up yet. Glad to see I'm not the only having trouble with this. 

I'm just kinda test driving Ubuntu. I'm not buying a new sound card just to have sound. Guess we all might just wait for the next iteration and see if this is fixed. 
 
Shame though as I like everything else in Natty :( Will keep pecking at this during free time and see what happens. Best of luck to all :)

---

### Post by lidex on 2011-06-26
> **Veritas_08 said:**
> Same issue here. No sound trough an intel_hda card. It shows up on the diagnostics but no sound comes through. Ran all the diagnostics, alsamixer, pavucontrol, purged and reinstalled sound programs. Just a lot of silence.

I haven't given up yet. Glad to see I'm not the only having trouble with this. 

I'm just kinda test driving Ubuntu. I'm not buying a new sound card just to have sound. Guess we all might just wait for the next iteration and see if this is fixed. 
 
Shame though as I like everything else in Natty :( Will keep pecking at this during free time and see what happens. Best of luck to all :)
I'm a gamer. These megathreads are too hard to follow. If you wouldn't mind starting a new thread I would be happy to address your problem.

---

### Post by DunZH on 2011-06-26
[B]Veritas_08, if you were looking for support, pls start a new thread.  Jumping in on someone's thread isn't a good way (not that you were trying to do that, just FYI).

And, welcome to the other side!  Some things are tougher but some aspects are much better :-)

I just bought a rig for Linux, and found this thread because after compiling and installing the HD drivers from Realtek, my system no longer recognizes my Intel HDA hardware :-(

And no, I am not looking for support here !  :P

Carfield, thanks for putting all the commands right there.  This is a good thread.

The hardware is there, and can be found and installed.  I am sure of it, I wrestled with an azalia soundcard once before, and here I am!  So it can be done.

:lolflag:
[/B]

---

### Post by carfield on 2011-06-27
Hi all, finally get the solution, it is because the user I login is not under group "audio" . After I added this group to my login, I can listen to music again. Thanks all for the support!

BTW, just wonder, if there some kind of document or FAQ about that? I choose "keep existing setting" option when upgrade, it is very likely the root cause of this problem. But sound like I am only one encounter this?

---

### Post by Veritas_08 on 2011-06-28
I certainly wasn't trying to jump in the thread :(

And I did post my problem. And I got it solved :)

I am as of now using only Ubuntu. Yes, this side is much better!

---

