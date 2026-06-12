---
title: "Unable to listen to online radio"
date: 2010-08-21
forum: Multimedia Software
---

### Post by badger_fruit on 2010-08-21
Guys
I often listen to online radio when pottering around the house or what not but since I migrated over from Windows to Linux (Ubuntu 10.4 in this case) I can't seem to play the stream.  The particular station I want to listed to has a help page --> [http://www.galaxyyorkshire.co.uk/listen-live-having-problems-3281](http://www.galaxyyorkshire.co.uk/listen-live-having-problems-3281) which unfortunately does not help.

There is a link to the stream here --> [http://mediaweb.musicradio.com/player/default.asp?s=77&e=0](http://mediaweb.musicradio.com/player/default.asp?s=77&e=0)
I tried using Mplayer, VLC, Kaffeine, Movie Player and Firefox but nothing plays it :(

I'm sorry, I don't know where to get any logs from to find out why it's not working but would really appreciate some help with this please!

Cheers

---

### Post by ron999 on 2010-08-21
Hi
This is the link to play the stream:-
> mms://mediasrv-sov.musicradio.com/GalaxyYorkshire?MSWMExt=.asf


It's a WMA stream, takes quite a while to buffer.

You can test it with vlc and mplayer using these commands:-

```
vlc mms://mediasrv-sov.musicradio.com/GalaxyYorkshire?MSWMExt=.asf
```

```
mplayer mms://mediasrv-sov.musicradio.com/GalaxyYorkshire?MSWMExt=.asf
```

---

### Post by drs305 on 2010-08-21
badger_fruit,

It played on my system.

Not knowing what you have installed on your system, I booted a Lucid LiveCD to start from the basic setup. 

The link wouldn't play.

I installed ubuntu-restricted-extras but the link still wouldn't play, and the link asked to search and install an MMSH plugin.

The Ubuntu Software Center didn't reveal an MMSH option, but Gstreamer has the MMS plugin, which I installed. (Gstreamer plugins for MMS).

I restarted FireFox and tried the link again It again asked to search and install a suitable plugin, and this time it successfully found and installed the gstreamer plugin and the link then played.

---

### Post by cmcanulty on 2010-08-21
Try rt clicking the volume icon in panel and make sure you try all the settings. Mine had it set to external amplifier and when I unchecked that I got sound.

---

### Post by badger_fruit on 2010-08-21
> **ron999 said:**
> Hi
```
vlc mms://mediasrv-sov.musicradio.com/GalaxyYorkshire?MSWMExt=.asf
```


Hi guys
I've been out all day and just in now; tested using the above from terminal and it's playing .. to [[COLOR=#D40000]**drs305**[/COLOR]]("http://ubuntuforums.org/member.php?u=223945") i apologise for missing this from the original post but it's a clean, default install.  

I also tried using the terminal to launch the URL HTTP: version and got this output:-

```

badger_fruit@bgrlaptop:~$ VLC media player 1.0.6 Goldeneye
[0x8d11668] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[0x909ff10] ts demux error: cannot peek
^C
[1]+  Done                    vlc http://mediaweb.musicradio.com/player/default.asp?s=77

```

I have another PC which is unable to play (this is OpenSuse 11.3) so I'm gonna try this terminal method/link and will post back when I have some results.  As it is now, I have it working which is good enough for me (although it would be great if I can get it so I just click the link on the website and it plays in the browser!)

Cheers though and watch this space for results of the terminal > vlc ...

---

### Post by ron999 on 2010-08-21
Hi
It's easy to make a shortcut for your desktop.
Paste this text below into a file and save it on the desktop as **galaxy.m3u**
Then you can right-click open with ...vlc
> #EXTM3U
mms://mediasrv-sov.musicradio.com/GalaxyYorkshire?MSWMExt=.asf
#
#
# Shortcut for GalaxyYorkshire.

---

### Post by KegHead on 2010-08-21
Hi!

I've switched to stream tuner 2 with great results.

KegHead

---

### Post by mc4man on 2010-08-21
> although it would be great if I can get it so I just click the link on the website and it plays in the browser!

In-browser playback using the http url would seem to be limited to users from the UK, whether that's a 'cold, dark place' not sure - U.S. here.
The mms links bypass that restriction

Edit:
the "(Gstreamer plugins for MMS", should be provided from the bad plugin, depending on which wma codec is used that should suffice.
( to add wmap, wmas and some others codecs to lucid and probably karmic's gstreamer use link in sig - a highly 'trusted' ppa imo

---

### Post by shantiq on 2010-08-21
> **ron999 said:**
> Hi
It's easy to make a shortcut for your desktop.
Paste this text below into a file and save it on the desktop as **galaxy.m3u**
Then you can right-click open with ...vlc


cool info ron

got me looking around and found  [http://www.listenlive.eu/uk.html](http://www.listenlive.eu/uk.html)  which might be of interest to some  it has the whole of europe

[COLOR=#000000][FONT=Times New Roman][LEFT][**Yorkshire Radio**]("http://www.yorkshireradio.net/")Leeds[IMG]http://ubuntuforums.org/mp3.gif[/IMG][48 Kbps]("http://streaming.planetwideradio.com:8080/listen.pls")
Adult Contemporary/Sport[**Yorkshire Coast Radio**]("http://www.yorkshirecoastradio.com/")Scarborough[IMG]http://ubuntuforums.org/mp3.gif[/IMG][128 Kbps]("http://str1.sad.ukrd.com/yorkshirecoast.m3u")
Current/Classic Hits[**Yorkshire Coast Radio**]("http://www.yorkshirecoastradio.com/")Bridlington[IMG]http://ubuntuforums.org/mp3.gif[/IMG][128 Kbps]("http://str1.sad.ukrd.com/yorkshirecoastb.m3u")
Current/Classic Hits[**Your Radio**]("http://www.yourradiofm.com/")Dumbarton[IMG]http://ubuntuforums.org/wma.gif[/IMG][64 Kbps]("http://on-demand.phasebroadcast.net/yourradio")
Current/classic hits[**Youthcomm Radio**]("http://www.youthcomm.org.uk/")Worcester[IMG]http://ubuntuforums.org/wma.gif[/IMG][96 Kbps]("http://www.youthcomm.org.uk/broadcasting/radio/YouthcommRadio.asx")

[/LEFT]
[/FONT][/COLOR]


again like you indicated save a link to desktop by right clicking on where it says 96kbps or whatever and saving to desktop then find a nice icon mayhaps

---

### Post by andrew.46 on 2010-08-22
Perhaps because I complicate things too much but I usually embellish the commandline a little:

```

mplayer -cache 2048 -cache-min 80 \
'mms://mediasrv-sov.musicradio.com/GalaxyYorkshire?MSWMExt=.asf'

``` 

Often manipulating the cache size as well as the initial cache fill percentage makes a big difference with more precarious streams, and certainly from my part of the world this stream is none too solid :).

Andrew

---

