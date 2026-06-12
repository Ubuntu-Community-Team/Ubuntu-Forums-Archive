---
title: "No sound Audigy 2 Alsamixer"
date: 2009-01-25
forum: Multimedia Software
---

### Post by vipertga on 2009-01-25
don't hear any sounds!

I am a complete Ubuntu noob but, In a forum I read that I must

run "alsamixer" in terminal
then turn everything up for my soundcard.

But the problem is....

when I run "alsamixer" the only thing that shows up is "pulseaudio" and not "Audigy 2." So, how do I make my card the Audigy 2?

Thanks

PS:I will upload a screenshot of my Alsamixer

---

### Post by vipertga on 2009-01-26
Any luck?

---

### Post by Linuxdork on 2009-01-26
What version of Ubuntu are you using and what is the output of the following commands:
[B]
lspci | grep -i audio[/B]

**lsmod | grep sn**d

Actually, I don't know what the module name is for your card.  I think it is something like emu10k1.  So give the output of this to:
[B]
lsmod | grep emu10k1[/B]  or  **lsmod | grep emu**

---

### Post by mc4man on 2009-01-26
I just finished setting up 8.10 with an audigy 2zs. While getting excellent sound quality and proper 6 channel output and up mixing of 2, 2.1 sources was a bit of a pita, sound itself wasn't. 

Maybe check something basic.

Double left click on the little speaker icon in the upper panel next to the date. In the pop up click preferences and scroll down to the switches. Enable Audigy Analog/Digitial Output Jack and close out.
Back in the main window click on the switches tab and make sure it's checked. (for me in must be checked.

