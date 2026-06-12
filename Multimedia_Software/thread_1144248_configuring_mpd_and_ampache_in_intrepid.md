---
title: "configuring mpd and ampache in intrepid"
date: 2009-04-30
forum: Multimedia Software
---

### Post by dasbooter on 2009-04-30
I struggled through the set up using this [[COLOR="Red"]ampache the easy way[/COLOR]]("http://ubuntuforums.org/showthread.php?t=546007"). And now I am stuck trying to get MPD  and localplay working with ampache. I am kind of hoping cjssmo sort of heres my plea. MPD is installed I havent started messing with the mpd.conf and I should probably enable the log for ampache but so far I have set up the local play instance I can add songs to the playlist but I get no sound...maybe somebody has done the grunt work... I am a little tired from the ampache install all didnt go as planned or as to the how to :) thanks for the help.

here is a little bit of the mpd log```
Apr 30 15:25 : interface 0: process command "play"
Apr 30 15:25 : playlist: play 0:"http://192.168.0.100/ampache/play/index.php?song=1330&uid=1&sid=2c19c324195e3606cd4a098518c9c170&name=/The%20Decemberists%20-%20A%20Bower%20Scene.mp3"
Apr 30 15:25 : copyMpdTagToOB: !acceptMetadata || !tag
Apr 30 15:25 : interface 0: command returned 0
Apr 30 15:25 : playlist: queue song 1:"http://192.168.0.100/ampache/play/index.php?song=1330&uid=1&sid=ec5595f41649eb91912bb8e10438f20c&name=/The%20Decemberists%20-%20A%20Bower%20Scene.mp3"
Apr 30 15:25 : interface 0: process command "stats"
Apr 30 15:25 : interface 0: command returned 0
Apr 30 15:25 : interface 0: process command "status"
Apr 30 15:25 : interface 0: command returned 0
Apr 30 15:25 : interface 0: process command "playlistinfo"
Apr 30 15:25 : interface 0: command returned 0
Apr 30 15:25 : interface 0: closed
Apr 30 15:25 : copyMpdTagToOB: copiedTag
Apr 30 15:25 : alsa device "default" will be playing 16 bit, 2 channel audio at 44100 Hz
Apr 30 15:25 : player: metadata change
Apr 30 15:25 : player: new metadata from decoder!
Apr 30 15:25 : playerCurrentDecodeSong: caught new metadata!
```

---

### Post by tshearman on 2009-12-23
bump... experiencing the exact same problem.  Dasbooster did you find a fix?

---

