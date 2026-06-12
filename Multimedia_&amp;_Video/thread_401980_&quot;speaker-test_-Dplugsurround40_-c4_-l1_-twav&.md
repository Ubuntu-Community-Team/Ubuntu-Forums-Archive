---
title: "&quot;speaker-test -Dplug:surround40 -c4 -l1 -twav&quot; wont work"
date: 2007-04-05
forum: Multimedia &amp; Video
---

### Post by george_swine on 2007-04-05
```
speaker-test -Dplug:surround40 -c4 -l1 -twav
```

Won't work anymore. It used to, and I got sound coming from all four speakers, the 5.1 version wouldn't work and I didn't try the 7.1 since I don't have a 7.1 card.

I have two sound cards, one onboard and one I put it. The onboard one is the one from the GA-965p-DS4 I couldn't get surround sound working on it so I put in a sound blaster LIVE. Well that doesn't work either, but I got close I could get all four working with this command:

```
speaker-test -Dplug:surround40 -c4 -l1 -twav
```

Now that command doesn't work anymore, I have this error:

```
ALSA lib confmisc.c:1105:(snd_func_refer) Unable to find definition 'defaults.pcm.surround51.card'
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib confmisc.c:242:(snd_func_getenv) error evaluating default
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_getenv returned error: No such file or directory
ALSA lib conf.c:3936:(snd_config_expand) Args evaluate error: No such file or directory
ALSA lib pcm.c:2146:(snd_pcm_open_noupdate) Unknown PCM surround51
aplay: main:547: audio open error: No such file or directory

```

---

### Post by george_swine on 2007-04-05
My default soundcard is set to my soundblaster. I did this via system > preferences > sound.

---

### Post by george_swine on 2007-04-05
If I use `multichannel playback` in the sound option I can hear a beeping noise coming from all speakers, I using 5 and a sub.

---

### Post by george_swine on 2007-04-05
If I put 'Multichannel Playback' in xmms as the device it wont work.

Also when 

```
speaker-test -Dplug:surround40 -c4 -l1 -twav
```

Was working if I put 

```
plug:surround41
```

in the device it still wouldn't work.

---

### Post by george_swine on 2007-04-05
Will no one help George Swine?

---

### Post by george_swine on 2007-04-06
Will no one help George Swine?

---

