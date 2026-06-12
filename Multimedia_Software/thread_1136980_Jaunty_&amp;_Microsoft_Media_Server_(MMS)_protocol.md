---
title: "Jaunty &amp; Microsoft Media Server (MMS) protocol"
date: 2009-04-25
forum: Multimedia Software
---

### Post by karanga on 2009-04-25
I'm sorry if this has been discussed in another thread but I've tried a search for 'Jaunty Microsoft Media Server (MMS) protocol jaunty' which returned no results.

I'm trying to open a BBC radio (Five Live) audio feed

[http://www.bbc.co.uk/iplayer/console/5live](http://www.bbc.co.uk/iplayer/console/5live)

which opens the BBC Iplayer console window before a search for suitable plugin dialogue box appears. Nothing is found and the error message is displayed:

An Error occurred

The playback of this movie requires a Microsoft Media Server (MMS) protocol source plugin which is not installed.

Is it possible to run IPlayer streams in Jaunty yet or are things still being worked out?

I'm running Ubuntu Jaunty (fully updated) and Firefox 3.0.9

Any help or advice greatly appreciated.

---

### Post by genii90 on 2009-04-28
Go* Application > Add Remove. *Select '*Sound and video*'. In the application Window select '*Gstream pugin for mms, wavpack ..*..'. Then *Apply Changes*

---

### Post by Markus_Glasgow on 2009-04-28
It works for me in Jaunty with the Mplayer plugin. 

However, I had the same error message from Rhythmbox. There I installed the packages gstreamer0.10-plugins-ugly, gstreamer0.10-plugins-bad and gstreamer0.10-plugins-ffmpeg and it finally worked.

Hope that helps.

---

### Post by iMerlin on 2009-04-29
Totem refused to play MMS, the codec finder says no plugins are found. I've tried installing good, bad and the ugly codec packs to gstreamer and after ugly-multiverse my Totem just stops responding.

Mplayer works fine though but if Totem can't play mms, it's kind of useless as a mozilla plugin.

---

### Post by yunone on 2009-09-04
> **Markus_Glasgow said:**
> It works for me in Jaunty with the Mplayer plugin. 

However, I had the same error message from Rhythmbox. There I installed the packages gstreamer0.10-plugins-ugly, gstreamer0.10-plugins-bad and gstreamer0.10-plugins-ffmpeg and it finally worked.

Hope that helps.


worked perfectly! thank you

---

### Post by oferdavidi on 2010-08-07
Non of the above recommendation has worked for me.
I have managed to run MSS after I installed the "ubuntu-restricted-extras" package using synaptic 
Hope it will help you too ;)

---

### Post by phonemic_chip on 2010-08-26
> **genii90 said:**
> Go* Application > Add Remove. *Select '*Sound and video*'. In the application Window select '*Gstream pugin for mms, wavpack ..*..'. Then *Apply Changes*

thank you. oh i am a real newbie...

---

