---
title: "A light internet radio player?"
date: 2008-08-29
forum: Multimedia Software
---

### Post by Cam_B on 2008-08-29
I am looking for a light internet radio player, to play .pls files (you know, streams). I currently use banshee, but I find it far too resource heavy, particularly when I am working and have a lot of apps running. Don't mention XMMS, I dislike the way it sounds (just listen to a song on banshee, and then on XMMS without EQ on both). If I could just connect and play a stream in the terminal it would be awesome.

It would be even better if it worked in both gnome and enlightenment E17 and E16.

Thank you in advance.

---

### Post by Crafty Kisses on 2008-08-29
You might want to look into StreamTuner.

---

### Post by Cam_B on 2008-08-29
StreamTuner just browses streams from various sources, it needs a player (like XMMS) to play the streams...

---

### Post by Crafty Kisses on 2008-08-29
> **Cam_B said:**
> StreamTuner just browses streams from various sources, it needs a player (like XMMS) to play the streams...

I like VLC.

---

### Post by kostkon on 2008-08-29
I just use Totem for PLS streams.

---

### Post by wolfen69 on 2008-08-29
you could also go to pandora.com and make your own "radio station". no player needed. awesome web app.

---

### Post by fenian on 2008-08-29
You can use mplayer from the terminal to connct to streams,for emple to listen to bbc radio 4 you would enter...

> mplayer rtsp://rmlive.bbc.co.uk/bbc-rbs/rmlive/ev7/live24/radio4/live/r4_dsat_g2.ra

There is also a radio screenlet (uses mplayer) that works well though you have to edit some files to get the stations you want.

---

### Post by Crafty Kisses on 2008-08-29
Yeah I knew there was something like that, just didn't know what. :)

---

### Post by Cam_B on 2008-08-30
ok cool, I will try out the various things mentioned above

---

### Post by kru24d3r on 2012-01-16
You should try radio tray

---

### Post by SUPERFITTER on 2012-02-19
> **wolfen69 said:**
> you could also go to pandora.com and make your own "radio station". no player needed. awesome web app.
 
