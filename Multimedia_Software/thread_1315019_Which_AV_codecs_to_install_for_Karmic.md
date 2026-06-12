---
title: "Which AV codecs to install for Karmic???"
date: 2009-11-04
forum: Multimedia Software
---

### Post by emeraldgirl08 on 2009-11-04
I am wondering what code in terminal I would need to run to get DVD playback w/ VLC. I have no problem playing FLVs and AVIs with VLC. It's when I try playing commercial DVD's that it does not work.

I also would like the MP3 codecs required to listen to music. I can play MP3's through VLC but Rhythmbox or Banshee would be preferable.

As far as flash in Firefox I got that working by clicking on the Install Missing Plug-ins. Now I can watch Youtube videos. 

I know all about the complete AV Multimedia Guide but that requires a solo wifi connection which is hard for me to get right now. I share the connection and it would take WAY TOO long to do it that way! 

So I just need the code in terminal to play commercial DVD's and the necessary codec to play MP3 formats.

TIA.

---

### Post by mick222 on 2009-11-04
```
sudo apt-get install w32codecs libdvdcss2
```

that should give you dvd play back for mp3s install gstreamer pluginsugly from synaptic

---

### Post by emeraldgirl08 on 2009-11-05
```
Package w32codecs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package w32codecs has no installation candidate

```

That's what I get when I try and put the code in.

and there are different versions of gstreamerugly...which one do I install?

---

### Post by emeraldgirl08 on 2009-11-05
Okay solved my issues...

*knock on wood*

Enabled the Medibuntu repository..

```
sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list; sudo apt-get -q update; sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring; sudo apt-get -q update
```

then

```
sudo apt-get install w32codecs libdvdcss2
```

I popped in a commercial DVD and ran it through VLC. It works! Now for the MP3's!

Going to Synaptic was a little daunting. I had a horrible problem with sound in Jaunty w/my R51e. So far I have none in Karmic so I really don't want to ruin it!

I merely opened up rhythmbox and clicked on an MP3 in "open file" and it prompted to look for the codecs. I figured "why not?" and now I can listen to MP3's :D

Thanks for the useful advice guys!

---

### Post by e-nygma on 2009-11-05
You seem to have everything under control, but generally it's good idea to use **w32codecs[B] only if you're using the 32-bit OS.  If you're using 64-bit OS, then you should use [B]w64codecs**.  

If you want full multimedia support (audio and video), then it will be a good idea to install the **Ubuntu restricted extras and Gstreamer fluendo MPEG2 demuxing plugin** in addition to what you have already installed.  They can be installed through the software center.  As for flash support, just open up a terminal and type:

**sudo apt-get install flashplugin-nonfree.**

---

