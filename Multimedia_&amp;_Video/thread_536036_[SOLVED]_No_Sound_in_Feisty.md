---
title: "[SOLVED] No Sound in Feisty"
date: 2007-08-27
forum: Multimedia &amp; Video
---

### Post by eosha on 2007-08-27
Just installed Feisty, and sound doesn't work. I've poked through the forums and tried everything I've seen, but no success.

Things I've tried:
speakers are plugged in and work
volume's up
alsamixer isn't muted
alsamixer IEC channel is muted
every combination of things in Sound-Devices (none of the Tests work)
purging/reinstalling linux-sound-base alsa-base alsa-utils
I've tried getting sound from Rhythmbox, mpg123 and mplayer, as a normal user or root.

aplay -l yields:

```
**** List of PLAYBACK Hardware Devices ****
card 0: SIS966 [HDA SIS966], device 0: ALC861VD Analog [ALC861VD Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SIS966 [HDA SIS966], device 1: ALC861VD Digital [ALC861VD Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

lspci -v yields:

```
00:0f.0 Audio device: Silicon Integrated Systems [SiS] Azalia Audio Controller
        Subsystem: Foxconn International, Inc. Unknown device 0c99
        Flags: bus master, medium devsel, latency 0, IRQ 22
        Memory at fdff4000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
```

I'm out of ideas... help?

---

### Post by jnorthr on 2007-08-27
Can you play a music CD ? Does the menu bar show a speaker ? Does the speaker icon look mute ? It really should play something out-of-the-box, not .mp3 and some video DVD's as these typically need further downloas to make them work.
Look here for ideas : [https://answers.launchpad.net/medibuntu](https://answers.launchpad.net/medibuntu)  and [https://launchpad.net/medibuntu/](https://launchpad.net/medibuntu/)  and the HowTo here: [http://www.medibuntu.org/](http://www.medibuntu.org/)

---

### Post by fmhoyt on 2007-08-27
I have a very similar problem. 

I have installed Feisty Fawn on a new Thinkpad T61. There is no sound *except* when the system beep sounds. In other words, if I am playing audio (CD, Realaudio, etc) I only hear the music when the System Beep also goes off. For example, if I do a Find in Firefox and hold down a character key, I can hear the music just fine.  This happens with a fresh install of Feisty.  

I have gone through the Ubuntu Community [Sound Troubleshooting ]("https://help.ubuntu.com/community/SoundTroubleshooting#head-083f68c150e8cc9de635a7ab89b8ccfc6100ecf8") and [Debugging Sound Problems]("https://help.ubuntu.com/community/DebuggingSoundProblems")  pages without finding a solution. 

I have also tried installing the most recent ALSA driver and support software without it making a difference. 

The problem has nothing to do with the computer waking from sleep (I have seen discussion of a bug involving that): it happens after a full startup. 

Here's the configuration: 

Thinkpad T61, 4gb RAM, 2.0ghz Intel Centrino Duo.
Sound card:
Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)

Thanks for any help.

---

### Post by eosha on 2007-08-27
Yes, the system bar shows a speaker, volume's at full. I just booted from an old Ubuntu 6.06 CD I had around, and the sound card was autodetected and worked fine (played some OGGs). So I know it's not a hardware issue...

System beep works (a separate subsystem), but no login sound or anything else like that.

I've got all the w32 and libdvdcss codecs installed. OGGs in Rhythmbox don't work either.

---

### Post by maqifrnswa on 2007-08-27
Hi - i have pretty much the same thing as the original poster. It used to work prior to fiesty upgrade, haven't used my laptop (IBM T22) since upgrading, and now noticing the sound is gone.

From the original poster:
Things I've tried:
speakers are plugged in and work (dual boot windows and they work there)
volume's up (checked)
alsamixer isn't muted (checked)
alsamixer IEC channel is muted (checked)
every combination of things in Sound-Devices (I checked and none of the tests work for me either)
purging/reinstalling linux-sound-base alsa-base alsa-utils (I did this too)
I've tried getting sound from Rhythmbox, mpg123 and mplayer, as a normal user or root. (yes, both as root and user)




alsamixer doesn't have master muted, the speaker icon in the top right corner doesn't have an mute symbol.

lspci -v
```
00:05.0 Multimedia audio controller: Cirrus Logic CS 4614/22/24/30 [CrystalClear SoundFusion Audio Accelerator] (rev 01)
        Subsystem: IBM ThinkPad A20m
        Flags: bus master, slow devsel, latency 64, IRQ 11
        Memory at e8122000 (32-bit, non-prefetchable) [size=4K]
        Memory at e8000000 (32-bit, non-prefetchable) [size=1M]
        Capabilities: <access denied>

