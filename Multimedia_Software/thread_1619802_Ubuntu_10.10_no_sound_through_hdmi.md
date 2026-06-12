---
title: "Ubuntu 10.10 no sound through hdmi"
date: 2010-11-12
forum: Multimedia Software
---

### Post by prasadrvln on 2010-11-12
Hi!

I have recently installed Ubuntu 10.10. Everything is working fine except I have no sound.  
When I use the command 'aplay -D hw:0,0 somefile.wav', I can get sound through headphones attached to the headphone jack.  But I can't get any sound through the speakers.  This is a dual boot desktop and the sound works fine under Windows, so no problems with hardware.  

The PC monitor is connected through a hdmi cable and I would need sound through the speakers.  Please could somebody help me.

The output of alsa-info.sh is at 
[HTML]<a href="http://www.alsa-project.org/db/?f=cb172534097c313b25836f77f2a40fef857102ba">alsa-info.sh output file.</a>[/HTML]

Please let me know if you need further information.

Thanks a lot in advance
Prasad

---

### Post by dartmusic on 2010-11-12
Can you post the output of aplay -l and aplay -L?

Also, are all channels unmuted when you check alsamixer?

---

### Post by prasadrvln on 2010-11-13
Thanks for the response.  And my apologies.  I didn't include the results of aplay because I thought the same is in the file I attached with my earlier.  Here it is.

