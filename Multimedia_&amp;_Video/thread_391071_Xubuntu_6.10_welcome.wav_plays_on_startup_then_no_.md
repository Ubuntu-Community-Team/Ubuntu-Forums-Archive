---
title: "Xubuntu 6.10 welcome.wav plays on startup then no more sound"
date: 2007-03-22
forum: Multimedia &amp; Video
---

### Post by sjan on 2007-03-22
Fresh install, tried all the suggestions from other forums (including [this one]("http://www.ubuntuforums.org/showthread.php?t=205449")) - but so far, no luck.

[FONT="Fixedsys"]aplay -l[/FONT] shows the proper card, drivers are loaded, (snd-intel8x0, snd-ac97, etc) alsamixer shows nothing muted, but after logging in if I run [FONT="Fixedsys"]ps -elf[/FONT] I see the following:

[FONT="Fixedsys"]4 S root      4508  4141  0  78   0 -   415 wait   14:28 ?        00:00:00 /bin/sh /usr/lib/gdmplay /usr/share/sounds/question.wav
4 S root      4509  4508  0  75   0 -  1061 41     14:28 ?        00:00:00 /usr/bin/aplay -q -N /usr/share/sounds/question.wav
1 S root      4513     1  0  75   0 -   986 25     14:28 ?        00:00:00 /usr/bin/aplay -q -N /usr/share/sounds/question.wav
[/FONT]

If I [FONT="Fixedsys"]killall aplay[/FONT] then I can get aplay to play the welcome.wav one more time, but that's it. Then there are no more sounds until the next reboot.

Also, not sure if this has anything to do with the sound issue but it seems like it does, trying to play anything in gxine results in a freeze (after 6 seconds for video, less than 1 second for audio) and I have to use xkill to get rid of the gxine window. Before this fresh install (after trying all the other fixes) I tried Amarok, Mplayer, and xmms with the same results as gxine (which is I why I think it is probably related to the sound issue.)

Once I have crashed out of gxine, restarting it I get an error that it can't find the input device? aplay -l still shows the sound card at that time.

Thanks

(PS new to Ubuntu, but not to Linux - longtime Gentoo user)




**************
Mods pls delete - reposted in [ Comprehensive Sound Problem Solutions Guide]("http://ubuntuforums.org/showthread.php?t=205449")

---

### Post by bnuytten on 2007-04-06
> **sjan said:**
> Fresh install, tried all the suggestions from other forums (including [this one]("http://www.ubuntuforums.org/showthread.php?t=205449")) - but so far, no luck.

[FONT="Fixedsys"]aplay -l[/FONT] shows the proper card, drivers are loaded, (snd-intel8x0, snd-ac97, etc) alsamixer shows nothing muted, but after logging in if I run [FONT="Fixedsys"]ps -elf[/FONT] I see the following:




After loading the module. correct the access rights on the sound devices as suggested on [this site ]("http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=C-Media&card=.&chip=CMI8338%2C+CMI8738%2C+CMI8768&module=cmipci#Inst")
```
root@juno:~# modprobe snd-cmipci
root@juno:~# ls -l /dev/dsp 
crw-rw---- 1 root audio 14, 3 2007-04-06 08:31 /dev/dsp
root@juno:~# chmod a+rw /dev/dsp /dev/mixer /dev/sequencer /dev/midi 
chmod: cannot access `/dev/midi': No such file or directory
root@juno:~# ls -l /dev/dsp /dev/mixer /dev/sequencer /dev/midi ls: /dev/midi: No such file or directory
crw-rw-rw- 1 root audio 14, 3 2007-04-06 08:31 /dev/dsp
crw-rw-rw- 1 root audio 14, 0 2007-04-06 08:31 /dev/mixer
crw-rw-rw- 1 root audio 14, 1 2007-04-05 22:39 /dev/sequencer

```


I have exactly the same problem. As root you can play sound, as normal user you can't. Got the test file from [here]("http://wahiduddin.net/troubleshooting/testing.wav").
```
bjorn@juno:~$ aplay /home/bjorn/testing.wav 
ALSA lib confmisc.c:670:(snd_func_card_driver) cannot find card '0'
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:391:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1070:(snd_func_refer) error evaluating name
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3947:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2146:(snd_pcm_open_noupdate) Unknown PCM default
aplay: main:547: audio open error: No such device

root@juno:~# aplay /home/bjorn/testing.wav 
Playing WAVE '/home/bjorn/testing.wav' : Signed 16 bit Little Endian, Rate 11025 Hz, Mono

```

I still cannot play audio as normal user, but at least I know for sure that the sound card is working properly.

---

### Post by bnuytten on 2007-04-06
Guess I found the rest of the answer. Adding your own user to the audio group, logging in and out seems to have fixed the problem.

```
root@juno:~# usermod -aG audio bjorn
```

Logout from the GUI as normal user, then log back in. 
```
bjorn@juno:~$ aplay /home/bjorn/testing.wav 
Playing WAVE '/home/bjorn/testing.wav' : Signed 16 bit Little Endian, Rate 11025 Hz, Mono

```

Granting all users access to the sound device can be reverted using this command
```
root@juno:~# chmod 660 /dev/dsp /dev/mixer /dev/sequencer /dev/midi
chmod: cannot access `/dev/midi': No such file or directory
root@juno:~# ls -l /dev/dsp /dev/mixer /dev/sequencer /dev/midi
ls: /dev/midi: No such file or directory
crw-rw---- 1 root audio 14, 3 2007-04-06 08:31 /dev/dsp
crw-rw---- 1 root audio 14, 0 2007-04-06 08:31 /dev/mixer
crw-rw---- 1 root audio 14, 1 2007-04-05 22:39 /dev/sequencer

```

---

