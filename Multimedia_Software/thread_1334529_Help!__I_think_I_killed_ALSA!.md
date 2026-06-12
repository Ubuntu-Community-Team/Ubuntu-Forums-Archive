---
title: "Help!  I think I killed ALSA!"
date: 2009-11-22
forum: Multimedia Software
---

### Post by Superluke on 2009-11-22
I've been having trouble with audio since I upgraded to Karmic... finally got the headphone jack and line-out to work at the same time but I lost input from my webcam's built-in mic.

Followed directions to remove pulseAudio.

...But then I think I killed ALSA as well.  I get errors in every audio software I have.

aplay gives me:
aplay: device_list:223: no soundcards found...
 
lspci detects the card, no prob:
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)

I did upgrade ALSA to 1.0.21 but no difference at all.  Compiled fine and everything.

alsaconf seems to work ok, I think (No errors)

I also get this:
cat: /proc/asound/version: No such file or directory

so I don't think ALSA is even loading...  Here is the alsa info:

 ALSA Information Script v 0.4.58
--------------------------------

This script visits the following commands/files to collect diagnostic
information about your ALSA installation and sound related hardware.

  dmesg
  lspci
  lsmod
  aplay
  amixer
  alsactl
  /proc/asound/
  /sys/class/sound/
  ~/.asoundrc (etc.)

See 'alsa-info.sh --help' for command line options.

cat: /proc/asound/version: No such file or directory
grep: /proc/asound/cards: No such file or directory
cat: /proc/asound/cards: No such file or directory
WARNING: All config files need .conf: /etc/modprobe.d/sound, it will be ignored in a future release.
cat: /proc/asound/modules: No such file or directory
ls: cannot access /dev/snd/*: No such file or directory
grep: /proc/asound/cards: No such file or directory
/usr/sbin/alsactl: save_state:1502: No soundcards found...
cat: /tmp/alsa-info.mExhKVAAiy/alsactl.tmp: No such file or directory


HAAAAALP!

---

### Post by Uncle Spellbinder on 2009-11-22
Karmic uses Pulse Audio. I'm learning to live with it. Too big a hassle to revert to ALSA.

---

### Post by ajgreeny on 2009-11-22
Most of the sound problems in karmic seem to result from the default levels set for various audio channels and hardware of your machine.  The best way to solve the problems as far as I can see is to run ```
alsamixer
```in terminal and make sure those slider levels are not muted or too low.

The alsamixer window can be navigated with the cursor keys to move from slider to slider and to raise and lower the levels, M to mute or unmute channels, and tab to move between playback, capture and all channels.  Using that may have solved your problems, so perhaps reinstall pulse if needed and undo all the things you originally did, then try again.  As I understand it pulse runs on top of alsa and still uses it to actually produce the sounds that it then manages.

---

### Post by Superluke on 2009-11-22
When I try to open alsamixer I get:

alsamixer: function snd_ctl_open failed for default: No such file or directory


The problem is way worse than volume controls!

---

### Post by rolandixor on 2009-11-25
have you tried reinstalling all the related alsa packages from synaptic? that (might) fix your issue enough for you to then recompile. If not, we can walk through the long process of recreating the missing files.

---

### Post by Superluke on 2009-11-25
I've reinstalled everything Alsa, as far as I know, frum Synaptic and no dice.  Any help would be great!

---

### Post by Dirtpile on 2009-11-25
[SIZE=2]Try this, it should effectively refresh ALSA.
[/SIZE]```
sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
```
Followed by:
```
 
sudo apt-get install linux-sound-base alsa-base alsa-utils

```
 
You will have to set-up your alsa settings but it just might get you working again.

---

### Post by Superluke on 2009-11-28
That did the job, thanks!

---

