---
title: "Only certain codec and/or players play video"
date: 2009-02-17
forum: Multimedia Software
---

### Post by falkaholic on 2009-02-17
I've got a weird one on my hands. My current ubuntu 8.10 install doesn't seem to play most video.

I try: VLC, Kaffeine, MPlayer, Totem Movie Player.


VLC: Usually gives the error: "No suitable decoder module:
VLC does not support the audio or video format "[codec]". Unfortunately there is no way for you to fix this."

Kaffeine: Just searches for a codec that it never finds.

Totem: Looks for codec and give this error in the console.
(totem:7182): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstffmpeg.so': /usr/lib/i686/cmov/libavcodec.so.51: undefined symbol: ff_gcd

All: Play sound and the few mpgs i can find.

Nautilus: only seem to show thumbnail previews for xvid.

MPlayer: Plays everything fine.




What I have tried:
-Taking off all non-standard repositories and uninstalling and reinstalling everything video package I can find.

-Turning off Compiz

-Tried different version of nvidia driver.

-Made a new test user, same thing, not a config problem

-Searched the interwebs up and down.

-Went back to previous kernal version. 


What makes MPlayer work so well? Why does even the opens-everything VLC not working?

How do I reinstall everything video-related?

thanks for any help....

---

### Post by futureal2032 on 2009-02-17
I don't know much technically...
but i only have Totem Movie Player installed on my Ubuntu 8.10

and so far it plays following formats without any problems at all...
sure it asked me to install some plugins first time..
currently my Totem Player plays following formats:
mp3, mp4, mpeg, avi, avi(XVid), avi(DivX), DivX, rmvb, rm, mov,
DAT, wav, VOB, flv, ogg, mkv.

haven't checked other formats yet.
thing i like abt Totem is its simple, no frills, and fast.

I guess the MPlayer package/packages come with most codecs included when you install it.

---

### Post by cariboo on 2009-02-17
Install the unbuntu-restricted-extras meta package, it will install all the codecs you need to play most audio/video media. If you want to play dvds you will need to enable the Medibuntu reposiotires. Go [here]("http://help.ubuntu.com/community/Medibuntu") to enable them, there are also hints and tips for adding other codecs on the page.

Jim

---

### Post by falkaholic on 2009-02-17
thanks for the pointers

I forgot to mention video WAS working. Somewhere in my tinkering I managed to break it. 


As for the restricted drivers, I've uninstalled and reinstalled them, and all packages associated with ffmpeg, h264, gstreamer, etc. No change.

There has to be one damaged library or something somewhere.....

---

### Post by falkaholic on 2009-02-23
figured it out. 

Was using a strange version of libavutil49. Used synaptic to force it to intrepid version and everything is fine now.

---

