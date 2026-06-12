---
title: "Jack steals all sound"
date: 2007-01-11
forum: Multimedia &amp; Video
---

### Post by Hanj on 2007-01-11
I asked this a couple of weeks ago and got the advice to try again after the holidays, so here goes again :)

I have a machine running Edgy that's being used as a digital audio workstation. Things were working fine until I replaced the old sound card with an M-Audio Audiophile 2496. I had some trouble so I eventually ended up reinstalling the entire OS, and now the problem is this:

When I log in, everything works fine soundwise. I can get sound from multiple applications at the same time with no problems at all. But as soon as I start the jack server, it hogs up the sound card completely. I can connect any number of applications to jack (Ardour and Hydrogen for instance) and they all get sound. But if I try to run, say, xmms when jack is started I get a message saying the sound card is in use. If I stop jack it works again.

This is getting really annoying, so any help would be appreciated! I've been googling a lot, but I haven't been able to find anyone with the same problem, so maybe I just don't know what to look for.

---

### Post by Hanj on 2007-01-15
*Bump*

No one? Please?

---

### Post by Ashrael on 2007-01-17
if i'm remembering correctly, you can tell xmms to use jack too...and other sound appz usualy can uotput through jack too...

hope this helpss..

---

### Post by christhemonkey on 2007-01-17
Jack does hog the soundcard yes.
Thats what it is intended to do, and all audio apps attachthem selves to the server and output through that.

For some applications that use the gstreamer framework (which is the gnome standard) there is no jack ouput plug, so you will not be able to use them.
However, xmms does not use gstreamer, so you can install an output plug that uses jack (such as xmms-jack or xmms-jackasyn)
```
sudo apt-get install xmms-jack 
```
xmms-jack is an output plugin for XMMS that allows it to be treated as an audio source for jack, a low-latency audio server. 
```
sudo apt-get install xmms-jackasyn 
```
The advantage of using this plugin is that you do not have to change the output plugin if you want to work with or without jack. The plugin switches automatically between OSS and jack.

---

### Post by Hanj on 2007-01-17
Thanks for your replies!
That's weird, I was pretty sure I could run gstreamer apps alongside with jack before I changed my soundcard. I'll experiment with that jack plugin, so I can at least use xmms with jack running.

---

