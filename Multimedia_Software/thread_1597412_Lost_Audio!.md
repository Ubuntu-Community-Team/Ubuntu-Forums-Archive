---
title: "Lost Audio!"
date: 2010-10-15
forum: Multimedia Software
---

### Post by williepabon on 2010-10-15
I installed MythTV on my pc to use my WinTV card (TV tuner card), and while I was working with the application configuration (mythbackend) because I was getting video but not audio, and while playing with different configurations with the video capture card I LOST ALL AUDIO!. My pc has internal audio hardware on the main board but also I have an SB Audigy2 card, which is my main audio hardware for the pc. I don't know if also the problem was caused because I installed the ALSA mixer app and Kmix app (testing to see which of the two apps was more practical). I know that the problem is not hardware because when I boot up with WindowsXP the audio works fine.

The detected audio hardware of my system is:

*-multimedia
             description: Multimedia audio controller
             product: 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=Intel ICH latency=0
             resources: irq:17 ioport:ec00(size=256) ioport:e8c0(size=64) memory:dffffa00-dffffbff memory:dffff900-dffff9ff

*-multimedia
                   description: Multimedia audio controller
                   product: SB Audigy
                   vendor: Creative Labs
                   physical id: d
                   bus info: pci@0000:03:0d.0
                   version: 04
                   width: 32 bits
                   clock: 33MHz
                   capabilities: pm bus_master cap_list
                   configuration: driver=EMU10K1_Audigy latency=64 maxlatency=20 mingnt=2
                   resources: irq:49 ioport:dc80(size=64)
              *-input
                   description: Input device controller
                   product: SB Audigy Game Port
                   vendor: Creative Labs
                   physical id: d.1
                   bus info: pci@0000:03:0d.1
                   version: 04
                   width: 32 bits
                   clock: 33MHz
                   capabilities: pm bus_master cap_list
                   configuration: driver=Emu10k1_gameport latency=64
                   resources: irq:0 ioport:dc78(size=8)
              *-firewire
                   description: FireWire (IEEE 1394)
                   product: SB Audigy FireWire Port
                   vendor: Creative Labs
                   physical id: d.2
                   bus info: pci@0000:03:0d.2
                   version: 04
                   width: 32 bits
                   clock: 33MHz
                   capabilities: pm bus_master cap_list
                   configuration: driver=ohci1394 latency=64 maxlatency=4 mingnt=2
                   resources: irq:50 memory:dfecb800-dfecbfff memory:dfecc000-dfecffff

The TV card is:

 *-multimedia:0
                description: Multimedia video controller
                product: Bt878 Video Capture
                vendor: Brooktree Corporation
                physical id: d
                bus info: pci@0000:06:0d.0
                version: 11
                width: 32 bits
                clock: 33MHz
                capabilities: vpd pm bus_master cap_list
                configuration: driver=bttv latency=64 maxlatency=40 mingnt=16
                resources: irq:17 memory:d8001000-d8001fff(prefetchable)
           *-multimedia:1
                description: Multimedia controller
                product: Bt878 Audio Capture
                vendor: Brooktree Corporation
                physical id: d.1
                bus info: pci@0000:06:0d.1
                version: 11
                width: 32 bits
                clock: 33MHz
                capabilities: vpd pm bus_master cap_list
                configuration: driver=Bt87x latency=64 maxlatency=255 mingnt=4
                resources: irq:17 memory:d8000000-d8000fff(prefetchable)

I will REALLY, REALLY appreciate any help to restore my system to health; I don't understand why this should happen when you are only configuring an application.

Thanks.
wp

---

### Post by luks255 on 2010-10-15
Have you tried reading this and following instructions?

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

If you can't solve your problems after that, you should try uninstalling all sound packages and reinstalling them:

> sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils[SIZE=2] 
 [/SIZE][SIZE=2]
Then execute this:[/SIZE][SIZE=2]
     
     [/SIZE]> sudo apt-get install linux-sound-base alsa-base alsa-utils [LEFT][LEFT] [SIZE=2][B]
VERY IMPORTANT NOTE: [/B]Ubuntu (GNOME) users have reported that packages 'gdm' and 'ubuntu-desktop' are removed after removing the linux-sound-base packages. If this happens, then do the following[/SIZE]:
[SIZE=2]    
     [/SIZE]> sudo apt-get install gdm ubuntu-desktop [SIZE=2](3) Reboot[/SIZE][/LEFT]


 [SIZE=2]**VERY IMPORTANT NOTE: **Xubuntu (XFCE) users have reported that packages 'gdm' and 'xubuntu-desktop' are removed after removing the [/SIZE][SIZE=2]linux-sound-base[/SIZE][SIZE=2] packages. If this happens, then do the following[/SIZE]:
[SIZE=2]     
     [/SIZE]> sudo apt-get install gdm xubuntu-desktop [SIZE=2](3) Reboot[/SIZE]
[SIZE=2]
Now you may ask "I already had the packages, so why did I go through the trouble of removing them, then installing them". The answer lies in the --purge option which removes all the extra information that accumulated from tinkering and upgrading. After doing a purge then install, the packages are unpackaged as if it they are brand new.[/SIZE]
[SIZE=2](4) At this point, try using:

      [/SIZE]> aplay -l[SIZE=2] 

 you should get your soundcard listed.[/SIZE][/LEFT]

---

