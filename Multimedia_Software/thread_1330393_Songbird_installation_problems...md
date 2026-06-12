---
title: "Songbird installation problems.."
date: 2009-11-18
forum: Multimedia Software
---

### Post by daviiiiiid on 2009-11-18
Hi. I have been trying to install Songbird on my Ubuntu 9.10 Karmic but without success.

I tried with [www.getsongbird.com](www.getsongbird.com) with the file there being the official website. I extracted it but when I do ./configure it says

 bash: ./configure: No such file or directory

I tried the methods on this too [https://help.ubuntu.com/community/Songbird](https://help.ubuntu.com/community/Songbird)

So finally I tried the [http://www.getdeb.net/app/Songbird](http://www.getdeb.net/app/Songbird) as it sounded like the most painless way of doing it after finding .. after doing everything.

Then it tells me Song bird is already installed. But I cant find how to "uninstall" it or remove it. Its not in my apps list, not in synaptic or in ubuntu software center.. 

(If you did not notice, im new to linux :))

Thank you.

---

### Post by scout4536 on 2009-11-18
First in your terminal do: sudo apt-get autoremove songbird
hopefully that removes it completely so you can reinstall it using the following link:

[http://linux.softpedia.com/progDownload/SongBird-Download-18926.html](http://linux.softpedia.com/progDownload/SongBird-Download-18926.html)

Ubuntu 9.04 DEB i386 (1.2.0 Stable)

Download the .deb and install it that way, works great for me, Songbird is awesome.  Runs perfectly on Karmic as well.

---

### Post by daviiiiiid on 2009-11-18
So you mean I should get the 9.04 version? 

Because I already tried the 9.10 deb and it didnt work out :(. I'll try and let you know in 5 mins .

edit:
I installed it... I had a message telling me theres a newer version. I ignored it and went on with install. It went well. But its not in the applications list.

I typed in songbird in terminal and this what I got:

> daviiiiiid@ubuntu:~$ songbird

(songbird-bin:8142): GStreamer-WARNING **: invalid name template bwf_audio_sink_%u: conversion specification must be of type '%d' or '%s' for GST_PAD_REQUEST padtemplate

(songbird-bin:8142): GStreamer-WARNING **: invalid name template alaw_audio_sink_%u: conversion specification must be of type '%d' or '%s' for GST_PAD_REQUEST padtemplate

(songbird-bin:8142): GStreamer-WARNING **: invalid name template dv_dif_video_sink_%u: conversion specification must be of type '%d' or '%s' for GST_PAD_REQUEST padtemplate

(songbird-bin:8142): GStreamer-WARNING **: invalid name template jpeg2000_video_sink_%u: conversion specification must be of type '%d' or '%s' for GST_PAD_REQUEST padtemplate

(songbird-bin:8142): GStreamer-WARNING **: invalid name template mpeg_audio_sink_%u: conversion specification must be of type '%d' or '%s' for GST_PAD_REQUEST padtemplate

(songbird-bin:8142): GStreamer-WARNING **: invalid name template mpeg_video_sink_%u: conversion specification must be of type '%d' or '%s' for GST_PAD_REQUEST padtemplate

(songbird-bin:8142): GStreamer-WARNING **: invalid name template up_video_sink_%u: conversion specification must be of type '%d' or '%s' for GST_PAD_REQUEST padtemplate

(songbird-bin:8142): GStreamer-WARNING **: invalid name template vc3_video_sink_%u: conversion specification must be of type '%d' or '%s' for GST_PAD_REQUEST padtemplate

(songbird-bin:8142): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstmpegdemux.so': /usr/lib/gstreamer-0.10/libgstmpegdemux.so: undefined symbol: _gst_debug_dump_mem

(songbird-bin:8142): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstrawparse.so': /usr/lib/gstreamer-0.10/libgstrawparse.so: undefined symbol: gst_video_format_new_caps_interlaced

(songbird-bin:8142): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstlibvisual.so': /usr/lib/gstreamer-0.10/libgstlibvisual.so: undefined symbol: gst_adapter_prev_timestamp
././songbird-bin: symbol lookup error: /usr/lib/python2.6/dist-packages/gst-0.10/gst/_gst.so: undefined symbol: gst_task_pool_get_type
Could not initialize GStreamer: Error re-scanning registry , child terminated by signal


---

### Post by scout4536 on 2009-11-18
Now it seems you need the codecs:

In terminal type or paste this:

sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-fluendo-mp3 gstreamer0.10-gnonlin gstreamer0.10-pitfdll gstreamer0.10-sdl gstreamer0.10-plugins-bad-multiverse gstreamer0.10-schroedinger gstreamer0.10-plugins-ugly-multiverse totem-gstreamer

---

### Post by daviiiiiid on 2009-11-18
> **scout4536 said:**
> Before installing the new .deb package in your terminal do this:

sudo apt-get autoremove songbird and see if it uninstalls anything else.  You may have some files left over from your previous install.

Its not done installing but I cant wait before thanking you!

It does not give me any error saying its already installed!!

And its installing right now!

That autoremove was exactly the command I was looking for! 

Thanks a lot scout4536!!

---

### Post by scout4536 on 2009-11-18
So you got it working good now??

---

### Post by daviiiiiid on 2009-11-18
Yep works!! thanks a lot ! 

But hmm I downloaded this because not only is it a great music player, but it supports shoutcast. 

However, Is it possible to SAVE shoutcast stations? I can get it playing but I cant add it to favorite or anything.

On the songbird browser i went to shoutcast.com and tried .977 music the hitz and it plays but I cant find how to save it.

---

### Post by scout4536 on 2009-11-18
I have used Shoutcast, but never save the channels, I just click on one and listen to whatever is playing.  No idea how to save the channels.  But I am glad you got it working.  :popcorn:

---

### Post by daviiiiiid on 2009-11-18
Thank you again.!

---

### Post by markov035 on 2010-04-05
To record shoutcast you can use streamtuner + modified shoutcast.so lib (or in /etc/hosts make an alias for [www.shoutcast.com](www.shoutcast.com) to  classic.shoutcast.com)

Together with streamtuner lots of stations get ripped.

Rip off *some* of the artists, not all.

We need free maps, as they are made with tax money.
[http://openstreetmap.org](http://openstreetmap.org)

Marc

---

### Post by markov035 on 2010-04-05
> **scout4536 said:**
> Now it seems you need the codecs:

In terminal type or paste this:

sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-fluendo-mp3 gstreamer0.10-gnonlin gstreamer0.10-pitfdll gstreamer0.10-sdl gstreamer0.10-plugins-bad-multiverse gstreamer0.10-schroedinger gstreamer0.10-plugins-ugly-multiverse totem-gstreamer

Get this

sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-fluendo-mp3 gstreamer0.10-gnonlin gstreamer0.10-pitfdll gstreamer0.10-sdl gstreamer0.10-plugins-bad-multiverse gstreamer0.10-schroedinger gstreamer0.10-plugins-ugly-multiverse totem-gstreamer
Pakketlijsten worden ingelezen... Klaar
Boom van vereisten wordt opgebouwd
De status informatie wordt gelezen... Klaar
gstreamer0.10-ffmpeg is reeds de nieuwste versie.
gstreamer0.10-ffmpeg is ingesteld voor handmatige installatie.
Pakket gstreamer0.10-schroedinger is een virtueel pakket voorzien door:
  gstreamer0.10-plugins-bad 0.10.14-4ubuntu1.1
U dient er één expliciet te selecteren voor installatie.
E: Pakket gstreamer0.10-schroedinger heeft geen installeerbare kandidaat


E: pkg  gstreamer0.10-schroedinger  does not have installable candidate.

What depots?? Medibuntu?? 

Marc

---

### Post by Bob63 on 2010-04-10
markov035,

[LEFT]Edit the list and remove the reference to gstreamer0.10-schroedinger, so it looks like:
[/LEFT]
 
sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-fluendo-mp3 gstreamer0.10-gnonlin gstreamer0.10-pitfdll gstreamer0.10-sdl gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly-multiverse totem-gstreamer

This made it work for me.

---

