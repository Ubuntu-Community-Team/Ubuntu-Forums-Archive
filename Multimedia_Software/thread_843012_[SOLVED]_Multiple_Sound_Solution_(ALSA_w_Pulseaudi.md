---
title: "[SOLVED] Multiple Sound Solution (ALSA w Pulseaudio)"
date: 2008-06-27
forum: Multimedia Software
---

### Post by markbuntu on 2008-06-27
[b] [SOLVED] Multiple Sound Solution (ALSA w Pulseaudio)
The 10,000 Page Guide to Sound Troubleshooting and Configuration for Hardy Heron 8.04 and Intrepid 8.10 and Jaunty 9.04[/b]

THIS GUIDE IS OUTDATED. There is some, but not much, help here if you are using Karmic Koala 9.10 but there are many links still active and you will learn a lot by looking through this. Much of the information here is no longer relevant and the OP has not been updated since May 2009, use it at your own risk.

Many thanks to everyone who participated and best regards,

mark

Pulseaudio is the sound server for Ubuntu Hardy and Intrepid and the new Jaunty. It will continue to be so for the foreseeable future. This guide is geared towards first getting your sound hardware working and then getting Pulseaudio set up properly. If you are using KDE4/Kubuntu Intrepid Phonon is replacing aRts as the sound server. Since Phonon is so new some functionality has not yet been implemented. There is a link below for using Pulseaudio to fill the gaps.

**If you are using Intrepid you must read this before continuing**
The sound scheme in Intrepid 8.10 is fundamentally the same as that in Hardy 8.04 with few exceptions. ALSA 1.0.17 is now installed with Intrepid so more hardware works out of the box. The PulseAudio Volume Control now has a Recording tab. The link for the Multimedia overhaul has been updated for Intrepid and works, use it to get the dvd decoders and other restricted codecs from the medibuntu repository, it will also update some packages you got with the ubuntu-restricted-extras package. Flash 10 is now included in the ubuntu-restricted-extras package for both 32 and 64 bit users. Many of the other links have also been updated for Intrepid. If you know of some other helpful links, please let me know and I will include them here. It has been reported that Skype now works out of the box with Intrepid so if you are having problems it is either with your Skype setup or something more fundamental.

If your sound sort of works I have written a little quick start guide here just for you:

**Quick Start Guide for Intrepid and Hardy**

[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

**KDE4 Phonon and Pulseaudio**
If you are using Intrepid with KDE4/Kubuntu and need Pulseaudio because you have multiple sound hardware devices or for any other reason

[http://ubuntuforums.org/showthread.php?t=1055591](http://ubuntuforums.org/showthread.php?t=1055591)

**Jaunty 9.04**
Jaunty is released with Pulseaudio 0.9.14. There is a Jaunty Sound Solutions guide here

[http://ubuntuforums.org/showthread.php?t=1130384](http://ubuntuforums.org/showthread.php?t=1130384)

**Pulseaudio 0.9.15**
 Pulseaudio 0.9.15 includes new hal detection for digital and other devices which is missing in 0.9.10-0.9.14, better bluetooth and HDMI detection/support and many other new features. It also includes an entirely new pavucontrol which is the Pulseaudio volume control. As soon as I can, I will write a guide for using it. Pulseaudio 0.9.15 also requires ALSA 1.0.19 which is also available through Luke's ppa. There are also packages for Intrepid and Hardy. Remember that these are experimental so it is possible that things will not work smoothly. You will be performing testing and bug reports are needed for any problems you encounter.

Discussion thread for Pulseaudio 0.9.15. (This thread is in Jaunty testing forum and is closed for new posts)

[http://ubuntuforums.org/showthread.php?t=1066212](http://ubuntuforums.org/showthread.php?t=1066212)

Luke Yelavich's PPA for Pulseaudio 0.9.15, also includes debs for ALSA 1.0.19

[https://launchpad.net/~themuso/+archive/ppa](https://launchpad.net/~themuso/+archive/ppa)


**The Ubuntu Sound Scheme**
If you are looking for a general explanation of the Ubuntu Hardy Heron 8.04/Intrepid 8.10 sound scheme, I have written a little something here for you:

[http://ubuntuforums.org/showthread.php?p=5931543](http://ubuntuforums.org/showthread.php?p=5931543)

**Introduction**
This guide begins with a short basic troubleshooting section followed by a more comprehensive hardware **Drivers** troubleshooting area that deals with specific solutions for your hardware. You can skip this if your sound basically works. Next is the **ALSA Trouble** section. This tells you how to restart ALSA without rebooting, how to reload ALSA completely, and how to obtain the latest ALSA version.

Following that is a **Other Hardware Issues** section on getting your Surround Sound and Digital output and multiple sound cards/devices USB and bluetooth stuff working. You should get your basic hardware and sound server set up properly first before doing anything here.

The **Sound Server Setup** section  is about setting up the system so all your sound applications will work together properly. it tells you what packages you need and how to use all those crazy sound setting applications scattered all over your menus.

Following that is some info on getting a few specific applications setup and working properly, network streaming, and some other technical details that most people can just skip over.

The last section is about **Ubuntu Studio and Jack**. If you are serious about recording or contemplating using Ubuntu for recording/performing, it is very important that you read this section.

One important piece of advice if you are going to get any use out of this guide, a lot of important information that you need is in the links.

*********************************************************************************************************************************
**Basic Troubleshooting**

**If you can hear anything**
If you can hear the login sound but all other sound is not working you should first try **Try This First** and **This may or may not work for you**. If you have sound in some applications but not others then you can skip all the way down to the **Sound Server Setup** section. Either way it means your sound driver is working, lucky you.

** If your sound stops**
If your sound is generally working Ok but after a while just fades out or stops and you are not doing anything in particular to make this happen, like installing updates or fooling around with the sound settings or the applications and sound returns like normal when you reboot, this seems to be a particular bug in the hda-intel driver or kernel problems with Intrepid so we must wait for it to be fixed and an update made available. You can avoid having to reboot by restarting ALSA and PulseAudio following the directions in **ALSA Trouble** below for now.

**If you sound goes missing after an update**
If you just got a bunch of updates and rebooted and your sound no longer works it is most likely because some or all of your sound setting have been reset from where you put them. If you remember how you had everything set up, reset what was changed. If you do not remember... first check your volume controls. Next, go to **Try This First** below. If you edited some file to get your sound working, check that and reedit as necessary. If you got an application update check its preferences or settings. If you are really lost just go through the guide again. You should also check that your users and root are members of the following groups which you can check in System/Administration/Users and Groups since these sometimes are removed with updates.
pulse
pulse-rt
pulse-access

** Scratchy, glitchy sound**
If you have an HDA-Intel device try turning up the PCM slider in the volume control. If PCM is set to 0 it makes the sound scratchy for some of those devices.

Otherwise if your sound is scratchy or stuttering you can edit these lines in the file /etc/pulse/daemon.conf to look like this
```

default-fragments = 5
default-fragment-size =25

```
There are also some sound cards/chips that can only be fixed with an ALSA upgrade so you may want to consider that if this does not work for you.

**If your sound works randomly**
If your sound works sometimes when you boot but not all the time this problem is very common when multiple hadware sound devices are present. Nvidia and ATI include HDMI devices in their gpus now so that means if you have one of them you have multiple sound devices. If you have a USB headset or speakers you have multiple sound devices. If you have a tv card you have multiple sound devices and of course, if you have a plug in sound card and a sound chip on the motherboard you have multiple sound hardware.  What happens is that the devices are on the PCI bus and are detected and assigned somewhat randomly. This means that sometimes your motherboard sound chip is detected first and becomes the default and sometimes the HDMI or your plugin sound card or some other device is detected first and becomes the default sound device. In any case, this is an issue with **Multiple Sound Devices** which is a section of this guide below so you should look in there for help.

**No sound at all**
There are many links here for specific sound cards/chips and the answer you need may not be in the OP so you should look through the entire thread if it seems to be relevant to your problem. You should also post in that thread instead of starting a new one if possible. (Starting a new thread just fragments information and makes it more difficult for people to find answers so please try to avoid that.) Posting in a running thread will push it the the top and more people will notice it and reply. Someone will be along to help you if they can so please be patient. If you get no answer after one day, it is OK to bump the thread.

If you still have no sound after going through this guide and all the relevant links, you should do a search either in these forums or with google for your specific sound card/problem because there is about a %100 chance that someone has figured out your problem already. You can also try looking in the Mandriva and Fedora and SUSE and Debian forums, there are many smart people there. If you still cannot find any help, it is OK to start a new thread. If you find any information somewhere else that you think others might need, please bring it back.

**Missing Volume Controls**
If you seem to be missing some items from the volume control in your panel ( the little speaker icon) you most likely just need to make them visible. Right click on the little speaker and choose Open Volume Control. Make sure the Device: xxxxxxxxxx is your hardware device. It should be something like
Device: HDA ATI SB (Alsa mixer) or Device: HDA Intel(Alsa mixer) or Device:C-Media 8768 (Alsa mixer) etc, in other words, a hardware device with an Alsa mixer.
Once you have the proper device selected click on Preferences down at the lower right. This will show you a list of check boxes. Check  all the items you want to appear in the volume control and close the box.

**Try This First**
Go to System/Preferences/Sound and switch everything except Default Mixer Tracks to ALSA or Pulse Audio. if you see ...HDMI... in Default Mixer Tracks, change it to your sound card/chip, Realtecxxxx or Emuxxx or ATI SB or HDA INTEL or something like that, anything but HDMI that is not Capture or Playback or OSS.

Right click on the speaker icon on the top panel and choose Open Volume Control. Click File/Change Device and make sure you have the correct device chosen. Go to Edit/Preferences and check the following boxes: Main, PCM, CD, PC Speaker, Mic, mic boost, mic capture, mic boost capture, etc. You may or may not have these and more. In the Playback tab make sure the sliders are up and there are no red x over the little speakers. In the Recording tab, do the same. In the Switches tab check any boxes marked mix, 3D control, mic boost, capture, etc. In the Options tab, make sure the Line in mode and Mic-on mode and any other option is like how you have your speakers plugged in. (Some surround sound outputs are also line in and mic inputs and can be switched here.) Make sure any SPDIF or IEC958 or External Amplifier boxes are unchecked. (With some sound cards/chips these will turn off your sound so for now leave them off.) Close that window, right click on the icon again and choose Preferences. Make sure the device listed in the box is your sound card and select Master. Close the window. Now left click on the speaker icon and move the slider all the way up.

Try to play something, Rythmbox is a good choice, so is totem or mplayer. (Firefox/flash is not such a good choice at this time since it may not be working for other reasons). If you still get no sound, read on.

**This may or may not work for you**
One easy way that some people have fixed their sound problems is by creating a new user in System/Administration/Users and Groups and then logging in with that. It seems the generic system defaults for new users are different from the initial user defaults that Ubuntu installs. You should try that first before resorting to some of the more drastic steps below, It is a simple thing to do and will make no changes to your system. And if it works, you will know it is just a user configuration problem and you can compare the hidden user default files in the respective home directories to find and fix the problems or just transfer your personal files to the new user directory.

If you still get no sound, get up and walk around for a minute, get something to drink. This could take a while.

OK, sit back down and start reading.

********************************************************************************************************************
**Drivers**
Drivers are low level software code that connects the hardware to the software operating system so applications can make use of it. The sound drivers live in the kernel which is the heart of the operating system. ALSA sound drivers are included in the installation.  New and updated hardware drivers for sound are generally provided through automatic updates and version upgrades to ALSA. This means that, for the most part, you do not have to worry about hunting down drivers and installing them yourself to get your hardware working. It can also mean that if there is no open source linux driver and your hardware manufacturer does not supply a proprietary one you could just be out of luck with your hardware but that is a pretty rare circumstance.

**Sound Cards/On Board Chips and other Devices**
If you want to find out if your sound card is supported by ALSA and other information you should try the ALSA Wiki ( According to the ALSA developers all usb compliant sound devices should work with no special setup.):

[http://alsa.opensrc.org/index.php/Main_Page](http://alsa.opensrc.org/index.php/Main_Page)

If you are having trouble determining which module or module option you need for your sound card the entire list of supported cards and options is already on your computer ( the driver directory where this file resides also has all sorts of miscellaneous information on specific sound cards/devices):

/user/share/doc/alsa-base/driver/ALSA-Configuration.tar.gz

**Getting Information from your Machine**
Much of the information you will need for further troubleshooting you will need to gather yourself from your machine. This will involve using a few very simple and easy commands from the terminal. Do not be afraid, just follow this guide here. It is written for total noobs.

[http://ubuntuforums.org/showthread.php?p=6628921](http://ubuntuforums.org/showthread.php?p=6628921)

**HDA sound chips**
snd-hda-intel
The Intel Hda sound chip is widely used and can be found on almost every desktop and laptop PC manufactured over the last few years. There are numerous versions of this chip and a zillion configurations that OEMs have made by programming them for their particular needs. This has created a nightmare for the driver writers since the OEMs are very lazy about publishing the details. Nevertheless the driver writers are forging on in the total pitch black using only sputtering candles to light their way and have come up with numerous options you can use to configure this driver for your particular machine. You should send them roses, or candy, or beer, or even just a thank you for taking on this near-impossible task. 

If you are having problems with the HDA card/chip on your laptop or aplay -l reports one of these:

HD Audio (ICH6, ICH6M, ESB2, ICH7, ICH8, ICH9, ICH10 ),
ATI SB, SB450, SB600, RS600,
VIA VT8251/VT8237A,
SIS966, ULI M5461
Many people have reported success with their problematic HDA sound problems by upgrading to ALSA 1.0.17, 1.0.18 or 1.0.19 and/or Intrepid 8.10 which includes ALSA1.0.17. You might want to consider one of these options if you continue to have difficulties after trying the following. If you have an ALC 861 or ALC 888 chip people have reported that ALSA 1.0.17 provides more switches and options than 1.0.16. if you experience very low volumes with your ICH8-10 you should consider upgrading. The drivers are being updated regularly and each release supports more chips/cards and options so if your card/chip or some option is missing from your current driver you should seriously consider upgrading. (Directions for that are in the ALSA Trouble Section below)

First, you should get some information from your machine. The section immediately above has a link to how to do that. Next, open this file with your file manager

/user/share/doc/alsa-base/driver/ALSA-Configuration.tar.gz

Scroll down to the Module snd-hda-intel section and, using the information you just got, look for your sound chip. If you are lucky you will find a listing for your particular machine. If not, at least you know which options are available for that chip. You can also look here which has a list by manufacturer I am trying to get together. If you fix your machine but it is not on any of the lists, please post there so we can add you to the list.

[http://ubuntuforums.org/showthread.php?t=1043568](http://ubuntuforums.org/showthread.php?t=1043568)

Once you find something that looks hopeful you need to get it into the /etc/modprobe.d/alsa-base file. Save it in a notepad. Open a terminal and copy this into it. In Jaunty the file name has been changed to alsa-base.conf to conform to configuration file naming conventions. 

```

sudo gedit /etc/modprobe.d/alsa-base

```
It will ask for your password and then open the file for you to edit. Add this to the end of the file
```

options snd-hda-intel xxxxxxxxxxxxx

```
Replace the xxxxxxxxx with  whatever option you want to use.
Reboot or restart alsa (directions for that are below in ALSA Trouble). If it works you should now have your sound working, YAY! If it doesn't you may need to try the other options until you find one that does, meh. You can also try this option which seems to work for some machines where the listed options fail.

```

options snd-hda-intel probe_mask=1

```
If you are having problems with headphone/speaker control with your HDA sound device you can try this thread:

[http://ubuntuforums.org/showthread.php?t=806620](http://ubuntuforums.org/showthread.php?t=806620)

**ALC1200**
If you have an ALC 1200 sound chip (ASUS P5QL-EM mobo) you need  ALSA 1.0.17 or 1.0.18 or 1.0.19 which there is a link to below.  Upgrade and add the following line to the end of the  /etc/modprobe.d/alsa-base file:
```

options snd-hda-intel probe_mask=1

```

**Nvidia HDA** 
If you have a new Nvidia HDA sound chip and it sounds scratchy, this is a known problem and is fixed in the 2.6.27 kernel( It is part of Intrepid so you may want to consider upgrading):

[http://ubuntuforums.org/showthread.php?t=925409](http://ubuntuforums.org/showthread.php?t=925409)

**Creative Soundblaster Cards**
Creative cards have been nothing but a big pain in linux forever. Creative has been completely unwilling to make any technical information about their cards available to driver the open source community so drivers have had to be reverse engineered. Creative has released a few proprietary linux drivers but these have proven to be generally unusable. Just recently, after the latest fiasco with their proprietary X-FI driver, Creative has thrown in the towel and announced that they will make technical information available so the open source community can write proper drivers. OSS4 has drivers for the X_Fi cards now but there is no ALSA driver included in the ALSA packages yet.

**X-FI**
If you are having problems getting your Creative X-FI card to work you can try the newest driver from creative, it seems to actually work for a few people:

[http://ubuntuforums.org/showthread.php?t=870001](http://ubuntuforums.org/showthread.php?t=870001)

Or you can switch to OSS4:

[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

[http://ubuntuforums.org/showthread.php?t=780961](http://ubuntuforums.org/showthread.php?t=780961)

Or you can recompile your kernel with a patch. To recompile your kernel and apply the patch (take extreme care doing this, recompiling a kernel is serious business and can break your system. Do not do this unless you are absolutely sure you know what you are doing):

[http://ubuntuforums.org/showpost.php?p=4823915&postcount=675](http://ubuntuforums.org/showpost.php?p=4823915&postcount=675)

The ALSA x-fi driver has finally been completed and will be released in the 2.6.31 kernel.

**Audigy**
If your Creative Audigy card is not giving you any sound, make sure the analog/digital check box in your sound mixer is unchecked. Updates seem to reset this switch regularly so keep this in mind.
 
** AWE64, SB16**
If you have dug out an old Soundblaster AWE 64 or SB16  ISA card and were wondering if you could get it to work

[http://ubuntuforums.org/showthread.php?t=1011516](http://ubuntuforums.org/showthread.php?t=1011516)

** ICE1712 **
If you have a sound card with the ICE1712 chip, like a M-audio Delta 44, M-Audio 2496, ST Audio Media 7.1 and others and are having trouble getting it working with pulseaudio you can try this:

[http://ubuntuforums.org/showpost.php?p=6449370&postcount=989](http://ubuntuforums.org/showpost.php?p=6449370&postcount=989)

**Cards that need firmware**
The following devices do not come with the software necessary for them to function (firmware) embedded into the device. It must be loaded each time the device is attached or turned on. Newer versions of ALSA should automatically load this firmware upon detecting the device but there are some exceptions...If you seem to have an unsupported device and are dual booting with windows one trick that people use is to boot up with windows and load the firmware and then soft restart the computer and boot into Ubuntu while leaving the device plugged in and powered up.
  
**MobilePre, Sonica. Ozone, Transit. Audiophile USB devices **
Firmware needs to be loaded into these devices before they will work properly. Here are directions for doing that for older devices(newer devices should work without needing to do this):

[http://ubuntuforums.org/showthread.php?t=846621](http://ubuntuforums.org/showthread.php?t=846621)

**Tascam US 122**
If you have a Tascam US122  you also need a firmware loader:

[http://ubuntuforums.org/showpost.php?p=6272809&postcount=3](http://ubuntuforums.org/showpost.php?p=6272809&postcount=3)

**EMU404**
If you have an EMU404 and it does not work chances are that it is an early model. If that is the case you are out of luck because there is no firmware loader for that card or any plans to make one. Later models should work without problems.Cards that will work have a hardware identifier 1102:0008. Cards that do not work have an identifier of 1102:0004. There is an ongoing discussion about this issue here

[http://ubuntuforums.org/showthread.php?t=768934](http://ubuntuforums.org/showthread.php?t=768934)

**Other Sound card and chip Drivers**
Most other sound cards and chips should work without any problems but if you are having problems getting you AC'97 chip or any other card or chip working, the file

/user/share/doc/alsa-base/driver/ALSA-Configuration.tar.gz

also contains many options for those. You can follow the directions in the HDA sound chip section to apply them. Of course, you need to replace snd-hda-intel with the name of the driver you are using. Many AC'97 chips can be made to work with the "quirk" options. 

*******************************************************************************************************************************
** ALSA Trouble**

If you are having problems with ALSA the first thing you should try is to reload the alsa drivers. In a terminal type:

```

killall pulseaudio

sudo alsa force-reload

pulseaudio -D

```

This is a temporary fix for many people who have problems with sound fading out or strange messages from ALSA caused by buggy drivers. More permanent fixes can only come from driver updates.

**Reinstalling ALSA**
It is also possible something has gone really wrong with the ALSA drivers or there is a problem with some configuration file that got messed up with all that fooling around from above. You can try purging and reinstalling ALSA.  (I recently had to do this after replacing my motherboard, the new on-board sound card was correctly detected but my existing pci sound card was not, weird...) 


(1) Remove the ALSA packages
```

sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils

```

(2) Reinstall the same packages
```

sudo apt-get install linux-sound-base alsa-base alsa-utils

```

Packages gdm and ubuntu-desktop are also removed in this process if you are using Gnome. They need to be reinstalled:
```

sudo apt-get install gdm ubuntu-desktop

``` 

If you are using xubuntu this will also happen to you
```

sudo apt-get install gdm xubuntu-desktop

```

(3) Reboot.

**Upgrading ALSA**

**ALSA 1.0.19 ** 

If you want or need to upgrade to ALSA 1.0.19 you can get the debs from Luke Yelavich's PPA which has packages for Hardy and Intrepid and Jaunty. The best way to do it is to add the ppa to your sources list and then use apt or Synaptic to install the packages. 

[https://launchpad.net/~themuso/+archive/ppa](https://launchpad.net/~themuso/+archive/ppa)


**Still no Sound**
If you still have absolutely no sound at all or the above did not seem to offer anything helpful for you, you can try these guides:

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

[https://wiki.ubuntu.com/DebuggingSoundProblems](https://wiki.ubuntu.com/DebuggingSoundProblems)

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

**************************************************************************************************************
**Other Hardware Issues**
A single sound card/chip providing stereo sound to a pair of speakers is no longer the model for computer sound. Surround Sound, digital output, HDMI, USB , Bluetooth, multiple cards, all are having an impact on the way people want sound to come out of their computers and the linux community has risen to the challenge.  This section is all about getting those things working with your Ubuntu. If your sound drivers are working and your sound server is set up properly these guides should work for you.

**Surround Sound**

Many sound cards/chips have configurable plugs that can be used for things like line-in or rear speaker outputs. You should check in the Volume Control/Options and /Switches that you have these correctly chosen and that your speakers are plugged into the proper plugs. If you are dual booting with windows take care because windows may configure your speakers even though they are in the wrong plugs.

If you are not getting surround sound but have some sound then try this:

[http://www.automaticable.com/2008-05-28/how-to-enable-surround-sound-on-ubuntu-hardy/](http://www.automaticable.com/2008-05-28/how-to-enable-surround-sound-on-ubuntu-hardy/)

If you have 2.1, 4.1. or 6.0 Surround Sound, or a custom configuration, try this guide:

[http://ubuntuforums.org/showthread.php?t=795525](http://ubuntuforums.org/showthread.php?t=795525)

If that doesn't work for you, you can try editing your /.asoundrc file like this:

[http://ubuntuforums.org/showthread.php?t=899139](http://ubuntuforums.org/showthread.php?t=899139)

**Digital Output**
Digital output has two different formats. S/PDIF and IEC958. The easiest way to get your digital output working is to just turn it on in your mixer by checking the box labeled S/PDIF or IEC958. You may have number of these boxes so you need to play around with them to find the ones that work for you. If you have a IEC958 or S/PDIF Capture box and you check that, it may direct your microphone to the digital output which will make it unavailable for recording so be careful with that. Some cards will disable the analog sound when digital is selected so be aware of that. These boxes may not appear in the Volume Control and so may need to be accessed directly in the mixer. I highly recommend the gnome-alsamixer for this (see below). If checking any of these boxes causes your sound to disappear, uncheck them. You also may need to reboot before these changes take place as some hardware configuration files are only read at startup.

Mplayer, has an option for AC3 passthrough. VLC has an option to use S/PDIF when available. These options will redirect the audio stream from these players directly to the digital output. Players without these options will use the digital outputs through the ALSA sound server and driver. Older versions of Mplayer have a bug that does not allow the release of the digital output when Mplayer is closed. This is fixed in later versions. More in depth information about getting digital output working with ALSA is available here:

[http://alsa.opensrc.org/index.php/DigitalOut](http://alsa.opensrc.org/index.php/DigitalOut)

**Digital Output and Pulse Audio**
If you are using Pulse Audio, you may have noticed that your digital outputs are unavailable to Pulse Audio. You can still control them in your alsa mixer and their use should not effect your use of Pulse Audio. If you would like to make them available in Pulse Audio, you can follow this guide:

[http://ubuntuforums.org/showthread.php?t=776958](http://ubuntuforums.org/showthread.php?t=776958)

NOTE: This problem is fixed with PulseAudio 0.9.15 which is just released. There is a PPA at Launchpad for rc1 for Jaunty testers (as of now, Feb11, it will not be included in Jaunty (meh). You also need ALSA 1.0.19. Luke Yelavich has provided the PPA. (It is Jaunty specific so will probably not work with Hardy or Intrepid due to dependency problems). There are links to the discussion thread and the PPA at the beginning of this guide in **Jaunty 9.04**
More on that soon....

**HDMI**
If you are trying to get your HDMI working with your ati card, you need the 8.9 or later driver, if you have an nvidia card, you need the update 177.78 or later. These have been reported to work by some desktop users and some laptop users, but not all so if it still does not work for you, you may have to wait for a later update. Check that the HDMI or SPDIF/IEC958 output is switched on in the ALSA mixer. HDMI may be in a separate section in alsa mixer or gnome-alsamixer if you have a pci card. Also, because these devices are not generally device 0 on the video card, they may have to be added manually to be used with PulseAudio. See the section immediately above for all that and more general digital output help.

** Multiple Sound Devices, Hardware **
Multiple sound devices are becoming more and more common these days. If you have a newer Nvidia or ATI graphics processor that includes HDMI output you have multiple sound device hardware. If you want to be able to control them you should look here. If one of them is HDMI you should also read the HDMI section directly above.

[http://ubuntuforums.org/showthread.php?t=922860](http://ubuntuforums.org/showthread.php?t=922860)

** USB Headsets, speakers, sound cards, etc**
Once you have Pulseaudio set up properly you can easily use your USB Headset/Headphones/Microphone and other USB audio device.
They should appear in the Input and Output Devices of the Pulse Audio Volume Control as something like:

ALSA PCM on front 2: (USB Audio) via DMA

You can right click on them to make them the default device, adjust the volume by moving the slider and mute them by clicking on the little speaker icon.  You can also move streams to or from them in Playback by right clicking on the stream and choosing move stream. You can make your usb device mic the default device by right clicking on it in the PA Volume Control Input Device section.

If the volume control for your usb headset is not working properly in the panel volume control or in your alsamixer (gnome-alsamixer included), more specifically when you move the slider the left one always goes to zero, this is a known bug and is being worked on. Meanwhile, you can use the slider in the PulseAudio volume control as it is not effected by this bug.

You can also use your usb device simultaneously with your sound card and other audio devices with the PA Device Chooser/Configure Local Sound Server/Simultaneous Output and check the "Add virtual output device for simultaneous output on all local sound cards" box. This will add a virtual simultaneous output device in Output Devices and you can select it in Playback, adjust the volume etc like any other device.

[b] Bluetooth[/b
The bluetooth problems with pulseaudio have finally been solved. While none of the required parts necessary to make this work are part of any current Ubuntu distribution *this is still good news.

*Requirements

*bluez 4.35 or later
*pulseaudio 0.9.15
*alsa 1.0.19
*Kernel 2.6.29
*gnome bluetooth 2.27.4

*Make sure module-bluetooth-discover is loaded in /etc/pulse/default.pa or the default.pa in your home directory if you are using one

If you are trying to use bluetooth with Hardy or Intrepid or Jaunty it is still somewhat of a work in progress. 

[https://help.ubuntu.com/community/BluetoothHeadset](https://help.ubuntu.com/community/BluetoothHeadset)

[http://wiki.bluez.org/wiki/HOWTO/AudioDevices](http://wiki.bluez.org/wiki/HOWTO/AudioDevices)

[http://forums.overclockers.com.au/showthread.php?t=694010](http://forums.overclockers.com.au/showthread.php?t=694010)


***********************************************************************************************

** Sound Server Setup**
The sound server is a critical part of the Ubuntu sound system. It is the interface between your sound using applications and the drivers for your sound card/chip. In Hardy 8.04 and Intrepid 8.10 and Jaunty 9.04 Pulseaudio is the default sound server. Unfortunately, Pulseaudio is not set up properly by default. This has caused untold amounts of trouble and heartache for many many Ubuntu users myself included. While this section appears to be very long and involved it is not really. A lot of it is just explanation about what you need, how things work, and how to use stuff, all in one place. You will have a much better understanding about how your sound works by reading it.

If you have already followed the Interpid Sound Solutions guide it is just a compressed version of this section so a lot of this will seem redundant.

Anyway, this section will help you to get your sound scheme set up properly for maximum usability.

** Multimedia**
If you are not able to play your mp3s or other formats, you can use the Synaptic package manager to get:

ubuntu-restricted-extras

This will get you the codecs for many formats and a bunch of other useful stuff like java and flash.

If you need a total multimedia overhaul follow this guide ( I alway do this immediately after any install):

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

Because some codecs are proprietary and not available through a general use license or their use or distribution is not allowed in all countries they are excluded from the regular Ubuntu repositories. But, you can get them from the medibuntu repositories so If you just want the plugins and w32codecs and libdvdcss2 to play restricted dvds and other proprietary formats follow this guide.

[http://ubuntutip.googlepages.com/multimediaubuntustep1](http://ubuntutip.googlepages.com/multimediaubuntustep1)
[http://ubuntutip.googlepages.com/multimediaubuntustep2](http://ubuntutip.googlepages.com/multimediaubuntustep2)

**Flash and java**
If you have flash9, you need to have
libflashsupport
to get your audio to work properly. If you have flash10 or higher, you do not need libflashsupport and should remove it. You should not need to do anthing like this if you are using Intrepid and got flash with the ubuntu-restricted-extras package. If you got flash from somewhere else you are on your own. If you are having problems with flash you can try installing libflashsupport anyway, it may help, it may make thing worse.

If you are using amd64 Hardy be sure to read the sticky guides at the top of the 64bit forum to get 32bit flash and java working. The ubuntu-restricted-extras package should set you up properly but if you are having problems with missing 32 bit libs or crashing etc.

[http://ubuntuforums.org/showthread.php?t=772490](http://ubuntuforums.org/showthread.php?t=772490)

[http://ubuntuforums.org/showthread.php?t=774956](http://ubuntuforums.org/showthread.php?t=774956)

**Multiple Application Sound Sharing**
It is assumed you are using Hardy Heron 8.04 amd64, i386, or Hardy UbuntuStudio8.04 i386 and amd64 or Intrepid. If you are testing Jaunty, it is somewhat different and subject to change so bear that in mind while you follow this guide. 

It is very unlikely that anything you try here will put your sound into an unusable state that cannot be easily remedied by you after you read this.

This has been tested on i386 and amd64 Hardy8.04, UbuntuStudio8.04.1 i386 and amd64, Intrepid i386 and amd64 Gnome2.2.1 and KDE4 and Intrepid UbuntuStudio. Jaunty testing is underway.I have an HDA ALC883 sound chip, a C-Media 8768 7.1 PCI sound card, a Plantronics USB Headset and a Logitec webcam and they all work all the time. I have 21 devices in my volume control. I just got a bluetooth dongle and headset and as soon as I figure them out I will provide an update in the bluetooth section. Things I have used and tested: amarok, audacious, rythmbox, xmms, ardour, hydrogen, rosegarden, vlc, mplayer, totem, miro, streamtuner, tunapie, firefox, opera, ZynAddSubFx,  Banshee, jackrack, soundrecorder, sound converter, timidity, beast, djplay, Qsynth, mixx, muse,.....and many many more.

**Restore Default Configurations**
Default sound configurations are of two types, system wide configurations and user configurations. . System wide configuration files are /etc/asoundrc and in /etc/pulse. The file etc/asoundrc is not normally necessary or included so it is OK if it is not there. It is used for setting up special configurations for system wide use. User configurations are hidden in the users home directory under ~ /.asoundrc and ~/.pulseThe files ~/.asound.rc and ~/.pulse/default.pa  are used for the same thing but per user. In general you will have a ~/.asoundrc file but no ~/.pulse directory since there is generally no need for per user settings for pulseaudio.

If you edited asoundrc to get your surround sound working and were successful, leave that part. If you changed the sample size and/or rate to eliminate stuttering in /etc/pulse/daemon.conf and it worked, you can leave those changes. If you have edited your pulse/default.pa for multiple sound card devices or used combine and it works, you can leave those parts alone too. Otherwise, if you have an etc/asoundrc file, rename it to asoundrc.back so it won't be used. If you have edited your ~/.asound.rc for any reason but those mentioned above, then you should reload the backup you saved. If you edited your etc/pulse/default.pa for equalizer support you should re-edit and comment those lines out for now, same thing if you have a ~./pulse/default.pa. You can try the other changes you made again once everything is working properly.

Keep the new libs and anything else you installed following this guide from psyke83 if you have already been there:
[http://ubuntuforums.org/showthread.php?p=4928900](http://ubuntuforums.org/showthread.php?p=4928900)

**Packages**
Check with Synaptic that these are all installed(You probably already have most of them. Some are specific to specific applications/servers, if you do not use these, they are not necessary. If you are not sure, get them anyway):

AlSA Packages (search alsa)

aconnectgui  (ALSA MIDI connection utility)
alsa-oss  (alsa wrapper for OSS apps)
alsaplayer-alsa  (PCM player for alsa)
alsa-utils  (command line utilities)
asoundconf-gtk  (choose default alsa sound card)
gnome-alsamixer (GUI alsa mixer for Gnome)
gstreamer0.10-alsa (gstreamer plugin)
xmms2-plugin-alsa (xmms2 plugin)
libasound2 (alsa libs and plugins)
libasound2-plugins (jack, OSS, pulseaudio plugins for libasound2)
libesd-alsa0 Enlightened Sound Demon (allows  multiple audio streams on one device, not really necessary)

PulseAudio Packages (search pulseaudio will find most of them)

audacious-plugins-extra (audacious plugin)
gstreamer0.10-pulseaudio (gstreamer plugin)
libao-pulse (libao plugin)
libpulse0 (client libraries)
libpulse-browse0 (client libraries)
libpulsecore5 (core services modules)
libpulse-mainloop-glib0 (client libraries)
padevchooser ( device chooser for setting up networking)
paman (PulseAudio Device Manager)
paprefs (Pulse Audio Preferences)
pavucontrol (Pulse Audio Volume Control)
pavumeter(Pulse Audio VU Meters)
pulseaudio( The Pulse Audio Daemon)
pulseaudio-esound-compat( Pulse Audio Esound drop in replacement for libesd for multiple audio streams)
pulseaudio-module-gconf (gconf module)
pulseaudio-module-hal (hal module, discover new sound devices via hal)
pulseadio-module-x11 (replace x11 bell/beep with PA sounds)
pulseaudio-module-zeroconf (Avahi, mdns, network help)
pulseaudio-utils (command line tools)
vlc-plugin-pulse (vlc plugin)
libsdl1.2debian-pulseaudio (plugin for sdl apps)

Many of the above user applications can be found in Applications/Sound and Video after they are installed, others are in System/Preferences. Others are command line programs that need to be run in a terminal or libs that you do not need to access or plugins available in or to applications. 

**Default Sound Card**
What we are doing here is routing the ALSA plugins and players through Pulse Audio so it can manage them. Some applications have an ALSA plugin but no Pulse Audio support so they go through ALSA to Pulse Audio and on to the ALSA low level sound device drivers. Contrary to popular belief this does not increase latency since pulseaudio adds zero latency but actually reduces it since applications sharing sound no longer need to go through dmix.

System/Preferences/Default Sound Card, ( this is asoundconf-gtk) choose Pulse Audio.

System/Preferences/Multimedia Systems Selector/Audio set Plugin to Pulse Audio.

System/Preferences/Sound, set all to Pulse Audio except Default mixer tracks which should be set to "your sound card" (i.e. ATI IXP (ALSA )mixer) probably the first choice 0. If you have more than one hardware device, choose the one you want to use/control. If you set your defaults to automatic some applications will bypass Pulse Audio and grab exclusive control of the sound card. We want to avoid this.

Reboot. If you are having trouble changing settings in Multimedia Systems Selector or Sound, reboot and then make the changes and reboot again. You need to reboot because some configuration files are only read at boot.

** Volume Control**
The Volume control is the little speaker on your top panel. If you left click on it you can adjust the volume. This can get a little tricky if you have more than one device. To choose the device to control right click on it and choose Preferences. This will open a little window where you can choose which device to control. You can also choose what sliders you want to control. You should select Master but you can play around with it to see what it can do.If you hold down the sift key you can select more than one control. If you want to control the volume with your multimedia keys you need to select the device in System/Preferences/Sound.

For now though, right click on the Volume Control on the Panel and choose Open Volume Control/File/Change Device and make sure it is set to the same device as in System/Preferences/Sound. Go to Recording if that section is available and put the capture slider up about 1/3 to 1/2 and make sure the icons on the bottom are not x-ed out. If available, go to to Switches and check mix. If you have an Options section, check to make sure they are set to the proper configuration for where your speakers and mic are attached. If you get feedback, mute the microphone, it is working just fine. If you do not have these sections, do not worry, they are not available for all devices. If you only have one hardware device to choose, that is also OK.

** Sound Mixer**
Open any alsa mixer, I use gnome-alsamixer. Turn stuff on and put up the sliders. check mix, capture, cd, mic, etc, unmute, mute, blah blah blah... If you have a usb mic or headphones tab over to that section and turn them on and set the levels etc. Some of this is redundant but it doesn't hurt and gets you familiar with your mixer.  This is the same controls as the volume control in your panel. If you adjust the sliders and switches they will adjust in every other volume control. 

**Pulse Audio Device Chooser padevchooser**
The Pulse Audio Device Chooser is a small applet that lives on your panel. From it you can open all the Pulse Audio interfaces, the Pulse Audio Manager and Pulse Audio Volume Control, the Pulse Audio Meters, and also Configure Local Sound Server and PulseAudio Preferences. You can put this in your panel by opening it from the Applications/Sound and Video menu and then clicking on Preferences/Start applet on session login. You can tell it to start up automatically when you login by choosing Preferences and selecting Start Applet on session login.

**Pulse Audio Volume Control, pavucontrol**
This is the control center for Pulse Audio. It has tabs as follows. You can find it in Applications/Sound and Video or open it from the Pulse Audio Device Chooser.
**Playback**
You can adjust the volume of the individual streams by moving the sliders, You can change which output device they use by right clicking on the stream and choosing move stream, 
**Output Devices**
You can set the default output device in the Output Device section by right clicking on it. This section also lists any Virtual Output Devices you have if you set Show: ALL Output Devices, like one for Simultaneous Output and one for RTP Multicast for network streaming or one for jack. You can select these in Playback just like any of your hardware devices.
**Input Device**
You can set the default input device in the Input Device Section by right clicking on it. You can set the Default Input Device to a monitor of one of the Output Devices so you can record what you are playing. You can set Show to All Input Devices of Show: Monitors to see the monitors.
**Recording**
This is new in Intrepid. It operates the same as Playback but for recording.

If you do not see an application playing in the Pulse Audio Volume Control then it is using the sound device directly. and is most likely an OSS or Jack or other type application. If you can, change their audio output to alsa or pulseaudio. OSS applications may need to be launched with aoss which is the alsa wrapper for oss . You can also try launching them with padsp which is the pulseaudio wrapper for OSS. Edit the launchers as necessary by putting either aoss or padsp before the application name. If it is a jack application, see the jack section below. If the application uses Portaudio or some other sound server then you may need to use the pasuspender command.

**Pulse Audio Manager, paman**
Go to Applications/Sound and Video/Pulse Audio Manager or use the padevchooser and you should see in Server Information:

Default Sink: alsa_output.pci_1002_4370_sound_card_0_alsa_playback_0
Defalt Source: alsa_input.pci_1002_4370_sound_card_0_alsa_capture_0

or something like that or completely not like that but with alsa as the first word.

All of your applications are listed in the Devices section of Pulse Audio Device Manager as #1, #2, #18 etc, under the line for what sink it is using. You can highlight one of them and click on properties to see what client/plugin it is using and other useful information. 

The PulseAudio Manager is being deprecated and will not appear in future versions of PulseAudio. It is not recommended to use the PA Manager for controlling PulseAudio. The padevchoser is also being deprecated so the Configure Local Sound Server will be found in PulseAudio Preferences along with the rtp network controls.

**Testing**
Test with Rythmbox, vlc, totem, firefox flash, firefox mplayer, and other plugins, etc. configure preferences to ALSA or Pulseaudio if available/possible. Play a cd or dvd or both. Run them all at once, or as many as you want/can. You should hear them all, together and see them in Pulseaudio Volume Control/Playback.

**Testing, Recording**
To control your input for recording you can set your System/Preferences/Sound/Audio Conferencing/Sound capture to PulseAudio Sound Server and use PulseAudio Volume Control/Input Devices to choose which device to record from. This is very handy as you can quickly switch between  your sound card pcm stream or microphone to your webcam mic or usb headset. All you need to do is open the PulseAudio Volume Control/Input Devices and right click on any available device to make it the default then open the application. You can choose any (ALSA) hardware device available or one of the "monitor" virtual devices. So, if you are listening to some music in your speakers you can choose the monitor for your Output Device to record. Just make sure that "capture" is enabled and turned up in the panel volume control or your alsa based mixer if you are trying to use a hardware input device.

If you are using Intrepid you can move the recording application to another Input device in the recording tab of the Pulseaudio Volume Control and adjust the levels, mute etc.

**PulseAudio Volume Meters**
You should now have a PulseAudio Volume Meter (capture) you can use to test your microphone or other capture inputs available in your sound mixer or volume control. Once you have chosen your default device, you can open sound recorder and record it. If you choose a monitor device, you can record whatever is going through the comparable Output Device.
You can use the PulseAudio Volume Meter (Playback) for monitoring playback streams. The volume meters work on the default streams.

If you are using a microphone for recording and wish to not hear the microphone input to prevent feedback, you can just mute the microphone playback in the panel volume control or ALSA sound mixer. It is the Capture settings that are the only important ones for recording.

If you are using jack this will not work for you. As far as I can tell you can only change jack inputs in jack control setup/input device and then restart jack. For using jack with PulseAudio, see the Ubuntu Studio and jack section below.

**Starting and Stopping Pulse Audio**
To start Pulseaudio from a terminal. 
```

pulseaudio -D

```
The -D option starts pulseaudio as a daemon so it is OK to close the terminal after using it to start Pulseaudio. 
If you want to kill the pulseaudio daemon:
```

killall pulseaudio

```

**Troubleshooting Pulseaudio**
If you are having weird problems using pulseaudio then you can kill pulseaudio and restart it from a terminal with
```

pulseaudio -vvv

```
This will run pulseaudio in the terminal in verbose mode so all the messages about what pulseaudio is doing will be written to the terminal. When you close the terminal Pulseaudio will exit. These messages can pinpoint problems with ALSA drivers or application plugins or network streaming issues etc along with problems with pulseaudio itself.
Bugs in pulseaudio can be reported by opening  new ticket. Make sure you search the tickets before filing a new bug. You can also talk to the devs at the mailing list or with IRC which have links from the home page:

[http://www.pulseaudio.org/](http://www.pulseaudio.org/)

**************************************************************************************************************************
**Application Specific Solutions and other misc info**
There are some applications that need specific configurations to work properly with Pulseaudio. In most cases these can be found in the Preferences or Settings menus. If available choose Pulseaudio or ALSA plugins. Applications using gstreamer will use the gstreamer defaults you set in Multimedia Systems Selector. You can set the xine defaults in the xine application.

For vlc set ALSA to default, for mplayer set audio to ALSA, for Audacious you can choose Pulseaudio Output Plugin. For Miro set the Preferences/Playback to gstreamer. Some people have have success choosing xine so you can try that too. In wine, try the OSS setting for audio and launch wine with padsp wine.

**Audacity, Wine, Skype and other troublesome applications**
There are some applications that have trouble working with Pulseaudio. This is usually caused by the developers who write the ALSA plugins  for these applications making assumptions about hardware or seeking to take control of it. Since the ALSA sound drivers have moved to the kernel this is no longer allowed due to security issues. Pulseaudio strictly enforces these rules. So, if you are having problems getting your application to work do not blame Pulseaudio.

Nonetheless, there is information about running specific applications including Audacity, Wine and others with Pulse Audio here and more info below:

[http://pulseaudio.org/wiki/PerfectSetup](http://pulseaudio.org/wiki/PerfectSetup)

**SKYPE and Pulse Audio **
Since so many people are having such a hard time getting their skype to work, I finally installed it and true, it does not work out of the box but the solution is fairly simple for Hardy and has been posted to here:

[http://ubuntuforums.org/showthread.php?t=937323](http://ubuntuforums.org/showthread.php?t=937323)

It has been reported by that Skype works out of the box with Intrepid but many also report problems ,mostly with getting their mic to work. If your mic is not working in skype, try to get it working in any other application first.

**A special note on Audacity**
Audacity was originally written for the Portaudio sound server which is not used in Ubuntu and many other major distributions anymore. The audacity developers have implemented plugins for alsa and oss and jack. While these plugins work in general with a standalone alsa or jack situation, they have bugs due to their non-standard implementation that causes them to not work in all circumstances or share the sound device properly with other applications in alsa, oss or jack and Audacity will not work at all with pulseaudio which enforces strict standard alsa protocols. We can only hope that they are working on these issues.

You can try compiling  Audacity yourself from source with jack support. This will allow you to use other jack applications and the jackrack effects etc with Audacity but will not give you full jack connection integration.

[http://ubuntuforums.org/showthread.php?t=982577](http://ubuntuforums.org/showthread.php?t=982577)

It has been reported that audacity now launches correctly with padsp audacity in Intrepid. There is a post around here about that,

[http://ubuntuforums.org/showthread.php?t=1005196](http://ubuntuforums.org/showthread.php?t=1005196)

If Audacity is giving you too many problems you should consider using ardour. It is a professional quality digital audio workstation fully integrated with jack ( it is written by the same people). For more information see ** Ubuntu Studio and Jack ** below

**Second Life**
I do not use Second Life myself so these links are getting a little old. If you are a Second Life user please let me know if this information is still valid or if it needs to be updated, otherwise this section will be deleted.

[http://vboards.stratics.com/showthread.php?p=836114](http://vboards.stratics.com/showthread.php?p=836114)

[http://jira.secondlife.com/browse/VWR-5708](http://jira.secondlife.com/browse/VWR-5708)

**xmms**
If you miss your xmms (not xmms2) and would like to have it back:
i386:

[https://launchpad.net/ubuntu/hardy/i386/xmms/1:1.2.10+20070601-1build2](https://launchpad.net/ubuntu/hardy/i386/xmms/1:1.2.10+20070601-1build2)

amd64:

[https://launchpad.net/ubuntu/hardy/amd64/xmms/1:1.2.10+20070601-1build2](https://launchpad.net/ubuntu/hardy/amd64/xmms/1:1.2.10+20070601-1build2) 

Beware of dependency problems with libglib1.2 and libglib1.2dbl on the amd64 build, i386 is no problem. You can read about that here:

[http://ubuntuforums.org/showthread.php?t=774461](http://ubuntuforums.org/showthread.php?t=774461)

Change the output plugin to alsa and you should be good to go.
These debs are also reported to work with Intrepid, give them a try.

** Streaming Audio Over a Network with PulseAudio**
If you are wanting to use PulseAudio to stream audio over your local or home network, it is very easy, you can use this guide here (this will not work for macs and windows boxes are difficult to setup this way):

[http://x4.6times7.org/dokuwiki/doku.php/devlog/blog/streaming_on_ubuntu_8.04_with_pulseaudio](http://x4.6times7.org/dokuwiki/doku.php/devlog/blog/streaming_on_ubuntu_8.04_with_pulseaudio)

**Streaming Audio to the Internet**

If you want to do local network music streaming to non-linux boxes or to the internet you can start here

[http://www.yolinux.com/TUTORIALS/LinuxTutorialAudioStreaming.html](http://www.yolinux.com/TUTORIALS/LinuxTutorialAudioStreaming.html)

For more technical information about Pulseaudio and about setting up surround sound and for network streaming, etc go here:

[http://pulseaudio.org/wiki/FAQ](http://pulseaudio.org/wiki/FAQ)

**Setting up a automatic PulseAudio server on startup**
If you have a media server and would like to set it up as a Pulseaudio server on startup then 13iggs has figured it out for you here. This is very handy if you have a headless server. 

[http://ubuntuforums.org/showpost.php?p=6869726&postcount=5](http://ubuntuforums.org/showpost.php?p=6869726&postcount=5)

Just be aware that setting up Pulseaudio as a system wide daemon is not especially recommended by the PulseAudio developers due to security concerns so take precautions like using the auth-ip... if you are running this on an open network.

**Pulse Audio Modules**
Pulse Audio loads its modules in etc/default.pa. You can edit this file to control which modules are loaded when Pulse Audio starts up. 

You can also load modules dynamically (while it is running) into the Pulse Audio daemon with the pactl command.
 
If your sound setup is being changed back to the wrong default settings every time you reboot, you can try this:

Look In etc/pulse/default.pa for the line:
```

load-module module-default-device-restore

```
comment this line out (put a # at the start of the line). Save the file. You will have to be sudo to do this. If you have a ~/.pulse/default.pa you can do it there for yourself as an individual user instead without being sudo.

You can find more info about the Pulse Audio modules here:

[http://pulseaudio.org/wiki/Modules](http://pulseaudio.org/wiki/Modules)

And about pactl here:

[http://linux.die.net/man/1/pactl](http://linux.die.net/man/1/pactl)


***************************************************************************************************

**Ubuntu Studio and Jack**
UbuntuStudio has three basic parts, audio, video, and graphics. This is about UbuntuStudio-audio exclusively.


Ubuntu Studio comes with the Jack Audio Connection Kit which is designed for one thing only, quality tools for professionals in the music business. This is a powerful utility that sits on top of the hardware drivers and provides connection and control services and real time priority for jack aware applications whose demands are time critical like for live recording and performance. With it you can synchronize playback and recording across multiple jack aware applications. One common use is to sync ardour with rosegarden and hydrogen for easy playback/recording of multiple midi and audio sources at the same time on multiple tracks. Jack and jack applications are used in many environments, from garages and basements to high end studios that charge $100s per hour, from internet DJs wth tiny audiences to live performance with audiences in the thousands. Jack performs, jack delivers.

If you are using jackd and are not using UbuntuStudio you should at least install: 
ubuntustudio-audio-plugins 
jackd (the jack daemon)
qjackctl (Jack Control)
jackeq (Jack EQ)
jack-rack(effects rack)
jack-tools(command line tools)
patchage (patchbay)
linuxrt (real time kernel)

**Getting UbuntuStudio**
If you want a real recording setup just get the ubuntustudio-audio and ubuntustudio-audio-plugins metapackages available in the repositories, ubuntustudio-audio includes jack and the rt kernel and all kinds of audio production applications. (It is a big download, took about an hour on my dsl connection.)

** Warning** Ubuntu Studio for Intrepid 8.10 has some serious problems with the rt kernel, among them are no support for multiple core cpus. It is strongly recommended that Ubuntu Studio users stay with or install 8.04 Hardy until these issues are resolved though many users have reported no problems with using Intrepid for sound mixing and editing.

If you are installing the rt kernel and are using the ati or nvidia restricted drivers that you downloaded directly from ati or nvidia, it is highly recommended that you remove these drivers from your system and replace your etc/X11/xorg.conf with the original generic version.  If you are not sure which file that is, copy the xorg.conf.failsafe file into xorg.conf. You can reinstall the driver after the rt kernel is working and should have no problems with it in Hardy or Intrepid. NOTE: The ati 9.1 driver build for Hardy is missing a patch for the rt kernel and so should be avoided by rt kernel users for now. There are scattered reports of similar issues with some nvidia drivers with certain nvidia cards. You can try these drivers, just be prepared to remove them and reinstall previous ones that worked.

If you are having basic jack setup problems, or you just want to know where to start:

[http://en.wikipedia.org/wiki/JACK_Audio_Connection_Kit](http://en.wikipedia.org/wiki/JACK_Audio_Connection_Kit)

If you are having trouble setting up jack in UbuntuStudio:

[http://en.wikipedia.org/wiki/JACK_Audio_Connection_Kit](http://en.wikipedia.org/wiki/JACK_Audio_Connection_Kit)

[https://help.ubuntu.com/community/UbuntuStudio/GettingStarted](https://help.ubuntu.com/community/UbuntuStudio/GettingStarted)

[http://hubpages.com/hub/Recording-in-Linux-aka-Free-and-Open-Source-Digital-Audio-Workstation](http://hubpages.com/hub/Recording-in-Linux-aka-Free-and-Open-Source-Digital-Audio-Workstation)

Excellent ardour tutorial here:

[http://out-of-order.nfshost.com/tutorials/ardour/](http://out-of-order.nfshost.com/tutorials/ardour/)

If you are wondering how to sync applications together through jack:

[https://help.ubuntu.com/community/HowToQjackCtlConnections](https://help.ubuntu.com/community/HowToQjackCtlConnections)

[http://www.ubustu.com/globe/2007/09/19/how-to-sync-hydrogen-with-ardour/](http://www.ubustu.com/globe/2007/09/19/how-to-sync-hydrogen-with-ardour/)

[http://www.rosegardenmusic.com/](http://www.rosegardenmusic.com/)

**Unlocking memory and setting priority for audio applications**
UbuntuStudio in Intrepid and Jaunty now comes with an UnbuntuStudio settings manager to control these options but if you are using previous versions... 
and you are getting memory limit or memory lock messages when running any audio application, try this:
Edit /etc/security/limits.conf and add or modify these lines

```

@audio - memlock unlimited
@audio - nice -10
@audio - rtprio 99

```


    * The 'memlock' line determines the amount of memory available to users in the group "audio". 
    * The 'nice' line, has to do with how long the processor will wait for processes queued from group "audio".
    * The 'rtprio' line assigns an extremely high priority to the group "audio".

The nice and rtprio settings will basically give your audio top priority at the cpu which is a necessity for live work.

** jack and Pulse Audio with more than one sound card**
If you have more than one sound card, you can configure jack to use one of them exclusively with Jack Control and set Pulse Audio to use the other one In the Pulse Audio Volume Control. They should both work at the same time if they are using different hardware devices and when you close jack, Pulse Audio can use that card again. Make sure you do not have any application using the Pulse Audio sink for the sound card you configured jack to use or jack will not start. 

Unless you are using professional quality sound cards that are made to share clocks, using two sound cards together can be problematic as their clocks/timing will drift apart. Pulse Audio, through the module combine can hold two cards in sync fairly well but some deviation is inevitable and glitches will occur as the clocks are periodically resynchronized. This is not a big problem with playback only but is not recommended for recording or live performance unless you have actually tested this with your hardware and are satisfied with it. I have not yet figured out how to get this to work with jack but it seems promising. If you have figured this out, please make a post.

** Pulse Audio through jack**
If you want to set up Pulse Audio to play through jack you can do so. This has been tested on Hardy 386, amd64 generic and Ubuntu Studio and on Intrepid 386, amd64 and Intrepid Studio ( it is from debian of course which is the base of Ubuntu).

First of all, you need to install the pulseaudio-module-jack from the debian lenny repository:

[http://packages.debian.org/lenny/sound/pulseaudio-module-jack](http://packages.debian.org/lenny/sound/pulseaudio-module-jack)

If you are using Jaunty 9.04 and you are using pulseaudio0.9.14, the pulseaudio-module-jack in Debian unstable has been removed so you will need to build it from source. It would be better if you upgraded to pulseaudio 0,9,15 which is much improved from Pulseaudio0.9.14 (which the pulse devs actually did not recommend for distribution use). There is a link at the beginning of this post to Luke Yelavich,s PPA for Pulseaudio 0.9.15 which also includes ALSA1.0.19 which you will need.

The pulseaudio-module-jack is no longer included in luke Yelavich's PPA for pulseaudio 0.9.15 so you need to get it from Debian sid

[http://packages.debian.org/sid/pulseaudio-module-jack](http://packages.debian.org/sid/pulseaudio-module-jack)

Download the appropriate deb by clicking on one of the mirror sites and install it with the gdebi package manager ( 386 and amd64 versions work for both Hardy and Intrepid).

Then you need to make a little script. I keep mine in a /scripts directory in my /home directory. Just make a new file with Natilus called jack_startup and make it executable and put these lines in it.

```

#load pulseaudio jack modules
#!/bin/bash

pactl load-module module-jack-sink
pactl load-module module-jack-source

```

Then start up jack control and go to Setup/Options/Execute script after Startup. click on the... box and go to where the script is and click open. and then after you make sure the path is correct click the box on the left so it has an x in it. Click OK at the bottom and make sure no application is using the sound card before you start jack or jack will not start. 

If the jack sink disappears from the Pulse Audio Volume Control after a few seconds or you do not see it, adjust the timeout in the jack control setup menu to 1000-5000. Applications that just play back audio streams through Pulse Audio are very lazy about talking to their sound server and this will prevent jack from timing out the connection. (Read the pactl and modules links above to change the default options which should work for most people. It has been reported that the m-audio 1010 card needs the channels=2 option)

You should now have jack sinks and sources in the Pulse Audio Volume Control and in the Volume Control on the panel. And a Pulse Audio JACK Sink and Pulse Audio JACK Source in the jack connection bay in the Audio section all connected up to system playback and system source automatically. When you close jack, the jack sinks and sources will automatically go away.
 
You can now start up any non-jack application and it will play through the pulseaudio-jack sink if you select it with move stream in the Pulse Audio Volume Control. And all your jack applications should work too, at the same time. You can connect the pulse audio sink to any jack application in the jack connections bay and record, add effects, eq, pretty much anything you want that jack can hook you up with. 

You can also route the mic/line inputs from the sound card by setting the jack control/setup/Input Device to the hardware device ie hw:0 or hw:1, etc. They will show up in the connections box as system capture inputs. You should hear them through the speakers. If you do not want to hear your mic in the speakers you can mute the mic input in the playback tab of your volume control and leave the captures on so you will still be able to record. If you have a usb mic, you can make that the default in the PA Volume Control and it will show up in jack/connections/audio/system capture and you will not hear it through the speakers unless you hook it to an output.

If you change the input, you will have to shut down jack, close jack control and restart. You will also have to make sure the input you are trying to use is properly enabled and turned up in whatever alsa-mixer you are using.

Now that you have pulse-jack working you can try these quick and easy fun projects to learn about using the pulse audio sinks and sources with jack:

[http://ubuntuforums.org/showthread.php?t=986966](http://ubuntuforums.org/showthread.php?t=986966)

**Closing jack**
If you close jack before you stop or close any application playing through the Pulse Audio jack sink, Pulse Audio may crash and need to be restarted if you do not disconnect the pulseaudio sink and source before closing jack. You can go to connections and choose disconnect all before stopping jack and your applications should not crash when you stop jack. 

**Jack and Pulse on one sound device**
If you have only one sound device your pulse applications may be orphaned when you close jack and their connection to pulseaudio may fail. You can try adding a null-sink and module-rescue-streams should move them to that when the jack sink closes and then they can be moved again when pulse regains control of the sound card. However, this does not seem to be a surefire thing and may not work for you so you may need to restart your pulseaudio applications after closing jack and after pulseaudio regains the sound device sink. There is a pulse audio module, module-always-sink, that would alleviate this problem but this module does not seem to be available in the Hardy and Intrepid pulse audio 0.9.10 but should be available in Jaunty which is using 0.9.14.

********************************************************************************************

If this guide doesn't work for you, or you would like me to add/subtract/edit it, post a reply. Also, please post if this works as is or if you had to change anything. 

Good Luck and best regards,
mark

---

### Post by maxxum on 2008-07-07
Thanks!
I was having constant sound problems on my 8.04 32 bit setup. Often after a reboot I would have no sound. I would get sound back if I monkey around with the sound preferences and switch it to all Pulse Audio. My hardware is realtek ALC885 (HDA Intel) on my Gigabyte EX38 motherboard (custom built PC). 
I do not have sound in flash as of now. In the past I would have sound either in flash or in everything else. At least right now it is working on everything else and not messing up on reboots. I have XP PRO installed in a virtual machine so everytime I want to see something in flash, I have to open it inside the virtual machine and I get sound then. 
Your guide introduced me to all these sound managers and mixers I didn't know existed. I was able to record sound in linux for the first time too. :)

---

### Post by fosix on 2008-07-07
really great! Thanks!

my soundcard is ASUS sigmaTel C-Major Audio and snd-intel8x0 of the laptop of ASUS M2N, the applications have been correctly installed according to your instruction, but there is no trace for me to see my soundcard in options of /pref.../sound or some default mixer tracks, I couldn't open /system/preference/default sound card.

could you please give some advice? Thank you very much!:confused:

---

### Post by markbuntu on 2008-07-08
Is the ASUS sound card recognized and enabled in the bios?

Did it ever make sound?

---

### Post by fosix on 2008-07-09
> **markbuntu said:**
> Is the ASUS sound card recognized and enabled in the bios?

Did it ever make sound?

I don't think the ASUS sound card was recognized, but I didn't check the bios and I never heard any sound.

Anyway, I have switched 8.04 back to 6.06, it works fine. 

Thanks for your help! for me the sound problem is too difficult, when the 8.10 is released, I will be glad to try.

---

### Post by eye208 on 2008-07-09
I just switched from 7.10 to 8.04.1 and immediately ran into the notorious Pulse Audio problem. On 7.10 all my applications used ALSA, except for Second Life which required ESD. ALSA and ESD clients worked perfectly side by side, so this setup was 100% trouble-free. SL voice chat, Skype, Flash, Totem, VLC, MPlayer, Blender, Audacity ... everything worked without any conflicts.

These are the steps to configure 8.04 the same way as 7.10:
[LIST=1]
[*]In System-->Preferences-->Sound, set all devices to ALSA (instead of Autodetect). Disable system sounds but leave software mixing enabled.
[*]In Synaptic, mark "esound" for installation and "pulseaudio" for removal. "pulseaudio-esound-compat" and "ubuntu-desktop" will automatically be marked for removal as well. Apply the changes.
[*]Reboot.
[/LIST]

---

### Post by t.rei on 2008-07-17
Thanks alot - this finally got me to be able to look into movies without turning my online-radio off. 

Now everything on my Asus A6000 is working like a charm - well, need to look into this firefox-crashing-on-some-embedded movies, but thats hardly something I desperately need. :)

---

### Post by Ed J on 2008-07-17
OK I can hear my sources all at the same time. I want to record them using Audacity.  I previously was using Ardour + JACK but couldn't get that to work as advertised, at least not without much difficulty and never the same way twice and/or without reboots/reconfig at terminal/wasting time. Since Ardour seems to only play nice with JACK I ditched it for now. I'm trying the Audacity + ALSA + PulseAudio approach.

PulseAudio record meters are indicating sound from my sources which are Hydrogen and a Line In.

I can hear everything on my soundcard when the above listed sources are providing input.

When using Audacity I cannot set the Preferences-> Audio I/O -> Playback or Recording selections to ALSA, Pulseaudio, or my desired soundcard, none of these options are listed.  My choices are:
OSS...
ALSA, Intel...(onboard sound, not desired)
JACK Audio Connection

Also I don't appear to boot into the right config, still working on that to.  When setting pulseaudio devices to default using Pulseaudio Volume Control, does that persist after a reboot? I'm about find out.  

Man I'm tired of rebooting. I want to jam.

Suggestions?

Ed

---

### Post by Ed J on 2008-07-17
Progress
After reboot I can make desired selections in Audacity. good

Default config appears correct. OK

Hydrogen and Line In both simultaneously record to Audacity. Now I'm getting somewhere (BTW Audacity is ver 1.3.4 Beta).

Attempting to playback Audacity while Hydrogen running (playing or not) caused Audacity to complain about drivers.

I think part of the problem is Hydrogen and Audacity both attempting to get control of ALSA. I can't select Pulseaudio as an input or output source in Hydrogen or Audacity.  In Audacity->Pref.."ALSA default" works for recording/playback. 

Using Pulseaudio volume meters for playback there is no movement yet I hear sound. Should I try a stable ver of Audacity and dump the Beta? Or is there some other magic?

I'm still not sure if this is going to work for me.  I'm not comfortable with pulseaudio as another software layer, thats what Pulseaudio appears to be. The problem is that my apps don't seem to recognize pulse audio so there is some gray area when configuring audio sources and playback destinations.  
I liked the principle behind JACK, I could see where I was "patching" audio. My apps "saw" JACK, know JACK, maybe they even love JACK. but it wasn't working 100% either.  JACK is another software layer but I have better luck with it. I'm going to reinstall ardour and give it another shot now that I think I have my default config working better.

Back to the front! Maybe I'll get to play guitar today.

Ed

---

### Post by markbuntu on 2008-07-17
Well, jack is a more direct control layer with very low latency for your time crtical apps like live recording etc. If you really want to use jack for that kind of stuff you need the real time kernel, linux rt. But many people have complaints about that and it is a whole other nightmare.

If you open the Pulse Audio Manager, you should be able to see if they are using pulse as they will be listed in devices as #3, # 18, etc. You can highlight one and click on properties to see which one it is, ie which plug in it is using, etc. If you do not see it, then it is using alsa directly.  In the devices property section you can also adjust the volume.

If the app is using PA, it should show up on both playback and capture Volume Meters. If you have

libesd-alsa0 Enlightened Sound Demon (allows multiple audio streams on one device)

and

alsa-oss should smoothly integrate anything looking for oss into your sound set up.

Then multiple streams in alsa should not be a problem but I have heard that the libasound2 in the repos has a few bugs and that may be you problem. There is a newer version available at launchpad but I can't find my notes right now about where it can be found. I think that is the one I am using and I seem to remember I got it from a link at the xmms site in launchpad.

The problem with hydrogen and audacity on playback may have to do with jack.

Yes, the default choice you make in PA Manager should persist.

---

### Post by Ed J on 2008-07-17
markbuntu Thanks for the help,
  I ended up going back to Ardour + JACK.  Its working good. Now I'm just creating a drum track in Hydrogen, exporting it to file, import that into Ardour and then start laying down tracks in Ardour.
  I open JACK (via qjackqtl) and leave it. When I start Ardour I open a new session, all default and move on. When I add a track in Ardour, JACK is automatically moving my inputs to the new track because Ardour is telling it to.  So I'm letting Ardour do the patching work for me.  Ardour and JACK were developed by the same guy so I assumed they would work together once configured and they are.
  Even when I did get something going with Audacity & PA it wasn't sounding that great anyhow.  That could be my PC, beta ver or bugs or who knows.  I'm recording, it sounds pretty damn good, done deal.  Now I'll start checking out plug-ins for effects and tweaking the sound.

Thanks again to markbuntu and everyone else posting in the forum/thread it helped me get to a happy place.

:guitar:

Ed

---

### Post by markbuntu on 2008-07-17
Yeah, I don't use audacity, it seems buggy to me as does pulse audio in general. That's why my guide basically pushes pulse off to the side and lets alsa do the heavy lifitng, which it should in my opinion.

---

### Post by markbuntu on 2008-07-31
I have made a few minor edits to this guide and added a link to a thread with a possible jack solution. ALso, I thought it could use a bump since I have run into a few recent threads linking to this from satisfied users.

---

### Post by atari130xe on 2008-08-01
> **eye208 said:**
> I just switched from 7.10 to 8.04.1 and immediately ran into the notorious Pulse Audio problem. On 7.10 all my applications used ALSA, except for Second Life which required ESD. ALSA and ESD clients worked perfectly side by side, so this setup was 100% trouble-free. SL voice chat, Skype, Flash, Totem, VLC, MPlayer, Blender, Audacity ... everything worked without any conflicts.

These are the steps to configure 8.04 the same way as 7.10:
[LIST=1]
[*]In System-->Preferences-->Sound, set all devices to ALSA (instead of Autodetect). Disable system sounds but leave software mixing enabled.
[*]In Synaptic, mark "esound" for installation and "pulseaudio" for removal. "pulseaudio-esound-compat" and "ubuntu-desktop" will automatically be marked for removal as well. Apply the changes.
[*]Reboot.
[/LIST]

Wow!!! guy! thank you very much! finally I got multiple sounds in my box!
After trying many many posts, these few lines, helped me a lot!
greetings :)

---

### Post by markbuntu on 2008-08-02
In Hardy, the PulseAudio devs have sneakily replaced esound with a link to PA. So, if you have mixing enabled, it will start PA.

---

### Post by Jokimoto on 2008-08-04
Thanks very much, markbuntu, nice tutorial
Unfortunately it didn't help with Skype, which stubbornly refuses to let any other application play sound when it's active. I wish I could do w/out it, but until other apps allow me to import skype contacts I'm stuck with it.
So, no music while on skype :(, but still you're tutorial helped me understand how things work a little better. Thanks again.

*also, regarding the above post from eye208: removing ubuntu-desktop just to get sound working, and disabling system sounds altogether, doesn't seem like the best solution. If you go to re-install ubuntu-desktop afterwards, it simply re-installs pulseaudio again, along with all those games i'd removed, etc.

---

### Post by sharad.sharma on 2008-08-04
Followed all those steps and now I have sound while using multiple applications!Thank you,Mark! :)

---

### Post by oeblio on 2008-08-05
Thanks eye208. I have been trying for months, without luck, to get sound from flash content on 8.04. This works and everything seems stable.
Youtube is my friend again.

 A happy bass player :guitar:




> **eye208 said:**
> I just switched from 7.10 to 8.04.1 and immediately ran into the notorious Pulse Audio problem. On 7.10 all my applications used ALSA, except for Second Life which required ESD. ALSA and ESD clients worked perfectly side by side, so this setup was 100% trouble-free. SL voice chat, Skype, Flash, Totem, VLC, MPlayer, Blender, Audacity ... everything worked without any conflicts.

These are the steps to configure 8.04 the same way as 7.10:
[LIST=1]
[*]In System-->Preferences-->Sound, set all devices to ALSA (instead of Autodetect). Disable system sounds but leave software mixing enabled.
[*]In Synaptic, mark "esound" for installation and "pulseaudio" for removal. "pulseaudio-esound-compat" and "ubuntu-desktop" will automatically be marked for removal as well. Apply the changes.
[*]Reboot.
[/LIST]

---

### Post by sharad.sharma on 2008-08-06
The 2nd step in the procedure above asks to remove the file etc/asoundrc.I do not have it there.Instead I found asoundrc in /home/username.
Do I remove it from there following those steps.I also the file .asoundrc.asoundconf there..Do I need to do anything with that?

I followed all those steps the first time without regard to those files.I got multiple applications to play sound simultaneously.
But the problem reappears at a random time again.
A restart solves it until the next time

please help.

---

### Post by markbuntu on 2008-08-06
If you do not have an etc/asoundrc it is not a problem. You shoyuld not remove your asoundrc.asoundconf, it is the default setups for alsa. If you need to change any of the defaults you would do so in either the etc/asoundrc for systemwide changes ( you would need to create this file) or in your~/.asoundrc for the user. Otherwise, you do not need them.

What exactly happens, no sound at all suddenly?
Which applications are running when this happens?
What does the PulseAudio Volume Control tell you the different streams are doing?
Are they there at all?
Are they playing?
Are they using the wrong output device?

You can use the PA Volume Contol to change each streams output device, just right click on the playing stream and choose move stream. You can also change the default output device in the Output Device section by right clicking on it.

Sometimes an application will cause PA to rapidly open and close devices until the number of devices it can support (about 800 I think) is exceeded and then it could stop playing any sound or freeze or even crash your system. Flash 9 does this to Pulse Audio and you can watch the device numbers flash up and up in the Pulse Audio Manager/Devices screen when flash 9 is playing without libflashsupport.

---

### Post by sharad.sharma on 2008-08-06
hey.. thanks for the information on those files
I switched from one user to mine and played Amarok.It said xine could not initialize audio drivers.No other application was running at that time apart from Pidgin.Then I checked if others could play any sound but they couldn't.
I could not even open System->Preferences->Sound.
Then a restart solved that. 
I didn't check pavucontrol. I'll do that and report here with the details the next time it happens.

---

### Post by Xhoonet on 2008-08-06
Hi I followed your guide and got all my media players audio to work simultaneously, which is cool, but now I got no sound from Firefox/Youtube!

Any pointers thanks!

---

### Post by markbuntu on 2008-08-06
Start up the Pulse Audio Volume Control. Look in the playback section and see if there is a listing for more than one device in Output Devices. 

Start up a you tube video and 
see if you get a listing in Playback like this:

ALSA plug-in[firefox]:Alsa Playback

If you do, right click on it and select move stream and move it to another output device.

If that stream is flickering on and off, you probably have flash 9 and need to get:

libflashsupport

from the repositories to get it to work properly. I highly reccomend trying to find flash10b. It solves a lot of problems with flash audio playback. If you get flash10b, get rid of libflashsupport, it will cause problems with flash10. Do not get flash10b2, it is very buggy at last report.

---

### Post by Xhoonet on 2008-08-06
Thanks it worked like a charm! I couldn't find the pulse audio thingy -another thread told me it is called "pavucontrol" and the flash flickered just like you said -installing libflashsupport it did the trick! Much appreciated!

---

### Post by markbuntu on 2008-08-06
If you followed my guide, the Pulse Audio Volume Control should be in Applications/Sound and Video. If you do not see it there, it is probably hidden and you can unhide it by using System/Preferences/Main Menu. It is a handy item for checking your sound players and adjusting their individual volumes.

---

### Post by Xhoonet on 2008-08-06
...and you are right, I kept going to System/Prefs of course it was not there

> **markbuntu said:**
> If you followed my guide, the Pulse Audio Volume Control should be in Applications/Sound and Video. If you do not see it there, it is probably hidden and you can unhide it by using System/Preferences/Main Menu. It is a handy item for checking your sound players and adjusting their individual volumes.

---

### Post by eye208 on 2008-08-07
> **Jokimoto said:**
> *also, regarding the above post from eye208: removing ubuntu-desktop just to get sound working, and disabling system sounds altogether, doesn't seem like the best solution.
Ubuntu 7.10 had no system sounds at all, because ESD was not included in the standard install. Most people didn't even notice. In Ubuntu 8.04 there are only two system sounds enabled by default: startup and shutdown. If you can't live without these, my solution is obviously not for you. However, my solution does make Skype work properly. The choice is yours.

There may be a way to make Gnome use ESD for system sounds again, but I didn't bother looking for it. My solution is the least intrusive one because it doesn't require editing system config files. And you can quickly revert to the old setup if required.

> If you go to re-install ubuntu-desktop afterwards, it simply re-installs pulseaudio again, along with all those games i'd removed, etc.
Umm yes, that's the whole point of ubuntu-desktop: to provide a quick way to restore the default setup. Otherwise we would not need it in the first place. In case you are suggesting to remove pulseaudio by hand without using the package manager: That would be wrong. It would leave the system in an inconsistent state, and subsequent updates to pulseaudio would most likely break it. **Not recommended!**

---

### Post by markbuntu on 2008-08-07
Your solution is is not a solution, it is a convenient work around that voids a lot of what the upgrade to Hardy is about. There are other solutions to your problems, they may involve a little more work, but they do not remove a big piece of the future of Ubuntu and of linux in general since many distributions have or are moving to pulseaudio.

Look at it this way, the entire linux community is moving to pulseaudio and you are missing the bus because you found some quick and easy way to get your skype working without even bothering to look at the wiki.

[http://pulseaudio.org/wiki/PerfectSetup](http://pulseaudio.org/wiki/PerfectSetup)

---

### Post by eye208 on 2008-08-08
> **markbuntu said:**
> Look at it this way, the entire linux community is moving to pulseaudio
No, it isn't.

Take a look at Kubuntu 8.04 and realize that PulseAudio is not a part of it. So far PulseAudio is only replacing ESD in GNOME, nothing else. It is far from replacing Jack, and it will never replace ALSA. In fact it needs ALSA.

This is not just about Skype. If you take a look at sound applications on Linux, you'll realize that almost all of them can talk to ALSA directly. So far I have come across only one app (Second Life) with buggy ALSA support, but it works fine with ESD. However it does _not_ work with Pulse which was advertised as a "drop-in replacement for ESD". Go figure.

It makes perfect sense to ditch PulseAudio until the developers make it work with everything out of the box. So far PulseAudio has achieved almost nothing. It did not introduce mixing of multiple streams; ALSA could do that anyway. It did not simplify using sound on Linux. It has only caused trouble and confusion for the majority of its users; just take a look at the polls and the bug trackers. Removing it from the system _is_ the solution.

---

### Post by markbuntu on 2008-08-08
The following distributions either have moved or are moving to pulse audio:

  * ArchLinux - has a nice Wiki page
    * Debian
    * Ubuntu (Enabled by default in Ubuntu 8.04.)
    * Fedora (Enabled by default in Core 8)
    * Gentoo
    * Lunar Linux
    * Mandriva (Enabled by default in Mandriva 2008.1)
    * OpenEmbedded
    * OpenSUSE Factory
    * FreeBSD 

That is over 90% of the installed linux base.

I have pulseaudio working just fine with my three sound cards and USB mic. I have even got pulse and jack to play nice together though on different sound cards. I will be experimenting later this weekend on a permanent solution to getting pulse to play through jack and use the same sound card in my UbuntuStudio installation. I have got pulse to play through both of the sound cards I use at the same time through a virtual device fairly easily. This is something I was never able to figure out with alsa, oss, or ESD.

Anyway, I know how you feel, pulse was driving me crazy for a while but I have got it figured out and now I am sharing what I learned and that is what this thread is about, figuring it out, not running away.

I have just updated the OP and there is a lot more information about how to use pulse and links to the pa wikis and other places of interest. I have added a section for jack that will be expanded as I uncover more information that I thnk will be useful. There is a link to getting skype and other troublesome applications working with pulseaudio.

---

### Post by markbuntu on 2008-08-09
OK, jack solution has been worked out and is now in the OP. Many changes have been made so you should check it out. It is now possible to run any application that uses pulse audio/alsa/oss through jack and connect it to any running jack application in the jack connections bay.

For example, you can now record streaming internet radio or a cd from Rythmbox with Ardour.

---

### Post by eye208 on 2008-08-09
> **markbuntu said:**
> The following distributions either have moved or are moving to pulse audio:

  * ArchLinux - has a nice Wiki page
    * Debian
    * Ubuntu (Enabled by default in Ubuntu 8.04.)
    * Fedora (Enabled by default in Core 8)
    * Gentoo
    * Lunar Linux
    * Mandriva (Enabled by default in Mandriva 2008.1)
    * OpenEmbedded
    * OpenSUSE Factory
    * FreeBSD 

That is over 90% of the installed linux base.
Don't confuse Linux distributions and the Linux community. 100% of existing distributions include Apache, but that doesn't mean everyone is running a web server.

PulseAudio is optional by design. It is designed to work as a plug-in for ALSA. The problem with PulseAudio in its current state is that it doesn't work. The majority of users don't have three sound cards in their computers. They have only one. And they expect it to work at least as well as it did in Windows. Anything less is considered a failure.

The fact that my solution works by removing the defective component doesn't mean your solution is better. It is just targeting a different group of users. My solution takes only 2 minutes to apply, is easily reversible, **and makes _all_ sound applications work**. You have to understand that some people (including myself) are looking for just that. We are not running away from PulseAudio. We will happily embrace a fully functional version of it with the next Ubuntu release.

There is a saying that goes like this: "Linux is free if your time has no value."

---

### Post by markbuntu on 2008-08-09
You are highjacking this thread and wasting my time.
This conversation with you is finished here.
If you want to continue, start your own thread.

---

### Post by leepesjee on 2008-08-09
If one things clear, than it's were all trapped in the same linux-sound mess. A quote as 'great, thank you, now i have sounds from multiple apps' shouldn't have a time-stamp of 2008, as the problem is technically solved years and years ago. And now it comes as far that were having flames over that one's solution to get out of the swamp is better than one's others. 

Ironically, the problem of linux-audio seems to be that there are too many (non-compatible) solutions to the same problem. And we cannot blame application developers for not keeping track of it all. So now we have to compile plugin xy to lead output of app X to sound server Y, and hack the configuration of Z and have another handy XYZ to make ik all work together.

I kinda symphatise with eye208's solution. Why bother with software you don't need and which is only giving you problems. It's really a mistake of Ubuntu (or is it gnome?) to step into this thing, given it's far from mature. It shouldn't be the standard setup, at least.
Don't know why, but is seems that linux-audio has a history of lobbying and politics. And the end is not in sight, as there are now people advocating the return of OSS in linux-audio (see i.e [http://insanecoding.blogspot.com/2007/05/sorry-state-of-sound-in-linux.html](http://insanecoding.blogspot.com/2007/05/sorry-state-of-sound-in-linux.html) ).

We have to give credits to Markbuntu for working out everything that is needed to connect all loose ends and let things play together, which is quite an achievement given - to quote the link above - the sorry state of sound in linux.
The bad news is that this all might be too much for the average linux starter. Taken first steps, choosen a distribution which (s)he's told is user friendly and just works.
Leo.

---

### Post by markbuntu on 2008-08-09
Thank you for the compliment. It was not so difficult to put this all together and I am very surprised that no one else has. It just took a little snooping around and a lot of bookmarks and free time.

I have only been using Ubuntu since April 25, the release date for Hardy. The last time I used linux was in the mid 90s kernel v0.9 something I think. You think things are hard now, try building a buggy kernel on a real 386 machine with a 13.3k modem as your only link to the outside world. this Ubuntu is a piece of cake and people should stop complaining about the FREE cake they are getting. I am not a software person or developer or anything like that. I am just a regular type person who would like to not be using windows.

There is nothing very difficult about my guide that a beginner would have too much trouble with. A few file system activities and some Synaptic work, no apt get remove install mumbo jumbo. What it is mostly is a compendium of information.

Anyway, a few comments on the state of things.
Systems progress abecause people want to do certain things that they find current solutions inadequate for and so a program gets written and then the api is not satisfactory so that gets changed too, and then the backend is not up to snuff so it is messed around with. Then someone wants some other features so that spawns a new program and api and then eventually, when enough bad code and crappy workarounds make the entire thing a mess the backend gets overhauled and the entire process starts again. It is an iterative process. It will never end.

I believe the reason for alsa was that oss had just accumulated a lot of bad code and workarounds so some people decided to start fresh and the reason for pulse audio is that, while the low level drivers in alsa are good, the api was beginning to become messy and too many workarounds and difficult changes would be necessary to do what the pulse devs wanted to do. So they wrote pulse to run on top of the alsa drivers and now I can record my streaming internet radio from Rythmbox into ardour/jack and put a deep echoing reverb onto it so it sound like I am in a endless tunnel.

We can at least be pretty well assured of three years of working sound now with Hardy. Besides, it has only been out for a few months and no organization, no matter how large, can test every piece of software on every possible hardware combination and actually release a product.

Anyway, I would like to thank all the people who made this possible, which is everyone here on these forums for providing timely and informative help to everyone who asks and all the people who took the time to write all those informative pages I have linked to It would have been impossible to do this without you.

---

### Post by eye208 on 2008-08-09
> **markbuntu said:**
> So they wrote pulse to run on top of the alsa drivers and now I can record my streaming internet radio from Rythmbox into ardour/jack and put a deep echoing reverb onto it so it sound like I am in a endless tunnel.
Some fun facts as a sidenote:

There is a JACK plug-in for ALSA. It works like the Pulse plug-in, with one exception: It connects to JACK instead of PulseAudio. Using this plug-in, every sound application appears as a JACK client. Anyone familiar with JACK knows what this means: unrestrained routing of sound between all applications. It lets you do all kinds of funny things, e.g. streaming internet radio from Rhythmbox into Ardour or JACK Rack and putting a deep echoing reverb onto it so it sounds like you're in an endless tunnel. You get the idea. You can also use the NetJack tool to transport audio over any IP network. Basically all the stuff that Pulse is promising to do when it's ready can be done with JACK _now_.

JACK has been around for years, so why are we now struggling with PulseAudio to do the same things? Why are we adding yet another API, yet another sound daemon, yet another level of complexity if all these features are redundant? I hear you ask. Well, the answer is in the [package description of "libasound2-plugins"](http://packages.ubuntu.com/hardy/libasound2-plugins):

> Note that in the Ubuntu package the JACK, a52, and Maemo plugins are disabled by default due to build component separation and cd image capacity issues.
Note that "libasound2-plugins" is the very same package that later included the Pulse plug-in. Apparently when it came to adding PulseAudio, all the previous CD image capacity issues suddenly disappeared.

---

### Post by motin on 2008-08-10
:guitar: :lolflag:

I have been waiting for this to work since Apr 2004... Last attempts where from Feisty through Hardy: [http://ubuntuforums.org/showthread.php?t=548178](http://ubuntuforums.org/showthread.php?t=548178)

By dynamically loading the pulseaudio sink after JACK startup this is finally working!

One smaller thing you may be missing in your guide however is to route OSS to JACK. A guide on the subject from a couple of weeks ago: [HOWTO: Install oss2jack on Ubuntu Hardy]("http://ubuntuforums.org/showthread.php?t=867329")

I needed it to be able to use [The Wiinstrument in Ubuntu]("http://ph.ubuntuforums.com/showthread.php?t=866322"), but it may come in handy for other older sound applications as well...

August 2008 is the timestamp for 24/7 JACK! Late is better than never... Hopefully the JACK pulseaudio module and this after-startup script gets into the default Ubuntu (at least Ubuntu Studio...) JACK setup.

> **eye208 said:**
> Some fun facts as a sidenote:

There is a JACK plug-in for ALSA. It works like the Pulse plug-in, with one exception: It connects to JACK instead of PulseAudio. Using this plug-in, every sound application appears as a JACK client. Anyone familiar with JACK knows what this means: unrestrained routing of sound between all applications. It lets you do all kinds of funny things, e.g. streaming internet radio from Rhythmbox into Ardour or JACK Rack and putting a deep echoing reverb onto it so it sounds like you're in an endless tunnel. You get the idea. You can also use the NetJack tool to transport audio over any IP network. Basically all the stuff that Pulse is promising to do when it's ready can be done with JACK _now_.

JACK has been around for years, so why are we now struggling with PulseAudio to do the same things? Why are we adding yet another API, yet another sound daemon, yet another level of complexity if all these features are redundant? I hear you ask. Well, the answer is in the [package description of "libasound2-plugins"](http://packages.ubuntu.com/hardy/libasound2-plugins):

Note that "libasound2-plugins" is the very same package that later included the Pulse plug-in. Apparently when it came to adding PulseAudio, all the previous CD image capacity issues suddenly disappeared.

Are you referring to the ALSA JACK sink? I think most of us have tried that approach, but it only works with some applications. PulseAudio through JACK means that all applications that works with pulseaudio works with JACK. Finally!

---

### Post by eye208 on 2008-08-10
> **motin said:**
> Are you referring to the ALSA JACK sink? I think most of us have tried that approach, but it only works with some applications.
The ALSA JACK sink and the ALSA Pulse sink are implemented in the same way. Applications can either use both or none of them.

The problem is that Ubuntu does not provide the JACK sink.

> PulseAudio through JACK means that all applications that works with pulseaudio works with JACK.
"Applications that work with PulseAudio" is the critical part here.

---

### Post by motin on 2008-08-10
> **eye208 said:**
> The ALSA JACK sink and the ALSA Pulse sink are implemented in the same way. Applications can either use both or none of them.

The problem is that Ubuntu does not provide the JACK sink.


I installed it from Debian but ran into several problems when using it as the default sink. It didn't work very well for me at least. 

> **eye208 said:**
> "Applications that work with PulseAudio" is the critical part here.

Indeed, but at least all of my important applications does. Haven't come across any that doesn't yet. As for OSS, see below:

> **motin said:**
> One smaller thing you may be missing in your guide however is to route OSS to JACK. A guide on the subject from a couple of weeks ago: [HOWTO: Install oss2jack on Ubuntu Hardy]("http://ubuntuforums.org/showthread.php?t=867329")

I just realized that oss2jack is not necessary. Just install jacklaunch from the repositories instead:

```
sudo apt-get install libjackasyn0
```

Then run your OSS applications using it, for instance:
```
jacklaunch ./wiinstrument
```

So much hassle writing the oss2jack-guide for nothing :P Glad there was an easier solution though!

---

### Post by markbuntu on 2008-08-10
> **eye208 said:**
> Some fun facts as a sidenote:

There is a JACK plug-in for ALSA. It works like the Pulse plug-in, with one exception: It connects to JACK instead of PulseAudio. Using this plug-in, every sound application appears as a JACK client. Anyone familiar with JACK knows what this means: unrestrained routing of sound between all applications. It lets you do all kinds of funny things, e.g. streaming internet radio from Rhythmbox into Ardour or JACK Rack and putting a deep echoing reverb onto it so it sounds like you're in an endless tunnel. You get the idea. You can also use the NetJack tool to transport audio over any IP network. Basically all the stuff that Pulse is promising to do when it's ready can be done with JACK _now_.

JACK has been around for years, so why are we now struggling with PulseAudio to do the same things? Why are we adding yet another API, yet another sound daemon, yet another level of complexity if all these features are redundant? I hear you ask. Well, the answer is in the [package description of "libasound2-plugins"](http://packages.ubuntu.com/hardy/libasound2-plugins):


Note that "libasound2-plugins" is the very same package that later included the Pulse plug-in. Apparently when it came to adding PulseAudio, all the previous CD image capacity issues suddenly disappeared.

Thank you, I will look into the libasound2-plugin situation and add the information to the guide if it works and I can figure out how to explain it in a simple manner. I do not have the time right at this moment. 

The reason for doing this with pulse is because it is there and I would like to get it to work. 

If you know of any way to get multiple sound cards to work in jack at the same time without some kludgy work around I would appreciate if you could point me in the right direction. I found a site for getting two m-audio 1010 boards to work together and another that involves wiring the clocks of identical cards together but not much else.

Right now, the only way I can find to do multiple sound cards is with pulse.

I have 3 sound cards and use 2 of them all the time. It is nice to be able to just click between them and use them both at the same time, which I do, a lot.

---

### Post by markbuntu on 2008-08-10
> **motin said:**
> :guitar: :lolflag:

I have been waiting for this to work since Apr 2004... Last attempts where from Feisty through Hardy: [http://ubuntuforums.org/showthread.php?t=548178](http://ubuntuforums.org/showthread.php?t=548178)

By dynamically loading the pulseaudio sink after JACK startup this is finally working!

One smaller thing you may be missing in your guide however is to route OSS to JACK. A guide on the subject from a couple of weeks ago: [HOWTO: Install oss2jack on Ubuntu Hardy]("http://ubuntuforums.org/showthread.php?t=867329")

I needed it to be able to use [The Wiinstrument in Ubuntu]("http://ph.ubuntuforums.com/showthread.php?t=866322"), but it may come in handy for other older sound applications as well...

August 2008 is the timestamp for 24/7 JACK! Late is better than never... Hopefully the JACK pulseaudio module and this after-startup script gets into the default Ubuntu (at least Ubuntu Studio...) JACK setup.



Are you referring to the ALSA JACK sink? I think most of us have tried that approach, but it only works with some applications. PulseAudio through JACK means that all applications that works with pulseaudio works with JACK. Finally!

If you notice, the title of my guide does not mention OSS. That is because I have not even begun to investigate that situation.

Thanks for the link, I will start there on the quest for OSS to join the title.

Have to go now, brunch with mum.

---

### Post by motin on 2008-08-11
> **markbuntu said:**
> If you notice, the title of my guide does not mention OSS. That is because I have not even begun to investigate that situation.

Thanks for the link, I will start there on the quest for OSS to join the title.

Have to go now, brunch with mum.

Ok great! Don't forget my follow-up reply:

> **motin said:**
> I just realized that oss2jack is not necessary. Just install jacklaunch from the repositories instead:

```
sudo apt-get install libjackasyn0
```

Then run your OSS applications using it, for instance:
```
jacklaunch ./wiinstrument
```

So much hassle writing the oss2jack-guide for nothing :P Glad there was an easier solution though!

---

### Post by markbuntu on 2008-08-11
I,m sorry, I did not see that. Anyway, it is great news. The other way in the link you gave me seemed far too intimidating to put in my guide but I will give this jacklaunch/libjackasyn0 a try and then probably add it in the jack section. 

I was pretty sure there was a way to run OSS apps directly in jack, they have both been around for so long it seemed almost impossible that someone had not made some easy way to do it.

It turns out someone has figured out an easy way to do most anything in linux/Ubuntu, the hardest part is always finding where the information is.

---

### Post by markbuntu on 2008-08-11
Update bump.
EDIT:08/11/08 Added Getting Started Section with links for no sound, codecs, etc. Tested on UbuntuStudio amd64 now, major jack section edit, added jacklaunch for OSS, crash warning for pulse through jack, rt kernel warning, other minor edits.

REQUEST: If anyone can point me to a definitive guide for getting soundblaster and other problem cards to work in a quick and easy manner, or other specific cards/issues that have been fixed, I would greatly appreciate it.

I am working on an addendum to the guide and would like to include as much "extra information" for specific items as possible. I am trying to get together a one stop shopping thread for sound issues, any help would be appreciated. 

I want to keep the guide itself focused on the more general issues but I see there is a pressing need to accumulate, in one place, answers, or more likely, links to answers for the many specific problems people are encountering.

(kudos will flow like water.)

---

### Post by motin on 2008-08-12
[Comprehensive Sound Problem Solutions Guide]("http://ubuntuforums.org/showthread.php?t=205449")

Maybe you should instead put all general sound related instructions there and focus on the ALSA + PulseAudio + JACK combination here?

---

### Post by markbuntu on 2008-08-12
motin,

That thread is very good and I have a link to it from the OP but it also does not address a number of specific problems. Also, it is extremely long and sifting through it for just the right answer is a very time consuming and tedious process. I do not control that thread so there is not much I can do there and if I did post, it would quickly become buried. I feel I cannot accomplish the goal there.

My idea would be to keep the OP in this new thread updated regularly as newer and easier and more complete fixes for peoples problems become available. This would be  mostly links with only a few specific issues actually adressed in the OP. A sort of clearing house for sound problems.

I fully intend to keep this thread focused on the more general issues of getting multiple applications and the sound servers working together in Ubuntu and that is why the new thread is important, it would do the same thing but for hardware. 

I have accumulated a lot of information and links on hardware fixes and configurations and a bunch of miscellaneous info on using and getting stuff that would be useful to a lot of people but I feel it would just clutter up the OP which is getting pretty long as it is.

One thing I would like to add to the OP would be a good OSS section but that is about it for additions.

Anyway, thanks for giving this your atttention and if you come across any more useful stuff, feel free to let me know about it.

---

### Post by carlinuxlearner on 2008-08-13
@ eye208

        How exactly did you uninstall pulseaudio and not ruin everything? If I uninstall it, it forces me to uninstall ubuntu-desktop (which is uh, kind of "essential") and then I don't have any menus and I can't run anything in X. (kills the whole point of fixing audacity)

C@RL

---

### Post by eye208 on 2008-08-13
> **carlinuxlearner said:**
> How exactly did you uninstall pulseaudio and not ruin everything?
[http://ubuntuforums.org/showthread.php?t=885437](http://ubuntuforums.org/showthread.php?t=885437)

> If I uninstall it, it forces me to uninstall ubuntu-desktop (which is uh, kind of "essential")
"ubuntu-desktop" is a package without any content. Its only purpose is to define Ubuntu's default software setup. Think of it as a system restore point. Whenever you remove something from the default setup, "ubuntu-desktop" will be removed as well *so that you can restore the original setup simply by reinstalling "ubuntu-desktop"*. That's the point of it.

> and then I don't have any menus and I can't run anything in X.
You forgot to disable system sounds before removing PulseAudio.

---

### Post by toemos on 2008-08-13
> **markbuntu said:**
> System/Preferences/Default Sound Card, ( this is asoundconf-gtk) choose Pulse Audio.

When i try to open asoundconf-gtk i get this error

```
You need to make sure asoundconf is active!
By default, asoundconf's configuration file is ~/.asoundrc.asoundconf
and must be included in ~/.asoundrc. Open this file to make sure it is!

```

from what i can see, it is already included in the asoundrc file...
where am i going wrong?

---

### Post by carlinuxlearner on 2008-08-14
@ eye208

Thanks, got it working.

C@RL

---

### Post by markbuntu on 2008-08-14
In your home/username/.asoundrc file the only uncommented line should be:

</home/username/.asoundrc.asoundconf>

Have you tried rebooting before trying to open Default Sound Card?

---

### Post by motin on 2008-08-14
> **markbuntu said:**
> motin,

That thread is very good and I have a link to it from the OP but it also does not address a number of specific problems. Also, it is extremely long and sifting through it for just the right answer is a very time consuming and tedious process. I do not control that thread so there is not much I can do there and if I did post, it would quickly become buried. I feel I cannot accomplish the goal there.

My idea would be to keep the OP in this new thread updated regularly as newer and easier and more complete fixes for peoples problems become available. This would be  mostly links with only a few specific issues actually adressed in the OP. A sort of clearing house for sound problems.

I fully intend to keep this thread focused on the more general issues of getting multiple applications and the sound servers working together in Ubuntu and that is why the new thread is important, it would do the same thing but for hardware. 

I have accumulated a lot of information and links on hardware fixes and configurations and a bunch of miscellaneous info on using and getting stuff that would be useful to a lot of people but I feel it would just clutter up the OP which is getting pretty long as it is.

One thing I would like to add to the OP would be a good OSS section but that is about it for additions.

Anyway, thanks for giving this your atttention and if you come across any more useful stuff, feel free to let me know about it.

What about organizing and maintaining a corresponding page on the Ubuntu Wiki instead? That way we can all help maintain and add to the guide, and we need not to duplicate contents.

---

### Post by markbuntu on 2008-08-14
> **motin said:**
> What about organizing and maintaining a corresponding page on the Ubuntu Wiki instead? That way we can all help maintain and add to the guide, and we need not to duplicate contents.

Well, that is a great idea and you are welcome to drop my entire guide into a wiki at Ubuntu Wikis and edit it and add to it however you please if you would like to do so. So is anyone else for that matter.

I can't really make any sort of commitment to doing that myself. These past few months I have had a lot of free time to do this but commitments are looming in my future that may take me away. I know nothing about building/maintaining WIKIs. But I will see what I can do.

Someone needs to flesh out this idea and come back here with a report on our options. Or find the right WIKI ripe for invasion or maybe just a friendly takeover.

Do we have any volunteers?

---

### Post by markbuntu on 2008-08-18
Update Bump.

---

### Post by dorite on 2008-08-24
I'm running a Dell with a motherboard sound card.  Sound died for me when I upgraded from 7.10 to 8.04.1.  

@eye208:  Your "put this in, take that out" instructions were enough to get sound working for me (sound died when I upgraded from 7.10 to 8.04.1).  Thank you.

@markubuntu:  When I have time and need to understand how sound works and want to strive for perfection, your detailed analysis will be most helpful.  Thank you for your work.

---

### Post by athianos on 2008-08-27
First things first, thank you!

To have a pulse into Jack solves many problems for me. 

I've followed your instructions and am pleased to say that Jack can see Pulse and vice versa.

Trouble now is with the microphone inputs. 

Everything is unmuted and at good volume. I've tried many variants of defaults between ALSA and Pulse. 

I have two microphone inputs. 1 is through my USB internal Webcam. The second is a microphone input next to my headphone socket. (I'm trying not to use the word JACK there because this is confusing enough as it is...!)


When I try to record in Ardour via Pulse and Jack, there is no input at all, although the input meter registers about half way.
When I test the microphone in preferences>sound I find that only two selections work, Pulse or Alsa, and all I get from either is a crackling buzz that changes mildly when I change the settings but in a way apparently unrelated to the volume or input I send through the mic. 

I have skype set up to killpulseaudio on launching and to use the USB camera mic. These settings still work after the changes I have made using your guide and after making a test call that demonstrates a fully functional microphone, I can exit skype, which smoothly resumes pulseaudio with a click of the OK button. It's a useful setup. [URL="http://ubuntuforums.org/showthread.php?t=790889"]See here
[/URL]

I'm stumped how to get the microphones working through ALSA-PULSE-JACK setup. Do you have any suggestions?

:confused:

Thanks again for your brilliant work here.

---

### Post by markbuntu on 2008-08-27
Funny, I have just been pondering this problem after running into it myself. I think I was just being too lazy to shut everything down to give this a try. But I will try it now. Stand by.

---

### Post by markbuntu on 2008-08-27
I was able to get my sound card microphone to work after much fooling around. The biggest problem was that my sound card mic capture was listed as mic boost capture, lol. Anyway the only thing I really had to do was set the Input Device to hw:1 in jack/setup and start everything from scratch. You may need to choose differently depending on your hardware. 

The same worked for my usb mic which is hw:3 on my system though I could control the usb mic in the PA Volume Control and leave the jack/setup/Input Device to default.

Either mic showed up in jack/connections/audio as system capture and could be connected to ardour for recording. PCM streaming audio is still connected separately through the pulseaudio/jack sink so that is a good thing in and of itself.

The only problem is that the mic connected to the sound card is always connected to the speakers but at least it can be recorded now. The usb mic does not do this through pulseaudio.

The reason seems to be that alsa passes soundcard capture straight to the output at a system level that cannot be intercepted by jack or pulse.

---

### Post by markbuntu on 2008-08-27
OK, I figured it out, if you read my despondent post of a few hours ago, I have replaced it, see above.

---

### Post by athianos on 2008-08-28
I apologise for the explosive and uncouth screenshot! I couldn't figure out another way to make things visible. 

Thanks for your time on this. 

Here are my settings, I've tried all the combinations I can think of, to no avail. I wondered if a look over what I have would help you to see something I am missing.

To the left of the screenshot is the ardour input static it is receiving, however there is still no recording available via the mic socket. This is vital for me as this is my line in. 

I have been able to record a mono track via my web cam! SO thanks for that. It means that now I can:
:lolflag:

However I cannot:

:guitar:

And the latter is of course what I would like to do. 

Any suggestions?

You'll see the Pulse volume meter is showing no input. I wondered if this is what you mean about going straight through the system and bypassing alsa and pulse. 

Before, when I mentioned Skype, it was through my Webcam's usb mic, so I figure its all about getting that line-in socket working. I just don't know where to start. 

Many thanks again.

 

[IMG]http://lh6.ggpht.com/andrewtilling/SLahzpVhgqI/AAAAAAAAACE/36hLDY2OUic/pulseardourjackalsa.png[/IMG]

---

### Post by sashi3 on 2008-08-28
Thanks for the detailed documentation. I am working towards enabling mutiple sound sources to be audible at the same time in my hardy setup. I have done the setup. But have not gotten around to testing it yet. May be tonight. But I had a question.

I have SageTV Placeshifter client running on this box. I understand it uses ALSA. So after I have done of installation of Pulseaudio plugin for ALSA and the susequent setup, should I not be seeing the SageTV client in the Pulseaudio Manager Devices tab, when I have the client up and running. I did not see it, when I logged in through VNC little while ago and started it up to see what happens. Apps such as Rhythmbox is showing up fine. Also I have read some old comments somewhere about an earlier version of SageTV that it takes over the ALSA server. Not sure how relevant that information is with the current version of Placeshifter and setup. 

I was wondering if you had any comments about SageTV client in this respect. As I said I have not yet tried listening to multiple sources simultaenously after your suggest setup. But in past multiple sources did not work for me at the same time. Once I had something playing, the other app would gray out the volume button.

Additionaly with SageTV Placeshifter I have seen sometimes after I have used this app (and exited), no sound would be coming out from other apps that I play afterwards even with max volume. I guess somehow the volume level or some gain gets set to very very low or something. rebooting would tend to fix it. It does not happen all the time, but often enough.

I am hoping your setup would help me resolve all these issues.

---

### Post by markbuntu on 2008-08-28
> **athianos said:**
> I apologise for the explosive and uncouth screenshot! I couldn't figure out another way to make things visible. 

Thanks for your time on this. 

Here are my settings, I've tried all the combinations I can think of, to no avail. I wondered if a look over what I have would help you to see something I am missing.

To the left of the screenshot is the ardour input static it is receiving, however there is still no recording available via the mic socket. This is vital for me as this is my line in. 

I have been able to record a mono track via my web cam! SO thanks for that. It means that now I can:
:lolflag:

However I cannot:

:guitar:

And the latter is of course what I would like to do. 

Any suggestions?

You'll see the Pulse volume meter is showing no input. I wondered if this is what you mean about going straight through the system and bypassing alsa and pulse. 

Before, when I mentioned Skype, it was through my Webcam's usb mic, so I figure its all about getting that line-in socket working. I just don't know where to start. 

Many thanks again.

 

[IMG]http://lh6.ggpht.com/andrewtilling/SLahzpVhgqI/AAAAAAAAACE/36hLDY2OUic/pulseardourjackalsa.png[/IMG]

As i said, you will need to use jack/setup/Input Device set to your sound card, ie hw:0 or hw:1, etc and use the alsa mixer to set the mic capture or line in capture. Because pulse does not distinguish between capture and output devices in sound cards, you must explicitly set the Input Device in jack/setup. 

It will then show up in jack connection/audio as system capture and can be linked into ardour from there. You may have to close jack down completely and restart for this to take effect.

---

### Post by markbuntu on 2008-08-28
> **sashi3 said:**
> Thanks for the detailed documentation. I am working towards enabling mutiple sound sources to be audible at the same time in my hardy setup. I have done the setup. But have not gotten around to testing it yet. May be tonight. But I had a question.

I have SageTV Placeshifter client running on this box. I understand it uses ALSA. So after I have done of installation of Pulseaudio plugin for ALSA and the susequent setup, should I not be seeing the SageTV client in the Pulseaudio Manager Devices tab, when I have the client up and running. I did not see it, when I logged in through VNC little while ago and started it up to see what happens. Apps such as Rhythmbox is showing up fine. Also I have read some old comments somewhere about an earlier version of SageTV that it takes over the ALSA server. Not sure how relevant that information is with the current version of Placeshifter and setup. 

I was wondering if you had any comments about SageTV client in this respect. As I said I have not yet tried listening to multiple sources simultaenously after your suggest setup. But in past multiple sources did not work for me at the same time. Once I had something playing, the other app would gray out the volume button.

Additionaly with SageTV Placeshifter I have seen sometimes after I have used this app (and exited), no sound would be coming out from other apps that I play afterwards even with max volume. I guess somehow the volume level or some gain gets set to very very low or something. rebooting would tend to fix it. It does not happen all the time, but often enough.

I am hoping your setup would help me resolve all these issues.

I know absolutely nothing about this SageTV Placeshifter client but if it is a properly written alsa application it should be showing up in the PA manager. It could be a program originally written for OSS or portaudio or something else that is using a poorly written alsa plugin. 

Can you change the audio preference in this program?
If you can change it to OSS, try that and then launch it with aoss so it will use the alsa-oss wrapper.

If other applications cannot use sound after the program closes, it is possible that it did not close cleanly and is still running as a zombie. You can check with the system monitor and kill it from there if you still see it after you have closed it.

---

### Post by sashi3 on 2008-08-28
Alight, concurrent sound is working fine with apps like rhythmbox and mplayer. Unfortuntaley SageTV continues to behave oddly. When I was playing rhythmbox or mplayer, and start up sageTV placeshifter client no sound would be coming out of the sageTV client. Similarly if SageTv client is running by itself I get its audio fine. But at the sametime if I start up Rhythmbox or some other app, I dont hear sound from them.

I will ping folks on the SageTV forum. But I doubt I will get much clarification.

But thanks to you at least I have other audio apps working correctly right now!

---

### Post by tigercorp on 2008-09-04
> **markbuntu said:**
> 
one way that some people have fixed their sound problems is by creating a new user in system/administration/users and groups and then logging in with that. It seems the generic system defaults for new users are different from the initial user defaults that ubuntu installs. You should try that first before resorting to some of the more drastic steps below, it is a simple thing to do and will make no changes to your system. And if it works, you will know it is just a user configuration problem and you can compare the hidden user default files in the respective home directories to find and fix the problems.




:):):)   THANK YOU!!!!  :):):)


I'm new to linux (I'm a Windows sys engineer for a living) and installed Hardy on my work lappy last Sun after losing a 2 week long battle with Vista SP1.  Reinstalled on Mon after realizing I should set up my partitions differently and had it all working perfectly by Tues evening, except for low volume on the internal mic and Skype.  Have probably spent 12 hours over the past 2 days trying to fix.
I guess I wrecked something in my user settings along the way, cos when I log in as a different user IT ALL JUST WORKS!!!! 

While I'm soo happy it's all working, I'm also glad I had the problems as I've learnt so much over the past couple of days.  Fantastic forums and supportive community, its all very cool.

Right, about to go through and compare user settings to see what the problem was now....

Thanks again!

:)

---

### Post by chitresh4u on 2008-09-11
Thanks a lot. I managed to solve all problems related to sound on Hardy. Though I found some unexpected behaviors, which are as follows:
[LIST=1]
[*]Amarok (using xine engine) kept giving error : Cannot initialize any sound drivers. 
I also found that when no other application (using sound) is running then amarok could play and nothing was displayed in the Devices tab of Pulseaudio manager. It seems to be using OSS. So I tried launching amarok with **padsp**. It worked (& displayed in the Devices tab of Pulseaudio manager), but it shooted my CPU usage to 100%. Launching with **aoss** solved the high cpu usage problem as well.
[*]Xine: same as amarok
[*]gnome-alsamixer kept exiting with following error 
(Though I can still use **alsamixer** from terminal) :

(gnome-alsamixer:6556): GLib-GObject-CRITICAL **: g_type_instance_get_private: assertion `instance != NULL && instance->g_class != NULL' failed

(gnome-alsamixer:6556): GLib-GObject-CRITICAL **: g_type_instance_get_private: assertion `instance != NULL && instance->g_class != NULL' failed
Segmentation fault
.
[/LIST]

**Anyway thanks a lot for all the help.**

EDIT: There seems to be a bug report related to the amarok issue. [https://bugs.launchpad.net/ubuntu/+source/amarok/+bug/211006](https://bugs.launchpad.net/ubuntu/+source/amarok/+bug/211006)

---

### Post by talking Llama on 2008-09-11
Amazing! Thank you so so much! All I did was the Try This First section and as soon as I got to "Play something in Rhythm Box" it worked perfectly, I can't thank you enough! 100% solved, thanks! ^-^

---

### Post by markbuntu on 2008-09-12
> **chitresh4u said:**
> Thanks a lot. I managed to solve all problems related to sound on Hardy. Though I found some unexpected behaviors, which are as follows:
[LIST=1]
[*]Amarok (using xine engine) kept giving error : Cannot initialize any sound drivers. 
I also found that when no other application (using sound) is running then amarok could play and nothing was displayed in the Devices tab of Pulseaudio manager. It seems to be using OSS. So I tried launching amarok with **padsp**. It worked (& displayed in the Devices tab of Pulseaudio manager), but it shooted my CPU usage to 100%. Launching with **aoss** solved the high cpu usage problem as well.
[*]Xine: same as amarok
[*]gnome-alsamixer kept exiting with following error 
(Though I can still use **alsamixer** from terminal) :

(gnome-alsamixer:6556): GLib-GObject-CRITICAL **: g_type_instance_get_private: assertion `instance != NULL && instance->g_class != NULL' failed

(gnome-alsamixer:6556): GLib-GObject-CRITICAL **: g_type_instance_get_private: assertion `instance != NULL && instance->g_class != NULL' failed
Segmentation fault
.
[/LIST]

**Anyway thanks a lot for all the help.**

EDIT: There seems to be a bug report related to the amarok issue. [https://bugs.launchpad.net/ubuntu/+source/amarok/+bug/211006](https://bugs.launchpad.net/ubuntu/+source/amarok/+bug/211006)

I have had some problems with xine myself so I try to avoid it and use gstreamer instead. 

In Amarok, you can go to Settings/Configure Amarok/Engine and change the output plugin to pulseaudio and you should not have these problems with it. You do not need to launch it with padsp or aoss if you do this. Amarok has its own plugins for alsa and pulseaudio.

Have you tried reinstalling the gnome-alsamixer?
If you do, and still get the segfault error, you should file a bug report with launchpad. The gnome-alsamixer is very stable. You should not be having this problem.

---

### Post by leepesjee on 2008-09-12
I've set the audio-driver in xine to jack and never had problems.
You can set the audio driver in xine in Settings -> Setup (set experience level to at least "Advanced") -> Audio -> driver.
Maybe worth a try.

---

### Post by culturepunk on 2008-09-14
@markbuntu

Thanks so much for this, been trying to get my sound working for about a week after installing pulseaudio when had a flash bug.

:) Got it working in about 5 mins thanks to your guide!

---

### Post by shane19174 on 2008-09-17
THANK YOU!!!!

After updating my Hardy to use the Ibex kernel (a desparate but successful attempt to solve system freezes), I had lots of sound issues. Following psyke83's instructions for setting up Pulseaudio ([http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)) got me most of the way, and your instructions filled in the last holes. 

Again, thanks!

Shane

---

### Post by pejobe on 2008-09-18
Thank you!
I run 64bit and this guide together with the useful links solved my sound problems.

---

### Post by chitresh4u on 2008-09-18
> **markbuntu said:**
> I have had some problems with xine myself so I try to avoid it and use gstreamer instead. 
In amarok, the only engine available is xine. Gstreamer is installed but its not present in the engine menu. I am using Amarok 1.4.9.1 (on Ubuntu 8.04 with gnome).

> **markbuntu said:**
> In Amarok, you can go to Settings/Configure Amarok/Engine and change the output plugin to pulseaudio and you should not have these problems with it. You do not need to launch it with padsp or aoss if you do this. Amarok has its own plugins for alsa and pulseaudio.
I am not getting any option for ALSA or Pulseaudio. Do I need any extra package for these ?

---

### Post by markbuntu on 2008-09-18
You probably do. If you are using the amarok-xine engine which is most likely you need:

libxine1-misc-plugins

to get all the xine audio output plugins.

---

### Post by chitresh4u on 2008-09-18
> **markbuntu said:**
> You probably do. If you are using the amarok-xine engine which is most likely you need:

libxine1-misc-plugins

to get all the xine audio output plugins.

libxine1-misc-plugins is installed. libxine1-plugins & libxine1-gnome is also installed. But I am not getting ALSA or Pulseaudio output. 

I also cannot figure out how to get Gstreamer engine for amarok.

---

### Post by markbuntu on 2008-09-18
I am not really an expert on Amarok, I just play one on tv. I am using the xine engine with Amarok myself and have not had any problems with it in Amarok but I have had some issues with xine in other applications. As far as I know, there is no gstreamer plugin for amarok.

I just installed Amarok and all these things were there. In Settings/Configure/Engine I have xine Engine listed and no other available option. Below that it says Output plugin: That is where I changed to pulseaudio.

---

### Post by motin on 2008-09-18
At the time of this thread's birth, xine -> pulseaudio -> jack-sink was working great!

At some point or another there-after this has stopped working! paplay can still output through the jack sink, but xine applications such as xine-ui and Amarok just won't play along any longer. 

Just re-installed the system (leaving nothing but /home) with the latest Intrepid alpha and the problem persists...

Other's are experiencing problems with xine as well - anyone found a solution to this? Smells like some sort of regression in the xine packages...

EDIT: Created a new thread on this issue: [http://ubuntuforums.org/showthread.php?p=5816790#post5816790](http://ubuntuforums.org/showthread.php?p=5816790#post5816790)

---

### Post by markbuntu on 2008-09-19
Well, I just checked and I am not having this problem. I have Amarok set up to use  pulseaudio and the stream shows up just fine and plays through the jack sink without any problem. Anyway, we will move further discussion to the thread listed above. Anyone having this problem should follow along.

---

### Post by motin on 2008-09-22
Other people that are having problems with Amarok/Xine seem not to have chosen pulseaudio as audio driver for Amarok/Xine. 

I just wanted to clarify that I have pulseaudio chosen without any success...

---

### Post by markbuntu on 2008-09-26
I did not have Amarok on my amd64 install but I am using it now through the pulse-jack sink and am not having any problems. I am using the pulseaudio output plugin.

I am also running xmms and audacious through the sink at the same time on the same internet radio channel and they all play though there is a weird effect from the 3 streams playing at slightly different delays, not to mention the jackrack effects I have plugged in.

---

### Post by xcafeus on 2008-09-28
thank you very much I will do some reading now :)

---

### Post by markbuntu on 2008-10-03
**SKYPE with Pulse Audio Solved!!!**

OK, Since so many, many people are complaining about Skype not working I finally installed it today and found the solution in the Mandriva Errata. It is so easy I almost fell out of my chair when I read it.

[http://wiki.mandriva.com/en/Releases/Mandriva/2008.0/Errata#Skype_with_PulseAudio](http://wiki.mandriva.com/en/Releases/Mandriva/2008.0/Errata#Skype_with_PulseAudio)

I have added a SKYPE section to the guide explaining how to do it.

(I also though this was a good excuse to give this thread a bump.)

---

### Post by eye208 on 2008-10-03
OK, what about Second Life? I know a lot of people waiting for this.

When the voice chat client attempts to open ALSA's "default" device it prints this message into the log:
```
alsa.c:562: set access failed: Invalid argument
```

Any ideas?

---

### Post by markbuntu on 2008-10-03
Geeze, you are just a troll. It took me less than 2 hours from the time I downloaded skype to the time I posted the solution, and that includes installing skype and confirming where the problem was, looking for a solution, finding it, testing it and writing it up. 

Why don't you fix this one!!
Something to do rather than just trolling around.

I can tell you why so many of these applications don't work with pulseaudio. I found out in my research that many of them make faulty assumptions about the hardware or about alsa. The wine devs admit this. They assumed that all sound cards have pcm controls, which is not the case. Pulseaudio was just the first place this cropped up but the sh** was about to hit the fan for them since so many usb devices have no pcm control. They are hurrying to fix it now. It is about the same with skype. The skype devs have made some faulty assumptions about the alsa devices so we must make a fake pulse device to compensate for their faulty assumptions. It was similar with flash 9 and is why flash 10 now works without libflashsupport.

I am sure it is the same with second life. It may be that this fix for skype also fixes second life. I remember reading some post somewhere a few months ago that some fix for skype also fixed second life.... Maybe I will look in the Mandriva Errata again, maybe Gentoo... so many places..answers are out there for everything if you just follow the links...

---

### Post by eye208 on 2008-10-04
> **markbuntu said:**
> Why don't you fix this one!!
I did, but you didn't like [the way I fixed it](http://ubuntuforums.org/showthread.php?t=885437), so here I am, giving PulseAudio another shot. Isn't that what you were asking for?

> I can tell you why so many of these applications don't work with pulseaudio.
Wait a minute. When I said that some applications don't work with PulseAudio you accused me of talking BS. You can look it up [right here](http://ubuntuforums.org/showpost.php?p=5877157&postcount=18).

> I found out in my research that many of them make faulty assumptions about the hardware or about alsa.
Did it ever occur to you that maybe the PulseAudio developers made faulty assumptions about ALSA when they created the pulse plugin?

Could it be that only a subset of ALSA's PCM access modes (listed [here](http://www.alsa-project.org/alsa-doc/alsa-lib/group___p_c_m.html#gb305f210b05bc39dac0a31480023ddb9), documented [here](http://www.alsa-project.org/alsa-doc/alsa-lib/pcm.html)) is supported by the pulse plugin?

Could it be that PulseAudio's compatibility layer is incomplete?

Could it be that the PulseAudio developers expected to get away with it by pointing fingers at application developers? Could it be that the release of an immature version of PulseAudio in mainstream Linux distributions was expected to build up enough community pressure so that app developers would take over the rest of the work, modifying their code around PulseAudio's quirks?

The problem in this case is that the SL voice chat client is not open source. It was made by [Vivox](http://www.vivox.com/), and the Linux version came 6 months later than the Windows and Mac versions. I guess we can consider ourselves lucky that there is a Linux version at all. I don't think the Linux community is large enough to apply pressure to Vivox. Their client works perfectly with ALSA, i.e. they fulfilled their part of the contract with Linden Lab. They won't add PA support for free, so this one has to be fixed by the PulseAudio guys themselves.

---

### Post by markbuntu on 2008-10-04
> **eye208 said:**
> I did, but you didn't like [the way I fixed it](http://ubuntuforums.org/showthread.php?t=885437), so here I am, giving PulseAudio another shot. Isn't that what you were asking for?

Not really, but now that you are here, you can help out. What the entire linux community suffers from is no lack of criticism when what it really needs is more help. So, if people who put so much energy into criticism would help instead, we could all move things along in a much better environment. So what happened, got a USB something or other with a buggy volume control?

> 
Wait a minute. When I said that some applications don't work with PulseAudio you accused me of talking BS. You can look it up [right here](http://ubuntuforums.org/showpost.php?p=5877157&postcount=18).[QUOTE]

I did not say that pulseaudio works with all applications there, I said it will fix problems and that you were spreading disinformation, which I still think you were doing, but I am willing to let bygones be bygones. Peace, OK?


Did it ever occur to you that maybe the PulseAudio developers made faulty assumptions about ALSA when they created the pulse plugin?[/QUOTE]

Well, that did occur to me, so I thought I would look into it and it turns out that the PA devs actually made correct assumptions while some application devs did not. As I said, the wine devs even fessed up to it.

> 
Could it be that only a subset of ALSA's PCM access modes (listed [here](http://www.alsa-project.org/alsa-doc/alsa-lib/group___p_c_m.html#gb305f210b05bc39dac0a31480023ddb9), documented [here](http://www.alsa-project.org/alsa-doc/alsa-lib/pcm.html)) is supported by the pulse plugin?

Could it be that PulseAudio's compatibility layer is incomplete?

Could it be that the PulseAudio developers expected to get away with it by pointing fingers at application developers? Could it be that the release of an immature version of PulseAudio in mainstream Linux distributions was expected to build up enough community pressure so that app developers would take over the rest of the work, modifying their code around PulseAudio's quirks?


What is more likely is that the app devs expected to get away with what they wrote and Pulse pulled their pants down.
PA's compatibility layer is still a work in progress, as is everything else. And ALSA is one of the fastest moving and poorly documented targets in software. If the ALSA devs would actually document their work, many applications would not be having these sort of problems. As it is, pulseaudio conforms to the very basic alsa standards and makes no assumptions about hardware, it leaves that to the drivers, where it belongs.

> 
The problem in this case is that the SL voice chat client is not open source. It was made by [Vivox](http://www.vivox.com/), and the Linux version came 6 months later than the Windows and Mac versions. I guess we can consider ourselves lucky that there is a Linux version at all. I don't think the Linux community is large enough to apply pressure to Vivox. Their client works perfectly with ALSA, i.e. they fulfilled their part of the contract with Linden Lab. They won't add PA support for free, so this one has to be fixed by the PulseAudio guys themselves.


Well there you go, if it was open source, it would have already been fixed by the community. Developers can write code to do things and the code will do it, but that does not mean that the code is correct and will work in all circumstances. skype code is also closed, but at least the skype devs are listening and trying fixing their code. The flash devs also listened and fixed their code too, as did the wine devs who are getting their alsa fixes into the next release but for now, wine works with padsp when set to OSS.

Like I said elsewhere, people should be glad that pulseaudio is exposing all this bad code now, so it can be fixed now, instead of causing even bigger problems in the future. Look at it this way, out of all the many many OSS and ALSA applications, only a few fail to work with PulseAudio. If all those other applications work fine, how can it be PulseAudio's fault? Should they implement some demented workaround that may break other things to get these poorly written applications to work?

These things should be fixed at the application level, which is where the problem lies.

---

### Post by markbuntu on 2008-10-04
**Second Life**
If you would like to use Second Life with Hardy and PulseAudio, read this thread (Post #7 seems most important):

[http://vboards.stratics.com/showthread.php?p=836114](http://vboards.stratics.com/showthread.php?p=836114)

Once again, Pulseaudio has revealed poorly written coding assumptions:

[http://jira.secondlife.com/browse/VWR-5708](http://jira.secondlife.com/browse/VWR-5708)

I have not tried this, Second life is not my thing.

If someone would give this a try and let me know, I will put it in the guide if it works.

---

### Post by eye208 on 2008-10-05
The VWR-5708 ticket is an entirely separate issue. It's a coding error that makes SLvoice crash on some machines. [VWR-6593](http://jira.secondlife.com/browse/VWR-6593) is what you want to look at.

SLvoice does not crash here. It just uses an access mode that seems to be unsupported with the pulse plugin. At least that's what ALSA is complaining about, according to the logs. Keep in mind, dmix is a plugin too. And it works. So the issue doesn't seem to be with ALSA's plugin interface in general but with that particular plugin. And no, I don't have a USB headset. My sound hardware consists of one Intel HDA onboard chip, the most basic setup you can possibly imagine, and probably the most widely used one as well.

Your conclusion doesn't make sense. If a Windows application fails to run on WINE, it is WINE's fault. Plain and simple. The PulseAudio developers have to either support ALSA in a transparent way or admit that they are unable to do so.

---

### Post by markbuntu on 2008-10-05
> **eye208 said:**
> 

Your conclusion doesn't make sense. If a Windows application fails to run on WINE, it is WINE's fault. Plain and simple. The PulseAudio developers have to either support ALSA in a transparent way or admit that they are unable to do so.

Not necessarily. Many windows applications fail to run on different windoze variations because they were not properly coded in the first place and so fall apart when they try to run on a different system. This is wine's fault?

Unless you can run the code line by line in a debugger, you cannot say that.

The pulse devs are very responsive when dealing with problems on their side, but they can only do so much and the fact is that the failure was caused by bad coding assumptions on the app devs side.

According to the other thread, [http://jira.secondlife.com/browse/VWR-6593](http://jira.secondlife.com/browse/VWR-6593) there are a myriad of problems with both ESD and its pulse replacement since some people seem to be having problems and success with either way. This points to a buggy implementation. Anyway, the devs have initiated and open source initiative so more people can scrutinize this and fix it.

We will see who fixes what.

---

### Post by eye208 on 2008-10-06
> **markbuntu said:**
> According to the other thread, [http://jira.secondlife.com/browse/VWR-6593](http://jira.secondlife.com/browse/VWR-6593) there are a myriad of problems with both ESD and its pulse replacement since some people seem to be having problems and success with either way. This points to a buggy implementation.
Contrary to what I suspected earlier, the problem is not with the ESD compatibility layer. The SL viewer is in fact using it successfully. But the SL voice app fails to open the ALSA default device. In my .asoundrc I have mapped it like this:
```
pcm.!default
{
    type pulse
}

ctl.!default
{
    type pulse
}
```
This results in:
```
alsa.c:562: set access failed: Invalid argument
```
The only reason I am looking into this at all is because switching between PulseAudio and ALSA+ESD takes only a minute, thanks to APT.

---

### Post by aidi.aidi on 2008-10-06
I don't know if it's the right forum to ask my question. I have a problem with my new computer Asus X20Eseries since I install Kubuntu 8.04. Sound doesn't work. I tried every solutions but until now nothing happens. Could anybody help me, please?

I post the results of following commands:

lspci |grep -i audio


00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)



cat /dev/sndstat


Sound Driver:3.8.1a-980706 (ALSA v1.0.16 emulation code)
Kernel: Linux Esplanada07 2.6.24-21-generic #1 SMP Mon Aug 25 17:32:09 UTC 2008 i686
Config options: 0

Installed drivers:
Type 10: ALSA emulation

Card config:
HDA Intel at 0xfeaf8000 irq 23

Audio devices:
0: ALC861VD Analog (DUPLEX)

Synth devices: NOT ENABLED IN CONFIG

Midi devices: NOT ENABLED IN CONFIG

Timers:
7: system timer

Mixers:
0: Silicon Image SiI1392 HDMI

---

### Post by markbuntu on 2008-10-06
> **eye208 said:**
> Contrary to what I suspected earlier, the problem is not with the ESD compatibility layer. The SL viewer is in fact using it successfully. But the SL voice app fails to open the ALSA default device. In my .asoundrc I have mapped it like this:
```
pcm.!default
{
    type pulse
}

ctl.!default
{
    type pulse
}
```
This results in:
```
alsa.c:562: set access failed: Invalid argument
```
The only reason I am looking into this at all is because switching between PulseAudio and ALSA+ESD takes only a minute, thanks to APT.

Did you try what this person did in post #7 of this thread here?

[http://vboards.stratics.com/showthread.php?p=836114](http://vboards.stratics.com/showthread.php?p=836114)

---

### Post by markbuntu on 2008-10-06
> **aidi.aidi said:**
> I don't know if it's the right forum to ask my question. I have a problem with my new computer Asus X20Eseries since I install Kubuntu 8.04. Sound doesn't work. I tried every solutions but until now nothing happens. Could anybody help me, please?

I post the results of following commands:

lspci |grep -i audio


00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)



cat /dev/sndstat


Sound Driver:3.8.1a-980706 (ALSA v1.0.16 emulation code)
Kernel: Linux Esplanada07 2.6.24-21-generic #1 SMP Mon Aug 25 17:32:09 UTC 2008 i686
Config options: 0

Installed drivers:
Type 10: ALSA emulation

Card config:
HDA Intel at 0xfeaf8000 irq 23

Audio devices:
0: ALC861VD Analog (DUPLEX)

Synth devices: NOT ENABLED IN CONFIG

Midi devices: NOT ENABLED IN CONFIG

Timers:
7: system timer

Mixers:
0: Silicon Image SiI1392 HDMI

Did you look in the HDA links in the OP and read through the threads. These are alsa settings so they should work fine in kbuntu.


[http://ubuntuforums.org/showthread.php?t=616845](http://ubuntuforums.org/showthread.php?t=616845)

[http://ubuntuforums.org/showthread.php?t=820959](http://ubuntuforums.org/showthread.php?t=820959)

More specifically all the options available for the SLC861. There are quite a few and unless someone has posted a specific answer for your machine, start with the most likely and then go on to the others if that doesn't work.

---

### Post by Jaz969 on 2008-10-07
Found an error
> libpulse-browser0 (client libraries)
should be libpulse-browse0

I'm using a CA0106 (Creative Labs) sound card and a microphone that plugs into the jack in the back of it. Anyone care to help me configure it?

---

### Post by markbuntu on 2008-10-07
> **Jaz969 said:**
> Found an error

should be libpulse-browse0

I'm using a CA0106 (Creative Labs) sound card and a microphone that plugs into the jack in the back of it. Anyone care to help me configure it?

Wow, thanks for that, fixed it.

I take it the mic is not working at all. Is the rest of the sound card.

Have you tried setting the capture and mic and mic boost in the Volume Control and mainkg it the default Input Device in the PulseAudio Volume Control?

Which app are you trying to record with?

---

### Post by Jaz969 on 2008-10-07
> **markbuntu said:**
> Wow, thanks for that, fixed it.

I take it the mic is not working at all. Is the rest of the sound card.

Have you tried setting the capture and mic and mic boost in the Volume Control and mainkg it the default Input Device in the PulseAudio Volume Control?

Which app are you trying to record with?

The mic does not work, but yes I have surround sound and everything working from the soundcard.

I'd like to record with Ventrilo I run off wine, but if I can get anything now I'd appreciate it. I'll probably be using Sound Recorder to test. As for setting it as default input etc.. you gotta run me through how to do that lol.

---

### Post by markbuntu on 2008-10-07
In System/Preferences/Sound change the audioconferencing sound capture to pulseaudio and in the Pulseaudio Volume Control (pavucontrol) you can go to Input Devices and choose the ALSA PCM on ...(CA106...) via DMA as you default by right cicking on it. Then try sound recorder.

---

### Post by Jaz969 on 2008-10-08
In Input Devices I see:

ALSA PCM on surround51:0 (CA0106)
and
ALSA PCM on front:1 (STAC92xx Analog) via DMA

doesn't work on either, and yes I'm 100% positive this microphone is set up correct, because i can just boot up xp and go right on ventrilo and talk fine.

---

### Post by Jaz969 on 2008-10-08
bump!

---

### Post by markbuntu on 2008-10-08
Please, no need to bump this, I get here as soon as I can. Ok, some people have trouble with their audigy cards that when the analog/digital box in their sound mixer is checked, they are unable to record. Make sure that the mic in the sound mixer is enabled and turned up, also the capture and mic boost if you have one these. You can check with the Pulseaudio Volume meter (capture) to see if pulseaudio is using the mic as a source.

Also, using windows is not really definitive for checking these things as windows can and does rearrange the connections to your sound card.

---

### Post by Jaz969 on 2008-10-08
> **markbuntu said:**
> Please, no need to bump this, I get here as soon as I can. Ok, some people have trouble with their audigy cards that when the analog/digital box in their sound mixer is checked, they are unable to record. Make sure that the mic in the sound mixer is enabled and turned up, also the capture and mic boost if you have one these. You can check with the Pulseaudio Volume meter (capture) to see if pulseaudio is using the mic as a source.

Also, using windows is not really definitive for checking these things as windows can and does rearrange the connections to your sound card.

I use the analog for sound. Is that a problem? Also I have no pulseaudio volume meter (capture) only playback and recording

---

### Post by markbuntu on 2008-10-08
Is the box checked? 
have you tried unchecking it?

Hmm..perhaps the pa volume meter (capture) is hidden in your menus, did you look?

---

### Post by Jaz969 on 2008-10-08
> **markbuntu said:**
> Is the box checked? 
have you tried unchecking it?

Hmm..perhaps the pa volume meter (capture) is hidden in your menus, did you look?

I don't have check boxes with is what I see. I also don't have microphone boost.

[http://omploader.org/vdDd5](http://omploader.org/vdDd5)

also i cant have sound from both wine and ubuntu at the same time.

---

### Post by markbuntu on 2008-10-08
You can fix that, and possibly your other problems, by following the OP and the links.

---

### Post by Jaz969 on 2008-10-08
Still having trouble, if I go to 
System > Pref > Default Sound Card
it just sits there and does the spinny wheel on the mouse then nothing happens :\

---

### Post by markbuntu on 2008-10-09
You probably need to reboot before you go further so all the changes you are making can be consolidated.

---

### Post by rishabh.bitsgoa on 2008-10-11
hey,
i have a compaq presario v3000, with the intel corporation 82801G(ICH7 family) High Definition Audio Controller(rev 02).
i recently installed ubuntu 8.04 and the sound is totally gone.it used to work on 7.10 as well as xp. 
i get a red cross mark on the volume control icon on the top right panel and on clicking it gives "no volume control GStreamer plugins and/or devices found"... so i cant do all the things mentioned in the posts. :(
i have installed linux i386 and all the other related deb packages.

i have done
 sudo aptitude install build-essential libncurses-dev gettext linux-headers-'uname -r'
sudo apt-get install module-assistant alsa-source
 sudo aptitude install linux-ubuntu-modules- 'uname -r'linux-genric. nothing has worked .

lspci gives:
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
05:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
08:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 02)
08:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
08:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
08:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a)
08:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 05)
08:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)


sysinfo:
intel corporation 82801G(ICH7 family) High Definition Audio Controller(rev 02)
Subsysytem" Hewlwtt-Packard company Unknown device 30b2

lspci -v:
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
Subsystem: Hewlett-Packard Company Unknown device 30b2
Flags: bus master, fast devsel, latency 0
Memory at d4280000 (32-bit, non-prefetchable) [size=512K]
Capabilities: <access denied>

on doing aplay -L , nothing comes up
and on doin sudo modprobe snd-82801G.. it gives
FATAL: Module snd_82801G not found.

lsmod | grep snd gives:
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  1 snd_pcm_oss
snd_seq_dummy           4868  0 
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
snd_rawmidi            25760  1 snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    56996  9 snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
snd_page_alloc         11400  1 snd_pcm


please help..

---

### Post by markbuntu on 2008-10-11
Most likely you need to reinstall alsa since it does not seem to be finding your sound card which is a fairly common ICH7. Since you upgraded, there may be some old configuration files which were left behind which you may have to remove. I don't know much about that. 

To help you figure out what is going on follow this guide:

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

The module you need is most likely snd_hda_intel with some option. Look in these links for that:

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

[http://ubuntuforums.org/showthread.php?t=616845](http://ubuntuforums.org/showthread.php?t=616845)

[http://ubuntuforums.org/showthread.php?t=820959](http://ubuntuforums.org/showthread.php?t=820959)

---

### Post by markbuntu on 2008-10-26
Update bump. Many new links.

---

### Post by Ng Oon-Ee on 2008-11-03
Hey, thanks so much for the Howto, especially about getting Pulse and JACK to play nice.

Just wanted to share, I've been playing around myself, and instead of starting ```
jackd -d alsa
``` as suggested in one of your links, I find it better to setup qjackctl to startup with the system, running a startup script which kills pulse if it happens to be running, and then loads the correct modules. I thought I'd have to start pulseaudio after that, but I think the fact that I'm using pamanager already does that for me.

So anyway, what I'm doing is setting up Jack using qjackctl, then under 'Setup' in qjackctl I click 'Start JACK audio server on application startup' and create a link to qjackctl in my Sessions.

Will be testing out this setup over the next week or so. No need to boot to windows to record anymore, hopefully.


EDIT: Instead of killing pulse on startup (which seems to have caused problems in the case of JACK crashing on me), I now kill it after shutdown. Under 'Setup', for scripts to execute after shutdown, I put 'killall jackd pulseaudio'

---

### Post by markbuntu on 2008-11-03
> **Ng Oon-Ee said:**
> Hey, thanks so much for the Howto, especially about getting Pulse and JACK to play nice.

Just wanted to share, I've been playing around myself, and instead of starting ```
jackd -d alsa
``` as suggested in one of your links, I find it better to setup qjackctl to startup with the system, running a startup script which kills pulse if it happens to be running, and then loads the correct modules. I thought I'd have to start pulseaudio after that, but I think the fact that I'm using pamanager already does that for me.

So anyway, what I'm doing is setting up Jack using qjackctl, then under 'Setup' in qjackctl I click 'Start JACK audio server on application startup' and create a link to qjackctl in my Sessions.

Will be testing out this setup over the next week or so. No need to boot to windows to record anymore, hopefully.


EDIT: Instead of killing pulse on startup (which seems to have caused problems in the case of JACK crashing on me), I now kill it after shutdown. Under 'Setup', for scripts to execute after shutdown, I put 'killall jackd pulseaudio'

Well, there is really no need to kill pulseaudio at all if you are using the pulse jack modules and the script included in that section of the OP. If anything, you might need a script to disconnect the pulseaudio connections to jack before closing jack so pulseaudio does not crash. I have no idea how to do that.

But anyway, thanks fot the info and be sure to keep us informed of your progress.

---

### Post by Ng Oon-Ee on 2008-11-03
> **markbuntu said:**
> Well, there is really no need to kill pulseaudio at all if you are using the pulse jack modules and the script included in that section of the OP. If anything, you might need a script to disconnect the pulseaudio connections to jack before closing jack so pulseaudio does not crash. I have no idea how to do that.

But anyway, thanks fot the info and be sure to keep us informed of your progress.

Yes, and I tried that first. Basically the command according to the 'man' page is:-

```
pactl [options] unload-module ID
```

So the problem with that is firstly getting the ID of the particular module, which changes (and is assigned) on first load of the module. If I load the module, unload it, and then load it (manually), it gets a higher ID (if it was 11, it will be 12 when next loaded).

Also, assuming I get that working, the end effect is of no benefit, because even though pulse doesn't have to restart, any applications that were playing sound through pulse will not continue playing without a restart if the module they were using for sink/source was removed. This applies both to media players like Rhythmbox as well as intermittent sounds from the likes of Pidgin.

The man page also has:-

```
pactl [options] move-sink-input ID SINK
```

which looks promising to move the currently connected streams to another sink, perhaps after reloading the modules. However, the problem as well is how to get the IDs of the currently running streams.

For now, my hackery works, except for needing all audio applications to restart to get sound due to pulse restarting. Which would be the same case if I unloaded/loaded the modules. If you have any other advise, would love to hear it :p

---

### Post by Lantesh on 2008-11-03
> **markbuntu said:**
> Digital Output
Digital output has two different formats. S/PDIF and IEC958. The easiest way to get your digital output working is to just turn it on in your mixer by checking the box labeled S/PDIF or IEC958. You may have number of these boxes so you need to play around with them to find the ones that work for you. If you have a IEC958 or S/PDIF Capture box and you check that, it may direct your microphone to the digital output which will make it unavailable for recording so be careful with that.

These boxes may not appear in the Volume Control and so may need to be accessed directly in the mixer. I highly recommend the gnome-alsamixer for this (see below). If checking any of these boxes causes your sound to disappear, uncheck them. You also may need to reboot before these changes take place as some hardware configuration files are only read at startup.

Mplayer, has an option for AC3 passthrough. VLC has an option to use S/PDIF when available. These options will redirect the audio stream from these players directly to the digital output. Players without these options will use the digital outputs through the ALSA sound server and driver. More in depth information about getting digital output working is available here:


Thank you thank you thank you thank you thank you.  I can't say this enough.  No matter what I tried I just couldn't get my SPDIF digital output to work.  Your post gave me the information I needed.  I am really grateful that you took the time to post all of this great information.

---

### Post by markbuntu on 2008-11-04
> **Ng Oon-Ee said:**
> Yes, and I tried that first. Basically the command according to the 'man' page is:-

```
pactl [options] unload-module ID
```

So the problem with that is firstly getting the ID of the particular module, which changes (and is assigned) on first load of the module. If I load the module, unload it, and then load it (manually), it gets a higher ID (if it was 11, it will be 12 when next loaded).

Also, assuming I get that working, the end effect is of no benefit, because even though pulse doesn't have to restart, any applications that were playing sound through pulse will not continue playing without a restart if the module they were using for sink/source was removed. This applies both to media players like Rhythmbox as well as intermittent sounds from the likes of Pidgin.

The man page also has:-

```
pactl [options] move-sink-input ID SINK
```

which looks promising to move the currently connected streams to another sink, perhaps after reloading the modules. However, the problem as well is how to get the IDs of the currently running streams.

For now, my hackery works, except for needing all audio applications to restart to get sound due to pulse restarting. Which would be the same case if I unloaded/loaded the modules. If you have any other advise, would love to hear it :p

I just use disconnect all in the connections box before closing jack. I think that may be what you want your closing script to do since the pulsejack modules are automatically closed when jack closes and the

module-rescue-streams

will move your streams to another device automatically if you have one available. 

Oh, I can see how that would be problematic when you have only one device. The streams would become orphans since pulse may have no where to move them if it has not yet realized that jack has released the hardware when it closed. So, I think this may be a matter of timing with the commands. Maybe inserting a

wait 10

somewhere in there after jack closes will give pulse time to figure out what is going on, recapture the hardware, and let module-rescue-streams do its thing.

Since pactl writes the module id to stdout when it loads, you could pipe it to somewhere your closing script could find it. I have not fooled around with command line scripts for years so I cannot tell you specifically how to do that but I do remember it as a fairly easy operation.

Anyway, thanks for bringing this up, I never really thought about this particular problem. And please keep us informed of your progress.

---

### Post by Ng Oon-Ee on 2008-11-04
> **markbuntu said:**
> I just use disconnect all in the connections box before closing jack. I think that may be what you want your closing script to do since the pulsejack modules are automatically closed when jack closes and the

module-rescue-streams

will move your streams to another device automatically if you have one available.

So I just tried this out, a disconnect all works if no application is playing sound at that instance, when I startup qjackctl again (of course removing the startup code to kill/restart pulse) after quitting with rhythmbox running and paused, I can just click play for it to move on, however if Rhythmbox is playing while qjackctl quits, Rhythmbox itself hangs and has to be killed (starts cycling through all the songs in my playlist, probably finds itself unable to play each one).

Anyway, any idea whether I can run some type of CLI code that duplicates the 'disconnect all' button in qjackctl? The man pages for qjackctl and jackd are unhelpful in this area, I believe they're just used to START the JACK session.

> **markbuntu said:**
> Oh, I can see how that would be problematic when you have only one device. The streams would become orphans since pulse may have no where to move them if it has not yet realized that jack has released the hardware when it closed. So, I think this may be a matter of timing with the commands. Maybe inserting a

wait 10

somewhere in there after jack closes will give pulse time to figure out what is going on, recapture the hardware, and let module-rescue-streams do its thing.

Since pactl writes the module id to stdout when it loads, you could pipe it to somewhere your closing script could find it. I have not fooled around with command line scripts for years so I cannot tell you specifically how to do that but I do remember it as a fairly easy operation.

Anyway, thanks for bringing this up, I never really thought about this particular problem. And please keep us informed of your progress.

Yes, there's the problem that I only have one device, and Pulse can't take control of it since JACK already has control. Perhaps a way of using pactl to inform pulse that 'hey, you can have the ALSA API now'. Which would also require the reverse, a way of telling pulse 'hands off the ALSA, its my turn' when JACK stats up.

JACK could be totally transparent to apps using Pulse in that case, either Pulse sends the audio directly to the device or JACK says "excuse me" and inserts itself in between Pulse and the device, with maybe a bit of a glitch at changeover :lolflag: sounds good.

---

### Post by markbuntu on 2008-11-06
> **Ng Oon-Ee said:**
> 

Yes, there's the problem that I only have one device, and Pulse can't take control of it since JACK already has control. Perhaps a way of using pactl to inform pulse that 'hey, you can have the ALSA API now'. Which would also require the reverse, a way of telling pulse 'hands off the ALSA, its my turn' when JACK stats up.

JACK could be totally transparent to apps using Pulse in that case, either Pulse sends the audio directly to the device or JACK says "excuse me" and inserts itself in between Pulse and the device, with maybe a bit of a glitch at changeover :lolflag: sounds good.

Maybe a good place to bring this up would be in the pulseaudio mailing list, the pulseaudio developers are very active in replying there.

[https://tango.0pointer.de/mailman/listinfo/pulseaudio-discuss](https://tango.0pointer.de/mailman/listinfo/pulseaudio-discuss)

---

### Post by Ng Oon-Ee on 2008-11-07
> **markbuntu said:**
> Maybe a good place to bring this up would be in the pulseaudio mailing list, the pulseaudio developers are very active in replying there.

[https://tango.0pointer.de/mailman/listinfo/pulseaudio-discuss](https://tango.0pointer.de/mailman/listinfo/pulseaudio-discuss)

Thank you, I've just shot off a mail.

So, no idea about a CLI for 'disconnect all' for JACK? I haven't managed to find any info about controlling a currently running JACK daemon without qjackctl, surprisingly enough.

---

### Post by markbuntu on 2008-11-07
> **Ng Oon-Ee said:**
> Thank you, I've just shot off a mail.

So, no idea about a CLI for 'disconnect all' for JACK? I haven't managed to find any info about controlling a currently running JACK daemon without qjackctl, surprisingly enough.

Have you tried looking into jack-tools?
It is a set of command line tools for jack. Maybe you can find something in there that will help you.

---

### Post by Dark Hornet on 2008-11-12
I am having an odd issue that I can't seem to find a fix for....I have posted in the forums here [http://ubuntuforums.org/showthread.php?t=978746](http://ubuntuforums.org/showthread.php?t=978746) the other day...but I am thinking that this thread is more along the lines of what I need...

Here goes...I am using Ubuntu 8.04 x64 and everything was working great (sound wise) until the other day.  The only sound that I can get to come out of my speakers are my .mkv High def movie files.  The rest of my files (.mp3, boot sounds, .avi, etc) all play just fine, but only through the headphones.

I have a surround sound set up that is hooked up to my on board Intel sound card via an optical cable.  I have tried the different suggestions mentioned in this thread and others, all to no avail.  

Please let me know if you need any additional information, and thanks for any help.

Darkhornet

---

### Post by markbuntu on 2008-11-12
Do these application streams appear in the pulseaudio volume control when they are playing?

---

### Post by Dark Hornet on 2008-11-12
> **markbuntu said:**
> Do these application streams appear in the pulseaudio volume control when they are playing?


How would I check that?

EDIT -- note, I do not have pavucontrol installed on my system, as I am not using Pulse.

---

### Post by Ng Oon-Ee on 2008-11-13
> **Dark Hornet said:**
> How would I check that?

EDIT -- note, I do not have pavucontrol installed on my system, as I am not using Pulse.

What's your setup then? Alsamix?

More info would be good =). Considering the whole guide is mainly about setting up Pulseaudio.




Ah, and markbuntu, I've been trying stuff. So far starting up with module-null-sink means that if I kill jack the currently playing apps jump to the null sink. However, when starting up qjackctl again, I have to manually move them back, I'm currently looking at automating that with pactl.

---

### Post by Dark Hornet on 2008-11-13
Yes, I am using ALSA...rather, I am assuming I am using ALSA, as most of my settings under sound are set to "auto detect".  I have changed these settings to pulse, alsa, oss, etc, and it has fixed nothing.

Thanks for the help.

Darkhornet

---

### Post by Ng Oon-Ee on 2008-11-13
> **Dark Hornet said:**
> Yes, I am using ALSA...rather, I am assuming I am using ALSA, as most of my settings under sound are set to "auto detect".  I have changed these settings to pulse, alsa, oss, etc, and it has fixed nothing.

Thanks for the help.

Darkhornet

I'd suggest going through the guide in the first post step-by-step. That you're not using pulse at all seems to indicate you have not, or maybe that you've only tried some steps individually. It doesn't take that long, though it does seem lengthy.

Otherwise, not very fair to expect markbuntu to give you much help, especially since all he has to go on are symptoms instead of actual details (what your setup is like, what configuration files you're using, etc.)

---

### Post by Dark Hornet on 2008-11-13
Ok, well, I have been through the guide, all to no avail...I could possibly be missing something though.  I did end up installing "pauvcontrol" just to make sure I had no streams, and just as I suspected, there is nothing on the Playback tab where it would show the available streams.

---

### Post by markbuntu on 2008-11-13
> **Ng Oon-Ee said:**
> ...

Yes, there's the problem that I only have one device, and Pulse can't take control of it since JACK already has control. Perhaps a way of using pactl to inform pulse that 'hey, you can have the ALSA API now'. Which would also require the reverse, a way of telling pulse 'hands off the ALSA, its my turn' when JACK stats up.

...

I have found our some more info that may help with your problem.

If pulse has module-always-sink loaded then it will create a null sink if all the sinks go away and move existing streams to that and then move them to a new sink when one shows up with the help of module-rescue-streams. 

You might try adding a line
```

load-module module-always-stream

```

and make sure the line
```

load-module module-rescue-streams

```
 
is not commented out in your etc/pulse/default.pa. I am not entirely sure that this module is available in the version of pulseaudio for Hardy but you should give it a try. If the module is not available, you will get error messages if it does not load, let me know and we can hunt it down in the debian repos or somewhere like that.

---

### Post by markbuntu on 2008-11-13
> **Dark Hornet said:**
> Ok, well, I have been through the guide, all to no avail...I could possibly be missing something though.  I did end up installing "pauvcontrol" just to make sure I had no streams, and just as I suspected, there is nothing on the Playback tab where it would show the available streams.

Are you using mplayer?
There is a problem with mplayer using the ac3 digital playthrough that causes alsa to get confused and play nothing. You should try reinstalling alsa and then follow the guide.

---

### Post by Dark Hornet on 2008-11-13
no, I try not to use Mplayer for anything...I like VLC for my video files, and Amarok for audio...but I will try to reinstall ALSA if you think that will help.

---

### Post by markbuntu on 2008-11-13
> **Dark Hornet said:**
> no, I try not to use Mplayer for anything...I like VLC for my video files, and Amarok for audio...but I will try to reinstall ALSA if you think that will help.

It may, but let me try to get a better understanding of your problem. You have music through your headphones now but not your speakers right?
Is there a switch in your sound mixer for that?
If you turn off the digital output do your speakers work?

---

### Post by Dark Hornet on 2008-11-13
Correct, I have .mp3, boot sounds, older .avi files, etc through my headphones, and my .mkv (high def video files) are through my speakers.  I have checked and rechecked all of my settings in the sound preferences, and I have made sure that everything is showing...and I can't see that there is a setting for it.  If there was, wouldn't it pipe ALL sound through the headphones?

Thanks,
Darkhornet

---

### Post by Ng Oon-Ee on 2008-11-13
> **markbuntu said:**
> I have found our some more info that may help with your problem.

If pulse has module-always-sink loaded then it will create a null sink if all the sinks go away and move existing streams to that and then move them to a new sink when one shows up with the help of module-rescue-streams. 

You might try adding a line
```

load-module module-always-stream

```

and make sure the line
```

load-module module-rescue-streams

```
 
is not commented out in your etc/pulse/default.pa. I am not entirely sure that this module is available in the version of pulseaudio for Hardy but you should give it a try. If the module is not available, you will get error messages if it does not load, let me know and we can hunt it down in the debian repos or somewhere like that.

Ah, you must have received the same email I did =). I can confirm that this module is not in the Intrepid version (I'm using that) 0.9.10. If I add a certain repo (themuso) I can up that to 0.9.13, but then module-jack breaks and I can't add it without downgrading pulseaudio 0.9.13. Any ideas?

Anyway, I use the pulseaudio-null-sink module, sometimes it rescues properly, but other times pulseaudio dies when Jack is closed down. Can't find a pattern to that yet.

---

### Post by NeoZiggy on 2008-11-15
wow thanks, this really helped. i have crappy onboard sound, intel/ac'97, and i could never have multiple things going. flash videos on youtube would make all my sound completely stop even after firefox was closed. i hate reseting. 2 thumbs up!

---

### Post by mocha on 2008-11-19
Wow!  Thank you very much for this guide!  Now I FINALLY understand how to use PulseAudio and Jack sources and sinks to "route" audio.  Literally after more than 1 year of struggling how to record the internal audio mix from my crappy Intel HDA controller with gtk-recordmydesktop and arecord, this guide has allowed me to finally understand how to route that audio to be captured.   I wasted so much time on the ALSA bug tracking system, there are so many bugs with Intel HDA, I can see the power of the Pulse layer now.  Thanks so much!!!!  :guitar:

---

### Post by Ng Oon-Ee on 2008-11-20
Ah, I don't think I'm ever going to figure out how to properly rescue without crashing. Will look at that again in a couple of months when real-life has slowed down.

In the mean-time, I've discovered that Audacity works well with JACK if compiled from source with portaudio compiled for JACK support. Written a HOWTO [here]("http://ubuntuforums.org/showthread.php?t=982577"). May be useful for some people, if you just add that in to the section mentioning Audacity, since I keep referring people to your guide for setting up JACK with Pulse in the first place.

---

### Post by markbuntu on 2008-11-20
I tried audacity but it was a huge pain, crash crash crash so I switched to ardour and it is fantastic. You should really give it a try. It makes the most of jack. If you are intimidated by all the controls you can just leave most of the zillion control options at the defaults. But read the jack links in the OP.

How well does this Audacity work? Does it work with the jack transport controls?
Does it work well with patchage and jackrack?
The transport control is important when using hydrogen and rosegarden synced with ardour, no cutting an pasting tracks back and forth, huge time savings.

Anyway, I will add the link probably tomorrow sometime when I plan to be back on my Ubuntu Hardy install, I am using Mandriva One 2009 right now, trying out KDE4, so far so good but I have no access to my notes on another drive, some weird issue they have a bug report on.

---

### Post by Ng Oon-Ee on 2008-11-20
> **markbuntu said:**
> I tried audacity but it was a huge pain, crash crash crash so I switched to ardour and it is fantastic. You should really give it a try. It makes the most of jack. If you are intimidated by all the controls you can just leave most of the zillion control options at the defaults. But read the jack links in the OP.

How well does this Audacity work? Does it work with the jack transport controls?
Does it work well with patchage and jackrack?
The transport control is important when using hydrogen and rosegarden synced with ardour, no cutting an pasting tracks back and forth, huge time savings.

Anyway, I will add the link probably tomorrow sometime when I plan to be back on my Ubuntu Hardy install, I am using Mandriva One 2009 right now, trying out KDE4, so far so good but I have no access to my notes on another drive, some weird issue they have a bug report on.

I mainly use Audacity because it supports all the proprietary formats, and I have no desire to convert my entire collection into OGG anytime soon. As for how well it works with JACK, it works, of course. I'm not sure how to use transport control (or, even, what its for). Assuming that its for syncing of tracks, then I doubt Audacity has support for that, as JACK support is only through the PortAudio v19 compile, which means that JACK is basically just seen as a source/sink.

KDE4 eh, you're braver than I am. Every single time I try out the latest KDE I always give up after a couple of hours. Am not able to figure out even the most basic stuff there. And to think it was supposed to be the most windows-like, familiar to long-term Windows users DE :lolflag:


EDIT: Ah, forgot to mention, Audacity is much simpler to use than Ardour (my opinion, of course), and I can always edit Audacity projects in Windows (I normally prefer cross-platform software, the firefox/thunderbird/pidgin etc compared to konquerer/evolution/kontact). Which are my main reasons for using it. Ardour just scares me =)

---

### Post by Portable_Jim on 2008-11-21
I had trouble with the java web-start app Elluminate in Hardy 64-bit

Workaround:[ http://portablejim.site-hosts.net...buntu-64-bit.html]("http://portablejim.site-hosts.net/Problems-and-Solutions/Howto-Elluminate-sound-Java-working-in-Ubuntu-64-bit.html")

---

### Post by Ng Oon-Ee on 2008-11-21
> **Portable_Jim said:**
> I had trouble with the java web-start app Elluminate in Hardy 64-bit

Solution:[ http://portablejim.site-hosts.net...buntu-64-bit.html]("http://portablejim.site-hosts.net/Problems-and-Solutions/Howto-Elluminate-sound-Java-working-in-Ubuntu-64-bit.html")

Yes, I'm pretty sure most programs will work if you kill pulseaudio/esd and all other sound servers. The point is to try and make the programs play through them.

I would think the fact that you're using 32-bit Java in a 64-bit OS is the problem, esp to deal with the requisite libraries etc. For example, when running Wine (which is only 32-bit) I had to manually install 32-bit aoss in order to get sound to work properly with Pulse. Perhaps you could try using aoss as well (though I'm not sure how you'd start the Java engine up with that option).

---

### Post by psyke83 on 2008-11-21
> **Portable_Jim said:**
> I had trouble with the java web-start app Elluminate in Hardy 64-bit

Solution:[ http://portablejim.site-hosts.net...buntu-64-bit.html]("http://portablejim.site-hosts.net/Problems-and-Solutions/Howto-Elluminate-sound-Java-working-in-Ubuntu-64-bit.html")

That's not a solution, it's a workaround (and not a very good one).

You need to enable the PulseAudio ALSA plugins. These plugins are enabled by default in Intrepid, but not in Hardy.

See: [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

---

### Post by markbuntu on 2008-11-21
> **Ng Oon-Ee said:**
> I mainly use Audacity because it supports all the proprietary formats, and I have no desire to convert my entire collection into OGG anytime soon. As for how well it works with JACK, it works, of course. I'm not sure how to use transport control (or, even, what its for). Assuming that its for syncing of tracks, then I doubt Audacity has support for that, as JACK support is only through the PortAudio v19 compile, which means that JACK is basically just seen as a source/sink.

KDE4 eh, you're braver than I am. Every single time I try out the latest KDE I always give up after a couple of hours. Am not able to figure out even the most basic stuff there. And to think it was supposed to be the most windows-like, familiar to long-term Windows users DE :lolflag:


EDIT: Ah, forgot to mention, Audacity is much simpler to use than Ardour (my opinion, of course), and I can always edit Audacity projects in Windows (I normally prefer cross-platform software, the firefox/thunderbird/pidgin etc compared to konquerer/evolution/kontact). Which are my main reasons for using it. Ardour just scares me =)

LOL! Ardour can certainly seem intimidating but then again, it is aimed at professionals and is what you would see in a professional recording studio. Many studios use linux and ardour, it is far less expensive than proprietary studio networking/clustering solutions and works just as well or better.

I was a sound engineer in the 80s, workjing the sound board, recording punk bands live on a  half track tape machine, doing studio work, etc and to me ardour is just amazing, so many things I could have used back then....

I can see your point but for me audacity was not worth the effort. For simple recording from the net and stuff I just pop up soundrecorder or streamripper and use soundkonverter on them afterwards if I need to change the format.

But anyway, using jack as a sound server seems criminal to me. It is an audio connection kit and is capable of amazing feats. At the bottom of the jack control panel are transport buttons. When jack applications like ardour and hydrogen and rosegarden are set up to use it, it will sync them together for playback and recording. 

So if your drum tracks are in hydrogen, your synths in rosegarden, connected through patchage to ardour which has your analog tracks, you can use the jack transport controls to play/record them all in sync. If you need to fiddle with the drum track, you can just edit it in hydrogen and then push play in jack control to hear how it sounds with everything else. 

You can hook your midi devices directly to hydrogen and rosegarden and use them to play live with your other tracks and have mic and instrument inputs in ardour to do the same. You can also add effects anywhere you like.

Like I said, it is a professional recording solution. Personally, I don't go very deep into the zillion options in ardour. I find no need to change them but when I do it is one at a time and very carefully.

KDE4 is still in its infancy and a lot of functions and applications have not been ported over yet but it seems very stable in Mandriva. I tried Madriva because Intrepid will not even boot on this machine. :lolflag:

---

### Post by Ng Oon-Ee on 2008-11-21
> **markbuntu said:**
> I was a sound engineer in the 80s, workjing the sound board, recording punk bands live on a  half track tape machine, doing studio work, etc and to me ardour is just amazing, so many things I could have used back then....

I can see your point but for me audacity was not worth the effort. For simple recording from the net and stuff I just pop up soundrecorder or streamripper and use soundkonverter on them afterwards if I need to change the format.

Yes, that's what I'd do if I was just to record that one track, as well, but I use audacity for slightly more complicated projects. While I'm not sound engineer (I've got a non-related engineering education/degree and do music as a hobby) I have yearly Christmas projects where I record from my Korg keyboard's audio output. I normally layer a few tracks, firstly I'll do the drums on the keyboard, then add in the melody, then some bells/strings, stuff like that. So Audacity is mainly used for recording over previous recordings, which it can do pretty well. More importantly, soundrecorder can't. Ardour can do that very well, I'm sure, but as I mentioned, I'm scared =). Maybe once I've a bit of free time mid next year.

> **markbuntu said:**
> But anyway, using jack as a sound server seems criminal to me. It is an audio connection kit and is capable of amazing feats. At the bottom of the jack control panel are transport buttons. When jack applications like ardour and hydrogen and rosegarden are set up to use it, it will sync them together for playback and recording. 

So if your drum tracks are in hydrogen, your synths in rosegarden, connected through patchage to ardour which has your analog tracks, you can use the jack transport controls to play/record them all in sync. If you need to fiddle with the drum track, you can just edit it in hydrogen and then push play in jack control to hear how it sounds with everything else. 

You can hook your midi devices directly to hydrogen and rosegarden and use them to play live with your other tracks and have mic and instrument inputs in ardour to do the same. You can also add effects anywhere you like.

Like I said, it is a professional recording solution. Personally, I don't go very deep into the zillion options in ardour. I find no need to change them but when I do it is one at a time and very carefully.

Thanks, I've been looking for a real-life example of what the whole JACK setup is for, its easier to find HOWTO guides than an explanation of what the whole setup is for. I've been especially interested in Hydrogen, as my drum beats from my keyboard sound very MIDI, obviously, and I'd like to do some more drum-like sounds for my next year's projects. Looks like this is a possibility.

> **markbuntu said:**
> KDE4 is still in its infancy and a lot of functions and applications have not been ported over yet but it seems very stable in Mandriva. I tried Madriva because Intrepid will not even boot on this machine. :lolflag:

Not even boot? Now that's serious :). Haven't run across that yet, with any Linux OS on the rigs I've tried out, but seen enough complaints on this forum. Mainly about Xorg though, and just from looking its obvious they haven't done their research, esp concerning the 3D-accelerated drivers. Doubt thats your problem though.

---

### Post by thorgal on 2008-11-26
markbuntu,

I think you should mention netjack that contains 2 tools, alsa_in and alsa_out that can be used with 2 soundcards or more that are not clock-sync'ed via h/w. I don't know if there's a netjack ubuntu package but netjack and tools are part of the installed jack tools in newer jack versions (0.115.x).

---

### Post by markbuntu on 2008-11-26
> **thorgal said:**
> markbuntu,

I think you should mention netjack that contains 2 tools, alsa_in and alsa_out that can be used with 2 soundcards or more that are clock-sync'ed via h/w. I don't know if there's a netjack ubuntu package but netjack and tools are part of the installed jack tools in newer jack versions (0.115.x).

That is a really good idea. I looked into netjack a few months ago and the info I was able to find on setting it up was very scarce and seemed incomplete so I never gave it a try. 

If you could give me a link to some very simple instructions for setting up netjack, and can confirm that netjack is available in the current version of jack in the repos i will look into it.

I really do not want to tell people they need to compile anything from source unless they are in a truly desperate situation because that can create all sorts of other difficult problems with updates, etc so I would like to avoid that.

Anyway, what I am really looking for with jack is a not too complicated way to setup multiple inputs/outputs from my multiple sound cards, essentially multiple system inputs to ardour through the jack connections box or patchage. Can I do that with netjack?

---

### Post by thorgal on 2008-11-27
markbuntu,

have a look at this : [http://trac.jackaudio.org/wiki/WalkThrough/User/AlsaInOut](http://trac.jackaudio.org/wiki/WalkThrough/User/AlsaInOut)

This is about alsa_in and alsa_out.

---

### Post by nomind111 on 2008-11-28
hello, when i have jack running and recordmydesktop running, and then open firefox to the site i want to record a video with, firefox will load the video but the video doesnt work,stalls, and firefox crashes.  this happens continuously if jack and recordmydesktop are running. when they arent running everything is normal...any ideas? thanks in advance:)

---

### Post by Ng Oon-Ee on 2008-11-28
> **nomind111 said:**
> hello, when i have jack running and recordmydesktop running, and then open firefox to the site i want to record a video with, firefox will load the video but the video doesnt work,stalls, and firefox crashes.  this happens continuously if jack and recordmydesktop are running. when they arent running everything is normal...any ideas? thanks in advance:)
You probably have your system (and therefore Firefox) set to use your soundcard directly, or to use Pulseaudio. Obviously, if it tries to play sound through a channel that does not exist, it will crash (most music players do this as well, I notice).

Have you actually followed the guide? If you're just asking a question which is out of topic for this guide please start your own thread.

---

### Post by markbuntu on 2008-11-29
> **nomind111 said:**
> hello, when i have jack running and recordmydesktop running, and then open firefox to the site i want to record a video with, firefox will load the video but the video doesnt work,stalls, and firefox crashes.  this happens continuously if jack and recordmydesktop are running. when they arent running everything is normal...any ideas? thanks in advance:)

You may be running out of headroom there. Is your cpu/ram maxed out when you try this?

---

### Post by Dark Hornet on 2008-12-01
> **markbuntu said:**
> It may, but let me try to get a better understanding of your problem. You have music through your headphones now but not your speakers right?
Is there a switch in your sound mixer for that?
If you turn off the digital output do your speakers work?

Well, I have finally had a bit more time to troubleshoot my sound issue...I have reinstalled my ALSA drivers, and I have even upgraded them to ALSA 1.0.18a.  I am still having the same issues...sound is great through my headphones with .mp3, .avi, etc. and the ONLY thing that I can get to play through my speakers are my .mkv High Def movie files...and they play perfectly in dolby dts sound.  This is really frustrating.  I have rechecked all of my settings, and nothing is muted...everything is turned up, I have no pulse streams getting in the way of ALSA (if that is possible)...I am at my wits end here.

---

### Post by eleniontolto on 2008-12-01
I've gone through and done most of the relevant steps in both this guide, the intrepid guide and a couple others you suggested and none have helped...

I had sound working just fine until I turned it on today and it wasn't working (except on select video files played via XBMC).  I get no startup sound and no navigation sounds.  I have also tried reinstalling sound components to reset defaults.  Any suggestions here?  It seems like all the video files that actually put out sound are files with ac3 audio.  Mp3, at least, does not work.

EDIT: nevermind, found somebody with teh same problem.  A temporary fix can be found here: [http://ubuntuforums.org/showthread.php?t=991219](http://ubuntuforums.org/showthread.php?t=991219)

---

### Post by markbuntu on 2008-12-02
> **Dark Hornet said:**
> Well, I have finally had a bit more time to troubleshoot my sound issue...I have reinstalled my ALSA drivers, and I have even upgraded them to ALSA 1.0.18a.  I am still having the same issues...sound is great through my headphones with .mp3, .avi, etc. and the ONLY thing that I can get to play through my speakers are my .mkv High Def movie files...and they play perfectly in dolby dts sound.  This is really frustrating.  I have rechecked all of my settings, and nothing is muted...everything is turned up, I have no pulse streams getting in the way of ALSA (if that is possible)...I am at my wits end here.

How do you have your speakers hooked up?

---

### Post by Dark Hornet on 2008-12-02
> **markbuntu said:**
> How do you have your speakers hooked up?

via a digital fiber cable...it was working perfectly for the past 8 months...ever since I built this box.

---

### Post by markbuntu on 2008-12-02
It is entirely possible that despite your considerable efforts pulseaudio is still running. In a terminal type

killall pulseaudio

and see if that fixes your problem. There is a way to get a digital ouput sink in pulseaudio that will give you more control, it is in the OP.

Also, some people have reported that Mplayer does not relinquish control of the digital output when it is closed. This is a known problem and is fixed in then latest version at launchpad. I do not know if any mplayer update from the repos has fixed this issue.

Anyway, please keep me informed of your progress on this.

---

### Post by Dark Hornet on 2008-12-02
> **markbuntu said:**
> It is entirely possible that despite your considerable efforts pulseaudio is still running. In a terminal type

killall pulseaudio

and see if that fixes your problem. There is a way to get a digital ouput sink in pulseaudio that will give you more control, it is in the OP.

Also, some people have reported that Mplayer does not relinquish control of the digital output when it is closed. This is a known problem and is fixed in then latest version at launchpad. I do not know if any mplayer update from the repos has fixed this issue.

Anyway, please keep me informed of your progress on this.

Well, I killed pulse audio and that did nothing...I even went back through the OP just to make sure of everything.  I found a few ALSA packages that I did not have installed...so I installed them via synaptic...rebooted...no luck.  Same situation.

---

### Post by markbuntu on 2008-12-04
Have you read this:

[http://alsa.opensrc.org/index.php/DigitalOut](http://alsa.opensrc.org/index.php/DigitalOut)

---

### Post by Spirallll on 2008-12-05
Thanks you so much,  I love you sound one

---

### Post by Setehk on 2008-12-29
Ah grand day indeed! After purging the ALSA software, my sound is finally working, thanks a bunch!

---

### Post by gruss on 2008-12-29
thanks man, helped me solve my issue as well!

---

### Post by markbuntu on 2008-12-30
I liked OS/2. Too bad it was so doomed from the start.

---

### Post by philidox on 2008-12-30
First and foremost let me say thanks for the thread it has help me out a lot!!!  Look I'll confess, my sound was working perfectly until I was messing around and jacked it up. I cannot figure out why my sound isn't working on my primary account.  I added a new user to test out the sound and it works just fine under the new account. I compared ALL the settings on my primary account to the new account and there identical from what I can see.  Does ANYBODY have any idea what settings I could change to restore my sound on my primary account.

---

### Post by Ng Oon-Ee on 2008-12-31
> **philidox said:**
> First and foremost let me say thanks for the thread it has help me out a lot!!!  Look I'll confess, my sound was working perfectly until I was messing around and jacked it up. I cannot figure out why my sound isn't working on my primary account.  I added a new user to test out the sound and it works just fine under the new account. I compared ALL the settings on my primary account to the new account and there identical from what I can see.  Does ANYBODY have any idea what settings I could change to restore my sound on my primary account.
Shot in the dark, but I guess you should primarily be interested in comparing anything within the ~/.pulse directory between the two user's home directories. Also check to make sure your primary account is member of the correct groups.

---

### Post by jesuspresley on 2009-01-10
I had problems with Firefox & Flash sounds (no sound at all). I read your hint from post one:

> **markbuntu said:**
> **Flash and java**
If you have flash9, you need to have
libflashsupport
to get your audio to work properly. If you have flash10 or higher, you do not need libflashsupport and should remove it.


Even though I have Flash10, I wondered if the *libflashsupport* package might cause the trouble. Itwas not installed at my system.
So I installed *libflashsupport* using Synaptics, restarted Firefox and everything worked.

You might want to consider this in your initial post.

---

### Post by baanya on 2009-01-11
Thanks a ton !! Very useful article for an absolute beginner on Linux like me!! :)

---

### Post by DestroyerOfTheSeas on 2009-01-18
alright, I completed all the aforementioned, I think.. but now I cannot get the Jack server to start and it obviously doesn't show up under PulseAudio Volume Control. 

I'm running Intrepid. 

All my Jack settings are default with Runtime and Monitor ticked off.. Here is a screenshot: [http://www.deleonspringscommunity.com/Screenshot.jpg](http://www.deleonspringscommunity.com/Screenshot.jpg)

Here is the message I'm getting from Jack..

> 
 20:20:12.951 Patchbay deactivated.
20:20:13.136 Statistics reset.
20:20:13.278 Startup script...
20:20:13.279 artsshell -q terminate
20:20:13.294 ALSA connection graph change.
20:20:13.722 Startup script terminated with exit status=256.
20:20:13.722 JACK is starting...
20:20:13.723 /usr/bin/jackd -R -t1000 -dalsa -dhw:0 -r44100 -p1024 -n3 -m
jackd 0.109.2
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
cannot use real-time scheduling (FIFO at priority 10) [for thread -1209067856, from thread -1209067856] (1: Operation not permitted)
cannot create engine
20:20:13.734 JACK was started with PID=11301.
20:20:13.742 JACK was stopped successfully.
20:20:13.743 Post-shutdown script...
20:20:13.743 killall jackd
20:20:13.933 ALSA connection change.
jackd: no process killed
20:20:14.158 Post-shutdown script terminated with exit status=256.
20:20:15.980 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.

Does someone know what's going on?

~/Cheers!

---

### Post by markbuntu on 2009-01-18
You cannot use the rt option in Intrepid.

---

### Post by SergeantOreo on 2009-01-29
Thank you sooo much Markbuntu! Your guide helped me configure all
my Alsa-related apps and settings and now I can record audio properly
in GTK RecordMyDesktop. :D

---

### Post by sebastian_buettrich on 2009-02-03
I had the same probs on an

IBM X40 
soundcard: card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 0: Intel ICH [Intel 82801DB-ICH4]

Ubuntu 8.10

After having spent one hour on the various troubleshooting tracks, finding everything looked ok,
 i came across the remark that "often Audio services are disabled by default" in Ubuntu. (???)

Checking System>Administration>Services

indeed, Audo Services unchecked. one click and everything worked.

This might save others some hours of trouble, i hope.

---

### Post by HotDogBunToo on 2009-02-07
Hey markbuntu excellent writeup!

It was literally too simple for me since I wound up skipping a vital step which was
**"One easy way that some people have fixed their sound problems is by creating a new user in System/Administration/Users and Groups and then logging in with that"**

Turns out that before in my old login my ALSA & Pulseaudio was pretty much crap with only the OSS working - but with new account everything is working like clockwork for the new user. Soooo now that it's just a matter of user config files, any idea what config files I should carry over to old user?  Otherwise I'm just gonna move everything to new account lol

---

### Post by Ng Oon-Ee on 2009-02-07
> **HotDogBunToo said:**
> Hey markbuntu excellent writeup!

It was literally too simple for me since I wound up skipping a vital step which was
**"One easy way that some people have fixed their sound problems is by creating a new user in System/Administration/Users and Groups and then logging in with that"**

Turns out that before in my old login my ALSA & Pulseaudio was pretty much crap with only the OSS working - but with new account everything is working like clockwork for the new user. Soooo now that it's just a matter of user config files, any idea what config files I should carry over to old user?  Otherwise I'm just gonna move everything to new account lol
Try going through your home directory, specifically looking for pulse or ALSA related stuff. Here's some files/folders to check (off the top of my head)

~/.asoundrc
~/.pulse
~/.gconf/system/pulseaudio

You can also search your home folder for files with pulse/alsa in their name...

---

### Post by HotDogBunToo on 2009-02-07
> **Ng Oon-Ee said:**
> Try going through your home directory, specifically looking for pulse or ALSA related stuff. Here's some files/folders to check (off the top of my head)

~/.asoundrc
~/.pulse
~/.gconf/system/pulseaudio

You can also search your home folder for files with pulse/alsa in their name...

ah cool, can't say if this'll work or not since I already made move to new account after abit of impatience of copying what I thought were some config files. But if my ALSA/Pulseaudio screws up again I'll be sure to keep those files/folders in mind 

p.s. what happened to the thank you buttons in here?

---

### Post by Ng Oon-Ee on 2009-02-08
> **HotDogBunToo said:**
> ah cool, can't say if this'll work or not since I already made move to new account after abit of impatience of copying what I thought were some config files. But if my ALSA/Pulseaudio screws up again I'll be sure to keep those files/folders in mind 

p.s. what happened to the thank you buttons in here?
After the server problems recently both the 'thank you' and 'solved' features were removed, no one knows when they'll be brought back.

And ya, things aren't really very hidden in the Unix file-system, everything is there if you just know where to look.

---

### Post by HotDogBunToo on 2009-02-09
> **Ng Oon-Ee said:**
> After the server problems recently both the 'thank you' and 'solved' features were removed, no one knows when they'll be brought back.

And ya, things aren't really very hidden in the Unix file-system, everything is there if you just know where to look.

Ah kinda sucks those features are removed, but understandable seeing server had probs & all.

But yea, I once again had sound problems with Pulseaudio in my new account (fiddling around with things like having VMWare work with Pulseaudio) and made yet another account, this time I just copied over the config stuff you specified and presto - everything works after restart haha.  So thanks again :cool:

---

### Post by Athena1 on 2009-02-11
Hi 

when i tested my sound card i got the foll result

Hi All..

I have some problem with my laptop. when i tested for sound cards i got following information.

lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Hewlett-Packard Company Unknown device 9602
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 11h HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 11h DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 11h Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 11h Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]
01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller
08:00.0 System peripheral: JMicron Technologies, Inc. Unknown device 2382
08:00.2 SD Host controller: JMicron Technologies, Inc. Unknown device 2381
08:00.3 System peripheral: JMicron Technologies, Inc. Unknown device 2383
08:00.4 System peripheral: JMicron Technologies, Inc. Unknown device 2384
09:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
0a:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 02)


Bus 005 Device 003: ID 046d:09b8 Logitech, Inc. 
Bus 005 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 03f0:171d Hewlett-Packard 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 093a:2510 Pixart Imaging, Inc. 
Bus 001 Device 001: ID 0000:0000  

cat /proc/asound/cards
 0 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0x92500000 irq 16
 1 [HDMI           ]: HDA-Intel - HDA ATI HDMI
                      HDA ATI HDMI at 0x92410000 irq 19

 cat /proc/asound/modules
 0 snd_hda_intel
 1 snd_hda_intel

 aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

arecord -l
**** List of CAPTURE Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1

According to that the sound card is STAC9250 for my Compaq presario CQ45AU series. When i modified the alsa-base code model to m6 nothing is working...i still havent fixed this sound problem in my laptop. Please can anyone help me with this????

---

### Post by dhanes420 on 2009-02-12
Thank you!

For some reason:

Audigy
If your Creative Audigy card is not giving you any sound, make sure the analog/digital check box in your sound mixer is unchecked.

After the latest update, that lil' sucker got checked.

Working fine now!

---

### Post by Gray Beard on 2009-02-15
I have Intrepid running on three boxes. Audio failed only on the one with a Sound Blaster Audigy2 ZS sound card. Turned out to be the check in the analog/digital checkbox. But before I found this thread, I tried a lot of other things and discovered this. Yesterday (2/14/09) I went to the GA Tech mirror and downloaded the Intrepid ISO (32-bit). I installed it and the sound worked fine until I updated. Then it quit. So I re-installed, went through the update package list (253 of them), culled all that contained the names "alsa" or "pulseaudio" (7 of them) and installed the rest. When I rebooted, the audio was dead. I don't know which package ticks the Audigy analog/digital checkbox but it appears that it isn't specifically identified as alsa or pulse audio. I hope this helps the developers a little in their search for the culprit and my thanks to all who contribute.

---

### Post by markbuntu on 2009-02-15
> **Gray Beard said:**
> I have Intrepid running on three boxes. Audio failed only on the one with a Sound Blaster Audigy2 ZS sound card. Turned out to be the check in the analog/digital checkbox. But before I found this thread, I tried a lot of other things and discovered this. Yesterday (2/14/09) I went to the GA Tech mirror and downloaded the Intrepid ISO (32-bit). I installed it and the sound worked fine until I updated. Then it quit. So I re-installed, went through the update package list (253 of them), culled all that contained the names "alsa" or "pulseaudio" (7 of them) and installed the rest. When I rebooted, the audio was dead. I don't know which package ticks the Audigy analog/digital checkbox but it appears that it isn't specifically identified as alsa or pulse audio. I hope this helps the developers a little in their search for the culprit and my thanks to all who contribute.

That problem has been around for a while and the audigy driver was most likely not updated but the driver defaults were reset. You guys should complain loudly to the alsa audigy driver devs that digital should be OFF by default.

---

### Post by dhanes420 on 2009-02-15
> **markbuntu said:**
> That problem has been around for a while and the audigy driver was most likely not updated but the driver defaults were reset. You guys should complain loudly to the alsa audigy driver devs that digital should be OFF by default.

I think I remember there were only PulseAudio updates, no ALSA  updates but I could be wrong.

---

### Post by stuartmcfadyen on 2009-02-21
Ubuntu 8.10 .... I have searched every forum I can find, installed and followed ALL the hints, tips, etc and still ...... WHEN I BOOT 8.10 I CAN NEVER BE CERTAIN THAT SOUND IS WORKING ! 
Sometimes, on a random basis, it works other times it does not. 
The only cure that guarantees 100% sucess to have sound is to run [COLOR="Red"]**sudo alsa force-reload**[/COLOR]. This 8.10 problem is SO STUPID ................ UBUNTU FIX IT !

---

### Post by markbuntu on 2009-02-21
> **stuartmcfadyen said:**
> Ubuntu 8.10 .... I have searched every forum I can find, installed and followed ALL the hints, tips, etc and still ...... WHEN I BOOT 8.10 I CAN NEVER BE CERTAIN THAT SOUND IS WORKING ! 
Sometimes, on a random basis, it works other times it does not. 
The only cure that guarantees 100% sucess to have sound is to run [COLOR="Red"]**sudo alsa force-reload**[/COLOR]. This 8.10 problem is SO STUPID ................ UBUNTU FIX IT !

If you have a gpu with HDMI or more than one sound device this can happen as the devices are not always detected in the same order every time so the default device can change. There is info on how to fix this in the link in the Multiple Sound Cards section of the OP.

btw, I have just posted a major edit that is an almost complete rewrite to the guide

---

### Post by Ng Oon-Ee on 2009-02-21
> **stuartmcfadyen said:**
> Ubuntu 8.10 .... I have searched every forum I can find, installed and followed ALL the hints, tips, etc and still ...... WHEN I BOOT 8.10 I CAN NEVER BE CERTAIN THAT SOUND IS WORKING ! 
Sometimes, on a random basis, it works other times it does not. 
The only cure that guarantees 100% sucess to have sound is to run [COLOR="Red"]**sudo alsa force-reload**[/COLOR]. This 8.10 problem is SO STUPID ................ UBUNTU FIX IT !
It's commendable that you first search for solutions and try out different things, but if your problem isn't solved you should ask, perhaps in a new thread or a related thread. All software has bugs, and if you don't give symptoms and help other volunteersr to examine your system, then those bugs won't go away, no matter how much you vent your frustration.

As markbuntu says, perhaps the device names are changing. I'd add that sometimes there can be race conditions in startup, where different scripts get executed almost at the same time, sometimes the order gets mixed up.

---

### Post by stuartmcfadyen on 2009-02-22
Thank you Mark for your technical references which I have read and where necessary installed/amended code. Sorry to say to no avail .... random sound still exists at startup !
My main point though is this ..... it is 2009 ....and having been in IT for over 40 years I thought we had passed the stage of Operating Systems struggling to load the correct drivers etc. 
If Linux is to continue its excellent growth in popularity **(and I want it to)**, it must overcome this type of problem FAST so that newbies are not put off at the first installation hurdle.  
One only has to wonder at the volume of Forum correspondence related to sound problems.
Thanks again for your help, and I shall say no more. 
I will continue to use **[COLOR="Red"]sudo alsa force-reload[/COLOR]** as the solution to my problem.

---

### Post by stuartmcfadyen on 2009-02-23
Despite my last post saying I would "say no more" I am pleased to report that I HAVE SOLVED MY PROBLEM OF INTERMITTENT SOUND AT BOOT ....... as follows ..... 

(Bear in mind that I only have on-board sound installed on my PC).

1. **Change** all entries in SYSTEM PREFERENCES SOUND to "ALSA - Advanced Linux Sound Architecture"

2. **Edit**  /etc/modprobe.d/alsa-base (lines altered by [COLOR="Red"]**#**[/COLOR] shown in red, as follows)

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
[COLOR="Red"]# install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe --quiet snd-ioctl32 ; : ; }
# install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }
# install snd-pcm /sbin/modprobe --ignore-install snd-pcm && { /sbin/modprobe --quiet snd-pcm-oss ; : ; }
# install snd-mixer /sbin/modprobe --ignore-install snd-mixer && { /sbin/modprobe --quiet snd-mixer-oss ; : ; }
# install snd-seq /sbin/modprobe --ignore-install snd-seq && { /sbin/modprobe --quiet snd-seq-midi ; /sbin/modprobe --quiet # snd-seq-oss ; : ; }
# install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi && { /sbin/modprobe --quiet snd-seq-midi ; : ; }[/COLOR]
# Cause optional modules to be loaded above sound card driver modules
[COLOR="Red"]# install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-#synth ; }
# install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }[/COLOR]

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from beeing loaded as first soundcard
options snd-pcsp index=-2
[COLOR="Red"]options snd-hda-intel model=STAC9221 index=-0[/COLOR]

This has given me 10 out of 10 successful boots with sound working OK in Skype, MP3 and DVD players .... Thanks again to all .... maybe this will help others ? :D

---

### Post by mc4man on 2009-02-23
> culled all that contained the names "alsa" or "pulseaudio" (7 of them) and installed the rest. When I rebooted, the audio was dead. I don't know which package ticks the Audigy analog/digital checkbox but it appears that it isn't specifically identified as alsa or pulse audio.

The update was/is this, it appears they have got it right, the switch must be off for analog output (it's in the kernel upgrade, not a standalone update

> ALSA: emu10k1 - Add more invert_shared_spdif flag to Audigy models

---

### Post by markbuntu on 2009-02-23
Well that explains that.

---

### Post by RealG187 on 2009-02-23
[http://ubuntuforums.org/showthread.php?t=1071708](http://ubuntuforums.org/showthread.php?t=1071708)

My laptop has an HDMI port, is there a command I can type that will list all my audio hardware?

---

### Post by markbuntu on 2009-02-24
Well no, not really. You can look here for an explanation about getting hardware info

[http://ubuntuforums.org/showthread.php?p=6628921](http://ubuntuforums.org/showthread.php?p=6628921)

You should really read the OP. It was just updated with an almost complete rewrite.

---

### Post by RealG187 on 2009-02-24
What's the OP

---

### Post by markbuntu on 2009-02-24
Oh, sorrry for the geek spreak, the OP is the first post in a thread, the Original Post.

---

### Post by jaklumen on 2009-02-26
Very thorough, very comprehensive guide.

Right now, though, I am having difficulty getting multiple application sound sharing to work.  Before, I was using a SB Live card (emu10k1 chip) to handle sound mixing through hardware but I believe the card stopped working, and I am using an Audigy SE card (CA0106 chip).

For some reason I do not have Multimedia Systems Selector in System Preferences.

I had to do a reinstall and while I used psyke83's guide in the past I have not implemented anything from there yet.  I have otherwise followed your guide as thoroughly as I can-- I think.

Please have patience with me-- I have gone through this at least a half dozen times and followed all the major guides and I am still having trouble.

---

### Post by markbuntu on 2009-02-26
If you don't have the Multimedia Systems Selector then you are missing some gstreamer stuff. You should get ALL the gstreamer packages with SYnaptic package manager. Or you can just get

ubuntu-restricted-extras

This is a metapackage of all the restricted codecs and plugins, etc. It is all explained in either this guide or the quick start guide here. If you have a new install I would recommend starting with this guide here first

[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

If that does not fix you up you can come back to the 10,000 page guide.

---

### Post by jaklumen on 2009-03-02
> **markbuntu said:**
> If you don't have the Multimedia Systems Selector then you are missing some gstreamer stuff. You should get ALL the gstreamer packages with SYnaptic package manager. Or you can just get

ubuntu-restricted-extras

This is a metapackage of all the restricted codecs and plugins, etc. It is all explained in either this guide or the quick start guide here. If you have a new install I would recommend starting with this guide here first

[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

If that does not fix you up you can come back to the 10,000 page guide.
Everything's installed.  I found it by putting "gstreamer-properties" into a terminal, but is there a way to access it through the menu?  I selected "Simultaneous output..." under Device for Default Output.

---

### Post by markbuntu on 2009-03-02
Multimedia System Selector should be in them menus under System/Preferences. It might just be hidden. You can use System/Preferences/Main Menu to find it and unhide it.

---

### Post by AlexTepes on 2009-03-15
I wish i could have OSD back :(

---

### Post by carlosIII on 2009-03-22
hello,
this is a wonderful guide.
just with installation i had regular sound (for playing mp3s and stuff)
but i use other applications like hydrogen or ardour through jack, and this were not working well.
i followed the steps in this guide, but, i still cant make get hydrogen or anything else to work properly with jack: when i use hydrogen and jack the sound becomes slow and noisy. and if i add a jackeq or something it gets worst.
can you recommend me anything to configure it rigth?

thanks
Carlos

---

### Post by markbuntu on 2009-03-22
> **carlosIII said:**
> hello,
this is a wonderful guide.
just with installation i had regular sound (for playing mp3s and stuff)
but i use other applications like hydrogen or ardour through jack, and this were not working well.
i followed the steps in this guide, but, i still cant make get hydrogen or anything else to work properly with jack: when i use hydrogen and jack the sound becomes slow and noisy. and if i add a jackeq or something it gets worst.
can you recommend me anything to configure it rigth?

thanks
Carlos

Did you look in the links for setting up jack?

You need to set jack and hydrogen and ardour to your sound card specs to get best performance or things slow down with resampling. Some cards only do 48000 and some only do 44100.

You also need a fairly powerful machine with lots of ram to do this, what are your machine specs and what OS are you using?

---

### Post by TimeBecomes on 2009-03-22
Hi, this is my first post.  I'm not completely sure if this is the best thread to post this in but it is likely useful to someone and this is the best match I could find.  I have a Gateway PC with an HDA intel card, SigmaTel STAC9221 A1.  I spent over a day trying to get sound to work (updated ALSA, followed the instructions to use OSS instead, etc) and nothing worked.  Then I did some googling and found a thread where someone suggested plugging the speakers into the blue jack rather than the green one.  It worked instantly.  I even reinstalled Ubuntu just to see if it would work without all the things I had previously changed (I'm a complete novice and hadn't customized anything I would miss), and it again worked instantly.

---

### Post by carlosIII on 2009-03-22
> **markbuntu said:**
> Did you look in the links for setting up jack?

You need to set jack and hydrogen and ardour to your sound card specs to get best performance or things slow down with resampling. Some cards only do 48000 and some only do 44100.

You also need a fairly powerful machine with lots of ram to do this, what are your machine specs and what OS are you using?

ok, ill check the links you mention
for now: i have an msi u100 (1.6 ghz and igb ram)

edit:
i have noticed that when i start jack it immediatly "turns red" and lots of Xrun, and im not using anyother audio software.
other question, i have all settings to pulseaudio like was said in this guide, do i have to set anything in special in the pulseaudio applet? i mean those options Default 
server, sink and source.

thanks for the response

---

### Post by kylea on 2009-03-23
Applied this deb [http://ppa.launchpad.net/themuso/ppa/ubuntu](http://ppa.launchpad.net/themuso/ppa/ubuntu) jaunty main to repositories and updated to pulse0.9.15 and alsa 1.0.19 and previous choppy audio is now excellent.

---

### Post by markbuntu on 2009-03-23
> **carlosIII said:**
> ok, ill check the links you mention
for now: i have an msi u100 (1.6 ghz and igb ram)

edit:
i have noticed that when i start jack it immediatly "turns red" and lots of Xrun, and im not using anyother audio software.
other question, i have all settings to pulseaudio like was said in this guide, do i have to set anything in special in the pulseaudio applet? i mean those options Default 
server, sink and source.

thanks for the response

To get rid of xruns tou need to adjust the frames/period and periods/buffer settings in jackcontrol. This is highly dependent on your hardware so it may not be possible to get the low latency you want. If you are using the rt kernel you also need to check the Realtime box.

For using pulseaudio and jack together you need to follow the **Pulseaudio through Jack** instructions very carefully. Those "Defaults" you mention are for rtp networking and do not need to be changed for normal use. You can change the default sink and source for your applications in pavucontrol.

---

### Post by Justbill on 2009-03-23
I tried this: [http://ubuntuforums.org/showthread.php?t=1099930&highlight=problems+recording+audacity](http://ubuntuforums.org/showthread.php?t=1099930&highlight=problems+recording+audacity) 

solution to my problem, and now I have more problems!

Can anyone tell me how to get back to  what came by default in Ubuntu 8.10 Intrepid? I would like to start from scratch here

What I  am trying to accomplish is to be able to record guitar music into Audacity. My computer is a Compaq Presario SR1426NX, it has the "firewire" stuff on the front, and I had previously been recording guitar music through the "firewire" in Audacity, using "Ultimate Edition".

Any help would be greatly appreciated!

---

### Post by markbuntu on 2009-03-23
> **Justbill said:**
> I tried this: [http://ubuntuforums.org/showthread.php?t=1099930&highlight=problems+recording+audacity](http://ubuntuforums.org/showthread.php?t=1099930&highlight=problems+recording+audacity) 

solution to my problem, and now I have more problems!

Can anyone tell me how to get back to  what came by default in Ubuntu 8.10 Intrepid? I would like to start from scratch here

What I  am trying to accomplish is to be able to record guitar music into Audacity. My computer is a Compaq Presario SR1426NX, it has the "firewire" stuff on the front, and I had previously been recording guitar music through the "firewire" in Audacity, using "Ultimate Edition".

Any help would be greatly appreciated!

I do not use audacity myself as I found it too troublesome for my liking but let's see what we can do to restore your system and get it configured properly before you start fooling around again.

If you want to restore your intrepid you first need to uninstall OSS4. The directions for that should be linked to where the directions for installing it are. Then you need to reinstall ALSA and pulseaudio packages which are all listed in the OP of this thread. You can just follow the directions in the OP.

To get audacity working with your firewire stuff I believe you will need freebob or ffado but I could be wrong about that. Once you get your system back the way it was you should probably search for an existing thread or failing that start a new thread about audacity and firewire. I am sure that someone is doing that and would probably help you out.

---

### Post by aviynw on 2009-03-25
great guide, but I think you should also link to [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449) and [http://ubuntuforums.org/showthread.php?p=4928900](http://ubuntuforums.org/showthread.php?p=4928900) and any other sound guides that may exist.  You should also add any fixes in those other guides that are not listed here.  One fix which was not listed here as far as I can tell but elsewhere is fixing sound permission problems.  
a quote from the first link 
> 
A very common cause for a user to not have sound is not having his/her username in the /etc/group.

Thanks to rustybutt for this simple check.

```


grep 'audio' /etc/group

```
You should see a line similar to
```


audio:x:29:

```
followed by a username i.e. if the username is "ubuntu" then you should see
```


audio:x:29:ubuntu

```
. If you see something else i.e.
```


audio:x:29:root

```
you should add your username to the file by doing
```


 sudo nano /etc/group

```
. Now find the line that looks like
```


audio:x:29:root

```
and change it to
```


audio:x:29:root,moocow 

```
(the original quote had a colon between root and moocow, but that is not correct on my ubuntu 8.10 installation.  I've mentioned that in the quoted thread)
only replacing moocow with your real username.

Hit CTRL + 0 to save, then CTRL + X to exit. That's the end of that


---

### Post by markbuntu on 2009-03-25
There is no link to ([http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)) for a number of reasons. The OP has not been updated for over 2 years and the link from it is dead. Much of the informations is not really revelant for Hardy and Intrepid and it causes many people problems. It is also a sticky so people should have no problem finding it.

I already have a link to psyke83's guide at [http://ubuntuforums.org/showthread.php?p=4928900](http://ubuntuforums.org/showthread.php?p=4928900) in the Sound Server setup section. It was one of the first links I put in the guide but I am hesitant to make it more prominent. Though it works for many people it also causes many people to end up with problems, myself included. It also involves getting packages from someone's private repository which is not necessarily the safest thing to do.

As far as I know, group audio has been deprecated since Hardy and is no longer in use. Its functionality has been replaced by the pulse groups. Of course if you remove pulseaudio you will lose this functionality so you may need a group audio but the whole purpose of this guide is getting pulseaudio working properly, not removing it. My sound works just fine without any group audio.

---

### Post by jgossage on 2009-03-26
Thank you for a most informative guide.

Unfortunately, after trying all your recommendations I still have a problem.

I am running Intrepid on a new Dell XPS M1330 laptop. Initially the sound worked fine. However, just before starting a trip to Mexico, I had to play with the sound configuration to try to correct an echo problem when using a microphone in Ekiga. Eventually I came to the conclusion that the only solution was to use a USB headset and took off with my laptop for Mexico. When I booted up the only sound I had was some crackling of a length similar to what I would expect as normal login and initial Gnome desktop presentation. I have been totally unable to find any solution since. Any help you could provide will be greatly appreciated as I am working with my son on a joint project and it is very inefficient not being able to talk to him as we work.

My hardware and driver settings follow:

jonathan@socrates:~$ sudo /bin/bash
[sudo] password for jonathan: 
root@socrates:~# lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8400M GS (rev a1)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
09:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
root@socrates:~# 
root@socrates:~# 
root@socrates:~# lsusb
Bus 007 Device 004: ID 05a9:2640 OmniVision Technologies, Inc. 
Bus 007 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 002: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 007: ID 0a5c:4503 Broadcom Corp. 
Bus 001 Device 006: ID 0a5c:4502 Broadcom Corp. 
Bus 001 Device 005: ID 413c:8126 Dell Computer Corp. Wireless 355 Bluetooth
Bus 001 Device 004: ID 0a5c:4500 Broadcom Corp. 
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 004: ID 045e:00b9 Microsoft Corp. Wireless Optical Mouse 3.0
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
root@socrates:~# 
root@socrates:~# 
root@socrates:~# cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xf6ffc000 irq 21
root@socrates:~# 
root@socrates:~# 
root@socrates:~# cat /proc/asound/modules
 0 snd_hda_intel
root@socrates:~# 
root@socrates:~# 
root@socrates:~# aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
root@socrates:~# 
root@socrates:~# 
root@socrates:~# arecord -l
**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 3/3
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
root@socrates:~#

---

### Post by Yeti can't ski on 2009-03-27
> **jgossage said:**
> Thank you for a most informative guide.

Unfortunately, after trying all your recommendations I still have a problem.

I am running Intrepid on a new Dell XPS M1330 laptop. Initially the sound worked fine.

Hello there, I have the same computer and recently also had some sound problems after using Skype and not Ekiga (shame on me!). 

I am absolutely a rookie with Ubuntu, but may be I can help a bit. 

I don't know what you have already tried, so sorry if I am being repetitive (note: references to Menu names can be a little imprecise because I am not using my computer now and I am basing comments on my memory). 

I would suggest you to: 

(i) check if the system recognizes your sound card by going to terminal and doing "aplay -l". The output should contain a reference to your installed hardware. If it doesn't, then you are in deeper trouble; 

(ii) check if no volume button has been zeroed down or some strange sound option has been automatically selected (it may happen after an update or use of an application). The best way of checking these things IMHO is with "gnome-alsamixer" (you can add it with Synaptic, on "System\Administration\Synaptic package administration" and then open it with "Applications\Sound & Video\gnome-alsamixer"). It has a much better interface (all in one screen!) than regular Alsamixer or gnome volume control. To have an idea of how it looks: 

[http://lh4.ggpht.com/mgreenly/R_ejooqe7kI/AAAAAAAAAR8/OWy347hnQVI/s400/Screenshot-GNOME+ALSA+Mixer.png](http://lh4.ggpht.com/mgreenly/R_ejooqe7kI/AAAAAAAAAR8/OWy347hnQVI/s400/Screenshot-GNOME+ALSA+Mixer.png)

(iii)check if after an update the system has not stripped you out of the privileges for using pulseaudio. Go to "System/Administration/Users & Groups", unlock it, and confirm that you and root user have permission for any group having "pulse" in its name (there three or four of them);  

(iv) check if you are not missing any important packages (always using Synaptic). They use very little disk space, so in this case, if in doubt it is better to have the package. Check out a list in the beginning of Markubuntu's post here: 

[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

In my case, I think it was particularly helpful to add this one: "asoundconf-gtk".

Hope some of this will help you. I was going crazy with the sound problem. 

Good luck!

---

### Post by jgossage on 2009-03-27
Thanks for the response. I have actually tried everything you suggested without any success. On my system I get sound, just not useful sound. I get crackling static instead of anything recognizable. It was working one day and the next day when I rebooted only crackling.

Regards

Jonathan Gossage

---

### Post by wbee on 2009-03-27
Mark and Others,

Mark,thank you for putting this together. I would have sent a private message thank you note,but I read your disclaimer,so here it is.:-)

I've been reading Mark's ten thousand page sound guide a little bit at a time,trying to get the hang of how Linux audio works.

That said,I have a specific question.

Thanks to the kindness of other posters and trial and error,I have gotten a Philips chip saa7134 TV tuner card to show video,using the tvtime software. But I can't get the audio to work.

The owner's manual tells me the other chip on the card is TDA 8275. The roster of TV tuner cards that shows all the numbers tells me that my card is Tuner=82,but there is no listing for the audio portion. There is a number for "TDA 8290+75,but that (alsa=54) does not work either. Does that mean what I would understand to mean TDA 8290.75 or is it confusing shorthand? My terminal list shows it recognizes tuner=2.

Using the XP software,I have the option of using "713x Analogue Audio Capture" or the audio output from my Soundblaster Audigy SE card.

In the former instance,I get the video and audio of the TV signal. In the later instance, I get the video from the TV signal and can listen to a compact disk or streaming FM,to name two.

Do I properly infer from "713x Analogue Audio Capture" that the audio portion is originating from the saa7134 chip? Does that mean the TDA 8275 is the FM radio audio chip or is it a shared function because TV audio is within FM radio frequencies?

All that said,what should I download,what should I  save and add to modules, and what sliders and speakers' preferences should I be using to get audio/video from the TV tuner card and,if possible,video from the TV tuner card and audio from the compact disk or streaming FM?

------------

Thank you.

---

### Post by Yeti can't ski on 2009-03-27
> **jgossage said:**
> Thanks for the response. I have actually tried everything you suggested without any success. On my system I get sound, just not useful sound. I get crackling static instead of anything recognizable. It was working one day and the next day when I rebooted only crackling.

Regards

Jonathan Gossage

I see. Sorry then for not bringing anything new. If you have a Live CD at hand you could boot through it and test the sound. With this, you could at least exclude any hardware problem (a loose wire or somethint like that).

---

### Post by beerguzzler on 2009-03-27
> **jgossage said:**
> Thanks for the response. I have actually tried everything you suggested without any success. On my system I get sound, just not useful sound. I get crackling static instead of anything recognizable. It was working one day and the next day when I rebooted only crackling.

Regards


Jonathan Gossage


i've had crackling sound before. try muting the microphone in the volume settings. worked for me.

---

### Post by markbuntu on 2009-03-27
> **jgossage said:**
> Thanks for the response. I have actually tried everything you suggested without any success. On my system I get sound, just not useful sound. I get crackling static instead of anything recognizable. It was working one day and the next day when I rebooted only crackling.

Regards

Jonathan Gossage

Did you try reinstalling alsa?
That can sometimes fix problems like you are having.
Did you ever get that usb headset?
Usb headests are cheap and easy to set up and use.

---

### Post by markbuntu on 2009-03-27
> **wbee said:**
> Mark and Others,

Mark,thank you for putting this together. I would have sent a private message thank you note,but I read your disclaimer,so here it is.:-)

I've been reading Mark's ten thousand page sound guide a little bit at a time,trying to get the hang of how Linux audio works.

That said,I have a specific question.

Thanks to the kindness of other posters and trial and error,I have gotten a Philips chip saa7134 TV tuner card to show video,using the tvtime software. But I can't get the audio to work.

The owner's manual tells me the other chip on the card is TDA 8275. The roster of TV tuner cards that shows all the numbers tells me that my card is Tuner=82,but there is no listing for the audio portion. There is a number for "TDA 8290+75,but that (alsa=54) does not work either. Does that mean what I would understand to mean TDA 8290.75 or is it confusing shorthand? My terminal list shows it recognizes tuner=2.

Using the XP software,I have the option of using "713x Analogue Audio Capture" or the audio output from my Soundblaster Audigy SE card.

In the former instance,I get the video and audio of the TV signal. In the later instance, I get the video from the TV signal and can listen to a compact disk or streaming FM,to name two.

Do I properly infer from "713x Analogue Audio Capture" that the audio portion is originating from the saa7134 chip? Does that mean the TDA 8275 is the FM radio audio chip or is it a shared function because TV audio is within FM radio frequencies?

All that said,what should I download,what should I  save and add to modules, and what sliders and speakers' preferences should I be using to get audio/video from the TV tuner card and,if possible,video from the TV tuner card and audio from the compact disk or streaming FM?

------------

Thank you.

Does the tv tuner show up in aplay -l or cat /proc/asound/cards or in the pulseaudio volume control?
Gather up the hardware information and post it here and let's see ehat we can do.

A lot of people are having difficulties with their tv tuner cards so you are not alone in this. I don't know much about them. I don't watch tv.

---

### Post by jgossage on 2009-03-27
> **markbuntu said:**
> Did you try reinstalling alsa?
That can sometimes fix problems like you are having.
Did you ever get that usb headset?
Usb headests are cheap and easy to set up and use.

I am reluctant to reinstall ALSA because so much of the system goes with it. Any problem that occurs could lead to a completely trashed system and I cannot afford to have this system out of action right now. 

I would be better served to wait for Jaunty which will be out at a time when I could safely trash the system and re-install. If re-installing ALSA did not mean having to do a complete desktop re-install as well it might be an option.

Incidentally, a previous poster's suggestion that the crackling might be coming from the microphone turned out to be correct. When I muted the microphone, I get no sound at all.

Regards

Jonathan Gossage

---

### Post by markbuntu on 2009-03-27
The desktop package is just a meta-package list sort of thing of what is installed on your system. I have done this a bunch of times without problems.

Anyway, glad you got that figured out?

---

### Post by jgossage on 2009-03-27
> **markbuntu said:**
> The desktop package is just a meta-package list sort of thing of what is installed on your system. I have done this a bunch of times without problems.

Anyway, glad you got that figured out?

Tried re-installing Alsa with no joy. With the microphone muted I get no sound and with it enabled I get crackling when I should get sound. I guess the next step is to do as another poster suggested, get a Live CD and test that way to see if I have a potential hardware problem.

Regards and thankyou for your suggestions.

Jonathan Gossage

---

### Post by jlh68 on 2009-03-27
I also haave a sound problem.  To start when I do: 

john@Eagle:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 2: default [PnP Audio Device        ], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

As you can see itonly shows one device.  I know I have a sound card built into my MoBo and I also have a PCI video capture card that has sound capabilities.  My MoBo sound edvice is a Via 82xx, and the capture card uses a brooktree BT878.

Does the via82xx list as the PnP device or is it another device?

In any case my sound is just "white noise" no matter what I do.  So I need help in solving my sound problem.  

I am using Ubuntu 8.10 and had sound for awhile using it, but somewhere the sound broke.

---

### Post by markbuntu on 2009-03-27
The via and BT878 should list in lspci. You should also check with cat /proc/asound/cards and /modules to see if they are being found and the modules loaded but it does not look likely.

What did you do before the sound broke?
Did you get some updates?

---

### Post by jlh68 on 2009-03-28
I am not sure if an update caused the problem or not.  I am relative3ly new at the tweaking of a Linux system.  I might have caused it after an update possibley borke it.  Who knows at this point.  Of course I like being able to do stuff with Linux, and most of the time I have a good experience tweaking. 

Right now I would like to get the sound to work from the Mobo sound card.  I have not used the video capture card yet.  I hope to use it soon in the capture of my VHS taapes to DVD, to resduce the storage volume and to better preserve the program material.  I also want to do the same with my vinyl records and my cassette tapes.

I will go to the desktop and look where you saaid for the audio cards and see if i can get all recongnized.

Thanks.

---

### Post by jlh68 on 2009-03-28
Here is what shows in cat /proc/asound/cards:

john@Eagle:~$ cat /proc/asound/cards
 1 [default        ]: USB-Audio - PnP Audio Device        
                      PnP Audio Device         at usb-0000:00:02.0-7, full speed
 2 [Bt878          ]: Bt87x - Brooktree Bt878
                      Brooktree Bt878 at 0xfdffe000, irq 16

lspci shows this:
00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev f3)
00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3)
00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev f2)
00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev f2)
00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev f3)
00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev f3)
00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev f3)
00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev f3)
00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:01.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev c0)
01:06.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
01:06.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
01:07.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 62)
01:07.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 62)
01:07.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 65)
05:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7300 GT] (rev a1)

/proc/asound/modules caused the following message: bash: /proc/asound/modules: Permission denied

What is next for me to try?

---

### Post by Taus on 2009-03-28
Awesome guide!! tons of useful hints and tips.

I was wondering if any of you sound gurus knows if the x-fi sound card works with s/pdif in ubuntu?

I tried the S/PDIF guide/link in your post with no luck as well.

I have been struggling with this in ages so any hint or point in direction would be very much appreciated.

---

### Post by wbee on 2009-03-28
Mark and Others:

--The Philips chip saa 7134 video was playing well just after a reinstall of 8.10. The menu on the speaker inset was set to SAA 7134(alsa mixer). I could not get the TV signal's audio,but I could play a cd in the rhythm player with excellent quality. Switching between the menu settings for CAO1106(alsa mixer) and saa7134 alsa mixer made no difference in the excellent sound quality. However,when I set the tvtime tuner to a channel that was not recognized,neither setting would furnish audio.

--I then downloaded the updates and the tvtime no longer worked,though the rhythm player's cd function remained excellent.

--I downloaded the supported nvidia proprietary drivers and the tvtime worked again. This time the the sound quality was truly bad,because it was picking up "noise" from the TV video signal. That is,the video and audio distortion were synchronized. I could get the audio from the cd, from any channel,from either menu setting.

--You asked me about the pulse audio volume settings. I checked the synaptic list and pulse audio is a filled in green square,but no sliders.

--Here are the terminal settings you requested:

aplay -l

```
ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 2: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 3: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
wbee@ubuntu:~$ 
```

cat/proc/asoundcards

```
bash: cat/proc/asound/cards: No such file or directory
```\

A few more you did not request:




Here is  sudo lshw -C multimedia :

```
 *-multimedia:0          
       description: Multimedia controller
       product: SAA7131/SAA7133/SAA7135 Video Broadcast Decoder
       vendor: Philips Semiconductors
       physical id: 6
       bus info: pci@0000:04:06.0
       version: d1
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=saa7134 latency=64 maxlatency=255 mingnt=255 module=saa7134

```

Here is dmesg:

```
15.920123] saa7133[0]: i2c eeprom f0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   16.224198] tuner' 1-004b: chip found @ 0x96 (saa7133[0])
[   16.504065] tuner-simple 1-004b: creating new instance
[   16.504070] tuner-simple 1-004b: type set to 2 (Philips NTSC (FI1236,FM1236 and compatibles))
[   16.513049] saa7133[0]: registered device video0 [v4l2]
[   16.513092] saa7133[0]: registered device vbi0
[   16.547711] saa7134 ALSA driver for DMA sound loaded
[   16.548426] saa7133[0]/alsa: saa7133[0] at 0xfebff800 irq 18 registered as card -2]
```

Here is the line from the modprobe:

```
-rw-r--r-- 1 root root   84 2009-03-28 13:56 saa7134

```



Here is lspci:

```
04:06.0 Multimedia controller: Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast Decoder (rev d1)

```

On one hand,I'm tempted to post asking for a card that works,but on the other hand,I want to learn why it's not working and how to fix it.

---------------

Thank you.

---

### Post by wbee on 2009-04-01
Bump.

---

### Post by markbuntu on 2009-04-01
> **jlh68 said:**
> Here is what shows in cat /proc/asound/cards:

john@Eagle:~$ cat /proc/asound/cards
 1 [default        ]: USB-Audio - PnP Audio Device        
                      PnP Audio Device         at usb-0000:00:02.0-7, full speed
 2 [Bt878          ]: Bt87x - Brooktree Bt878
                      Brooktree Bt878 at 0xfdffe000, irq 16

lspci shows this:
00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev f3)
00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3)
00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev f2)
00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev f2)
00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev f3)
00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev f3)
00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev f3)
00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev f3)
00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:01.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev c0)
01:06.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
01:06.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
01:07.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 62)
01:07.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 62)
01:07.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 65)
05:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7300 GT] (rev a1)

/proc/asound/modules caused the following message: bash: /proc/asound/modules: Permission denied

What is next for me to try?

Well, lspci is not showing your on-board sound so check in the bios that it is turned on.

---

### Post by markbuntu on 2009-04-01
> **Taus said:**
> Awesome guide!! tons of useful hints and tips.

I was wondering if any of you sound gurus knows if the x-fi sound card works with s/pdif in ubuntu?

I tried the S/PDIF guide/link in your post with no luck as well.

I have been struggling with this in ages so any hint or point in direction would be very much appreciated.

You are lucky if the x-fi works at all. Are you sing OSS4?

---

### Post by markbuntu on 2009-04-01
> **wbee said:**
> Mark and Others:

--The Philips chip saa 7134 video was playing well just after a reinstall of 8.10. The menu on the speaker inset was set to SAA 7134(alsa mixer). I could not get the TV signal's audio,but I could play a cd in the rhythm player with excellent quality. Switching between the menu settings for CAO1106(alsa mixer) and saa7134 alsa mixer made no difference in the excellent sound quality. However,when I set the tvtime tuner to a channel that was not recognized,neither setting would furnish audio.

--I then downloaded the updates and the tvtime no longer worked,though the rhythm player's cd function remained excellent.

--I downloaded the supported nvidia proprietary drivers and the tvtime worked again. This time the the sound quality was truly bad,because it was picking up "noise" from the TV video signal. That is,the video and audio distortion were synchronized. I could get the audio from the cd, from any channel,from either menu setting.

--You asked me about the pulse audio volume settings. I checked the synaptic list and pulse audio is a filled in green square,but no sliders.

--Here are the terminal settings you requested:

aplay -l

```
ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 2: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 3: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
wbee@ubuntu:~$ 
```

cat/proc/asoundcards

```
bash: cat/proc/asound/cards: No such file or directory
```\

A few more you did not request:




Here is  sudo lshw -C multimedia :

```
 *-multimedia:0          
       description: Multimedia controller
       product: SAA7131/SAA7133/SAA7135 Video Broadcast Decoder
       vendor: Philips Semiconductors
       physical id: 6
       bus info: pci@0000:04:06.0
       version: d1
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=saa7134 latency=64 maxlatency=255 mingnt=255 module=saa7134

```

Here is dmesg:

```
15.920123] saa7133[0]: i2c eeprom f0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   16.224198] tuner' 1-004b: chip found @ 0x96 (saa7133[0])
[   16.504065] tuner-simple 1-004b: creating new instance
[   16.504070] tuner-simple 1-004b: type set to 2 (Philips NTSC (FI1236,FM1236 and compatibles))
[   16.513049] saa7133[0]: registered device video0 [v4l2]
[   16.513092] saa7133[0]: registered device vbi0
[   16.547711] saa7134 ALSA driver for DMA sound loaded
[   16.548426] saa7133[0]/alsa: saa7133[0] at 0xfebff800 irq 18 registered as card -2]
```

Here is the line from the modprobe:

```
-rw-r--r-- 1 root root   84 2009-03-28 13:56 saa7134

```



Here is lspci:

```
04:06.0 Multimedia controller: Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast Decoder (rev d1)

```

On one hand,I'm tempted to post asking for a card that works,but on the other hand,I want to learn why it's not working and how to fix it.

---------------

Thank you.

I am not very familiar with tv cards or tvtime but I have noticed a number of posts around here from others with similar problems. Your best bet would be to do a forum search for tvtime or your capture card. Sorry I can not be more helpful. Let me know how you make out.

---

### Post by Baasha on 2009-04-01
Hi,
I have followed all the instructions in this post (I think) and it certainly has given me some impprovements, so thanks for that.  But I still have some weird problems.  When I play a cd with Rythmbox I get sound from FL, FR, Center, and very low volume from LFE, but no sound from RR, or RL.  I am set up for 5.1 output and all six channels show on pavmeter and all the volumes at normal levels.  But then if I run speaker-test -Dplug:surround51 -c6 -l1 -twav I get different results: 
O Front Left works
4 Center no sound
1 Front Right works
3 Rear Right sound comes from Center
2 Rear Left sound comes from Center
5 LFE no sound

Do you have any suggestions as to what I should try next?

Here is the results from various files, but I don't see anything out of the ordinary:

bob@ubuntu:~$ lspci
00:00.0 Host bridge: nVidia Corporation nForce2 IGP2 (rev a2)
00:00.1 RAM memory: nVidia Corporation nForce2 Memory Controller 1 (rev a2)
00:00.2 RAM memory: nVidia Corporation nForce2 Memory Controller 4 (rev a2)
00:00.3 RAM memory: nVidia Corporation nForce2 Memory Controller 3 (rev a2)
00:00.4 RAM memory: nVidia Corporation nForce2 Memory Controller 2 (rev a2)
00:00.5 RAM memory: nVidia Corporation nForce2 Memory Controller 5 (rev a2)
00:01.0 ISA bridge: nVidia Corporation nForce2 ISA Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation nForce2 SMBus (MCP) (rev a2)
00:02.0 USB Controller: nVidia Corporation nForce2 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation nForce2 USB Controller (rev a3)
00:02.2 USB Controller: nVidia Corporation nForce2 USB Controller (rev a3)
00:04.0 Ethernet controller: nVidia Corporation nForce2 Ethernet Controller (rev a1)
00:05.0 Multimedia audio controller: nVidia Corporation nForce Audio Processing Unit (rev a2)
00:06.0 Multimedia audio controller: nVidia Corporation nForce2 AC97 Audio Controler (MCP) (rev a1)
00:08.0 PCI bridge: nVidia Corporation nForce2 External PCI Bridge (rev a3)
00:09.0 IDE interface: nVidia Corporation nForce2 IDE (rev a2)
00:0c.0 PCI bridge: nVidia Corporation nForce2 PCI Bridge (rev a3)
00:0d.0 FireWire (IEEE 1394): nVidia Corporation nForce2 FireWire (IEEE 1394) Controller (rev a3)
00:1e.0 PCI bridge: nVidia Corporation nForce2 AGP (rev a2)
01:0b.0 RAID bus controller: Silicon Image, Inc. SiI 3112 [SATALink/SATARaid] Serial ATA Controller (rev 02)
02:01.0 Ethernet controller: 3Com Corporation 3C920B-EMB Integrated Fast Ethernet Controller [Tornado] (rev 40)
03:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 MX 440] (rev a3)

bob@ubuntu:~$ lsusb
Bus 003 Device 005: ID 0424:2228 Standard Microsystems Corp. 9-in-2 Card Reader
Bus 003 Device 004: ID 0424:2602 Standard Microsystems Corp. 
Bus 003 Device 002: ID 0424:2512 Standard Microsystems Corp. 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 03f0:1204 Hewlett-Packard DeskJet 930c
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

bob@ubuntu:~$ cat /proc/asound/cards
 0 [nForce2        ]: NFORCE - NVidia nForce2
                      NVidia nForce2 with ALC650E at irq 16
 1 [UART           ]: MPU-401 UART - MPU-401 UART
                      MPU-401 UART at 0x330, irq 10

bob@ubuntu:~$ cat /proc/asound/modules
 0 snd_intel8x0
 1 snd_mpu401

bob@ubuntu:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: nForce2 [NVidia nForce2], device 0: Intel ICH [NVidia nForce2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: nForce2 [NVidia nForce2], device 2: Intel ICH - IEC958 [NVidia nForce2 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

bob@ubuntu:~$ arecord -l
**** List of CAPTURE Hardware Devices ****
card 0: nForce2 [NVidia nForce2], device 0: Intel ICH [NVidia nForce2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: nForce2 [NVidia nForce2], device 1: Intel ICH - MIC ADC [NVidia nForce2 - MIC ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
bob@ubuntu:~$

---

### Post by wbee on 2009-04-02
Mark,

Thanks,and again for the work involved in the guide.

I'm working on it.

---------

W

---

### Post by markbuntu on 2009-04-02
> **Baasha said:**
> Hi,
I have followed all the instructions in this post (I think) and it certainly has given me some impprovements, so thanks for that.  But I still have some weird problems.  When I play a cd with Rythmbox I get sound from FL, FR, Center, and very low volume from LFE, but no sound from RR, or RL.  I am set up for 5.1 output and all six channels show on pavmeter and all the volumes at normal levels.  But then if I run speaker-test -Dplug:surround51 -c6 -l1 -twav I get different results: 
O Front Left works
4 Center no sound
1 Front Right works
3 Rear Right sound comes from Center
2 Rear Left sound comes from Center
5 LFE no sound

Do you have any suggestions as to what I should try next?

Here is the results from various files, but I don't see anything out of the ordinary:

bob@ubuntu:~$ lspci
00:00.0 Host bridge: nVidia Corporation nForce2 IGP2 (rev a2)
00:00.1 RAM memory: nVidia Corporation nForce2 Memory Controller 1 (rev a2)
00:00.2 RAM memory: nVidia Corporation nForce2 Memory Controller 4 (rev a2)
00:00.3 RAM memory: nVidia Corporation nForce2 Memory Controller 3 (rev a2)
00:00.4 RAM memory: nVidia Corporation nForce2 Memory Controller 2 (rev a2)
00:00.5 RAM memory: nVidia Corporation nForce2 Memory Controller 5 (rev a2)
00:01.0 ISA bridge: nVidia Corporation nForce2 ISA Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation nForce2 SMBus (MCP) (rev a2)
00:02.0 USB Controller: nVidia Corporation nForce2 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation nForce2 USB Controller (rev a3)
00:02.2 USB Controller: nVidia Corporation nForce2 USB Controller (rev a3)
00:04.0 Ethernet controller: nVidia Corporation nForce2 Ethernet Controller (rev a1)
00:05.0 Multimedia audio controller: nVidia Corporation nForce Audio Processing Unit (rev a2)
00:06.0 Multimedia audio controller: nVidia Corporation nForce2 AC97 Audio Controler (MCP) (rev a1)
00:08.0 PCI bridge: nVidia Corporation nForce2 External PCI Bridge (rev a3)
00:09.0 IDE interface: nVidia Corporation nForce2 IDE (rev a2)
00:0c.0 PCI bridge: nVidia Corporation nForce2 PCI Bridge (rev a3)
00:0d.0 FireWire (IEEE 1394): nVidia Corporation nForce2 FireWire (IEEE 1394) Controller (rev a3)
00:1e.0 PCI bridge: nVidia Corporation nForce2 AGP (rev a2)
01:0b.0 RAID bus controller: Silicon Image, Inc. SiI 3112 [SATALink/SATARaid] Serial ATA Controller (rev 02)
02:01.0 Ethernet controller: 3Com Corporation 3C920B-EMB Integrated Fast Ethernet Controller [Tornado] (rev 40)
03:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 MX 440] (rev a3)

bob@ubuntu:~$ lsusb
Bus 003 Device 005: ID 0424:2228 Standard Microsystems Corp. 9-in-2 Card Reader
Bus 003 Device 004: ID 0424:2602 Standard Microsystems Corp. 
Bus 003 Device 002: ID 0424:2512 Standard Microsystems Corp. 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 03f0:1204 Hewlett-Packard DeskJet 930c
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

bob@ubuntu:~$ cat /proc/asound/cards
 0 [nForce2        ]: NFORCE - NVidia nForce2
                      NVidia nForce2 with ALC650E at irq 16
 1 [UART           ]: MPU-401 UART - MPU-401 UART
                      MPU-401 UART at 0x330, irq 10

bob@ubuntu:~$ cat /proc/asound/modules
 0 snd_intel8x0
 1 snd_mpu401

bob@ubuntu:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: nForce2 [NVidia nForce2], device 0: Intel ICH [NVidia nForce2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: nForce2 [NVidia nForce2], device 2: Intel ICH - IEC958 [NVidia nForce2 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

bob@ubuntu:~$ arecord -l
**** List of CAPTURE Hardware Devices ****
card 0: nForce2 [NVidia nForce2], device 0: Intel ICH [NVidia nForce2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: nForce2 [NVidia nForce2], device 1: Intel ICH - MIC ADC [NVidia nForce2 - MIC ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
bob@ubuntu:~$

First, check in the alsa volume control for switches for the center, rear and lfe. Many sound cards also use those connectors for mic or line in and they are switchable. Next, check the actual connections are correct.

You can also remap the outputs. There are directions for that in the surround sound section links and at 

[http://pulseaudio.org/wiki/FAQ](http://pulseaudio.org/wiki/FAQ)

---

### Post by Taus on 2009-04-02
> **markbuntu said:**
> You are lucky if the x-fi works at all. Are you sing OSS4?

no i'm not using OSS4 i tried, but couldn't get S/PDIF working with that either...

i'm currently using ALSA

---

### Post by markbuntu on 2009-04-02
> **Taus said:**
> no i'm not using OSS4 i tried, but couldn't get S/PDIF working with that either...

i'm currently using ALSA

Is there any SPDIF or IEC958 switch anywhere in one of your sound mixers?

---

### Post by Baasha on 2009-04-02
> **markbuntu said:**
> First, check in the alsa volume control for switches for the center, rear and lfe. Many sound cards also use those connectors for mic or line in and they are switchable. Next, check the actual connections are correct.

You can also remap the outputs. There are directions for that in the surround sound section links and at 

[http://pulseaudio.org/wiki/FAQ](http://pulseaudio.org/wiki/FAQ)

Hi,
I already have the switches for center, rear, and lfe turned on.  I turned off all the mic, line in, and aux in switches in case there was a conflict.  I couldn't find any instructions regarding remapping channels on the pa wiki but I assume you are referring to the etc/pulse/default.pa file.  If that is so, I have already mapped all 6 channels as per instructions in your thread.

Just once, while running speaker-test -Dplug:surround51 -c6 -l1 -twav I got an error message "-32 broken pipe" but I don't know what that means.  The 32 refers to the RL and RR channels as reported by that command.

I also have double checked all the physical wiring connections and they all all ok.

Any other suggestions?

PS: Thanks for all your help.

---

### Post by markbuntu on 2009-04-02
> **Baasha said:**
> Hi,
I already have the switches for center, rear, and lfe turned on.  I turned off all the mic, line in, and aux in switches in case there was a conflict.  I couldn't find any instructions regarding remapping channels on the pa wiki but I assume you are referring to the etc/pulse/default.pa file.  If that is so, I have already mapped all 6 channels as per instructions in your thread.

Just once, while running speaker-test -Dplug:surround51 -c6 -l1 -twav I got an error message "-32 broken pipe" but I don't know what that means.  The 32 refers to the RL and RR channels as reported by that command.

I also have double checked all the physical wiring connections and they all all ok.

Any other suggestions?

PS: Thanks for all your help.

It could be a problem with your specific hardware that is not fixed by the alsa devs. You could try updating alsa to the latest version, which always have added support for more devices That may help.

---

### Post by Taus on 2009-04-03
> **markbuntu said:**
> Is there any SPDIF or IEC958 switch anywhere in one of your sound mixers?

if you mean switch as in on/off then no.. there's a switch (checkbox) for I/O though... and there's a volume bar for master, pcm and spdif.

---

### Post by markbuntu on 2009-04-03
Did you try playing with the I/O switch or the volume bars?

---

### Post by burntresistor on 2009-04-03
I'm getting frustrated with this sound problem. I've tried a majority of the fixes. I'm a unbuntu noob. I have a Audigy 2 ZS SB0350, When I just installed it was on auto detect and it was working fine till I updated. The Sounded mixer mentioned in the Audigy section of the guide , is that the alsa mixer ? or sound  in preferences ?



2.6.27-11-generic
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 8.10
Release:	8.10
Codename:	intrepid

---

### Post by Taus on 2009-04-04
> **markbuntu said:**
> Did you try playing with the I/O switch or the volume bars?

Hi markbuntu,

first of all thanks a million for your effort! your help is very much appreciated.

Yes I did play around with the settings of my Alsa mixer. 

If i switch on the IO my receiver writes COAX pcm 96 in the display. So i guess that something is happening. I turned the SPDIF volume bar up and down, but it doesn't play any sounds. Maybe I have to change the output of my players somehow?

---

### Post by markbuntu on 2009-04-04
> **burntresistor said:**
> I'm getting frustrated with this sound problem. I've tried a majority of the fixes. I'm a unbuntu noob. I have a Audigy 2 ZS SB0350, When I just installed it was on auto detect and it was working fine till I updated. The Sounded mixer mentioned in the Audigy section of the guide , is that the alsa mixer ? or sound  in preferences ?



2.6.27-11-generic
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 8.10
Release:	8.10
Codename:	intrepid

That would be in the alsa mixer, the gnome-alsamixer is ususally the best mixer for that.

---

### Post by markbuntu on 2009-04-04
> **Taus said:**
> Hi markbuntu,

first of all thanks a million for your effort! your help is very much appreciated.

Yes I did play around with the settings of my Alsa mixer. 

If i switch on the IO my receiver writes COAX pcm 96 in the display. So i guess that something is happening. I turned the SPDIF volume bar up and down, but it doesn't play any sounds. Maybe I have to change the output of my players somehow?

Well, that is progress of some sort, you digital output seems to be working. In order to direct your applications to the digital output you need to make a sink for it in pulseaudio. There are directions for doing so here

[http://ubuntuforums.org/showthread.php?t=776958](http://ubuntuforums.org/showthread.php?t=776958)

---

### Post by Taus on 2009-04-05
> **markbuntu said:**
> Well, that is progress of some sort, you digital output seems to be working. In order to direct your applications to the digital output you need to make a sink for it in pulseaudio. There are directions for doing so here

[http://ubuntuforums.org/showthread.php?t=776958](http://ubuntuforums.org/showthread.php?t=776958)

ive been trying unsing aplay -l to find my digital output before. But i'm not sure if it's on the list aplay returns. Here is what i get when i run aplay -l

```
**** List of PLAYBACK Hardware Devices ****
card 0: XFi [Creative X-Fi], device 0: X-Fi 20k1 [WaveOut/WaveIn]
  Subdevices: 7/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7

```

Does that mean that one of the subdevices of 0,0 is the SPDIF output? is there a way to test the different subdevices?

---

### Post by markbuntu on 2009-04-05
Usually those subdevices would be more descriptive and the spdif output would be explicitly described. In this case it seems the driver writers have pushed something out a little prematurely to give functionality now rather than wait for better descriptions. At this point all you can do is try them and see which one works.

---

### Post by Taus on 2009-04-05
> **markbuntu said:**
> Usually those subdevices would be more descriptive and the spdif output would be explicitly described. In this case it seems the driver writers have pushed something out a little prematurely to give functionality now rather than wait for better descriptions. At this point all you can do is try them and see which one works.

this might be a stupid question, but how do i try them? I read the post u refered to, but they aren't using subdevices to configure the sound. From what i understand i need to make a sink for hw(0,0) but how do i tell it which subdevice to use?

---

### Post by markbuntu on 2009-04-05
the subdevices would be hw(0,1), hw(0,2) etc.

---

### Post by libihero on 2009-04-09
I can't get my mic to work on my laptop at all after installing ubuntu.  my sound works perfectly, and i unmuted the mics in the sound manager, but the mic still wont work.

---

### Post by markbuntu on 2009-04-10
> **libihero said:**
> I can't get my mic to work on my laptop at all after installing ubuntu.  my sound works perfectly, and i unmuted the mics in the sound manager, but the mic still wont work.

What model laptop do you have?

---

### Post by libihero on 2009-04-10
it's a gateway m series

---

### Post by markbuntu on 2009-04-11
Check the capture switches, open the volume control on the panel. You may need to select them in Edit/preferences to make them visible. Or you can chekc the record switches in the gnome-alsamixer which do the same thing.  

If that does not work....
It is a common problem since the OEMs have tweaked the firmware so much it is difficult for the driver to figure everything out, especially microphones. But we can tell it what to do with options.

Did you look in this link here, some of the gateway m series are listed and there are directions for adding the options. Also check the links as they have more listings.

[http://ubuntuforums.org/showthread.php?t=1043568](http://ubuntuforums.org/showthread.php?t=1043568)

If none of that works you may try upgrading your alsa version. Later versions have improved hardware support for a lot more machines.

---

### Post by neu2buntu on 2009-04-15
**System/Preferences/Multimedia Systems Selector/Audio set Plugin to Pulse Audio.   **noticed this part in your multiple sound solution guide under **default soundcard **title. that "multimedia systems selector" is not in system/preferences in 8.04 and 8.10 (2 i have tried) and has to either be enabled by right clicking the main menu and choosing >edit menu ,or by using the "```
gstreamer-properties
```" command in the terminal. thought this may be usefull to add to your guide Markbuntu!!!!     oooops just realised "PMs will be ignored."  silly me :lolflag:

---

### Post by markbuntu on 2009-04-30
Actually, in the guide somehwere it says that you may have to enable some menu items with System/Preferences/Menu to see them. Mybe I should make it more prominenet or move it. I will have a look.

---

### Post by wb0gaz on 2009-05-03
I have not yet been able to use audio in Ubuntu 9.04 server; several command line scripts working under Alsa in Ubuntu 7.10 are now broken (no sound.)

I have installed pulse audio in the command line using:

sudo apt-get install libasound2-plugins "pulseaudio-*" paman padevchooser paprefs pavucontrol pavumeter

There are two problems with this:

1. My server may not have a GUI at all (I had to install Xorg and stuff to run paman, but I don't want this in my server configurations as it is a "headless" server

2. There is no test utility in the pulse audio tools above to send/receive a sample sound

I am stuck and would appreciate assistance,

---

### Post by markbuntu on 2009-05-03
> **wb0gaz said:**
> I have not yet been able to use audio in Ubuntu 9.04 server; several command line scripts working under Alsa in Ubuntu 7.10 are now broken (no sound.)

I have installed pulse audio in the command line using:

sudo apt-get install libasound2-plugins "pulseaudio-*" paman padevchooser paprefs pavucontrol pavumeter

There are two problems with this:

1. My server may not have a GUI at all (I had to install Xorg and stuff to run paman, but I don't want this in my server configurations as it is a "headless" server

2. There is no test utility in the pulse audio tools above to send/receive a sample sound

I am stuck and would appreciate assistance,

Well, it should be pretty apparent that the guide was not written for healdess servers since so much of the configuration is done through guis. 9.04 is very different from 7.10 since much of the alsa sound server funtions have been replaced with pulseaudio.

That said, you can set up pulse audio for headless system operation fairly easily through editing the etc/pulse/default.pa and daemon.conf files. There are a couple of links from the OP for setting up a headless server and starting pulse as a systemwide daemon. You would get better help addressing your questions in those threads.

---

### Post by wb0gaz on 2009-05-04
Thanks, Mark.

It appears pulse audio is a show-stopper for me, as it's CPU overhead is waaaay excessive (500 MHz machine, getting only about 50% of audio when running out-of-the-box configuration with pulse audio.) Therefore, the GUI situation is secondary.

Is it possible to avoid pulse audio entirely and get alsa working directly (that is, with, for example, aplay actually delivering audio to the speakers?)

Unfortunately, as much as I'd like to revert back to Ubuntu 7.10, the on-line repositories from which applications are installed appear defunct, so I'm stuck in a no-win situation now with this forced upgrade to 9.04 (8.04 didn't work as it would not tolerate my absence of a DMA controller in this server)

Dave

---

### Post by neu2buntu on 2009-05-16
am having some minor problems with jack/pulseaudio... i am running on the latest versions of alsa and pulse (from this post) the problem was that the pulseaudio jack sink/source died everytime i changed between audio of any kind eg playing last fm changing to say youtube.infact switching or moving from any audio source at all would kill my jack sink and source inside qjackctl (using the pactl script in qjackctl). 
 i edited my /etc/pulse/default.pa to look like this (notice my added jack sink and source modules)which brings the sink and source back again every failure(which is everytime i change audio)  
#!/usr/bin/pulseaudio -nF
#
# This file is part of PulseAudio.
#
# PulseAudio is free software; you can redistribute it and/or modify it
# under the terms of the GNU Lesser General Public License as published by
# the Free Software Foundation; either version 2 of the License, or
# (at your option) any later version.
#
# PulseAudio is distributed in the hope that it will be useful, but
# WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU
# General Public License for more details.
#
# You should have received a copy of the GNU Lesser General Public License
# along with PulseAudio; if not, write to the Free Software Foundation,
# Inc., 59 Temple Place, Suite 330, Boston, MA 02111-1307 USA.

# This startup script is used only if PulseAudio is started per-user
# (i.e. not in system mode)

.nofail

### Load something into the sample cache
#load-sample-lazy x11-bell /usr/share/sounds/gtk-events/activate.wav
#load-sample-lazy pulse-hotplug /usr/share/sounds/startup3.wav
#load-sample-lazy pulse-coldplug /usr/share/sounds/startup3.wav
#load-sample-lazy pulse-access /usr/share/sounds/generic.wav
load-sample-dir-lazy /usr/share/sounds/ubuntu/stereo

.fail

### Automatically suspend sinks/sources that become idle for too long
#load-module module-suspend-on-idle

### Automatically restore the volume of streams and devices
#load-module module-device-restore
#load-module module-stream-restore
#load-module module-card-restore

### Automatically augment property information from .desktop files
### stored in /usr/share/application
load-module module-augment-properties

### Load audio drivers statically (it's probably better to not load
### these drivers manually, but instead use module-hal-detect --
### see below -- for doing this automatically)
#load-module module-alsa-sink
#load-module module-alsa-source device=hw:1,0
#load-module module-oss device="/dev/dsp" sink_name=output source_name=input
#load-module module-oss-mmap device="/dev/dsp" sink_name=output source_name=input
#load-module module-null-sink
#load-module module-pipe-sink

### Automatically load driver modules depending on the hardware available
.ifexists module-hal-detect.so
load-module module-hal-detect tsched=0
.else
### Alternatively use the static hardware detection module (for systems that
### lack HAL support)
load-module module-detect
.endif

### Automatically load driver modules for Bluetooth hardware
.ifexists module-bluetooth-discover.so
load-module module-bluetooth-discover
.endif

### Load several protocols
.ifexists module-esound-protocol-unix.so
load-module module-esound-protocol-unix
.endif
load-module module-native-protocol-unix

### Network access (may be configured with paprefs, so leave this commented
### here if you plan to use paprefs)
#load-module module-esound-protocol-tcp
#load-module module-native-protocol-tcp
#load-module module-zeroconf-publish

### Load the RTP reciever module (also configured via paprefs, see above)
#load-module module-rtp-recv

### Load the RTP sender module (also configured via paprefs, see above)
#load-module module-null-sink sink_name=rtp format=s16be channels=2 rate=44100 description="RTP Multicast Sink"
#load-module module-rtp-send source=rtp.monitor

### Load additional modules from GConf settings. This can be configured with the paprefs tool.
### Please keep in mind that the modules configured by paprefs might conflict with manually
### loaded modules.
.ifexists module-gconf.so
.nofail
load-module module-gconf
.fail
.endif

### Automatically restore the default sink/source when changed by the user during runtime
#load-module module-default-device-restore

### Automatically move streams to the default sink if the sink they are
### connected to dies, similar for sources
load-module module-rescue-streams

### Make sure we always have a sink around, even if it is a null sink.
#load-module module-always-sink


### Load pulse jack mods
load-module module-jack-sink
load-module module-jack-source


### If autoexit on idle is enabled we want to make sure we only quit
### when no local session needs us anymore.
load-module module-console-kit

### Enable positioned event sounds
load-module module-position-event-sounds

### Cork music streams when a phone stream is active
load-module module-cork-music-on-phone

# X11 modules should not be started from default.pa so that one daemon
# can be shared by multiple sessions.

### Load X11 bell module
#load-module module-x11-bell sample=bell-windowing-system

### Register ourselves in the X11 session manager
#load-module module-x11-xsmp

### Publish connection data in the X11 root window
#.ifexists module-x11-publish.so
#.nofail
#load-module module-x11-publish
#.fail
#.endif

### Make some devices default
set-default-sink jack_out
set-default-source jack_in

up until 9.04 jack and pulse worked perfect for me , it seems as though the pulse modules timeout as i can change fast between e.g 2 totem-audio-previews of .ogg /.wav/mp3 and it wont die, but if dont use any sound for a few seconds the modules die.


this is not a total disaster as i can do all that i want with my audio,but it is definately a bug of some kind,and as i am using non repo version of pulseaudio i cant really report (apport) it.

here is an eg of my verbose output from qjackctl on failure....this is long so i will wrap it in code tags
 p, li { white-space: pre-wrap; }  ```

we have problem clients (problems = 1
 ++ Removing failed clients ...
 client alsa_pcm error status 0
 client PulseAudio JACK Sink error status 10000001
 removing failed client PulseAudio JACK Sink state = Running errors = 10000001
 removing client "PulseAudio JACK Sink"
 removing client "PulseAudio JACK Sink" from the processing chain
 DIS-connect PulseAudio JACK Sink:front-right and system:playback_2
 ++ jack_sort_graph
 ++ jack_rechain_graph():
 +++ client is now alsa_pcm active ? 1
 client alsa_pcm: internal client, execution_order=0.
 +++ client is now PulseAudio JACK Source active ? 1
 client PulseAudio JACK Source: start_fd=7, execution_order=0.
 +++ client is now qjackctl active ? 1
 client qjackctl: in subgraph after PulseAudio JACK Source, execution_order=1.
 client event poll on 24 for qjackctl starts at 2652181197
 back from client event poll after 50 usecs
 +++ client is now PulseAudio JACK Sink active ? 1
 client PulseAudio JACK Sink: in subgraph after PulseAudio JACK Source, execution_order=2.
 client PulseAudio JACK Source: wait_fd=28, execution_order=3 (last client).
 -- jack_rechain_graph()
 -- jack_sort_graph
 client event poll on 24 for qjackctl starts at 2652181646
 back from client event poll after 39 usecs
 DIS-connect PulseAudio JACK Sink:front-left and system:playback_1
 ++ jack_sort_graph
 ++ jack_rechain_graph():
 +++ client is now alsa_pcm active ? 1
 client alsa_pcm: internal client, execution_order=0.
 +++ client is now PulseAudio JACK Sink active ? 1
 client PulseAudio JACK Sink: start_fd=7, execution_order=0.
 +++ client is now qjackctl active ? 1
 client qjackctl: in subgraph after PulseAudio JACK Sink, execution_order=1.
 client event poll on 24 for qjackctl starts at 2652182593
 back from client event poll after 57 usecs
 +++ client is now PulseAudio JACK Source active ? 1
 client PulseAudio JACK Source: in subgraph after PulseAudio JACK Sink, execution_order=2.
 client PulseAudio JACK Sink: wait_fd=28, execution_order=3 (last client).
 -- jack_rechain_graph()
 -- jack_sort_graph
 11:29:52.671 JACK active patchbay scan...
 11:29:52.679 JACK connection change.
 client event poll on 24 for qjackctl starts at 2652183147
 back from client event poll after 46 usecs
 +++ deactivate PulseAudio JACK Sink
 client qjackctl error status 0
 client PulseAudio JACK Source error status 1
 client failure: client PulseAudio JACK Source state = Not triggered errors = 1
 removing client "PulseAudio JACK Source" from the processing chain
 DIS-connect system:capture_2 and PulseAudio JACK Source:front-right
 ++ jack_sort_graph
 ++ jack_rechain_graph():
 +++ client is now alsa_pcm active ? 1
 client alsa_pcm: internal client, execution_order=0.
 +++ client is now PulseAudio JACK Source active ? 1
 client PulseAudio JACK Source: start_fd=7, execution_order=0.
 +++ client is now qjackctl active ? 1
 client qjackctl: in subgraph after PulseAudio JACK Source, execution_order=1.
 client event poll on 24 for qjackctl starts at 2652184382
 back from client event poll after 52 usecs
 client PulseAudio JACK Source: wait_fd=25, execution_order=2 (last client).
 -- jack_rechain_graph()
 -- jack_sort_graph
 client event poll on 24 for qjackctl starts at 2652184816
 back from client event poll after 42 usecs
 DIS-connect system:capture_1 and PulseAudio JACK Source:front-left
 ++ jack_sort_graph
 ++ jack_rechain_graph():
 +++ client is now alsa_pcm active ? 1
 client alsa_pcm: internal client, execution_order=0.
 +++ client is now qjackctl active ? 1
 client qjackctl: start_fd=7, execution_order=0.
 client event poll on 24 for qjackctl starts at 2652185630
 back from client event poll after 53 usecs
 +++ client is now PulseAudio JACK Source active ? 1
 client PulseAudio JACK Source: in subgraph after qjackctl, execution_order=1.
 client qjackctl: wait_fd=25, execution_order=2 (last client).
 -- jack_rechain_graph()
 -- jack_sort_graph
 client event poll on 24 for qjackctl starts at 2652186167
 back from client event poll after 50 usecs
 +++ deactivate PulseAudio JACK Source
 ++ jack_sort_graph
 ++ jack_rechain_graph():
 +++ client is now alsa_pcm active ? 1
 client alsa_pcm: internal client, execution_order=0.
 +++ client is now qjackctl active ? 1
 11:29:52.860 JACK connection graph change.
 client qjackctl: start_fd=7, execution_order=0.
 client event poll on 24 for qjackctl starts at 2652187083
 back from client event poll after 47 usecs
 client qjackctl: wait_fd=17, execution_order=1 (last client).
 -- jack_rechain_graph()
 -- jack_sort_graph
 -- Removing failed clients ...
 after removing clients, problems = 2
 trying to lock graph to remove 2 problems
 we have problem clients (problems = 2
 ++ Removing failed clients ...
 client alsa_pcm error status 0
 client PulseAudio JACK Source error status 0
 client qjackctl error status 0
 -- Removing failed clients ...
 after removing clients, problems = 0
 start poll on 4 fd's
 server thread back from poll
 new client: PulseAudio JACK Sink, id = 8 type 2 @ 0xb55e8000 fd = 26
 start poll on 5 fd's
 server thread back from poll
 new client PulseAudio JACK Sink using 27 for events
 start poll on 5 fd's
 server thread back from poll
 client event poll on 24 for qjackctl starts at 2652190859
 back from client event poll after 50 usecs
 registered port PulseAudio JACK Sink:front-left, offset = 12288
 start poll on 5 fd's
 server thread back from poll
 client event poll on 24 for qjackctl starts at 2652191629
 back from client event poll after 49 usecs
 registered port PulseAudio JACK Sink:front-right, offset = 16384
 start poll on 5 fd's
 client event poll on 24 for qjackctl starts at 2652204371
 back from client event poll after 70 usecs
 server thread back from poll
 start poll on 5 fd's
 server thread back from poll
 start poll on 5 fd's
 server thread back from poll
 start poll on 5 fd's
 server thread back from poll
 start poll on 5 fd's
 server thread back from poll
 ++ jack_sort_graph
 ++ jack_rechain_graph():
 +++ client is now alsa_pcm active ? 1
 client alsa_pcm: internal client, execution_order=0.
 +++ client is now qjackctl active ? 1
 client qjackctl: start_fd=7, execution_order=0.
 client event poll on 24 for qjackctl starts at 2652520666
 back from client event poll after 21 usecs
 +++ client is now PulseAudio JACK Sink active ? 1
 client PulseAudio JACK Sink: in subgraph after qjackctl, execution_order=1.
 11:29:52.988 JACK active patchbay scan...
 11:29:52.997 JACK connection change.
 client event poll on 27 for PulseAudio JACK Sink starts at 2652520775
 back from client event poll after 106 usecs
 client qjackctl: wait_fd=25, execution_order=2 (last client).
 -- jack_rechain_graph()
 -- jack_sort_graph
 start poll on 5 fd's
 server thread back from poll
 connect PulseAudio JACK Sink:front-left and system:playback_1 (output)
 client event poll on 27 for PulseAudio JACK Sink starts at 2652521165
 back from client event poll after 26 usecs
 ++ jack_sort_graph
 ++ jack_rechain_graph():
 +++ client is now alsa_pcm active ? 1
 client alsa_pcm: internal client, execution_order=0.
 +++ client is now PulseAudio JACK Sink active ? 1
 client PulseAudio JACK Sink: start_fd=7, execution_order=0.
 client event poll on 27 for PulseAudio JACK Sink starts at 2652521598
 back from client event poll after 32 usecs
 +++ client is now qjackctl active ? 1
 client qjackctl: in subgraph after PulseAudio JACK Sink, execution_order=1.
 client event poll on 24 for qjackctl starts at 2652521713
 back from client event poll after 103 usecs
 client PulseAudio JACK Sink: wait_fd=25, execution_order=2 (last client).
 -- jack_rechain_graph()
 -- jack_sort_graph
 start poll on 5 fd's
 server thread back from poll
 connect PulseAudio JACK Sink:front-right and system:playback_2 (output)
 client event poll on 27 for PulseAudio JACK Sink starts at 2652522198
 back from client event poll after 27 usecs
 ++ jack_sort_graph
 ++ jack_rechain_graph():
 +++ client is now alsa_pcm active ? 1
 client alsa_pcm: internal client, execution_order=0.
 +++ client is now qjackctl active ? 1
 client qjackctl: start_fd=7, execution_order=0.
 client event poll on 24 for qjackctl starts at 2652522547
 back from client event poll after 860 usecs
 +++ client is now PulseAudio JACK Sink active ? 1
 client PulseAudio JACK Sink: in subgraph after qjackctl, execution_order=1.
 client event poll on 27 for PulseAudio JACK Sink starts at 2652523519
 back from client event poll after 107 usecs
 client qjackctl: wait_fd=25, execution_order=2 (last client).
 -- jack_rechain_graph()
 -- jack_sort_graph
 start poll on 5 fd's
 server thread back from poll
 new client: PulseAudio JACK Source-01, id = 9 type 2 @ 0xb7b4a000 fd = 32
 start poll on 6 fd's
 server thread back from poll
 new client PulseAudio JACK Source-01 using 33 for events
 start poll on 6 fd's
 server thread back from poll
 client event poll on 24 for qjackctl starts at 2652544905
 back from client event poll after 90 usecs
 registered port PulseAudio JACK Source-01:front-left, offset = 0
 start poll on 6 fd's
 server thread back from poll
 client event poll on 24 for qjackctl starts at 2652545397
 back from client event poll after 73 usecs
 registered port PulseAudio JACK Source-01:front-right, offset = 0
 start poll on 6 fd's
 server thread back from poll
 ++ jack_sort_graph
 ++ jack_rechain_graph():
 +++ client is now alsa_pcm active ? 1
 client alsa_pcm: internal client, execution_order=0.
 +++ client is now PulseAudio JACK Sink active ? 1
 client PulseAudio JACK Sink: start_fd=7, execution_order=0.
 client event poll on 27 for PulseAudio JACK Sink starts at 2652565971
 back from client event poll after 133 usecs
 +++ client is now qjackctl active ? 1
 client qjackctl: in subgraph after PulseAudio JACK Sink, execution_order=1.
 client event poll on 24 for qjackctl starts at 2652566223
 back from client event poll after 148 usecs
 +++ client is now PulseAudio JACK Source-01 active ? 1
 client event poll on 33 for PulseAudio JACK Source-01 starts at 2652566548
 back from client event poll after 30 usecs
 client PulseAudio JACK Sink: wait_fd=28, execution_order=3 (last client).
 -- jack_rechain_graph()
 -- jack_sort_graph
 start poll on 6 fd's
 server thread back from poll
 connect system:capture_1 and PulseAudio JACK Source-01:front-left (forward)
 client event poll on 33 for PulseAudio JACK Source-01 starts at 2652566868
 back from client event poll after 27 usecs
 ++ jack_sort_graph
 ++ jack_rechain_graph():
 +++ client is now alsa_pcm active ? 1
 client alsa_pcm: internal client, execution_order=0.
 +++ client is now PulseAudio JACK Source-01 active ? 1
 client PulseAudio JACK Source-01: start_fd=7, execution_order=0.
 client event poll on 33 for PulseAudio JACK Source-01 starts at 2652567342
 back from client event poll after 33 usecs
 +++ client is now qjackctl active ? 1
 client qjackctl: in subgraph after PulseAudio JACK Source-01, execution_order=1.
 client event poll on 24 for qjackctl starts at 2652567571
 back from client event poll after 29 usecs
 +++ client is now PulseAudio JACK Sink active ? 1
 client event poll on 27 for PulseAudio JACK Sink starts at 2652567682
 back from client event poll after 98 usecs
 client PulseAudio JACK Source-01: wait_fd=28, execution_order=3 (last client).
 -- jack_rechain_graph()
 -- jack_sort_graph
 start poll on 6 fd's
 server thread back from poll
 connect system:capture_2 and PulseAudio JACK Source-01:front-right (forward)
 client event poll on 33 for PulseAudio JACK Source-01 starts at 2652568195
 back from client event poll after 32 usecs
 ++ jack_sort_graph
 ++ jack_rechain_graph():
 +++ client is now alsa_pcm active ? 1
 client alsa_pcm: internal client, execution_order=0.
 11:29:53.251 JACK active patchbay scan...
 +++ client is now PulseAudio JACK Sink active ? 1
 client PulseAudio JACK Sink: start_fd=7, execution_order=0.
 client event poll on 27 for PulseAudio JACK Sink starts at 2652568654
 back from client event poll after 126 usecs
 +++ client is now qjackctl active ? 1
 client qjackctl: in subgraph after PulseAudio JACK Sink, execution_order=1.
 client event poll on 24 for qjackctl starts at 2652568884
 back from client event poll after 166 usecs
 +++ client is now PulseAudio JACK Source-01 active ? 1
 client PulseAudio JACK Source-01: in subgraph after PulseAudio JACK Sink, execution_order=2.
 client event poll on 33 for PulseAudio JACK Source-01 starts at 2652569248
 back from client event poll after 29 usecs
 client PulseAudio JACK Sink: wait_fd=28, execution_order=3 (last client).
 -- jack_rechain_graph()
 -- jack_sort_graph
 start poll on 6 fd's
 server thread back from poll
 start poll on 6 fd's
 server thread back from poll
 start poll on 6 fd's
 server thread back from poll
 start poll on 6 fd's
 server thread back from poll
 start poll on 6 fd's
 server thread back from poll
 start poll on 6 fd's
 server thread back from poll
 start poll on 6 fd's
 server thread back from poll
 start poll on 6 fd's
 server thread back from poll
 start poll on 6 fd's
 **** alsa_pcm: xrun of at least 146.952 msecs
 11:29:53.715 XRUN callback (5).
 client event poll on 27 for PulseAudio JACK Sink starts at 2653381260
 back from client event poll after 57 usecs
 client event poll on 24 for qjackctl starts at 2653381370
 back from client event poll after 82 usecs
 client event poll on 33 for PulseAudio JACK Source-01 starts at 2653381484
 back from client event poll after 42 usecs
 11:29:54.057 XRUN callback (1 skipped).
 load = 58.0180 max usecs: 192610.000, spare = 0.000
 load = 33.2749 max usecs: 1981.000, spare = 21238.000
 load = 21.4891 max usecs: 2253.000, spare = 20966.000
 load = 15.2495 max usecs: 2092.000, spare = 21127.000
 load = 12.7800 max usecs: 2394.000, spare = 20825.000
 server thread back from poll
 marking client PulseAudio JACK Sink with SOCKET error state = Triggered errors = 0
 trying to lock graph to remove 1 problems
 subgraph starting at PulseAudio JACK Sink timed out (subgraph_wait_fd=28, status = 0, state = Triggered, pollret = 0 revents = 0x0)
 at 2663421545 waiting on 28 for 5001147 usecs, status = 1 sig = 2658420382 awa = 0 fin = 0 dur=0
 checking client alsa_pcm: awake at 0 finished at 0
 checking client PulseAudio JACK Source: awake at 0 finished at 0
 checking client qjackctl: awake at 0 finished at 0
 checking client PulseAudio JACK Source-01: awake at 0 finished at 0
 waking server thread
 client PulseAudio JACK Sink has died/exited
 client PulseAudio JACK Source has died/exited
 client PulseAudio JACK Source-01 has died/exited
 waking server thread
 **** alsa_pcm: xrun of at least 4956.067 msecs
 11:30:03.794 JACK connection graph change.
 11:30:03.801 XRUN callback (6).
 we have problem clients (problems = 1
 ++ Removing failed clients ...
 client alsa_pcm error status 0
 client PulseAudio JACK Sink error status 10000001
 removing failed client PulseAudio JACK Sink state = Triggered errors = 10000001
 removing client "PulseAudio JACK Sink"
 removing client "PulseAudio JACK Sink" from the processing chain
 DIS-connect PulseAudio JACK Sink:front-right and system:playback_2
 ++ jack_sort_graph
 ++ jack_rechain_graph():
 +++ client is now alsa_pcm active ? 1
 client alsa_pcm: internal client, execution_order=0.
 +++ client is now PulseAudio JACK Source-01 active ? 1
 client PulseAudio JACK Source-01: start_fd=7, execution_order=0.
 +++ client is now qjackctl active ? 1
 client qjackctl: in subgraph after PulseAudio JACK Source-01, execution_order=1.
 client event poll on 24 for qjackctl starts at 2663422383
 back from client event poll after 208 usecs
 +++ client is now PulseAudio JACK Sink active ? 1
 client PulseAudio JACK Sink: in subgraph after PulseAudio JACK Source-01, execution_order=2.
 client PulseAudio JACK Source-01: wait_fd=28, execution_order=3 (last client).
 -- jack_rechain_graph()
 -- jack_sort_graph
 client event poll on 24 for qjackctl starts at 2663422842
 back from client event poll after 43 usecs
 DIS-connect PulseAudio JACK Sink:front-left and system:playback_1
 ++ jack_sort_graph
 ++ jack_rechain_graph():
 +++ client is now alsa_pcm active ? 1
 client alsa_pcm: internal client, execution_order=0.
 +++ client is now PulseAudio JACK Sink active ? 1
 client PulseAudio JACK Sink: start_fd=7, execution_order=0.
 +++ client is now qjackctl active ? 1
 client qjackctl: in subgraph after PulseAudio JACK Sink, execution_order=1.
 client event poll on 24 for qjackctl starts at 2663423552
 back from client event poll after 36 usecs
 +++ client is now PulseAudio JACK Source-01 active ? 1
 client PulseAudio JACK Source-01: in subgraph after PulseAudio JACK Sink, execution_order=2.
 client PulseAudio JACK Sink: wait_fd=28, execution_order=3 (last client).
 -- jack_rechain_graph()
 -- jack_sort_graph
 client event poll on 24 for qjackctl starts at 2663423847
 back from client event poll after 33 usecs
 +++ deactivate PulseAudio JACK Sink
 client PulseAudio JACK Source error status 1
 client failure: client PulseAudio JACK Source state = Not triggered errors = 1
 removing client "PulseAudio JACK Source" from the processing chain
 +++ deactivate PulseAudio JACK Source
 client qjackctl error status 0
 client PulseAudio JACK Source-01 error status 1
 client failure: client PulseAudio JACK Source-01 state = Not triggered errors = 1
 removing client "PulseAudio JACK Source-01" from the processing chain
 DIS-connect system:capture_2 and PulseAudio JACK Source-01:front-right
 ++ jack_sort_graph
 ++ jack_rechain_graph():
 +++ client is now alsa_pcm active ? 1
 client alsa_pcm: internal client, execution_order=0.
 +++ client is now PulseAudio JACK Source-01 active ? 1
 client PulseAudio JACK Source-01: start_fd=7, execution_order=0.
 +++ client is now qjackctl active ? 1
 11:30:04.011 JACK active patchbay scan...
 11:30:04.020 JACK connection change.
 client qjackctl: in subgraph after PulseAudio JACK Source-01, execution_order=1.
 client event poll on 24 for qjackctl starts at 2663424797
 back from client event poll after 39 usecs
 client PulseAudio JACK Source-01: wait_fd=25, execution_order=2 (last client).
 -- jack_rechain_graph()
 -- jack_sort_graph
 client event poll on 24 for qjackctl starts at 2663425039
 back from client event poll after 31 usecs
 DIS-connect system:capture_1 and PulseAudio JACK Source-01:front-left
 ++ jack_sort_graph
 ++ jack_rechain_graph():
 +++ client is now alsa_pcm active ? 1
 client alsa_pcm: internal client, execution_order=0.
 +++ client is now qjackctl active ? 1
 client qjackctl: start_fd=7, execution_order=0.
 client event poll on 24 for qjackctl starts at 2663425567
 back from client event poll after 36 usecs
 +++ client is now PulseAudio JACK Source-01 active ? 1
 client PulseAudio JACK Source-01: in subgraph after qjackctl, execution_order=1.
 client qjackctl: wait_fd=25, execution_order=2 (last client).
 -- jack_rechain_graph()
 -- jack_sort_graph
 client event poll on 24 for qjackctl starts at 2663425844
 back from client event poll after 30 usecs
 +++ deactivate PulseAudio JACK Source-01
 ++ jack_sort_graph
 ++ jack_rechain_graph():
 +++ client is now alsa_pcm active ? 1
 client alsa_pcm: internal client, execution_order=0.
 +++ client is now qjackctl active ? 1
 client qjackctl: start_fd=7, execution_order=0.
 client event poll on 24 for qjackctl starts at 2663426345
 back from client event poll after 30 usecs
 client qjackctl: wait_fd=17, execution_order=1 (last client).
 -- jack_rechain_graph()
 -- jack_sort_graph
 -- Removing failed clients ...
 after removing clients, problems = 2
 trying to lock graph to remove 2 problems
 we have problem clients (problems = 2
 ++ Removing failed clients ...
 client alsa_pcm error status 0
 client PulseAudio JACK Source-01 error status 0
 client qjackctl error status 0
 client PulseAudio JACK Source error status 0
 -- Removing failed clients ...
 after removing clients, problems = 0
 start poll on 4 fd's
 server thread back from poll
 11:30:04.164 JACK connection graph change.
 new client: PulseAudio JACK Sink, id = 10 type 2 @ 0xb7b49000 fd = 26
 start poll on 5 fd's
 server thread back from poll
 new client PulseAudio JACK Sink using 27 for events
 start poll on 5 fd's
 server thread back from poll
 client event poll on 24 for qjackctl starts at 2663429568
 back from client event poll after 42 usecs
 registered port PulseAudio JACK Sink:front-left, offset = 12288
 start poll on 5 fd's
 server thread back from poll
 client event poll on 24 for qjackctl starts at 2663430154
 back from client event poll after 37 usecs
 registered port PulseAudio JACK Sink:front-right, offset = 16384
 start poll on 5 fd's
 client event poll on 24 for qjackctl starts at 2663452364
 back from client event poll after 98 usecs
 server thread back from poll
 start poll on 5 fd's
 server thread back from poll
 start poll on 5 fd's
 server thread back from poll
 start poll on 5 fd's
 server thread back from poll
 start poll on 5 fd's
 server thread back from poll
 ++ jack_sort_graph
 ++ jack_rechain_graph():
 +++ client is now alsa_pcm active ? 1
 client alsa_pcm: internal client, execution_order=0.
 +++ client is now qjackctl active ? 1
 client qjackctl: start_fd=7, execution_order=0.
 client event poll on 24 for qjackctl starts at 2663789585
 back from client event poll after 144 usecs
 +++ client is now PulseAudio JACK Sink active ? 1
 client PulseAudio JACK Sink: in subgraph after qjackctl, execution_order=1.
 client event poll on 27 for PulseAudio JACK Sink starts at 2663789939
 back from client event poll after 31 usecs
 client qjackctl: wait_fd=25, execution_order=2 (last client).
 -- jack_rechain_graph()
 -- jack_sort_graph
 start poll on 5 fd's
 server thread back from poll
 connect PulseAudio JACK Sink:front-left and system:playback_1 (output)
 client event poll on 27 for PulseAudio JACK Sink starts at 2663790409
 back from client event poll after 26 usecs
 ++ jack_sort_graph
 ++ jack_rechain_graph():
 +++ client is now alsa_pcm active ? 1
 client alsa_pcm: internal client, execution_order=0.
 +++ client is now PulseAudio JACK Sink active ? 1
 client PulseAudio JACK Sink: start_fd=7, execution_order=0.
 11:30:04.291 JACK active patchbay scan...
 11:30:04.298 JACK connection change.
 client event poll on 27 for PulseAudio JACK Sink starts at 2663790968
 back from client event poll after 32 usecs
 +++ client is now qjackctl active ? 1
 client qjackctl: in subgraph after PulseAudio JACK Sink, execution_order=1.
 client event poll on 24 for qjackctl starts at 2663791113
 back from client event poll after 130 usecs
 client PulseAudio JACK Sink: wait_fd=25, execution_order=2 (last client).
 -- jack_rechain_graph()
 -- jack_sort_graph
 start poll on 5 fd's
 server thread back from poll
 connect PulseAudio JACK Sink:front-right and system:playback_2 (output)
 client event poll on 27 for PulseAudio JACK Sink starts at 2663791500
 back from client event poll after 47 usecs
 ++ jack_sort_graph
 ++ jack_rechain_graph():
 +++ client is now alsa_pcm active ? 1
 client alsa_pcm: internal client, execution_order=0.
 +++ client is now qjackctl active ? 1
 client qjackctl: start_fd=7, execution_order=0.
 client event poll on 24 for qjackctl starts at 2663791867
 back from client event poll after 123 usecs
 +++ client is now PulseAudio JACK Sink active ? 1
 client PulseAudio JACK Sink: in subgraph after qjackctl, execution_order=1.
 client event poll on 27 for PulseAudio JACK Sink starts at 2663792264
 back from client event poll after 26 usecs
 client qjackctl: wait_fd=25, execution_order=2 (last client).
 -- jack_rechain_graph()
 -- jack_sort_graph
 start poll on 5 fd's
 server thread back from poll
 new client: PulseAudio JACK Source-02, id = 11 type 2 @ 0xb7b48000 fd = 34
 start poll on 6 fd's
 server thread back from poll
 new client PulseAudio JACK Source-02 using 35 for events
 start poll on 6 fd's
 server thread back from poll
 client event poll on 24 for qjackctl starts at 2663821550
 back from client event poll after 86 usecs
 registered port PulseAudio JACK Source-02:front-left, offset = 0
 start poll on 6 fd's
 server thread back from poll
 client event poll on 24 for qjackctl starts at 2663821974
 back from client event poll after 22 usecs
 registered port PulseAudio JACK Source-02:front-right, offset = 0
 start poll on 6 fd's
 server thread back from poll
 ++ jack_sort_graph
 ++ jack_rechain_graph():
 +++ client is now alsa_pcm active ? 1
 client alsa_pcm: internal client, execution_order=0.
 +++ client is now PulseAudio JACK Sink active ? 1
 client PulseAudio JACK Sink: start_fd=7, execution_order=0.
 client event poll on 27 for PulseAudio JACK Sink starts at 2663841531
 back from client event poll after 147 usecs
 +++ client is now qjackctl active ? 1
 client qjackctl: in subgraph after PulseAudio JACK Sink, execution_order=1.
 client event poll on 24 for qjackctl starts at 2663841913
 back from client event poll after 25 usecs
 +++ client is now PulseAudio JACK Source-02 active ? 1
 client PulseAudio JACK Source-02: in subgraph after PulseAudio JACK Sink, execution_order=2.
 client event poll on 35 for PulseAudio JACK Source-02 starts at 2663842180
 back from client event poll after 26 usecs
 client PulseAudio JACK Sink: wait_fd=28, execution_order=3 (last client).
 -- jack_rechain_graph()
 -- jack_sort_graph
 start poll on 6 fd's
 server thread back from poll
 connect system:capture_1 and PulseAudio JACK Source-02:front-left (forward)
 client event poll on 35 for PulseAudio JACK Source-02 starts at 2663842655
 back from client event poll after 31 usecs
 ++ jack_sort_graph
 ++ jack_rechain_graph():
 +++ client is now alsa_pcm active ? 1
 client alsa_pcm: internal client, execution_order=0.
 +++ client is now PulseAudio JACK Source-02 active ? 1
 client PulseAudio JACK Source-02: start_fd=7, execution_order=0.
 client event poll on 35 for PulseAudio JACK Source-02 starts at 2663843316
 back from client event poll after 32 usecs
 +++ client is now qjackctl active ? 1
 client qjackctl: in subgraph after PulseAudio JACK Source-02, execution_order=1.
 client event poll on 24 for qjackctl starts at 2663843639
 back from client event poll after 27 usecs
 +++ client is now PulseAudio JACK Sink active ? 1
 client PulseAudio JACK Sink: in subgraph after PulseAudio JACK Source-02, execution_order=2.
 client event poll on 27 for PulseAudio JACK Sink starts at 2663843785
 back from client event poll after 106 usecs
 client PulseAudio JACK Source-02: wait_fd=28, execution_order=3 (last client).
 -- jack_rechain_graph()
 -- jack_sort_graph
 start poll on 6 fd's
 server thread back from poll
 connect system:capture_2 and PulseAudio JACK Source-02:front-right (forward)
 client event poll on 35 for PulseAudio JACK Source-02 starts at 2663848387
 back from client event poll after 63 usecs
 ++ jack_sort_graph
 ++ jack_rechain_graph():
 +++ client is now alsa_pcm active ? 1
 client alsa_pcm: internal client, execution_order=0.
 +++ client is now PulseAudio JACK Sink active ? 1
 client PulseAudio JACK Sink: start_fd=7, execution_order=0.
 client event poll on 27 for PulseAudio JACK Sink starts at 2663848901
 back from client event poll after 29 usecs
 +++ client is now qjackctl active ? 1
 client qjackctl: in subgraph after PulseAudio JACK Sink, execution_order=1.
 client event poll on 24 for qjackctl starts at 2663849026
 back from client event poll after 101 usecs
 +++ client is now PulseAudio JACK Source-02 active ? 1
 11:30:04.546 JACK active patchbay scan...
 client PulseAudio JACK Source-02: in subgraph after PulseAudio JACK Sink, execution_order=2.
 client event poll on 35 for PulseAudio JACK Source-02 starts at 2663849219
 back from client event poll after 93 usecs
 client PulseAudio JACK Sink: wait_fd=28, execution_order=3 (last client).
 -- jack_rechain_graph()
 -- jack_sort_graph
 start poll on 6 fd's
 server thread back from poll
 start poll on 6 fd's
 server thread back from poll
 start poll on 6 fd's
 server thread back from poll
 start poll on 6 fd's
 server thread back from poll
 start poll on 6 fd's
 server thread back from poll
 start poll on 6 fd's
 server thread back from poll
 start poll on 6 fd's
 server thread back from poll
 start poll on 6 fd's
 server thread back from poll
 start poll on 6 fd's
 **** alsa_pcm: xrun of at least 86.505 msecs
 11:30:04.922 XRUN callback (7).
 client event poll on 27 for PulseAudio JACK Sink starts at 2664588293
 back from client event poll after 87 usecs
 client event poll on 24 for qjackctl starts at 2664588418
 back from client event poll after 76 usecs
 client event poll on 35 for PulseAudio JACK Source-02 starts at 2664588528
 back from client event poll after 30 usecs
 load = 56.3900 max usecs: 132086.000, spare = 0.000
 load = 37.3255 max usecs: 4240.000, spare = 18979.000
 load = 23.8783 max usecs: 2422.000, spare = 20797.000
 server thread back from poll
 marking client PulseAudio JACK Sink with SOCKET error state = Triggered errors = 0
 trying to lock graph to remove 1 problems
 11:30:13.130 JACK connection graph change.
 subgraph starting at PulseAudio JACK Sink timed out (subgraph_wait_fd=28, status = 0, state = Triggered, pollret = 0 revents = 0x0)
 at 2672794141 waiting on 28 for 5001145 usecs, status = 1 sig = 2667792976 awa = 0 fin = 0 dur=0
 checking client alsa_pcm: awake at 0 finished at 0
 checking client PulseAudio JACK Source-01: awake at 0 finished at 0
 checking client qjackctl: awake at 0 finished at 0
 checking client PulseAudio JACK Source: awake at 0 finished at 0
 checking client PulseAudio JACK Source-02: awake at 0 finished at 0
 waking server thread
 client PulseAudio JACK Sink has died/exited
 client PulseAudio JACK Source-01 has died/exited
 client PulseAudio JACK Source has died/exited
 client PulseAudio JACK Source-02 has died/exited
 waking server thread
 **** alsa_pcm: xrun of at least 4955.962 msecs
 we have problem clients (problems = 1
 ++ Removing failed clients ...
 client alsa_pcm error status 0
 client PulseAudio JACK Sink error status 10000001
 11:30:13.387 XRUN callback (8).
 removing failed client PulseAudio JACK Sink state = Triggered errors = 10000001
 removing client "PulseAudio JACK Sink"
 removing client "PulseAudio JACK Sink" from the processing chain
 DIS-connect PulseAudio JACK Sink:front-right and system:playback_2
 ++ jack_sort_graph
 ++ jack_rechain_graph():
 +++ client is now alsa_pcm active ? 1
 client alsa_pcm: internal client, execution_order=0.
 +++ client is now PulseAudio JACK Source-02 active ? 1
 client PulseAudio JACK Source-02: start_fd=7, execution_order=0.
 +++ client is now qjackctl active ? 1
 client qjackctl: in subgraph after PulseAudio JACK Source-02, execution_order=1.
 client event poll on 24 for qjackctl starts at 2672795427
 back from client event poll after 40 usecs
 +++ client is now PulseAudio JACK Sink active ? 1
 client PulseAudio JACK Sink: in subgraph after PulseAudio JACK Source-02, execution_order=2.
 client PulseAudio JACK Source-02: wait_fd=28, execution_order=3 (last client).
 -- jack_rechain_graph()
 -- jack_sort_graph
 client event poll on 24 for qjackctl starts at 2672795795
 11:30:13.437 JACK active patchbay scan...
 11:30:13.448 JACK connection change.
 back from client event poll after 35 usecs
 DIS-connect PulseAudio JACK Sink:front-left and system:playback_1
 ++ jack_sort_graph
 ++ jack_rechain_graph():
 +++ client is now alsa_pcm active ? 1
 client alsa_pcm: internal client, execution_order=0.
 +++ client is now PulseAudio JACK Sink active ? 1
 client PulseAudio JACK Sink: start_fd=7, execution_order=0.
 +++ client is now qjackctl active ? 1
 client qjackctl: in subgraph after PulseAudio JACK Sink, execution_order=1.
 client event poll on 24 for qjackctl starts at 2672796635
 back from client event poll after 55 usecs
 +++ client is now PulseAudio JACK Source-02 active ? 1
 client PulseAudio JACK Source-02: in subgraph after PulseAudio JACK Sink, execution_order=2.
 client PulseAudio JACK Sink: wait_fd=28, execution_order=3 (last client).
 -- jack_rechain_graph()
 -- jack_sort_graph
 client event poll on 24 for qjackctl starts at 2672797185
 back from client event poll after 50 usecs
 +++ deactivate PulseAudio JACK Sink
 client PulseAudio JACK Source-01 error status 1
 11:30:13.501 JACK connection graph change.
 client failure: client PulseAudio JACK Source-01 state = Not triggered errors = 1
 removing client "PulseAudio JACK Source-01" from the processing chain
 +++ deactivate PulseAudio JACK Source-01
 client qjackctl error status 0
 client PulseAudio JACK Source error status 1
 client failure: client PulseAudio JACK Source state = Not triggered errors = 1
 removing client "PulseAudio JACK Source" from the processing chain
 +++ deactivate PulseAudio JACK Source
 client PulseAudio JACK Source-02 error status 1
 client failure: client PulseAudio JACK Source-02 state = Not triggered errors = 1
 removing client "PulseAudio JACK Source-02" from the processing chain
 DIS-connect system:capture_2 and PulseAudio JACK Source-02:front-right
 ++ jack_sort_graph
 ++ jack_rechain_graph():
 +++ client is now alsa_pcm active ? 1
 client alsa_pcm: internal client, execution_order=0.
 +++ client is now PulseAudio JACK Source-02 active ? 1
 client PulseAudio JACK Source-02: start_fd=7, execution_order=0.
 +++ client is now qjackctl active ? 1
 client qjackctl: in subgraph after PulseAudio JACK Source-02, execution_order=1.
 client event poll on 24 for qjackctl starts at 2672798789
 back from client event poll after 57 usecs
 client PulseAudio JACK Source-02: wait_fd=25, execution_order=2 (last client).
 -- jack_rechain_graph()
 -- jack_sort_graph
 client event poll on 24 for qjackctl starts at 2672799219
 back from client event poll after 43 usecs
 DIS-connect system:capture_1 and PulseAudio JACK Source-02:front-left
 ++ jack_sort_graph
 ++ jack_rechain_graph():
 +++ client is now alsa_pcm active ? 1
 client alsa_pcm: internal client, execution_order=0.
 +++ client is now qjackctl active ? 1
 client qjackctl: start_fd=7, execution_order=0.
 client event poll on 24 for qjackctl starts at 2672800170
 back from client event poll after 50 usecs
 +++ client is now PulseAudio JACK Source-02 active ? 1
 client PulseAudio JACK Source-02: in subgraph after qjackctl, execution_order=1.
 client qjackctl: wait_fd=25, execution_order=2 (last client).
 -- jack_rechain_graph()
 -- jack_sort_graph
 client event poll on 24 for qjackctl starts at 2672800668
 back from client event poll after 57 usecs
 +++ deactivate PulseAudio JACK Source-02
 ++ jack_sort_graph
 ++ jack_rechain_graph():
 +++ client is now alsa_pcm active ? 1
 client alsa_pcm: internal client, execution_order=0.
 +++ client is now qjackctl active ? 1
 client qjackctl: start_fd=7, execution_order=0.
 client event poll on 24 for qjackctl starts at 2672801628
 back from client event poll after 57 usecs
 client qjackctl: wait_fd=17, execution_order=1 (last client).
 -- jack_rechain_graph()
 -- jack_sort_graph
 -- Removing failed clients ...
 after removing clients, problems = 2
 trying to lock graph to remove 2 problems
 we have problem clients (problems = 2
 ++ Removing failed clients ...
 client alsa_pcm error status 0
 client PulseAudio JACK Source-02 error status 0
 client PulseAudio JACK Source error status 0
 client qjackctl error status 0
 client PulseAudio JACK Source-01 error status 0
 -- Removing failed clients ...
 after removing clients, problems = 0
 start poll on 4 fd's
 server thread back from poll
 new client: PulseAudio JACK Sink, id = 12 type 2 @ 0xb7b49000 fd = 26
 start poll on 5 fd's
 server thread back from poll
 new client PulseAudio JACK Sink using 27 for events
 start poll on 5 fd's
 server thread back from poll
 client event poll on 24 for qjackctl starts at 2672808589
 back from client event poll after 53 usecs
 registered port PulseAudio JACK Sink:front-left, offset = 12288
 start poll on 5 fd's
 server thread back from poll
 client event poll on 24 for qjackctl starts at 2672809398
 back from client event poll after 50 usecs
 registered port PulseAudio JACK Sink:front-right, offset = 16384
 start poll on 5 fd's
 client event poll on 24 for qjackctl starts at 2672824365
 back from client event poll after 113 usecs
 server thread back from poll
 start poll on 5 fd's
 server thread back from poll
 start poll on 5 fd's
 server thread back from poll
 start poll on 5 fd's
 server thread back from poll
 start poll on 5 fd's
 server thread back from poll
 ++ jack_sort_graph
 ++ jack_rechain_graph():
 11:30:13.749 JACK active patchbay scan...
 11:30:13.754 JACK connection change.
 +++ client is now alsa_pcm active ? 1
 client alsa_pcm: internal client, execution_order=0.
 +++ client is now qjackctl active ? 1
 client qjackctl: start_fd=7, execution_order=0.
 client event poll on 24 for qjackctl starts at 2673132839
 back from client event poll after 42 usecs
 +++ client is now PulseAudio JACK Sink active ? 1
 client PulseAudio JACK Sink: in subgraph after qjackctl, execution_order=1.
 client event poll on 27 for PulseAudio JACK Sink starts at 2673133197
 back from client event poll after 31 usecs
 client qjackctl: wait_fd=25, execution_order=2 (last client).
 -- jack_rechain_graph()
 -- jack_sort_graph
 start poll on 5 fd's
 server thread back from poll
 connect PulseAudio JACK Sink:front-left and system:playback_1 (output)
 client event poll on 27 for PulseAudio JACK Sink starts at 2673136358
 back from client event poll after 30 usecs
 ++ jack_sort_graph
 ++ jack_rechain_graph():
 +++ client is now alsa_pcm active ? 1
 client alsa_pcm: internal client, execution_order=0.
 +++ client is now PulseAudio JACK Sink active ? 1
 client PulseAudio JACK Sink: start_fd=7, execution_order=0.
 client event poll on 27 for PulseAudio JACK Sink starts at 2673137554
 back from client event poll after 49 usecs
 +++ client is now qjackctl active ? 1
 client qjackctl: in subgraph after PulseAudio JACK Sink, execution_order=1.
 client event poll on 24 for qjackctl starts at 2673137945
 back from client event poll after 29 usecs
 client PulseAudio JACK Sink: wait_fd=25, execution_order=2 (last client).
 -- jack_rechain_graph()
 -- jack_sort_graph
 start poll on 5 fd's
 server thread back from poll
 connect PulseAudio JACK Sink:front-right and system:playback_2 (output)
 client event poll on 27 for PulseAudio JACK Sink starts at 2673141350
 back from client event poll after 98 usecs
 ++ jack_sort_graph
 ++ jack_rechain_graph():
 +++ client is now alsa_pcm active ? 1
 client alsa_pcm: internal client, execution_order=0.
 +++ client is now qjackctl active ? 1
 client qjackctl: start_fd=7, execution_order=0.
 client event poll on 24 for qjackctl starts at 2673142032
 back from client event poll after 37 usecs
 +++ client is now PulseAudio JACK Sink active ? 1
 client PulseAudio JACK Sink: in subgraph after qjackctl, execution_order=1.
 client event poll on 27 for PulseAudio JACK Sink starts at 2673142197
 back from client event poll after 105 usecs
 client qjackctl: wait_fd=25, execution_order=2 (last client).
 -- jack_rechain_graph()
 -- jack_sort_graph
 start poll on 5 fd's
 server thread back from poll
 new client: PulseAudio JACK Source-03, id = 13 type 2 @ 0xb7b47000 fd = 36
 start poll on 6 fd's
 server thread back from poll
 new client PulseAudio JACK Source-03 using 37 for events
 start poll on 6 fd's
 server thread back from poll
 client event poll on 24 for qjackctl starts at 2673175756
 back from client event poll after 86 usecs
 registered port PulseAudio JACK Source-03:front-left, offset = 0
 start poll on 6 fd's
 server thread back from poll
 client event poll on 24 for qjackctl starts at 2673176146
 back from client event poll after 67 usecs
 registered port PulseAudio JACK Source-03:front-right, offset = 0
 start poll on 6 fd's
 server thread back from poll
 ++ jack_sort_graph
 ++ jack_rechain_graph():
 +++ client is now alsa_pcm active ? 1
 client alsa_pcm: internal client, execution_order=0.
 +++ client is now PulseAudio JACK Sink active ? 1
 client PulseAudio JACK Sink: start_fd=7, execution_order=0.
 client event poll on 27 for PulseAudio JACK Sink starts at 2673201033
 back from client event poll after 30 usecs
 +++ client is now qjackctl active ? 1
 client qjackctl: in subgraph after PulseAudio JACK Sink, execution_order=1.
 client event poll on 24 for qjackctl starts at 2673201171
 back from client event poll after 130 usecs
 +++ client is now PulseAudio JACK Source-03 active ? 1
 client PulseAudio JACK Source-03: in subgraph after PulseAudio JACK Sink, execution_order=2.
 client event poll on 37 for PulseAudio JACK Source-03 starts at 2673201385
 back from client event poll after 78 usecs
 client PulseAudio JACK Sink: wait_fd=28, execution_order=3 (last client).
 -- jack_rechain_graph()
 -- jack_sort_graph
 start poll on 6 fd's
 server thread back from poll
 connect system:capture_1 and PulseAudio JACK Source-03:front-left (forward)
 client event poll on 37 for PulseAudio JACK Source-03 starts at 2673201794
 back from client event poll after 31 usecs
 ++ jack_sort_graph
 ++ jack_rechain_graph():
 +++ client is now alsa_pcm active ? 1
 client alsa_pcm: internal client, execution_order=0.
 +++ client is now PulseAudio JACK Source-03 active ? 1
 client PulseAudio JACK Source-03: start_fd=7, execution_order=0.
 client event poll on 37 for PulseAudio JACK Source-03 starts at 2673202352
 back from client event poll after 36 usecs
 +++ client is now qjackctl active ? 1
 client qjackctl: in subgraph after PulseAudio JACK Source-03, execution_order=1.
 client event poll on 24 for qjackctl starts at 2673202476
 back from client event poll after 106 usecs
 +++ client is now PulseAudio JACK Sink active ? 1
 client PulseAudio JACK Sink: in subgraph after PulseAudio JACK Source-03, execution_order=2.
 11:30:13.996 JACK active patchbay scan...
 client event poll on 27 for PulseAudio JACK Sink starts at 2673202813
 back from client event poll after 29 usecs
 client PulseAudio JACK Source-03: wait_fd=28, execution_order=3 (last client).
 -- jack_rechain_graph()
 -- jack_sort_graph
 start poll on 6 fd's
 server thread back from poll
 connect system:capture_2 and PulseAudio JACK Source-03:front-right (forward)
 client event poll on 37 for PulseAudio JACK Source-03 starts at 2673203190
 back from client event poll after 53 usecs
 ++ jack_sort_graph
 ++ jack_rechain_graph():
 +++ client is now alsa_pcm active ? 1
 client alsa_pcm: internal client, execution_order=0.
 +++ client is now PulseAudio JACK Sink active ? 1
 client PulseAudio JACK Sink: start_fd=7, execution_order=0.
 client event poll on 27 for PulseAudio JACK Sink starts at 2673203569
 back from client event poll after 109 usecs
 +++ client is now qjackctl active ? 1
 client qjackctl: in subgraph after PulseAudio JACK Sink, execution_order=1.
 client event poll on 24 for qjackctl starts at 2673203774
 back from client event poll after 119 usecs
 +++ client is now PulseAudio JACK Source-03 active ? 1
 client PulseAudio JACK Source-03: in subgraph after PulseAudio JACK Sink, execution_order=2.
 client event poll on 37 for PulseAudio JACK Source-03 starts at 2673203965
 back from client event poll after 109 usecs
 client PulseAudio JACK Sink: wait_fd=28, execution_order=3 (last client).
 -- jack_rechain_graph()
 -- jack_sort_graph
 start poll on 6 fd's
 server thread back from poll
 start poll on 6 fd's
 server thread back from poll
 start poll on 6 fd's
 server thread back from poll
 start poll on 6 fd's
 server thread back from poll
 start poll on 6 fd's
 server thread back from poll
 start poll on 6 fd's
 server thread back from poll
 start poll on 6 fd's
 server thread back from poll
 start poll on 6 fd's
 server thread back from poll
 start poll on 6 fd's
 load = 35.7903 max usecs: 11076.000, spare = 12143.000
 load = 29.9327 max usecs: 5590.000, spare = 17629.000
 load = 18.8123 max usecs: 1786.000, spare = 21433.000
 load = 16.2152 max usecs: 3162.000, spare = 20057.000
 load = 14.5162 max usecs: 2976.000, spare = 20243.000
 11:30:19.357 XRUN callback (9).
 delay of 22080.000 usecs exceeds estimated spare time of 20243.000; restart ...
 client event poll on 27 for PulseAudio JACK Sink starts at 2679023052
 back from client event poll after 121 usecs
 client event poll on 24 for qjackctl starts at 2679023244
 back from client event poll after 122 usecs
 client event poll on 37 for PulseAudio JACK Source-03 starts at 2679023431
 back from client event poll after 69 usecs
 load = 22.1877 max usecs: 6933.000, spare = 16286.000
 load = 15.1552 max usecs: 1886.000, spare = 21333.000
 load = 13.5016 max usecs: 2751.000, spare = 20468.000
 server thread back from poll
 marking client PulseAudio JACK Sink with SOCKET error state = Triggered errors = 0
 trying to lock graph to remove 1 problems
 subgraph starting at PulseAudio JACK Sink timed out (subgraph_wait_fd=28, status = 0, state = Triggered, pollret = 0 revents = 0x0)
 11:30:26.849 JACK connection graph change.
 client PulseAudio JACK Source error status 0
 client PulseAudio JACK Source-02 error status 0
 -- Removing failed clients ...
 after removing clients, problems = 0
 start poll on 4 fd's
 server thread back from poll
 start poll on 4 fd's
 11:30:26.890 XRUN callback (10).
 client event poll on 24 for qjackctl starts at 2686544331
 back from client event poll after 108 usecs
 11:30:26.968 JACK active patchbay scan...
 11:30:26.980 JACK connection change.
 server thread back from poll
 start poll on 4 fd's
 server thread back from poll
 start poll on 4 fd's
 11:30:27.182 JACK active patchbay scan...
 server thread back from poll
 start poll on 4 fd's
 server thread back from poll
 start poll on 4 fd's
 load = 7.3882 max usecs: 296.000, spare = 22923.000
 load = 4.2734 max usecs: 269.000, spare = 22950.000
 load = 2.7461 max usecs: 283.000, spare = 22936.000
 load = 2.0040 max usecs: 293.000, spare = 22926.000
 load = 1.6911 max usecs: 320.000, spare = 22899.000
 load = 1.4571 max usecs: 284.000, spare = 22935.000
 load = 1.4349 max usecs: 328.000, spare = 22891.000
 11:30:34.796 Client deactivated.
 11:30:34.799 JACK is stopping...
 server thread back from poll
 +++ deactivate qjackctl
 ++ jack_sort_graph
 ++ jack_rechain_graph():
 +++ client is now alsa_pcm active ? 1
 client alsa_pcm: internal client, execution_order=0.
 -- jack_rechain_graph()
 -- jack_sort_graph
 start poll on 4 fd's
 server thread back from poll
 marking client qjackctl with SOCKET error state = Running errors = 0
 trying to lock graph to remove 1 problems
 we have problem clients (problems = 1
 ++ Removing failed clients ...
 client alsa_pcm error status 0
 client PulseAudio JACK Source-02 error status 0
 client PulseAudio JACK Source error status 0
 client qjackctl error status 10000000
 removing failed client qjackctl state = Running errors = 10000000
 removing client "qjackctl"
 removing client "qjackctl" from the processing chain
 +++ deactivate qjackctl
 client PulseAudio JACK Source-01 error status 0
 client PulseAudio JACK Source-03 error status 0
 ++ jack_sort_graph
 ++ jack_rechain_graph():
 +++ client is now alsa_pcm active ? 1
 client alsa_pcm: internal client, execution_order=0.
 -- jack_rechain_graph()
 -- jack_sort_graph
 -- Removing failed clients ...
 after removing clients, problems = 0
 start poll on 3 fd's
 jack main caught signal 15
 starting server engine shutdown
 stopping driver
 server thread back from poll
 unloading driver
 freeing shared port segments
 stopping server thread
 stopping watchdog thread
 last xrun delay: 4956081.000 usecs
 max delay reported by backend: 4959944.000 usecs
 freeing engine shared memory
 max usecs: 192610.000, engine deleted
 WARNING: 4 message buffer overruns!
 cleaning up shared memory
 cleaning up files
 unregistering server `default'
 11:30:34.987 JACK was stopped successfully.
 11:30:34.989 Post-shutdown script...
 11:30:34.991 killall jackd
 jackd: no process killed
 11:30:35.822 Post-shutdown script terminated with exit status=256.

```

maybe someone can point me in the right direction here......thanks for taking the time to look anyway!!!

---

### Post by markbuntu on 2009-05-16
I didn't really try pulse-jack that much in Jaunty before moving to pulse0.9.15 and alsa 1.0.19 and kernel 2.6.29 and I haven't had the time to test that very thoroughly. Maybe you could play arund with the idle-time parameters in daemon.conf.

If you are using pulse0.9.15 and the pulse-jack module you should look into filing a bug report at the pulseaudio trac. pulse-jack in ubuntu is unsupported so filing a bug report in launchpad against ubuntu will probably be ignored. It looks like that will continue since themuso has already stripped the module-pulse-jack out for pulseaudio in koala.

I am looking into Debian and Fedora and Mandriva to see what can be done about this audio mess in Ubuntu so I am not spending so much time with Ubuntu lately. But anyway I would appreciate if you would keep me informed of what you discover.

---

### Post by mack27 on 2009-05-18
HEELP!! I had some problems with the sound and i followed the tips in this thread and now I have NO SOUND in Skype and other applicationS, and system sounds are much more quiet than before. HEELP!! I must have typed the commands wrong or something... Can somebody help me please.....:cry:

---

### Post by markbuntu on 2009-05-18
Go to the link in the OP for getting hardware information from your machine and get all the info and post it here, along with what version of ubuntu you are using and your general sound setup. It would also be helpful if you went throgh the basic troubleshooting part again.

It is not possible to help you without more specific information.

---

### Post by orys on 2009-05-19
EDITED: Below is now sorted and I have absolutely no idea how it happened. I just was desperate and I decided to start clicking everything arround :P - I started with kmix. I clicked "mute" in "kmix" then I unclicked "mute" and tadaam - it's working now. I did it for another user as well and it seems to work. I'll try to reboot now. 

EDITED AGAIN:Rebooted, everything seems to work fine. Either it's something magic going on or I am simply stupid. 
Anyway that was enjoyable waste of 3 hours :-) 

I am living this below as a couriosity. 


Help. 

I am just getting desperate. 

I did not touched nothing from yesterday but:

Few days ago I noticed that SOMETIMES i got no sound. But when I logged onto another user and then came back to me sound was OK. I told myself that I will deal with that later. 

Then: 
Today suddenly I have no sound at all - nowhere and never. 

I have SB live 5.1 and the card on the motherboard, which is disabled in BIOS, so system can't see it. 

I started with restarting ALSA system - nothing. Then I found this post here: [http://forum.ubuntu.pl/showthread.php?p=600266#post600266](http://forum.ubuntu.pl/showthread.php?p=600266#post600266)

I installed                                                                      >    Kod:
     sudo apt-get install alsa-base alsa-utils alsa-tools alsamixergui                                                           as adviced, I removed Pulseaudio, as adviced - nothing happened. 

When I was restarting ALSA with Rhytmbox on (but still no sound) I had a sound for half a second and system told:

> [I]orys@blaszak-magdy-i-orysia:~$ sudo /etc/init.d/alsa-utils restart 
* Shutting down ALSA... [ OK ] 
* Setting up ALSA... * warning: 'alsactl restore' failed with error message 'alsactl: set_control:1400: Cannot write control '3:0:0:EMU10K1 PCM Send Routing:0' : Operation not permitted 
alsactl: set_control:1400: Cannot write control '3:0:0:EMU10K1 PCM Send Volume:0' : Operation not permitted'... Invalid card number.[/I]Then I followed advice from this thread up to completely reinstaling ALSA - nothing happened except that quoted above daes not repeated anymore. 

I tried every hole in my computer to plug my speakers on and there is no sound. 

I noticed that when the system is going up there is an info: 

> Driver 'pcspkr' is already registered, aborting...I do not know if that's any related but I don't remember nothing like that before... 

PLEASE, help before I will go and hung myself. 

That was the most unlucky upgrade ever. 

Ah, I am using kubuntu 9.04 with new KDE and this is not an hardware fault as it works perfectly in Windows :(

---

### Post by neu2buntu on 2009-05-19
> **markbuntu said:**
> I didn't really try pulse-jack that much in Jaunty before moving to pulse0.9.15 and alsa 1.0.19 and kernel 2.6.29 and I haven't had the time to test that very thoroughly. Maybe you could play arund with the idle-time parameters in daemon.conf.

If you are using pulse0.9.15 and the pulse-jack module you should look into filing a bug report at the pulseaudio trac. pulse-jack in ubuntu is unsupported so filing a bug report in launchpad against ubuntu will probably be ignored. It looks like that will continue since themuso has already stripped the module-pulse-jack out for pulseaudio in koala.

I am looking into Debian and Fedora and Mandriva to see what can be done about this audio mess in Ubuntu so I am not spending so much time with Ubuntu lately. But anyway I would appreciate if you would keep me informed of what you discover.
  
hello Markbuntu, after a few days of tinkering with all things pulseaudio i have solved my problem(POST #250) . i have done quite a few edits of my /etc/pulse/default.pa but none of it seemed to make any difference.  i will post it now

```
# This startup script is used only if PulseAudio is started per-user
# (i.e. not in system mode)

.nofail

### Load something into the sample cache
#load-sample-lazy x11-bell /usr/share/sounds/gtk-events/activate.wav
#load-sample-lazy pulse-hotplug /usr/share/sounds/startup3.wav
#load-sample-lazy pulse-coldplug /usr/share/sounds/startup3.wav
#load-sample-lazy pulse-access /usr/share/sounds/generic.wav
load-sample-dir-lazy /usr/share/sounds/ubuntu/stereo

.fail

### Automatically suspend sinks/sources that become idle for too long
#load-module module-suspend-on-idle

### Automatically restore the volume of streams and devices
#load-module module-device-restore
#load-module module-stream-restore
#load-module module-card-restore

### Automatically augment property information from .desktop files
### stored in /usr/share/application
load-module module-augment-properties

### Load audio drivers statically (it's probably better to not load
### these drivers manually, but instead use module-hal-detect --
### see below -- for doing this automatically)
#load-module module-alsa-sink
#load-module module-alsa-source device=hw:1,0
#load-module module-oss device="/dev/dsp" sink_name=output source_name=input
#load-module module-oss-mmap device="/dev/dsp" sink_name=output source_name=input
#load-module module-null-sink
#load-module module-pipe-sink

### Automatically load driver modules depending on the hardware available
.ifexists module-hal-detect.so
load-module module-hal-detect tsched=0
.else
### Alternatively use the static hardware detection module (for systems that
### lack HAL support)
#load-module module-detect
.endif

### Automatically load driver modules for Bluetooth hardware
.ifexists module-bluetooth-discover.so
load-module module-bluetooth-discover
.endif

### Load several protocols
.ifexists module-esound-protocol-unix.so
load-module module-esound-protocol-unix
.endif
load-module module-native-protocol-unix

### Network access (may be configured with paprefs, so leave this commented
### here if you plan to use paprefs)
#load-module module-esound-protocol-tcp
#load-module module-native-protocol-tcp
#load-module module-zeroconf-publish

### Load the RTP reciever module (also configured via paprefs, see above)
#load-module module-rtp-recv

### Load the RTP sender module (also configured via paprefs, see above)
#load-module module-null-sink sink_name=rtp format=s16be channels=2 rate=44100 description="RTP Multicast Sink"
#load-module module-rtp-send source=rtp.monitor

### Load additional modules from GConf settings. This can be configured with the paprefs tool.
### Please keep in mind that the modules configured by paprefs might conflict with manually
### loaded modules.
.ifexists module-gconf.so
.nofail
load-module module-gconf
.fail
.endif

### Automatically restore the default sink/source when changed by the user during runtime
#load-module module-default-device-restore

### Automatically move streams to the default sink if the sink they are
### connected to dies, similar for sources
load-module module-rescue-streams

### Make sure we always have a sink around, even if it is a null sink.
#load-module module-always-sink


### Load pulse jack mods
load-module module-jack-sink
load-module module-jack-source


### If autoexit on idle is enabled we want to make sure we only quit
### when no local session needs us anymore.
load-module module-console-kit

### Enable positioned event sounds
load-module module-position-event-sounds

### Cork music streams when a phone stream is active
load-module module-cork-music-on-phone

# X11 modules should not be started from default.pa so that one daemon
# can be shared by multiple sessions.

### Load X11 bell module
#load-module module-x11-bell sample=bell-windowing-system

### Register ourselves in the X11 session manager
#load-module module-x11-xsmp

### Publish connection data in the X11 root window
#.ifexists module-x11-publish.so
#.nofail
#load-module module-x11-publish
#.fail
#.endif

### Make some devices default (i copied these from qjackctl not sure if work)
set-default-sink PulseAudio_JACK_Sink
set-default-source PulseAudio_JACK_Source
```

i can also post my /etc/pulse/client.conf & /etc/pulse/daemon.conf if needed by anyone.

the answer was to do code ```
paprefs
``` and enable these options in screenshot....  well hopefully this can help someone,   and i am error free in my log files too (which is good) i will keep updating if i find anything more

---

### Post by markbuntu on 2009-05-19
Well, it is good you figured that one out, kudos to you. The only thing I can figure is that pa needed another sink to occupy it and keep it from going idle. I would guess the loopback is keeping the connection to jack from crashing.

I was just at the jack website, their newsest version 0.19.2 included this in the release notes
> 
D-BUS based device reservation to better coexist with PulseAudio on Linux.


Things are definitely looking up for us pulse-jack users.

There are a few recent bugs reported for pulse-jack at the pulseaudio trac list. You might want to look at them and maybe make one about your experience. The devs are very active on the pulseaudio mailing list also so you might want to check that out too. 

Did you make any changes in the daemon.conf or client.conf that made any difference?

---

### Post by neu2buntu on 2009-05-19
thanks....yeah i think your right about the loopback keeping the sink alive in jack ,.. the only problem i noticed was an increase in xruns so i had to increase frames/period in qjackctl to calm this a bit)  as i usually work with loops made in lmms and exported,then brought into ardour this is not a worry at the minute!!

> Things are definitely looking up for us pulse-jack users.

about time..lol...  it takes a lot of trial and error/luck/troubleshooting/googling/etc to get this all setup. oh and not forgetting this guide too!!!!

i have been looking at the trac and i will post on my experience.

changes to client.conf 
default-sink = jack_out         
default-source = jack_in       
; default-server = pulseaudio (not sure what to set this to eg ~/.pulse)
disable-shm = no
shm-size-bytes = 0 # setting this 0 will use the system-default, usually 64 MiB

and to daemon.conf
disallow-module-loading = no
use-pid-file = yes
high-priority = yes
nice-level = -11
resample-method = src-linear

i have been editing the /etc/pulse files for so long now i cant remember exactly if some of these values were originally uncommented (; or #) but the default sink and source were def changed by me (i will have to start writing my changes down..lol)    anyway thanks for your time and your great guide Markbuntu....cheers

---

### Post by missacrane on 2009-05-19
this ABSOLUTELY worked for me!!! i'm very grateful i have sound:

**No sound at all**
There are many links here for specific sound cards/chips and the answer you need may not be in the OP so you should look through the entire thread if it seems to be relevant to your problem. You should also post in that thread instead of starting a new one if possible. (Starting a new thread just fragments information and makes it more difficult for people to find answers so please try to avoid that.) Posting in a running thread will push it the the top and more people will notice it and reply. Someone will be along to help you if they can so please be patient. If you get no answer after one day, it is OK to bump the thread.

If you still have no sound after going through this guide and all the relevant links, you should do a search either in these forums or with google for your specific sound card/problem because there is about a %100 chance that someone has figured out your problem already. You can also try looking in the Mandriva and Fedora and SUSE and Debian forums, there are many smart people there. If you still cannot find any help, it is OK to start a new thread. If you find any information somewhere else that you think others might need, please bring it back.

**Missing Volume Controls**
If you seem to be missing some items from the volume control in your panel ( the little speaker icon) you most likely just need to make them visible. Right click on the little speaker and choose Open Volume Control. Make sure the Device: xxxxxxxxxx is your hardware device. It should be something like
Device: HDA ATI SB (Alsa mixer) or Device: HDA Intel(Alsa mixer) or Device:C-Media 8768 (Alsa mixer) etc, in other words, a hardware device with an Alsa mixer.
Once you have the proper device selected click on Preferences down at the lower right. This will show you a list of check boxes. Check all the items you want to appear in the volume control and close the box.

**Try This First**
Go to System/Preferences/Sound and switch everything except Default Mixer Tracks to ALSA or Pulse Audio. if you see ...HDMI... in Default Mixer Tracks, change it to your sound card/chip, Realtecxxxx or Emuxxx or ATI SB or HDA INTEL or something like that, anything but HDMI that is not Capture or Playback or OSS.

Right click on the speaker icon on the top panel and choose Open Volume Control. Click File/Change Device and make sure you have the correct device chosen. Go to Edit/Preferences and check the following boxes: Main, PCM, CD, PC Speaker, Mic, mic boost, mic capture, mic boost capture, etc. You may or may not have these and more. In the Playback tab make sure the sliders are up and there are no red x over the little speakers. In the Recording tab, do the same. In the Switches tab check any boxes marked mix, 3D control, mic boost, capture, etc. In the Options tab, make sure the Line in mode and Mic-on mode and any other option is like how you have your speakers plugged in. (Some surround sound outputs are also line in and mic inputs and can be switched here.) Make sure any SPDIF or IEC958 or External Amplifier boxes are unchecked. (With some sound cards/chips these will turn off your sound so for now leave them off.) Close that window, right click on the icon again and choose Preferences. Make sure the device listed in the box is your sound card and select Master. Close the window. Now left click on the speaker icon and move the slider all the way up.

Try to play something, Rythmbox is a good choice, so is totem or mplayer. (Firefox/flash is not such a good choice at this time since it may not be working for other reasons). If you still get no sound, read on.:KS

---

### Post by markbuntu on 2009-05-20
> **neu2buntu said:**
> .....  as i usually work with loops made in lmms and exported,then brought into ardour this is not a worry at the minute!!
> 

Yeah, I should get back to doing some of that myself.....


resample-method = src-linear


Have you tried using speex-float-1 or any of the other higher quality resampling settings? src-linear is used by ubuntu to get around their kernel issues. 

I need to find a rt kernel that works with my hardware, I will probably have to build it myself....if I ever get the time....

There is a few recent posts at the pulse mailing list about jack. I find the mailing list most enlightening about progress with pulse. It is not so busy so it is easy to keep up with and the devs are always posting. I get a lot of my info about pulse from that list.

---

### Post by neu2buntu on 2009-05-20
hey Markbuntu... no i have not tried any of the other option like "speex-float-1" i have actually looked at my options by doing ```
pulseaudio --dump-resample-methods
```, but was unsure of the best choice.... i will have to spend more time in the pulse mailing list etc.....

> I need to find a rt kernel that works with my hardware, I will probably have to build it myself....if I ever get the time....    this sounds like a big project eg patching or building a kernel (way above my head atm) good luck with that... and maybe you can get it released!!

i will just keep reading and learning so i can understand better the whole ubuntu sound structure...

---

### Post by jeps on 2009-05-23
hi,
i've been struggling with this Jack/PulseAudio setup for quite some time, reading through this and other guides.
I'm using Ubuntu Studio 9.04 with an Intel HDA.
When I boot the system all sounds are playing nicely, and the sound recorder can record from the microphone as well as the monitor. But as soon as I start Jack, all sounds disappear and I get an error("Failed to construct test pipeline for 'gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat'") when I try to test the recording under system>settings>sound... Jack seems to run fine though(even with rt enabled) and I am able to record from the microphone with the Sound Recorder or Ardour. But if I try to start the radio, a youtube-clip or play an mp3 with Rhythmbox, it just stalls so there's no way to test if it can record from the monitor.
When I run these lines,
pactl load-module module-jack-sink
pactl load-module module-jack-source,
I start getting tons of xruns, from the sink I think.
And lastly, when I try to run system>settings>Default Sound Card, nothing happens -a tab appears saying: starting Default Sound Card, but after 10 secs it just disappears.

Hope someone can help me out here

---

### Post by markbuntu on 2009-05-24
If you are using Jaunty9.04 you should upgrade pulseaudio to 0.9.15 using themuso's repository and then add the pulse-jack modules from the debian repo or build them youself from source. Follow the directions in the OP.

Juanty uses pulse0.9.14 which has a lot of problems and was not reccomended by the pulse devs for inclusion in distributions.

The Default Sound card app may be deprecated. All it does is add a few lines in asoundrc.asoundconf to make pulse the default for alsa apps which should be automatic in Jaunty so it is not really something to worry about.

---

### Post by neu2buntu on 2009-05-24
> The Default Sound card app may be deprecated. All it does is add a few lines in asoundrc.asoundconf to make pulse the default for alsa apps which should be automatic in Jaunty so it is not really something to worry about.   i think it is the default in jaunty,... i have found that the .asoundrc controls whether the .asoundrc.asoundconf script file runs or not (make sure the last line is not commented out # in .asoundrc) and look for these lines at the end of .asoundrc.asoundconf 
```
pcm.!default { type pulse }
ctl.!default { type pulse }
```

---

### Post by landgrvi on 2009-05-26
Markbuntu and everyone, thanks for all the effort.  This thread has helped me a lot.

I'd like to add a little bit of information regarding running pulseaudio through jack.  I'm running Ubuntu 8.04 (Hardy), pretty much stock everything -- no rt kernel, sticking with packages from the standard Hardy repos wherever possible -- so I have pulseaudio 0.9.10, jack 0.109.2.   The machine is a Gateway 3040GZ, with onboard sound card Intel 82801DB-ICH4.  I followed the "Pulse Audio through jack" section in the original post and had to make a small change.  

On my system,
```
pactl load-module module-jack-sink
pactl load-module module-jack-source
```did not work.  Instead of coming back with a module number, it showed "Failure: Module initalization failed".

Instead, I had to do
```
pactl load-module module-jack-sink channels=2 channel_map=front-left,front-right 
pactl load-module module-jack-source channels=2 channel_map=front-left,front-right
```I don't know if the difference has more to do with my software or my hardware, but it might help somebody else.

Also, there's a minor typo in that section:  pulse-audio-module-jack should be pulseaudio-module-jack.

I'm definitely having more fun with my audio now that I don't have to stop jack whenever I want to do 'normal' stuff.  Thanks again, all.

---

### Post by alex777 on 2009-05-27
I have followed this guide and installed PulseAudio. Now I have a **problem with Skype** (it worked with ALSA perfectly).

I have several audio devices on my system. With Skype I use two of them: VXI headset for sound in and out, and HDA Intel for ringing. When I choose the appropriate devices in Skype (Options -> Sound Devices), they work, but there's a minor problem:
- the incoming sound in the headset is too low, though it's set to 100% in PulseAudio's Volume Control;
- PulseAudio doesn't recognize the incoming and outgoing audiostreams when I use Skype (Volume Control -> Playback and Recording), so Skype isn't using PulseAudio at all?

The major problem is as follows. Skype doesn't remember the sound devices I have chosen. After a reboot Skype doesn't work, and when I open Options -> Sound Devices I see that quite different devices are set which are not appropriate (HDA Intel for Sound In and Out, web camera for ringing). I can't save the settings I have chosen.

---

### Post by markbuntu on 2009-05-27
> **landgrvi said:**
> Markbuntu and everyone, thanks for all the effort.  This thread has helped me a lot.

I'd like to add a little bit of information regarding running pulseaudio through jack.  I'm running Ubuntu 8.04 (Hardy), pretty much stock everything -- no rt kernel, sticking with packages from the standard Hardy repos wherever possible -- so I have pulseaudio 0.9.10, jack 0.109.2.   The machine is a Gateway 3040GZ, with onboard sound card Intel 82801DB-ICH4.  I followed the "Pulse Audio through jack" section in the original post and had to make a small change.  

On my system,
```
pactl load-module module-jack-sink
pactl load-module module-jack-source
```did not work.  Instead of coming back with a module number, it showed "Failure: Module initalization failed".

Instead, I had to do
```
pactl load-module module-jack-sink channels=2 channel_map=front-left,front-right 
pactl load-module module-jack-source channels=2 channel_map=front-left,front-right
```I don't know if the difference has more to do with my software or my hardware, but it might help somebody else.

Also, there's a minor typo in that section:  pulse-audio-module-jack should be pulseaudio-module-jack.

I'm definitely having more fun with my audio now that I don't have to stop jack whenever I want to do 'normal' stuff.  Thanks again, all.

Thanks for pointing out that typo, it is fixed now.

Hmmm, the channel mapping problem is probably very hardware/driver specific since no one has mentioned this before.
How does aplay -l report that card?
And cat /proc/asound/modules?

That information will be more specific so I can make a special note about it.

My c-media card maps front left and front right channels automatically and my mobo ALC883 maps 5 channel surround front left, front right, rear left, rear right, and center/lfe, also automatic. It sort of depends on what distro, alsa/pulse versions I am using ( I have 6 different distros on this machine, 3 are Ubuntu, 2 are hardy).

You should give the rt kernel a try. Jack will work much better with rt enabled. The generic kernel will still be available unchanged in grub if you don't like it or if it does not work, which can happen.

Congratulations on getting it all working.

Enjoy :guitar:

---

### Post by markbuntu on 2009-05-27
> **alex777 said:**
> I have followed this guide and installed PulseAudio. Now I have a **problem with Skype** (it worked with ALSA perfectly).

I have several audio devices on my system. With Skype I use two of them: VXI headset for sound in and out, and HDA Intel for ringing. When I choose the appropriate devices in Skype (Options -> Sound Devices), they work, but there's a minor problem:
- the incoming sound in the headset is too low, though it's set to 100% in PulseAudio's Volume Control;
- PulseAudio doesn't recognize the incoming and outgoing audiostreams when I use Skype (Volume Control -> Playback and Recording), so Skype isn't using PulseAudio at all?

The major problem is as follows. Skype doesn't remember the sound devices I have chosen. After a reboot Skype doesn't work, and when I open Options -> Sound Devices I see that quite different devices are set which are not appropriate (HDA Intel for Sound In and Out, web camera for ringing). I can't save the settings I have chosen.

Skype, bleh. Skype is a mess, buggy plugins that they do not seem interested in fixing and using pulse 0.9.14 for Jaunty was not really the best thing to do since it is also pretty buggy. You might want to try pulseaudio 0.9.15 which is much better. There is a link to themuso's repository in the OP.

There are also some threads around here about setting up skype in Jaunty.

---

### Post by mocha on 2009-05-31
I'm having problem with Pulse and Jack after upgrading to Jaunty.  Pulseaudio seg faults when loading the jack sink and source.  I tried you guys' suggestions a few posts back but it's still not working.  Do you think upgrading to 0.9.15 will fix this?  I rely on the pulse-jack thing to get audio in recordmydesktop.  Thanks.

---

### Post by markbuntu on 2009-05-31
With Jaunty you need to set session sounds to none or jack will not start. I have had no problems with pulse-jack with 0.9.15. Pulse 0.9.14 was not reccomended for use by the pulse devs anyway.

---

### Post by landgrvi on 2009-05-31
> **markbuntu said:**
> 
Hmmm, the channel mapping problem is probably very hardware/driver specific since no one has mentioned this before.
How does aplay -l report that card?
And cat /proc/asound/modules?

That information will be more specific so I can make a special note about it.

My c-media card maps front left and front right channels automatically and my mobo ALC883 maps 5 channel surround front left, front right, rear left, rear right, and center/lfe, also automatic. It sort of depends on what distro, alsa/pulse versions I am using ( I have 6 different distros on this machine, 3 are Ubuntu, 2 are hardy).


Hmmm, interesting!  And here I was thinking it was a hardy thing.

aplay -l shows:
```
**** List of PLAYBACK Hardware Devices ****
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 0: Intel ICH [Intel 82801DB-ICH4]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 4: Intel ICH - IEC958 [Intel 82801DB-ICH4 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```and cat /proc/asound/modules shows:
 ```
0 snd_intel8x0
```and this is what I got in my syslog that led me to supply the channel_map argument:
 ```
pulseaudio[6026]: module-jack-sink.c: Failed to parse channel_map= argument.
```

---

### Post by uncoolbob on 2009-06-01
Haven't read this mighty thread, but it looks like there's a lot of useful info here.

<vent>
I just recently finally sorted out how to use pulsesudio properly to switch between headphones and USB speakers.  My gripe is that (my) 8.10 did not come with any of the useful pulseaudio stuff installed as default (e.g. pavucontrol paman etc).  Maybe that was to keep things simple for the majority of systems with one output.

In the end I still have no idea what Preferences->Sound does :-)
</vent>

---

### Post by kgpdeveloper on 2009-06-09
I need help.
Sounds are not working at all.

**options snd-hda-intel model=gateway**

used to work for me when I was using Ubuntu 8.10.
I am now using Ubuntu 9.04

I have no pulseaudio installed. 

Check other information on my setup here:
[http://www.alsa-project.org/db/?f=562f9b54f5ee65834b399dbbc1ab620ceb33a5c5](http://www.alsa-project.org/db/?f=562f9b54f5ee65834b399dbbc1ab620ceb33a5c5)

If there's anyone who can help me figure out how to fix this, it would be great. Again, it used to be easy to fix sound problem. Don't know what's wrong now.

---

### Post by PizzaOfHut on 2009-06-09
I have an Audigy 2 sound card and am getting no sound at all from my new Jaunty install. lspci IS showing that Linux is recognizing my card, as follows:

```
mwaters@knives:~$ lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 655 Host (rev 50)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS964 [MuTIOL Media IO] (rev 36)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:09.0 Network controller: RaLink RT2561/RT61 802.11g PCI
00:0c.0 Multimedia audio controller: Creative Labs SB Audigy (rev ff)
00:0c.1 System peripheral: Creative Labs SB Audigy Game Port (rev 04)
00:0c.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (rev 04)
01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7800 GS] (rev a2)

```

I have the emu10k1 ALSA module loaded, as that was the default when installing the system, however, the weird part is that when I fire up any mixers or sound control panels, they all report that I have no sound card installed, however, before I installed my new wireless NIC a few hours ago to replace my useless POS I had been using, these programs DID, in fact, recognize that I had an Audigy installed.

If any of you have any helpful advice, or can point me to somewhere this situation has been dealt with, I would be most appreciative.

---

### Post by asmaia on 2009-06-25
Hello, I think I did something wrong. I tried to fix my audio without knowing much about Ubuntu, so I typed in the terminal the instructions under ASLA Trouble, and to make a long story short, my computer now only boots into the terminal, or a screen that looks like DOS.

I don't know what I did. Can someone please help?? It says that it can't locate some of the updates and it all scrolls past too fast, but I'm not sure I did it right anyway. I run (or ran, as it seems almost gone now) Ubuntu Hardy Heron 8.04.

---

### Post by neu2buntu on 2009-06-26
if you were reinstalling "alsa" your desktop will have been uninstalled. if this is the case do this command from your terminal 
```
sudo apt-get install gdm ubuntu-desktop
```   followed by return and your password (password doesnt show when typing)...

---

### Post by EVendla on 2009-07-14
Hello,

Im a fresh user of Ubuntu 9.04 for a day or two now (no previous experience with Linux/Ubuntu).
My problem is that I get absolutely no sound though the device seems to have been detected correctly. My motherboard is Epox 8 KRA I (sound is onboard).

```
sudo lshw -C multimedia
  *-multimedia            
       description: Multimedia audio controller
       product: VT8233/A/8235/8237 AC97 Audio Controller
       vendor: VIA Technologies, Inc.
       physical id: 11.5
       bus info: pci@0000:00:11.5
       version: 60
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: driver=VIA 82xx Audio latency=0 module=snd_via82xx

``````
lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT8377 [KT400/KT600 AGP] Host Bridge (rev 80)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
00:0f.0 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon X1950 GT (rev 9a)
01:00.1 Display controller: ATI Technologies Inc Radeon X1950 GT (Secondary) (rev 9a)

```I have searched and messed around for a whole day now but to no avail (setting volumes, muting/unmuting, setting default devices etc.). Also, since I dont know pretty much anything about how Linux works I cant really solve the problem on my own. Some help would be deeply appreciated. Oh, and if you know the solution, try to explain it detail-by-detail since I am not too familiar with the commands nor the interface.

Best regards,
EVendla

EDIT: It appears that the problem was more hardware related. The fix was as simple as connecting an audio cable between the motherboard and the front panel.

---

### Post by igorzwx on 2009-07-14
ask markbuntu

---

### Post by markbuntu on 2009-07-14
> **EVendla said:**
> Hello,

Im a fresh user of Ubuntu 9.04 for a day or two now (no previous experience with Linux/Ubuntu).
My problem is that I get absolutely no sound though the device seems to have been detected correctly. My motherboard is Epox 8 KRA I (sound is onboard).

```
sudo lshw -C multimedia
  *-multimedia            
       description: Multimedia audio controller
       product: VT8233/A/8235/8237 AC97 Audio Controller
       vendor: VIA Technologies, Inc.
       physical id: 11.5
       bus info: pci@0000:00:11.5
       version: 60
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: driver=VIA 82xx Audio latency=0 module=snd_via82xx

```
```
lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT8377 [KT400/KT600 AGP] Host Bridge (rev 80)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
00:0f.0 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon X1950 GT (rev 9a)
01:00.1 Display controller: ATI Technologies Inc Radeon X1950 GT (Secondary) (rev 9a)

```
I have searched and messed around for a whole day now but to no avail (setting volumes, muting/unmuting, setting default devices etc.). Also, since I dont know pretty much anything about how Linux works I cant really solve the problem on my own. Some help would be deeply appreciated. Oh, and if you know the solution, try to explain it detail-by-detail since I am not too familiar with the commands nor the interface.

Best regards,
EVendla

I don't know of any particular problems with that driver but I know there are some problems with the AC'97 drivers in general in Jaunty but I am not sure if they have been fixed yet. Do you have all the updates?

If you are fully updated you might want to first try reinstalling alsa and if that does not work try a newer alsa version. There is a section in the OP for how to do all that.

---

### Post by nugget1960 on 2009-07-14
Creative SB live no sound.

I'm new at this, so please excuse any obvious dumbness. I fitted the card and installed Mythbuntu (Ubuntu 9.04 i386 amd64).

 There is no sound - no login sound either. There is no speaker icon on the desktop..

This is the information I extracted from my machine:

 lspci
00:00.0 Host bridge: Intel Corporation 82925X/XE Memory Controller Hub (rev 04)
00:01.0 PCI bridge: Intel Corporation 82925X/XE PCI Express Root Port (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FR/FRW (ICH6R/ICH6RW) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation NV36 [GeForce PCX 5750] (rev a2)
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express (rev 01)
04:02.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 62)
04:02.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 65)
04:03.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 08)
04:03.1 Input device controller: Creative Labs SB Live! Game Port (rev 08)


lsusb
Bus 002 Device 002: ID 2040:8400 Hauppauge 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 002: ID 073a:2130 Chaplet Systems, Inc. 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

cat /proc/asound/cards
 0 [Live           ]: EMU10K1 - SB Live 5.1
                      SB Live 5.1 (rev.8, serial:0x80641102) at 0xdce0, irq 16




cat /proc/asound/modules
 0 snd_emu10k1


aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Live [SB Live 5.1], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Subdevices: 32/32
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
  Subdevice #8: subdevice #8
  Subdevice #9: subdevice #9
  Subdevice #10: subdevice #10
  Subdevice #11: subdevice #11
  Subdevice #12: subdevice #12
  Subdevice #13: subdevice #13
  Subdevice #14: subdevice #14
  Subdevice #15: subdevice #15
  Subdevice #16: subdevice #16
  Subdevice #17: subdevice #17
  Subdevice #18: subdevice #18
  Subdevice #19: subdevice #19
  Subdevice #20: subdevice #20
  Subdevice #21: subdevice #21
  Subdevice #22: subdevice #22
  Subdevice #23: subdevice #23
  Subdevice #24: subdevice #24
  Subdevice #25: subdevice #25
  Subdevice #26: subdevice #26
  Subdevice #27: subdevice #27
  Subdevice #28: subdevice #28
  Subdevice #29: subdevice #29
  Subdevice #30: subdevice #30
  Subdevice #31: subdevice #31
card 0: Live [SB Live 5.1], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: Live [SB Live 5.1], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


arecord -l
**** List of CAPTURE Hardware Devices ****
card 0: Live [SB Live 5.1], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Live [SB Live 5.1], device 1: emu10k1 mic [Mic Capture]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Live [SB Live 5.1], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0





Any help appreciated

Nugget1960

---

### Post by ranch hand on 2009-07-15
nugget1960

Is your onboard sound manager turned off/disabled in bios?

---

### Post by nugget1960 on 2009-07-15
Ranch Hand

Yes I switched off the onboard sound. Any other thoughts?

Nugget1960

---

### Post by ranch hand on 2009-07-15
I am concerned that you do not have the volume control applet.  This is not right.

Check to see if the gnome-alsamixer is installed (check in synaptic).  If not install it and if it is reinstall it.

---

### Post by ranch hand on 2009-07-15
If the above didn't work go to System->Administration->Services.  Unlock and make sure that Audio settings is checked.  Reboot.

If the above does not work, right click on your upper pannel, just left of the notification area, click on "add to panel".  Go to the bottom of the list and highlight "volume control".

The two of those should give you a working volume control.

Make sure that it says, by device, your cards name (my case=SB Sudigy 1 ES [SB0160](Alsa mixer)).  If not click on that panel and see if yours is on the list there and click on it.

Also check setting in System->Prefrences->Sound->Devices.

---

### Post by nugget1960 on 2009-07-18
[ranch hand]("http://ubuntuforums.org/member.php?u=647614"), thanks for your help on this.

It turns out that in trying to setup for surround, I had made a change in MythTV frontend that stopped the sound. When I changed it to ALSA:default, I got sound. Now I just have to fiddle around to get 5.1 surround sound working.

Nugget1960

---

### Post by ranch hand on 2009-07-19
The only SB card that I know anything about is the one I have in this box.  It is 5.1 and things sound great as long as I have the wires hooked up right from the box to the main unit (Old altec lansing 5.1 speaker set).

I am on 9.10 alpha2 right now and it does fight a bit every now and then but it sounds good (Jackson Browne right now).

Good luck

---

### Post by wizard10000 on 2009-07-19
Excellent thread - thank you  :)

My own experience has been that an upgrade to 64-bit Jaunty altered policy settings denying me access to soundcard and TV tuner card.

Did a total of three clean installs of Jaunty this week with two different sound cards - and right after the install sound worked fine.  After installing recommended updates sound went away along with my TV tuner card and the ability to shut down, suspend or hibernate the system.

aplay -l showed no soundcard detected.

Anyway, after about four days of messing with it I found that although policykit said I had access to the soundcard and so on, I didn't - permissions looked like this:

Anyone:  No
Console:  No
Active Console:  Yes

Okay, you'd think I'd be able to use the soundcard but it didnt' work.  Had to set 'console' to yes to get the hardware working again.

I'd file a bug but I'm not sure which package broke it.  Hope this helps someone else.

---

### Post by markbuntu on 2009-07-19
file that against policykit.

---

### Post by wizard10000 on 2009-07-20
> **markbuntu said:**
> file that against policykit.

Added it to existing bug #370982.

thanks -

---

### Post by chris777E on 2009-07-26
My distribution is Intrepid 64bits.

```
[SIZE=2]grep 'audio' /etc/group[/SIZE]
```for me this command line return : 
```

audio:x:29:pulse,chris777

```Alsa don't work for me. When I tested sound in Application->setup->sound it's return :

```

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Impossible d'obtenir ou de définir un paramètre de ressource

```How can I resolve my problem?

---

### Post by bresdog on 2009-07-27
Ive been struggling with my sound since i installed Jaunty, ive tried looking through lots of other threads and trying suggestions there but ive had no luck. Im getting sound through headphones and when using external speakers but i cant get any sound through my laptops internal speakers. Any suggestions?

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

lspci -v
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
	Subsystem: Hewlett-Packard Company Device 3613
	Flags: bus master, slow devsel, latency 64, IRQ 16
	Memory at d4400000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

---

### Post by shane2peru on 2009-07-29
Thanks!!!
> ALSA Trouble

If you are having problems with ALSA the first thing you should try is to reload the alsa drivers. In a terminal type:

Code:

killall pulseaudio

sudo alsa force-reload

pulseaudio -D


This fixed my issue, apparently it is a kernel bug, and will have to wait for it to be fixed!  Arggh.  At least I have a work around.  This is odd though, because it just showed up after using my box for over a month without issues.

Shane

---

### Post by caalamus on 2009-08-07
Hi...
 I am trying to get a 500Mhz g3 iBook, with 540MB of ram and a firewire bus.... recording via firewire. I am running Ubuntu 9.04

Initially I couldn't even use it due to display issues. I've sorted that out using terminal commands I found on this forum. I must say, it was a good feeling. 

Now I want to get into the audio stuff. That's what this computer was purchased for.

A few things:

Is there a version of Ubuntustudio compatible with PowerPC machines?

Some say no... but I found a page through Google which *seems* to indicate yes.

Freebob, FFADO... Jack? Will that be enough to use my Firewire audio interfaces?

I tried to install Ubuntustudio using the walk through found here

[http://www.ubustu.com/globe/2007/05/...buntu-install/](http://www.ubustu.com/globe/2007/05/...buntu-install/)

...and everything seemed fine, but then it "couldn't find linux-rt"

What do you think?


:]

---

### Post by markbuntu on 2009-08-07
You should be able to use FFADO, it is much improved lately. You can find liunux-rt with the synaptic package manager you should also be able to find the ubuntustudio audio and ubuntustudio audio-plugins metapackages with synaptic.

There are newer versions fo FFADO and Jack available hopefully they will be in the next ubuntu release in Oct.

---

### Post by brunog on 2009-08-07
I have followed the instructions, and believe I have done it all correctly. All output sound works fine, but I cannot get my mic to work - not in sjype and not using Sound Recorder.
I had it working a while ago, but cannot remember how, now it is just gone.
If I open Volume Control - it show the setting for Intel ICH5 (ALSA Mixer). The recording tab shows Capture, but the littel mic icon has a red X. I deselct this - does not make a difference, when I open the Volume control again, this little mic is once again muted? It does not stay un-muted - not sure if this is the problem.

---

### Post by markbuntu on 2009-08-07
> **brunog said:**
> I have followed the instructions, and believe I have done it all correctly. All output sound works fine, but I cannot get my mic to work - not in sjype and not using Sound Recorder.
I had it working a while ago, but cannot remember how, now it is just gone.
If I open Volume Control - it show the setting for Intel ICH5 (ALSA Mixer). The recording tab shows Capture, but the littel mic icon has a red X. I deselct this - does not make a difference, when I open the Volume control again, this little mic is once again muted? It does not stay un-muted - not sure if this is the problem.

Those problems are very hardware specific and concern the alsa driver. You might try upgrading your alsa version or looking in the links in the HDA  section of the OP.

---

### Post by caalamus on 2009-08-08
Sorry bear with me :]

I connect to the internet and run the commands in terminal like I did... but when it says that it can't find "linux-rt", I use Synaptic to locate it on my machine or on the internet? I have **NO ** experience with Synaptic.

If you could, can you please give me a walk through on getting FFADO in order?

I really appreciate your response and any info, including that which you have already provided is gratefully received.

(the scope of my expertise thus far has been fixing screen resolution... yeah I make music... not source code... but I'm trying :] )

---

### Post by markbuntu on 2009-08-09
There are people at the multimedia production forum that can help you with FFADO.

---

### Post by caalamus on 2009-08-10
well o.k,
    thanks :]

---

### Post by PowerSource on 2009-08-11
at 5% volume it sounds really much. at 30% it sounds really much and my headphones are vibrating.
any idea why the volume is so messed up?
I recently installed this [http://ubuntuforums.org/showthread.php?t=870001&highlight=Creative+Soundblaster](http://ubuntuforums.org/showthread.php?t=870001&highlight=Creative+Soundblaster) . but not the oss in the guide.

---

### Post by MyOwnOwner on 2009-08-14
Hello,

After some trouble and trying out the guide here (not working for me in the past),
I finally found a solution for getting the sound working on a [COLOR="Red"]HP Pavilion dv7 1018eg[/COLOR].

I followed the guide [ATTENTION HP dvX laptop owners with speaker sound issues ...]("http://ubuntuforums.org/showthread.php?t=1073090").

All I changed was the 4th. command into 
sudo nano /etc/modprobe.d/alsa-base.conf

Hope this helps others getting their sound fixed. 
Keep up the good work :)

---

### Post by kastanedowski on 2009-08-21
Well after trying everyhing at last i really mess up with my computer, the worst was "re installing"  "Packages gdm and ubuntu-desktop are also removed"  NO WAY TO COME BACK AND PROBLEMS WITH GNOME

NEVER BUT NEVER FOLLOW THE BELOW ADVICE, the sound is the same bad quality and not the sounds stops from time to time


I REPEAT NEVER DO THIS BELOW!

"**Reinstalling ALSA**
It is also possible something has gone really wrong with the ALSA drivers or there is a problem with some configuration file that got messed up with all that fooling around from above. You can try purging and reinstalling ALSA. (I recently had to do this after replacing my motherboard, the new on-board sound card was correctly detected but my existing pci sound card was not, weird...) 


(1) Remove the ALSA packages
 	Code:
 	sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils 
(2) Reinstall the same packages
 	Code:
 	sudo apt-get install linux-sound-base alsa-base alsa-utils 
Packages gdm and ubuntu-desktop are also removed in this process if you are using Gnome. They need to be reinstalled:
 	Code:
 	sudo apt-get install gdm ubuntu-desktop 
If you are using xubuntu this will also happen to you
 	Code:
 	sudo apt-get install gdm xubuntu-desktop 




> **markbuntu said:**
> [B] [SOLVED] Multiple Sound Solution (ALSA w Pulseaudio)
The 10,000 Page Guide to Sound Troubleshooting and Configuration for Hardy Heron 8.04 and Intrepid 8.10 and Jaunty 9.04[/B]

You should check back here often, the guide is being updated on a continuous basis.

Pulseaudio is the sound server for Ubuntu Hardy and Intrepid and the new Jaunty. It will continue to be so for the foreseeable future. This guide is geared towards first getting your sound hardware working and then getting Pulseaudio set up properly. If you are using KDE4/Kubuntu Intrepid Phonon is replacing aRts as the sound server. Since Phonon is so new some functionality has not yet been implemented. There is a link below for using Pulseaudio to fill the gaps.

**If you are using Intrepid you must read this before continuing**
The sound scheme in Intrepid 8.10 is fundamentally the same as that in Hardy 8.04 with few exceptions. ALSA 1.0.17 is now installed with Intrepid so more hardware works out of the box. The PulseAudio Volume Control now has a Recording tab. The link for the Multimedia overhaul has been updated for Intrepid and works, use it to get the dvd decoders and other restricted codecs from the medibuntu repository, it will also update some packages you got with the ubuntu-restricted-extras package. Flash 10 is now included in the ubuntu-restricted-extras package for both 32 and 64 bit users. Many of the other links have also been updated for Intrepid. If you know of some other helpful links, please let me know and I will include them here. It has been reported that Skype now works out of the box with Intrepid so if you are having problems it is either with your Skype setup or something more fundamental.

If your sound sort of works I have written a little quick start guide here just for you:

**Quick Start Guide for Intrepid and Hardy**

[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

**KDE4 Phonon and Pulseaudio**
If you are using Intrepid with KDE4/Kubuntu and need Pulseaudio because you have multiple sound hardware devices or for any other reason

[http://ubuntuforums.org/showthread.php?t=1055591](http://ubuntuforums.org/showthread.php?t=1055591)

**Jaunty 9.04**
Jaunty is released with Pulseaudio 0.9.14. There is a Jaunty Sound Solutions guide here

[http://ubuntuforums.org/showthread.php?t=1130384](http://ubuntuforums.org/showthread.php?t=1130384)

**Pulseaudio 0.9.15**
 Pulseaudio 0.9.15 includes new hal detection for digital and other devices which is missing in 0.9.10-0.9.14, better bluetooth and HDMI detection/support and many other new features. It also includes an entirely new pavucontrol which is the Pulseaudio volume control. As soon as I can, I will write a guide for using it. Pulseaudio 0.9.15 also requires ALSA 1.0.19 which is also available through Luke's ppa. There are also packages for Intrepid and Hardy. Remember that these are experimental so it is possible that things will not work smoothly. You will be performing testing and bug reports are needed for any problems you encounter.

Discussion thread for Pulseaudio 0.9.15. (This thread is in Jaunty testing forum and is closed for new posts)

[http://ubuntuforums.org/showthread.php?t=1066212](http://ubuntuforums.org/showthread.php?t=1066212)

Luke Yelavich's PPA for Pulseaudio 0.9.15, also includes debs for ALSA 1.0.19

[https://launchpad.net/~themuso/+archive/ppa]("https://launchpad.net/%7Ethemuso/+archive/ppa")


**The Ubuntu Sound Scheme**
If you are looking for a general explanation of the Ubuntu Hardy Heron 8.04/Intrepid 8.10 sound scheme, I have written a little something here for you:

[http://ubuntuforums.org/showthread.php?p=5931543](http://ubuntuforums.org/showthread.php?p=5931543)

**Introduction**
This guide begins with a short basic troubleshooting section followed by a more comprehensive hardware **Drivers** troubleshooting area that deals with specific solutions for your hardware. You can skip this if your sound basically works. Next is the **ALSA Trouble** section. This tells you how to restart ALSA without rebooting, how to reload ALSA completely, and how to obtain the latest ALSA version.

Following that is a **Other Hardware Issues** section on getting your Surround Sound and Digital output and multiple sound cards/devices USB and bluetooth stuff working. You should get your basic hardware and sound server set up properly first before doing anything here.

The **Sound Server Setup** section  is about setting up the system so all your sound applications will work together properly. it tells you what packages you need and how to use all those crazy sound setting applications scattered all over your menus.

Following that is some info on getting a few specific applications setup and working properly, network streaming, and some other technical details that most people can just skip over.

The last section is about **Ubuntu Studio and Jack**. If you are serious about recording or contemplating using Ubuntu for recording/performing, it is very important that you read this section.

One important piece of advice if you are going to get any use out of this guide, a lot of important information that you need is in the links.

*********************************************************************************************************************************
**Basic Troubleshooting**

**If you can hear anything**
If you can hear the login sound but all other sound is not working you should first try **Try This First** and **This may or may not work for you**. If you have sound in some applications but not others then you can skip all the way down to the **Sound Server Setup** section. Either way it means your sound driver is working, lucky you.

** If your sound stops**
If your sound is generally working Ok but after a while just fades out or stops and you are not doing anything in particular to make this happen, like installing updates or fooling around with the sound settings or the applications and sound returns like normal when you reboot, this seems to be a particular bug in the hda-intel driver or kernel problems with Intrepid so we must wait for it to be fixed and an update made available. You can avoid having to reboot by restarting ALSA and PulseAudio following the directions in **ALSA Trouble** below for now.

**If you sound goes missing after an update**
If you just got a bunch of updates and rebooted and your sound no longer works it is most likely because some or all of your sound setting have been reset from where you put them. If you remember how you had everything set up, reset what was changed. If you do not remember... first check your volume controls. Next, go to **Try This First** below. If you edited some file to get your sound working, check that and reedit as necessary. If you got an application update check its preferences or settings. If you are really lost just go through the guide again. You should also check that your users and root are members of the following groups which you can check in System/Administration/Users and Groups since these sometimes are removed with updates.
pulse
pulse-rt
pulse-access

** Scratchy, glitchy sound**
If you have an HDA-Intel device try turning up the PCM slider in the volume control. If PCM is set to 0 it makes the sound scratchy for some of those devices.

Otherwise if your sound is scratchy or stuttering you can edit these lines in the file /etc/pulse/daemon.conf to look like this
```

default-fragments = 5
default-fragment-size =25

```There are also some sound cards/chips that can only be fixed with an ALSA upgrade so you may want to consider that if this does not work for you.

**If your sound works randomly**
If your sound works sometimes when you boot but not all the time this problem is very common when multiple hadware sound devices are present. Nvidia and ATI include HDMI devices in their gpus now so that means if you have one of them you have multiple sound devices. If you have a USB headset or speakers you have multiple sound devices. If you have a tv card you have multiple sound devices and of course, if you have a plug in sound card and a sound chip on the motherboard you have multiple sound hardware.  What happens is that the devices are on the PCI bus and are detected and assigned somewhat randomly. This means that sometimes your motherboard sound chip is detected first and becomes the default and sometimes the HDMI or your plugin sound card or some other device is detected first and becomes the default sound device. In any case, this is an issue with **Multiple Sound Devices** which is a section of this guide below so you should look in there for help.

**No sound at all**
There are many links here for specific sound cards/chips and the answer you need may not be in the OP so you should look through the entire thread if it seems to be relevant to your problem. You should also post in that thread instead of starting a new one if possible. (Starting a new thread just fragments information and makes it more difficult for people to find answers so please try to avoid that.) Posting in a running thread will push it the the top and more people will notice it and reply. Someone will be along to help you if they can so please be patient. If you get no answer after one day, it is OK to bump the thread.

If you still have no sound after going through this guide and all the relevant links, you should do a search either in these forums or with google for your specific sound card/problem because there is about a %100 chance that someone has figured out your problem already. You can also try looking in the Mandriva and Fedora and SUSE and Debian forums, there are many smart people there. If you still cannot find any help, it is OK to start a new thread. If you find any information somewhere else that you think others might need, please bring it back.

**Missing Volume Controls**
If you seem to be missing some items from the volume control in your panel ( the little speaker icon) you most likely just need to make them visible. Right click on the little speaker and choose Open Volume Control. Make sure the Device: xxxxxxxxxx is your hardware device. It should be something like
Device: HDA ATI SB (Alsa mixer) or Device: HDA Intel(Alsa mixer) or Device:C-Media 8768 (Alsa mixer) etc, in other words, a hardware device with an Alsa mixer.
Once you have the proper device selected click on Preferences down at the lower right. This will show you a list of check boxes. Check  all the items you want to appear in the volume control and close the box.

**Try This First**
Go to System/Preferences/Sound and switch everything except Default Mixer Tracks to ALSA or Pulse Audio. if you see ...HDMI... in Default Mixer Tracks, change it to your sound card/chip, Realtecxxxx or Emuxxx or ATI SB or HDA INTEL or something like that, anything but HDMI that is not Capture or Playback or OSS.

Right click on the speaker icon on the top panel and choose Open Volume Control. Click File/Change Device and make sure you have the correct device chosen. Go to Edit/Preferences and check the following boxes: Main, PCM, CD, PC Speaker, Mic, mic boost, mic capture, mic boost capture, etc. You may or may not have these and more. In the Playback tab make sure the sliders are up and there are no red x over the little speakers. In the Recording tab, do the same. In the Switches tab check any boxes marked mix, 3D control, mic boost, capture, etc. In the Options tab, make sure the Line in mode and Mic-on mode and any other option is like how you have your speakers plugged in. (Some surround sound outputs are also line in and mic inputs and can be switched here.) Make sure any SPDIF or IEC958 or External Amplifier boxes are unchecked. (With some sound cards/chips these will turn off your sound so for now leave them off.) Close that window, right click on the icon again and choose Preferences. Make sure the device listed in the box is your sound card and select Master. Close the window. Now left click on the speaker icon and move the slider all the way up.

Try to play something, Rythmbox is a good choice, so is totem or mplayer. (Firefox/flash is not such a good choice at this time since it may not be working for other reasons). If you still get no sound, read on.

**This may or may not work for you**
One easy way that some people have fixed their sound problems is by creating a new user in System/Administration/Users and Groups and then logging in with that. It seems the generic system defaults for new users are different from the initial user defaults that Ubuntu installs. You should try that first before resorting to some of the more drastic steps below, It is a simple thing to do and will make no changes to your system. And if it works, you will know it is just a user configuration problem and you can compare the hidden user default files in the respective home directories to find and fix the problems or just transfer your personal files to the new user directory.

If you still get no sound, get up and walk around for a minute, get something to drink. This could take a while.

OK, sit back down and start reading.

********************************************************************************************************************
**Drivers**
Drivers are low level software code that connects the hardware to the software operating system so applications can make use of it. The sound drivers live in the kernel which is the heart of the operating system. ALSA sound drivers are included in the installation.  New and updated hardware drivers for sound are generally provided through automatic updates and version upgrades to ALSA. This means that, for the most part, you do not have to worry about hunting down drivers and installing them yourself to get your hardware working. It can also mean that if there is no open source linux driver and your hardware manufacturer does not supply a proprietary one you could just be out of luck with your hardware but that is a pretty rare circumstance.

**Sound Cards/On Board Chips and other Devices**
If you want to find out if your sound card is supported by ALSA and other information you should try the ALSA Wiki ( According to the ALSA developers all usb compliant sound devices should work with no special setup.):

[http://alsa.opensrc.org/index.php/Main_Page](http://alsa.opensrc.org/index.php/Main_Page)

If you are having trouble determining which module or module option you need for your sound card the entire list of supported cards and options is already on your computer ( the driver directory where this file resides also has all sorts of miscellaneous information on specific sound cards/devices):

/user/share/doc/alsa-base/driver/ALSA-Configuration.tar.gz

**Getting Information from your Machine**
Much of the information you will need for further troubleshooting you will need to gather yourself from your machine. This will involve using a few very simple and easy commands from the terminal. Do not be afraid, just follow this guide here. It is written for total noobs.

[http://ubuntuforums.org/showthread.php?p=6628921](http://ubuntuforums.org/showthread.php?p=6628921)

**HDA sound chips**
snd-hda-intel
The Intel Hda sound chip is widely used and can be found on almost every desktop and laptop PC manufactured over the last few years. There are numerous versions of this chip and a zillion configurations that OEMs have made by programming them for their particular needs. This has created a nightmare for the driver writers since the OEMs are very lazy about publishing the details. Nevertheless the driver writers are forging on in the total pitch black using only sputtering candles to light their way and have come up with numerous options you can use to configure this driver for your particular machine. You should send them roses, or candy, or beer, or even just a thank you for taking on this near-impossible task. 

If you are having problems with the HDA card/chip on your laptop or aplay -l reports one of these:

HD Audio (ICH6, ICH6M, ESB2, ICH7, ICH8, ICH9, ICH10 ),
ATI SB, SB450, SB600, RS600,
VIA VT8251/VT8237A,
SIS966, ULI M5461
Many people have reported success with their problematic HDA sound problems by upgrading to ALSA 1.0.17, 1.0.18 or 1.0.19 and/or Intrepid 8.10 which includes ALSA1.0.17. You might want to consider one of these options if you continue to have difficulties after trying the following. If you have an ALC 861 or ALC 888 chip people have reported that ALSA 1.0.17 provides more switches and options than 1.0.16. if you experience very low volumes with your ICH8-10 you should consider upgrading. The drivers are being updated regularly and each release supports more chips/cards and options so if your card/chip or some option is missing from your current driver you should seriously consider upgrading. (Directions for that are in the ALSA Trouble Section below)

First, you should get some information from your machine. The section immediately above has a link to how to do that. Next, open this file with your file manager

/user/share/doc/alsa-base/driver/ALSA-Configuration.tar.gz

Scroll down to the Module snd-hda-intel section and, using the information you just got, look for your sound chip. If you are lucky you will find a listing for your particular machine. If not, at least you know which options are available for that chip. You can also look here which has a list by manufacturer I am trying to get together. If you fix your machine but it is not on any of the lists, please post there so we can add you to the list.

[http://ubuntuforums.org/showthread.php?t=1043568](http://ubuntuforums.org/showthread.php?t=1043568)

Once you find something that looks hopeful you need to get it into the /etc/modprobe.d/alsa-base file. Save it in a notepad. Open a terminal and copy this into it. In Jaunty the file name has been changed to alsa-base.conf to conform to configuration file naming conventions. 

```

sudo gedit /etc/modprobe.d/alsa-base

```It will ask for your password and then open the file for you to edit. Add this to the end of the file
```

options snd-hda-intel xxxxxxxxxxxxx

```Replace the xxxxxxxxx with  whatever option you want to use.
Reboot or restart alsa (directions for that are below in ALSA Trouble). If it works you should now have your sound working, YAY! If it doesn't you may need to try the other options until you find one that does, meh. You can also try this option which seems to work for some machines where the listed options fail.

```

options snd-hda-intel probe_mask=1

```If you are having problems with headphone/speaker control with your HDA sound device you can try this thread:

[http://ubuntuforums.org/showthread.php?t=806620](http://ubuntuforums.org/showthread.php?t=806620)

**ALC1200**
If you have an ALC 1200 sound chip (ASUS P5QL-EM mobo) you need  ALSA 1.0.17 or 1.0.18 or 1.0.19 which there is a link to below.  Upgrade and add the following line to the end of the  /etc/modprobe.d/alsa-base file:
```

options snd-hda-intel probe_mask=1

```**Nvidia HDA** 
If you have a new Nvidia HDA sound chip and it sounds scratchy, this is a known problem and is fixed in the 2.6.27 kernel( It is part of Intrepid so you may want to consider upgrading):

[http://ubuntuforums.org/showthread.php?t=925409](http://ubuntuforums.org/showthread.php?t=925409)

**Creative Soundblaster Cards**
Creative cards have been nothing but a big pain in linux forever. Creative has been completely unwilling to make any technical information about their cards available to driver the open source community so drivers have had to be reverse engineered. Creative has released a few proprietary linux drivers but these have proven to be generally unusable. Just recently, after the latest fiasco with their proprietary X-FI driver, Creative has thrown in the towel and announced that they will make technical information available so the open source community can write proper drivers. OSS4 has drivers for the X_Fi cards now but there is no ALSA driver included in the ALSA packages yet.

**X-FI**
If you are having problems getting your Creative X-FI card to work you can try the newest driver from creative, it seems to actually work for a few people:

[http://ubuntuforums.org/showthread.php?t=870001](http://ubuntuforums.org/showthread.php?t=870001)

Or you can switch to OSS4:

[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

[http://ubuntuforums.org/showthread.php?t=780961](http://ubuntuforums.org/showthread.php?t=780961)

Or you can recompile your kernel with a patch. To recompile your kernel and apply the patch (take extreme care doing this, recompiling a kernel is serious business and can break your system. Do not do this unless you are absolutely sure you know what you are doing):

[http://ubuntuforums.org/showpost.php?p=4823915&postcount=675](http://ubuntuforums.org/showpost.php?p=4823915&postcount=675)

The ALSA x-fi driver has finally been completed and will be released in the 2.6.31 kernel.

**Audigy**
If your Creative Audigy card is not giving you any sound, make sure the analog/digital check box in your sound mixer is unchecked. Updates seem to reset this switch regularly so keep this in mind.
 
** AWE64, SB16**
If you have dug out an old Soundblaster AWE 64 or SB16  ISA card and were wondering if you could get it to work

[http://ubuntuforums.org/showthread.php?t=1011516](http://ubuntuforums.org/showthread.php?t=1011516)

** ICE1712 **
If you have a sound card with the ICE1712 chip, like a M-audio Delta 44, M-Audio 2496, ST Audio Media 7.1 and others and are having trouble getting it working with pulseaudio you can try this:

[http://ubuntuforums.org/showpost.php?p=6449370&postcount=989](http://ubuntuforums.org/showpost.php?p=6449370&postcount=989)

**Cards that need firmware**
The following devices do not come with the software necessary for them to function (firmware) embedded into the device. It must be loaded each time the device is attached or turned on. Newer versions of ALSA should automatically load this firmware upon detecting the device but there are some exceptions...If you seem to have an unsupported device and are dual booting with windows one trick that people use is to boot up with windows and load the firmware and then soft restart the computer and boot into Ubuntu while leaving the device plugged in and powered up.
  
**MobilePre, Sonica. Ozone, Transit. Audiophile USB devices **
Firmware needs to be loaded into these devices before they will work properly. Here are directions for doing that for older devices(newer devices should work without needing to do this):

[http://ubuntuforums.org/showthread.php?t=846621](http://ubuntuforums.org/showthread.php?t=846621)

**Tascam US 122**
If you have a Tascam US122  you also need a firmware loader:

[http://ubuntuforums.org/showpost.php?p=6272809&postcount=3](http://ubuntuforums.org/showpost.php?p=6272809&postcount=3)

**EMU404**
If you have an EMU404 and it does not work chances are that it is an early model. If that is the case you are out of luck because there is no firmware loader for that card or any plans to make one. Later models should work without problems.Cards that will work have a hardware identifier 1102:0008. Cards that do not work have an identifier of 1102:0004. There is an ongoing discussion about this issue here

[http://ubuntuforums.org/showthread.php?t=768934](http://ubuntuforums.org/showthread.php?t=768934)

**Other Sound card and chip Drivers**
Most other sound cards and chips should work without any problems but if you are having problems getting you AC'97 chip or any other card or chip working, the file

/user/share/doc/alsa-base/driver/ALSA-Configuration.tar.gz

also contains many options for those. You can follow the directions in the HDA sound chip section to apply them. Of course, you need to replace snd-hda-intel with the name of the driver you are using. Many AC'97 chips can be made to work with the "quirk" options. 

*******************************************************************************************************************************
** ALSA Trouble**

If you are having problems with ALSA the first thing you should try is to reload the alsa drivers. In a terminal type:

```

killall pulseaudio

sudo alsa force-reload

pulseaudio -D

```This is a temporary fix for many people who have problems with sound fading out or strange messages from ALSA caused by buggy drivers. More permanent fixes can only come from driver updates.

**Reinstalling ALSA**
It is also possible something has gone really wrong with the ALSA drivers or there is a problem with some configuration file that got messed up with all that fooling around from above. You can try purging and reinstalling ALSA.  (I recently had to do this after replacing my motherboard, the new on-board sound card was correctly detected but my existing pci sound card was not, weird...) 


(1) Remove the ALSA packages
```

sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils

```(2) Reinstall the same packages
```

sudo apt-get install linux-sound-base alsa-base alsa-utils

```Packages gdm and ubuntu-desktop are also removed in this process if you are using Gnome. They need to be reinstalled:
```

sudo apt-get install gdm ubuntu-desktop

```If you are using xubuntu this will also happen to you
```

sudo apt-get install gdm xubuntu-desktop

```(3) Reboot.

**Upgrading ALSA**

**ALSA 1.0.19 ** 

If you want or need to upgrade to ALSA 1.0.19 you can get the debs from Luke Yelavich's PPA which has packages for Hardy and Intrepid and Jaunty. The best way to do it is to add the ppa to your sources list and then use apt or Synaptic to install the packages. 

[https://launchpad.net/~themuso/+archive/ppa]("https://launchpad.net/%7Ethemuso/+archive/ppa")


**Still no Sound**
If you still have absolutely no sound at all or the above did not seem to offer anything helpful for you, you can try these guides:

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

[https://wiki.ubuntu.com/DebuggingSoundProblems](https://wiki.ubuntu.com/DebuggingSoundProblems)

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

**************************************************************************************************************
**Other Hardware Issues**
A single sound card/chip providing stereo sound to a pair of speakers is no longer the model for computer sound. Surround Sound, digital output, HDMI, USB , Bluetooth, multiple cards, all are having an impact on the way people want sound to come out of their computers and the linux community has risen to the challenge.  This section is all about getting those things working with your Ubuntu. If your sound drivers are working and your sound server is set up properly these guides should work for you.

**Surround Sound**

Many sound cards/chips have configurable plugs that can be used for things like line-in or rear speaker outputs. You should check in the Volume Control/Options and /Switches that you have these correctly chosen and that your speakers are plugged into the proper plugs. If you are dual booting with windows take care because windows may configure your speakers even though they are in the wrong plugs.

If you are not getting surround sound but have some sound then try this:

[http://www.automaticable.com/2008-05-28/how-to-enable-surround-sound-on-ubuntu-hardy/](http://www.automaticable.com/2008-05-28/how-to-enable-surround-sound-on-ubuntu-hardy/)

If you have 2.1, 4.1. or 6.0 Surround Sound, or a custom configuration, try this guide:

[http://ubuntuforums.org/showthread.php?t=795525](http://ubuntuforums.org/showthread.php?t=795525)

If that doesn't work for you, you can try editing your /.asoundrc file like this:

[http://ubuntuforums.org/showthread.php?t=899139](http://ubuntuforums.org/showthread.php?t=899139)

**Digital Output**
Digital output has two different formats. S/PDIF and IEC958. The easiest way to get your digital output working is to just turn it on in your mixer by checking the box labeled S/PDIF or IEC958. You may have number of these boxes so you need to play around with them to find the ones that work for you. If you have a IEC958 or S/PDIF Capture box and you check that, it may direct your microphone to the digital output which will make it unavailable for recording so be careful with that. Some cards will disable the analog sound when digital is selected so be aware of that. These boxes may not appear in the Volume Control and so may need to be accessed directly in the mixer. I highly recommend the gnome-alsamixer for this (see below). If checking any of these boxes causes your sound to disappear, uncheck them. You also may need to reboot before these changes take place as some hardware configuration files are only read at startup.

Mplayer, has an option for AC3 passthrough. VLC has an option to use S/PDIF when available. These options will redirect the audio stream from these players directly to the digital output. Players without these options will use the digital outputs through the ALSA sound server and driver. Older versions of Mplayer have a bug that does not allow the release of the digital output when Mplayer is closed. This is fixed in later versions. More in depth information about getting digital output working with ALSA is available here:

[http://alsa.opensrc.org/index.php/DigitalOut](http://alsa.opensrc.org/index.php/DigitalOut)

**Digital Output and Pulse Audio**
If you are using Pulse Audio, you may have noticed that your digital outputs are unavailable to Pulse Audio. You can still control them in your alsa mixer and their use should not effect your use of Pulse Audio. If you would like to make them available in Pulse Audio, you can follow this guide:

[http://ubuntuforums.org/showthread.php?t=776958](http://ubuntuforums.org/showthread.php?t=776958)

NOTE: This problem is fixed with PulseAudio 0.9.15 which is just released. There is a PPA at Launchpad for rc1 for Jaunty testers (as of now, Feb11, it will not be included in Jaunty (meh). You also need ALSA 1.0.19. Luke Yelavich has provided the PPA. (It is Jaunty specific so will probably not work with Hardy or Intrepid due to dependency problems). There are links to the discussion thread and the PPA at the beginning of this guide in **Jaunty 9.04**
More on that soon....

**HDMI**
If you are trying to get your HDMI working with your ati card, you need the 8.9 or later driver, if you have an nvidia card, you need the update 177.78 or later. These have been reported to work by some desktop users and some laptop users, but not all so if it still does not work for you, you may have to wait for a later update. Check that the HDMI or SPDIF/IEC958 output is switched on in the ALSA mixer. HDMI may be in a separate section in alsa mixer or gnome-alsamixer if you have a pci card. Also, because these devices are not generally device 0 on the video card, they may have to be added manually to be used with PulseAudio. See the section immediately above for all that and more general digital output help.

** Multiple Sound Devices, Hardware **
Multiple sound devices are becoming more and more common these days. If you have a newer Nvidia or ATI graphics processor that includes HDMI output you have multiple sound device hardware. If you want to be able to control them you should look here. If one of them is HDMI you should also read the HDMI section directly above.

[http://ubuntuforums.org/showthread.php?t=922860](http://ubuntuforums.org/showthread.php?t=922860)

** USB Headsets, speakers, sound cards, etc**
Once you have Pulseaudio set up properly you can easily use your USB Headset/Headphones/Microphone and other USB audio device.
They should appear in the Input and Output Devices of the Pulse Audio Volume Control as something like:

ALSA PCM on front 2: (USB Audio) via DMA

You can right click on them to make them the default device, adjust the volume by moving the slider and mute them by clicking on the little speaker icon.  You can also move streams to or from them in Playback by right clicking on the stream and choosing move stream. You can make your usb device mic the default device by right clicking on it in the PA Volume Control Input Device section.

If the volume control for your usb headset is not working properly in the panel volume control or in your alsamixer (gnome-alsamixer included), more specifically when you move the slider the left one always goes to zero, this is a known bug and is being worked on. Meanwhile, you can use the slider in the PulseAudio volume control as it is not effected by this bug.

You can also use your usb device simultaneously with your sound card and other audio devices with the PA Device Chooser/Configure Local Sound Server/Simultaneous Output and check the "Add virtual output device for simultaneous output on all local sound cards" box. This will add a virtual simultaneous output device in Output Devices and you can select it in Playback, adjust the volume etc like any other device.

[b] Bluetooth[/b
The bluetooth problems with pulseaudio have finally been solved. While none of the required parts necessary to make this work are part of any current Ubuntu distribution *this is still good news.

*Requirements

*bluez 4.35 or later
*pulseaudio 0.9.15
*alsa 1.0.19
*Kernel 2.6.29
*gnome bluetooth 2.27.4

*Make sure module-bluetooth-discover is loaded in /etc/pulse/default.pa or the default.pa in your home directory if you are using one

If you are trying to use bluetooth with Hardy or Intrepid or Jaunty it is still somewhat of a work in progress. 

[https://help.ubuntu.com/community/BluetoothHeadset](https://help.ubuntu.com/community/BluetoothHeadset)

[http://wiki.bluez.org/wiki/HOWTO/AudioDevices](http://wiki.bluez.org/wiki/HOWTO/AudioDevices)

[http://forums.overclockers.com.au/showthread.php?t=694010](http://forums.overclockers.com.au/showthread.php?t=694010)


***********************************************************************************************

** Sound Server Setup**
The sound server is a critical part of the Ubuntu sound system. It is the interface between your sound using applications and the drivers for your sound card/chip. In Hardy 8.04 and Intrepid 8.10 and Jaunty 9.04 Pulseaudio is the default sound server. Unfortunately, Pulseaudio is not set up properly by default. This has caused untold amounts of trouble and heartache for many many Ubuntu users myself included. While this section appears to be very long and involved it is not really. A lot of it is just explanation about what you need, how things work, and how to use stuff, all in one place. You will have a much better understanding about how your sound works by reading it.

If you have already followed the Interpid Sound Solutions guide it is just a compressed version of this section so a lot of this will seem redundant.

Anyway, this section will help you to get your sound scheme set up properly for maximum usability.

** Multimedia**
If you are not able to play your mp3s or other formats, you can use the Synaptic package manager to get:

ubuntu-restricted-extras

This will get you the codecs for many formats and a bunch of other useful stuff like java and flash.

If you need a total multimedia overhaul follow this guide ( I alway do this immediately after any install):

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

Because some codecs are proprietary and not available through a general use license or their use or distribution is not allowed in all countries they are excluded from the regular Ubuntu repositories. But, you can get them from the medibuntu repositories so If you just want the plugins and w32codecs and libdvdcss2 to play restricted dvds and other proprietary formats follow this guide.

[http://ubuntutip.googlepages.com/multimediaubuntustep1](http://ubuntutip.googlepages.com/multimediaubuntustep1)
[http://ubuntutip.googlepages.com/multimediaubuntustep2](http://ubuntutip.googlepages.com/multimediaubuntustep2)

**Flash and java**
If you have flash9, you need to have
libflashsupport
to get your audio to work properly. If you have flash10 or higher, you do not need libflashsupport and should remove it. You should not need to do anthing like this if you are using Intrepid and got flash with the ubuntu-restricted-extras package. If you got flash from somewhere else you are on your own. If you are having problems with flash you can try installing libflashsupport anyway, it may help, it may make thing worse.

If you are using amd64 Hardy be sure to read the sticky guides at the top of the 64bit forum to get 32bit flash and java working. The ubuntu-restricted-extras package should set you up properly but if you are having problems with missing 32 bit libs or crashing etc.

[http://ubuntuforums.org/showthread.php?t=772490](http://ubuntuforums.org/showthread.php?t=772490)

[http://ubuntuforums.org/showthread.php?t=774956](http://ubuntuforums.org/showthread.php?t=774956)

**Multiple Application Sound Sharing**
It is assumed you are using Hardy Heron 8.04 amd64, i386, or Hardy UbuntuStudio8.04 i386 and amd64 or Intrepid. If you are testing Jaunty, it is somewhat different and subject to change so bear that in mind while you follow this guide. 

It is very unlikely that anything you try here will put your sound into an unusable state that cannot be easily remedied by you after you read this.

This has been tested on i386 and amd64 Hardy8.04, UbuntuStudio8.04.1 i386 and amd64, Intrepid i386 and amd64 Gnome2.2.1 and KDE4 and Intrepid UbuntuStudio. Jaunty testing is underway.I have an HDA ALC883 sound chip, a C-Media 8768 7.1 PCI sound card, a Plantronics USB Headset and a Logitec webcam and they all work all the time. I have 21 devices in my volume control. I just got a bluetooth dongle and headset and as soon as I figure them out I will provide an update in the bluetooth section. Things I have used and tested: amarok, audacious, rythmbox, xmms, ardour, hydrogen, rosegarden, vlc, mplayer, totem, miro, streamtuner, tunapie, firefox, opera, ZynAddSubFx,  Banshee, jackrack, soundrecorder, sound converter, timidity, beast, djplay, Qsynth, mixx, muse,.....and many many more.

**Restore Default Configurations**
Default sound configurations are of two types, system wide configurations and user configurations. . System wide configuration files are /etc/asoundrc and in /etc/pulse. The file etc/asoundrc is not normally necessary or included so it is OK if it is not there. It is used for setting up special configurations for system wide use. User configurations are hidden in the users home directory under ~ /.asoundrc and ~/.pulseThe files ~/.asound.rc and ~/.pulse/default.pa  are used for the same thing but per user. In general you will have a ~/.asoundrc file but no ~/.pulse directory since there is generally no need for per user settings for pulseaudio.

If you edited asoundrc to get your surround sound working and were successful, leave that part. If you changed the sample size and/or rate to eliminate stuttering in /etc/pulse/daemon.conf and it worked, you can leave those changes. If you have edited your pulse/default.pa for multiple sound card devices or used combine and it works, you can leave those parts alone too. Otherwise, if you have an etc/asoundrc file, rename it to asoundrc.back so it won't be used. If you have edited your ~/.asound.rc for any reason but those mentioned above, then you should reload the backup you saved. If you edited your etc/pulse/default.pa for equalizer support you should re-edit and comment those lines out for now, same thing if you have a ~./pulse/default.pa. You can try the other changes you made again once everything is working properly.

Keep the new libs and anything else you installed following this guide from psyke83 if you have already been there:
[http://ubuntuforums.org/showthread.php?p=4928900](http://ubuntuforums.org/showthread.php?p=4928900)

**Packages**
Check with Synaptic that these are all installed(You probably already have most of them. Some are specific to specific applications/servers, if you do not use these, they are not necessary. If you are not sure, get them anyway):

AlSA Packages (search alsa)

aconnectgui  (ALSA MIDI connection utility)
alsa-oss  (alsa wrapper for OSS apps)
alsaplayer-alsa  (PCM player for alsa)
alsa-utils  (command line utilities)
asoundconf-gtk  (choose default alsa sound card)
gnome-alsamixer (GUI alsa mixer for Gnome)
gstreamer0.10-alsa (gstreamer plugin)
xmms2-plugin-alsa (xmms2 plugin)
libasound2 (alsa libs and plugins)
libasound2-plugins (jack, OSS, pulseaudio plugins for libasound2)
libesd-alsa0 Enlightened Sound Demon (allows  multiple audio streams on one device, not really necessary)

PulseAudio Packages (search pulseaudio will find most of them)

audacious-plugins-extra (audacious plugin)
gstreamer0.10-pulseaudio (gstreamer plugin)
libao-pulse (libao plugin)
libpulse0 (client libraries)
libpulse-browse0 (client libraries)
libpulsecore5 (core services modules)
libpulse-mainloop-glib0 (client libraries)
padevchooser ( device chooser for setting up networking)
paman (PulseAudio Device Manager)
paprefs (Pulse Audio Preferences)
pavucontrol (Pulse Audio Volume Control)
pavumeter(Pulse Audio VU Meters)
pulseaudio( The Pulse Audio Daemon)
pulseaudio-esound-compat( Pulse Audio Esound drop in replacement for libesd for multiple audio streams)
pulseaudio-module-gconf (gconf module)
pulseaudio-module-hal (hal module, discover new sound devices via hal)
pulseadio-module-x11 (replace x11 bell/beep with PA sounds)
pulseaudio-module-zeroconf (Avahi, mdns, network help)
pulseaudio-utils (command line tools)
vlc-plugin-pulse (vlc plugin)
libsdl1.2debian-pulseaudio (plugin for sdl apps)

Many of the above user applications can be found in Applications/Sound and Video after they are installed, others are in System/Preferences. Others are command line programs that need to be run in a terminal or libs that you do not need to access or plugins available in or to applications. 

**Default Sound Card**
What we are doing here is routing the ALSA plugins and players through Pulse Audio so it can manage them. Some applications have an ALSA plugin but no Pulse Audio support so they go through ALSA to Pulse Audio and on to the ALSA low level sound device drivers. Contrary to popular belief this does not increase latency since pulseaudio adds zero latency but actually reduces it since applications sharing sound no longer need to go through dmix.

System/Preferences/Default Sound Card, ( this is asoundconf-gtk) choose Pulse Audio.

System/Preferences/Multimedia Systems Selector/Audio set Plugin to Pulse Audio.

System/Preferences/Sound, set all to Pulse Audio except Default mixer tracks which should be set to "your sound card" (i.e. ATI IXP (ALSA )mixer) probably the first choice 0. If you have more than one hardware device, choose the one you want to use/control. If you set your defaults to automatic some applications will bypass Pulse Audio and grab exclusive control of the sound card. We want to avoid this.

Reboot. If you are having trouble changing settings in Multimedia Systems Selector or Sound, reboot and then make the changes and reboot again. You need to reboot because some configuration files are only read at boot.

** Volume Control**
The Volume control is the little speaker on your top panel. If you left click on it you can adjust the volume. This can get a little tricky if you have more than one device. To choose the device to control right click on it and choose Preferences. This will open a little window where you can choose which device to control. You can also choose what sliders you want to control. You should select Master but you can play around with it to see what it can do.If you hold down the sift key you can select more than one control. If you want to control the volume with your multimedia keys you need to select the device in System/Preferences/Sound.

For now though, right click on the Volume Control on the Panel and choose Open Volume Control/File/Change Device and make sure it is set to the same device as in System/Preferences/Sound. Go to Recording if that section is available and put the capture slider up about 1/3 to 1/2 and make sure the icons on the bottom are not x-ed out. If available, go to to Switches and check mix. If you have an Options section, check to make sure they are set to the proper configuration for where your speakers and mic are attached. If you get feedback, mute the microphone, it is working just fine. If you do not have these sections, do not worry, they are not available for all devices. If you only have one hardware device to choose, that is also OK.

** Sound Mixer**
Open any alsa mixer, I use gnome-alsamixer. Turn stuff on and put up the sliders. check mix, capture, cd, mic, etc, unmute, mute, blah blah blah... If you have a usb mic or headphones tab over to that section and turn them on and set the levels etc. Some of this is redundant but it doesn't hurt and gets you familiar with your mixer.  This is the same controls as the volume control in your panel. If you adjust the sliders and switches they will adjust in every other volume control. 

**Pulse Audio Device Chooser padevchooser**
The Pulse Audio Device Chooser is a small applet that lives on your panel. From it you can open all the Pulse Audio interfaces, the Pulse Audio Manager and Pulse Audio Volume Control, the Pulse Audio Meters, and also Configure Local Sound Server and PulseAudio Preferences. You can put this in your panel by opening it from the Applications/Sound and Video menu and then clicking on Preferences/Start applet on session login. You can tell it to start up automatically when you login by choosing Preferences and selecting Start Applet on session login.

**Pulse Audio Volume Control, pavucontrol**
This is the control center for Pulse Audio. It has tabs as follows. You can find it in Applications/Sound and Video or open it from the Pulse Audio Device Chooser.
**Playback**
You can adjust the volume of the individual streams by moving the sliders, You can change which output device they use by right clicking on the stream and choosing move stream, 
**Output Devices**
You can set the default output device in the Output Device section by right clicking on it. This section also lists any Virtual Output Devices you have if you set Show: ALL Output Devices, like one for Simultaneous Output and one for RTP Multicast for network streaming or one for jack. You can select these in Playback just like any of your hardware devices.
**Input Device**
You can set the default input device in the Input Device Section by right clicking on it. You can set the Default Input Device to a monitor of one of the Output Devices so you can record what you are playing. You can set Show to All Input Devices of Show: Monitors to see the monitors.
**Recording**
This is new in Intrepid. It operates the same as Playback but for recording.

If you do not see an application playing in the Pulse Audio Volume Control then it is using the sound device directly. and is most likely an OSS or Jack or other type application. If you can, change their audio output to alsa or pulseaudio. OSS applications may need to be launched with aoss which is the alsa wrapper for oss . You can also try launching them with padsp which is the pulseaudio wrapper for OSS. Edit the launchers as necessary by putting either aoss or padsp before the application name. If it is a jack application, see the jack section below. If the application uses Portaudio or some other sound server then you may need to use the pasuspender command.

**Pulse Audio Manager, paman**
Go to Applications/Sound and Video/Pulse Audio Manager or use the padevchooser and you should see in Server Information:

Default Sink: alsa_output.pci_1002_4370_sound_card_0_alsa_playback_0
Defalt Source: alsa_input.pci_1002_4370_sound_card_0_alsa_capture_0

or something like that or completely not like that but with alsa as the first word.

All of your applications are listed in the Devices section of Pulse Audio Device Manager as #1, #2, #18 etc, under the line for what sink it is using. You can highlight one of them and click on properties to see what client/plugin it is using and other useful information. 

The PulseAudio Manager is being deprecated and will not appear in future versions of PulseAudio. It is not recommended to use the PA Manager for controlling PulseAudio. The padevchoser is also being deprecated so the Configure Local Sound Server will be found in PulseAudio Preferences along with the rtp network controls.

**Testing**
Test with Rythmbox, vlc, totem, firefox flash, firefox mplayer, and other plugins, etc. configure preferences to ALSA or Pulseaudio if available/possible. Play a cd or dvd or both. Run them all at once, or as many as you want/can. You should hear them all, together and see them in Pulseaudio Volume Control/Playback.

**Testing, Recording**
To control your input for recording you can set your System/Preferences/Sound/Audio Conferencing/Sound capture to PulseAudio Sound Server and use PulseAudio Volume Control/Input Devices to choose which device to record from. This is very handy as you can quickly switch between  your sound card pcm stream or microphone to your webcam mic or usb headset. All you need to do is open the PulseAudio Volume Control/Input Devices and right click on any available device to make it the default then open the application. You can choose any (ALSA) hardware device available or one of the "monitor" virtual devices. So, if you are listening to some music in your speakers you can choose the monitor for your Output Device to record. Just make sure that "capture" is enabled and turned up in the panel volume control or your alsa based mixer if you are trying to use a hardware input device.

If you are using Intrepid you can move the recording application to another Input device in the recording tab of the Pulseaudio Volume Control and adjust the levels, mute etc.

**PulseAudio Volume Meters**
You should now have a PulseAudio Volume Meter (capture) you can use to test your microphone or other capture inputs available in your sound mixer or volume control. Once you have chosen your default device, you can open sound recorder and record it. If you choose a monitor device, you can record whatever is going through the comparable Output Device.
You can use the PulseAudio Volume Meter (Playback) for monitoring playback streams. The volume meters work on the default streams.

If you are using a microphone for recording and wish to not hear the microphone input to prevent feedback, you can just mute the microphone playback in the panel volume control or ALSA sound mixer. It is the Capture settings that are the only important ones for recording.

If you are using jack this will not work for you. As far as I can tell you can only change jack inputs in jack control setup/input device and then restart jack. For using jack with PulseAudio, see the Ubuntu Studio and jack section below.

**Starting and Stopping Pulse Audio**
To start Pulseaudio from a terminal. 
```

pulseaudio -D

```The -D option starts pulseaudio as a daemon so it is OK to close the terminal after using it to start Pulseaudio. 
If you want to kill the pulseaudio daemon:
```

killall pulseaudio

```**Troubleshooting Pulseaudio**
If you are having weird problems using pulseaudio then you can kill pulseaudio and restart it from a terminal with
```

pulseaudio -vvv

```This will run pulseaudio in the terminal in verbose mode so all the messages about what pulseaudio is doing will be written to the terminal. When you close the terminal Pulseaudio will exit. These messages can pinpoint problems with ALSA drivers or application plugins or network streaming issues etc along with problems with pulseaudio itself.
Bugs in pulseaudio can be reported by opening  new ticket. Make sure you search the tickets before filing a new bug. You can also talk to the devs at the mailing list or with IRC which have links from the home page:

[http://www.pulseaudio.org/](http://www.pulseaudio.org/)

**************************************************************************************************************************
**Application Specific Solutions and other misc info**
There are some applications that need specific configurations to work properly with Pulseaudio. In most cases these can be found in the Preferences or Settings menus. If available choose Pulseaudio or ALSA plugins. Applications using gstreamer will use the gstreamer defaults you set in Multimedia Systems Selector. You can set the xine defaults in the xine application.

For vlc set ALSA to default, for mplayer set audio to ALSA, for Audacious you can choose Pulseaudio Output Plugin. For Miro set the Preferences/Playback to gstreamer. Some people have have success choosing xine so you can try that too. In wine, try the OSS setting for audio and launch wine with padsp wine.

**Audacity, Wine, Skype and other troublesome applications**
There are some applications that have trouble working with Pulseaudio. This is usually caused by the developers who write the ALSA plugins  for these applications making assumptions about hardware or seeking to take control of it. Since the ALSA sound drivers have moved to the kernel this is no longer allowed due to security issues. Pulseaudio strictly enforces these rules. So, if you are having problems getting your application to work do not blame Pulseaudio.

Nonetheless, there is information about running specific applications including Audacity, Wine and others with Pulse Audio here and more info below:

[http://pulseaudio.org/wiki/PerfectSetup](http://pulseaudio.org/wiki/PerfectSetup)

**SKYPE and Pulse Audio **
Since so many people are having such a hard time getting their skype to work, I finally installed it and true, it does not work out of the box but the solution is fairly simple for Hardy and has been posted to here:

[http://ubuntuforums.org/showthread.php?t=937323](http://ubuntuforums.org/showthread.php?t=937323)

It has been reported by that Skype works out of the box with Intrepid but many also report problems ,mostly with getting their mic to work. If your mic is not working in skype, try to get it working in any other application first.

**A special note on Audacity**
Audacity was originally written for the Portaudio sound server which is not used in Ubuntu and many other major distributions anymore. The audacity developers have implemented plugins for alsa and oss and jack. While these plugins work in general with a standalone alsa or jack situation, they have bugs due to their non-standard implementation that causes them to not work in all circumstances or share the sound device properly with other applications in alsa, oss or jack and Audacity will not work at all with pulseaudio which enforces strict standard alsa protocols. We can only hope that they are working on these issues.

You can try compiling  Audacity yourself from source with jack support. This will allow you to use other jack applications and the jackrack effects etc with Audacity but will not give you full jack connection integration.

[http://ubuntuforums.org/showthread.php?t=982577](http://ubuntuforums.org/showthread.php?t=982577)

It has been reported that audacity now launches correctly with padsp audacity in Intrepid. There is a post around here about that,

[http://ubuntuforums.org/showthread.php?t=1005196](http://ubuntuforums.org/showthread.php?t=1005196)

If Audacity is giving you too many problems you should consider using ardour. It is a professional quality digital audio workstation fully integrated with jack ( it is written by the same people). For more information see ** Ubuntu Studio and Jack ** below

**Second Life**
I do not use Second Life myself so these links are getting a little old. If you are a Second Life user please let me know if this information is still valid or if it needs to be updated, otherwise this section will be deleted.

[http://vboards.stratics.com/showthread.php?p=836114](http://vboards.stratics.com/showthread.php?p=836114)

[http://jira.secondlife.com/browse/VWR-5708](http://jira.secondlife.com/browse/VWR-5708)

**xmms**
If you miss your xmms (not xmms2) and would like to have it back:
i386:

[https://launchpad.net/ubuntu/hardy/i386/xmms/1:1.2.10+20070601-1build2](https://launchpad.net/ubuntu/hardy/i386/xmms/1:1.2.10+20070601-1build2)

amd64:

[https://launchpad.net/ubuntu/hardy/amd64/xmms/1:1.2.10+20070601-1build2](https://launchpad.net/ubuntu/hardy/amd64/xmms/1:1.2.10+20070601-1build2) 

Beware of dependency problems with libglib1.2 and libglib1.2dbl on the amd64 build, i386 is no problem. You can read about that here:

[http://ubuntuforums.org/showthread.php?t=774461](http://ubuntuforums.org/showthread.php?t=774461)

Change the output plugin to alsa and you should be good to go.
These debs are also reported to work with Intrepid, give them a try.

** Streaming Audio Over a Network with PulseAudio**
If you are wanting to use PulseAudio to stream audio over your local or home network, it is very easy, you can use this guide here (this will not work for macs and windows boxes are difficult to setup this way):

[http://x4.6times7.org/dokuwiki/doku.php/devlog/blog/streaming_on_ubuntu_8.04_with_pulseaudio](http://x4.6times7.org/dokuwiki/doku.php/devlog/blog/streaming_on_ubuntu_8.04_with_pulseaudio)

**Streaming Audio to the Internet**

If you want to do local network music streaming to non-linux boxes or to the internet you can start here

[http://www.yolinux.com/TUTORIALS/LinuxTutorialAudioStreaming.html](http://www.yolinux.com/TUTORIALS/LinuxTutorialAudioStreaming.html)

For more technical information about Pulseaudio and about setting up surround sound and for network streaming, etc go here:

[http://pulseaudio.org/wiki/FAQ](http://pulseaudio.org/wiki/FAQ)

**Setting up a automatic PulseAudio server on startup**
If you have a media server and would like to set it up as a Pulseaudio server on startup then 13iggs has figured it out for you here. This is very handy if you have a headless server. 

[http://ubuntuforums.org/showpost.php?p=6869726&postcount=5](http://ubuntuforums.org/showpost.php?p=6869726&postcount=5)

Just be aware that setting up Pulseaudio as a system wide daemon is not especially recommended by the PulseAudio developers due to security concerns so take precautions like using the auth-ip... if you are running this on an open network.

**Pulse Audio Modules**
Pulse Audio loads its modules in etc/default.pa. You can edit this file to control which modules are loaded when Pulse Audio starts up. 

You can also load modules dynamically (while it is running) into the Pulse Audio daemon with the pactl command.
 
If your sound setup is being changed back to the wrong default settings every time you reboot, you can try this:

Look In etc/pulse/default.pa for the line:
```

load-module module-default-device-restore

```comment this line out (put a # at the start of the line). Save the file. You will have to be sudo to do this. If you have a ~/.pulse/default.pa you can do it there for yourself as an individual user instead without being sudo.

You can find more info about the Pulse Audio modules here:

[http://pulseaudio.org/wiki/Modules](http://pulseaudio.org/wiki/Modules)

And about pactl here:

[http://linux.die.net/man/1/pactl](http://linux.die.net/man/1/pactl)


***************************************************************************************************

**Ubuntu Studio and Jack**
UbuntuStudio has three basic parts, audio, video, and graphics. This is about UbuntuStudio-audio exclusively.


Ubuntu Studio comes with the Jack Audio Connection Kit which is designed for one thing only, quality tools for professionals in the music business. This is a powerful utility that sits on top of the hardware drivers and provides connection and control services and real time priority for jack aware applications whose demands are time critical like for live recording and performance. With it you can synchronize playback and recording across multiple jack aware applications. One common use is to sync ardour with rosegarden and hydrogen for easy playback/recording of multiple midi and audio sources at the same time on multiple tracks. Jack and jack applications are used in many environments, from garages and basements to high end studios that charge $100s per hour, from internet DJs wth tiny audiences to live performance with audiences in the thousands. Jack performs, jack delivers.

If you are using jackd and are not using UbuntuStudio you should at least install: 
ubuntustudio-audio-plugins 
jackd (the jack daemon)
qjackctl (Jack Control)
jackeq (Jack EQ)
jack-rack(effects rack)
jack-tools(command line tools)
patchage (patchbay)
linuxrt (real time kernel)

**Getting UbuntuStudio**
If you want a real recording setup just get the ubuntustudio-audio and ubuntustudio-audio-plugins metapackages available in the repositories, ubuntustudio-audio includes jack and the rt kernel and all kinds of audio production applications. (It is a big download, took about an hour on my dsl connection.)

** Warning** Ubuntu Studio for Intrepid 8.10 has some serious problems with the rt kernel, among them are no support for multiple core cpus. It is strongly recommended that Ubuntu Studio users stay with or install 8.04 Hardy until these issues are resolved though many users have reported no problems with using Intrepid for sound mixing and editing.

If you are installing the rt kernel and are using the ati or nvidia restricted drivers that you downloaded directly from ati or nvidia, it is highly recommended that you remove these drivers from your system and replace your etc/X11/xorg.conf with the original generic version.  If you are not sure which file that is, copy the xorg.conf.failsafe file into xorg.conf. You can reinstall the driver after the rt kernel is working and should have no problems with it in Hardy or Intrepid. NOTE: The ati 9.1 driver build for Hardy is missing a patch for the rt kernel and so should be avoided by rt kernel users for now. There are scattered reports of similar issues with some nvidia drivers with certain nvidia cards. You can try these drivers, just be prepared to remove them and reinstall previous ones that worked.

If you are having basic jack setup problems, or you just want to know where to start:

[http://en.wikipedia.org/wiki/JACK_Audio_Connection_Kit](http://en.wikipedia.org/wiki/JACK_Audio_Connection_Kit)

If you are having trouble setting up jack in UbuntuStudio:

[http://en.wikipedia.org/wiki/JACK_Audio_Connection_Kit](http://en.wikipedia.org/wiki/JACK_Audio_Connection_Kit)

[https://help.ubuntu.com/community/UbuntuStudio/GettingStarted](https://help.ubuntu.com/community/UbuntuStudio/GettingStarted)

[http://hubpages.com/hub/Recording-in-Linux-aka-Free-and-Open-Source-Digital-Audio-Workstation](http://hubpages.com/hub/Recording-in-Linux-aka-Free-and-Open-Source-Digital-Audio-Workstation)

Excellent ardour tutorial here:

[http://out-of-order.nfshost.com/tutorials/ardour/](http://out-of-order.nfshost.com/tutorials/ardour/)

If you are wondering how to sync applications together through jack:

[https://help.ubuntu.com/community/HowToQjackCtlConnections](https://help.ubuntu.com/community/HowToQjackCtlConnections)

[http://www.ubustu.com/globe/2007/09/19/how-to-sync-hydrogen-with-ardour/](http://www.ubustu.com/globe/2007/09/19/how-to-sync-hydrogen-with-ardour/)

[http://www.rosegardenmusic.com/](http://www.rosegardenmusic.com/)

**Unlocking memory and setting priority for audio applications**
UbuntuStudio in Intrepid and Jaunty now comes with an UnbuntuStudio settings manager to control these options but if you are using previous versions... 
and you are getting memory limit or memory lock messages when running any audio application, try this:
Edit /etc/security/limits.conf and add or modify these lines

```

@audio - memlock unlimited
@audio - nice -10
@audio - rtprio 99

```
    * The 'memlock' line determines the amount of memory available to users in the group "audio". 
    * The 'nice' line, has to do with how long the processor will wait for processes queued from group "audio".
    * The 'rtprio' line assigns an extremely high priority to the group "audio".

The nice and rtprio settings will basically give your audio top priority at the cpu which is a necessity for live work.

** jack and Pulse Audio with more than one sound card**
If you have more than one sound card, you can configure jack to use one of them exclusively with Jack Control and set Pulse Audio to use the other one In the Pulse Audio Volume Control. They should both work at the same time if they are using different hardware devices and when you close jack, Pulse Audio can use that card again. Make sure you do not have any application using the Pulse Audio sink for the sound card you configured jack to use or jack will not start. 

Unless you are using professional quality sound cards that are made to share clocks, using two sound cards together can be problematic as their clocks/timing will drift apart. Pulse Audio, through the module combine can hold two cards in sync fairly well but some deviation is inevitable and glitches will occur as the clocks are periodically resynchronized. This is not a big problem with playback only but is not recommended for recording or live performance unless you have actually tested this with your hardware and are satisfied with it. I have not yet figured out how to get this to work with jack but it seems promising. If you have figured this out, please make a post.

** Pulse Audio through jack**
If you want to set up Pulse Audio to play through jack you can do so. This has been tested on Hardy 386, amd64 generic and Ubuntu Studio and on Intrepid 386, amd64 and Intrepid Studio ( it is from debian of course which is the base of Ubuntu).

First of all, you need to install the pulseaudio-module-jack from the debian lenny repository:

[http://packages.debian.org/lenny/sound/pulseaudio-module-jack](http://packages.debian.org/lenny/sound/pulseaudio-module-jack)

If you are using Jaunty 9.04 and you are using pulseaudio0.9.14, the pulseaudio-module-jack in Debian unstable has been removed so you will need to build it from source. It would be better if you upgraded to pulseaudio 0,9,15 which is much improved from Pulseaudio0.9.14 (which the pulse devs actually did not recommend for distribution use). There is a link at the beginning of this post to Luke Yelavich,s PPA for Pulseaudio 0.9.15 which also includes ALSA1.0.19 which you will need.

The pulseaudio-module-jack is no longer included in luke Yelavich's PPA for pulseaudio 0.9.15 so you need to get it from Debian sid

[http://packages.debian.org/sid/pulseaudio-module-jack](http://packages.debian.org/sid/pulseaudio-module-jack)

Download the appropriate deb by clicking on one of the mirror sites and install it with the gdebi package manager ( 386 and amd64 versions work for both Hardy and Intrepid).

Then you need to make a little script. I keep mine in a /scripts directory in my /home directory. Just make a new file with Natilus called jack_startup and make it executable and put these lines in it.

```

#load pulseaudio jack modules
#!/bin/bash

pactl load-module module-jack-sink
pactl load-module module-jack-source

```Then start up jack control and go to Setup/Options/Execute script after Startup. click on the... box and go to where the script is and click open. and then after you make sure the path is correct click the box on the left so it has an x in it. Click OK at the bottom and make sure no application is using the sound card before you start jack or jack will not start. 

If the jack sink disappears from the Pulse Audio Volume Control after a few seconds or you do not see it, adjust the timeout in the jack control setup menu to 1000-5000. Applications that just play back audio streams through Pulse Audio are very lazy about talking to their sound server and this will prevent jack from timing out the connection. (Read the pactl and modules links above to change the default options which should work for most people. It has been reported that the m-audio 1010 card needs the channels=2 option)

You should now have jack sinks and sources in the Pulse Audio Volume Control and in the Volume Control on the panel. And a Pulse Audio JACK Sink and Pulse Audio JACK Source in the jack connection bay in the Audio section all connected up to system playback and system source automatically. When you close jack, the jack sinks and sources will automatically go away.
 
You can now start up any non-jack application and it will play through the pulseaudio-jack sink if you select it with move stream in the Pulse Audio Volume Control. And all your jack applications should work too, at the same time. You can connect the pulse audio sink to any jack application in the jack connections bay and record, add effects, eq, pretty much anything you want that jack can hook you up with. 

You can also route the mic/line inputs from the sound card by setting the jack control/setup/Input Device to the hardware device ie hw:0 or hw:1, etc. They will show up in the connections box as system capture inputs. You should hear them through the speakers. If you do not want to hear your mic in the speakers you can mute the mic input in the playback tab of your volume control and leave the captures on so you will still be able to record. If you have a usb mic, you can make that the default in the PA Volume Control and it will show up in jack/connections/audio/system capture and you will not hear it through the speakers unless you hook it to an output.

If you change the input, you will have to shut down jack, close jack control and restart. You will also have to make sure the input you are trying to use is properly enabled and turned up in whatever alsa-mixer you are using.

Now that you have pulse-jack working you can try these quick and easy fun projects to learn about using the pulse audio sinks and sources with jack:

[http://ubuntuforums.org/showthread.php?t=986966](http://ubuntuforums.org/showthread.php?t=986966)

**Closing jack**
If you close jack before you stop or close any application playing through the Pulse Audio jack sink, Pulse Audio may crash and need to be restarted if you do not disconnect the pulseaudio sink and source before closing jack. You can go to connections and choose disconnect all before stopping jack and your applications should not crash when you stop jack. 

**Jack and Pulse on one sound device**
If you have only one sound device your pulse applications may be orphaned when you close jack and their connection to pulseaudio may fail. You can try adding a null-sink and module-rescue-streams should move them to that when the jack sink closes and then they can be moved again when pulse regains control of the sound card. However, this does not seem to be a surefire thing and may not work for you so you may need to restart your pulseaudio applications after closing jack and after pulseaudio regains the sound device sink. There is a pulse audio module, module-always-sink, that would alleviate this problem but this module does not seem to be available in the Hardy and Intrepid pulse audio 0.9.10 but should be available in Jaunty which is using 0.9.14.

********************************************************************************************

If this guide doesn't work for you, or you would like me to add/subtract/edit it, post a reply. Also, please post if this works as is or if you had to change anything. 

Good Luck and best regards,
mark

Thanks: netlerb, leepsejee, motin, Donny K., psyke83, pulseaudio alsa and linux developers everywhere, jack wiki writers,  LordRaiden, ubuntu-freak, Jimmy Hopkins, and everyone else who ever helped anyone with a sound problem here on these forums.

EDIT: 02/21/09 Major rewrite
EDIT 04/23/09 jaunty, pulse0.9.15, bluetooth updates

---

### Post by ranch hand on 2009-08-21
Actually that does work.

It is a good idea to keep track of the packages removed.

You may want them back.

---

### Post by v1nsai on 2009-08-23
lol did you really feel the need to repost the entire thread?

Anyway, I was led here after installing kubuntu-desktop on my ubuntu 9.04 install.  Sound hasn't worked in either desktop manager since.  I followed the instructions [here]("http://ubuntuforums.org/showthread.php?t=1130384") for setting up pulseaudio.  Pulseaudio is getting the streams, because when I click on the pulseaudio device chooser and go to volume control, I can see the rhythmbox stream being picked up, and the bar is moving below the volume control for it, but I still hear nothing.

I have to ask, if the phonon sound server is so new and unstable, why was it implemented so early?  It broke my sound when it was working perfectly fine before...

Oh well, who can complain about free software?


EDIT:
Just needed a restart, everything works now except the volume buttons on my keyboard, they're still controlling the alsa mixer, which still obediently goes up and down when I tell it to, but has no effect.  How can I switch the keys over to the pulseaudio server?  In Preferences/Sound I have the Default Mixer Track set to my sound card and the pulseaudio server, which I thought controlled the buttons.

EDIT EDIT:
Messing with things has paid off again, it was one of the other options under Default Mixer Track.  I just went down the list and picked the one labeled 'playback' and then tested it.  This is the last time I try to mix desktop environment, GNOME is just fine for me o_0

---

### Post by c5vetter on 2009-08-24
relative newb to Ubuntu 9.0.4 - have basically got everything to work by following Guides and asking questions - sound is one area I haven't been able to figure out - so, went back to basics and started with the following:


lspci

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation G72M [GeForce Go 7400] (rev a1)
06:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
08:06.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
08:06.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
08:06.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
08:06.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller
08:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 01)

then lsusb

Bus 005 Device 002: ID 03f0:171d Hewlett-Packard Wireless (Bluetooth + WLAN) Interface [Integrated Module]
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 067b:2305 Prolific Technology, Inc. PL2305 Parallel Port
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 007: ID 059b:0033 Iomega Corp. 
Bus 001 Device 006: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 001 Device 011: ID 0d8c:0006 C-Media Electronics, Inc. Storm HP-USB500 5.1 Headset
Bus 001 Device 010: ID 067b:2303 Prolific Technology, Inc. PL2303 Serial Port
Bus 001 Device 009: ID 067b:2305 Prolific Technology, Inc. PL2305 Parallel Port
Bus 001 Device 008: ID 0b95:7720 ASIX Electronics Corp. AX88772
Bus 001 Device 005: ID 0409:0059 NEC Corp. HighSpeed Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0409:0059 NEC Corp. HighSpeed Hub

then cat /proc/asound/cards
cat: /proc/asound/cards: No such file or directory

then cat /proc/asound/modules
cat: /proc/asound/modules: No such file or directory

then aplay -l
aplay: device_list:217: no soundcards found...

then arecord -l
arecord: device_list:217: no soundcards found...


so........where do I go from here!?

---

### Post by markbuntu on 2009-08-24
From there your best bet would be to reinstall alsa and see if it can autodetect your sound hardware which is seems to have completely missed. Before you do that though update your system and reboot.

---

### Post by c5vetter on 2009-08-24
otay - next I tried the following, and am still confused BIG TIME!


sudo modprobe snd-hda-intel
[sudo] password for aleshire: 
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base.save, it will be ignored in a future release.
WARNING: /etc/modprobe.d/alsa-base.save line 4: ignoring bad line starting with 'grep'
WARNING: /etc/modprobe.d/alsa-base.save line 5: ignoring bad line starting with 'cat'
WARNING: Error inserting snd_timer (/lib/modules/2.6.28-15-generic/kernel/sound/core/snd-timer.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_pcm (/lib/modules/2.6.28-15-generic/kernel/sound/core/snd-pcm.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_hda_intel (/lib/modules/2.6.28-15-generic/kernel/sound/pci/hda/snd-hda-intel.ko): Unknown symbol in module, or unknown parameter (see dmesg)

---

### Post by c5vetter on 2009-08-24
what do you mean by From there your best bet would be to reinstall alsa and see if it can autodetect your sound hardware which is seems to have completely missed. Before you do that though update your system and reboot.

want to try and do this step-by-step, as it seems I missed some steps following the Guide

---

### Post by mocha on 2009-08-24
> **c5vetter said:**
> WARNING: Error inserting snd_timer (/lib/modules/2.6.28-15-generic/kernel/sound/core/snd-timer.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_pcm (/lib/modules/2.6.28-15-generic/kernel/sound/core/snd-pcm.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_hda_intel (/lib/modules/2.6.28-15-generic/kernel/sound/pci/hda/snd-hda-intel.ko): Unknown symbol in module, or unknown parameter (see dmesg)

Did you change or update your kernel after compiling Alsa?

---

### Post by c5vetter on 2009-08-24
don't remember doing anything like that - but anything is possible - doing things from the CLI is all new to me!

---

### Post by c5vetter on 2009-08-24
also, decided to run the following cmd:  lshw -C sound

and got the following result:

WARNING: you should run this program as super-user.
  *-multimedia UNCLAIMED  
       description: Audio device
       product: 82801G (ICH7 Family) High Definition Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0

so, does this help in any way towards helping me get sound????

---

### Post by c5vetter on 2009-08-25
okay, tried something different this evening to see what the heck is going on with my 'puter

sudo aptitude install linux-ubuntu-modules-`uname -r` linux-generic

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done
Couldn't find any package whose name or description matched "linux-ubuntu-modules-2.6.28-15-generic"
Couldn't find any package whose name or description matched "linux-ubuntu-modules-2.6.28-15-generic"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done

so, what does this tell the Ubuntu gurus??????

---

### Post by neu2buntu on 2009-08-28
you are trying to install a package that doesnt exist or is not in the repos....  it must either be linux-restricted-modules or linux-backports-modules or both you need. just find out the package you need and run the original command ,replacing "ubuntu" with "restricted" and/or "backports"

---

### Post by jtuchscherer on 2009-08-30
> **markbuntu said:**
> 

** If your sound stops**
If your sound is generally working Ok but after a while just fades out or stops and you are not doing anything in particular to make this happen, like installing updates or fooling around with the sound settings or the applications and sound returns like normal when you reboot, this seems to be a particular bug in the hda-intel driver or kernel problems with Intrepid so we must wait for it to be fixed and an update made available. You can avoid having to reboot by restarting ALSA and PulseAudio following the directions in **ALSA Trouble** below for now.



I had this problem and found a good solution. See here:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/279478](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/279478)

I wish this could be added to the starting post. That would have  saved me some time.

---

### Post by gotchanisa on 2009-09-07
Hi,

I have just installed 9.04. My PC has a dual boot to windows. I am a novice when it comes to Ubuntu. The problem is that I don't hear sound on 9.04. My PC had an integrated sound card that went kaput. I now have another sound card inserted in a PCI slot. Sound works properly on windows but not able to get the same behavior on Ubuntu. I think it has got something to do with the drivers. Help! Please remember that I am a novice and need very simple instructions.

Thanks
Thomas

---

### Post by ranch hand on 2009-09-07
> **gotchanisa said:**
> Hi,

I have just installed 9.04. My PC has a dual boot to windows. I am a novice when it comes to Ubuntu. The problem is that I don't hear sound on 9.04. My PC had an integrated sound card that went kaput. I now have another sound card inserted in a PCI slot. Sound works properly on windows but not able to get the same behavior on Ubuntu. I think it has got something to do with the drivers. Help! Please remember that I am a novice and need very simple instructions.

Thanks
Thomas
It is pretty hard to see what your problem is without knowing anything about your system other than it will run 9.04 and has a pci sound card.

How about some details?

---

### Post by gotchanisa on 2009-09-07
The PC is a 1.7Ghz pentium 4 with 1 GB ram. I have two hard disks and one of them is partitioned into 2. The windows is on the 40 GB hard disk. Ubuntu is intalled on one of the 80 GB partitions. I am using a creative sound card.

What other kind of details would you like to know? Is there a command I can run and post the result here?

Thanks!
Thomas

---

### Post by ranch hand on 2009-09-07
I think that most of the creative cards are covered.  Which one do you have?

I use an Audigy 1 card on this box, I got it because I had never run Linux before and my son had this type card in his box.

Have you checked in System>Sound>Devices?  It is a good place to start.

Are you sure that your sound is not muted?

I really like the gnome-alsamixer better than any other, it is available in synaptic or;
```

sudo apt-get install gnome-alsamixer

```
will get it for you and it will appear in your Applications>Sound & Video as soon as download/install is finished.  Be sure to get into the preferences and select bass, treble and tone.  You will need to go to the "switchs" tab and check the "tone" box.

If you have not already done so you had better add the Medibuntu repo and key to your box.

[http://ubuntuguide.org/wiki/Ubuntu:Jaunty#Add_Extra_Ubuntu_Repositories](http://ubuntuguide.org/wiki/Ubuntu:Jaunty#Add_Extra_Ubuntu_Repositories)

A lot of good info on that site.

After that run;
```

sudo apt-get install ubuntu-restricted-extras

```
This will get you the stuff you need to play CDs and DVDs.

Theer is good information on ubuntuguide about that too.

---

### Post by gotchanisa on 2009-09-08
I tried everything you suggested... still no sounds :(
I'm not sure what is the make of my sound card. I tired following instructions from here [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)
but when I run that command, I get a no such file or directory message in the terminal.:confused:

---

### Post by ranch hand on 2009-09-08
> **gotchanisa said:**
> I tried everything you suggested... still no sounds :(
I'm not sure what is the make of my sound card. I tired following instructions from here [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)
but when I run that command, I get a no such file or directory message in the terminal.:confused:
I haven't looked at those directions, I am trying to get another of my 9 9.10 variations to work again.  Alpha testing is a lot of FUN.  There are times though when it is a lot like work.

Your sound card is a pci card.  To find it all you need to do is this command in terminal;
```

lspci

```
This will list your pci stuff like so;
```

jak@jak-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82X38/X48 Express DRAM Controller
00:01.0 PCI bridge: Intel Corporation 82X38/X48 Express Host-Primary PCI Express Bridge
00:06.0 PCI bridge: Intel Corporation 82X38/X48 Express Host-Secondary PCI Express Bridge
00:19.0 Ethernet controller: Intel Corporation 82566DC-2 Gigabit Network Connection (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IR (ICH9R) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 4 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA IDE Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc RV610 video device [Radeon HD 2400 PRO]
04:00.0 Serial controller: 3Com Corp, Modem Division 56K FaxModem Model 5610 (rev 01)
04:04.0 Multimedia audio controller: Creative Labs SB Audigy (rev 03)
04:04.1 Input device controller: Creative Labs SB Audigy Game Port (rev 03)
04:05.0 Communication controller: NetMos Technology PCI 9835 Multi-I/O Controller (rev 01)
04:0a.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)

```
Now let us see yours and we will go on from there.

---

### Post by gotchanisa on 2009-09-09
Here is what I get


nibu@nibu-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
01:00.0 RAID bus controller: VIA Technologies, Inc. VT6421 IDE RAID Controller (rev 50)
01:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
01:03.0 Multimedia audio controller: Creative Labs CA0106 Soundblaster
nibu@nibu-desktop:~$ 


Thanks again for your patience :)

---

### Post by ranch hand on 2009-09-09
I should have asked you this in the first place and didn't because your sound works on that off brand OS you have on there too.  But I am not real familiar with that OS and maybe there is a different proceedure used to switch this stuff.

Is your intigrated Intel Audio Controler turned off in your bios?  I would assume that you had to do that to get the SB card to work but I am not sure.

This is adifferent card than I use so a little research is needed.  To give you an idea how to work on these things here is what I have done.  It is hard but I think that you can do it.

I pulled up my search engine (no I don't google but I am sure it would work and they have a dedicated linux search engine) and entered "CA0106" copy/pasted right off your post.

This card has been around a while too, like mine, it should work.  Here is what the Alsa folks have to say;

[http://alsa.opensrc.org/index.php/Ca0106](http://alsa.opensrc.org/index.php/Ca0106)

Acording to the "page info" on that page it was last modified on "Fri 05 Oct 2007 05:46:54 PM MDT".

Down at the bottom of the page there is a list of cards using that chip.  One, the 24bit, needs (or did then) a codec.  Which one have you got?  If you pull up the gnome-also mixer it, hopefully, will list the card up at the top of the page as in:
"Audigy 1 ES [SB0160] (Alsa mixer)" which is what mine says running under Jaunty.

[http://ubuntuforums.org/showthread.php?t=19307](http://ubuntuforums.org/showthread.php?t=19307)

Is a thread from '05 on the 24bit card.

You can access the controls for the alsa mixer in the terminal (you may want to check this as it is sometime more accurate than any gui) by;
```

sudo alsamixer -c 0

```
Another command that my be helpful is;
```

man alsamixer

```
This will give you whatever info is available through Ubuntu on the mixer.  The "man" pages are a handy thing to study in your "free" time.  Sometimes I can even under stand some of it.  This man page looks pretty understandable.

If you want to experiment just remember that you are probably safe as long as you go slow.  I multi-boot so I can work on problems like this in an environment that is safe (I can bugger it and it doesn't matter - 10Gb partition is big enough for a "play" install, just not much room for data).

I am rambling (tired).  Here is the link to the search page;

[http://www.search.com/search?q=CA0106](http://www.search.com/search?q=CA0106)

Looks like a lot of good info.

I love SB cards.  Let us get this bugger up and running.

---

### Post by gotchanisa on 2009-09-09
Ranch hand - you are invincible!!! You rock!!:guitar:
I had not disabled the integrated sound card and on doing so in the bios... sound works like a charm :) 
Thank You Thank You Thank YOU!!:P

---

### Post by ranch hand on 2009-09-09
WOW, that was simple.  Great.

Does suround sound work or don't you have that?

Works great on my Audigy 1 (5,1 suround) with an Altec Lansing speaker system.  My son runs a RCA cable from his card to a mixer board and big speakers.  I am going to get he cable and run it through the house to our reciever so that we can play our collection of music over large speakers.

I am glad your system is working.  I think you will be happy with it.  When you save music to your music file be sure to try the .ogg format.  I think it sounds great.

---

### Post by leeelson on 2009-09-14
I have an inop internal mike (all other sound OK) on an HP mini 110 running Ubuntu 8.04. This setup does *not* include Pulseaudio. As a newbie trying to sift through massive amounts of info, it seems like the most likely solution for me is to upgrade from Alsa 1.0.16 (original installed version) to something higher. Similar reports (different platform) indicate that some later versions work OK, some (21???) don't. I'm having problems doing an upgrade because the configure script assumes that the kernel headers are in /usr/src. Mine aren't and I'm not sure where to find them (or whether the upgrade will even work, or what version to upgrade to).

Any thoughts?

---

### Post by ranch hand on 2009-09-14
> **leeelson said:**
> I have an inop internal mike (all other sound OK) on an HP mini 110 running Ubuntu 8.04. This setup does *not* include Pulseaudio. As a newbie trying to sift through massive amounts of info, it seems like the most likely solution for me is to upgrade from Alsa 1.0.16 (original installed version) to something higher. Similar reports (different platform) indicate that some later versions work OK, some (21???) don't. I'm having problems doing an upgrade because the configure script assumes that the kernel headers are in /usr/src. Mine aren't and I'm not sure where to find them (or whether the upgrade will even work, or what version to upgrade to).

Any thoughts?
Not sure exactly what you are asking for.

If you want to upgrade to 8.10;
Go to terminal:
```

gksudo gedit /etc/apt/sources.list

```
Go through the whole file and change all references to "Hardy" to read "Intrepid".

The only one I would not change is hashed out (##  whatever) and that is Hardy backports.  I would unhash that (  whatever).

Save the file, close the file.  Close everything but your terminal.  In terminal;
```

sudo apt-get update

```
and then
```

sudo apt-get dist-upgrade

```
For full enjoyment, maximize the terminal.  Follow instructions as they may appear.  Take your time.

HAVE FUN

---

### Post by leeelson on 2009-09-14
> **ranch hand said:**
> Not sure exactly what you are asking for.

If you want to upgrade to 8.10;
Go to terminal:
```

gksudo gedit /etc/apt/sources.list

```
Go through the whole file and change all references to "Hardy" to read "Intrepid".

The only one I would not change is hashed out (##  whatever) and that is Hardy backports.  I would unhash that (  whatever).

Save the file, close the file.  Close everything but your terminal.  In terminal;
```

sudo apt-get update

```
and then
```

sudo apt-get dist-upgrade

```
For full enjoyment, maximize the terminal.  Follow instructions as they may appear.  Take your time.

HAVE FUN
Thanks for the reply, but I was looking more for help upgrading to a later version of Alsa. Is there any reason to believe 8.10 has a later version of Alsa and that it is likely to solve the problem?

---

### Post by JOshea on 2009-09-14
I know this thread came out awhile ago but for AMD64 users with jaunty

one very important thing that is not covered here is using 
audacity to record whats coming through the speakers ie 
how to record songs playing on the web or wherever if you are using amd64 
jaunty - including flash files that are encoded ...

I switched everything to pulse audio from preferences on the main menu 
the "sound" selection on the main menu - sound preferences - except the main mixer - leave as is ...then 

use the pulse audio device chooser - go under the volume control 
and fire up audacity ...go under preferences there and choose pulse for audacity under both playback and record 

under the device chooser/ volume control -  go to recording tab - 
and hit record on audacity ...my card does not have a mix setting - but you can move the stream to the simultaneous from both playback and record tabs setting - and then you will see Audacity recording whats playing 

this took me way too long to figure out and you don't have to do any fancy work arounds or scripts to get it to work - I followed the link for jaunty but did not get rid of flash by adding the extra 32bit plugs to replace them but the others don't hurt to have - jack audio is not necessary and you can still save and load the wav files into something like Ardour 

cheers

---

### Post by leeelson on 2009-09-14
> **ranch hand said:**
> Not sure exactly what you are asking for.

If you want to upgrade to 8.10;
Go to terminal:
```

gksudo gedit /etc/apt/sources.list

```
Go through the whole file and change all references to "Hardy" to read "Intrepid".

The only one I would not change is hashed out (##  whatever) and that is Hardy backports.  I would unhash that (  whatever).

Save the file, close the file.  Close everything but your terminal.  In terminal;
```

sudo apt-get update

```
and then
```

sudo apt-get dist-upgrade

```
For full enjoyment, maximize the terminal.  Follow instructions as they may appear.  Take your time.

HAVE FUN
Also, my /etc/apt/sources.list contains no "hardy" references. It seems to be a list of deb URL's.

---

### Post by ranch hand on 2009-09-15
> **leeelson said:**
> Also, my /etc/apt/sources.list contains no "hardy" references. It seems to be a list of deb URL's.
```

deb http://us.archive.ubuntu.com/ubuntu/ hardy main restricted

```
This is from my Hardy install.

Please note, end of line "hardy main restricted"

That said I would, first try changing under
```

## Uncomment the following two lines to add software from the 'backports'
## repository.

```
```

## deb http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

```
to
```

deb http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

```
run
```

sudo apt-get update

```
and 
```

sudo apt-get upgrade

```
This will update all the restricted stuff from newer releases that have been backported
to Hardy but may have missed the regular update stream.

If that doesn't work I would download the Jaunty live CD and try it on your box and see how it works.  If good I would upgrade to it.  I would upgrade to Intrepid first because there is a lot of difference between Hardy and Jaunty.

I still use Hardy as my secure "main" OS for business on line.  I use Jaunty(ext4) much more because it is faster and more fun.  I really like the LTS (Hardy) but the sucker has been turned into an antique very fast.

---

### Post by momist on 2009-09-16
Hi everyone.  I hope someone can help me here.

I upgraded Intrepid to Jaunty a couple of weeks ago, and then went sick (with a spell in hospital).  Sound WAS working after the upgrade.  My audio device is on the motherboard; SiS AC'97.

Over the last few days (I don't know just when) sound stopped working - I got the drumbeat and logon sounds but nothing after that.  Since I've been fiddling to find out what's wrong, I've lost ALL sound entirely :confused:
No drumbeat or anything.  I've looked through reams and reams of threads on here to try to sort this out, checked permissions in GROUPS and all volume controls at maximum etc.  It seems that ALSA can't see my sound card.  I tried re-installing ALSA, and I think that's when the drumbeat stopped working.  Here's the current outputs:

```
 
ian@***:~$ aplay -l
aplay: device_list:217: no soundcards found...

ian@***:~$ lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 735 Host (rev 01)
<snip>
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
<snip>
00:0d.0 Multimedia video controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
00:0d.2 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)
00:0d.4 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [IR Port] (rev 05)

ian@***:~$ cat /proc/asound/cards
 0 [SI7012         ]: ICH - SiS SI7012
                      SiS SI7012 with CMI9738 at irq 11
 1 [Camera         ]: USB-Audio - USB Video Camera
                      USB Video Camera at usb-0000:00:0b.2-3, high speed

ian@***:~$ cat /proc/asound/modules
 0 snd_intel8x0
 1 snd_usb_audio

ian@***:~$ arecord -l
arecord: device_list:217: no soundcards found...

```

I've checked, and  "0 snd_intel8x0" is correct for the onboard audio device listed. I can't find how to cure this missing 'card'.  Sound has never had this trouble on this machine before, and I don't see why it should have suddenly failed.  Can anyone point out what to try next please?

Thanks,

Ian

P.S.  I've run the alsa-info.sh from here:
[https://help.ubuntu.com/community/SoundTroubleshooting?action=show&redirect=DebuggingSoundProblems](https://help.ubuntu.com/community/SoundTroubleshooting?action=show&redirect=DebuggingSoundProblems)

with this result:
[http://www.alsa-project.org/db/?f=afacae8e41c50e03884beddf56465e1e60f351cc](http://www.alsa-project.org/db/?f=afacae8e41c50e03884beddf56465e1e60f351cc)

Is that any help?

---

### Post by BRRFOC on 2009-09-16
I was intrigued by **markbuntu**'s suggestion below, which worked for me. I have 2 sound cards, Intel onboard and Indigo Echo; streaming audio worked fine in Hardy but now Jaunty poses a challenge. Banshee, Rhythymbox work fine, unable to get sound (but have video) for Mozilla stream (but works fine for new user). Any advice for what configuration to look for in new user /home folder that might eliminate need to migrate all files/applications to new user?? 

**This may or may not work for you**
*One easy way that some people have fixed their sound problems is by creating a new user in System/Administration/Users and Groups and then logging in with that. It seems the generic system defaults for new users are different from the initial user defaults that Ubuntu installs. *

---

### Post by jsaulters on 2009-10-10
> **Scratchy, glitchy sound**
If you have an HDA-Intel device try turning up the PCM slider in the volume control. If PCM is set to 0 it makes the sound scratchy for some of those devices.

This worked like a charm for me.  Thank you very much!  

Here is aplay -l output from my system:
```
card 0: NVidia [HDA NVidia], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```


Thanks for also explaining the linux sound architecture in your other thread.  This, too, was was very helpful.

[http://ubuntuforums.org/showthread.php?p=5931543](http://ubuntuforums.org/showthread.php?p=5931543)

---

### Post by gheevaari on 2009-10-16
I Have Audio question ?
Hi There 
               Please Could anybody help me with this problem have soundcard creative soundblaster 5.1 with livedrive & Remote  installed is Ubuntu 9.04 & Ubuntu 9.10 Am Very New to Ubuntu.When I play music whether In Totem Or Any Other multimedia alsamixer Headphone LFE 1 Switches On & Headphone Center 1 Goes on.Thus Sound In Headphone 1 goes to one speaker. Ok So I Switch it off again now this goes on again if i play any other music or if the track changes. so far i have searched for this but no joy.this problem is in jaunty as well as in karmic in  which i have to access the terminal alsamixer i believe this is caused by pulse audio resetting alsamixer but do not know how to solve it .Any Help is greatly appreciated thanks  gheevaari
 lspci  of  Ubuntu 9.10

 00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:02.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Graphics Port 0)
00:07.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 3)
00:12.0 RAID bus controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 13)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation G98 [GeForce 8400 GS] (rev a1)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
03:06.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 08)
03:06.1 Input device controller: Creative Labs SB Live! Game Port (rev 08)

---

### Post by abhiroopb on 2009-10-25
I made a mess of things. Basically, I added some repo's that totally destroyed my dependencies and I had to re-install a lot of packages (including alsa and pulse). I also had to re-install my kernel and numerous other things.

In between doing all this my configuration got messed up. Before adding the repo everything was fine. So, I assume if I were to re-install jaunty at this point everything would work fine. But, of course I'd rather not re-install everything.

What the basic commands show me:

```

$ aplay -l
aplay: device_list:217: no soundcards found...

```

```

$ alsamixer

alsamixer: function snd_ctl_open failed for default: No such device

```

```

lspci
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
	Subsystem: Hewlett-Packard Company Device 30a5
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at d2400000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

```

I've done everything in these guides: 
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)
[http://ubuntuforums.org/showthread.php?t=1130384](http://ubuntuforums.org/showthread.php?t=1130384)
[http://ubuntuforums.org/showthread.php?t=1043568](http://ubuntuforums.org/showthread.php?t=1043568)
[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

Nothing has worked for me. In fact I've done everything twice I think!

Please help!!

---

### Post by markbuntu on 2009-10-25
You could try reloading alsa, which is explained in the OP, and then reboot and hope for the best. A lot of people make many conflicting changes to their system and expect them to work without rebooting...a serious misunderstanding.

---

### Post by Natural20 on 2009-10-25
Hi,

I have a problem with Jaunty 9.04.

I get no sound for anything unless I go to "Sound preferences" and choose HDA Intel198x Analogue (OSS). And even then I can only get sound if I click on the "Test" button beside the choice. The sound does not work in applications outside of the devices tab in sound preferences. 

Copypasted are my basic logs from the OP

00:00.0 Host bridge: Intel Corporation 82P965/G965 Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82P965/G965 PCI Express Root Port (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HB/HR (ICH8/R) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801H (ICH8 Family) 4 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801H (ICH8 Family) 2 port SATA IDE Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc RV570 [Radeon X1950 Pro] (rev 9a)
01:00.1 Display controller: ATI Technologies Inc RV570 [Radeon X1950 Pro] (secondary) (rev 9a)
02:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 03)
02:00.1 IDE interface: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 03)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
05:01.0 Multimedia audio controller: VIA Technologies Inc. VT1720/24 [Envy24PT/HT] PCI Multi-Channel Audio Controller (rev 01)
natural20@natural20-desktop:~$ lsusb
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 003: ID 06a3:8020 Saitek PLC 
Bus 006 Device 002: ID 046d:c051 Logitech, Inc. G3 (MX518) Optical Mouse
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
natural20@natural20-desktop:~$ cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xffaf8000 irq 22
 1 [T71Universe    ]: Aureon71Univ - Terratec Aureon 7.1-Universe
                      Terratec Aureon 7.1-Universe at 0xbc00, irq 22
natural20@natural20-desktop:~$ cat /prc/asound/modules
cat: /prc/asound/modules: No such file or directory
natural20@natural20-desktop:~$ cat /proc/asound/modules
 0 snd_hda_intel
 1 snd_ice1724
natural20@natural20-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: T71Universe [Terratec Aureon 7.1-Universe], device 0: ICE1724 [ICE1724]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: T71Universe [Terratec Aureon 7.1-Universe], device 1: IEC1724 IEC958 [IEC1724 IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: T71Universe [Terratec Aureon 7.1-Universe], device 2: ICE1724 Surrounds [ICE1724 Surround PCM]
  Subdevices: 3/3
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
natural20@natural20-desktop:~$ arecord -l
**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 3/3
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
card 0: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: T71Universe [Terratec Aureon 7.1-Universe], device 0: ICE1724 [ICE1724]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: T71Universe [Terratec Aureon 7.1-Universe], device 1: IEC1724 IEC958 [IEC1724 IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

So I'm really not sure what to do, any help would be wonderful.

---

### Post by markbuntu on 2009-10-25
> **gheevaari said:**
> I Have Audio question ?
Hi There 
               Please Could anybody help me with this problem have soundcard creative soundblaster 5.1 with livedrive & Remote  installed is Ubuntu 9.04 & Ubuntu 9.10 Am Very New to Ubuntu.When I play music whether In Totem Or Any Other multimedia alsamixer Headphone LFE 1 Switches On & Headphone Center 1 Goes on.Thus Sound In Headphone 1 goes to one speaker. Ok So I Switch it off again now this goes on again if i play any other music or if the track changes. so far i have searched for this but no joy.this problem is in jaunty as well as in karmic in  which i have to access the terminal alsamixer i believe this is caused by pulse audio resetting alsamixer but do not know how to solve it .Any Help is greatly appreciated thanks  gheevaari
 lspci  of  Ubuntu 9.10

 00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:02.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Graphics Port 0)
00:07.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 3)
00:12.0 RAID bus controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 13)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation G98 [GeForce 8400 GS] (rev a1)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
03:06.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 08)
03:06.1 Input device controller: Creative Labs SB Live! Game Port (rev 08)

There are some problems with Pulseaudio in 9.10 now and many fixes will be instituted at the release. If this problem persists after the release updates next week please start a new thread and we will see what we can do to help you.

---

### Post by markbuntu on 2009-10-25
> **Natural20 said:**
> Hi,

I have a problem with Jaunty 9.04.

I get no sound for anything unless I go to "Sound preferences" and choose HDA Intel198x Analogue (OSS). And even then I can only get sound if I click on the "Test" button beside the choice. The sound does not work in applications outside of the devices tab in sound preferences. 

...........

So I'm really not sure what to do, any help would be wonderful.

Did you follow the directions in here?

[http://ubuntuforums.org/showthread.php?t=1130384](http://ubuntuforums.org/showthread.php?t=1130384)

---

### Post by Natural20 on 2009-10-25
Well I don't get startup sound which basically contravenes what's said in the first sentence there. I'll check it though.

---

### Post by markbuntu on 2009-10-25
> **BRRFOC said:**
> I was intrigued by **markbuntu**'s suggestion below, which worked for me. I have 2 sound cards, Intel onboard and Indigo Echo; streaming audio worked fine in Hardy but now Jaunty poses a challenge. Banshee, Rhythymbox work fine, unable to get sound (but have video) for Mozilla stream (but works fine for new user). Any advice for what configuration to look for in new user /home folder that might eliminate need to migrate all files/applications to new user?? 


There are many places you can look in the hidden folders in your /home/user to try to parse the differences. I gave up on trying to figure it all out myself and moved my personal files to a new directory. Then deleted the old user name, which I wanted to keep, rebooted and then created a new user with the old user name and password and moved everything back. A pita but it was easier than parsing all the settings in all those files and trying to figure out what to change where.

---

### Post by Natural20 on 2009-10-25
> **markbuntu said:**
> Did you follow the directions in here?

[http://ubuntuforums.org/showthread.php?t=1130384](http://ubuntuforums.org/showthread.php?t=1130384)

Have now followed the entire guide apart from the mic part which isn't relevant to the problem. 

The terratec aureon 7.1 universe soundcard detects the music being played but I can't hear anything.

My headphones are fine because I can still hear the test beep on HDA Intel with OSS.

Help would be appreciated.

EDIT: If I switch the stream to HDA Intel then the audio is fine. Now I just don't get why my soundcard is failing at the linux game.

---

### Post by abhiroopb on 2009-10-25
> **markbuntu said:**
> You could try reloading alsa, which is explained in the OP, and then reboot and hope for the best. A lot of people make many conflicting changes to their system and expect them to work without rebooting...a serious misunderstanding.

Thanks. I did reload alsa quite a few times (after I did any change). And I have rebooted. Unfortunately, nothing seems to be working.

Is there any way to basically reset all the kernels, modules, drivers, etc. and start from scratch with regard to the sound?

---

### Post by itsjareds on 2009-10-29
Does anyone know of any updated settings for Ubuntu Karmic that I can set to get my HDA Intel working in multiple applications? Currently I can only get audio to work in one app at a time. I noticed the OP's section about multiple applications but there is nothing for Karmic in there yet.

Hope to get some response soon since this is really annoying :)

---

### Post by Garyu on 2009-10-30
I did a fresh install of 9.10 Karmic Koala today, but couldn't get sound to work. Not that I tried that many options, basically I've just gone through anything and everything available from the sound icon at the clock on the main panel. 

My problems are:
1) can only get stereo (I have 5.1 surround)
2) can not get mic working at all

I'm doing a complete reinstall now, and hoping to get it fixed. If I do I will update this post with how I did it, but in the mean time I would very much appreciate any tips.

---

### Post by ranch hand on 2009-10-30
A reinstall is probably not going to fix this.

What is your sound card?

If you do not know;
```

lspci

```

---

### Post by Garyu on 2009-10-30
> **ranch hand said:**
> What is your sound card?
Soundblaster X-Fi XtremeGamer

Maybe I should have put that in the text rather than just the title. :p

---

### Post by ranch hand on 2009-10-30
Yup, I can't read.

I would;
```

sudo apt-get install gnome-alsamexer

```
You can find it in the Applications>Sound and Video section and right click on it and put it on your panel.  Go through the preferences.  Make sure you check the box for tone and add the bass and treble.  I am on Jaunty, right now, and it is slightly different here than in 9.10 but I think there is a box for external amp you need to click too.

There are a bunch in preferences you can uncheck too.  This will give you a lot cleaner look.

SB cards seem to do better with the gnome-alsamixer than other mixers.  Beats me, but it works, generally.

---

### Post by Garyu on 2009-10-30
> **ranch hand said:**
> SB cards seem to do better with the gnome-alsamixer than other mixers.  Beats me, but it works, generally.

Interesting.

1) Lots of high-pitch static, nothing with standard mixer changes anything (except from good stereo sound to crappy stereo sound).
2) Loaded gnome-alsamixer. Touching any of the controls makes the high-pitch static disappear. Sound is actually rather nice and surround works fine. 
3) If I touch the surround speakers slider, all the other automatically mute sometimes. If I then reset the other sliders it is sometimes possible to change the surround slider and it actually affects only the surround speakers. Then other times it resets all of the other sliders to mute again.
4) After fixing the sound with gnome-alsamixer, changing the volume with the icon at the clock will re-introduce the high-pitch static again. If I then go back to 100% volume, the high-pitch sound disappears. Same way, if I use my keyboard multimedia keys to change volume, high-pitch static returns unless I have the volume at 100%. Changing volume in gnome-alsamixer works fine.

**5) Mic still isn't working.** ](*,)

---

### Post by ranch hand on 2009-10-30
I don't know about the mic problem, works on my desktop box.

I always use the mixer for all controls.  The resetting to mute sucks.  Hopefully there will be an update.

My sound is great on my old audigy1 5.1 card.  I got it and put it in because I knew it would work with Linux.  Sound great so why get a newer one?

The integrated sound controller on this Dell sounded awful.  Like an early transister radio.

---

### Post by prabath_fun on 2009-11-13
Hi,
I want to enable 5.1 surround in Ubuntu9.10. I was/am using Ubuntu9.04 and I got it worked by right click on speaker Icon, preferences and enabled 6 speakers under speaker mode. Also, I was able to select "RLC:883....." as sound card option.
  But, In Ubuntu9.10, I am not finding "RLC:883..." option and could not able to see speaker mode etc., any where. Blieve that Ubuntu 9.10 not identifies my sound chip set which is in-built to my motherboard.
My Desktop Mother board Details are **[COLOR="Magenta"]D102GGC2[/COLOR]**.
High Definition Audio Subsystem
The board includes a flexible 6-channel audio subsystem based on a High Definition Audio interface. The audio subsystem features:
&#8226; ATI IXP 450 Southbridge
&#8226; Realtek ALC883 audio codec
&#8226; Impedance sensing capability for jack re-tasking
&#8226; S/N (signal-to-noise) ratio of 90 dB
&#8226; Microphone input supporting:
&#9135; Stereo microphone
&#9135; Microphone boost
Xpress200 chipset.

Please help me to enable 5.1 in my motherboard with Ubuntu9.10.
Prabath

---

### Post by ranch hand on 2009-11-13
I would install the gnome-alsamixer.  If it does not do the job you can always remove it.

---

### Post by lostinlove on 2009-11-13
> **ranch hand said:**
> I would install the gnome-alsamixer.  If it does not do the job you can always remove it.

is it good to enable 5.1in ubuntoo actually i am experiencing the same problem in ubuntoo

---

### Post by ranch hand on 2009-11-13
All I can say is that my Audigy5.1 sounds great in 8.04, 9.04, 9.10, 10.04testing.

---

### Post by SuperScottishHero on 2010-03-04
My sound works OK for whichever user logs on FIRST to my Karmic laptop. However, if I switch to a second user (so that my wife and I don't clog up each others desktop, bookmarks, etc!) then whoever logs in second gets no sound playback, no matter what volume settings are. 

Is there a way to workaround this, without the dogmatic suggestion that some other threads have of "just delete pulseaudio!"?

Thanks

---

### Post by ElectricJake on 2010-03-10
I'm open to dogmatic suggestions

---

### Post by markbuntu on 2010-03-10
> **SuperScottishHero said:**
> My sound works OK for whichever user logs on FIRST to my Karmic laptop. However, if I switch to a second user (so that my wife and I don't clog up each others desktop, bookmarks, etc!) then whoever logs in second gets no sound playback, no matter what volume settings are. 

Is there a way to workaround this, without the dogmatic suggestion that some other threads have of "just delete pulseaudio!"?

Thanks

Do you logout when switching users or are you using the fast user switcher?

The way pulseaudio is designed is for one user at a time so the first one logged in gets control of the hardware and keeps it until logged out.

There was recently a long and trying discussion of this very issue at the pulse mailing list and some fixes were proposed. I am not really clear on how that worked out but it is somewhere between pulse and dbus rules Any fixes will come in newer releases of pulseaudio or some changes in the dbus rules or both.

You can file a bug report at launchpad against pulseaudio and/or fast user switcher to get some awareness and maybe some attention to this by the ubuntu packagers if the fast user switcher is where the problem is.

---

### Post by chris5 on 2010-07-21
I've got an old Presario 2700 running Lubuntu 10.04 LTS. Sound is through Intel 82801CA-ICH3. My question is why I can't hear sound through the built-in speakers but I can through wired headphones?
I have tried all the obvious - I think - such as clicking on volume icon on taskbar and moving it to 100%, I have run alsamixer in the terminal and moved the necessary sliders to the max, etc.

Is it looking like the internal speakers are knackered or am I missing something basic?

Peace,

Chris

---

### Post by chris5 on 2010-07-23
Well the laptop speakers aren't u/s, they do indeed work - with windows. It's a shame that a major player in the 'alternative' operating systems market can't get the basics sorted out after all this time. Actually, its pathetic.

Peace

---

### Post by gtr225 on 2010-08-08
> **SuperScottishHero said:**
> My sound works OK for whichever user logs on FIRST to my Karmic laptop. However, if I switch to a second user (so that my wife and I don't clog up each others desktop, bookmarks, etc!) then whoever logs in second gets no sound playback, no matter what volume settings are. 

Is there a way to workaround this, without the dogmatic suggestion that some other threads have of "just delete pulseaudio!"?

Thanks
I am also missing this feature. One of the reasons I switched from Fedora to Ubuntu back in 2006 was the ability to share the soundcard between fast switching users. So much for progress...

---

### Post by omarly on 2010-08-14
[/QUOTE]
> **Second Life**
I do not use Second Life myself so these links are getting a little old. If you are a Second Life user please let me know if this information is still valid or if it needs to be updated, otherwise this section will be deleted.

[http://vboards.stratics.com/showthread.php?p=836114](http://vboards.stratics.com/showthread.php?p=836114)

[http://jira.secondlife.com/browse/VWR-5708](http://jira.secondlife.com/browse/VWR-5708)
[/QUOTE]

I just found I was the one without problems in Second Life, but it was a person with a mac, who did have issues with the mic.

I run 10.04 64bit, and had to do a mod in the start of the secondlife script so it reads like this:

```

#!/bin/bash

## Here are some configuration options for Linux Client Testers.
## These options are for self-assisted troubleshooting during this beta
## testing phase; you should not usually need to touch them.

## - Avoids using any OpenAL audio driver.
export LL_BAD_OPENAL_DRIVER=x
## - Avoids using any FMOD audio driver.
#export LL_BAD_FMOD_DRIVER=x
```

to get the audio stream to run. The mod was in the line 

export LL_BAD_OPENAL_DRIVER=x

which read "#export LL_BAD_OPENAL_DRIVER=x" before.

Excellent guide, I think I have been here "in the old days" when tweaking was more of a problem. I got some hardware which needed special attention.
Now I run all my programs without issues, except for flash, which is OK, after last update, even on dual screen.

Just wanted to add this, and thank everybody for their contribution with this OS. Its getting SO good, and I can not understand why MS users are so hard to get converted??? I still have trouble getting my family to switch.

I never looked back a 1/100 sec after my switch.

HAVE FUN!

PS:
Sorry if i do not code/quote correctly

---

### Post by jabeavers on 2010-08-15
I've read several of the pertinent links and could not find what I need. Basically, I want pulseaudio to bind to only one output on one of my soundcards. I have an hda-intel 7.1 onboard card which I have split the outputs into individual pcm's (via asound.conf). These outputs will go into a mixing console. So, basically, I want to use pulseaudio to bind to one output for system sounds and flash movies on websites and stuff like that. I have a pro soundcard for low latency recording through jack, but I'm just asking about pulseaudio. I want pulseaudio to bind to only one of the outputs on the hda-intel card, and leave the others alone for alsa to deal with.

So, is it possible to have pulseaudio connect to only one device/pcm, and if so, how do I do it?

John

---

### Post by jabeavers on 2010-08-17
Nevermind, I'm doing what I need with alsa only. Thanks.

---

### Post by marcoharder on 2010-08-31
Hi!
 
I was just wondering whether you guys could help me. For some reason, my two soundcards [EMU 1212m and an ES1371 chipset card] are detected on the regular kernel [2.6.34] but only one appears on the RT kernel. I'm using Ubuntu 10.04 Desktop now and installed the Ubuntu Studio packages via Synaptic. 
 
I've also already installed the necessary firmware and drivers for both cards, which makes me wonder whether I need to do that again, only thatI need to boot using the RT kernel. Please advise. Thanks!
 
MH

---

### Post by BigJules on 2010-09-01
Sometimes the easiest works: try putting a definite value into all of the columns of alsamixer. Seems if there's a value omitted in any of the variables it gets it all in a twist and can't parse the resulting string. 
Restarting PulseAudio ($ pulseaudio --kill, --start) helps too.
Worked for me!

---

### Post by ThexDarksider on 2010-12-20
The "only one program at a time can access ALSA" problem has bothered me for  about 6 months now, but I've finally found a workaround. Most certainly  not the best, but at least it works. Whenever you open an application  that "steals" sound from others (like from PulseAudio), go to System &#8594;  Preferences &#8594; Sound, then click the Hardware tab, select the device  you're using, change the profile in the drop-down box to "Off", and then  change it back to what it was. That should restore the sound once again  and make it available to all open applications. I don't know will it  work for you, but it worked for me so I thought I should share this neat  little workaround. :)

---

### Post by mrz80 on 2011-01-10
> **SuperScottishHero said:**
> My sound works OK for whichever user logs on FIRST to my Karmic laptop. However, if I switch to a second user (so that my wife and I don't clog up each others desktop, bookmarks, etc!) then whoever logs in second gets no sound playback, no matter what volume settings are. 

Is there a way to workaround this, without the dogmatic suggestion that some other threads have of "just delete pulseaudio!"?

Thanks

I have exactly the opposite problem on my Lucid desktop box.  The *second* user to fire up an X server hijacks sound from the first user, and the only way the first user can get it back is to kill the second user's session.  Needless to say, this is a suboptimal solution to the problem!  Any progress on the subject?

---

