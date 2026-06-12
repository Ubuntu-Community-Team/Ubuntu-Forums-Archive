---
title: "mod radio uk"
date: 2010-04-14
forum: Multimedia Software
---

### Post by jeff betts on 2010-04-14
I'm trying to listen to a station called "mod radio uk" but am getting no sound. Each time I go to the site it asks to look for a suitable plugin but cannot find one. It says that it is looking for a text/html decoder. Everything else to do with sound and music is working fine. I've listened to the station before when I had Linpus  and an earlier Ubuntu (9.04 I think) installed.

UNR 9.10 chrome & firefox on AOA-110-aw

---

### Post by WinterRain on 2010-04-14
Mod radio UK works for me. As far as codecs I'm using, I have **non-free-codecs**, **flash**, **java**, and **gecko-mediaplayer** for firefox.

---

### Post by jeff betts on 2010-04-15
I had non-free codecs, java and flash, and tried gecko media player to no avail. Went to my dad's this morning (8.04LTS)and couldn't get it to play there. Thanks tho, will keep trying.

---

### Post by andrew.46 on 2010-04-15
Hi jeff,

Plays ok with MPlayer:

```

andrew@skamandros~$ **[COLOR="Red"]mplayer -playlist http://www.modradiouk.net/listen.ram[/COLOR]**
Resolving www.modradiouk.net for AF_INET6...
Couldn't resolve name for AF_INET6: www.modradiouk.net
Resolving www.modradiouk.net for AF_INET...
Connecting to server www.modradiouk.net[77.232.72.34]: 80...
Cache size set to 320 KBytes
MPlayer SVN-r31036-4.3.3 (C) 2000-2010 MPlayer Team

Playing http://87.117.250.5:9104/.
Resolving 87.117.250.5 for AF_INET6...
Couldn't resolve name for AF_INET6: 87.117.250.5
Connecting to server 87.117.250.5[87.117.250.5]: 9104...
Name   : Mod Radio UK
Genre  : Mod
Website: http://www.modradiouk.net
Public : yes
Bitrate: 64kbit/s
Cache size set to 320 KBytes
Cache fill: 17.50% (57344 bytes)   
Audio only file format detected.
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 22050 Hz, 2 ch, s16le, 64.0 kbit/9.07% (ratio: 8000->88200)
**[COLOR="Red"]Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)[/COLOR]**
==========================================================================
AO: [oss] 22050Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A:  11.4 (11.4) of -0.1 (unknown)  0.4% 68% 

```

I see it is an mp3 stream, perhaps your system is not setup for mp3 streaming? BTW the actual url of the stream seems to be *http://87.117.250.5:9104/* and this might be an easier one to test...

All the best,

Andrew

---

### Post by jeff betts on 2010-05-19
I gave up then came back to it after upgrading to Lucid - mplayer + gecko & most importantly remember to tell Firefox which app to use to play mp3s.

Thanks all

Jeff :)

---

