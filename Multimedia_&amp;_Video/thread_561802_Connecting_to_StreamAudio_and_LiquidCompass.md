---
title: "Connecting to StreamAudio and LiquidCompass?"
date: 2007-09-28
forum: Multimedia &amp; Video
---

### Post by CyyberSpaceCowboy on 2007-09-28
I have a fresh Ubuntu 7 install and I've been trying to get streaming audio from talk radio stations to play in FireFox.  I've installed the GStreamer codecs, restricted applications, Mplayer, Streamtuner, Totem, Aramok, and VLC.

Both LiquidCompass and StreamAudio pop up Java windows so I can't find an actual audio link to plug into a player.  Is there any kind of sniffer that I can use to reveal the link the Java windows are trying to load?  I found a link in a forum for a StreamAudio link to a different station that worked, but switch the call letters to the station I want to listen to didn't.  Is there any way to re-direct pop-up audio links to a particular player?

Liquid Compass' tech page says all I need in Linux is MPlayer and the Mozilla MPlayer plugin.   Launching NPR (which works) opens a FireFox window that says the MPlayer plugin is running.  I downloaded the latest plugin RAM from Source Forge, but Archive Manager doesn't know what to do with it.  I found the command to download and install the plugin in another post, so I can try it in the terminal window. 

I had StreamAudio working before, but after an unrelated tweak (I'm also trying to get my WiFi card to connect to a WPA encrypted link), Ubuntu loaded with the "cannot find settings" message an hung on shutdown, so I decided to start over with a clean install now that I've learned I need to run Add/Remove and other administrative tasks under GKSUDO.

---

### Post by CyyberSpaceCowboy on 2007-10-14
I found a work around.  StreamAudio and LiquidCompass are front ends for MMS (Microsoft Media Stream?) links.  A lot of direct links have been posted, so if you do a search (Google strips out punctuation, so use something else) on MMS:// and the radio station call letters, you have a good chance of finding a link you can plug into the stream field of VLC (so far, I haven't found any other multimedia apps that work).

---

### Post by zeeHesh on 2007-11-22
I had experienced the same problem with LiquidCompass trying to stream in my favorite talk radio.  What worked for me was a reinstall of Mozilla and the mplayer plug-in, then setting 'percent of media to cache' to zero.

---

