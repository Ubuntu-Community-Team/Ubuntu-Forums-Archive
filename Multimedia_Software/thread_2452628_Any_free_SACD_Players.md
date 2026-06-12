---
title: "Any free SACD Players"
date: 2020-10-26
forum: Multimedia Software
---

### Post by eby on 2020-10-26
Is there a free player that support SACD ISO in Ubuntu ?. or a compatible plugin/decoder ?.

The latest version of DeaDBeeF can't open iso files, even with latest ffmpeg, the [developer commented]("https://github.com/DeaDBeeF-Player/deadbeef/issues/683") sacd iso playback "may be with ffmpeg".

On Windows, foobar2000 with [sacddecoder]("https://sourceforge.net/projects/sacddecoder/") plugin does the job, unfortunately i could not get to load the iso under wine.

thanks,

---

### Post by Holger_Gehrke on 2020-10-26
If you look carefully at the sourceforge link you posted there is a link to a fork of mpd - music player daemon - with a sacd-plugin on the page.

Holger

---

### Post by eby on 2020-10-27
> **Holger_Gehrke said:**
> If you look carefully at the sourceforge link you posted there is a link to a fork of mpd - music player daemon - with a sacd-plugin on the page.

Tried that, could not get it to play sacd iso files, may be i'm have not configured it properly.

---

### Post by shantiq on 2020-10-27
Couple of thoughts

I have played many SACD with [COLOR=#000000]foobar2000 with [/COLOR][sacddecoder]("https://sourceforge.net/projects/sacddecoder/")[COLOR=#000000] plugin UNDER WINE with no problems so if that does not work are you sure the iso works on windows even?



PS   [this too]("https://askubuntu.com/questions/1128159/is-there-a-working-sacd-iso-player-for-ubuntu") might be of help[I][SIZE=1]  

[/SIZE][/I][/COLOR][COLOR=#696969]*[SIZE=1]**An alternate route where you unpack iso to wavs then to a lossless format whilst retaining the hi-specs**[/SIZE]*
[/COLOR][COLOR=#000000]

[/COLOR][COLOR=#000000]
[/COLOR]```
git clone https://github.com/Sound-Linux-More/sacd
cd sacd
make
sudo make install
```[COLOR=#000000]

see info on usage on link

BUT basically:


[/COLOR]```
sacd -i youriso.iso 

```

then


```
cd
``` into folder


Flac or Alac

```
for f in *.wav; do ffmpeg -i  "$f" "${f%.wav}.flac"; done

```

```
for f in *.wav; do ffmpeg -i  "$f" -c:a alac "${f%.wav}.m4a"; done

```[COLOR=#000000]


and hi-specs retained: and can be played in any player

[/COLOR]```
AudioID                                       : 1
Format                                   : ALAC
Codec ID                                 : alac
Codec ID/Info                            : Apple Lossless Audio Codec
Duration                                 : 7 min 18 s
Duration_LastFrame                       : -27 ms
Bit rate mode                            : Variable
Bit rate                                 : 6 494 kb/s
Nominal bit rate                         : 12.7 Mb/s
Channel(s)                               : 6 channels
Sampling rate                            : 88.2 kHz
Bit depth                                : 24 bits
Stream size                              : 339 MiB (100%)
Default                                  : Yes
Alternate group                          : 1



```[COLOR=#000000]





[/COLOR]

---

### Post by eby on 2020-10-30
> **shantiq said:**
> 
I have played many SACD with [COLOR=#000000]foobar2000 with [/COLOR][sacddecoder]("https://sourceforge.net/projects/sacddecoder/")[COLOR=#000000] plugin UNDER WINE with no problems so if that does not work are you sure the iso works on windows even?


On Windows 7(32bit), those sacd iso files do work with foobar2000 v1.4.8 with scddecoder plug-ins. Winetricks let you install only foobar2000 v1.4, could not get any other version to install.

P.S. I'm keeping W7 only for Nokia PC Suite and have not connected to Internet in years !!!!! :D

---

### Post by shantiq on 2020-10-30
hmmm weird   running v1.6.1   on Ubuntu 20.04

so do not go thru winetricks simply click[ here]("https://www.foobar2000.org/getfile/54b433ad48ddbf9c8a0de33367dfccef/foobar2000_v1.6.2.exe") go to the file right-click and properties /permissions/everyone

then right-click again Open with Wine install / it will overwrite your v1.4


Sorted i should say and hope :KS

Let us know how you get on

---

