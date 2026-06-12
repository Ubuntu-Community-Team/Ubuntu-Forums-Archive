---
title: "How to use: USB microphone Logitech /dev/dsp1 with skype ?"
date: 2005-12-07
forum: Multimedia &amp; Video
---

### Post by patrick295767 on 2005-12-07
How to use: USB microphone Logitech /dev/dsp1 with skype ?
  
It cannot start phoning someone ... error message appears, ...
Someone would know how to solve this ?

 thank you veyr much
 
greetz

pat'

---

### Post by jkyro on 2005-12-09
I don't know what kind of gadget you have, but the basic problem is that the microphone shows up as a separate sound device. So what you'll have to do is to configure a virtual sound device whose capture channel is taken from the USB mic and playback is your normal sound card. Furthermore, since Skype can't use alsa directly, you'll have to use some kind of a wrapper.

Here's some instructions. Skype will work with the aoss wrapper mentioned on the page.
[http://alsa.opensrc.org/asym]("http://alsa.opensrc.org/asym")

---

### Post by Xappe on 2005-12-09
this probably can be done with the skype_dsp_hijacker script (I use the script myself to get rid of the "skype locks sound device" issue).

[http://juljas.net/linux/skype/]("http://juljas.net/linux/skype/")

---

### Post by anil_robo on 2005-12-16
I can't record any sound through any microphone! I tried microphone through the soundcard jack - didn't work. Tried Logitech quickcam webcam (USB mike) - didn't work either. I tried both the steps mentioned in the two posts above - none of them worked either!

---

### Post by patrick295767 on 2006-01-07
[QUOTE=Xappe]this probably can be done with the skype_dsp_hijacker script (I use the script myself to get rid of the "skype locks sound device" issue).

[http://juljas.net/linux/skype/]("http://juljas.net/linux/skype/")[/QUOTE]
  
I got thsi : 
```
./skype_dsp_hijacker --mic2nd
ERROR: ld.so: object '/usr/local/lib/libskype_dsp_hijacker.so' from LD_PRELOAD cannot be preloaded: ignored.

```
  
How to make it...? 
  
Thank you !

Pat'

---

### Post by fdimmling on 2006-01-08
I'm using a Logitech USB headset with Skype wich worked out of the box on Breezy. When I connect the headset a window pops up that new hardware is found and leading directly to system->preferences->audio where I select the Logitech USB headset as the new default device. In Skype i have selected /dev/dsp1. That's it. In Hoary it should be not as easy because you could not select the default audio device afterwards AFAIK.

Friedrich

---

### Post by patrick295767 on 2006-01-08
[QUOTE=fdimmling]I'm using a Logitech USB headset with Skype wich worked out of the box on Breezy. When I connect the headset a window pops up that new hardware is found and leading directly to system->preferences->audio where I select the Logitech USB headset as the new default device. In Skype i have selected /dev/dsp1. That's it. In Hoary it should be not as easy because you could not select the default audio device afterwards AFAIK.

Friedrich[/QUOTE]
Are u using gnome or kde for this ? Do you see ur logitech headset in the alsamixer ? Is it present the /dev/dsp1   in audacity ? 
I just  tried to plug / un plug with my breezy and it's not saying anythg...
I am stuck with that since 1-2 months now ... 

Thank you 

Pat'

---

### Post by fdimmling on 2006-01-08
[QUOTE=patrick295767]Are u using gnome or kde for this ? Do you see ur logitech headset in the alsamixer ? [/QUOTE]

I'm using Ubuntu with Gnome. I can see the headset as "Logitech USB Headset" when I call the alsamixer with

alsamixer -c 1

otherwise I get the built in Intel sound chip of my Acer Travelmate. I do not use audacity but I can record sound using sweep which is a similar program for Gnome users.

Friedrich

---

### Post by patrick295767 on 2006-01-08
[QUOTE=fdimmling]I'm using Ubuntu with Gnome. I can see the headset as "Logitech USB Headset" when I call the alsamixer with

alsamixer -c 1

otherwise I get the built in Intel sound chip of my Acer Travelmate. I do not use audacity but I can record sound using sweep which is a similar program for Gnome users.

Friedrich[/QUOTE]
  
alsamixer -c 1 
gives : no mixer elems found ;.....

 I will try sweep: looks very nice & promising I hope !
  
THnak you !

Patrick

---

### Post by RagingOcelot on 2006-02-13
[QUOTE=fdimmling]I'm using a Logitech USB headset with Skype wich worked out of the box on Breezy. When I connect the headset a window pops up that new hardware is found and leading directly to system->preferences->audio where I select the Logitech USB headset as the new default device. In Skype i have selected /dev/dsp1. That's it. In Hoary it should be not as easy because you could not select the default audio device afterwards AFAIK.

Friedrich[/QUOTE]

What model number is that headset?

---

### Post by crache on 2006-05-06
I just got this mic and it was a bit of a mess getting everything working. I'm running dapper, so my blog my be a bit of help:

[http://crache.net/blog/2006/05/06/logitech-usb-desktop-microphone-in-linux/](http://crache.net/blog/2006/05/06/logitech-usb-desktop-microphone-in-linux/)

---

### Post by patrick295767 on 2006-06-21
[QUOTE=crache]I just got this mic and it was a bit of a mess getting everything working. I'm running dapper, so my blog my be a bit of help:

[http://crache.net/2006/05/06/logitech-usb-desktop-microphone-in-linux/](http://crache.net/2006/05/06/logitech-usb-desktop-microphone-in-linux/)[/QUOTE]
  
Thank you VERY much !!!
  
I first copied: > pcm.!default {
type plug
slave.pcm "combined"
}

pcm.combined {
type asym
playback.pcm "playback"
capture.pcm "hw:1,0"
}

pcm.playback {
type dmix
ipc_key 1024
slave {
pcm "hw:0,0"
period_time 0
period_size 1024
buffer_size 4096
rate 44100
}
bindings {
0 0
1 1
}
}

ctl.dmixer {
type hw
card 0
}
into ~/.asoundrc,

then : 
> sudo rm /dev/dsp;ln -s /dev/dsp0 /dev/dsp  #also try /dev/dsp1,2,etc.
sudo chmod 666 /dev/dsp0
sudo chmod 666 /dev/dsp 

I am working on it or trying:
I got such error msg for audacity after the ./configure --with-portaudio=v19 --without-portmixer

```

checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking whether gcc needs -traditional... no
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking how to run the C++ preprocessor... g++ -E
checking for a BSD-compatible install... /usr/bin/install -c
checking for lib-src/libmad/frame.h... no
checking for lib-src/libvorbis/include/vorbis/vorbisenc.h... no
checking for lib-src/libid3tag/frame.h... no
checking for lib-src/libsndfile/src/sndfile.h.in... yes
checking for lib-src/libsamplerate/src/samplerate.h... no
checking for lib-src/libresample/include/libresample.h... yes
checking for lib-src/libflac/include/FLAC/format.h... no
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking mad.h usability... yes
checking mad.h presence... yes
checking for mad.h... yes
checking vorbis/vorbisenc.h usability... yes
checking vorbis/vorbisenc.h presence... yes
checking for vorbis/vorbisenc.h... yes
checking id3tag.h usability... yes
checking id3tag.h presence... yes
checking for id3tag.h... yes
checking FLAC/format.h usability... no
checking FLAC/format.h presence... no
checking for FLAC/format.h... no
--- Configuring soundtouch
--- Configuring libsndfile
--- Configuring libresample
checking for mad_decoder_init in -lmad... yes
checking for mad.h... (cached) yes
checking for vorbis_bitrate_addblock in -lvorbisfile... yes
checking vorbis/vorbisfile.h usability... yes
checking vorbis/vorbisfile.h presence... yes
checking for vorbis/vorbisfile.h... yes
checking for id3_file_open in -lid3tag... yes
checking for id3tag.h... (cached) yes
checking for zip... no
configure: error: "Could not find zip - needed to create the help file"
root@laptop06:~/audacity-src-1.2.4b#   
```
    
====
  I did also : 
alsamixer -c 1 
and put to maximum the recording of the AK stuff microphone
=========
   
  mhwaveedit 
I set : alsa in preference
then it says no input...
===========
  
with : 
arecord -D plughw:0,0 RecTest.wav
and 
arecord -D plughw:1,0 RecTest.wav
 
when checking with totem if there is sthg in ... no sound :-(
  
==============

Linux is so difficult sometimes !  I am so crap.

---

### Post by patrick295767 on 2006-06-21
Nice nfo : [http://www.daniel-lemire.com/blog/archives/2005/10/12/logitech-usb-desktop-microphone-under-linux/](http://www.daniel-lemire.com/blog/archives/2005/10/12/logitech-usb-desktop-microphone-under-linux/)

---

### Post by bkanuka on 2006-11-05
Following your directions, I think I just rm'ed /dev/dsp and now Audacity has an error on startup. uh oh.

---

### Post by patrick295767 on 2006-11-05
> **bkanuka said:**
> Following your directions, I think I just rm'ed /dev/dsp and now Audacity has an error on startup. uh oh.


It was old post. 

Is it for skype purposes ?
Did you try the last skype 1.3 beta ?
[http://share.skype.com/sites/de/2006/06/linux_beta_13_mit_alsaunterstu.html](http://share.skype.com/sites/de/2006/06/linux_beta_13_mit_alsaunterstu.html)
it supports the ALSA.  alsa gives much better results.

For me, it's fully working with skpye my usb microphones (VOip and an usb one too):KS

---

### Post by Versable on 2007-10-06
Just set up skype to use the USB soundcard:

Sound Devices:

Sound in: EasyCall Speakerphone HW
Sound out: EasyCall Speakerphone HW

works like a charm under Gutsy

---