_aplay -l_
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: ALC1200 Digital [ALC1200 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

_aplay -L_
default
pulse
    Playback/recording through the PulseAudio sound server
front:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Analog
    Front speakers
surround40:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
hdmi:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Digital
    HDMI Audio Output
dmix:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Analog
    Direct sample mixing device
dmix:CARD=NVidia,DEV=3
    HDA NVidia, ALC1200 Digital
    Direct sample mixing device
dsnoop:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Analog
    Direct sample snooping device
dsnoop:CARD=NVidia,DEV=3
    HDA NVidia, ALC1200 Digital
    Direct sample snooping device
hw:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Analog
    Direct hardware device without any conversions
hw:CARD=NVidia,DEV=3
    HDA NVidia, ALC1200 Digital
    Direct hardware device without any conversions
plughw:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Analog
    Hardware device with all software conversions
plughw:CARD=NVidia,DEV=3
    HDA NVidia, ALC1200 Digital
    Hardware device with all software conversions

All channels are unmuted.

---

### Post by prasadrvln on 2010-11-15
Someone please help.
 
Thanks
Prasad.

---

### Post by dartmusic on 2010-11-16
> **prasadrvln said:**
> Thanks for the response.  And my apologies.  I didn't include the results of aplay because I thought the same is in the file I attached with my earlier.  Here it is.

_aplay -l_
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: ALC1200 Digital [ALC1200 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

_aplay -L_
default
pulse
    Playback/recording through the PulseAudio sound server
front:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Analog
    Front speakers
surround40:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
hdmi:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Digital
    HDMI Audio Output
dmix:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Analog
    Direct sample mixing device
dmix:CARD=NVidia,DEV=3
    HDA NVidia, ALC1200 Digital
    Direct sample mixing device
dsnoop:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Analog
    Direct sample snooping device
dsnoop:CARD=NVidia,DEV=3
    HDA NVidia, ALC1200 Digital
    Direct sample snooping device
hw:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Analog
    Direct hardware device without any conversions
hw:CARD=NVidia,DEV=3
    HDA NVidia, ALC1200 Digital
    Direct hardware device without any conversions
plughw:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Analog
    Hardware device with all software conversions
plughw:CARD=NVidia,DEV=3
    HDA NVidia, ALC1200 Digital
    Hardware device with all software conversions

All channels are unmuted.

This listing looks to be your onboard audio, nothing via HDMI.

---

### Post by prasadrvln on 2010-11-16
Thanks for the response.  Under _aplay -L_ please see the following lines.
 
hdmi:CARD=NVidia,DEV=0
HDA NVidia, ALC1200 Digital
HDMI Audio Output

Also, when I click on the volume icon on gnome desktop and select sound preferences, I can see HDMI Digital output under the "hardware" section.
 
Regards,
Prasad.

---

### Post by prasadrvln on 2010-11-18
Come on guys.  Please help.  I am a java music programmer and need the sound.  Any help would be greatly appreciated.  Thanks a lot.
Prasad

---

### Post by dcpck on 2010-11-19
HI,

This just worked for me a few minutes ago, after a few hours of wasted reading.  I've got an Acer Revo 3610 hooked up to my Sony Bravia TV via HDMI.  I can switch between stereo on the TV and my 5.1 Bravia home theatre.  Silence no more!

[http://ubuntuforums.org/showthread.php?t=1607475](http://ubuntuforums.org/showthread.php?t=1607475)

Dave

---

### Post by theSuperman on 2010-11-19
> **dcpck said:**
> HI,

This just worked for me a few minutes ago, after a few hours of wasted reading.  I've got an Acer Revo 3610 hooked up to my Sony Bravia TV via HDMI.  I can switch between stereo on the TV and my 5.1 Bravia home theatre.  Silence no more!

[http://ubuntuforums.org/showthread.php?t=1607475](http://ubuntuforums.org/showthread.php?t=1607475)

Dave
Yeah I realized that S/PDIF 2 was muting my HDMI. It is still choppy/staticy though,  but the OP should try running alsamixer and playing with muting/unmuting.

Use arrow keys to move left and right. "m" mutes and unmutes.

---

### Post by prasadrvln on 2010-11-19
Thanks dcpck and theSuperman.  But I have done all that.  Still no sound.  Not only did I unmute everything, but over the course of 15 days I went to through may be a 1000 posts, and also tried so many things.  Still no sound.

---

### Post by prasadrvln on 2010-11-24
Hi,
 
Need help please.  
 
One thing that I have done during these days is that I used the AlsaUpgrade script from [http://ubuntuforums.org/showthread.php?p=6589810](http://ubuntuforums.org/showthread.php?p=6589810).  Could not compile in the first go.  So used the -s option in that script to download the latest snapshot version of Alsa.  It ran and now "aplay -l" says "no sound cards found".  Does anyone know how to restore it to my previous setting?  Or does anyone know when Alsa is going to release the next version of alsa-driver?
 
Been trying to get OSSv4 to produce sounds as well.  Osstest, ossinfo all show the presence of sound cards, but no sounds :mad:.  Sound comes only through headphones connected to headphone jack.
 
Really frustrated about it.  Does Alsa / pulse audio / nvidia hdmi care?  Can't understand how Windows has been able to do it for since before linux was born, and how linux hasn't been able to do it in nearly 20 years.  I think this sound issue (there are millions of posts in thousands of forums across the world regarding sound in linux) has really killed linux as an alternative to Windows.
 
Any help would be greatly appreciated.  Thanks a lot in advance.
Regards,
P.

---

### Post by efflandt on 2010-11-25
What video card do you have, which drivers are you using for it, and what does alsamixer show under HDA NVidia?  Since **aplay -l** does not show HDMI and if alsamixer shows "no controls" instead of S/PDIF devices, you may need a newer snapshot of alsa 1.0.23 from the ppa repositories.  [https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules](https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules)

For example my nvidia GT 430 is so new that Linux does not even identify its model in lspci (although, it works fine with nvidia 260.19.21 drivers).  alsamixer said something about no controls, and aplay -l did not list any HDMI NVidia.  With newer alsa snapshot **aplay -l** now shows:

```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC887 Analog [ALC887 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC887 Digital [ALC887 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 9: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```Once you get that far you have to narrow down which of those devices works on that card (1 in my case):

```
aplay -D plughw:1,3 /usr/share/sounds/alsa/Front_Center.wav
```And try 1,7 1,8 1,9 until you find one that works.  My GT 220 used 1,3, but my GT 430 uses 1,9

Look for the module-alsa-sink line in /etc/pulse/default.pa and add this line to that section for whichever card,device worked (do not begin with # or that comments it out):

```
load-module module-alsa-sink device=hw:1,9
```I ended up with an extra Output device in Sound Preferences and contrary to what appears, **HDA NVidia** works for HDMI sound and **HDA NVidia Digital Stereo (HDMI)** does not.

---

### Post by prasadrvln on 2010-11-25
Thanks for the response efflandt.  I am at the office now.  Will try it tonight and let you know how I have gone.
 
Thanks again.  Much appreciated.
Regards,
P.

---

### Post by lidex on 2010-11-27
> **prasadrvln said:**
> Thanks for the response efflandt.  I am at the office now.  Will try it tonight and let you know how I have gone.
 
Thanks again.  Much appreciated.
Regards,
P.

An excellent post from efflandt, should do the trick. One concern however is OSS. If you installed that there could very well be issues with alsa. Post your alsa-info please. Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.

---

### Post by prasadrvln on 2010-11-29
Thank you both efflandt and lidex.  And my apologies for late reply.  I had to suddenly go out of town and was not at the computer, hence could not reply.

To the point, I have done the following:

[LIST]
[*]Installed linux alsa driver modules as suggested by efflandt.  But still no  sound.  I guess I changed my system so much (in an effort to get sound, and reading so many posts on the issue) that it was not the original alsa system any more.
[*]To get my system back to the original shape, I have reinstalled the entire Ubuntu 10.10 system.  Now I have the freshly installed system with original alsa that comes with Ubuntu 10.10.
[*]The output of alsa-info.sh is at [http://www.alsa-project.org/db/?f=b02ea29db6af965fbc37723a0d6c04cda3e8afa7](http://www.alsa-project.org/db/?f=b02ea29db6af965fbc37723a0d6c04cda3e8afa7).
[*]I also include here the output of aplay -L (which doesn't get shown in alsa-info.sh output file).
[/LIST]

prasad@mainComputer:~$ aplay -L
default
pulse
    Playback/recording through the PulseAudio sound server
front:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Analog
    Front speakers
surround40:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Digital
    IEC958 (S/PDIF) Digital Audio Output
dmix:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Analog
    Direct sample mixing device
dmix:CARD=NVidia,DEV=1
    HDA NVidia, ALC1200 Digital
    Direct sample mixing device
dsnoop:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Analog
    Direct sample snooping device
dsnoop:CARD=NVidia,DEV=1
    HDA NVidia, ALC1200 Digital
    Direct sample snooping device
hw:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Analog
    Direct hardware device without any conversions
hw:CARD=NVidia,DEV=1
    HDA NVidia, ALC1200 Digital
    Direct hardware device without any conversions
plughw:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Analog
    Hardware device with all software conversions
plughw:CARD=NVidia,DEV=1
    HDA NVidia, ALC1200 Digital
    Hardware device with all software conversions


[LIST]
[*]As can be seen from the above, the output does not say there is a hdmi thingy, even though the CPU is connected to the monitor by a hdmi cable.  If it helps, my computer is HP Elite m9370a (please google for specifications of this computer).  (Secondly the system works fine under windows in this dual boot machine, so I don't think the problem is with hardware).
[*]I can hear sound through headphones connected to the CPU headphone jack, and by selecting "Analog Stereo surround" or anything analog in the "sound preferences" window.  But no sound through the monitor speakers.
[*]Previously I was with Fedora 12.  There also I had problems with sound.  But to get sound, one thing I did was to add the two following lines to the file "patch_nvhdmi.c" (under alsa-kernel/pci/hda folder of the alsa-driver, compile it and install the modules.  That way I was able to get sound.  When I tried the same with Ubuntu 10.10, the driver doesn't compile (the driver exits with errors under 2.6.35-22 kernel).  (This experiment and my effort to install a snapshot version through lidex's script was before I reinstalled the Ubuntu system yesterday). The lines I added when I was with Fedora 12 are:
[/LIST]
{ .id = 0x10de06e0, .name = "My HDMI", .patch = patch_nvhdmi },
MODULE_ALIAS("snd-hda-codec-id:10de06e0"); 			 		

After reinstalling Ubuntu, I have not yet installed the linux alsa driver modules suggested by efflandt.  Should I install that software?

I above is all the information that I can think of.  Please indicate if you need further information.  Thanks a lot again for offering to help.

Regards,
Prasad.

---

### Post by prasadrvln on 2010-11-30
Some more information.  This is what is shown in nvidia x server window for my graphic processor (as asked by efflandt).

Graphics processor:  GeForce 9300 GE
Cuda Cores: 8
VBIOS version: 62.98.29.00.13
Memory: 512 MB
Memory Interface: 64-bit

Bus type: PCI Express x16 Gen 1
Bus ID: PCI:2:0:0
PCI Device ID: 0x06e0
PCI Vender ID: 0x10de
IRQ: 16

PCI-E Max Link speed: 2500
X Screens: Screen 0

Display devices: HP 2228h (DFP-1)

[B]NVidia Driver Version: 260.19.06


[/B]

---

### Post by lidex on 2010-11-30
I believe you need this module loaded:
```
snd-hda-codec-nvhdmi
```
and it's not happening. Try this:
```
sudo modprobe snd-hda-codec-nvhdmi
```
then check aplay again.
Reference post #9 here:
[http://ubuntuforums.org/showthread.php?t=1619995](http://ubuntuforums.org/showthread.php?t=1619995)

---

### Post by IPon6MT on 2010-11-30
I too am having the same problem. No sound over HDMI on a fresh install of Ubuntu 10.10 on Jetway mini-top with Intel Atom D525 chip.

I followed these instructions and I actually heard sound when running the test against each of the listed devices.

On my machine it was device 0,7 that worked:
```
aplay -D plughw:0,7 /usr/share/sounds/alsa/Front_Center.wav
```I added the necessary line to the module-alsa-sink line in /etc/pulse/default.pa file. However, with this new configuration, the sound device is not even recognized after reboot. I can't get into the audio preferences either.

any other suggestions?

> **efflandt said:**
> What video card do you have, which drivers are you using for it, and what does alsamixer show under HDA NVidia?  Since **aplay -l** does not show HDMI and if alsamixer shows "no controls" instead of S/PDIF devices, you may need a newer snapshot of alsa 1.0.23 from the ppa repositories.  [https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules](https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules)

For example my nvidia GT 430 is so new that Linux does not even identify its model in lspci (although, it works fine with nvidia 260.19.21 drivers).  alsamixer said something about no controls, and aplay -l did not list any HDMI NVidia.  With newer alsa snapshot **aplay -l** now shows:

```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC887 Analog [ALC887 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC887 Digital [ALC887 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 9: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```Once you get that far you have to narrow down which of those devices works on that card (1 in my case):

```
aplay -D plughw:1,3 /usr/share/sounds/alsa/Front_Center.wav
```And try 1,7 1,8 1,9 until you find one that works.  My GT 220 used 1,3, but my GT 430 uses 1,9

Look for the module-alsa-sink line in /etc/pulse/default.pa and add this line to that section for whichever card,device worked (do not begin with # or that comments it out):

```
load-module module-alsa-sink device=hw:1,9
```I ended up with an extra Output device in Sound Preferences and contrary to what appears, **HDA NVidia** works for HDMI sound and **HDA NVidia Digital Stereo (HDMI)** does not.

---

### Post by prasadrvln on 2010-12-01
Hi lidex,

As advised, I have executed  the command you gave me to insert snd-hda-codec-nvhdmi module.  With lsmod I can see that the module is there, but don't know what I should expect.  Should I expect that a hdmi port will show up under 'aplay -l'?  I have run the 'aplay -l' command as well, but the output is the same as what it was before the module was inserted.  I have rebooted and checked as well (upon rebooting, the module gets deleted and I need to use your command again).  Still no luck.

Regards,
P.

---

### Post by lidex on 2010-12-02
> **prasadrvln said:**
> Hi lidex,

As advised, I have executed  the command you gave me to insert snd-hda-codec-nvhdmi module.  With lsmod I can see that the module is there, but don't know what I should expect.  Should I expect that a hdmi port will show up under 'aplay -l'?  I have run the 'aplay -l' command as well, but the output is the same as what it was before the module was inserted.  I have rebooted and checked as well (upon rebooting, the module gets deleted and I need to use your command again).  Still no luck.

Regards,
P.
Did you check out the thread I posted as a reference?

---

### Post by prasadrvln on 2010-12-02
lidex,

Yes.  I went through the entire post and post 9 in particular.  Not only that I also went through the entire post that was linked from post 1 of your link.  But pardon my ignorance, I must admit I did not understand anything in those posts other than that the posts only say either one or both of the following:

[LIST]
[*]use linux alsa driver modules
[*]use module snd-hda-codec-nvhdmi.
[/LIST]
I really don't understand whether I have missed something in those posts.

I am a bit wary of installing the linux alsa driver modules, because once I installed the latest snapshot version of alsa (using the alsa upgrade script) and ended up with 'aplay -l' saying 'no sound cards found'.  And hence had to reinstall entire ubuntu (didn't know the way back). Wouldn't like to do it unless I know that it is safe to do it, and that it can be uninstalled without trouble if it doesn't work.  Please could you tell me if it safe to install it?

Secondly, from what little I can understand from the alsa upgrade script, I can see that you automatically check for and install a lot of software such libasound, etc.  Are all of them really required for alsa to function properly?  Just asking because, after reinstalling ubuntu less than a week ago, my system is a fresh system.  I haven't installed any software other than those that came with original installation.  I am sure that a lot of software that gets installed with alsa upgrade script are presently not installed in my system.

Thanks again for helping me with my issues with sound.

Regards,
P.

---

### Post by lidex on 2010-12-02
> **prasadrvln said:**
> lidex,

Yes.  I went through the entire post and post 9 in particular.  Not only that I also went through the entire post that was linked from post 1 of your link.  But pardon my ignorance, I must admit I did not understand anything in those posts other than that the posts only say either one or both of the following:

[LIST]
[*]use linux alsa driver modules
[*]use module snd-hda-codec-nvhdmi.
[/LIST]
I really don't understand whether I have missed something in those posts.

I am a bit wary of installing the linux alsa driver modules, because once I installed the latest snapshot version of alsa (using the alsa upgrade script) and ended up with 'aplay -l' saying 'no sound cards found'.  And hence had to reinstall entire ubuntu (didn't know the way back). Wouldn't like to do it unless I know that it is safe to do it, and that it can be uninstalled without trouble if it doesn't work.  Please could you tell me if it safe to install it?

Secondly, from what little I can understand from the alsa upgrade script, I can see that you automatically check for and install a lot of software such libasound, etc.  Are all of them really required for alsa to function properly?  Just asking because, after reinstalling ubuntu less than a week ago, my system is a fresh system.  I haven't installed any software other than those that came with original installation.  I am sure that a lot of software that gets installed with alsa upgrade script are presently not installed in my system.

Thanks again for helping me with my issues with sound.

Regards,
P.

Yeah, it's safe to do.

---

### Post by prasadrvln on 2010-12-06
lidex,
 
Over the weekend, I installed the linux-alsa-driver-modules as suggested.  But I must admit the results have not been very successful.  The installation went smoothly.  When I rebooted and checked,
[LIST]
[*]there was no difference in the output of "aplay -l", meaning that there were no additional hdmi ports shown.
[*]the output of "aplay -L", however, is different.  It looks like the iec958 port I had before got changed to "hdmi", but with same card no. and device no. I tried to play a .wav file using aplay (and with hw, plughw, hdmi etc), but no sound.
[*]when I select the volume mixer icon (on the top right hand corner) and select sound preferences, the devices available under "hardware" tab are different from what I had before.  There is now a "HDMI output" menu item.  But selecting that and trying to play a .wav file had no effect.  No sound.
[*]because I rebooted, I had to "modprobe snd-hda-codec-nvhdmi" again.  But this module did not get inserted/loaded into the kernel.  It exited with a fatal error.  I was able to load the module "snd-hda-codec-hdmi".  But no sound again.
[*]I also have a module called "snd-hda-codec-intelhdmi" (or something like that).  But I didn't try to load it.
[*]because of all the above, I uninstalled the linux-alsa-driver-modules thingy.  Uninstallation went smoothly. And I am back to normal (or rather back to where I was).
[/LIST]Regards,
P.

---

### Post by prasadrvln on 2010-12-09
[FONT=Times New Roman][SIZE=3]After struggling for more than a month with not getting sound through my Monitor speakers, I have found a very simple solution. But before I put my solution down I would like to ask a few simple questions. (a) Why should thousands of Linux users struggle with this issue? (b) How has Windows been doing it for all these years and Apple Macs probably since before Windows? And why is that Linux can’t do it, in over 15 years of existence in the public world? (c) I have read more than about 3000 posts on the issue of sound.  Many people recommended solutions.  But is it really realistic or appropriate to expect that people who implement these solutions understand what they are trying to do? And don’t start telling me that “Linux is free. So you get what you get.  Don’t like it? Go away”.  You probably could say that 10 years ago, when Linux was not even recognising USB ports.  Not any more.  You can’t say that today, when so many people are taking pains to promote it as the alternative to Windows. (d) Lennart Pottering (developer of PulseAudio) says that it is his goal to see that the system should work right out of the box.  As far as I know, there is no timeframe for this.  Does anybody know? (e) As I asked before, do the people at Alsa / PulseAudio / NVidia care? As I see it, my system is not exactly new.  I bought it two years ago.  There have been four updates to Alsa in the intervening period. (f) I am a (Java) programmer myself.  When I program I take care to see that the program compiles.  Sometimes I am faced with a decision to use a new feature in Java in my code.  My decision always has been to not use it, because when I give my code to someone, I want them to be able to compile it, even if they don’t have the newest Java.  Why can’t the Alsa programs be written like that? My obvious question is the latest 1.0.23 Alsa packages compile under 2.6.32 kernel, but not under 2.6.35 kernel.  Why? Or more importantly, why can’t the program be written such that it compiles under any kernel? [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]I don’t expect anybody to answer the above questions (but it would be nice to get answers, at least for some, if not all).[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ok. My solution is hereunder:[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]1.[/SIZE]                  [SIZE=3]Unless I can hear sound through my speakers (by the time I sleep on this Friday night), I have decided to remove Linux completely from my system.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]2.[/SIZE]                  [SIZE=3]I don’t like Windows that much.  But at least it gives me sound.  I am a music programmer and I need sound.  I am going back to Windows.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]3.[/SIZE]                  [SIZE=3]After using Linux for nearly 10 years, I am sad to have to do this.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT] 
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT] 
[FONT=Times New Roman][SIZE=3]Happy now? [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Thanks for your understanding.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Regards,[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]P.[/SIZE][/FONT]

---

### Post by opuss20 on 2010-12-25
I've been searching for the answer to this for the entire day, and I managed to get a result much better than yours. 

After much fiddling and formats I arrived on this:
[http://ubuntuforums.org/showpost.php?p=9219191&postcount=212](http://ubuntuforums.org/showpost.php?p=9219191&postcount=212)
Look at section 11b. If you're unable:

> ...For anyone with an nVidia card and not able to get sound to go through their HDMI cable and does not even show HDMI or digital as an option in sound preferences this may be able to help:

1. Add "ppa:ubuntu-audio-dev/ppa" to the repository in synaptic. Refresh synaptic.

2. Upgrade all the pulse-audio packages

3. find out your kernel version: type "uname -r" in a terminal. Mine came out to be 2.6.32-21-generic (default ubuntu 10.04). 

4. install "linux-alsa-driver-modules-2.6.32-21-generic" (your kernel may be different). 

I got this package from a launchpad bug that listed it as a possible fix to the dreaded sound through HDMI cables problem. Installing this package gave me the options in sound preferences to choose digital sound/HDMI (IEC958 ). I'm not 100% sure that being able to see IEC958 in sound preferences came right after updating all pulse-audio packages or if it only came after installing this package. 

I did also have to change some sound setting on MythTV's frontend. Go to Utilities/Setup -> General -> Audio system -> Audio output device -> change to ALSA:spdif

Note: I wasnt using Mythbuntu or MythTV, just plain ubuntu 10.10.

I just followed those steps.

Blacklisted the required modules I believe stated on this thread
Follow Steps
Reboot
put: 'load-module module-alsa-sink device=hw:1,9' under line '#load-module module-alsa-sink' in /etc/pulse/default.pa.
Rebooted
I then went into alsamixer, hit f6, enabled the nvidia hdmi sound, unmuted the options in that section
Rebooted
Enabled the Nvidia hdmi in the sound applet under hardware. 

Good luck if any one follows these directions.

---

### Post by layr on 2010-12-29
Hey. Same prob here-no voice via HDMI. Installed ppa and alsa. When opening alsamixer, and hit F6(select soundcard), i only had two options - default and HD intel. My alsa script output is [here]("http://www.alsa-project.org/db/?f=b7593b0710e4c3d49c8190c39c2de7c6c5480301").
Any advice would be appreciated:)

Edit: graphics: Quadro fx 570m (don't know how the graphics card should have anything to do with this, but some users added this to their info, so..:P)
sound: Intel high-definition SoundBlaster Pro

---

### Post by jimbo99 on 2010-12-29
> **prasadrvln said:**
> 
Can't understand how Windows has been able to do it for since before linux was born, and how linux hasn't been able to do it in nearly 20 years.  I think this sound issue (there are millions of posts in thousands of forums across the world regarding sound in linux) has really killed linux as an alternative to Windows.


HDMI hasn't been out that long.  Linux hasn't quite hit the 20 year mark.  I believe the quoted price-tag for building an OS the stature of Linux (and Windows) is around $10 billion.  

Unfortunately, there is the side affect of having other outputs disabled when you try to output to HDMI.  At least that's the way it is under Win7.  As far as Vista goes I'm pretty sure it's the same as Win7.  I have no idea of whether HDMI works with XP at all.

I had the desire to plug in my speakers to use along with using my TVs speakers only to find that Win7 wouldn't allow that.  Apparently you can set your computer to output to HDMI and nothing else, or something else (even multiples) but no HDMI.  I desired this because I felt there was a problem with the speakers on the TV not having enough clarity for me.

My main multimedia rig runs 64bit Ubuntu 10.10 along with XBMC.  I have many speakers going out through the sound ports and it sounds nice.  I don't have any sound output to HDMI on this rig though.  I do on my PS3 and XBOX360 though.

My PS3 is connected via HDMI to the TV.  Then I connected a set of speakers up as an "out" from the TV itself (via one of the RCA jack series).  That gave me enough of a boost to make things sound clear.  I wound up with RCA out to a 3.5mm jack, then a coupler, then 3.5mm jack to the powered speakers.  It's tough to balance the sound between the two, but at least it's clarity is better.

As far as the HDMI out limitation goes, I don't know why the it's there -- that you can only output to HDMI and nothing else (from a computer), when you can have multiple outputs, and multiple sound cards, in a PC (even under Windows).

---

### Post by layr on 2010-12-29
> **jimbo99 said:**
> I have no idea of whether HDMI works with XP at all.
Like a charm.

---

### Post by lidex on 2010-12-29
> **jimbo99 said:**
> 
As far as the HDMI out limitation goes, I don't know why the it's there -- that you can only output to HDMI and nothing else (from a computer), when you can have multiple outputs, and multiple sound cards, in a PC (even under Windows).

You could try this method. Scroll down to section 'Using asound.conf' on this page:
[http://www.knoppmythwiki.org/index.php?page=DigitalAudioHowTo](http://www.knoppmythwiki.org/index.php?page=DigitalAudioHowTo)

---

### Post by Salane on 2010-12-30
hdmi is simply not enabled in xorg.conf

add these lines to the device section in xorg.conf then reboot
code:
> Option "Audio" "true"
Option "HDMI" "all"

---

### Post by layr on 2010-12-30
> **Salane said:**
> hdmi is simply not enabled in xorg.conf

add these lines to the device section in xorg.conf then reboot
code:

Didn't change anything whatsoever
My xorg file is:
> 
Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Default Device"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
    Option "Audio" "true"
    Option "HDMI" "all" 
EndSection
Should i uninstall alsa and ppa?

---

### Post by Salane on 2010-12-30
I don't know I didn't

---

### Post by giox069 on 2010-12-30
Hello, I'm new on this thread.
I solved a similar problem in my shuttle XS35GT (no HDMI audio with nvidia drivers) and ubuntu deskop 10.10 x86:

It seems that pulseaudio does not correctly setup its "sinks" (maybe due to a udev problem ?).
On my pc, the "aplay -l" command says that there are 4 HDMI devices on card 1.
Checking with cat /proc/asound/card1/eld#0.0  (and eld#1.0, eld#2.0, eld#3.0) I discovered that only the SECOND device (in the file eld#1.0) has monitor_present = 1. The device has number "7" as reported by aplay -l.

But pulseaudio only reports one sink to the FIRST hdmi device:
pactl list | less
only shows one sink to analog audio and one sink to HDMI device on card 1 number 3, which is wrong, because the device 3 does not have a monitor connected.

So my workaround was to edit the file /etc/pulse/default.pa and add
load-module module-alsa-sink device=hw:1,7
just after all other module-alsa-sink lines.
Rreboot and HDMI audio should work.

This is a workaround, because in this way we are doing a static mapping, and a minor change in device numbering in the kernel will stop the workaround working. I think the final solution will be somewhere else, maybe in udev. But I'm not an udev expert :(

---

### Post by xloubis on 2011-01-01
Well I would like to share with you my solution to this problem. For my case /ATI user/ (as well as for Nvidia users) there is a serious issue with the interference of the -fglrx with the radeon drivers (as well as with the nvidia ones). So follow the instructions in [https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch) reboot and check again for the sound issue. I wish it'll work for you guys as worked for me :)

Cheers

---

### Post by layr on 2011-01-04
> **giox069 said:**
> Hello, I'm new on this thread.
I solved a similar problem in my shuttle XS35GT (no HDMI audio with nvidia drivers) and ubuntu deskop 10.10 x86:

It seems that pulseaudio does not correctly setup its "sinks" (maybe due to a udev problem ?).
On my pc, the "aplay -l" command says that there are 4 HDMI devices on card 1.
Checking with cat /proc/asound/card1/eld#0.0  (and eld#1.0, eld#2.0, eld#3.0) I discovered that only the SECOND device (in the file eld#1.0) has monitor_present = 1. The device has number "7" as reported by aplay -l.
Thanks for reply. Anyway, my 'aplay -l' command results in this:
```

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
```so i really can't figure out how to edit my pulse files.

---

### Post by lidex on 2011-01-04
> **layr said:**
> Thanks for reply. Anyway, my 'aplay -l' command results in this:
```

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
```so i really can't figure out how to edit my pulse files.
Need to see a little more system info. 
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by layr on 2011-01-05
I actually run that a week ago or so, don't know why i didn't upload it. Here it goes:
```
upload=true&script=true&cardinfo=
!!################################
!!ALSA Information Script v 0.4.59
!!################################

!!Script ran on: Wed Jan  5 10:59:35 UTC 2011


!!Linux Distribution
!!------------------

Ubuntu 10.10 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 10.10"


!!DMI Information
!!---------------

Manufacturer:      Hewlett-Packard
Product Name:      HP Compaq 8510w 


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

snd_hda_intel


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

 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xe8044000 irq 46


!!PCI Soundcards installed in the system
!!--------------------------------------

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)


!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!--------------------------------------------------------

00:1b.0 0403: 8086:284b (rev 03)
    Subsystem: 103c:30c5


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

!!Module: snd_hda_intel
    bdl_pos_adj : 1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
    beep_mode : 1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1
    enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
    enable_msi : -1
    id : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
    index : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
    model : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
    patch : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
    position_fix : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
    power_save : 0
    power_save_controller : Y
    probe_mask : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
    probe_only : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
    single_cmd : N


!!HDA-Intel Codec information
!!---------------------------
--startcollapse--

Codec: Analog Devices AD1981
Address: 0
AFG Function Id: 0x1 (unsol 0)
Vendor Id: 0x11d41981
Subsystem Id: 0x103c30c5
Revision Id: 0x100200
No Modem Function Group found
Default PCM:
    rates [0x7f]: 8000 11025 16000 22050 32000 44100 48000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Default Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
Default Amp-Out caps: ofs=0x3d, nsteps=0x3f, stepsize=0x05, mute=1
GPIO: io=4, o=0, i=0, unsolicited=1, wake=0
  IO[0]: enable=0, dir=0, wake=0, sticky=0, data=1, unsol=0
  IO[1]: enable=0, dir=0, wake=0, sticky=0, data=1, unsol=0
  IO[2]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[3]: enable=0, dir=0, wake=0, sticky=0, data=1, unsol=0
Node 0x02 [Audio Output] wcaps 0x30311: Stereo Digital
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0x60]: 44100 48000
    bits [0x2]: 16
    formats [0x5]: PCM AC3
  Delay: 3 samples
  Connection: 2
     0x01* 0x04
Node 0x03 [Audio Output] wcaps 0x441: Stereo
  Device: name="AD198x Analog", type="Audio", device=0
  Converter: stream=0, channel=0
  Power states:  D0 D3
  Power: setting=D0, actual=D0
  Processing caps: benign=1, ncoeff=70
Node 0x04 [Audio Input] wcaps 0x100511: Stereo
  Device: name="AD198x Analog", type="Audio", device=0
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x7f]: 8000 11025 16000 22050 32000 44100 48000
    bits [0x6]: 16 20
    formats [0x1]: PCM
  Power states:  D0 D3
  Power: setting=D0, actual=D0
  Connection: 1
     0x15
Node 0x05 [Pin Complex] wcaps 0x400187: Stereo Amp-In Amp-Out
  Control: name="Master Playback Switch", index=0, device=0
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x3d, nsteps=0x3f, stepsize=0x05, mute=1
  Amp-Out vals:  [0x2a 0x2a]
  Pincap 0x0001173f: IN OUT HP EAPD Detect Trigger ImpSense
    Vref caps: HIZ 50 GRD 80
  EAPD 0x2: EAPD
  Pin Default 0x92174110: [Fixed] Speaker at Int Front
    Conn = Analog, Color = Green
    DefAssociation = 0x1, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT VREF_HIZ
  Unsolicited: tag=00, enabled=0
  Connection: 2
     0x03 0x0e*
Node 0x06 [Pin Complex] wcaps 0x400185: Stereo Amp-Out
  Amp-Out caps: ofs=0x3d, nsteps=0x3f, stepsize=0x05, mute=1
  Amp-Out vals:  [0x2a 0x2a]
  Pincap 0x0000001f: OUT HP Detect Trigger ImpSense
  Pin Default 0x0321201f: [Jack] HP Out at Ext Left
    Conn = 1/8, Color = Grey
    DefAssociation = 0x1, Sequence = 0xf
  Pin-ctls: 0xc0: OUT HP
  Unsolicited: tag=37, enabled=1
  Connection: 2
     0x03 0x0e*
Node 0x07 [Pin Complex] wcaps 0x400104: Mono Amp-Out
  Amp-Out caps: ofs=0x3d, nsteps=0x3f, stepsize=0x05, mute=1
  Amp-Out vals:  [0x80]
  Pincap 0x00000010: OUT
  Pin Default 0x410710f0: [N/A] Line Out at Ext Rear
    Conn = Analog, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Connection: 1
     0x0f
Node 0x08 [Pin Complex] wcaps 0x400083: Stereo Amp-In
  Control: name="Mic Boost", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Pincap 0x00001727: IN Detect Trigger ImpSense
    Vref caps: HIZ 50 GRD 80
  Pin Default 0x03a12020: [Jack] Mic at Ext Left
    Conn = 1/8, Color = Grey
    DefAssociation = 0x2, Sequence = 0x0
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=38, enabled=1
Node 0x09 [Pin Complex] wcaps 0x400187: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x3d, nsteps=0x3f, stepsize=0x05, mute=1
  Amp-Out vals:  [0xbf 0xbf]
  Pincap 0x00001737: IN OUT Detect Trigger ImpSense
    Vref caps: HIZ 50 GRD 80
  Pin Default 0x0181302e: [Jack] Line In at Ext Rear
    Conn = 1/8, Color = Blue
    DefAssociation = 0x2, Sequence = 0xe
  Pin-ctls: 0x20: IN VREF_HIZ
  Unsolicited: tag=00, enabled=0
  Connection: 2
     0x03* 0x0e
Node 0x0a [Pin Complex] wcaps 0x400301: Stereo Digital
  Pincap 0x00000010: OUT
  Pin Default 0x1345f1a0: [Jack] SPDIF Out at Int Left
    Conn = Optical, Color = Other
    DefAssociation = 0xa, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Connection: 1
     0x02
Node 0x0b [Audio Selector] wcaps 0x300101: Stereo
  Connection: 6
     0x03 0x0c 0x09 0x0e* 0x05 0x18
Node 0x0c [Audio Mixer] wcaps 0x200101: Stereo
  Connection: 2
     0x1e 0x1f
Node 0x0d [Audio Selector] wcaps 0x30010c: Mono Amp-Out
  Control: name="Beep Playback Volume", index=0, device=0
    ControlAmp: chs=1, dir=Out, idx=0, ofs=0
  Control: name="Beep Playback Switch", index=0, device=0
    ControlAmp: chs=1, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x0f, nsteps=0x0f, stepsize=0x0b, mute=1
  Amp-Out vals:  [0x80]
  Connection: 2
     0x10* 0x16
Node 0x0e [Audio Mixer] wcaps 0x200101: Stereo
  Connection: 8
     0x0d 0x11 0x12 0x13 0x1a 0x1b 0x1c 0x1d
Node 0x0f [Audio Mixer] wcaps 0x200100: Mono
  Connection: 1
     0x0b
Node 0x10 [Beep Generator Widget] wcaps 0x700000: Mono
Node 0x11 [Audio Selector] wcaps 0x30010d: Stereo Amp-Out
  Control: name="PCM Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Control: name="PCM Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x17, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-Out vals:  [0x17 0x17]
  Connection: 1
     0x03
Node 0x12 [Audio Selector] wcaps 0x30010d: Stereo Amp-Out
  Amp-Out caps: ofs=0x17, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-Out vals:  [0x80 0x80]
  Connection: 1
     0x08
Node 0x13 [Audio Selector] wcaps 0x30010d: Stereo Amp-Out
  Amp-Out caps: ofs=0x17, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-Out vals:  [0x80 0x80]
  Connection: 1
     0x09
Node 0x14 [Power Widget] wcaps 0x500500: Mono
  Power states:  D0 D3
  Power: setting=D0, actual=D0
  Connection: 13
     0x0d 0x0e 0x0f 0x10 0x13 0x14 0x15 0x16 0x17 0x18 0x19 0x1a 0x1d
Node 0x15 [Audio Selector] wcaps 0x30010d: Stereo Amp-Out
  Control: name="Capture Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Control: name="Capture Switch", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Control: name="Capture Source", index=0, device=0
  Amp-Out caps: ofs=0x00, nsteps=0x0f, stepsize=0x05, mute=1
  Amp-Out vals:  [0x80 0x80]
  Connection: 8
     0x0c* 0x09 0x0e 0x0f 0x19 0x05 0x18 0x17
Node 0x16 [Pin Complex] wcaps 0x400000: Mono
  Pincap 0x00000020: IN
  Pin Default 0x995711f0: [Fixed] Digital Out at Int ATAPI
    Conn = Analog, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
Node 0x17 [Pin Complex] wcaps 0x400081: Stereo
  Pincap 0x00000027: IN Detect Trigger ImpSense
  Pin Default 0x5993e0f0: [N/A] Aux at Int ATAPI
    Conn = ATAPI, Color = White
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x20: IN
  Unsolicited: tag=00, enabled=0
Node 0x18 [Pin Complex] wcaps 0x400187: Stereo Amp-In Amp-Out
  Control: name="Internal Mic Boost", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x3d, nsteps=0x3f, stepsize=0x05, mute=1
  Amp-Out vals:  [0xbf 0xbf]
  Pincap 0x00001737: IN OUT Detect Trigger ImpSense
    Vref caps: HIZ 50 GRD 80
  Pin Default 0x91a79121: [Fixed] Mic at Int Rear
    Conn = Analog, Color = Pink
    DefAssociation = 0x2, Sequence = 0x1
    Misc = NO_PRESENCE
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=00, enabled=0
  Connection: 2
     0x03* 0x0e
Node 0x19 [Pin Complex] wcaps 0x400001: Stereo
  Pincap 0x00000020: IN
  Pin Default 0x593310f0: [N/A] CD at Int ATAPI
    Conn = ATAPI, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x20: IN
Node 0x1a [Audio Selector] wcaps 0x30010d: Stereo Amp-Out
  Amp-Out caps: ofs=0x17, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-Out vals:  [0x80 0x80]
  Connection: 1
     0x05
Node 0x1b [Audio Selector] wcaps 0x30010d: Stereo Amp-Out
  Amp-Out caps: ofs=0x17, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-Out vals:  [0x80 0x80]
  Connection: 1
     0x17
Node 0x1c [Audio Selector] wcaps 0x30010d: Stereo Amp-Out
  Amp-Out caps: ofs=0x17, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-Out vals:  [0x80 0x80]
  Connection: 1
     0x18
Node 0x1d [Audio Selector] wcaps 0x30010d: Stereo Amp-Out
  Amp-Out caps: ofs=0x17, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-Out vals:  [0x80 0x80]
  Connection: 1
     0x19
Node 0x1e [Audio Selector] wcaps 0x30010d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Connection: 1
     0x08
Node 0x1f [Audio Selector] wcaps 0x30010d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Connection: 1
     0x18
Codec: Conexant ID 2c06
Address: 1
MFG Function Id: 0x2 (unsol 1)
Vendor Id: 0x14f12c06
Subsystem Id: 0x103c1379
Revision Id: 0x100000
Modem Function Group: 0x2
--endcollapse--


!!ALSA Device nodes
!!-----------------

crw-rw----+ 1 root audio 116,  6 Jan  4 16:41 /dev/snd/controlC0
crw-rw----+ 1 root audio 116,  5 Jan  4 16:41 /dev/snd/hwC0D0
crw-rw----+ 1 root audio 116,  4 Jan  4 16:41 /dev/snd/hwC0D1
crw-rw----+ 1 root audio 116,  3 Jan  4 23:44 /dev/snd/pcmC0D0c
crw-rw----+ 1 root audio 116,  2 Jan  5 08:00 /dev/snd/pcmC0D0p
crw-rw----+ 1 root audio 116,  1 Jan  4 16:41 /dev/snd/seq
crw-rw----+ 1 root audio 116, 33 Jan  4 16:41 /dev/snd/timer

/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root  60 Jan  4 16:41 .
drwxr-xr-x 3 root root 200 Jan  4 16:41 ..
lrwxrwxrwx 1 root root  12 Jan  4 16:41 pci-0000:00:1b.0 -> ../controlC0


!!Aplay/Arecord output
!!------------

APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

ARECORD

**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

!!Amixer output
!!-------------

!!-------Mixer controls for card 0 [Intel]

Card hw:0 'Intel'/'HDA Intel at 0xe8044000 irq 46'
  Mixer name    : 'Analog Devices AD1981'
  Components    : 'HDA:11d41981,103c30c5,00100200 HDA:14f12c06,103c1379,00100000'
  Controls      : 11
  Simple ctrls  : 9
Simple mixer control 'Master',0
  Capabilities: pvolume pswitch pswitch-joined penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 63
  Mono:
  Front Left: Playback 42 [67%] [-28.50dB] [on]
  Front Right: Playback 42 [67%] [-28.50dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 23 [74%] [0.00dB] [on]
  Front Right: Playback 23 [74%] [0.00dB] [on]
Simple mixer control 'Mic',0
  Capabilities: cswitch cswitch-joined cswitch-exclusive penum
  Capture exclusive group: 0
  Capture channels: Mono
  Mono: Capture [on]
Simple mixer control 'Mic Boost',0
  Capabilities: volume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 0 [0%]
  Front Right: 0 [0%]
Simple mixer control 'Beep',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 15
  Mono: Playback 0 [0%] [-45.00dB] [off]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 15
  Front Left: Capture 0 [0%] [0.00dB] [off]
  Front Right: Capture 0 [0%] [0.00dB] [off]
Simple mixer control 'Mix',0
  Capabilities: cswitch cswitch-joined cswitch-exclusive penum
  Capture exclusive group: 0
  Capture channels: Mono
  Mono: Capture [off]
Simple mixer control 'Docking-Station',0
  Capabilities: cswitch cswitch-joined cswitch-exclusive penum
  Capture exclusive group: 0
  Capture channels: Mono
  Mono: Capture [off]
Simple mixer control 'Internal Mic Boost',0
  Capabilities: volume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 0 [0%]
  Front Right: 0 [0%]


!!Alsactl output
!!-------------

--startcollapse--
state.Intel {
    control.1 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 63'
        comment.dbmin -9150
        comment.dbmax 300
        iface MIXER
        name 'Master Playback Volume'
        value.0 42
        value.1 42
    }
    control.2 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'Master Playback Switch'
        value true
    }
    control.3 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 31'
        comment.dbmin -3450
        comment.dbmax 1200
        iface MIXER
        name 'PCM Playback Volume'
        value.0 23
        value.1 23
    }
    control.4 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 2
        iface MIXER
        name 'PCM Playback Switch'
        value.0 true
        value.1 true
    }
    control.5 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 3'
        comment.dbmin 0
        comment.dbmax 3000
        iface MIXER
        name 'Mic Boost'
        value.0 0
        value.1 0
    }
    control.6 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 3'
        comment.dbmin 0
        comment.dbmax 3000
        iface MIXER
        name 'Internal Mic Boost'
        value.0 0
        value.1 0
    }
    control.7 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 15'
        comment.dbmin 0
        comment.dbmax 2250
        iface MIXER
        name 'Capture Volume'
        value.0 0
        value.1 0
    }
    control.8 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 2
        iface MIXER
        name 'Capture Switch'
        value.0 false
        value.1 false
    }
    control.9 {
        comment.access 'read write'
        comment.type ENUMERATED
        comment.count 1
        comment.item.0 Mic
        comment.item.1 Docking-Station
        comment.item.2 Mix
        iface MIXER
        name 'Capture Source'
        value Mic
    }
    control.10 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 1
        comment.range '0 - 15'
        comment.dbmin -4500
        comment.dbmax 0
        iface MIXER
        name 'Beep Playback Volume'
        value 0
    }
    control.11 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'Beep Playback Switch'
        value false
    }
}
--endcollapse--


!!All Loaded Modules
!!------------------

Module
nls_iso8859_1
nls_cp437
vfat
fat
mmc_block
ppp_deflate
zlib_deflate
bsd_comp
ppp_async
crc_ccitt
binfmt_misc
option
usb_wwan
usbserial
ipt_REJECT
ipt_LOG
xt_limit
xt_tcpudp
ipt_addrtype
xt_state
ip6table_filter
ip6_tables
nf_nat_irc
nf_conntrack_irc
nf_nat_ftp
nf_nat
nf_conntrack_ipv4
nf_defrag_ipv4
nf_conntrack_ftp
nf_conntrack
iptable_filter
ip_tables
x_tables
pata_pcmcia
tpm_infineon
arc4
nvidia
snd_hda_codec_analog
pcmcia
joydev
snd_hda_intel
snd_hda_codec
snd_hwdep
snd_pcm
snd_seq_midi
snd_rawmidi
iwlagn
snd_seq_midi_event
snd_seq
iwlcore
snd_timer
snd_seq_device
mac80211
ppdev
hp_wmi
snd
cfg80211
tpm_tis
tpm
video
yenta_socket
pcmcia_rsrc
parport_pc
output
psmouse
soundcore
hp_accel
tpm_bios
pcmcia_core
serio_raw
lis3lv02d
input_polldev
intel_agp
snd_page_alloc
coretemp
agpgart
lp
parport
usbhid
hid
usb_storage
sdhci_pci
sdhci
firewire_ohci
led_class
firewire_core
crc_itu_t
e1000e


!!Sysfs Files
!!-----------

/sys/class/sound/hwC0D0/init_pin_configs:
0x05 0x92174110
0x06 0x0321201f
0x07 0x410710f0
0x08 0x03a12020
0x09 0x0181302e
0x0a 0x1345f1a0
0x16 0x995711f0
0x17 0x5993e0f0
0x18 0x91a79121
0x19 0x593310f0

/sys/class/sound/hwC0D0/driver_pin_configs:

/sys/class/sound/hwC0D0/user_pin_configs:

/sys/class/sound/hwC0D0/init_verbs:

/sys/class/sound/hwC0D1/init_pin_configs:
0x73 0x016a10f0

/sys/class/sound/hwC0D1/driver_pin_configs:

/sys/class/sound/hwC0D1/user_pin_configs:

/sys/class/sound/hwC0D1/init_verbs:


!!ALSA/HDA dmesg
!!------------------

[54386.628161] [UFW BLOCK] IN=ppp0 OUT= MAC= SRC=93.158.110.171 DST=46.131.25.99 LEN=40 TOS=0x08 PREC=0x60 TTL=56 ID=0 DF PROTO=TCP SPT=80 DPT=56703 WINDOW=0 RES=0x00 RST URGP=0 
[55111.756913] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[55111.756925] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x3, stream=0x5, channel=0, format=0x4011
[55111.768074] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[55111.768084] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x3, stream=0x5, channel=0, format=0x4011
[55236.012354] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[55236.012435] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x3
[55544.339587] [UFW AUDIT] IN= OUT=ppp0 SRC=46.131.25.99 DST=217.71.32.116 LEN=77 TOS=0x00 PREC=0x00 TTL=64 ID=48524 DF PROTO=UDP SPT=60164 DPT=53 LEN=57 


```

---

### Post by lidex on 2011-01-05
@layr
Do you have an hdmi device? If so, is it on the motherboard or the video adapter? Can you post these please:
```
lspci
sudo lshw -C display
```

hdmi may be disabled in bios

---

### Post by layr on 2011-01-05
lspci gave me```

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:03.0 Communication controller: Intel Corporation Mobile PM965/GM965 MEI Controller (rev 0c)
00:03.2 IDE interface: Intel Corporation Mobile PM965/GM965 PT IDER Controller (rev 0c)
00:03.3 Serial controller: Intel Corporation Mobile PM965/GM965 KT Controller (rev 0c)
00:19.0 Ethernet controller: Intel Corporation 82566MM Gigabit Network Connection (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HBM (ICH8M-E) LPC Interface Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation G84M [Quadro FX 570M] (rev a1)
02:06.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b9)
02:06.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b9)
02:06.2 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 03)
02:06.3 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 20)
10:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)

```sudo lshw -C display printed:
```
  *-display               
       description: VGA compatible controller
       product: G84M [Quadro FX 570M]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:16 memory:e5000000-e5ffffff memory:d0000000-dfffffff memory:e6000000-e7ffffff ioport:4000(size=128)

```What do you mean by whether i have a hdmi dev? In comp or a TV or such?
If Ubuntu installation didn't change my bios, it couldn't be the case, as before format in XP environment i watched movies via HDMI.

Edit: could you please explain what those commands mean? I know it's extra work but would be good knowledge for noobs like myself:D

---

### Post by lidex on 2011-01-05
Look in jockey/hardware drivers and see what version of nvidia driver is in use. Alsa is not detecting a hdmi device.

---

### Post by layr on 2011-01-05
Search resulted in multiple jockey directories, none of those contained "hardware drivers" of any kind. Installed packages says ```
nvidia-173
nvidia-current
```
I know i installed driver that Ubuntu recommended, and i tried also the 173.

---

### Post by lidex on 2011-01-05
No, jockey **is** 'hardware drivers' in the 'system>administration' menu although in natty it's called 'additional drivers'

---

### Post by layr on 2011-01-05
Well that says the same - 173 (the unactivated verstion) and current. It doesn't give the version of the "current" one.

---

### Post by jsmkbunch2000 on 2011-01-05
I'm having the same problem with my Zotac MiniPC.  See my thread.  I am stuck.  I'm a noob and have no idea of what half of the things are that I am reading to check or verify.  Can someone else help ???

[http://ubuntuforums.org/showthread.php?t=1659305]("http://ubuntuforums.org/showthread.php?t=1659305")

---

### Post by tjones00 on 2011-01-05
To check the currently installed nvidia driver version try:

```
cat /proc/driver/nvidia/version
```

To double check try reading from the xorg log.
```

grep "NVIDIA GLX Module" /var/log/Xorg.0.log
```

or

```
grep "X Driver" /var/log/Xorg.0.log
```

---

### Post by layr on 2011-01-05
Thanks tjones00.
Resulted in ```
NVRM version: NVIDIA UNIX x86 Kernel Module  **260.19.06**  Mon Sep 13 06:35:06 PDT 2010
GCC version:  gcc version 4.4.5 (Ubuntu/Linaro 4.4.4-14ubuntu5) 

```

---

### Post by lidex on 2011-01-08
You need this module loading:
```
snd_hda_codec_nvhdmi
```
and it's not. I'm guessing the drivers are not recognizing your hdmi device and therefore not loading it. Take a good read of this thread:
[http://ubuntuforums.org/showthread.php?t=1552250](http://ubuntuforums.org/showthread.php?t=1552250)
to see how to get it recognized. I can't walk you through this as I've never used hdmi, but perhaps tjones00 can.

---

### Post by BicyclerBoy on 2011-01-08
This post from the expert...

[http://www.nvnews.net/vbulletin/showpost.php?p=2312420&postcount=7](http://www.nvnews.net/vbulletin/showpost.php?p=2312420&postcount=7)

Could be that pulseaudio is part of the problem again..

---

### Post by lidex on 2011-01-08
I doubt it. Alsa isn't picking up even one hdmi device. It accesses the hardware and pulse accesses alsa.

---

### Post by layr on 2011-01-08
Hehe, i f-ed something seriously up:D
First i installed alsa using "sudo apt-get install linux-backports-modules-alsa-2.6.35-24-generic alsa-utils"

and also nVidia driver. None of those made any changes, except ubuntu now loads into terminal:P "xstart" ends up in an error: "no screens found".

---

### Post by lidex on 2011-01-08
In the terminal run this command and reboot:
```
sudo nvidia-xconfig
```

---

### Post by layr on 2011-01-08
Already tried it. Probably i messed up with driver installation. Fixed it via system->additional drivers and activated ubuntu recommended one (ps is the system OK with all this installing and reinstalling?)

Anyway, as i understand i need newer alsa via backport. I used 
```
sudo apt-get install linux-backports-modules-alsa-2.6.35-24-generic alsa-utils
```yet, 
```
laur@LA-HP-Compaq-8510w:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.23.
```doesn't have "Compiled on Jul  6 2010 for kernel 2.6.35-24-generic (SMP)." line in the end, that should indicate it's the backport version. What am i doing wrong here?

---

### Post by tjones00 on 2011-01-08
Edit: I should add a 2.6.35 kernel technically does not require an upgrade to alsa. alsa 1.0.23 is built into kernels >= 2.6.35. The alsa upgrade method was really for early builds of 10.04 that did not have the 2.6.35 kernel. (the time that post was written)

So don't sweat it over the timestamp. Now check to see if you have eld information for any device on your card. Refer to the link below.

[http://ubuntuforums.org/showpost.php?p=9732345&postcount=8](http://ubuntuforums.org/showpost.php?p=9732345&postcount=8)


If your graphics are still messed up try moving the xorg.conf and generating a new one to make sure nothing is merged.

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.original

sudo nvidia-xconfig
```



Great find from Nvidia BicyclerBoy. The probemask values are nice.

---

### Post by theSuperman on 2011-01-16
> **giox069 said:**
> Hello, I'm new on this thread.
I solved a similar problem in my shuttle XS35GT (no HDMI audio with nvidia drivers) and ubuntu deskop 10.10 x86:

It seems that pulseaudio does not correctly setup its "sinks" (maybe due to a udev problem ?).
On my pc, the "aplay -l" command says that there are 4 HDMI devices on card 1.
Checking with cat /proc/asound/card1/eld#0.0  (and eld#1.0, eld#2.0, eld#3.0) I discovered that only the SECOND device (in the file eld#1.0) has monitor_present = 1. The device has number "7" as reported by aplay -l.

But pulseaudio only reports one sink to the FIRST hdmi device:
pactl list | less
only shows one sink to analog audio and one sink to HDMI device on card 1 number 3, which is wrong, because the device 3 does not have a monitor connected.

So my workaround was to edit the file /etc/pulse/default.pa and add
load-module module-alsa-sink device=hw:1,7
just after all other module-alsa-sink lines.
Rreboot and HDMI audio should work.

This is a workaround, because in this way we are doing a static mapping, and a minor change in device numbering in the kernel will stop the workaround working. I think the final solution will be somewhere else, maybe in udev. But I'm not an udev expert :(
FINALLY! A solution that worked for me. I now have two devices listed under the Output tab in Sound Preferences: Internal Audio (stereo), which is HDMI output, and Internal Audio Analog Stereo (stereo), which my my internal laptop speakers.  This is on a 7,1 Macbook.

---

### Post by Volochanin on 2011-01-18
> **efflandt said:**
> What video card do you have, which drivers are you using for it, and what does alsamixer show under HDA NVidia?  Since **aplay -l** does not show HDMI and if alsamixer shows "no controls" instead of S/PDIF devices, you may need a newer snapshot of alsa 1.0.23 from the ppa repositories.  [https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules](https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules)

For example my nvidia GT 430 is so new that Linux does not even identify its model in lspci (although, it works fine with nvidia 260.19.21 drivers).  alsamixer said something about no controls, and aplay -l did not list any HDMI NVidia.  With newer alsa snapshot **aplay -l** now shows:

```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC887 Analog [ALC887 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC887 Digital [ALC887 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 9: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```Once you get that far you have to narrow down which of those devices works on that card (1 in my case):

```
aplay -D plughw:1,3 /usr/share/sounds/alsa/Front_Center.wav
```And try 1,7 1,8 1,9 until you find one that works.  My GT 220 used 1,3, but my GT 430 uses 1,9

Look for the module-alsa-sink line in /etc/pulse/default.pa and add this line to that section for whichever card,device worked (do not begin with # or that comments it out):

```
load-module module-alsa-sink device=hw:1,9
```I ended up with an extra Output device in Sound Preferences and contrary to what appears, **HDA NVidia** works for HDMI sound and **HDA NVidia Digital Stereo (HDMI)** does not.

thanks for this message. it helped me to receive sound.
nvidia GTS450. ubuntu 10.10

---

### Post by layr on 2011-01-19
Doublepost. Server responded in error, obviously it later passed these posts.

---

### Post by layr on 2011-01-19
Doublepost. Server responded in error, obviously it later passed these posts.

---

### Post by layr on 2011-01-19
> **tjones00 said:**
> Now check to see if you have eld information for any device on your card. Refer to the link below.

[http://ubuntuforums.org/showpost.php?p=9732345&postcount=8](http://ubuntuforums.org/showpost.php?p=9732345&postcount=8)

Okay, haven't been around for some time, had to concentrate on the exams - every time i try to fix something i end up dealing with the problem 20hours straight:P

Anyway, your post on that thread didn't help me. No eld info whatsoever. Is it a possibility there is no way for my card/system?

---

### Post by AJ1000 on 2011-01-20
This is how I got sound to work:

In terminal editor type:

gnome-alsamixer

Make sure all three items at the bottom are ticked.

I had one which was not ticked. When I ticked it, I got sound coming from HDMI.

---

### Post by edw00rd on 2011-01-21
Ok I've tried pretty much everything in this thread and have had minimal luck. I however HAVE BEEN SUCCESSFUL in getting the following command to work, and I do hear the .wav file through my HDMI audio on my Toshiba TV.

aplay -D plughw:0,3 /usr/share/sounds/alsa/Front_Center.wav
(This will actually play the wav "Front Center")

I also added this line to the /etc/pulse/default.pa:
<snip>
#load-module module-alsa-sink
load-module module-alsa-sink device=hw:0,3

rebooted. Still no sound. Did this:
$alsamixer
  F6
Only option is to select HDA Nvdia.
  TAB
(I turned the volume up on EVERYTHING possible lol)
Exited alsamixer

Navigated to System>Prferences>Sound
Hardware Tab: Under "Choose Device To Configure" I have only one choice "Internal Audio 1 Output Digital Stereo (HDMI) Output", under profile I have selected "Digital Stereo (HDMI) Output.

Output Tab: Selected "Internal Audio Digital Stereo (HDMI)"

::NO SOUND STILL:: (However the command "aplay -D plughw:0,3 /usr/share/sounds/alsa/Front_Center.wav" still works like a champ...WTF!

::Here is my aplay -l output:
** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC1200 Digital [ALC1200 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


And located here is the result to my alsa info script:
[http://www.alsa-project.org/db/?f=c8d5ca27267f08461e0c643674046fe027bc1798](http://www.alsa-project.org/db/?f=c8d5ca27267f08461e0c643674046fe027bc1798)

I am now at a dead end... frustrated... and soundless :(

Can someone please help me out?

---

### Post by edw00rd on 2011-01-23
nobody... really?

---

### Post by theSuperman on 2011-01-23
> **edw00rd said:**
> Ok I've tried pretty much everything in this thread and have had minimal luck. I however HAVE BEEN SUCCESSFUL in getting the following command to work, and I do hear the .wav file through my HDMI audio on my Toshiba TV.

aplay -D plughw:0,3 /usr/share/sounds/alsa/Front_Center.wav
(This will actually play the wav "Front Center")

You can manually set the output device in smplayer, vlc, mplayer, etc. Try manually setting it to the 0,3 device and see if that outputs. 
You could always try changing the audio output plugin and device using ```
gstreamer-properties
```

---

### Post by edw00rd on 2011-01-23
Ok, partial success....

When using gstreamer-properties:

I select plugin:ALSA and device:HDMI 0, when I hit test it gives me a repeated "bip bip bip bip...." and if I hit test again it errors out saying that HDMI0 is being used by another application.. and I have nothing else open... 

When I plugged the device info into VLC it worked like a champ... PROPS TO THE VLC PEOPLE!! I've been using VLC for years and this just made my day... I can now watch movies!!!

Still no system sound though :( .... I feel like I'm on the verge here... any other suggestions? I've been at this straight for 5 hours (thats just today) and this is the first major milestone I've hit. THANK YOU SO MUCH FOR GIVING ME HOPE!!! LOL

---

### Post by edw00rd on 2011-01-23
Ok so here's my issue now... VLC works perfectly when I tell it to use the specified device at hw0,3... but this doesn't fix my system sound. When I tell gstreamer-properties to use HDMI0 as my audio output and then browse to grooveshark.com (streaming radio) the audio comes through my speakers like (bip bip bip bip bip) and the "bips" change pitch so I'm sure there is a song playing there... *sigh Any ideas... Why would VLC work fine and everything else not? Is there some config I can do to the pulse audio setup... 

The help so far is greatly appreciated!

---

### Post by maxslug on 2011-01-27
OK, Mythbuntu 10.10, latest updates and my Nvidia sound card is all auto-detected straight out of the box.  This page is helpful : [http://www.mythtv.org/wiki/User_Manual:HDAudioPassthrough#Summary_of_working_.2F_non-working_know_solution](http://www.mythtv.org/wiki/User_Manual:HDAudioPassthrough#Summary_of_working_.2F_non-working_know_solution)  . My Combo is nVidia GT218 (MSI N210-MD512H), Pioneer VSX-1120, 2.6.35, alsa 1.0.23+dfsg-1ubuntu4

  

I made this script to try all the alsa devices ... run it in /usr/share/sound/alsa

```

#!/usr/bin/perl -w

$pcms = `aplay -L`;
@skip = qw/Intel/;
@wavs = glob("*.wav");

DEV:
foreach (split("\n",$pcms)) {
        chomp;
        next if /^\s+/;
        next unless /CARD=/;
        foreach my $s (@skip){
                next DEV if /CARD=$s/;
        }
        print "$_\n";
        foreach my $w (sort @wavs) {
                print "  $w\n";
                system("aplay -D $_ $w") and next DEV;
        }
}

```After unmuting all the SPDIF channels on my second card in alsamixer, Using this I found that these devices output sound for me :
```

plughw:CARD=NVidia,DEV=7
plughw:CARD=NVidia,DEV=8
plughw:CARD=NVidia,DEV=9

```My question to you guys is I only hear each of the waves being played in stereo, not in the individual speakers.  Is this right or do I have to do something special to get each of the files to play in each speaker?


EDIT: I stumbled upon the wonderful "speaker-test" command and now I hear each channel individually, so I know the driver is working.   Now for getting mythtv, system sounds, boxee, and blu-rays to setup correctly. 

```

 speaker-test -D plughw:CARD=NVidia,DEV=7 -c 8

```
My amp shows a crazy "PCM" mode when tis running btw.

Thanks!
-m

---

### Post by inverser on 2011-07-10
Sorry to resurrect this thread, but I came across it while helping a friend get his laptop HDMI audio working. The video was fine. This was on Maverick Meerkat. 

Anyway, the fix was simple.

```
sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update
sudo apt-get install linux-alsa-driver-modules-$(uname -r)
```

Then restart system. Please mark this thread solved.

---

