---
title: "MP3 Codec"
date: 2011-04-17
forum: Multimedia Software
---

### Post by Mazate on 2011-04-17
Howdy all... I'm brand new to Ubuntu.  I'm learning all the ins and outs and one aspect of linux is legal vs illegal on codecs and things of that nature is somewhat troubling... Which brings me to my question:

While I was doing the initial installation of Ubuntu, I was given the option to install a fully licensed and free Fluendo codec for MP3, which I did.  One thing I've noticed since is that Rhythmbox also plays wma files as well and not just MP3.  Is the ability to play wma files included in the MP3 codec or should I not be able to play the wma's (legally) with that codec?

 Any clarification on this issue would be most appreciated.

---

### Post by K_45 on 2011-04-17
Fluendo is licensed for mp3's. You probably installed other G-streamer codecs for .wma. Personally, I'd re-rip all the music into .ogg for something open or .flac. .wma is a useless proprietary codec I wouldn't use. To check if you installed anything G-streamer, open a terminal from the Accessories terminal and enter

```
apt-cache search gstreamer | grep "gstreamer0.10-plugins" | head -15
```

If you see g-streamer bad or ugly you have additional codecs installed.

---

### Post by Mazate on 2011-04-17
Yes, I have codecs from the bad and the ugly set.  So... 

How do I remove them without reinstalling the OS?

---

### Post by wolfen69 on 2011-04-18
Just search synaptic package manager for **gstreamer**. Then right click them and **completely remove**. But leaving them in won't hurt anything. But that's your choice.

---

### Post by Mazate on 2011-04-18
Forgive my ignorance but where would I search for it?

---

### Post by Mazate on 2011-04-18
Nevermind... got it figured out.  Thanks for the help on that.

---

### Post by Mazate on 2011-04-18
OK I take it back.  I went in and removed everything (including the fluendo mp3 codec) and I still have bad and ugly in my list.  There are still other gstreamer things installed but they all have the little Ubuntu logos next to them which I assume (perhaps erroneously) were installed with the OS.  Should the bad & ugly stuff disappear when I run that command above once I go into the synaptic package manager to remove them?

---

### Post by K_45 on 2011-04-18
I would keep the codecs, otherwise most media files you might have will not work. Run the command I gave again to see what is left if you really want to get rid of them.

---

### Post by Mazate on 2011-04-18
Yeah I ran it... It still shows bad and ugly stuff in there.  Do I have to delete all gstreamer stuff to get rid of them?

---

### Post by Mazate on 2011-04-18
Ok, I just did a brand new clean install of Ubuntu and did NOT select the option to have the MPEG/MP3 (licensed) decoder added on with the installation and this is what I have.  I haven't installed anything, including updates.

gstreamer0.10-plugins-base - GStreamer plugins from the "base" set
gstreamer0.10-plugins-base-apps - GStreamer helper programs from the "base" set
gstreamer0.10-plugins-base-dbg - GStreamer plugins from the "base" set
gstreamer0.10-plugins-base-doc - GStreamer documentation for plugins from the "base" set
gstreamer0.10-plugins-good - GStreamer plugins from the "good" set
gstreamer0.10-plugins-good-dbg - GStreamer plugins from the "good" set
gstreamer0.10-plugins-good-doc - GStreamer documentation for plugins from the "good" set
gstreamer0.10-plugins-bad - GStreamer plugins from the "bad" set
gstreamer0.10-plugins-bad-dbg - GStreamer plugins from the "bad" set (debug symbols)
gstreamer0.10-plugins-bad-doc - GStreamer documentation for plugins from the "bad" set
gstreamer0.10-plugins-cutter - Cutter GStreamer plugin
gstreamer0.10-plugins-ugly - GStreamer plugins from the "ugly" set
gstreamer0.10-plugins-ugly-dbg - GStreamer plugins from the "ugly" set (debug symbols)
gstreamer0.10-plugins-ugly-doc - GStreamer documentation for plugins from the "ugly" set
gstreamer0.10-plugins-bad-multiverse - GStreamer plugins from the "bad" set (Multiverse Variant)

---

### Post by Yellow Pasque on 2011-04-18
[http://www.gnewsense.org/Main/HomePage](http://www.gnewsense.org/Main/HomePage)

---

### Post by Mazate on 2011-04-18
Xx

---

### Post by wolfen69 on 2011-04-18
> **Mazate said:**
> I haven't installed anything, including updates.



Doing updates won't add non-free stuff, it just updates what you already have. It's recommended to do the updates.

---

