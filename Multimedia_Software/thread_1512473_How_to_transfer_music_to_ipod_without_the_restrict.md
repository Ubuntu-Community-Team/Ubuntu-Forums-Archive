---
title: "How to transfer music to ipod without the restricted extras"
date: 2010-06-18
forum: Multimedia Software
---

### Post by notbitmonk on 2010-06-18
I found an old ipod (2nd gen I think) which I gave to my daughter. I was able to read and then delete the music in it. It is formatted for Windows.  I tried adding files to it with no luck. My music files are all FLAC that I rip from my Cds. I bought the Fluendo codecs (decoding only) and then installed LAME. That means that I didn't install the Ubuntu restricted extras. I have noticed that for several versions of Ubuntu, Rhythmbox will not let you select mp3 as a rippable format if the restricted extras are not installed. I have done this over 20 times and the result is always the same. I can install LAME but to actually have mp3 encoding support in Rhythmbox, you have to install the restricted extras. I do not want to install the restricted extras. Does anyone know what happens during the restricted extras installation that makes Rhythmbox encode to mp3?  This will potentially make Rhythmbox transcode the FLAC to mp3 and transfer it to the ipod.  I know that I may be able to install Songbird or gtkpod but that is not the point.

---

### Post by notbitmonk on 2010-06-18
Can someone that has the restricted packages copy the command (or gstreamer pipe, or however is called) used in Rhythmbox to rip to mp3 and post it here to compare if there is a difference with the one that I have.

---

### Post by hansdown on 2010-06-18
Hi notbitmonk.

I think gstreamer lame, is included in the ubuntu-restricted extras.

```
sudo apt-get gstreamer0.10-fluendo-mp3
```

---

### Post by howefield on 2010-06-18
If you are feeling adventurous you could try Rockbox, an alternative firmware for the ipod which supports the playing of FLAC files.

rockbox.org

---

### Post by notbitmonk on 2010-06-18
@howefield: Yes, I thought about Rockbox but this is something I want to test.  I install Ubuntu for friends and other people and not everyone will want to change their ipod.

@Hansdown: The one that you are posting is the fluendo coded to decode mp3.  Fluendo does not offer an mp3 encoder.  The details from the package page ([http://packages.ubuntu.com/lucid/gstreamer0.10-fluendo-mp3):](http://packages.ubuntu.com/lucid/gstreamer0.10-fluendo-mp3):)
> This GStreamer plugin permits decoding of MPEG 1 audio layer III streams. It is derived from the ISO MPEG dist10 reference package.

That is why I want to know what is in the settings in Rhythmbox.  Maybe the pipe is changed when the restricted extras are installed.  Unfortunately for me, I do not know much about gstreamer pipes to make sense of it without something to compare.

---

### Post by howefield on 2010-06-18
> **notbitmonk said:**
> Rhythmbox will not let you select mp3 as a rippable format if the restricted extras are not installed. 

This isn't true., you do not need ubuntu-restricted-extras to rip CD to mp3. 

The required codec may well be in ubuntu-restricted-extras, but that is not the same as saying you need the package as a whole.

> Gstreamer Pipeline
audio/x-raw-int,rate=44100,channels=2 ! lame name=enc mode=0 vbr-quality=6 ! id3v2mux

Rips to mp3.

---

### Post by notbitmonk on 2010-06-18
@howefield:  Thanks for the pipe.  It may well be that I do not need ubuntu-restricted-extras to rip CD to mp3. The only requirement will be Lame.  However, in the window were the pipeline is constructed, there is an option to mark the instruction as active (a check box).  In every installation I've done it is checked by default.  However, in the dropdown box in which I can select which "format" to rip, mp3 does not show up.  It is only after the installation of the restricted extras that the option is available.  That has happened in every installation that I've made and that is the reason for which I think that it has something to do with the installation of the restricted extras.

---

### Post by howefield on 2010-06-18
> **notbitmonk said:**
> It is only after the installation of the restricted extras that the option is available.

Yep, because the restricted extras includes the package you need.

That isn't to say that restricted extras are required to enable mp3 ripping, restricted extras is simply a collection of packages that give you flash, java and some multimedia capability, maybe some other things, I don't know, I don't install the restricted extras package.

I am going to do a fresh install on a machine, I'll let you know what I need to enable mp3 ripping.

---

### Post by howefield on 2010-06-18
The package that gave me CD to mp3 ripping in Rhythmbox was

```
gstreamer0.10-plugins-ugly-multiverse
```

which as you can see forms part of the ubuntu-restricted-extras package.

[http://packages.ubuntu.com/lucid/ubuntu-restricted-extras](http://packages.ubuntu.com/lucid/ubuntu-restricted-extras)

---

### Post by notbitmonk on 2010-06-18
On the gstreamer page for the Lame plugin says that it needs libgstlame.so ([http://www.gstreamer.net/data/doc/gstreamer/head/gst-plugins-ugly-plugins/html/gst-plugins-ugly-plugins-plugin-lame.html#plugin-lame](http://www.gstreamer.net/data/doc/gstreamer/head/gst-plugins-ugly-plugins/html/gst-plugins-ugly-plugins-plugin-lame.html#plugin-lame)).  In Ubuntu, that is located in gstreamer0.10-plugins-ugly-multiverse.  Ended up in Synaptic and installed it.  Plugged the ipod and that was it. howefield, thanks for all your help.  For a quick summary: 
On a fresh installation of Ubuntu, mp3 encoding is not available.  Mp3 encoding can be enabled by installing LAME and gstreamer0.10-plugins-ugly-multiverse.  Both can be installed from the Ubuntu Software Center.

---

