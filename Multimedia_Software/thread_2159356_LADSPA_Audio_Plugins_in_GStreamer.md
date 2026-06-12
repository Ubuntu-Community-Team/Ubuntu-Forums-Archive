---
title: "LADSPA Audio Plugins in GStreamer"
date: 2013-07-02
forum: Multimedia Software
---

### Post by Iggy64 on 2013-07-02
I've posted here previously about various parts of this issue, but still haven't been able to pull together a bottom line.  Nor have my continuing experiments provided any answers.  I thought I should give it one more shot here.

I have a Linux box set up just for playing my very diverse music collection.  Relatively new to Linux, I soon discovered that there were two classes of players for Linux:

Type A - Those that aim for high-quality output and provide for some discreet signal processing, like Audacious and Aqualung.

Type B - Those that are great for exploring new music, providing extensive library tools and downloading artist information, like Clementine and Guayadeque.  

So I find myself using Clementine to explore new genres and artists, then building some new collections.  Later, I use Audacious to play them back with a bit more control.  For example, some old (ancient) recordings seem to benefit from a bit of extra stereo separation, or even some very slight reverb.  It would be great to have something like MusicBee (Windows program) that does both, and perhaps foobar would be the answer -- I plan to check on that.

Another approach would be to find a way to get some control over GStreamer, the back end for players like Clementine.  I have tried for hours on end without success.  I wonder if anyone here can answer any of my questions:

1) Clementine, Guayadeque, etc., provide no access to GStreamer audio enhancement plugins. However, plugins written in GStreamer protocol can reportedly be inserted directly into the music-audiosink for GStreamer, as a partial pipeline.  This is done through dconf-editor.  For example,

Setting music-audiosink    equal to     delta gain=120 ! autoaudiosink

inserts the GStreamer delta noise sharpening plugin into the pipeline, with a gain of 120.  However many ways I have tried this, I hear no difference in the sound, and I see no extra processes running or files open.

2) I am especially interested in using Tom Szilagyi's TAP plugins (which work great in Audacious) in GStreamer.  But there are a couple of hitches here.  I read that these LADSPA-protocol plugins will only work in GStreamer by way of a wrapper plugin.  I have no idea how to implement that.  Also, I read that GStreamer has problems with multichannel LADSPA plugins because of the channel interleaving GStreamer does.  So perhaps it is folly to even be trying this.

Can anyone enlighten me on how to implement GStreamer-protocol plugins directly in GStreamer, whether through dconf-editor or otherwise?  And how can I test to see whether the plugin is actually being used?

Also, is there any chance of doing anything like that with a plugin written with the LADSPA protocol, whether with a wrapper or otherwise?

---

### Post by Iggy64 on 2013-07-04
I guess I'm not too surprised at getting no responses on this one.  I've researched this topic (using LADSPA plugins directly in GStreamer) for tens of hours, and have found very little.  There is this, though:

[http://lwn.net/Articles/411761/](http://lwn.net/Articles/411761/)
GStreamer: Past, present, and future

        Posted Oct 26, 2010 23:18 UTC (Tue) by **alankila** (subscriber, #47141)        [[Link]("http://lwn.net/Articles/411971/")]     
      [I]
I'm not too impressed with gstreamer. It has difficulties to play vorbis  here on ubuntu 10.10 due to some completely unknowable and unfathomable  reason. It may well be pulseaudio's fault, though.
[/I][I] More to the point, I saw that something simple like volume control on  the audio pipeline contains something like 30 kB of code because it  handles every possible format like 8, 16, 24, 32 bit integer audio and  32-bit and 64-bit audio. Additionally I think there was some dynamic  runtime code generation involved. So much of that 200k LOC might  actually go away if the design was simplified somewhat.
[/I]
[I] 
Also when trying to hook a simple LADSPA plugin of mine into pipeline  using gstreamer I encountered various random issues, such as the need to  use audioconvert (which ought to be injected automatically where  necessary, lest people have to pepper their pipelines full of that) and  queue (some kind of buffer, many things don't work without explicit  buffering for some reason).
[/I]
[I] 
Even worse, since gstreamer can't support stereo ladspa plugins in any  way, one is forced to implement these manually by deinterleaving (=  splitting) a stream into separate pipes, then putting them through the  plugin using the appropriate sprinking of audioconvert / queue, and then  assembling it back with interleave. Of course, the result is not usable  to pulseaudiosink because the channel assignment is lost along the way  with no way to define it on command line...
[/I]
* In short, I think this media framework is not quite the success story it is portrayed to be, IME.*

So there are at least a couple of major problems with this approach.  Perhaps THIS is why I only find useful effects plugins in players like Audacious and Aqualung, which don't use GStreamer. 

I guess this noob will now start learning about JACK and PulseAudio, to see where they fit into the scheme of things, and what they have to offer (good and bad).

---

