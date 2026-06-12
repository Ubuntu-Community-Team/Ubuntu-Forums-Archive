---
title: "Card not found - but it is there"
date: 2007-05-22
forum: Multimedia &amp; Video
---

### Post by bananabob on 2007-05-22
I have a problem with my sound card.
I can play sound using Amarok - but when I use Firefox and go to youtube I get no sound.

I have dug around a bit in the forums and with google but can find nothing that helps.

If i run the command aplay --list-devices I get this result
> 
bananabob@thorium:~$ aplay --list-devices
**** List of PLAYBACK Hardware Devices ****
card 0: M2496 [M Audio Audiophile 24/96], device 0: ICE1712 multi [ICE1712 multi]
  Subdevices: 1/1
  Subdevice #0: subdevice #0



If I run aplay to play an mp3 I get this result

> bananabob@thorium:~$ aplay /home/audio/download/twu-20070519-1345-Internet_Phone_Calls-064.mp3 
ALSA lib confmisc.c:670:(snd_func_card_driver) cannot find card 'M2946'
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:391:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1070:(snd_func_refer) error evaluating name
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3947:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2146:(snd_pcm_open_noupdate) Unknown PCM default
aplay: main:547: audio open error: No such device


Where those smilies are should be colon open bracket : (

I also get a similar result when running firefox 

I also get the same messages when running gedit.

I have tried firefox by running > sudo -H firefox and the sound works.

Is there anyone that can help me with this please.

---

### Post by mitch.c on 2007-05-22
Are you saying that running firefox using sudo sound works correctly? What about 'sudo aplay file_name'?

If so, it sounds like a permission issue. What are permissions for /dev/dsp?

-- 
Mitch

---

### Post by bananabob on 2007-05-22
> 
ls -all /dev/dsp
crw-rw---- 1 root audio 14, 3 2007-05-23 09:19 /dev/dsp



and from sudo aplay
> 
sudo aplay /home/audio/download/twu-20070519-1345-Internet_Phone_Calls-064.mp3 
Password:
ALSA lib confmisc.c:670: (snd_func_card_driver) cannot find card 'M2946'
ALSA lib conf.c:3479: (_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:391: (snd_func_concat) error evaluating strings
ALSA lib conf.c:3479: (_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1070: (snd_func_refer) error evaluating name
ALSA lib conf.c:3479: (_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3947: (snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2146: (snd_pcm_open_noupdate) Unknown PCM default
aplay: main:547: audio open error: No such device



---

### Post by wr3ck on 2007-05-22
Same for me here
on Feisty
I did install a bunch of packages before a reboot... so I don't see what exactly it could be.
Please help us! ;)

---

### Post by bananabob on 2007-05-23
I have managed to get sound in Firefox going.

I did this by renaming two files so that they would not be found by the system.
the files were .asound whiich contains the following
> # ALSA library configuration file

# Include settings that are under the control of asoundconf(1).
# (To disable these settings, comment out this line.)
</home/bananabob/.asoundrc.asoundconf>
and .asoundrc.asoundconf which contains the following
> # ALSA library configuration file managed by asoundconf(1).
#
# MANUAL CHANGES TO THIS FILE WILL BE OVERWRITTEN!
#
# Manual changes to the ALSA library configuration should be implemented
# by editing the ~/.asoundrc file, not by editing this file.
!defaults.pcm.card PCM2702
defaults.ctl.card PCM2702
defaults.pcm.device 0
defaults.pcm.subdevice -1
defaults.pcm.nonblock 1
defaults.pcm.ipc_key 5678293
defaults.pcm.ipc_gid audio
defaults.pcm.ipc_perm 0660
defaults.pcm.dmix_max_periods 0
defaults.rawmidi.card 0
defaults.rawmidi.device 0
defaults.rawmidi.subdevice -1
defaults.hwdep.card 0
defaults.hwdep.device 0
defaults.timer.class 2
defaults.timer.sclass 0
defaults.timer.card 0
defaults.timer.device 0
defaults.timer.subdevice 0
!defaults.pcm.card M2946


I have tested aplay and that works as well. 

I assume that these files caused the problem. :p

Now all I need is to be able to control the input gain on my M Audio Audiophile 2496 card. :( So if you know a fix for that I would be happy to hear it.

---

### Post by mitch.c on 2007-05-23
alsamixer? alsactl? These are what I used to set my card.

---

