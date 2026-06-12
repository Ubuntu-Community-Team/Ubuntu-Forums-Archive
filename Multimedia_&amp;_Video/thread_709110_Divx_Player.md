---
title: "Divx Player"
date: 2008-02-27
forum: Multimedia &amp; Video
---

### Post by teejay17 on 2008-02-27
I'm looking for the answer on two things, actually: How do I get Divx videos to play within Firefox? And also, is there a standalone Divx player that I can get for Ubuntu? (Conversely, can I get Divx videos in VLC, Movie Player, etc.)

---

### Post by yabbadabbadont on 2008-02-27
Divx videos are really just renamed avi files that use a specific codec.  mplayerplug-in can play them in firefox, but I think there is a problem with the one in the repositories.  If I remember correctly, it didn't include the divx links in the firefox plugins directory like it should.  There were simple instructions on creating the proper links in the comments of the bug at launchpad about it.  Both vlc and mplayer can play divx files.

---

### Post by renzokuken on 2008-02-27
for watching divx you can use VLC which has the codecs built in, or you could use another player such as mplayer/totem and install the codecs through Synaptic or Add/Remove Programs. codec package is called gstreamer codecs i think.

there is also a codec pack available on the mplayer website.

what do you mean by standalone Divx player *for ubuntu?*

divx files should play in firefox with the mplayer-plugin for firefow

---

### Post by teejay17 on 2008-03-04
I don't know, but I can't get any Divx to play within Firefox. See [ninjavideo.net]("http://ninjavideo.net")
for an example; it's the site I'm trying to get working.

---

### Post by renzokuken on 2008-03-05
ahh i see now, in that  case my advice would be to install the mplayer-plugin for firefox (synaptic), making sure you have all the codecs installed (win32codecs archive available from [www.mplayerhq.hu](www.mplayerhq.hu))

---

### Post by teejay17 on 2008-03-06
> **renzokuken said:**
> ahh i see now, in that  case my advice would be to install the mplayer-plugin for firefox (synaptic), making sure you have all the codecs installed (win32codecs archive available from [www.mplayerhq.hu]("http://www.mplayerhq.hu"))
Thanks...but where exactly do I find the plugin on this site? I can't seem to find it...

---

### Post by wingnux on 2008-03-06
Did you read his answer???

INSTALL IT FROM SYNAPTIC!!

---

### Post by renzokuken on 2008-03-06
Sytem -> Admin -> Synaptic Package Manager

---

### Post by teejay17 on 2008-03-06
> **wingnux said:**
> Did you read his answer???

INSTALL IT FROM SYNAPTIC!!
Win32codecs have already been installed since, like, day one! They're there already, but nothing is working.

---

### Post by yabbadabbadont on 2008-03-06
> **teejay17 said:**
> Win32codecs have already been installed since, like, day one! They're there already, but nothing is working.

He meant that you should install mplayerplug-in from Synaptic...

---

### Post by renzokuken on 2008-03-07
```
sudo apt-get install mozilla-mplayer
```

---

### Post by teejay17 on 2008-03-12
> **renzokuken said:**
> ```
sudo apt-get install mozilla-mplayer
```
I already have that installed! Still no luck.

---

### Post by justsomedude on 2008-03-12
Uninstall totem-mozilla and mozilla-plugin-vlc if present.

Go to /usr/lib/mozilla/plugins and check if there are any leftovers of totem-mozilla and mozilla-plugin-vlc. If there are, remove them.

The site you posted works fine with mozilla-mplayer.

---

