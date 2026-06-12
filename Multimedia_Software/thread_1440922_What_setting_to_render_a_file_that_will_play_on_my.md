---
title: "What setting to render a file that will play on my DVD player."
date: 2010-03-28
forum: Multimedia Software
---

### Post by OsakaWilson on 2010-03-28
I am trying to create video on Ubuntu that will play on my DVD player. The player is a Pioneer DV-420-V. Below is a description of the features. Nearly anything I download from the net plays on it with no trouble--I just plug my hard-disk USB into the player and it works. However, I can't figure out how to render a file that works. I'm using Pitivi. I would be eternally grateful if someone can help with this.Below are my DVD player specifications.


Key Features

    * Plays DVD Video, DVD-R, DVD-RW (Video Format), CD, CD-R/RW, VCD, SVCD, WMA, MP3 and JPEG formats
    * Plays All-Region DVDs: Region 1, 2, 3, 4, 5, 6, 0
    * Plays PAL and NTSC Region DVDs on all TVs.
    * DVD-R/DVD-RW compatible
    * WMA/MP3/Jpeg playback
    * Advanced Disc Navigator
    * HDMI Output

Video Features

    * 108 MHz/12-bit D/A converter
    * Dual PureCinema Progressive Scan (PAL/NTSC)
    * Dual-Layer DVD-R*1/DVD/ DVD-R/DVD-RW*2/DVD+R/DVD+RW playback
    * SVCD/VCD/CD/CD-R/CD-RW playback
   ** * 1080p upscaling with HDMI output**
  **  * Official DivX Certified product**
    * WMV playback
    * PhotoViewer*3 (JPEG Playback)
    * Video Adjust function with Sharpness/Brightness/Contrast/Gamma/Hue/Chroma Level control
    * Zoom function
    * PAL/NTSC Dual System with PAL-NTSC video converter

Audio Features

    * 96 kHz/24-bit D/A converter
  **  * WMA/MPEG-4 AAC/MP3 playback**
    * Sound Equalizer (Rock/Pop/Live/Dance/Techno/Classic/Soft)
    * Virtual Surround

Conveniences

    * USB Terminal
    * PHOTO + MUSIC MIX (JPEG Slideshow with Music)
    * Advanced GUI
    * Disc Navigator for easy browsing
    * Last (Position) Memory: 5 (DVD)/1 (VCD)
    * Resume function*5
    * Screen saver 
    * Auto Power off

Terminals

    * 1 x HDMI output
    * 1 x USB (front-in)
    * 1 x Component out
    * 1 x Coaxial out
    * USB

---

### Post by cotcot on 2010-03-28
I opened pitivi and did not found detailed information on the render settings.
DVD video is mpeg2 with ac3 audio. I guess that the PAL option in the render choices is mpeg2. The default sound format (CD) is not correct. DVD is 48 kHz instead of 44.1. 
If you use Devede or DVDstyler or so to make a DVD from your rendered videos with Pitivis default settings you do not need to care a lot about these. These apps do the required transformation automatically.

---

### Post by OsakaWilson on 2010-03-28
To see the rending options, you have to stick a video in and click the render button. Then there will be a 'modify' button. 

I haven't been able to use DeVeDe since 9.10 because it tells me that it can't find mplayer and mencoder even though they are installed and have been reinstall to be sure. I've just been waiting until 10.04 hoping that it works. 

I don't think this is related to the Pitivi problem because the videos I make play fine on computers.

---

### Post by cotcot on 2010-03-28
If you have mencoder and mplayer installed this means that devede cannot find it.
Check where you have them. Most likely /usr/bin/ or /usr/local/bin/
It could be that devede is searching in /usr/bin/ whereas you have them in /usr/local/bin/. Than you could provide a link :

```
cd /usr/bin
ln -s /usr/local/bin/mplayer mplayer
ln -s /usr/local/bin/mencoder mencoder
```

---

