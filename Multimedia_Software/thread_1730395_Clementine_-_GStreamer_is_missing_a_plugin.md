---
title: "Clementine - GStreamer is missing a plugin"
date: 2011-04-16
forum: Multimedia Software
---

### Post by Falc7 on 2011-04-16
Just installed Clementine audio player, but it won't play mp4s. It says gstreamer is missing a plugin, google search turned up some leads but they didn't lead anywhere. Mp4s work fine in Amarok, and i have already installed the restricted extras package.

---

### Post by Yellow Pasque on 2011-04-16
Install gstreamer0.10-plugins-bad-multiverse to play mp4 using libfaac.

---

### Post by KegHead on 2011-04-16
Hi Temujin,

I've been unable to play any downloaded video's on 11.04b2.

I must be missing something--but, don't know what.

Any ideas?

Thanks!

KegHead

---

### Post by Falc7 on 2011-04-16
Already installed that package, but its not working

---

### Post by Yellow Pasque on 2011-04-16
> **Falc7 said:**
> Already installed that package, but its not working
Can you start Clementine from the terminal?

> I've been unable to play any downloaded video's on 11.04b2.
Any ideas?
Only videos of a certain format? Did you try other players?

---

### Post by Falc7 on 2011-04-16
```
jamie@jamie-Inspiron-N5010:~$ clementine
Couldn't load icon "clementine-panel" 
Couldn't load icon "clementine-panel-grey" 
virtual bool GnomeGlobalShortcutBackend::DoRegister() - starting 
virtual bool GnomeGlobalShortcutBackend::DoRegister() - gnome settings daemon not registered 
virtual bool QxtGlobalShortcutBackend::DoRegister() 
Couldn't load icon "find" 
"gstdecodebin2.c(3076): gst_decode_bin_expose (): /GstPipeline:pipeline/GstURIDecodeBin:uridecodebin-0/GstDecodeBin2:decodebin20:
no suitable plugins found" 
"qtdemux.c(2980): gst_qtdemux_loop (): /GstPipeline:pipeline/GstURIDecodeBin:uridecodebin-0/GstDecodeBin2:decodebin20/GstQTDemux:qtdemux0:
streaming stopped, reason not-linked" 
Gstreamer error: "Your GStreamer installation is missing a plug-in." 
QTimeLine::start: already running
QTimeLine::start: already running

```

---

### Post by Yellow Pasque on 2011-04-16
Since clementine is trying to use qtdemux, I'm thinking that it's confusing your mp4 audio for a video. I'm not really sure, though.

---

### Post by Falc7 on 2011-04-17
oh some of these mp4s may well be a music video, could i make it just play the audio portion?

---

### Post by Falc7 on 2011-04-27
bump

---

### Post by KegHead on 2011-04-27
Hi!

I did a fresh 11.04 install.

No longer working w/clementine.

No video problems.

KegHead

---

### Post by Falc7 on 2011-04-28
It plays videos for you? Or just the audio track?

---

### Post by SeijiSensei on 2011-05-19
I encountered this problem playing an Ogg Vorbis radio stream.  The stream plays fine, but I get the "missing plugin" message.  Playing a WAV or FLAC file doesn't generate the message.  I haven't tried all the possible types of files, but I'm surprised an Ogg stream would generate an error.

I've installed pretty much all the gstreamer plugins (using "sudo apt-get install gstreamer0.10-plugins-*"), but I still get the error. Unfortunately it doesn't say *which plugin(s)* are missing!  Nor does it offer to install the missing items for you the same way applications like K3b do.

Kubuntu 11.04

---

### Post by Yellow Pasque on 2011-05-19
> **SeijiSensei said:**
> I encountered this problem playing an Ogg Vorbis radio stream.  The stream plays fine, but I get the "missing plugin" message.  Playing a WAV or FLAC file doesn't generate the message.  I haven't tried all the possible types of files, but I'm surprised an Ogg stream would generate an error.

I've installed pretty much all the gstreamer plugins (using "sudo apt-get install gstreamer0.10-plugins-*"), but I still get the error. Unfortunately it doesn't say *which plugin(s)* are missing!  Nor does it offer to install the missing items for you the same way applications like K3b do.

Kubuntu 11.04
Terminal output, plz.

---

### Post by SeijiSensei on 2011-05-20
I didn't have kubuntu-restricted-extras installed.  After installing that, I no longer get the missing plugin warning.  Still it's strange that it would pop up while playing an Ogg stream.

Obviously I can no longer reproduce the problem, but maybe this will help with diagnosis?

---

### Post by lunalui on 2012-12-21
Hi,
I have the same message when trying to play this radio stream 
player.radioexe.co.uk
using clementine.
I added all possible gstreamer plugins and also tryed adding the kubuntu-restricted-extras to no avail: the radio stream just wont play (it plays fine on firefox). Any ideas?

---

### Post by nickdc on 2013-01-21
Any answers out there?

I'm in identical situation as lunalui: Clementine gives missing gstreamer plugin message when I try to play a radio stream (BBC Radio 3). Plays fine from Firefox. I've installed everything I can find, as suggested in other posts, and followed the new version of the Comprehensive Multimedia & Video Howto, but still no joy. One clue is that when I tried Rhythmbox it too could not play it, giving the same "missing plugin" message, but it was more helpful than Clementine as it tried to find the plugin. However it ended with:

Required plugin could not be found
Python (v2.7) requires to install plugins to play media files of the following type: text/html decoder

With streaming and internet radio so popular (I'm a latecomer) I'm amazed problems like this still crop up ... Can anyone help?

---

### Post by Tallyon on 2013-01-24
Hey guys.

Got the same problem on Fedora 18. And with the command following I got it working:


yum install gstreamer-{ffmpeg,plugins-{bad,good,ugly}} xine-lib-extras{,-freeworld} libtunepimp-extras-freeworld

In Your case just replace yum with apt-get. All packages should be in Ubuntu repo.

Hope it helps.
Cheers!

---

### Post by lunalui on 2013-02-18
> **Tallyon said:**
> Hey guys.

Got the same problem on Fedora 18. And with the command following I got it working:


yum install gstreamer-{ffmpeg,plugins-{bad,good,ugly}} xine-lib-extras{,-freeworld} libtunepimp-extras-freeworld

In Your case just replace yum with apt-get. All packages should be in Ubuntu repo.

Hope it helps.
Cheers!

thanks for your suggestion, Tallyon. Unfortunately I get the following error messages 

E: Unable to locate package gstreamer-ffmpeg
E: Unable to locate package gstreamer-plugins-bad
E: Unable to locate package gstreamer-plugins-good
E: Unable to locate package gstreamer-plugins-ugly
E: Unable to locate package xine-lib-extras
E: Unable to locate package xine-lib-extras-freeworld
E: Unable to locate package libtunepimp-extras-freeworld

In fact, according to my synaptic package manager I have the first four already installed while I'm unable to find the last three which are specific to fedora???

---

### Post by lunalui on 2013-02-18
I've installed the Fedora packages using Alien (great discovery, BTW) but unfortunately they do not seem to fix the problem.
I've also tried opening the stream with gxine but I get the following message

The xine engine failed to start.
No demuxer found - stream format not recognized.

---

