---
title: "How can I play WMV files?"
date: 2006-12-07
forum: Multimedia &amp; Video
---

### Post by core on 2006-12-07
Hi

I can't play WMV files. Totem can't read them, MPlayer can't read them, I dunno. I've installed w32codecs using Automatix2. Running edgy, upgraded from dapper.

Any ideas?

---

### Post by mitch.c on 2006-12-07
> **core said:**
> Hi

I can't play WMV files. Totem can't read them, MPlayer can't read them, I dunno. I've installed w32codecs using Automatix2. Running edgy, upgraded from dapper.

Any ideas?
What is the output of the following commands?

If there's no output here, the codecs aren't installed:
```
$ aptitude search w32codecs | grep ^i
```
If codecs are there, then try...
```
$ gst-inspect-0.10 pitfdll | grep features
```
If the last command says "0 Features", then:
```
$ mv ~/.gstreamer-0.10 ~/.gstreamer-0.10.bak
$ gst-inspect-0.10
```
See if that fixes it.

---

### Post by core on 2006-12-08
diogo@core:~$ aptitude search w32codecs | grep ^i
i   w32codecs                       - win32 binary codecs                       
diogo@core:~$ gst-inspect-0.10 pitfdll | grep features
  11 features:

I think i've already tried that .gst-inspect-0.10 backup thing from some other thread.

What am I missing? Thanks in advance.

---

### Post by Zero Prime on 2006-12-08
I use the mediaplayerconnectivity plugin for Fire Fox.  It uses VLC and works with no problems for me.

---

### Post by RudolfMDLT on 2006-12-08
Hi core,

please look at this link - It has helped lots of people and if it doesn't at least we know that you have installed the codecs and media engine's.

[http://ubuntuforums.org/showthread.php?t=182902](http://ubuntuforums.org/showthread.php?t=182902)

Good luck,

Cheers!

---

### Post by core on 2006-12-08
> **Zero Prime said:**
> I use the mediaplayerconnectivity plugin for Fire Fox.  It uses VLC and works with no problems for me.

Damn, when you referred VLC then I noticed, I hadn't tried VLC yet! Somehow, It worked. GXine worked also. MPlayer doesn't, Totem doesn't. I don't know why, I'm still hoping someone can explain me why.

RudolfMDLT, thanks for your advice. I was only missing gxine, which also read my wmv files. No luck for totem nor mplayer though.

---

