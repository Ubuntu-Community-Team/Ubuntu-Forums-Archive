---
title: "broken ALSA after installing alsa-lib"
date: 2020-12-08
forum: Multimedia Software
---

### Post by mileva1010 on 2020-12-08
Recently I started to learn about ALSA. I wanted to start with examples so I installed the alsa-lib-1.2.4 from [https://alsa-project.org/wiki/Download](https://alsa-project.org/wiki/Download). 
That caused the problems with the programs that uses ALSA lib so I uninstalled  alsa-lib package. 
However, it seems ALSA is broken now and I'm not sure ho to fix it. 

If I try to record the sound I get the following:

```
ssds:~/Desktop/alsa$ arecord -f S16_LE -d 10 -r 44100 -c 2  --device="hw:0,0" /tmp/test-mic.mp3
ALSA lib conf.c:3916:(snd_config_update_r) Cannot access file /usr/share/alsa/alsa.conf
ALSA lib pcm.c:2495:(snd_pcm_open_noupdate) Unknown PCM hw:0,0
arecord: main:788: audio open error: No such file or directory

```


When I run speaker-test, the output is similar:

```
speaker-test -c 2

speaker-test 1.1.3

Playback device is default
Stream parameters are 48000Hz, S16_LE, 1 channels
Using 16 octaves of pink noise
ALSA lib conf.c:3916:(snd_config_update_r) Cannot access file /usr/share/alsa/alsa.conf
ALSA lib pcm.c:2495:(snd_pcm_open_noupdate) Unknown PCM default
Playback open error: -2,No such file or directory

```Here is more information I could collect from my system:
```
aplay -L | grep :CARD
ALSA lib conf.c:3916:(snd_config_update_r) Cannot access file /usr/share/alsa/alsa.conf

```

```
cat /proc/asound/cards
 0 [PCH            ]: HDA-Intel - HDA Intel PCH
                      HDA Intel PCH at 0xa0430000 irq 169

```I'm not sure how to make ALSA work again on my Ubuntu 18.04. 
Thank you,

---

### Post by mileva1010 on 2020-12-08
I also realized that there is no /usr/share/alsa/alsa.conf file.

Running:

```

sudo apt-get install libasound2

```

gives me:

```

libasound2 is already the newest version (1.1.3-5ubuntu0.5).

```

Please help.

---

### Post by Yellow Pasque on 2020-12-08
```
sudo apt-get install --reinstall libasound2 libasound2-data libasound2-plugins
```

---

### Post by mileva1010 on 2020-12-08
Yes, that solved the problem. Thank you so much!

---

### Post by Yellow Pasque on 2020-12-08
You're welcome. Please mark the thread SOLVED (Thread Tools menu above first post).

---

