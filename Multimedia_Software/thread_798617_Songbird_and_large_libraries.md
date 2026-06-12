---
title: "Songbird and large libraries"
date: 2008-05-18
forum: Multimedia Software
---

### Post by mtblock on 2008-05-18
First of all, can it handle large libraries? Will it accept music and keep it on and external hard drive? What is needed for an install/ How?

---

### Post by meanerelk on 2008-05-18
I haven't used it yet, so I don't know about the features you asked about. However, I am sure it will handle large libraries, external media, etc. gracefully. After all, this is 2008.

As for installing, I found this guide that may help, though it is a bit old: [http://www.ubuntugeek.com/install-songbird-music-player-in-ubuntu.html](http://www.ubuntugeek.com/install-songbird-music-player-in-ubuntu.html)

---

### Post by mtblock on 2008-05-18
Ok, I downloaded and installed songbird successfully. When I click on a song, it tells me I need gstreamer and such. I have tried, but I cannot install/get this to work. How do I install gstreamer? I tried through synaptic package amanager, but that didn't work.

---

### Post by meanerelk on 2008-05-18
why didn't it work? did you get any error messages or anything? Have you enabled the other repos, like universe and multiverse?

Also, try taking a look at what the songbird wiki says about gstreamer plugins:

[http://publicsvn.songbirdnest.com/wiki/SettingUpGStreamer](http://publicsvn.songbirdnest.com/wiki/SettingUpGStreamer)

---

### Post by mtblock on 2008-05-18
I'm new to this. How would I do that?

---

### Post by meanerelk on 2008-05-18
The documentation is your friend for this kind of thing.

[https://help.ubuntu.com/8.04/add-applications/C/extra-repositories-adding.html](https://help.ubuntu.com/8.04/add-applications/C/extra-repositories-adding.html)

---

### Post by HomerSp on 2008-05-18
It currently does not handle large libraries well. I have a 70.000+ MP3 library and Songbird is pretty much unusable as it takes forever to load the program and switch to the Library tab.
However, they have promised that the next release will have better support for big libraries.

---

### Post by ufugu on 2008-05-20
Try the blessed .6pre build.  After an initial database build it works faster than anything else I've tried with my just under 20,000 library.  The .5 release was a dog, not a bird.

---

### Post by HomerSp on 2008-05-21
I tried the latest nightly and it doesn't handle my 70.000+ library very well sadly.

---

