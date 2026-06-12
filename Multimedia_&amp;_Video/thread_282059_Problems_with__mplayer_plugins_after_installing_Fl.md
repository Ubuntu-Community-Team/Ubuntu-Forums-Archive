---
title: "Problems with  mplayer plugins after installing Flash 9 beta ?"
date: 2006-10-22
forum: Multimedia &amp; Video
---

### Post by bewire on 2006-10-22
EDIT Oct 25 2006: I have tried to search the forum for help, but I can't find anything related to my problem with the mplayer plugin and streaming audio from NRK radio ...](*,) I will be greatfull for any help !

Hi, I downloaded and added the new flash 9 plugin yesterday. Later after testing sites with Flash content I tried to stream netradio from NRK Norway ([http://www.nrk.no/tjenester/nrk_nettradio/3220264.html?kanal=p3)](http://www.nrk.no/tjenester/nrk_nettradio/3220264.html?kanal=p3)), but the player don't load in Firefox (the controls don't show). If I try to reload and play by right clicking the controls show but the player goes to stop mode. 

See the attached screenshots for how this looks in Firefox ...

EDIT: Please also see the screenshot showing the configuration for mplayer. Should I change anything ?


The mplayer plugin for streaming video works but it's lagging, example [http://www1.nrk.no/nett-tv/klipp/197997](http://www1.nrk.no/nett-tv/klipp/197997) 

Playback of trailers from [http://www.apple.com/trailers/](http://www.apple.com/trailers/) seems to work fine ...

Does the flash plugin have any effect on the mplayer plugins or is the just coincidence that the mplayer stopped working ? 

When adding the new flash 9 beta plugin I removed the old one ...

I use Firefox ...

Here is a listing of my plugins:

/usr/lib/mozilla/plugins

libflash-mozplugin.so     mplayerplug-in-qt.so   mplayerplug-in-wmp.so
libflashplayer-backup.so  mplayerplug-in-qt.xpt  mplayerplug-in-wmp.xpt
libflashplayer.so         mplayerplug-in-rm.so   mplayerplug-in.xpt
mplayerplug-in-gmp.so     mplayerplug-in-rm.xpt
mplayerplug-in-gmp.xpt    mplayerplug-in.so

/usr/lib/firefox/plugins
libflash-mozplugin.so     mplayerplug-in-gmp.xpt  mplayerplug-in.so
libflashplayer-backup.so  mplayerplug-in-qt.so    mplayerplug-in-wmp.so
libflashplayer.so         mplayerplug-in-qt.xpt   mplayerplug-in-wmp.xpt
libunixprintplugin.so     mplayerplug-in-rm.so    mplayerplug-in.xpt
mplayerplug-in-gmp.so     mplayerplug-in-rm.xpt

---

### Post by bewire on 2006-10-22
Hi, I have now removed the following from plugins directories:

libflash-mozplugin.so
libflashplayer-backup.so

But still no sound for the netradio ...

---

### Post by bewire on 2006-10-23
Hi, please let me know if anyone else have problems with the NRK netradio ...

Or is possible solutions posted elsewhere in the forum ?

---

### Post by bewire on 2006-10-23
Hi, please let me know if anyone else have problems with the NRK netradio ...

Or is possible solutions posted elsewhere in the forum ?

---

### Post by bewire on 2006-10-23
Hi I just tested to stream netradio directly by the links at this site and it worked once but now its only buffering at 98-99% ...

[http://nrk.no/lyd/](http://nrk.no/lyd/)

I takes some time buffering at 99% but then the mplayer starts. So now I have to find out why the buffering process takes longer than normal and why NRKs netradio webapp don't starts the streaming at all.

And I will really appreciate any advice :-)

I've seen some postings about buffering stopping at 98% so maybe that applies to me system ?

Edit: After some more testing I realize that the Mplayer stops after some seconds ...

---

### Post by bewire on 2006-10-26
Hi. looks like playback works fine with this link:
[http://nettradio.nrk.no/php/includes/channelstreamingurl.php?pichannel=mp3&quality=h](http://nettradio.nrk.no/php/includes/channelstreamingurl.php?pichannel=mp3&quality=h)

I have been streaming the radio for 10 minutes now without interruption ...

So my challenge now is to find out why I can't stream through the net radio application:
[http://www.nrk.no/tjenester/nrk_nettradio/3220264.html?kanal=p3](http://www.nrk.no/tjenester/nrk_nettradio/3220264.html?kanal=p3)

---

### Post by bewire on 2006-10-27
Here is my ~/.mplayer/mplayerplug-in.conf:

autostart=1
ao=esd
noembed=0
cachesize=512
cache-percent=5
dload-dir=/home/bewire
showtime=1
enable-wmp=1
enable-qt=1
enable-rm=1
enable-gmp=1
enable-mpeg=1
enable-mp3=1
enable-ogg=1
enable-midi=0
enable-pls=1
enable-smil=1
enable-helix=1
nomediacache=0
nopauseonhide=0
rtsp-use-tcp=0
rtsp-use-http=0

Should I change or add anything ? Please post examples of working mplayerplug-in.conf files ...

I tried the testing page at [http://www.linspire.com/products_linspire_whatis.php?tab=compatibility](http://www.linspire.com/products_linspire_whatis.php?tab=compatibility) and I get the same problem when trying this MP3 Audio Stream:
[http://www.wfmu.org/wfmu_ogg.m3u](http://www.wfmu.org/wfmu_ogg.m3u)

The other sound tests seem to work fine except the one for .pls (it just go to stop mode)

---

### Post by bewire on 2006-11-15
Hi, the NRK Netradio player works again, lucky for me :-) I don't know why. and cant remember any significant changes in my system config lately. So, I guess I just have to accept that my problems are gone for now ;-) ...

---

