---
title: "How to connect Rhythmbox to Jack"
date: 2008-12-12
forum: Multimedia Software
---

### Post by prince.buster on 2008-12-12
Just writing because when I was trying to do the same thing it took AGES to find the relevant info via google. Hopefully I can make it a bit easier for the next person.

So connecting [Rhythmbox]("http://en.wikipedia.org/wiki/Rhythmbox") to Jack is actually pretty simple. There's more than one way to do it. And although I'm talking about Rhythmbox, this applies to any [gstreamer]("http://en.wikipedia.org/wiki/Gstreamer") app.

One way is to route all desktop audio through [pulseaudio]("http://en.wikipedia.org/wiki/Pulseaudio"), and then through to [Jack]("http://en.wikipedia.org/wiki/JACK_Audio_Connection_Kit"). See reply to this post for instructions. This may or may not be a better solution, I'm still undecided.

The way I went was to make each *gstreamer instance* output directly to Jack. Basically I followed [this dude's instructions]("http://ubuntuforums.org/showthread.php?t=554457&highlight=jack") to a tee, and it works!

The required bit of software is **jackaudiosink**, which is inside the **gstreamer0.10-plugins-bad** package. So install that, as well as any other jack programs or tools which I'll assume you know how to use. patchage and qjackctl are kinda good to have.
Then just a little bit of configuration.
In particular, telling gstreamer to actually *use* the jackaudiosink. You could use gconf-editor just as detailed in the above thread, or alternatively:
```
sudo aptitude install gstreamer-properties
gstreamer-properties &
```
and then under **default output** choose custom for the **Plugin** and type "jackaudiosink" for the **Pipeline**.

Should work! Be sure jackd is running before trying to play anything. If you get no sound, make sure rhythmbox (or whatever) is actually connected to your speakers.

Also be aware that rhythmbox's gstreamer instance seems to disappear whenever a song is not playing, and a fresh one created for each new song. This is frustrating, especially if you've set up something elaborate.
A way around is to set up the jack.plumbing daemon, which is in the jack-tools package. This allows you to specify rules on what connects to what at any time. But all that's in the thread above. I'm just trying to simplify and explain it a bit.

Also see the documentation for gstreamer's [jackaudiosink]("http://gstreamer.freedesktop.org/data/doc/gstreamer/head/gst-plugins-bad-plugins/html/gst-plugins-bad-plugins-jackaudiosink.html").

---

### Post by markbuntu on 2008-12-12
There is another way to do this so all pulseaudio using applications can play through jack. There are directions for that here, just scroll down the OP to the **Pulseaudio through jack** section. 

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

It only takes a few minutes to set up and then any application that plays though pulseaudio can be available through jack. This has been tested in Hardy and Intrepid on both 32 and 64 bit and on UbuntuStudio Hardy and Intrepid.

---

### Post by prince.buster on 2008-12-12
When connecting pulseaudio to jack, do we get a single jack source/sink for *all* the apps going through pulseaudio, or do we get one source/sink *per application*?

---

### Post by markbuntu on 2008-12-12
I am not sure if you can get multiple instances of these modules up and running if that is what you want to do. I never really thought about it that way.

Anyway,These modules create one jack source and one jack sink in the Pulse Audio Volume Control (pavucontrol)  that are in the Input Devices and Output Devices section . You can select the jack sink in the Playback section just like any other sink by right clicking on the stream and choosing move stream. It is the same for the jack-source for recording/capture applications that use pulseaudio

In jack, you will see the pulseaudio sink connected to system output and pulseaudio source connected to system input in jack control connections/audio. You can change these conenctions to whatever jack applications you have running.

At the end ot that section there is a link to some things you can try out that will help you get an understanding of how to use these sinks and sources with jack.

---

### Post by asuastrophysics on 2010-06-16
I tried this, it didn't work. No sound from rhythmbox, no sound from any MP3 player on linux.

---

