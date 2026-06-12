---
title: "Audacious mac plugin amd64 problem"
date: 2008-01-03
forum: Multimedia &amp; Video
---

### Post by liquid77 on 2008-01-03
I am trying to install libmac for the mac plugin for audacious on amd64 , but unfortunately getlibs cannot determine the dependencies for this lib.Any suggestions?

---

### Post by Perfect Storm on 2008-01-04
What do you need it for, if you're running amd64?

---

### Post by liquid77 on 2008-01-04
I have some Pink Floyd albums in APE format and I want to play them on audacious.I found the plugin and the 2 dependencies but ti's all for i386 and I cannot get them installed , not even with getlibs.Any alternatives for Monkey's audio files playback?Maybe I should try and install the monkey's audio player with wine...

---

### Post by Perfect Storm on 2008-01-04
Try follow my guide: [http://ubuntuforums.org/showthread.php?p=4072585](http://ubuntuforums.org/showthread.php?p=4072585)
It will have **Apple Lossless Plugin** I guess it can play that format.

---

### Post by liquid77 on 2008-01-04
Actually I have audacious and the aplle loseless plugin installed but still it cannot play the ape file.I have tried to install with wine the converter from monkey audio and it works fine.Still I would like to find something from Linux or even Java.The jlGui player (java player) says it's an invalid file..?But as I said it plays fine with monkey's audio converter.

---

### Post by Perfect Storm on 2008-01-04
I'll see what I can find to help you out.

---

### Post by Perfect Storm on 2008-01-04
Okay found something; Gnormalize: [http://gnormalize.sourceforge.net/](http://gnormalize.sourceforge.net/)

> gnormalize decodes the MP3/MP4/MPC/OGG/APE/FLAC file to WAV, then normalizes the WAV to a targeted volume level and re-encodes it. Moreover, gnormalize can extract Audio CD track and output as various popular audio formats (MP3, MP4, MPC, OGG, APE, FLAC, WAV) with fast speed and high quality. gnormalize can also convert audio format between MP3, MP4, MPC, OGG, APE and FLAC with high fidelity, which meets your need to play and collect audio files. It can change the encoding and Metadata (tag) properties of final normalized files.

gnormalize can be used to adjust the volume of audio files to a standard volume level, where different recording levels on different albums can cause the volume to vary greatly from song to song.

gnormalize is an alternative for replaygain, because "there is no consistent standard by which to define the appropriate replay gain which mp3 encoders and players agree on, and no automatic way to set the volume adjustment for each track". 

---

### Post by Perfect Storm on 2008-01-04
OKay, it seems it also need that lib, so I looked it up and it also seem that for whatever reason Apple shut down the linux lib.

Can you give me a link to those packages you found (plus -dev).

---

### Post by liquid77 on 2008-01-04
Thank's for the help! I found the plugin and the accomanying libs from inside the forum : [http://ubuntuforums.org/showthread.php?t=584082&highlight=audacious+mac](http://ubuntuforums.org/showthread.php?t=584082&highlight=audacious+mac) .
I will try gnormalize and see what happens.

---

### Post by liquid77 on 2008-01-04
Gnormalize worked fine.. :guitar: Thank's again..

---

