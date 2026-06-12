---
title: "Codecs In Linux"
date: 2007-02-22
forum: Multimedia &amp; Video
---

### Post by maikoherajin on 2007-02-22
Having gotten my laptop more or less set up successfully with Ubuntu and Kubuntu, I thought I'd turn to getting videos to work now. Here's my question: What's the underlying idea behind video codecs in Linux? For example, almost all codecs in Windows, you install through an installer, which registers them with Direct Show, creating an codec.ax file (I think?) which any compatible program can use, and then can be upgraded later.

Now on Linux, I've seen about about 5 different descriptions on how to install third party codecs, ranging from compiling them myself to long lists of APT packages. Are all these methods installing library files which can then be upgraded when a new version of the codec is released? Can any media program access these libraries and use the codec, or do I need to download a specific version of the codec for a specific media player? Help me end the confusion! (:

Thanks in advance!

---

### Post by rocknrolf77 on 2007-02-22
The codecs is installed for every program that needs them. I install the codecs with either automatix or from the repos. :)

---

### Post by justin whitaker on 2007-02-22
> **maikoherajin said:**
> Having gotten my laptop more or less set up successfully with Ubuntu and Kubuntu, I thought I'd turn to getting videos to work now. Here's my question: What's the underlying idea behind video codecs in Linux? For example, almost all codecs in Windows, you install through an installer, which registers them with Direct Show, creating an codec.ax file (I think?) which any compatible program can use, and then can be upgraded later.

Now on Linux, I've seen about about 5 different descriptions on how to install third party codecs, ranging from compiling them myself to long lists of APT packages. Are all these methods installing library files which can then be upgraded when a new version of the codec is released? Can any media program access these libraries and use the codec, or do I need to download a specific version of the codec for a specific media player? Help me end the confusion! (:

Thanks in advance!

I'll take a stab at this.

The idea behind just about everything in Linux is that someone saw a need at some point for something, and created a package or application for it. So you have a bunch of different codec packages that sprung up as time rolled on. Once you have the codec installed, pretty much any application can access it. 

Keep in mind, this is no different  in Windows, save for the fact that you can get codec packages like UltimateXP Codec pack (or something) and download them all at once.

For codecs, generally, I find it is best to handle them via tools like Easy Ubuntu or Automatix. Let those boys handle the endless list! :)

---

### Post by TheWizzard on 2007-02-22
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

i'd advice not to use automatix or easy ubuntu

---