I had Pandora running, but after the last update for 11.10 I get this message.:(
 
I cannot get any online radio stations to play, I can run these stations on WinXP. Something got deleted or corrupted in Ubuntu. Any suggestions?

---

### Post by Rodney9 on 2012-02-19
+1 for Radio Tray

Rodney

---

### Post by SUPERFITTER on 2012-02-21
> **SUPERFITTER said:**
> I had Pandora running, but after the last update for 11.10 I get this message.:(
 
I cannot get any online radio stations to play, I can run these stations on WinXP. Something got deleted or corrupted in Ubuntu. Any suggestions?
 
I found more online stations and they will not run either. Any suggestions?

---

### Post by andrew.46 on 2012-02-21
I guess that vlc is not an especially light application but there is an amazing [lua extension]("http://www.coderholic.com/extending-vlc-with-lua/") that turns vlc into a pretty capable radio player. You will have to add your radio stations manually but the lua syntax is pretty straightforward. I attach a screenshot of the player working with vlc 2.0.0 + goom.

---

### Post by shantiq on 2012-02-22
> **kru24d3r said:**
> You should try radio tray


the lightest there is and so easy to use:KS



**also**   as regards  >  If I could just connect and play a stream in the terminal it would be awesome.

 


the quickest route is here     ```
cvlc +url of station playlist
```




example  

```
cvlc http://www.bbc.co.uk/radio/listen/live/r3_aaclca.pls
```

---

### Post by shantiq on 2012-02-22
and even better   use **nvlc**

for example open terminal    save this list below as classical.m3u [of course put YOUR stations of choice]  in home folder 


then enter ```
nvlc classical.m3u
```


really supple and stable  up and down arrows to navigate    

&#9658;&#9658;&#9658;&#9658; [CENTER][ATTACH]213083[/ATTACH] or black and white click C [ATTACH]213084[/ATTACH][/CENTER]


list here to try out

> [http://www.bbc.co.uk/radio/listen/live/r3_aaclca.pls](http://www.bbc.co.uk/radio/listen/live/r3_aaclca.pls)
[http://lyd.nrk.no/nrk_radio_klassisk_aac_h.m3u](http://lyd.nrk.no/nrk_radio_klassisk_aac_h.m3u)
[http://91.121.92.167:8900](http://91.121.92.167:8900)
[http://streaming.rtbf.be:8000/mus3128xrtbf.m3u](http://streaming.rtbf.be:8000/mus3128xrtbf.m3u)
[http://web.mmm.elion.ee/klassikaraadio.asx](http://web.mmm.elion.ee/klassikaraadio.asx)
[http://srvhost24.serverhosting.apa.net:8000/rsdstream128.m3u](http://srvhost24.serverhosting.apa.net:8000/rsdstream128.m3u)
[http://sverigesradio.se/topsy/direkt/1603-hi-mp3.pls](http://sverigesradio.se/topsy/direkt/1603-hi-mp3.pls)
[http://sverigesradio.se/topsy/direkt/2562-hi-mp3.pls](http://sverigesradio.se/topsy/direkt/2562-hi-mp3.pls)
[http://www.radiosuisseclassique.ch/live/mp3.m3u](http://www.radiosuisseclassique.ch/live/mp3.m3u)
[http://radioclasica.rtve.stream.flumotion.com/rtve/radioclasica.mp3.m3u](http://radioclasica.rtve.stream.flumotion.com/rtve/radioclasica.mp3.m3u)
[http://www.dr.dk/netradio/Metafiler/ASX/DR_P2_128.asx](http://www.dr.dk/netradio/Metafiler/ASX/DR_P2_128.asx)
[http://http-live.sr.se/p2musik-aac-192](http://http-live.sr.se/p2musik-aac-192)
[http://bbc.co.uk/radio/listen/live/r3.asx](http://bbc.co.uk/radio/listen/live/r3.asx)
[http://music.myradio.com.ua:8000/Classica128.ogg](http://music.myradio.com.ua:8000/Classica128.ogg)
mms://mms.rondofm.fi/RondoHF
[http://www.tv-radio.com/station/france_musique_mp3/france_musique_mp3-128k.m3u](http://www.tv-radio.com/station/france_musique_mp3/france_musique_mp3-128k.m3u)
[http://listen.radionomy.com/radio-mozart](http://listen.radionomy.com/radio-mozart)
[http://myradio.com.ua/alias/Classica128.m3u](http://myradio.com.ua/alias/Classica128.m3u)
[http://srvhost24.serverhosting.apa.net:8000/rsdstream128.m3u](http://srvhost24.serverhosting.apa.net:8000/rsdstream128.m3u)
[http://www.rozhlas.cz/audio/download/ddur_maxogg.m3u](http://www.rozhlas.cz/audio/download/ddur_maxogg.m3u)
[http://mediau.yle.fi/liveklassinen](http://mediau.yle.fi/liveklassinen)
[http://www.play.cz/radio/classic128.asx](http://www.play.cz/radio/classic128.asx)
[http://broadcast.infomaniak.ch//radioclassique-high.mp3.m3u](http://broadcast.infomaniak.ch//radioclassique-high.mp3.m3u)
[http://avw.mdr.de/livestreams/mdr_figaro_live_128.m3u](http://avw.mdr.de/livestreams/mdr_figaro_live_128.m3u)
[http://avw.mdr.de/livestreams/mdr_klassik_live_128.m3u](http://avw.mdr.de/livestreams/mdr_klassik_live_128.m3u)
[http://ndrstream.ic.llnwd.net/stream/ndrstream_ndrkultur_hi_mp3.m3u](http://ndrstream.ic.llnwd.net/stream/ndrstream_ndrkultur_hi_mp3.m3u)
[http://www.listenlive.eu/mr3.m3u](http://www.listenlive.eu/mr3.m3u)
[http://82.135.234.195/Klasika.asx](http://82.135.234.195/Klasika.asx)
[http://shoutcast.omroep.nl:8074/listen.pls](http://shoutcast.omroep.nl:8074/listen.pls)
[http://live.slovakradio.sk:8000/Klasika_256.mp3.m3u](http://live.slovakradio.sk:8000/Klasika_256.mp3.m3u)
[http://live.slovakradio.sk:8000/Devin_256.mp3.m3u](http://live.slovakradio.sk:8000/Devin_256.mp3.m3u)
[http://sverigesradio.se/topsy/direkt/2562-hi-mp3.pls](http://sverigesradio.se/topsy/direkt/2562-hi-mp3.pls)
[http://media-ice.musicradio.com/ClassicFMMP3.m3u](http://media-ice.musicradio.com/ClassicFMMP3.m3u)
mms://live.rfn.ru/rcult



many stations [**here**]("http://www.listenlive.eu/")

---

