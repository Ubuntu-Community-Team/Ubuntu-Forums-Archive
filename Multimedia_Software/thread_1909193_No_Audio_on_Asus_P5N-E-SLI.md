---
title: "No Audio on Asus P5N-E-SLI"
date: 2012-01-14
forum: Multimedia Software
---

### Post by robn30 on 2012-01-14
I am try again to get help on this issue.  I am attaching a link to another thread I have elsewhere on the topic.  [http://ubuntuforums.org/showthread.php?t=1901598](http://ubuntuforums.org/showthread.php?t=1901598).  I am hoping someone can shed some light on this issue.  Basic background is when I install the NVidia Driver found under Additional Drivers it breaks my audio.  Before installing this driver all is well and works perfect.  How the heck can a display driver break my audio?  Also I have tried them all, as in the 4 available choices present in the list.  Luckily I can simply remove the driver, restart, and audio returns without fail.  Please someone help me understand how this can happen.  I am running a PNY GeForce 8600GT.

---

### Post by robn30 on 2012-01-16
Bump.  Anybody have any ideas.  Thanks.

---

### Post by MoreOrLess on 2012-01-16
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by robn30 on 2012-01-16
> **MoreOrLess said:**
> [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

Here is the information.
[http://www.alsa-project.org/db/?f=5f8b98ae20fa252739ce3c7bed5b4c5fb1be4e7f](http://www.alsa-project.org/db/?f=5f8b98ae20fa252739ce3c7bed5b4c5fb1be4e7f)

Thanks for the reply.

---

### Post by MoreOrLess on 2012-01-16
> Driver version:     1.0.24
Library version:    
Utilities version:  1.0.24.2


```
sudo apt-get install --reinstall libasound2
```

---

### Post by robn30 on 2012-01-20
I tried to install the driver again and no luck.  Here is the Alsa script once more.
[http://www.alsa-project.org/db/?f=13fa7b161525780120c6efd65b1a1ca4076d79d9](http://www.alsa-project.org/db/?f=13fa7b161525780120c6efd65b1a1ca4076d79d9)
Thanks.

---

### Post by robn30 on 2012-02-25
Ok so I have tried this Nvidia Driver install yet again and you guessed  it, the same result, broken sound.  I do have an update to report and  that is the front panel headphone does provide perfect sound.  Left and  right ear are perfect when I plug in headphones.  Its just the speakers  built into my Asus Monitor that will not work.  Of course they work  perfect before the application of the Nvidia Driver.  After reboot is  when the sound breaks.  This is such a mind boggling issue and really  frustrating.  Out of all the machines I have running Linux, this is the  only one with this issue.  I really wish I could get it squared away.   Next I am going to remove the Nvidia Driver and see if I have sound both  at the speakers and with headphones.  Hopefully someone can come up  with something that may help given this new data.  Thanks.

---

### Post by robn30 on 2012-02-25
> **robn30 said:**
> Ok so I have tried this Nvidia Driver install yet again and you guessed  it, the same result, broken sound.  I do have an update to report and  that is the front panel headphone does provide perfect sound.  Left and  right ear are perfect when I plug in headphones.  Its just the speakers  built into my Asus Monitor that will not work.  Of course they work  perfect before the application of the Nvidia Driver.  After reboot is  when the sound breaks.  This is such a mind boggling issue and really  frustrating.  Out of all the machines I have running Linux, this is the  only one with this issue.  I really wish I could get it squared away.   Next I am going to remove the Nvidia Driver and see if I have sound both  at the speakers and with headphones.  Hopefully someone can come up  with something that may help given this new data.  Thanks.

After  removing the driver I now have sound at both the speakers and the  headphones.  I should note that if I plug in the headphones I still have  sound at the speakers as well.  I just also hear it through the  headphones as well.  I am sure I can mute the speakers somehow with  alsamixer or something, but the short of it is the sound is working with  the Nvidia driver removed.  With the driver activated I only get  headphone sound.  Ok thats all I have, hopefully someone can help me  out.  Thanks again.

---

### Post by robn30 on 2012-02-26
Bump.  Any guru's out there who can finally put an end to this nonsense with my audio.

---

### Post by BicyclerBoy on 2012-02-26
Your video card supports pre-azalia HDMI audio (S/PDIF over HDMI).
To make this work you have to connect the mobo S/PDIF header to the video card (3 or 4 wire).

HDMI audio from the GPU requires the proprietary driver.
It is possible that the video card is outputting empty audio data packets & the monitor is switching to this..
Is your monitor connected by HDMI or DVI-HDMI adapter ?

---

### Post by robn30 on 2012-02-26
> **BicyclerBoy said:**
> Your video card supports pre-azalia HDMI audio (S/PDIF over HDMI).
To make this work you have to connect the mobo S/PDIF header to the video card (3 or 4 wire).

HDMI audio from the GPU requires the proprietary driver.
It is possible that the video card is outputting empty audio data packets & the monitor is switching to this..
Is your monitor connected by HDMI or DVI-HDMI adapter ?

Yes it is connected over DVI-HDMI.  The video card is a 8600GT, it doesn't have any audio capability to my knowledge.  The MB does not have HDMI out either.  My video card only has 2 DVI outputs and no HDMI.  You may need to explain more fully but clearly you are correct about something, especially with audio at the front panel headphone jack.  That at least tells me audio is not fully broke, something is just inhibiting the output to the speakers.

---

### Post by robn30 on 2012-02-26
Here is the exact card I have.  Link below.
[http://www3.pny.com/font-color9999998600-GT-Overclocked-512MB-PCIefont-P2547C396.aspx#Specifications](http://www3.pny.com/font-color9999998600-GT-Overclocked-512MB-PCIefont-P2547C396.aspx#Specifications)

---

### Post by BicyclerBoy on 2012-02-27
HDMI is just a cheap single link DVI-D with a different protocol specification (& licence fees).
DVI-D can carry HDMI audio.

If your card has a S/PDIF input then it can output 2 ch stereo & digital pass-thru' (AC3/DTS) only over HDMI (not HDA).

Some of the 8600GT have a S/PDIF input headersl, looks like a fan header.
I'm not sure if the video card will output 'empty' audio data with no connection to the S.PDIF header.

Have you tried using?
pavucontrol

There a comment about your mobo at the bottom page:
[http://alsa.opensrc.org/Hda](http://alsa.opensrc.org/Hda)

The MCP51 chipset has problems with "msi"; snd_hda_intel driver auto-disables it.
You could try adding to grub :
- pci=nomsi
- acpi=off

Did you ever try to disable the mobo sound in bios ?
And then plug in your soundcard ?

I'm glad I have the intel P45 chipset version of that mobo..

---

### Post by Yellow Pasque on 2012-02-27
> **BicyclerBoy said:**
> HDMI is just a cheap single link DVI-D with a different protocol specification (& licence fees).
DVI-D can carry HDMI audio.
If your card has a S/PDIF input then it can output 2 ch stereo & digital pass-thru' (AC3/DTS) only over HDMI (not HDA).
Some of the 8600GT have a S/PDIF input headersl, looks like a fan header.
I'm not sure if the video card will output 'empty' audio data with no connection to the S.PDIF header.

What are you talking about? There is no audio connected/detected on the 8600GT (not sure why OP even mentions the GPU).

> The MCP51 chipset has problems with "msi"; snd_hda_intel driver auto-disables it.
MSI is already disabled (look at the alsa info). I'm not sure how disabling ACPI helps either..

> Did you ever try to disable the mobo sound in bios ?
And then plug in your soundcard ?
The onboard/mobo sound IS the device the OP wants sound out of.

---

### Post by BicyclerBoy on 2012-02-27
Granted this is misleading..
But his monitor could detect HDMI audio stream & switch over.
I don't know any monitors that do this (some TVs do) but I don't presume...
His monitor speakers stop working with the nVidia driver.

The GPU is mentioned because when the nVidia driver is used the mobo audio stops working. 

What you you mean no audio detected on the GPU; pre-azalia does not work that way.
How do you know there is no audio connection to GPU?
Maybe the OP has the internal S/PDIF link cable fitted..

I explained that his HDMI audio (if possible) would be just S/PDIF from a soundcard (inc mobo).

I know msi is disabled by snd-hda-intel I already said just that & you quoted it....
but does this apply to all other MCP51 drivers &/or does it need to ?

I know the OP are trying to use mobo chipset sound..but..
The OP has tried to use a PCI soundcard previously..so this question was to find out if that option was exhausted.
It might still be a better solution.

I think trying a couple of grub boot options are :
- easy to try
- harmless
even if a long shot.

Maybe the OP just needs to find the right modprobe options to connect the I/O panel speaker jacks correctly.

---

### Post by robn30 on 2012-02-28
> **BicyclerBoy said:**
> Granted this is misleading..
But his monitor could detect HDMI audio stream & switch over.
I don't know any monitors that do this (some TVs do) but I don't presume...
His monitor speakers stop working with the nVidia driver.
 
The GPU is mentioned because when the nVidia driver is used the mobo audio stops working. 
 
What you you mean no audio detected on the GPU; pre-azalia does not work that way.
How do you know there is no audio connection to GPU?
Maybe the OP has the internal S/PDIF link cable fitted..
 
I explained that his HDMI audio (if possible) would be just S/PDIF from a soundcard (inc mobo).
 
I know msi is disabled by snd-hda-intel I already said just that & you quoted it....
but does this apply to all other MCP51 drivers &/or does it need to ?
 
I know the OP are trying to use mobo chipset sound..but..
The OP has tried to use a PCI soundcard previously..so this question was to find out if that option was exhausted.
It might still be a better solution.
 
I think trying a couple of grub boot options are :
- easy to try
- harmless
even if a long shot.
 
Maybe the OP just needs to find the right modprobe options to connect the I/O panel speaker jacks correctly.
 
I no longer have the Sound Blaster card installed as it would not produce sound either. I have not tried it in a while. I do not have anything connected to the Video card in the way of S/PDIF. Plus I am pretty positive that sound can't be passed over DVI->HDMI anyway. Obviously something is being disabled or rerouted but I don't know why. Like I said the front panel headphones work fine and I believe that is controlled by the MCP51 as well. I do not have any MSI components either. The MB is Asus and the video card is PNY. Being this card has 2 DVI and one S-video outputs, I would assume it has no audio capability. Lastly nothing in the write-up about the card says anything about audio. The link I posted is where I read up about the card. Thanks for the input, I really appeciate it. The more discussion the greater the possibilty of getting this solved. Thanks.
 
EDIT: Here is a link to the photo of the card.  I believe the connector on the top is for SLI.  i see no other connector for audio.
[http://img.ncix.com/images/26798_2.jpg](http://img.ncix.com/images/26798_2.jpg)

---

### Post by robn30 on 2012-02-28
Funny thing is I have a MSI 8600GT installed in a different machine with the Nvidia Driver activated and sound works perfectly fine.  Although I am not sure the video card has anything to do with this issue at all.  I am pretty sure it is the MB chipset that is the issue.  I wonder if the Nvidia Driver also modifies the MCP51 chipset somehow?

---

### Post by BicyclerBoy on 2012-02-28
With the risk of misleading you again...

[http://forums.nvidia.com/index.php?showtopic=155071](http://forums.nvidia.com/index.php?showtopic=155071)

Top left of your photo/picture; is that a missing header or just some SMD components?

msi is a TLA for message signalled interrupts; something the audio component of MCP chipsets have problems with..

For what's worth I agree with your assessment of the issue.
The video driver appears to be interfering with the chipset audio.
The driver probably has to modify the chipset configuration to function.
SLI ?

Your alsa info in post #4.. is this with the nVidia driver ?
The nouveau driver is listed in the loaded modules.
Historically (*buntu 10.04) the nouveau module had to be blacklisted.
I don't see the nVidia video driver..
The audio driver reports to be auto-setting the "enable_msi=0" option but there is no harm in setting this again.

When you tried the modprobe options for snd-hda-intel did you run
[sudo] update-initramfs -u
before rebooting ?
[http://www.kernel.org/doc/Documentation/sound/alsa/HD-Audio-Models.txt](http://www.kernel.org/doc/Documentation/sound/alsa/HD-Audio-Models.txt)

---

### Post by robn30 on 2012-02-28
> **BicyclerBoy said:**
> With the risk of misleading you again...

[http://forums.nvidia.com/index.php?showtopic=155071](http://forums.nvidia.com/index.php?showtopic=155071)

Top left of your photo/picture; is that a missing header or just some SMD components?

msi is a TLA for message signalled interrupts; something the audio component of MCP chipsets have problems with..

For what's worth I agree with your assessment of the issue.
The video driver appears to be interfering with the chipset audio.
The driver probably has to modify the chipset configuration to function.
SLI ?

Your alsa info in post #4.. is this with the nVidia driver ?
The nouveau driver is listed in the loaded modules.
Historically (*buntu 10.04) the nouveau module had to be blacklisted.
I don't see the nVidia video driver..
The audio driver reports to be auto-setting the "enable_msi=0" option but there is no harm in setting this again.

When you tried the modprobe options for snd-hda-intel did you run
[sudo] update-initramfs -u
before rebooting ?
[http://www.kernel.org/doc/Documentation/sound/alsa/HD-Audio-Models.txt](http://www.kernel.org/doc/Documentation/sound/alsa/HD-Audio-Models.txt)

ALSA info was with the driver installed.  Pretty sure there is no header there on the card.  It has been so long now that I can't remember exactly what I did with modprobe.  I may have to try and redo some of those procedures and see if anything happens to fix the issue.  I can't believe I am the only one with this issue.

---

### Post by BicyclerBoy on 2012-02-29
You can try the modprobe option directly in terminal.
sudo rmmod snd-hda-intel
sudo modprobe snd-hda-intel enable_msi=0 model=auto

There's only about 2 dozen to try..+ test..

Quoted from [http://www.kernel.org/doc/Documentation/sound/alsa/HD-Audio.txt](http://www.kernel.org/doc/Documentation/sound/alsa/HD-Audio.txt)
Some codecs such as ALC880 have a special model option `model=test`.
This configures the driver to provide as many mixer controls as
possible for every single pin feature except for the unsolicited
events (and maybe some other specials).  Adjust each mixer element and
try the I/O in the way of trial-and-error until figuring out the whole
I/O pin mappings.

---

### Post by robn30 on 2012-11-22
I still to this day have not figured out this issue.  Maybe resurfacing it in the forum may help to get more ideas on how to get this working.  Still the samething, as soon as I activate the Nvidia Drivers by way of the additional drivers search and reboot, no sound at all.  Except for the front panel headphone jack, it works.  The rear panel analog is a complete no go. It seems you have to be quite the Linux Driver Guru to work through issues such as this.  Unfortunately I am not one of those, I would love to be, but starting my Linux knowledge base so late in life doesn't help.  I am not a coder or programmer either so there is a large learning curve for me to succeed in the Linux Realm.  Luckily all my other machines have worked flawlessly, it is just this one desktop that is the problem.  It works fine as long as I don't install that Proprietary Driver.  Anyway I am open to more ideas to learn and to try and fix this.  Thanks as always.

---

### Post by robn30 on 2012-12-16
For the love of all things good, I need to fix this issue.  It is driving me nuts! I noticed that there were some new choices for Nvidia Drivers in the additional drivers GUI, so I selected the experimental 310 version.  Still the same issue, no sound!  I need to get this working and I know it is related to a driver configuration somewhere.  I don't know where to look anymore.  I am going to paste in my Alsa Config File and let you all inspect it.  I added the option snd-hda-intel model=auto but of course this did nothing to solve the problem.  Again I have a Asus P5NE-SLI MB with the MCP51 chipset.  It appears that this chipset is extremely problematic.  I have googled and googled to no avail.  Please for the love of my sanity, help if possible, this is the only Linux build that has ever failed of the 5-6 I have done.  Here is the Conf file---
# autoloader aliases
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
options snd-hda-intel model=auto


EDIT: Would moving to Ubuntu 12.10 yield any better results, Thanks.

---

### Post by robn30 on 2012-12-31
I have read in another post in a different forum that another person was having this same issue with a 8600GT Nvidia card as well.  It seems to be the Nvidia Drivers.  He said that using something other than DVI-->HDMI or HDMI fixes the issue.  Also he said as soon as he would unplug the DVI-->HDMI from his monitor the sound would begin working.  Seems that its an EDID and Nvidia Driver issue.  Is there any way I can force my system upon boot to send the audio to the analog back panel connector instead of Nvidia attempting to send it digitally over DVI-->HDMI?  I would assume this could be done through some configuration file but I am not experienced enough to know which one or how to do it.  So if someone could give me some advice or point me to the correct area to find the data, that would be much appreciated.  Thanks.

---