```

aplay -l
```
**** List of PLAYBACK Hardware Devices ****
card 0: CS46xx [Sound Fusion CS46xx], device 0: CS46xx [CS46xx]
  Subdevices: 29/31
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
card 0: CS46xx [Sound Fusion CS46xx], device 1: CS46xx - Rear [CS46xx - Rear]
  Subdevices: 31/31
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
card 0: CS46xx [Sound Fusion CS46xx], device 2: CS46xx - IEC958 [CS46xx - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

i've searched a bit on the internet and these forums, haven't found anything besides than "sudo modprobe snd-cd46xx" Any help would be appreciated - thanks



EDIT:
I got sound back... don't know which of these two did it but:
1) alsamixer and unmuted everything (except for IEC)
2) in "system"->"administration"->"services" the alsa audio settings management was unchecked, I checked it to load

---

### Post by eosha on 2007-08-28
ALSA audio was unchecked in "system"->"administration"->"services", but it still doesn't work...

---

### Post by okkie on 2007-08-28
my computer says type'deb' is not known on line 57 in source list list of sources could not be read.
probably the reason for 'no sound' can anyone help?

---

### Post by asheish on 2007-08-28
I have the same problem. I have installed feisty and the sound is not working

lspci -v

 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
 Subsystem: Lenovo Unknown device 384e
 Flags: bus master, fast devsel, latency 0, IRQ 22
 Memory at f8300000 (64-bit, non-prefetchable) [size=16K]
 Capabilities: <access denied>

---

### Post by fmhoyt on 2007-08-28
I seem to have fixed the problem (knocking on wood...), using one of the procedures on [this page]("http://thinkwiki.org/wiki/Installing_Ubuntu_7.04_%28Feisty_Fawn%29_on_a_ThinkPad_T61#ALSA_driver_update_.28hard_fix.2C_recommended_for_advanced_users.29"), which itself refers [to a discussion of similar problems]("http://forums.fedoraforum.org/showthread.php?t=159516&page=1&pp=15") with a Fedora installation on a Thinkpad. 

I went with the solution that was medium-complicated (the easier one was a python hack). The essentials are as follows: 

First, do the following in a terminal: 
 
$ sudo apt-get install build-essential linux-headers-$(uname -r)

This is necessary for the rest of the procedure: 

Download [path_analog.c]("http://forums.fedoraforum.org/attachment.php?attachmentid=12630")   and the [alsa driver package]("ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.14.tar.bz2") to your desktop (or wherever). 

Doubleclick on patch_analog.c.tar.gz and alsa-driver-1.0.14.tar.bz2 to extract them.

Once it's extracted, do the following: 

$ cd alsa-driver-1.0.14
$ cp ../patch_analog.c alsa-kernel/pci/hda/
$ ./configure && make
$ sudo make install
$ sudo echo options snd-hda-intel index=0 model=thinkpad >> /etc/modprobe.d/options

Once you've done all this, reboot your computer and try playing a CD after you check the following: 

Double-click the Volume Control icon and look at "Switches" to make sure that Speaker is checked; 
Still looking at the Volume Control panel, make sure that PCM is not muted; 
Under System > Administration > Services make sure that Audio Services Management is checked; 
One the music starts playing, adjust the volume using the buttons on the keyboard. 

Good Luck

---

### Post by eosha on 2007-08-29
That did it! Sound works fine now.

I didn't need ```
$ sudo echo options snd-hda-intel index=0 model=thinkpad >> /etc/modprobe.d/options

