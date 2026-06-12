---
title: "Only sudo can play sound"
date: 2008-12-03
forum: Multimedia Software
---

### Post by dmitrijledkov on 2008-12-03
Sudo can see soundcards, run alsamixer and play music. Without sudo it doesn't =(

Any help?

I've tried to use the defenite sound guide in the sticky but it has nothing about my problem.

I'm running 8.10 ubuntu server. My dream to turn it into alarm clock =D

```

dmitrij@samara:~$ aplay -l
aplay: device_list:215: no soundcards found...
dmitrij@samara:~$ sudo aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: I82801CAICH3 [Intel 82801CA-ICH3], device 0: Intel ICH [Intel 82801CA-ICH3]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
dmitrij@samara:~$ alsamixer

alsamixer: function snd_ctl_open failed for default: No such device
dmitrij@samara:~$ 

```

---

### Post by kostkon on 2008-12-03
Maybe you don't have the necessary *.asoundrc.asoundconf* and *.asoundrc* files in your home. Since you have the server version, I don't this there is any *PulseAudio* stuff installed.
Anyway, try doing
```
asoundconf list
```
this will show your card.

then, do the following and put the name of your card as it was shown by the previous command
```
asoundconf set-default-card nameofyourcard
```

Just to add the obvious, I want to be sure. Don't add *sudo* in from of these commands. ;)

---

### Post by kerry_s on 2008-12-03
sounds like your not in the audio group, check your /etc/group

---

### Post by dmitrijledkov on 2008-12-04
Heya. Thank you for suggestions but........ still only sudo can play music

Here is the results for actions you two have suggested.
```

dmitrij@samara:~$ asoundconf list
Names of available sound cards:
I82801CAICH3
dmitrij@samara:~$ asoundconf set-default-card I82801CAICH3
dmitrij@samara:~$ alsamixer 

alsamixer: function snd_ctl_open failed for default: No such device
dmitrij@samara:~$ mpg123 *any*song*.mp3 
[jack.c:201] error: Failed to open jack client: 0x1
[pulse.c:85] error: Failed to open pulse audio output: Connection refused
[audio.c:561] error: failed to open audio device
[audio.c:179] error: Unable to find a working output module in this list: alsa,oss,esd,jack,pulse,nas,arts
[audio.c:463] error: Failed to open audio output module
[mpg123.c:757] error: Failed to initialize output, goodbye.

```

and

```

dmitrij@samara:~$ cat /etc/group | grep audio
audio:x:29:pulse:root:mtdaapd:dmitrij

```

Sigh....

---

### Post by sinpalabras on 2008-12-06
Same problem here. Haven't found solution yet, via 8237 on board sound chip

---

