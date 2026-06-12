---
title: "Sound not working on Ubuntu 10.04"
date: 2010-05-12
forum: Multimedia Software
---

### Post by lkjoel on 2010-05-12
I got Ubuntu 10.04 and the sound is not working.

I did read this post ([https://lists.ubuntu.com/archives/ubuntu-users/2010-May/217641.html]("https://lists.ubuntu.com/archives/ubuntu-users/2010-May/217641.html")) telling me that I should remove PulseAudio.
I went on the Synaptic Package Manager, and it wanted me to remove ubuntu-desktop.

And one other thing. I don't know what is my sound cards name.
Is there any tools to help me find it?

Could any of you help me?

Thanks a lot!

---

### Post by lidex on 2010-05-13
Need more info. Is this an upgrade or clean install? 
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
Please post text output using code tags. *_Also helpful is the make/model of your PC/Laptop._*

---

### Post by lkjoel on 2010-05-13
Ok. We had a Ubuntu 8.10, then we installed Ubuntu 10.04, and made it so it would take over Ubuntu 8.10. So no more 8.10.

For the uname -a command:
```
Linux titgars-UB-10 2.6.32-22-generic-pae #33-Ubuntu SMP Wed Apr 28 14:57:29 UTC 2010 i686 GNU/Linux
```

For the aplay -l command:
```
**** List of PLAYBACK Hardware Devices ****
card 0: ICH5 [Intel ICH5], device 0: Intel ICH [Intel ICH5]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH5 [Intel ICH5], device 4: Intel ICH - IEC958 [Intel ICH5 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

For the cat /proc/asound/version command:
```
Advanced Linux Sound Architecture Driver Version 1.0.21.
```

For the head -n 1 /proc/asound/card*/codec#* command:
```
head: cannot open `/proc/asound/card*/codec#*' for reading: No such file or directory
```

And also, I have seen your ALSA Info Script and this is the webpage: [http://www.alsa-project.org/db/?f=ad2a74b151fa06c19705ff33f4b8cb551a79b7e8]("http://www.alsa-project.org/db/?f=ad2a74b151fa06c19705ff33f4b8cb551a79b7e8")

Ok and the make/model: It has Intel, and I think it is an ASUS Motherboard. Not sure though.

It says on the front: Macrotronics custom systems, so this might be a little more complicated.

Would the Boot Info script on your signature help for me to find the model?

Thanks again!

---

### Post by lkjoel on 2010-05-13
Oh and I forgot, if this is of any help:

The system architecture is: i686.

And I did uninstall PulseAudio, but then I installed ubuntu-desktop back.;-)

---

### Post by Jimbo8098 on 2010-05-13
I know this is gonna sound real bad but did you remember to unmute the volume using the lilk loudspeaker on the top bar? You need to click it then click unmute and set your volume.

I know that sounds insulting but seriously the amount of times people i know have done it would scare you XD

---

### Post by lkjoel on 2010-05-13
Yes, I did check it. It is on high. (Internal and "Outernal")

---

### Post by lidex on 2010-05-13
Yeah, go here and do 'Part A':
[http://ubuntuforums.org/showthread.php?t=789578]("http://ubuntuforums.org/showthread.php?t=789578")

Next use the alsa upgrade link in my sig to upgrade alsa. You have mismatched alsa components.

---

### Post by lkjoel on 2010-05-14
Thanks but... when I type:
```
aplay -l
```this is what I get:
```
aplay: device_list:235: no soundcards found...
```when I type:
```
cat /proc/asound/version
```this is what I get:
```
Advanced Linux Sound Architecture Driver Version 1.0.22.1.
Compiled on May 12 2010 for kernel 2.6.32-22-generic-pae (SMP).

```when I type:
```
aplay
```this is what I get:
```
ALSA lib confmisc.c:768:(parse_card) cannot find card '0'
ALSA lib conf.c:4154:(_snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:4154:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib conf.c:4154:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:4633:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default
aplay: main:654: audio open error: No such file or directory
```Could you please help this new problem?

Thanks a lot!

(Later, edited post)
I am just restoring the original version of ALSA.
It is really not working

---

### Post by optimusmedia on 2010-05-14
I had the same issue (still have a minor issue) but was able to fix this by doing the following: 

```
sudo gedit /etc/modprobe.d/alsa-base.conf 

```

Then adding the following line to the bottom ```
options snd-hda-intel model=acer
```

Reboot and it worked (everywhere except flash in firefox). 

Suitable options for other models can be found in [this forum thread]("http://ubuntuforums.org/showthread.php?t=1043568").

I hope that helps!

Ron

---

### Post by lkjoel on 2010-05-14
I know, but is it possible to have more than one model, so then if one doesn't work, the rest can work?
Here is all that I added by forum posts:
```
options snd-intel8x0 ac97_quirk=1 buggy_irq=1 enable=1 index=0
options snd-hda-intel model=3stack enable=yes
options snd-hda-intel model=auto position_fix=1 enable=yes
options snd-hda-intel enable_msi=1
options snd_hda_intel model=hp-dv5
options snd-hda-intel model=5stack
```So, should I remove them all, and get only the one I need, or should I keep them all?

Thanks!

Oh and one other thing...
I do not know what the model of my computer is.
It is a desktop computer, saying Macrotronics custom systems on the front.
Should I use the motherboard type??

I think they should make Ubuntu 10.05, fixing all those problems:-)

---

### Post by optimusmedia on 2010-05-14
Yes, only use one "options snd-hda-intel model=______" at a time.

---

### Post by lkjoel on 2010-05-14
Since I do not know my computer model, since it was a custom system, should I get the motherboard model? (ASUS)

Thanks!

---

### Post by lidex on 2010-05-14
Remove all the entries you added to alsa-base.conf
Now click on the alsa-upgrade-script link in my sig and follow directions there to upgrade alsa. After you reboot check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default.

---

### Post by lkjoel on 2010-05-17
I tried to do that /etc/modprobe.d/alsa-base.conf thing.
I added:
```
options snd-intel8x0 model=asus
```
Our model is not asus, but the motherboard is.

So this is what I get when I type:

```
aplay -l
```
```
aplay: device_list:235: no soundcards found...

```

And this is what I get when I type:

```
cat /proc/asound/version
```
```
Advanced Linux Sound Architecture Driver Version 1.0.22.1.
Compiled on May 14 2010 for kernel 2.6.32-22-generic-pae (SMP).

```

Also, Alsamixer won't work.
This is what I get

```
cannot open mixer: No such file or directory

```

Should logs of the downloading/compiling/installation processes help?

---

### Post by lidex on 2010-05-17
Your system uses the AC97 codec, not snd-hda-intel. More specifically your codec is snd-intel8x0. You can't use the hda options with the AC97 codec. The first line of custom entries you posted previously is valid, all others are not. Go ahead and try it with just that one line and report your results.
```
options snd-intel8x0 ac97_quirk=1 buggy_irq=1 enable=1 index=0

```

---

### Post by lkjoel on 2010-05-18
It did not work.
Attached is the complete "/etc/modprobe.d/alsa-base.conf" (alsa-base.conf.bz2)
I forgot to make a backup.

---

### Post by lidex on 2010-05-18
OK. Remove that entry from alsa-base.conf
Now this:
```
sudo apt-get update
sudo apt-get upgrade
```
```
sudo apt-get install --reinstall alsa-utils alsa-oss alsa-base libasound2 libasound2-plugins linux-sound-base gstreamer0.10-alsa
```
Reboot.

---

### Post by wheniwork on 2010-05-30
Moved my issue to here since my issue is "flakey" sound not "no" sound.
[http://ubuntuforums.org/showthread.php?p=9386212](http://ubuntuforums.org/showthread.php?p=9386212)

I'm having some sound problems in 10.4 too. I'm using the SPDIF digital audio out.

I can hear the startup sound when the system boots. But other apps (like, mythfrontend, boxee, etc) that play media don't play audio consistently. Sometimes if I set the audio device in myth or boxee to default and then restart the app and set the audio device to IEC958 the audio will work for a bit, but then stop again.

Also, when I have the audio device in boxee set to IEC958 I get the boxee startup sound everytime, but no audio or static audio on all video file playback. 

No audio on internet content either via flash in you tube, etc.

Here's my alsa information. Any thoughts? Thanks in advance.

[http://www.alsa-project.org/db/?f=94461426e9e803fa2630165783674e64ea00498a](http://www.alsa-project.org/db/?f=94461426e9e803fa2630165783674e64ea00498a)

---

### Post by lkjoel on 2010-05-30
My sound works!!!
Thanks all for all your help!!!

Just to recap, here were the issues and the steps taken to resolve.

1) Check if soundcard is detected.
2) Uninstall (purge) ALSA and ALSAMIXER.  The latter didn’t work even through the terminal. Then reinstall via Synaptics
3) Disable Pulse Audio
aplay -l works!! But...
still nothing! I suspected a faulty soundcard so I yanked one from an old computer and installed it. Voilà!  But...
No sound with Flash!

I tried to fix the flash audio, but I broke aplay -l.

So I switched to OSS. My sound works now!!!:guitar:

[https://help.ubuntu.com/community/OpenSound]("https://help.ubuntu.com/community/OpenSound") really helped me to install it.


Again thank you all who contributed to resolving this issue.  

I hope this can help someone else!

---

### Post by lidex on 2010-05-31
> **wheniwork said:**
> Moved my issue to here since my issue is "flakey" sound not "no" sound.
[http://ubuntuforums.org/showthread.php?p=9386212](http://ubuntuforums.org/showthread.php?p=9386212)

I'm having some sound problems in 10.4 too. I'm using the SPDIF digital audio out.

I can hear the startup sound when the system boots. But other apps (like, mythfrontend, boxee, etc) that play media don't play audio consistently. Sometimes if I set the audio device in myth or boxee to default and then restart the app and set the audio device to IEC958 the audio will work for a bit, but then stop again.

Also, when I have the audio device in boxee set to IEC958 I get the boxee startup sound everytime, but no audio or static audio on all video file playback. 

No audio on internet content either via flash in you tube, etc.

Here's my alsa information. Any thoughts? Thanks in advance.

[http://www.alsa-project.org/db/?f=94461426e9e803fa2630165783674e64ea00498a](http://www.alsa-project.org/db/?f=94461426e9e803fa2630165783674e64ea00498a)

Firstly, you're booting into an old kernel. There are other issues as well. Follow these steps:
Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Remove all the custom entries you added. Save. Close.

Back in the terminal:
```
sudo apt-get update
sudo apt-get upgrade
sudo update-grub
```
**Reboot** into latest kernel.

Now follow the alsa-upgrade link in my sig to update your alsa install.

Report your results. Also make/model of your PC/laptop.

---

### Post by wheniwork on 2010-05-31
I ran the update-grub thing and I'm not sure my kernel is right yet. It says 10.04 when I boot up, but the grub menu list still says 9.10. When I log in via SSH I get this greeting message showing the kernel.

```
Linux cinema 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686 GNU/Linux
Ubuntu 10.04 LTS
```

Also, when running the alsa script I get this on step 5:

```
***************************************************************************
*  Alsa packages(drivers/lib/util/firmware/oss) will be compiled
***************************************************************************

***************************************************************************
*  Prepare for compilation and installation...
***************************************************************************

***************************************************************************
*  Compiling drivers...
***************************************************************************
rm -f .depend *.o snd.map*
rm -f modules/*.o modules/*.ko
make[1]: Entering directory `/usr/src/Alsa-1.0.23/alsa-driver-1.0.23/include'
Makefile:6: ../Makefile.conf: No such file or directory
make[1]: *** No rule to make target `../Makefile.conf'.  Stop.
make[1]: Leaving directory `/usr/src/Alsa-1.0.23/alsa-driver-1.0.23/include'
make: *** [clean] Error 1
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for ranlib... ranlib
checking for a BSD-compatible install... /usr/bin/install -c
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking whether time.h and sys/time.h may both be included... yes
checking whether gcc needs -traditional... no
checking for current directory... /usr/src/Alsa-1.0.23/alsa-driver-1.0.23
checking cross compile... 
checking for directory with ALSA kernel sources... ../alsa-kmirror
checking for directory with kernel source... Please install the package with full kernel sources for your distribution
or use --with-kernel=dir option to specify another directory with kernel
sources (default is /usr/src/linux).

***************************************************************************
*  alsa-driver-1.0.23 configure failed
***************************************************************************

```

---

### Post by lidex on 2010-05-31
What is the output of;
```
uname -a
```

Mine is:
```
Linux lidex-lucid 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:28:05 UTC 2010 x86_64 GNU/Linux

```
Running lucid.
Are you using grub2 or legacy?

---

### Post by wheniwork on 2010-05-31
```
Linux cinema 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686 GNU/Linux

```

Not sure about grub. I think the legacy one. Whatever one came with 9.10 since that was the initial install. Would it be better if I just installed clean with 10.04? The only thing I have configured is LIRC and I can backup the conf files.

However, I was having the same sound issue with 9.10. :(

---

### Post by lidex on 2010-05-31
Output of this please:
```
grub-install -v
```

---

### Post by wheniwork on 2010-05-31
```
grub-install (GNU GRUB 0.97)

```

---

### Post by lidex on 2010-05-31
Go to this section:
'Upgrading to GRUB 2'
of this page:
[https://help.ubuntu.com/community/Grub2]("https://help.ubuntu.com/community/Grub2")
Follow the instructions there. Grub2 should be able to update and recognize your installed OS's and kernels. Once you're in the right kernel for lucid we can fix sound issues. Shouldn't need to reinstall ubuntu.

---

### Post by wheniwork on 2010-06-05
OK Grub 2 installed and things are looking up to date. Same sound issues preside.
```
Linux cinema 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:27:30 UTC 2010 i686 GNU/Linux

```

---

### Post by lidex on 2010-06-05
> **wheniwork said:**
> OK Grub 2 installed and things are looking up to date. Same sound issues preside.
```
Linux cinema 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:27:30 UTC 2010 i686 GNU/Linux

```

OK. Try the upgrade script again.

---

### Post by wheniwork on 2010-06-05
Ok. ALSA Upgraded.

```
Advanced Linux Sound Architecture Driver Version 1.0.23.
Compiled on Jun  5 2010 for kernel 2.6.32-22-generic (SMP).

```

Same issue with static/distorted audio on some media content. Tested WAVs with aplay and startup sound works fine.

Checked the alsa-mixer and levels are up an unmuted. 

I noticed the default settings don't work anymore for audio. I need to force things to use iec958 for OUTPUT and PASSTHROUGH. Also, not getting UI sounds in boxee like I was before.

What's next?

---

### Post by wheniwork on 2010-06-05
And here is the updated alsa info output.

[http://www.alsa-project.org/db/?f=ecd68b60c64d9419d7cda2b872dc9abf8f62b38d](http://www.alsa-project.org/db/?f=ecd68b60c64d9419d7cda2b872dc9abf8f62b38d)

---

### Post by lidex on 2010-06-05
Make and model please. Also number of audio jacks analog? Digital?

---

### Post by wheniwork on 2010-06-05
Is this what you need? I'm using the digital optical audio out (SPDIF). Nothing analog is plugged in to the PC

```

null
    Discard all samples (playback) or generate zero samples (capture)
default:CARD=Intel
    HDA Intel, AD198x Analog
    Default Audio Device
front:CARD=Intel,DEV=0
    HDA Intel, AD198x Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, AD198x Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, AD198x Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, AD198x Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, AD198x Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, AD198x Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Intel,DEV=0
    HDA Intel, AD198x Digital
    IEC958 (S/PDIF) Digital Audio Output
```


Or

```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

---

### Post by lidex on 2010-06-05
> **wheniwork said:**
> Is this what you need? I'm using the digital optical audio out (SPDIF). Nothing analog is plugged in to the PC


No. I am referring to the actual number of physical jacks and manufacturer/model of PC (or motherboard if homemade).

---

### Post by wheniwork on 2010-06-05
Here's the motherboard I have.

[http://www.newegg.com/Product/Product.aspx?Item=N82E16813131371](http://www.newegg.com/Product/Product.aspx?Item=N82E16813131371)

---

### Post by lidex on 2010-06-06
Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=6stack-dig 
```
Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default.

---

### Post by wheniwork on 2010-06-06
Did that. Still same scenario. System sounds play, but multimedia files do not play sound at all or are just play static/distorted.

---

### Post by lkjoel on 2010-06-06
Why don't you try OSS?
It is not deprecated, anyhow 4.x is not.
I use it and I am listening to music

I had the same issue.  After several attempts at troubleshooting I found that
1) my audio card wasn't working
2) PulseAudio and ALSA were conflicting
3) ALSA was corrupted
After installing a new card and resolving conflicts and corruption (sounds like in a movie), the final resolution was using OSS which is still supported and works like a charm.

For instructions on how to install it, go to [https://help.ubuntu.com/community/OpenSound]("https://help.ubuntu.com/community/OpenSound")

If the sound doesn't go on after installing it, and rebooting the system, just type
```
sudo soundon
```
If you see an error message, try
```
sudo rm /usr/lib/oss/starting
sudo soundon
```

---

### Post by lidex on 2010-06-06
If system sounds play, then I would surmise your base sound system is operable. What programs have you tried for playing media files? 

Try this:
```

rm -r ~/.pulse ~/.asound* 
sudo rm /etc/asound.conf
```
Logout/in.

'Part 1' here:
[http://ubuntuforums.org/showthread.php?t=766683]("http://ubuntuforums.org/showthread.php?t=766683")

Follow this howto:
[https://help.ubuntu.com/community/RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats")

---

### Post by jayemee on 2010-07-23
Just to weigh in with my two cents:

I was having the same (or very similar) problem, could only get audio output from one program at a time (which manifested itself most annoyingly while having amarok going in the background then wanting to watch a flash video or dvd or something). I tried all kinds of combinations of enabling/disabling puiseaudio and ALSA (not made easier by most of the tutorials seemingly not geared towards lucid, and me not being competent enough to know  what to tweak).

Just installed OSS as described earlier in this thread, and now programs seem to happily play sound simultaneously :)


Jme

---

### Post by Frisbee catcher on 2010-09-17
Hi,

I'm ultra new with Ubuntu having been a long time Win/XP user, decided to go in at the deep end and wipe everything from my laptop and start afresh with something different (after doing a backup just in case).

I installed Ubuntu 10.04, ran updates and spent many an hour trouble shooting the various issues that I came across, the one thing that has left me stumped is that I don't seem to have any sound from the speakers any more, I discovered that if I plug in a set of headphones that I do have sound - but only mono.

I have tried a few different suggestions that looked relevant from googling around but they haven't worked so far. 

I believe I have the latest version of GNOME ALSA Mixer installed.
My laptop is an Acer Aspire 9802WKMi.
Not sure what my soundcard is - is there a command I can put in the terminal that will tell me?

Not sure where the starting point is, but if some nice person could walk me through what I need to do to troubleshoot/fix this annoying problem I would be really really grateful.

Looking forward to learning more about Linux as I go - hate being a newbie!

Thanks in advance.

---

### Post by Frisbee catcher on 2010-09-17
Update on last post - 

I read from a previous entry in this thread that Pulse Audio can conflict with ALSA, so I looked for a way to completely uninstall it.

Entered the following into the terminal: 
sudo apt-get autoremove pulseaudio

(I'm not sure that it works on anything older than 10.04)

Upon re-booting my machine, I got sound coming externally at last! - BUT (always a but) the sound is still mono (certainly the headphones are still mono).

I wondered if it was a setting on the mixer, but I cant see anything that suggests the sound only being channelled through one speaker.
I also tried going to System>Preferences>Sound - to see if I could configure anything there, but a message pops up saying 'Waiting for sound system to respond' (along with the option to Cancel the box) 

I guess I'm one step closer now, but not quite there yet.

Any help greatly appreciated.

---

### Post by lidex on 2010-09-17
> **Frisbee catcher said:**
> Update on last post - 

I read from a previous entry in this thread that Pulse Audio can conflict with ALSA, so I looked for a way to completely uninstall it.

Entered the following into the terminal: 
sudo apt-get autoremove pulseaudio

(I'm not sure that it works on anything older than 10.04)

Upon re-booting my machine, I got sound coming externally at last! - BUT (always a but) the sound is still mono (certainly the headphones are still mono).

I wondered if it was a setting on the mixer, but I cant see anything that suggests the sound only being channelled through one speaker.
I also tried going to System>Preferences>Sound - to see if I could configure anything there, but a message pops up saying 'Waiting for sound system to respond' (along with the option to Cancel the box) 

I guess I'm one step closer now, but not quite there yet.

Any help greatly appreciated.

Removing pulse probably more of a last ditch effort than a troubleshooting step. I would re-install it, then this: Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Enter your user password when prompted. Choose the upload option and provide a link for the output.

---

### Post by Frisbee catcher on 2010-09-18
Hi Lidex,

Thankyou for responding to my query so fast (I've read this about the Ubuntu community!)

I re-installed pulse audio as you suggested and used the code provided - here is the link:

[http://www.alsa-project.org/db/?f=0093d021305b609c835dad2132aeeb447ce2acb2](http://www.alsa-project.org/db/?f=0093d021305b609c835dad2132aeeb447ce2acb2) .

My sound has gone mute again, but am happy to go with it for now if its a necessary step.

Thanks again for your help on this.

---

### Post by lidex on 2010-09-18
> **Frisbee catcher said:**
> Hi Lidex,

Thankyou for responding to my query so fast (I've read this about the Ubuntu community!)

I re-installed pulse audio as you suggested and used the code provided - here is the link:

[http://www.alsa-project.org/db/?f=0093d021305b609c835dad2132aeeb447ce2acb2](http://www.alsa-project.org/db/?f=0093d021305b609c835dad2132aeeb447ce2acb2) .

My sound has gone mute again, but am happy to go with it for now if its a necessary step.

Thanks again for your help on this.

Try upgrading your alsa install using the link in my sig. Once that's done, post this output:
```
dmesg | grep -C1 -E 'ALSA|HDA|HDMI|sound|hda.codec|hda.intel'
```

---

### Post by Frisbee catcher on 2010-09-19
Hi Iidex,

Ok, I think everything seemed to install without a hitch.

I entered the command that you asked - but didn't give me the option of uploading it like the last time, so I saved the contents and attached the file 'Output' here.

I haven't played about with it much yet but I noticed that there was a suggestion to test if "aplay" is working, as if it doesn't work then nothing else would.

It said to enter into a terminal, the command

$ aplay -l

I copied this directly from the text into my terminal so as make sure i didn't confuse the '-l' part with a 1 or a capital 'i' - but I got a message saying 'command not recognised' just the same.

I'll continue doing some 'hopefully' non-destructive tinkering in the meantime, but look forward to your comments on the 'Output' file and any further suggestions you have.

Thanks

---

### Post by Frisbee catcher on 2010-09-19
Ok, hopefully I've got the right attachment file-type this time!

- Learning all the time. . .

---

### Post by lidex on 2010-09-19
> **Frisbee catcher said:**
> Ok, hopefully I've got the right attachment file-type this time!

- Learning all the time. . .
Post these outputs please:

```
sudo fuser -v /dev/dsp* /dev/snd/* /dev/seq*
```

```
sudo dmidecode -t bios
sudo dmidecode -t baseboard

```

---

### Post by Frisbee catcher on 2010-09-19
I've attached the latest outputs as requested.

The first one didn't seem to do anything but the others brought back some results - see what you think.

Thanks again for taking the time to help with this.

---

### Post by lkjoel on 2010-09-19
> **Frisbee catcher said:**
> I've attached the latest outputs as requested.

The first one didn't seem to do anything but the others brought back some results - see what you think.

Thanks again for taking the time to help with this.
I think I see the problem.
When you typed in:
```
sudo dmidecode -t baseboard

```
it responded:
```
Base Board Information
	Manufacturer: Acer
	Product Name: Cheela
	Version: Not Applicable
	Serial Number: Not Applicable

Handle 0x000E, DMI type 10, 6 bytes
On Board Device Information
	Type: Sound
	**_Status: Disabled_**
	Description: ADI

```
It says that you sound card is disabled.
Lidex can catch me on this though!

---

### Post by Frisbee catcher on 2010-09-19
Hi Ikjoel,

Yeah, I spotted that as well, not that I would have the first idea how to enable it though!

Looking forward to a solution!

Thanks for taking an interest

---

### Post by lkjoel on 2010-09-19
> **Frisbee catcher said:**
> Hi Ikjoel,

Yeah, I spotted that as well, not that I would have the first idea how to enable it though!

Looking forward to a solution!

Thanks for taking an interest
Have you checked that your soundcard is working properly?

---

### Post by Frisbee catcher on 2010-09-19
It was working perfectly before I wiped XP off and installed Ubuntu 10.04.

I had mono sound from headphones only after the initial install, then un-installed pulse audio and got mono sound out of the laptop speakers as well as headphones.

Under advice I've re-installed pulse audio - well you can see this from the thread.

Anyway, currently all sound is off - which as you've noticed is probably something to do with the soundcard being disabled. Though I'm sure its just part of the process - I'm happy to break some eggs if someone can help me make the omelette - to coin a phrase!

---

### Post by Frisbee catcher on 2010-09-19
I guess I should ask. . .

Is there a way I can test to see if its working in its current state?

---

### Post by consoleman on 2010-09-19
Hello.

I had this problem too. I was able to fix it by installing one single package. After I reinstalled ubuntu, I have this problem again, and cant remember what package was the one that made it work.  It was something along the lines of blahblaha-ALSAblaha-blahala-blahblah. 

Please help

---

### Post by consoleman on 2010-09-19
> **consoleman said:**
> Hello.

I had this problem too. I was able to fix it by installing one single package. After I reinstalled ubuntu, I have this problem again, and cant remember what package was the one that made it work.  It was something along the lines of blahblaha-ALSAblaha-blahala-blahblah. 

Please help


Found it! Install this:[B]

sudo apt-get install linux-backports-modules-alsa-lucid-generic[/B]

reboot, and there is sound again!

---

### Post by lidex on 2010-09-19
*Frisbee catcher:*
Please update your bios

---

### Post by Frisbee catcher on 2010-09-19
Hi Iidex,

Could you tell me how I do that please?

---

### Post by lidex on 2010-09-19
> **Frisbee catcher said:**
> Hi Iidex,

Could you tell me how I do that please?

Go to the acer website:
[http://www.acer.com/worldwide/support/download.htm](http://www.acer.com/worldwide/support/download.htm)
and enter the info to get to your product's page. There you can download the update file.

In US go here:
[http://us.acer.com/acer/service.do?LanguageISOCtxParam=en&miu10einu24.current.attN2B2F2EEF=3750&sp=page15e&ctx2.c2att1=25&miu10ekcond13.attN2B2F2EEF=3750&CountryISOCtxParam=US&ctx1g.c2att92=453&ctx1.att21k=1&CRC=2054404012](http://us.acer.com/acer/service.do?LanguageISOCtxParam=en&miu10einu24.current.attN2B2F2EEF=3750&sp=page15e&ctx2.c2att1=25&miu10ekcond13.attN2B2F2EEF=3750&CountryISOCtxParam=US&ctx1g.c2att92=453&ctx1.att21k=1&CRC=2054404012)

---

### Post by Frisbee catcher on 2010-09-19
Hi again,

Sorry to sound a bit newbish - but I went to the Acer website and got the option to download one of three different Bios'es.

one is for 'Bios_v2.14_Vista' - I didn't have Vista before so I guess its not that one?
second option is for 'Bios_v1.21_XP.Raid
Third and last option is for 'Bios_v1.21_XP.non-Raid

I guess it would be one of the last two - but would they be compatible with Ubuntu either way?
One thing that has my concern was the warning message that went with it...



[SIZE=2][COLOR=Red]Updating an incorrect  BIOS may cause harm to your system. We recomend that you only do this  after being instructed by one of our Customer Care representatives. By  using these updates you agree to accept the possibility of product  failure.[/COLOR][/SIZE]
Sorry if I'm being thick!

---

### Post by lidex on 2010-09-19
Go with the latest - you're not using windows.

---

### Post by filox on 2010-09-19
I'm relative new in Ubuntu. I installed it a month ago and sound was working with ok. But on Friday (I guess) there was an update and sound stopped working because Ubuntu doesn't recognize the sound card.
I read this but it didn't help: [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

I checked that sound modules are installed and that the sound card is physically installed and Ubuntu recognize it.

I get this information:

01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller
        Subsystem: ASUSTeK Computer Inc. Device 82f1
        Flags: bus master, fast devsel, latency 0, IRQ 10
        Memory at fbce8000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel modules: snd-hda-intel

In the tab "Output" of sound preferences I only get "Dummy Audio - *Stereo*" but it doesn't work.

My Motherboard is an ASUS M3a78-EM.

I upgraded ALSA to 1.0.23 with this procedure: [http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/](http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/)

I really don't know what to do.

Many thanks for your help.

---

### Post by Frisbee catcher on 2010-09-20
Iidex,

I downloaded the latest BIOS and now have a series of files that I can't install.

there are 4 x .dll files
1 x .INI, 1 x .vxd, 1 x .sys, 1 x .ROM, 1 x .HLP

theres also a readme and and an executable file - which is what I tried initially (had a hunch that the .exe wouldn't work on this system - which was right)

got message:

[COLOR=Red]Archive:  /home/dave/.cache/.fr-79D28y/BIOS_v2.14_Vista/SWinFlash.exe
[/home/dave/.cache/.fr-79D28y/BIOS_v2.14_Vista/SWinFlash.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
zipinfo:  cannot find zipfile directory in one of /home/dave/.cache/.fr-79D28y/BIOS_v2.14_Vista/SWinFlash.exe or
          /home/dave/.cache/.fr-79D28y/BIOS_v2.14_Vista/SWinFlash.exe.zip, and cannot find /home/dave/.cache/.fr-79D28y/BIOS_v2.14_Vista/SWinFlash.exe.ZIP, period.[/COLOR]

[COLOR=Black]Would you be able to suggest how I install these please?

Thanks for your perseverance with this/me! 
[/COLOR]

---

### Post by lkjoel on 2010-09-21
> **filox said:**
> ...
I upgraded ALSA to 1.0.23 with this procedure: [http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/](http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/)
...
You don't need to use that procedure.
Instead, use the [ALSA Upgrade Script]("http://ubuntuforums.org/showthread.php?t=1046137")

---

### Post by lkjoel on 2010-09-21
> **Frisbee catcher said:**
> Iidex,

I downloaded the latest BIOS and now have a series of files that I can't install.

there are 4 x .dll files
1 x .INI, 1 x .vxd, 1 x .sys, 1 x .ROM, 1 x .HLP

theres also a readme and and an executable file - which is what I tried initially (had a hunch that the .exe wouldn't work on this system - which was right)

got message:

[COLOR=Red]Archive:  /home/dave/.cache/.fr-79D28y/BIOS_v2.14_Vista/SWinFlash.exe
[/home/dave/.cache/.fr-79D28y/BIOS_v2.14_Vista/SWinFlash.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
zipinfo:  cannot find zipfile directory in one of /home/dave/.cache/.fr-79D28y/BIOS_v2.14_Vista/SWinFlash.exe or
          /home/dave/.cache/.fr-79D28y/BIOS_v2.14_Vista/SWinFlash.exe.zip, and cannot find /home/dave/.cache/.fr-79D28y/BIOS_v2.14_Vista/SWinFlash.exe.ZIP, period.[/COLOR]

[COLOR=Black]Would you be able to suggest how I install these please?

Thanks for your perseverance with this/me! 
[/COLOR]
Get WINE.
Instuctions here: [http://www.winehq.org/download/deb]("http://www.winehq.org/download/deb")

---

### Post by Frisbee catcher on 2010-09-21
Hi Ikjoel,

Thanks for the tip, I have now installed Wine, and can see that it will be a useful tool.

Attempted to run the 'SWinflash.exe' file with it and all looked quite promising - however, after specifying where I wanted the .BAK file saved, and told it where to find the new .ROM file from my system, I hit the 'Flash Bios' tab - got a list of warning - do's and don'ts - accepted these and . . .  

'Failed to Initialize Driver'
'Access Denied'
'Error Code 5'

and no further did I get :(

I have been investigating another thread as to how to go about Flashing my BIOS at [http://ubuntuforums.org/showthread.php?t=318789](http://ubuntuforums.org/showthread.php?t=318789) 

Unfortunately, I cant fit all my files within the tmp/cdr directory as it only allows 1.44mb - nor will it fit into the 2.88mb version that is also suggested.

- Found a suggestion to try booting it from a pen drive - will get one of those tomorrow and see what I can do.

Any suggestions in the meantime, please do let me know, I'll check this post again before committing to any new actions as I'm well aware now that getting this wrong can seriously upset my mainboard - wish me luck!

---

### Post by lkjoel on 2010-09-21
> **Frisbee catcher said:**
> Hi Ikjoel,

Thanks for the tip, I have now installed Wine, and can see that it will be a useful tool.

Attempted to run the 'SWinflash.exe' file with it and all looked quite promising - however, after specifying where I wanted the .BAK file saved, and told it where to find the new .ROM file from my system, I hit the 'Flash Bios' tab - got a list of warning - do's and don'ts - accepted these and . . .  

'Failed to Initialize Driver'
'Access Denied'
'Error Code 5'

and no further did I get :(

I have been investigating another thread as to how to go about Flashing my BIOS at [http://ubuntuforums.org/showthread.php?t=318789](http://ubuntuforums.org/showthread.php?t=318789) 

Unfortunately, I cant fit all my files within the tmp/cdr directory as it only allows 1.44mb - nor will it fit into the 2.88mb version that is also suggested.

- Found a suggestion to try booting it from a pen drive - will get one of those tomorrow and see what I can do.

Any suggestions in the meantime, please do let me know, I'll check this post again before committing to any new actions as I'm well aware now that getting this wrong can seriously upset my mainboard - wish me luck!
If you are really scared, go ask a professional to do it.
If you are going to do that, Good Luck!

---

### Post by lidex on 2010-09-21
> **filox said:**
> I'm relative new in Ubuntu. I installed it a month ago and sound was working with ok. But on Friday (I guess) there was an update and sound stopped working because Ubuntu doesn't recognize the sound card.
I read this but it didn't help: [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

I checked that sound modules are installed and that the sound card is physically installed and Ubuntu recognize it.

I get this information:

01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller
        Subsystem: ASUSTeK Computer Inc. Device 82f1
        Flags: bus master, fast devsel, latency 0, IRQ 10
        Memory at fbce8000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel modules: snd-hda-intel

In the tab "Output" of sound preferences I only get "Dummy Audio - *Stereo*" but it doesn't work.

My Motherboard is an ASUS M3a78-EM.

I upgraded ALSA to 1.0.23 with this procedure: [http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/](http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/)

I really don't know what to do.

Many thanks for your help.

Remove your pulse config files:
Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.pulse-cookie ~/.asound* 
sudo rm /etc/asound.conf
```

Reboot and post your results.

---

### Post by lkjoel on 2010-09-24
> **lidex said:**
> Remove your pulse config files:
Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.pulse-cookie ~/.asound* 
sudo rm /etc/asound.conf
```

Reboot and post your results.
If anyone here has OSS 4.x installed, you must install PulseAudio and ALSA.
To do so, follow this guide:

Edit /etc/pulse/default.pa and
Remove "module-hal-detect" (it won't detect OSS anyway).
Uncomment "module-oss" line and add "mmap=0" at end.
If "module-oss" line does not exist add the line below to default.pa:

load-module module-oss device="/dev/dsp" sink_name=output source_name=input mmap=0

You may wish to copy this file to ~/.pulse directory, so that it isn't overwritten by a package upgrade.

Then install ALSA the normal way.

---

### Post by mihir.gupte on 2010-09-25
Hi, 

I installed Ubuntu 10.04 (64-bit) couple days ago and later was searching for flash plugin. Finally when I installed the plugin, i learn that sound is not working. As i said, i just installed Ubuntu few days back, im new to this and can anybody help me with the sound problem?

---

### Post by Frisbee catcher on 2010-09-25
Hi Ikjoel and Iidex,

I spent a long time trying to figure out how to get my BIOS updated, all methods I tried out to do this within a Linux environment failed - and I tried a few of them! In all I had to do a lot of learning as I've never updated BIOS before, in the end after many hours I decided to bite the bullet and install an old windows disk to do it.

Upside: I now have an updated BIOS - yay!
Downside: I've a fresh install of Ubuntu, so I dont have my original personal touches any more - I think I will spend less time getting my laptop back the way I like it, than searching for 'that' missing method that would Flash my BIOS from within Ubuntu.

So - I'm not sure where to go next with my sound issue, I've re-installed the script from Iidex's sig - (and left pulse audio alone this time)
I guess, going back to the start of my query in this thread (since I've a clean install - bar the measures mentioned above) I will re-post your (Iidex) first suggestion - if that helps.
[PHP]
Removing pulse probably more of a last ditch effort than a  troubleshooting step. I would re-install it, then this: Use the  alsa-info-script to provide detailed information.
Run this command in a terminal:
     Code:
     wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh[/PHP]

If you could help some more now, that would be great - as my sound is still off :(

Here is the newer version of the link to the first request (if its of any use)

[http://www.alsa-project.org/db/?f=9e7bdadda3921e82a2a918ed1d05593dc6e0e8c0](http://www.alsa-project.org/db/?f=9e7bdadda3921e82a2a918ed1d05593dc6e0e8c0)

I look forward to your help on this - if you need me to submit any more info, just let me know.

Many thanks.

---

### Post by lkjoel on 2010-09-25
> **Frisbee catcher said:**
> Hi Ikjoel and Iidex,

I spent a long time trying to figure out how to get my BIOS updated, all methods I tried out to do this within a Linux environment failed - and I tried a few of them! In all I had to do a lot of learning as I've never updated BIOS before, in the end after many hours I decided to bite the bullet and install an old windows disk to do it.

Upside: I now have an updated BIOS - yay!
Downside: I've a fresh install of Ubuntu, so I dont have my original personal touches any more - I think I will spend less time getting my laptop back the way I like it, than searching for 'that' missing method that would Flash my BIOS from within Ubuntu.

So - I'm not sure where to go next with my sound issue, I've re-installed the script from Iidex's sig - (and left pulse audio alone this time)
I guess, going back to the start of my query in this thread (since I've a clean install - bar the measures mentioned above) I will re-post your (Iidex) first suggestion - if that helps.
[PHP]
Removing pulse probably more of a last ditch effort than a  troubleshooting step. I would re-install it, then this: Use the  alsa-info-script to provide detailed information.
Run this command in a terminal:
     Code:
     wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh[/PHP]

If you could help some more now, that would be great - as my sound is still off :(

Here is the newer version of the link to the first request (if its of any use)

[http://www.alsa-project.org/db/?f=9e7bdadda3921e82a2a918ed1d05593dc6e0e8c0](http://www.alsa-project.org/db/?f=9e7bdadda3921e82a2a918ed1d05593dc6e0e8c0)

I look forward to your help on this - if you need me to submit any more info, just let me know.

Many thanks.
Try Fix your sound! in my signature.
Then use Post-Fix your sound! in my signature.

---

### Post by lidex on 2010-09-26
> **Frisbee catcher said:**
> Hi Ikjoel and Iidex,

If you could help some more now, that would be great - as my sound is still off :(

Here is the newer version of the link to the first request (if its of any use)

[http://www.alsa-project.org/db/?f=9e7bdadda3921e82a2a918ed1d05593dc6e0e8c0](http://www.alsa-project.org/db/?f=9e7bdadda3921e82a2a918ed1d05593dc6e0e8c0)

I look forward to your help on this - if you need me to submit any more info, just let me know.

Many thanks.

Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=acer-aspire 
```
Save. Close. Reboot. 
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

### Post by Frisbee catcher on 2010-09-26
Ikjoel, thanks for your suggestion about using the 'sound-fix' method, however, looking at it, I can see it involves uninstalling Pulse Audio and removing some part of Alsa, which goes against the initial advice Iidex gave to me toward the start of my initial enquiry - so, with respect, for the time being I'm not going to try that until all other options are exhausted.

Iidex, I edited the file as suggested and saved it, and rebooted - opened alsamixer, checked soundcard and made sure nothing was muted.

Still no sound.

I'm assuming I have the correct soundcard - I did a ```
sudo alsaconf
``` which searched out my soundcards, I have :

hda-intel   Intel Corporation N10/ICH 7 Family

and a 

Legacy   - Probe Legacy ISA (non-PnP) chips.

It asks me to select a sound card to configure, so I chose the Intel one, then got the following message:
     > Configuring snd-hda-intel                       
                &#9474; Do you want to modify /etc/modprobe.d/sound  
                &#9474; (and /etc/modprobe.conf if present)?  
 

 (I accepted this) Then got:
 
 
 OK, sound driver is configured.                      
           &#9474;                                                           
           &#9474;                   ALSA  CONFIGURATOR  
           &#9474;                                                           
           &#9474;           will prepare the card for playing now  
           &#9474;                                                           
           &#9474;      Now I'll run alsasound init script, then I'll use   
           &#9474;      amixer to raise the default volumes.                
           &#9474;      You can change the volume later via a mixer           
           &#9474;                                                           
           &#9474;                          <Ok>                       
 

 I pressed OK and got:
 
 
 Now ALSA is ready to use.  
  For adjustment of volumes, use your favorite mixer.  
 
 
  Have a lot of fun!  Reads like everything should be fine, but still have no sound.


One observation I made whilst in alsamixer - I have an S/PDIF jack which was showing as not muted but wouldn't increase the volume using the up/down arrows - just sits at 00.


Any other ideas?


I know I keep saying it, but thanks for helping me with this, seems like a bit of an epic quest (for me at least) to fix what I originally hoped to be a minor problem!

---

### Post by Frisbee catcher on 2010-09-26
- Oh, I meant to add:

I went to "System ->Preferences ->Sound"  to check my soundcard - in the Hardware tab, under the 'Choose a device to configure' window, I only have one device - which is rather basically described as 'Internal Audio'
 The Profile is currently on 'Digital Stereo (IEC958) Output + Analog Stereo Input'  - Should there be any options for 5.1 surround sound or similar? I don't have them if there are.
. 
On the output tab - under 'choose a device for sound output' :
 I have no option other than the one that is there - 'Internal Audio Digital Stereo (IEC958) Stereo'

no mentions here of the Intel sound card if that's what I'm looking for.

---

### Post by lkjoel on 2010-09-26
[QUOTE=Frisbee catcher;9892979]Ikjoel, thanks for your suggestion about using the 'sound-fix' method, however, looking at it, I can see it involves uninstalling Pulse Audio and removing some part of Alsa, which goes against the initial advice Iidex gave to me toward the start of my initial enquiry - so, with respect, for the time being I'm not going to try that until all other options are exhausted.
...[QUOTE]
That is only for a time.
If you install OSS, you can install ALSA and PulseAudio back.
So what I am saying is not that you should not follow **l**idex (It's an L (el) by the way)'s advice, but that you should try installing OSS 4.x, and re-installing ALSA and PulseAudio.
So if you decide to install OSS 4.x, here is how you install ALSA and PulseAudio.
Type this into a Terminal window:
```
sudo apt-get install alsa-base alsa-utils pulseaudio pulseaudio-utils
```
Edit /etc/pulse/default.pa and
Remove "module-hal-detect" (it won't detect OSS anyway).
Uncomment "module-oss" line and add "mmap=0" at end.
If "module-oss" line does not exist add the line below to default.pa:
load-module module-oss device="/dev/dsp" sink_name=output source_name=input mmap=0
You may wish to copy this file to ~/.pulse directory, so that it isn't overwritten by a package upgrade.
Then type in a Terminal window:
```
osstest
```
If you hear sound, all is well.
If not, continue following Lidex's advice.

---

### Post by lidex on 2010-09-26
> **Frisbee catcher said:**
> - Oh, I meant to add:

I went to "System ->Preferences ->Sound"  to check my soundcard - in the Hardware tab, under the 'Choose a device to configure' window, I only have one device - which is rather basically described as 'Internal Audio'
 The Profile is currently on 'Digital Stereo (IEC958) Output + Analog Stereo Input'  - Should there be any options for 5.1 surround sound or similar? I don't have them if there are.
. 
On the output tab - under 'choose a device for sound output' :
 I have no option other than the one that is there - 'Internal Audio Digital Stereo (IEC958) Stereo'

no mentions here of the Intel sound card if that's what I'm looking for.

Digital Stereo Output in your profile means your audio will be output through spdif. Are you using digital? If not you need to choose analog.

---

### Post by mihir.gupte on 2010-09-27
Hi lkjoel

your suggested last method to upgrade the alsa-mixer, i tried it and my sound works fine. But now when i go to OS choosing menu, i choose Ubuntu and then a screen with Ubuntu #.#.32-24 below theres another recovery I think below that is another Ubuntu#.#.32-21 does that mean older version was installed?Because with that im losing a 1.5GB for no reason.

---

### Post by Frisbee catcher on 2010-10-02
Hello again Ikjoel and Lidex,

Firstly, thanks for persevering with me through these issues.

Secondly, would you mind persevering a little longer!

Lidex, I checked my profile and even switching it over to analog didn't get the sound coming out of the laptops own speakers. I figured that - if I can hear sound through one headphone (when plugged in) then I should get something if I output it to my 5.1 surround sound system. Sure enough I'm getting a passable sound quality through them, though two of the speakers are not giving anything at all - the bottom line is, I don't always want the main sound system on when I'm just working at the computer though - would be nice to just hear the system noises (start-up jingle, bleeps, alerts, etc) or use headphones in stereo when I don't want to disturb the rest of the house!
An added problem I noticed was that when I did manage to play some music, after a while a shutdown menu would pop up - only it wasn't just sat there asking if I wanted to shut down, re-start, etc etc, it was blinking very fast between that and the music player (kind of like it couldn't decide what window to display, so would flicker between the two) - upon doing a CTRL-ALT-DEL it caused the shutdown menu to remain stable - so I just hit cancel, and it went away - however, after doing this, the panel effectively becomes 'frozen' in such that I can put the cursor over an icon - it changes to signify I'm hovering over it, but when I press the mouse button nothing happens at all - in fact I can't click anything at all and am forced to shut the laptop down by pressing and holding the standby button (which I really don't like doing!). This only happens when I play music for a little while.

Ikjoel, I tried out the sound-fix and post sound-fix links, got through the whole procedure and it seems to suggest that everything is fine - all tests OK.
Yet, I still have the same problem :(

I feel like I seem to have a million to one problem that can't be fixed! but I'm sure it must be doable as I know everything (on the sound front) worked spotlessly when I had Windows installed.

I can't let Windows get the better of me - anyone have any more ideas I can try?

Thanks again - and apologies for the rather extensive post!

---

### Post by lidex on 2010-10-02
> **Frisbee catcher said:**
> Hello again Ikjoel and Lidex,

Firstly, thanks for persevering with me through these issues.

Secondly, would you mind persevering a little longer!

Lidex, I checked my profile and even switching it over to analog didn't get the sound coming out of the laptops own speakers. I figured that - if I can hear sound through one headphone (when plugged in) then I should get something if I output it to my 5.1 surround sound system. Sure enough I'm getting a passable sound quality through them, though two of the speakers are not giving anything at all - the bottom line is, I don't always want the main sound system on when I'm just working at the computer though - would be nice to just hear the system noises (start-up jingle, bleeps, alerts, etc) or use headphones in stereo when I don't want to disturb the rest of the house!
An added problem I noticed was that when I did manage to play some music, after a while a shutdown menu would pop up - only it wasn't just sat there asking if I wanted to shut down, re-start, etc etc, it was blinking very fast between that and the music player (kind of like it couldn't decide what window to display, so would flicker between the two) - upon doing a CTRL-ALT-DEL it caused the shutdown menu to remain stable - so I just hit cancel, and it went away - however, after doing this, the panel effectively becomes 'frozen' in such that I can put the cursor over an icon - it changes to signify I'm hovering over it, but when I press the mouse button nothing happens at all - in fact I can't click anything at all and am forced to shut the laptop down by pressing and holding the standby button (which I really don't like doing!). This only happens when I play music for a little while.

Ikjoel, I tried out the sound-fix and post sound-fix links, got through the whole procedure and it seems to suggest that everything is fine - all tests OK.
Yet, I still have the same problem :(

I feel like I seem to have a million to one problem that can't be fixed! but I'm sure it must be doable as I know everything (on the sound front) worked spotlessly when I had Windows installed.

I can't let Windows get the better of me - anyone have any more ideas I can try?

Thanks again - and apologies for the rather extensive post!

Need to see where you are now. Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.

---

### Post by Frisbee catcher on 2010-10-02
Hey Lidex, thanks for getting back to me.

Ok, here is the link to what you've asked for:

[http://www.alsa-project.org/db/?f=9151372edc8e501ca73d2e7d0032c7b067926ac6](http://www.alsa-project.org/db/?f=9151372edc8e501ca73d2e7d0032c7b067926ac6)

looks to me like I've gone a step backward now? I can see that it has not found the soundcards this time for some reason.

I re-ran the script from your sig by the way - hoping this would keep everything up to date BEFORE submitting the link you asked for.

Another thing - from Ikjoels post:

> So if you decide to install OSS 4.x, here is how you install ALSA and PulseAudio.
Type this into a Terminal window:
     Code:
     sudo apt-get install alsa-base alsa-utils pulseaudio pulseaudio-utils 
Edit /etc/pulse/default.pa and
Remove "module-hal-detect" (it won't detect OSS anyway).
Uncomment "module-oss" line and add "mmap=0" at end.
If "module-oss" line does not exist add the line below to default.pa:
load-module module-oss device="/dev/dsp" sink_name=output source_name=input mmap=0
You may wish to copy this file to ~/.pulse directory, so that it isn't overwritten by a package upgrade.
Then type in a Terminal window:
     Code:
     osstest 
If you hear sound, all is well.
If not, continue following Lidex's advice.     
After entering the first bit of code to re-introduce Alsa and pulseaudio, it says to:

Edit /etc/pulse/default.pa

I tried this in the terminal (assuming this to be the correct thing to do) but got this message
> No command 'Edit' found, did you mean:
 Command 'edit' from package 'mime-support' (main)
Edit: command not foundconsequently I haven't managed to edit the rest of the instructions provided - which I guess would have some adverse affects?

Ikjoel, could you tell me if I did something wrong, if so could you walk me through where I went wrong please.

Thanks guys :)

---

### Post by Frisbee catcher on 2010-10-02
Additional - Ikjoel

Ok, found from an earlier post in this thread how to edit, had to use 'gedit' not 'edit'.

Regardless, I'm still a little less than confident how to carry out the editing instructions without the potential for making a mess of something.

I have attached the file that I got after entering:

```
gedit /etc/pulse/default.pa
```

Would you mind having a look and making the appropriate amendments? I would like the opportunity to learn by what you show me &  I wouldn't ordinarily ask anyone to do my work for me (feels like asking someone else to do your homework for you or something!) but like I say, I'm just a bit concerned about entering or deleting the wrong thing.

Much appreciated.

---

### Post by lidex on 2010-10-02
> **Frisbee catcher said:**
> Additional - Ikjoel

Ok, found from an earlier post in this thread how to edit, had to use 'gedit' not 'edit'.

Regardless, I'm still a little less than confident how to carry out the editing instructions without the potential for making a mess of something.

I have attached the file that I got after entering:

```
gedit /etc/pulse/default.pa
```

Would you mind having a look and making the appropriate amendments? I would like the opportunity to learn by what you show me &  I wouldn't ordinarily ask anyone to do my work for me (feels like asking someone else to do your homework for you or something!) but like I say, I'm just a bit concerned about entering or deleting the wrong thing.

Much appreciated.

You cannot combine these approaches as alsa and oss do not go together. Since you've already made some config changes to implement OSS I suggest you stick with that and perhaps in the future *lkjoel* will warn noobs of the consequences of blindly removing your integrated default sound system for something that requires tinkering beyond the amateur level.

---

### Post by Frisbee catcher on 2010-10-07
Hi Lidex,

I made the decision to do a fresh install of Lucid onto my laptop - wasn't too big a deal as I had left everything relatively 'bare bones' after my BIOS upgrade until I fixed the problems.

I've ran the ALSA Upgrade script again and followed the instructions you gave afterward:

> Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
 	Code:
 	 gksudo gedit /etc/modprobe.d/alsa-base.conf 
Insert this line at the bottom:
 	Code:
 	 options snd-hda-intel model=acer-aspire 
Save. Close. Reboot. 
Check your levels in alsamixer.
 	Code:
 	 alsamixer 
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct  soundcard is default and adjust your profile on the hardware tab. 
On the output tab choose the correct device.

I still have the same issue at the moment - no sound from laptops own speakers, only mono sound on headphones.

Checked sound profile, output is set on 'Analog Stereo Duplex' by default.

Checked ALSAMIXER to make sure nothing is muted.

One thing I have noticed - on boot-up I get a brief flash of a message saying 'Missing Firmware XC3028 v27' or similar. Everything boots up normally afterward, but I wonder if this might have anything to do with the problem?

The last thing i've done is to run the alsa-info-script as asked in a recent post of yours:

> Need to see where you are now. Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
 	Code:
 	wget [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh) -O alsa-info.sh && bash alsa-info.sh 
Choose the upload option and provide a link for the output. 	

Here is the most recent link address:  [http://www.alsa-project.org/db/?f=764f54d7ed37bf2182d1f2f0b66ad9fcd0db1527](http://www.alsa-project.org/db/?f=764f54d7ed37bf2182d1f2f0b66ad9fcd0db1527)

Hope you are able to help.

Thanks in advance.

---

### Post by Frisbee catcher on 2010-10-07
- update:

I did some googling and installed the missing firmware - hasn't made any difference to the sound though!

for anyone interested, I ended up here :  [https://launchpad.net/ubuntu/lucid/i386/linux-firmware-nonfree/1.8](https://launchpad.net/ubuntu/lucid/i386/linux-firmware-nonfree/1.8)

then dowloaded and installed this : [http://launchpadlibrarian.net/44390666/linux-firmware-nonfree_1.8_all.deb](http://launchpadlibrarian.net/44390666/linux-firmware-nonfree_1.8_all.deb)

Although this seems to have fixed the 'Firmware not found' message, upon boot-up now I get a DOS-like prompt, although, it just skips over this after a few seconds and continues to fire up normally.

Would be nice if the boot-up sequence didn't have show any of the 'internal processes' whilst starting up - just from an aesthetics point of view - unless of course its pointing out a specific error, which is just helpful, i'd rather it just go through the 'this is your computer' screen, then on to 'this is the OS' Splash - and onto the desktop, without any script showing in between. Hey ho, just my preference I guess.

---

### Post by lidex on 2010-10-07
Everything looks OK. I see you have the acer-aspire model added to alsa-base.conf. Next step is to try different models. Change acer-aspire to just acer. It would look like this:
```
options snd-hda-intel model=acer
```

---

### Post by Frisbee catcher on 2010-10-09
Hi Lidex,

Tried changing the model to just 'Acer' but hasn't made any difference. Not sure what other permutations I could try - unless you would suggest trying other makes and models though surely that could take a long time of trial and error.
Do you suppose I'm running out of technical solutions to this problem? Hmm, I hope not, just can't understand why I have such a unique problem - very frustrating!

Anyway, thanks for your persistence Lidex, much appreciated.

---

### Post by lidex on 2010-10-10
> **Frisbee catcher said:**
> Hi Lidex,

Tried changing the model to just 'Acer' but hasn't made any difference. Not sure what other permutations I could try - unless you would suggest trying other makes and models though surely that could take a long time of trial and error.
Do you suppose I'm running out of technical solutions to this problem? Hmm, I hope not, just can't understand why I have such a unique problem - very frustrating!

Anyway, thanks for your persistence Lidex, much appreciated.

Did you reboot?

---

### Post by Frisbee catcher on 2010-10-10
> Did you reboot? 	

Yes, I saved, closed and rebooted each time.

Have tried using ...'acer'  'acer-aspire' 'acer-aspire9800' 'acer-aspire-9800', also tried a suggestion I stumbled across on another forum to replace this with '6stack-dig' , which gave me several more options in the alsamixer, but still no sound.

Will keep trying a few other permutations of my laptop model, but if you have any ideas i will be glad to hear and try them!

---

### Post by lidex on 2010-10-10
> **Frisbee catcher said:**
> Yes, I saved, closed and rebooted each time.

Have tried using ...'acer'  'acer-aspire' 'acer-aspire9800' 'acer-aspire-9800', also tried a suggestion I stumbled across on another forum to replace this with '6stack-dig' , which gave me several more options in the alsamixer, but still no sound.

Will keep trying a few other permutations of my laptop model, but if you have any ideas i will be glad to hear and try them!

```
ALC882/883/885/888/889
======================
  3stack-dig    3-jack with SPDIF I/O
  6stack-dig    6-jack digital with SPDIF I/O
  arima        Arima W820Di1
  targa        Targa T8, MSI-1049 T8
  asus-a7j    ASUS A7J
  asus-a7m    ASUS A7M
  macpro    MacPro support
  mb5        Macbook 5,1
  macmini3    Macmini 3,1
  mba21        Macbook Air 2,1
  mbp3        Macbook Pro rev3
  imac24    iMac 24'' with jack detection
  imac91    iMac 9,1
  w2jc        ASUS W2JC
  3stack-2ch-dig    3-jack with SPDIF I/O (ALC883)
  alc883-6stack-dig    6-jack digital with SPDIF I/O (ALC883)
  3stack-6ch    3-jack 6-channel
  3stack-6ch-dig 3-jack 6-channel with SPDIF I/O
  6stack-dig-demo  6-jack digital for Intel demo board
  acer        Acer laptops (Travelmate 3012WTMi, Aspire 5600, etc)
  acer-aspire    Acer Aspire 9810
  acer-aspire-4930g Acer Aspire 4930G
  acer-aspire-6530g Acer Aspire 6530G
  acer-aspire-7730g Acer Aspire 7730G
  acer-aspire-8930g Acer Aspire 8930G
  medion    Medion Laptops
  medion-md2    Medion MD2
  targa-dig    Targa/MSI
  targa-2ch-dig    Targa/MSI with 2-channel
  targa-8ch-dig Targa/MSI with 8-channel (MSI GX620)
  laptop-eapd   3-jack with SPDIF I/O and EAPD (Clevo M540JE, M550JE)
  lenovo-101e    Lenovo 101E
  lenovo-nb0763    Lenovo NB0763
  lenovo-ms7195-dig Lenovo MS7195
  lenovo-sky    Lenovo Sky
  haier-w66    Haier W66
  3stack-hp    HP machines with 3stack (Lucknow, Samba boards)
  6stack-dell    Dell machines with 6stack (Inspiron 530)
  mitac        Mitac 8252D
  clevo-m540r    Clevo M540R (6ch + digital)
  clevo-m720    Clevo M720 laptop series
  fujitsu-pi2515 Fujitsu AMILO Pi2515
  fujitsu-xa3530 Fujitsu AMILO XA3530
  3stack-6ch-intel Intel DG33* boards
  intel-alc889a    Intel IbexPeak with ALC889A
  intel-x58    Intel DX58 with ALC889
  asus-p5q    ASUS P5Q-EM boards
  mb31        MacBook 3,1
  sony-vaio-tt  Sony VAIO TT
  auto        auto-config reading BIOS (default)

```

Also try running this command in a terminal for 10.04 or later:
```
ubuntu-bug audio
```
Reference the Ubuntu-Bug Audio link in my sig.

---

### Post by Frisbee catcher on 2010-10-10
Thanks for the list Lidex!

I take it I have to replace 'acer-aspire' (or whatever) with each of those models in that list one after the other - save, close - reboot, test - move on etc.. hehe, that could take a while, but I'll give it a go!

I'll get back to you after I try them out.

- not that I'm going to do it in case I mess things up - but, is it possible to copy and paste that entire list? 

I won't be going through the list one by one till tomorrow now - but if you get back to me in the meantime and say its possible - then you may save me a lot of time!

Thanks for your continued help.

---

### Post by lidex on 2010-10-10
> **Frisbee catcher said:**
> Thanks for the list Lidex!

I take it I have to replace 'acer-aspire' (or whatever) with each of those models in that list one after the other - save, close - reboot, test - move on etc.. hehe, that could take a while, but I'll give it a go!

I'll get back to you after I try them out.

- not that I'm going to do it in case I mess things up - but, is it possible to copy and paste that entire list? 

I won't be going through the list one by one till tomorrow now - but if you get back to me in the meantime and say its possible - then you may save me a lot of time!

Thanks for your continued help.

You could try reloading alsa instead of rebooting:
```
sudo alsa force-reload
```
Of course you can copy/paste that list - I assume you mean to a local text file?
Try the ubuntu bug command also and file a bug report.

BTW, you have the alsa documentation already. Simply run this in a terminal:
```
zless /usr/share/doc/alsa-base/driver/HD-Audio-Models.txt.gz
```

---

### Post by Robodaddio on 2010-12-05
I feel like an idiot. After hours of trying to fix my spdif output to my receiver the simple command below solved it. After the terminal popped up I hit M on the keyboard then used the arrow keys to increase the spdif volume. Hope this helps someone else.
alsamixer -c 1

---

### Post by lhearn on 2011-01-06
[FONT=Comic Sans MS][SIZE=2]I installed Ubuntu 10.04 on my HP G60 laptop and found I had no sound. It uses a **Conexan**t pebble High Definition Smartaudio sound card. Seems to be no linux driver for this soundcard and I almost gave up until, quite by chance, I found a **SIMPLE** solution. While trying to play a wmv (Windows Movie File) in the Ubuntu Media Player I got the message that I had to download and install an addon - simply pressed the download key and after installation VOILA for the 1st time in the 6 months since I installed Ubuntu on my laptop I had sound. A **SIMPLE** solution that requires no knowledge of supergeek cuneiform to implement. Should help the many of us who are not full of impenetrable baffegab.[/SIZE][/FONT]

---