```, since I don't have a thinkpad. 

Thanks a lot for your help (and clear instructions!)

---

### Post by asheish on 2007-08-29
Didnt work for me :(

---

### Post by fmhoyt on 2007-08-30
There's an even easier and better solution: update your kernel to the most recent version. 

Here's [a thread about how to do this]("http://ubuntuforums.org/showthread.php?t=511974") that includes a shell script that automates the whole process. 

Here's what you do: 

Download   to your desktop. 

Then do the following in a terminal: 

$ cd ~/Desktop
$ chmod +x kernel.sh
$ sudo ./kernel.sh 

That's all. You'll see a couple of dialog prompts requesting confirmation that you want to proceed, and you'll have to reboot when it's done. 

I did this and my computer started making noises that I didn't know it could make (like music at start up). And unless I'm mistaken applications are loading faster. Highly recommended.

---

### Post by asheish on 2007-08-30
I tried the new kernel and my display card also stopped working

its NVIDIA 8400M GS


Is there any other solution to get sound working....

---

### Post by Clint07 on 2007-10-08
> **fmhoyt said:**
> I seem to have fixed the problem (knocking on wood...), using one of the procedures on [this page]("http://thinkwiki.org/wiki/Installing_Ubuntu_7.04_%28Feisty_Fawn%29_on_a_ThinkPad_T61#ALSA_driver_update_.28hard_fix.2C_recommended_for_advanced_users.29"), which itself refers [to a discussion of similar problems]("http://forums.fedoraforum.org/showthread.php?t=159516&page=1&pp=15") with a Fedora installation on a Thinkpad. 

I went with the solution that was medium-complicated (the easier one was a python hack). The essentials are as follows: 

First, do the following in a terminal: 
 
$ sudo apt-get install build-essential linux-headers-$(uname -r)

This is necessary for the rest of the procedure: 

Download [path_analog.c]("http://forums.fedoraforum.org/attachment.php?attachmentid=12630")   and the [alsa driver package]("ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.14.tar.bz2") to your desktop (or wherever). 

Doubleclick on patch_analog.c.tar.gz and alsa-driver-1.0.14.tar.bz2 to extract them.

Once it's extracted, do the following: 

$ cd alsa-driver-1.0.14
$ cp ../patch_analog.c alsa-kernel/pci/hda/
$ ./configure && make
$ sudo make install
$ sudo echo options snd-hda-intel index=0 model=thinkpad >> /etc/modprobe.d/options

Once you've done all this, reboot your computer and try playing a CD after you check the following: 

Double-click the Volume Control icon and look at "Switches" to make sure that Speaker is checked; 
Still looking at the Volume Control panel, make sure that PCM is not muted; 
Under System > Administration > Services make sure that Audio Services Management is checked; 
One the music starts playing, adjust the volume using the buttons on the keyboard. 

Good Luck

For the past hour I've been trying to cd alsa-driver-1.0.14 but no luck.. I'm kind of new here and the files are located on my desktop.. Can anyone help me?

---

### Post by uflieven on 2007-10-22
Clint07, in the following command replace username with the name you use to login.

cd /home/username/Desktop/alsa-driver-1.0.14

Please note: Desktop has a capital D, not just a d.

This should work.

---

### Post by trjnhrse44 on 2007-10-23
Hey all, if you have the ICH8 Chipset (and some others im not exactly sure which ones) you dont have to compile or build from source anything, the fix is in the repos!
Just enable the backports and install linux-backports-modules, I have posted detailed instructions in this thread: [http://ubuntuforums.org/showthread.php?t=565873&page=2](http://ubuntuforums.org/showthread.php?t=565873&page=2)

If you have built a custom kernel or compiled alsa from source this may not work for you!

---

### Post by pikmaster on 2008-01-11
For me it helped to add this entry to /etc/modprobe.d/alsa-base:
```
options snd-hda-intel model=lenovo
```
Although I don't have a Lenovo notebook but a Packard-Bell Easynote MX37-T-003.

Before (without this entry), the card was detected, but there was no sound (unmuting did not help)

**lspci -v**
00:0f.0 Audio device: Silicon Integrated Systems [SiS] Azalia Audio Controller
        Subsystem: Unknown device 1631:c10b
        Flags: bus master, medium devsel, latency 0, IRQ 21
        Memory at fddf4000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2


**aplay -l**
**** List of PLAYBACK Hardware Devices ****
card 0: SIS966 [HDA SIS966], device 0: ALC861VD Analog [ALC861VD Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