Try your sound again, if no go maybe try the switch unchecked.
Screens show my basic setting in System -> preferences -> sound (though it took several other things to get the sound right. At the moment it's as good as it's ever been in Hardy, Gutsy.

Side note: if you get sound going and it doesn't sound right, or a player suddenly crashes, run this in a terminal and see if pulseaudio is shown as a process while playing files, music, whatever. (it shouldn't be there as far as I'm concerned, if it is it will be using an insane amount of cpu

```
top
```

---

### Post by vipertga on 2009-01-26
alex@Thing1:~$ lspci | grep -i audio
06:01.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
alex@Thing1:~$ lsmod | grep snd
snd_emu10k1_synth      14464  0 
snd_emux_synth         41344  1 snd_emu10k1_synth
snd_seq_virmidi        13568  1 snd_emux_synth
snd_seq_midi_emul      14592  1 snd_emux_synth
snd_emu10k1           146208  6 snd_emu10k1_synth
snd_ac97_codec        111652  1 snd_emu10k1
ac97_bus                9856  1 snd_ac97_codec
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
snd_pcm                83204  4 snd_emu10k1,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         16136  2 snd_emu10k1,snd_pcm
snd_util_mem           12416  2 snd_emux_synth,snd_emu10k1
snd_hwdep              15236  2 snd_emux_synth,snd_emu10k1
snd_seq_dummy          10884  0 
snd_seq_oss            38528  0 
snd_seq_midi           14336  0 
snd_rawmidi            29824  3 snd_seq_virmidi,snd_emu10k1,snd_seq_midi
snd_seq_midi_event     15232  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
snd_seq                57776  9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29960  3 snd_emu10k1,snd_pcm,snd_seq
snd_seq_device         15116  8 snd_emu10k1_synth,snd_emux_synth,snd_emu10k1,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    63268  22 snd_emux_synth,snd_seq_virmidi,snd_emu10k1,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15328  1 snd
alex@Thing1:~$ lsmod | grep emu10k1 or lsmod | grep emu
grep: or: No such file or directory
grep: lsmod: No such file or directory
alex@Thing1:~$

---

### Post by vipertga on 2009-01-26
> **mc4man said:**
> I just finished setting up 8.10 with an audigy 2zs. While getting excellent sound quality and proper 6 channel output and up mixing of 2, 2.1 sources was a bit of a pita, sound itself wasn't. 

Maybe check something basic.

Double left click on the little speaker icon in the upper panel next to the date. In the pop up click preferences and scroll down to the switches. Enable Audigy Analog/Digitial Output Jack and close out.
Back in the main window click on the switches tab and make sure it's checked. (for me in must be checked.

Try your sound again, if no go maybe try the switch unchecked.
Screens show my basic setting in System -> preferences -> sound (though it took several other things to get the sound right. At the moment it's as good as it's ever been in Hardy, Gutsy.

Side note: if you get sound going and it doesn't sound right, or a player suddenly crashes, run this in a terminal and see if pulseaudio is shown as a process while playing files, music, whatever. (it shouldn't be there as far as I'm concerned, if it is it will be using an insane amount of cpu

```
top
```

Followed these and still have nothing

---

### Post by vipertga on 2009-01-26
I have Ubuntu 8.10

---

### Post by Linuxdork on 2009-01-26
Okay, the kernel has found the device and the proper driver is loaded so at this point it's most likely some configuration issue.  Pulseaudio is the default soundserver on Ubuntu so this is what we need to configure to get the sound working.  Post the screenshots of what pops up when you run alsamixer.

---

### Post by vipertga on 2009-01-26
I dont know if this helps either

alex@Thing1:~$ asoundconf list
Names of available sound cards:
Audigy2
alex@Thing1:~$ 


I tried the command 

asoundconf set-default-card Audigy2
but, it doesnt help either.

---

### Post by vipertga on 2009-01-26
[IMG]http://img101.imageshack.us/img101/7342/screenshotaz2.jpg[/IMG]

---

### Post by Linuxdork on 2009-01-26
You may need to follow this thread to get your pulseaudio working correctly.  I have followed this and everything is working great now.

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

**[edit]** I just saw the screenshot and I don't think it is alsamixer at fault here.  Try the thread I just listed and lets see if that works.

---

### Post by vipertga on 2009-01-26
Do you see how it says "PulseAudio" for card?

I think if we get that to say "Audigy2" I will be okay.

---

### Post by Linuxdork on 2009-01-26
alsamixer is how it used to work.  Now that pulseaudio it the default sound server it will handle the sound card.  If pulseaudio was properly handling the sound card, from what we've seen so far you should have sound.

---

### Post by vipertga on 2009-01-26
Ill give it a try.

---

### Post by Linuxdork on 2009-01-26
Cool.  Like I said, it helped all of my sound problems.  Let us know how it works.

---

### Post by vipertga on 2009-01-26
Alright!

It works. 

I think the most important code was: "alsamixer -Dhw"


But, still one problem.

My rears dont produce sound.  I switched cables around to trouble shoot and it still doesnt work.  


Any ideas?

---

### Post by Linuxdork on 2009-01-26
That might be a setting.  If you can set it to 5.1 surround sound or something like that it should fix that.  I'll see if I can find something on that.

---

### Post by vipertga on 2009-01-26
Not sure if this would ever help someone but, here is what I did:


alex@Thing1:~$ $ mkdir ~/pulse-backup && cp -r ~/.pulse ~/.asound* /etc/asound.conf /etc/pulse -t ~/pulse-backup/
bash: $: command not found
alex@Thing1:~$ mkdir ~/pulse-backup && cp -r ~/.pulse ~/.asound* /etc/asound.conf /etc/pulse -t ~/pulse-backup/
cp: cannot stat `/etc/asound.conf': No such file or directory
alex@Thing1:~$ sudo rm -r ~/.pulse ~/.asound* /etc/asound.conf
[sudo] password for alex: 
rm: cannot remove `/etc/asound.conf': No such file or directory
alex@Thing1:~$ sudo apt-get install libasound2-plugins padevchooser libao-pulse libsdl1.2debian-pulseaudio flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libasound2-plugins is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.27-7 linux-headers-2.6.27-7-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libgconfmm-2.6-1c2 libglademm-2.4-1c2a libpulse-mainloop-glib0 paman paprefs
  pavucontrol pavumeter pulseaudio-module-zeroconf
Suggested packages:
  konqueror-nsplugins msttcorefonts ttf-xfree86-nonfree xfs
The following packages will be REMOVED:
  libsdl1.2debian-alsa
The following NEW packages will be installed:
  flashplugin-nonfree libao-pulse libgconfmm-2.6-1c2 libglademm-2.4-1c2a
  libpulse-mainloop-glib0 libsdl1.2debian-pulseaudio padevchooser paman
  paprefs pavucontrol pavumeter pulseaudio-module-zeroconf
0 upgraded, 12 newly installed, 1 to remove and 0 not upgraded.
Need to get 536kB/556kB of archives.
After this operation, 2036kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe libao-pulse 0.9.3-1 [7158B]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main libgconfmm-2.6-1c2 2.24.0-0ubuntu1 [31.1kB]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main libglademm-2.4-1c2a 2.6.6-1 [21.1kB]
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main libpulse-mainloop-glib0 0.9.10-2ubuntu9.2 [23.9kB]
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe paman 0.9.4-1ubuntu1 [95.3kB]
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main pulseaudio-module-zeroconf 0.9.10-2ubuntu9.2 [17.8kB]
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe paprefs 0.9.6-2ubuntu1 [31.6kB]
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe pavucontrol 0.9.6+svn20080426-1ubuntu1 [51.1kB]
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe pavumeter 0.9.3-1ubuntu1 [29.2kB]
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe padevchooser 0.9.3-2ubuntu3 [20.2kB]
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe libsdl1.2debian-pulseaudio 1.2.13-2ubuntu1 [208kB]
Fetched 536kB in 12s (41.8kB/s)                                                
Preconfiguring packages ...
dpkg: libsdl1.2debian-alsa: dependency problems, but removing anyway as you request:
 libsdl1.2debian depends on libsdl1.2debian-alsa (= 1.2.13-2ubuntu1) | libsdl1.2debian-all (= 1.2.13-2ubuntu1) | libsdl1.2debian-esd (= 1.2.13-2ubuntu1) | libsdl1.2debian-arts (= 1.2.13-2ubuntu1) | libsdl1.2debian-oss (= 1.2.13-2ubuntu1) | libsdl1.2debian-nas (= 1.2.13-2ubuntu1) | libsdl1.2debian-pulseaudio (= 1.2.13-2ubuntu1); however:
  Package libsdl1.2debian-alsa is to be removed.
  Package libsdl1.2debian-all is not installed.
  Package libsdl1.2debian-esd is not installed.
  Package libsdl1.2debian-arts is not installed.
  Package libsdl1.2debian-oss is not installed.
  Package libsdl1.2debian-nas is not installed.
  Package libsdl1.2debian-pulseaudio is not installed.
(Reading database ... 132833 files and directories currently installed.)
Removing libsdl1.2debian-alsa ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Selecting previously deselected package flashplugin-nonfree.
(Reading database ... 132825 files and directories currently installed.)
Unpacking flashplugin-nonfree (from .../flashplugin-nonfree_10.0.15.3ubuntu1~intrepid1_i386.deb) ...
Selecting previously deselected package libao-pulse.
Unpacking libao-pulse (from .../libao-pulse_0.9.3-1_i386.deb) ...
Replaced by files in installed package libao2 ...
Selecting previously deselected package libgconfmm-2.6-1c2.
Unpacking libgconfmm-2.6-1c2 (from .../libgconfmm-2.6-1c2_2.24.0-0ubuntu1_i386.deb) ...
Selecting previously deselected package libglademm-2.4-1c2a.
Unpacking libglademm-2.4-1c2a (from .../libglademm-2.4-1c2a_2.6.6-1_i386.deb) ...
Selecting previously deselected package libpulse-mainloop-glib0.
Unpacking libpulse-mainloop-glib0 (from .../libpulse-mainloop-glib0_0.9.10-2ubuntu9.2_i386.deb) ...
Selecting previously deselected package paman.
Unpacking paman (from .../paman_0.9.4-1ubuntu1_i386.deb) ...
Selecting previously deselected package pulseaudio-module-zeroconf.
Unpacking pulseaudio-module-zeroconf (from .../pulseaudio-module-zeroconf_0.9.10-2ubuntu9.2_i386.deb) ...
Selecting previously deselected package paprefs.
Unpacking paprefs (from .../paprefs_0.9.6-2ubuntu1_i386.deb) ...
Selecting previously deselected package pavucontrol.
Unpacking pavucontrol (from .../pavucontrol_0.9.6+svn20080426-1ubuntu1_i386.deb) ...
Selecting previously deselected package pavumeter.
Unpacking pavumeter (from .../pavumeter_0.9.3-1ubuntu1_i386.deb) ...
Selecting previously deselected package padevchooser.
Unpacking padevchooser (from .../padevchooser_0.9.3-2ubuntu3_i386.deb) ...
Selecting previously deselected package libsdl1.2debian-pulseaudio.
Unpacking libsdl1.2debian-pulseaudio (from .../libsdl1.2debian-pulseaudio_1.2.13-2ubuntu1_i386.deb) ...
Processing triggers for man-db ...
Setting up flashplugin-nonfree (10.0.15.3ubuntu1~intrepid1) ...
Downloading...
--2009-01-26 16:03:27--  [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.tar.gz)
Resolving fpdownload.macromedia.com... 96.6.130.70
Connecting to fpdownload.macromedia.com|96.6.130.70|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 3962157 (3.8M) [application/x-gzip]
Saving to: `./install_flash_player_10_linux.tar.gz'

     0K .......... .......... .......... .......... ..........  1% 86.2K 44s
    50K .......... .......... .......... .......... ..........  2% 85.5K 44s
   100K .......... .......... .......... .......... ..........  3% 61.2K 49s
   150K .......... .......... .......... .......... ..........  5% 43.3K 58s
   200K .......... .......... .......... .......... ..........  6% 90.9K 53s
   250K .......... .......... .......... .......... ..........  7% 49.8K 56s
   300K .......... .......... .......... .......... ..........  9% 30.6K 64s
   350K .......... .......... .......... .......... .......... 10% 37.7K 66s
   400K .......... .......... .......... .......... .......... 11% 34.7K 69s
   450K .......... .......... .......... .......... .......... 12% 71.9K 66s
   500K .......... .......... .......... .......... .......... 14% 72.1K 63s
   550K .......... .......... .......... .......... .......... 15% 63.5K 61s
   600K .......... .......... .......... .......... .......... 16% 71.3K 59s
   650K .......... .......... .......... .......... .......... 18% 33.5K 61s
   700K .......... .......... .......... .......... .......... 19% 70.3K 59s
   750K .......... .......... .......... .......... .......... 20% 69.9K 57s
   800K .......... .......... .......... .......... .......... 21% 46.9K 57s
   850K .......... .......... .......... .......... .......... 23% 23.0K 60s
   900K .......... .......... .......... .......... .......... 24% 62.0K 58s
   950K .......... .......... .......... .......... .......... 25% 82.9K 56s
  1000K .......... .......... .......... .......... .......... 27% 41.2K 56s
  1050K .......... .......... .......... .......... .......... 28% 57.8K 54s
  1100K .......... .......... .......... .......... .......... 29% 87.9K 52s
  1150K .......... .......... .......... .......... .......... 31% 88.4K 51s
  1200K .......... .......... .......... .......... .......... 32% 58.0K 49s
  1250K .......... .......... .......... .......... .......... 33% 73.3K 48s
  1300K .......... .......... .......... .......... .......... 34% 61.0K 47s
  1350K .......... .......... .......... .......... .......... 36% 64.8K 46s
  1400K .......... .......... .......... .......... .......... 37% 39.3K 45s
  1450K .......... .......... .......... .......... .......... 38% 50.3K 44s
  1500K .......... .......... .......... .......... .......... 40% 76.8K 43s
  1550K .......... .......... .......... .......... .......... 41% 76.5K 42s
  1600K .......... .......... .......... .......... .......... 42% 58.4K 41s
  1650K .......... .......... .......... .......... .......... 43% 62.6K 40s
  1700K .......... .......... .......... .......... .......... 45% 21.6K 40s
  1750K .......... .......... .......... .......... .......... 46% 53.1K 40s
  1800K .......... .......... .......... .......... .......... 47% 71.8K 38s
  1850K .......... .......... .......... .......... .......... 49% 73.8K 37s
  1900K .......... .......... .......... .......... .......... 50% 77.2K 36s
  1950K .......... .......... .......... .......... .......... 51% 67.0K 35s
  2000K .......... .......... .......... .......... .......... 52% 74.3K 34s
  2050K .......... .......... .......... .......... .......... 54% 60.5K 33s
  2100K .......... .......... .......... .......... .......... 55% 81.4K 31s
  2150K .......... .......... .......... .......... .......... 56% 67.5K 30s
  2200K .......... .......... .......... .......... .......... 58% 60.5K 29s
  2250K .......... .......... .......... .......... .......... 59% 62.7K 28s
  2300K .......... .......... .......... .......... .......... 60%  100K 27s
  2350K .......... .......... .......... .......... .......... 62% 51.8K 26s
  2400K .......... .......... .......... .......... .......... 63% 70.7K 25s
  2450K .......... .......... .......... .......... .......... 64% 71.9K 24s
  2500K .......... .......... .......... .......... .......... 65% 66.6K 23s
  2550K .......... .......... .......... .......... .......... 67% 67.4K 22s
  2600K .......... .......... .......... .......... .......... 68% 64.9K 22s
  2650K .......... .......... .......... .......... .......... 69% 75.0K 21s
  2700K .......... .......... .......... .......... .......... 71% 65.2K 20s
  2750K .......... .......... .......... .......... .......... 72% 59.8K 19s
  2800K .......... .......... .......... .......... .......... 73% 56.9K 18s
  2850K .......... .......... .......... .......... .......... 74% 58.5K 17s
  2900K .......... .......... .......... .......... .......... 76% 64.3K 16s
  2950K .......... .......... .......... .......... .......... 77% 49.6K 15s
  3000K .......... .......... .......... .......... .......... 78% 34.5K 15s
  3050K .......... .......... .......... .......... .......... 80% 42.4K 14s
  3100K .......... .......... .......... .......... .......... 81% 56.1K 13s
  3150K .......... .......... .......... .......... .......... 82% 76.3K 12s
  3200K .......... .......... .......... .......... .......... 83% 58.1K 11s
  3250K .......... .......... .......... .......... .......... 85% 69.8K 10s
  3300K .......... .......... .......... .......... .......... 86% 74.8K 9s
  3350K .......... .......... .......... .......... .......... 87% 72.1K 8s
  3400K .......... .......... .......... .......... .......... 89% 65.0K 7s
  3450K .......... .......... .......... .......... .......... 90% 72.8K 6s
  3500K .......... .......... .......... .......... .......... 91% 50.4K 6s
  3550K .......... .......... .......... .......... .......... 93% 30.3K 5s
  3600K .......... .......... .......... .......... .......... 94% 54.0K 4s
  3650K .......... .......... .......... .......... .......... 95% 50.8K 3s
  3700K .......... .......... .......... .......... .......... 96% 53.6K 2s
  3750K .......... .......... .......... .......... .......... 98% 55.2K 1s
  3800K .......... .......... .......... .......... .......... 99% 47.6K 0s
  3850K .......... .........                                  100% 25.3K=69s

2009-01-26 16:04:36 (55.8 KB/s) - `./install_flash_player_10_linux.tar.gz' saved [3962157/3962157]

Download done.
Flash Plugin installed.

Setting up libao-pulse (0.9.3-1) ...
Setting up libgconfmm-2.6-1c2 (2.24.0-0ubuntu1) ...

Setting up libglademm-2.4-1c2a (2.6.6-1) ...

Setting up libpulse-mainloop-glib0 (0.9.10-2ubuntu9.2) ...

Setting up paman (0.9.4-1ubuntu1) ...

Setting up pulseaudio-module-zeroconf (0.9.10-2ubuntu9.2) ...
Setting up paprefs (0.9.6-2ubuntu1) ...

Setting up pavucontrol (0.9.6+svn20080426-1ubuntu1) ...

Setting up pavumeter (0.9.3-1ubuntu1) ...

Setting up padevchooser (0.9.3-2ubuntu3) ...

Setting up libsdl1.2debian-pulseaudio (1.2.13-2ubuntu1) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
alex@Thing1:~$ sudo apt-get remove --purge libflashsupport flashplugin-nonfree-extrasound
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libflashsupport is not installed, so not removed
Package flashplugin-nonfree-extrasound is not installed, so not removed
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.27-7 linux-headers-2.6.27-7-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
alex@Thing1:~$ pavucontrol
alex@Thing1:~$ pulseaudio & pavucontrol
[1] 10000
W: ltdl-bind-now.c: Failed to find original dlopen loader.
E: pid.c: Daemon already running.
E: main.c: pa_pid_file_create() failed.
[1]+  Exit 1                  pulseaudio
alex@Thing1:~$ gksudo gedit /etc/apt/sources.list
alex@Thing1:~$ sudo apt-get update && sudo apt-get dist-upgrade
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release.gpg
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Translation-en_US
Get:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release [27.6kB]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid Release    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Sources    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Packages 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Sources
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Packages
Get:2 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages [5131B]
Get:3 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Sources [1237B]       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Sources
Fetched 34.0kB in 2s (12.9kB/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
alex@Thing1:~$ alsamixer -Dhw


................................

NOTE:  Rear Speakers did not work after these above tasks.

I will post when they work

---

### Post by vipertga on 2009-01-26
I tired this site and the "easy way" didnt work.


[http://ubuntuforums.org/showthread.php?t=795525](http://ubuntuforums.org/showthread.php?t=795525)

---

### Post by Linuxdork on 2009-01-26
> **vipertga said:**
> I tired this site and the "easy way" didnt work.


[http://ubuntuforums.org/showthread.php?t=795525](http://ubuntuforums.org/showthread.php?t=795525)


The hard way looks like what you're going to have to do.  I didn't find any settings that would just enable it.  I would recommend backing everything up and going the hard route.  If it doesn't work, just replace your changes with the backups.  At least now you have a semi-working configuration.  Keep us in the loop.  I hope you get all of this working.

---

### Post by sour17 on 2009-02-08
Hello-I'm having trouble getting my sound to work in Ubuntu Intrepid. I have a Audigy 2 ZS and I feel like I have tried everything. Some help would be great. Thanks

sour@sour-desktop:~$  aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Audigy2 [Audigy 2 ZS [SB0350]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
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
card 0: Audigy2 [Audigy 2 ZS [SB0350]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: Audigy2 [Audigy 2 ZS [SB0350]], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Audigy2 [Audigy 2 ZS [SB0350]], device 4: p16v [p16v]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: ICH5 [Intel ICH5], device 0: Intel ICH [Intel ICH5]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: ICH5 [Intel ICH5], device 4: Intel ICH - IEC958 [Intel ICH5 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
sour@sour-desktop:~$ pkill pulseaudio; sleep 2; pulseaudio -vv
I: main.c: PolicyKit refuses acquire-high-priority privilige.
I: main.c: Called SUID root and real-time/high-priority scheduling was requested in the configuration. However, we lack the necessary priviliges:
I: main.c: We are not in group 'pulse-rt' and PolicyKit refuse to grant us priviliges. Dropping SUID again.
I: main.c: For enabling real-time scheduling please acquire the appropriate PolicyKit priviliges, or become a member of 'pulse-rt', or increase the RLIMIT_NICE/RLIMIT_RTPRIO resource limits for this user.
I: main.c: Note that real-time/high-priority scheduling is NOT normally required. If you experience crackling or other sound anomalies, consider one or more of the above solutions.
I: main.c: High-priority scheduling enabled in configuration but now allowed by policy. Disabling forcibly.
W: ltdl-bind-now.c: Failed to find original dlopen loader.
W: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
W: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
I: main.c: This is PulseAudio 0.9.10
I: main.c: Page size is 4096 bytes
I: main.c: Fresh high-resolution timers available! Bon appetit!
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-hal-detect.so': success
I: module-hal-detect.c: Trying capability alsa
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/computer_alsa_timer
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/computer_alsa_sequencer
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_8086_24d5_sound_card_0_alsa_playback_4
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_8086_24d5_sound_card_0_alsa_capture_3
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_8086_24d5_sound_card_0_alsa_capture_2
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_8086_24d5_sound_card_0_alsa_capture_1
D: module-hal-detect.c: Loading module-alsa-sink with arguments 'device_id=1 sink_name=alsa_output.pci_8086_24d5_sound_card_0_alsa_playback_0'
D: alsa-util.c: Trying front:1...
I: module-alsa-sink.c: Successfully opened device front:1.
I: module-alsa-sink.c: Successfully enabled mmap() mode.
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:1
I: alsa-util.c: Unable to attach to mixer front:1: No such file or directory
I: alsa-util.c: Successfully attached to mixer 'hw:1'
I: alsa-util.c: Using mixer control "Master".
I: sink.c: Created sink 0 "alsa_output.pci_8086_24d5_sound_card_0_alsa_playback_0" with sample spec "s16le 2ch 44100Hz"
I: source.c: Created source 0 "alsa_output.pci_8086_24d5_sound_card_0_alsa_playback_0.monitor" with sample spec "s16le 2ch 44100Hz"
I: module-alsa-sink.c: Using 8 fragments of size 1760 bytes.
I: alsa-util.c: All 2 channels can be mapped to mixer channels. Using hardware volume control.
D: module-alsa-sink.c: Thread starting up
D: rtpoll.c: Acquired POSIX realtime signal SIGRTMIN+29
I: module-alsa-sink.c: Starting playback.
I: module.c: Loaded "module-alsa-sink" (index: #0; argument: "device_id=1 sink_name=alsa_output.pci_8086_24d5_sound_card_0_alsa_playback_0").
D: module-hal-detect.c: Loading module-alsa-source with arguments 'device_id=1 source_name=alsa_input.pci_8086_24d5_sound_card_0_alsa_capture_0'
D: alsa-util.c: Trying front:1...
I: module-alsa-source.c: Successfully opened device front:1.
I: module-alsa-source.c: Successfully enabled mmap() mode.
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:1
I: alsa-util.c: Unable to attach to mixer front:1: No such file or directory
I: alsa-util.c: Successfully attached to mixer 'hw:1'
I: alsa-util.c: Using mixer control "Capture".
I: source.c: Created source 1 "alsa_input.pci_8086_24d5_sound_card_0_alsa_capture_0" with sample spec "s16le 2ch 44100Hz"
I: module-alsa-source.c: Using 8 fragments of size 1760 bytes.
I: alsa-util.c: All 2 channels can be mapped to mixer channels. Using hardware volume control.
D: module-alsa-source.c: Thread starting up
D: rtpoll.c: Acquired POSIX realtime signal SIGRTMIN+28
I: module.c: Loaded "module-alsa-source" (index: #1; argument: "device_id=1 source_name=alsa_input.pci_8086_24d5_sound_card_0_alsa_capture_0").
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_8086_24d5_sound_card_0_alsa_control__1
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_1102_4_sound_card_0_alsa_playback_4
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_1102_4_sound_card_0_alsa_capture_4
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_1102_4_sound_card_0_alsa_playback_3
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_1102_4_sound_card_0_alsa_playback_2
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_1102_4_sound_card_0_alsa_capture_2
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_1102_4_sound_card_0_alsa_capture_1
D: module-hal-detect.c: Loading module-alsa-sink with arguments 'device_id=0 sink_name=alsa_output.pci_1102_4_sound_card_0_alsa_playback_0'
D: alsa-util.c: Trying front:0...
I: module-alsa-sink.c: Successfully opened device front:0.
I: module-alsa-sink.c: Successfully enabled mmap() mode.
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:0
I: alsa-util.c: Unable to attach to mixer front:0: No such file or directory
I: alsa-util.c: Successfully attached to mixer 'hw:0'
I: alsa-util.c: Using mixer control "Master".
I: sink.c: Created sink 1 "alsa_output.pci_1102_4_sound_card_0_alsa_playback_0" with sample spec "s16le 2ch 44100Hz"
I: source.c: Created source 2 "alsa_output.pci_1102_4_sound_card_0_alsa_playback_0.monitor" with sample spec "s16le 2ch 44100Hz"
I: module-alsa-sink.c: Using 8 fragments of size 1760 bytes.
I: alsa-util.c: ALSA device lacks independant volume controls for each channel, falling back to software volume control.
D: module-alsa-sink.c: Thread starting up
D: rtpoll.c: Acquired POSIX realtime signal SIGRTMIN+27
I: module-alsa-sink.c: Starting playback.
I: module.c: Loaded "module-alsa-sink" (index: #2; argument: "device_id=0 sink_name=alsa_output.pci_1102_4_sound_card_0_alsa_playback_0").
D: module-hal-detect.c: Loading module-alsa-source with arguments 'device_id=0 source_name=alsa_input.pci_1102_4_sound_card_0_alsa_capture_0'
D: alsa-util.c: Trying front:0...
ALSA lib setup.c:96:(snd_sctl_install) Cannot lock ctl elem
I: alsa-util.c: PCM device front:0 refused our hw parameters: Device or resource busy
D: alsa-util.c: Trying surround40:0...
I: alsa-util.c: Couldn't open PCM device surround40:0: Device or resource busy
D: alsa-util.c: Trying surround41:0...
I: alsa-util.c: Couldn't open PCM device surround41:0: Device or resource busy
D: alsa-util.c: Trying surround50:0...
I: alsa-util.c: Couldn't open PCM device surround50:0: Device or resource busy
D: alsa-util.c: Trying surround51:0...
I: alsa-util.c: Couldn't open PCM device surround51:0: Device or resource busy
D: alsa-util.c: Trying surround71:0...
I: alsa-util.c: Couldn't open PCM device surround71:0: Device or resource busy
D: alsa-util.c: Trying hw:0 as last resort...
I: module-alsa-source.c: Successfully opened device hw:0.
I: module-alsa-source.c: Successfully enabled mmap() mode.
I: alsa-util.c: Successfully attached to mixer 'hw:0'
I: alsa-util.c: Cannot find mixer control "Capture".
I: alsa-util.c: Using mixer control "Mic".
I: source.c: Created source 3 "alsa_input.pci_1102_4_sound_card_0_alsa_capture_0" with sample spec "s16le 2ch 44100Hz"
I: module-alsa-source.c: Using 2 fragments of size 1792 bytes.
I: alsa-util.c: All 2 channels can be mapped to mixer channels. Using hardware volume control.
D: module-alsa-source.c: Thread starting up
D: rtpoll.c: Acquired POSIX realtime signal SIGRTMIN+26
I: module.c: Loaded "module-alsa-source" (index: #3; argument: "device_id=0 source_name=alsa_input.pci_1102_4_sound_card_0_alsa_capture_0").
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_1102_4_sound_card_0_alsa_midi_3
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_1102_4_sound_card_0_alsa_midi_2
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_1102_4_sound_card_0_alsa_midi_1
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_1102_4_sound_card_0_alsa_midi_0
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_1102_4_sound_card_0_alsa_hw_specific_2
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_1102_4_sound_card_0_alsa_hw_specific_0
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_1102_4_sound_card_0_alsa_control__1
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_1002_aa18_sound_card_0_alsa_playback_3
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_1002_aa18_sound_card_0_alsa_control__1
I: module-hal-detect.c: Loaded 4 modules.
I: module.c: Loaded "module-hal-detect" (index: #4; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-esound-protocol-unix.so': success
I: module.c: Loaded "module-esound-protocol-unix" (index: #5; argument: "").
I: protocol-native.c: loading cookie from disk.
I: module.c: Loaded "module-native-protocol-unix" (index: #6; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-gconf.so': success
I: module.c: Loaded "module-gconf" (index: #7; argument: "").
I: module.c: Loaded "module-volume-restore" (index: #8; argument: "").
D: module-default-device-restore.c: Restored default sink 'alsa_output.pci_8086_24d5_sound_card_0_alsa_playback_0'.
D: core-subscribe.c: dropped redundant event.
D: module-default-device-restore.c: Restored default source 'alsa_input.pci_8086_24d5_sound_card_0_alsa_capture_0'.
I: module.c: Loaded "module-default-device-restore" (index: #9; argument: "").
I: module.c: Loaded "module-rescue-streams" (index: #10; argument: "").
D: module-suspend-on-idle.c: Sink alsa_output.pci_8086_24d5_sound_card_0_alsa_playback_0 becomes idle.
D: module-suspend-on-idle.c: Sink alsa_output.pci_1102_4_sound_card_0_alsa_playback_0 becomes idle.
D: module-suspend-on-idle.c: Source alsa_output.pci_8086_24d5_sound_card_0_alsa_playback_0.monitor becomes idle.
D: module-suspend-on-idle.c: Source alsa_input.pci_8086_24d5_sound_card_0_alsa_capture_0 becomes idle.
D: module-suspend-on-idle.c: Source alsa_output.pci_1102_4_sound_card_0_alsa_playback_0.monitor becomes idle.
D: module-suspend-on-idle.c: Source alsa_input.pci_1102_4_sound_card_0_alsa_capture_0 becomes idle.
I: module.c: Loaded "module-suspend-on-idle" (index: #11; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-x11-publish.so': success
D: module-x11-publish.c: using already loaded auth cookie.
I: module.c: Loaded "module-x11-publish" (index: #12; argument: "").
I: main.c: Daemon startup complete.
D: module-hal-detect.c: dbus: interface=org.freedesktop.DBus, path=/org/freedesktop/DBus, member=NameAcquired
I: module-suspend-on-idle.c: Source alsa_input.pci_1102_4_sound_card_0_alsa_capture_0 idle for too long, suspending ...
I: module-alsa-source.c: Device suspended...
I: module-suspend-on-idle.c: Source alsa_output.pci_1102_4_sound_card_0_alsa_playback_0.monitor idle for too long, suspending ...
I: module-suspend-on-idle.c: Source alsa_input.pci_8086_24d5_sound_card_0_alsa_capture_0 idle for too long, suspending ...
I: module-alsa-source.c: Device suspended...
I: module-suspend-on-idle.c: Source alsa_output.pci_8086_24d5_sound_card_0_alsa_playback_0.monitor idle for too long, suspending ...
I: module-suspend-on-idle.c: Sink alsa_output.pci_1102_4_sound_card_0_alsa_playback_0 idle for too long, suspending ...
I: module-alsa-sink.c: Device suspended...
I: module-suspend-on-idle.c: Sink alsa_output.pci_8086_24d5_sound_card_0_alsa_playback_0 idle for too long, suspending ...
I: module-alsa-sink.c: Device suspended...

---

### Post by jtliii on 2009-03-05
mc4man THANK YOU!!!

I have been fighting this for days.  Unchecking the box worked for me.

THANK YOU, THANK YOU, THANK YOU!!!!!

---

### Post by jred04 on 2009-03-09
Hey guys, I'm a total linux newbie, but I just intalled Ubuntu 8.10 and had similar issues. After reading your posts and some others I unchecked the Audigy Analog/Digital Output box under the Preferences-->switches tab in the volume control gui.This instantly gave me audio, but it's not the best quality yet. MP3 playback is a bit choppy, but listenable. Not sure if it's due to the files being streamed from USB2 external HDD, but it played fine like that under win XP. 

With respect to getting the sound to work initially, I also made sure to go under system-->preferences-->sound and manually set audigy multichannel playback under each of the drop down menus before looking at the switches in the volume control gui. After all this, when I view alsa mixer it says Audigy 2zs and I am able to view all the various channels by using the arrow keys. However, before completing these steps it only listed the pulse audio. 

Finally, someone had mentioned previously that pulseaudio should not be running in the background after completing these steps. I checked in the sys monitor and found it to be running but not hogging any resources like the previous post mentioned. Either way I ended the process and no harmful effects have been noticed. Maybe someone can shed some more light on that issue. Anyway, hope this helps someone. Thanks to all the other members for getting me this far. You guys rock.

---

### Post by green hornet1 on 2009-03-09
I am running ubuntu 8.10 and i have install new soundblaster audogy se sound card some media player such as vlc and totem player i have sound on other player i dont. on the firefox browser i have no sound on any video . and i cant get mic to work any help would appericated you can contact me     


                                      [email]littlekingtut@bellsouth.net[/email]

---