### Post by williepabon on 2010-10-15
Luks255:

Thanks for the info. I'm a newbie with Linux and some of the stuff you put in your reply have difficulty understanding. I went through the instructions in the Comprehensive solution for sound problems. When I do the aplay -l I get the sound cards that I have on my system. Then I ran the Alsamixer and unmutted everything and then did save per the instructions. Still no sound (do I have to reboot after this?). What will be the next steps for my case. Thanks again.
wp

---

### Post by williepabon on 2010-10-16
> **luks255 said:**
> Have you tried reading this and following instructions?

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

If you can't solve your problems after that, you should try uninstalling all sound packages and reinstalling them:

[SIZE=2] 
 [/SIZE][SIZE=2]
Then execute this:[/SIZE][SIZE=2]
     
     [/SIZE][LEFT][LEFT] [SIZE=2][B]
VERY IMPORTANT NOTE: [/B]Ubuntu (GNOME) users have reported that packages 'gdm' and 'ubuntu-desktop' are removed after removing the linux-sound-base packages. If this happens, then do the following[/SIZE]:
[SIZE=2]    
     [/SIZE][SIZE=2](3) Reboot[/SIZE][/LEFT]


 [SIZE=2]**VERY IMPORTANT NOTE: **Xubuntu (XFCE) users have reported that packages 'gdm' and 'xubuntu-desktop' are removed after removing the [/SIZE][SIZE=2]linux-sound-base[/SIZE][SIZE=2] packages. If this happens, then do the following[/SIZE]:
[SIZE=2]     
     [/SIZE][SIZE=2](3) Reboot[/SIZE]
[SIZE=2]
Now you may ask "I already had the packages, so why did I go through the trouble of removing them, then installing them". The answer lies in the --purge option which removes all the extra information that accumulated from tinkering and upgrading. After doing a purge then install, the packages are unpackaged as if it they are brand new.[/SIZE]
[SIZE=2](4) At this point, try using:

      [/SIZE][SIZE=2] 

 you should get your soundcard listed.[/SIZE][/LEFT]

------------------------------------------------------------
Per your instructions, I went through the following steps as explained on [http://ubuntuforums.org/showthread.php?t=205449:](http://ubuntuforums.org/showthread.php?t=205449:)

[FONT="Arial Black"]Getting ALSA drivers from a fresh kernel[/FONT]

**Remove packages**:

sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils

**Reinstall packages**

sudo apt-get install linux-sound-base alsa-base alsa-utils

**Reinstall gdm ubuntu-desktop**

sudo apt-get install gdm ubuntu-desktop

The activities above did not generate any problem.

**REBOOT**: No audio

**Shell Code:** aplay -l
[INDENT]Sound cards on my system are listed[/INDENT]

**Shell Code:** alsamixer
[INDENT]Unmute anything that needs to be unmutted[/INDENT]

**Shell Code:**lspci -v
[INDENT]Sound cards and other h/w are listed[/INDENT]

[FONT="Arial Black"]Verify if ALSA driver for my card (SB Audigy2) exists on ALSA website:[/FONT]
[INDENT]It exists and is the one installed on my system (emu10k1).[/INDENT]

**Shell Code:** sudo modprobe snd-emu10k1
[INDENT]No errors shown[/INDENT]

**Edit file etc/modules**

**Shell Code:** nano /etc/modules
[INDENT]Added at the end of the file:
snd-emu10k1
snd-bt87x[/INDENT]

**REBOOT:** Still no audio

[FONT="Arial Black"]Configuring default soundcards[/FONT]

**Shell Code:** sudo nano /etc/modprobe.d/alsa-base.conf
[INDENT]Inserted at the end of the file:[/INDENT]
[INDENT]options snd-emu10k1 index=0[/INDENT]
[INDENT]options snd-intel8x0 index=1[/INDENT]
[INDENT]options snd-usb-audio index=2[/INDENT]
[INDENT]options snd-bt87x index=3[/INDENT]

**Shell Code:** cat /proc/asound/modules
 0 snd_emu10k1
 1 snd_intel8x0
 2 snd_usb_audio
 3 snd_bt87x

**Adding current user to audio group**
Edited group file. Results as follow:
**Shell Code:**grep 'audio' /etc/group
audio:x:29:williepabon,pulse,mythtv

**REBOOT:** Still no audio

At this point, I don't know what else to do. Hope you people have more ideas based on the activities I have done. Please, help.
wp

---

### Post by lidex on 2010-10-16
> If your Creative Audigy card is not giving you any sound, make sure the analog/digital check box in your sound mixer is unchecked. Updates seem to reset this switch regularly so keep this in mind.
*~markbuntu*

---

### Post by williepabon on 2010-10-17
> **lidex said:**
> *~markbuntu*

Markbuntu:

I feel so stupid! Something as simple as unchecking the analog/digital check box would solve my problem. I was even thinking on reinstalling the whole OS. But, thanks to you, now I have sound.
wp

---

### Post by lidex on 2010-10-17
> **williepabon said:**
> Markbuntu:

I feel so stupid! Something as simple as unchecking the analog/digital check box would solve my problem. I was even thinking on reinstalling the whole OS. But, thanks to you, now I have sound.
wp

Glad you're fixed up...BTW, I was quoting markbuntu, I am not him

---

### Post by williepabon on 2010-10-17
Lidex:
Sorry about the confusion. Thanks again.
wp

---

