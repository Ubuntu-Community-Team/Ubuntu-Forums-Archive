---
title: "TV Tuner Card, Video Capture Card, Graphics Card ?"
date: 2008-07-27
forum: Multimedia Software
---

### Post by Sonomablue on 2008-07-27
All,

I am new to this forum. I am hoping that you can assist me.

My main desire is to convert VHS tapes to DVD, and my Sony Super-8 tapes to DVD. 

Through my research I have found (at least) 4 ways of doing this. (1) Buy a standalone DVD recorder, and connect the VCR inputs to the DVD standalone recorder, hit play on VCR and record on DVD Recorder. (2) Buy a DV camcorder, connect the VCR to the DV camcorder, and let the DV camcorder perform the analog to digital conversion, and use a firewire connection to the PC, to capture the video (from the VHS tape). (3) buy an "external analog capture device", plug the VCR into external capture device, and plug the ext capture device to PC (via firewire or USB) and send the video to the PC. (4) buy an internal capture card for the PC, attach the vcr to the capture card, and hit play on the vcr, adn record on some PC software.

I have done some preliminary research on all 4 methods. 

My question to you related to "internal video capture cards".  What determines what is, and what is not, a "video capture card"? Is it a function of the card itself, or is it the associated software that comes with the card?

Let me explain, some details, and why i am a bit confused. 

There are video capture cards.
There are TV Tuner cards.
There are Graphics cards. 

I know that not all graphic cards are video capture cards. but i believe that some video capture cards serve as a graphics card. (please confirm if this is true, or not).

I am really confused as to whether all TV Tuner cards are also PC Capture cards. 

for 'my' situation. I have a new HP Pavilion m9300t. 

It came with a Nvidia 9300 256MB graphics card. (not the best gaming card in the world, but it is doing quite well so far, since i am not a gamer). I do know that the Nvidia 9300 is NOT a video capture card, but it is my graphics card.

My HP Pavilion also came with a "TV TUNER Card with PVR, FMTUNER and Remote" (i have come to find out that it is a "ViXS PureTV 48B9  (NTSC/ATSC combo)".

What i do NOT know is if my "ViXS PureTV TV Tuner card" is ALSO a "video capture card".  

Here is what i have been able to do so far:

I have cabled the output from my Direct receiver to the TV Tuner card (via s-video, and composite red/white audio RCA connecters). I am able to "view" my Directv channels on my PC using Vista's Windows Media Center. It is fun, but it is not my main goal (VHS tapes to DVD).

I also connected my Super-8 (analog) camcorder to the TV Tuner card. I am able to see the video (via Windows Media Center). 

I also downloaded the trial copy (free 30-day version) of ULead/Corel VideoStudio 11.5 Plus. When i bring up the software, the "capture" function does NOT see the video from my Super-8 camcorder, like Windows Media Center did.

Therefore, my question about what IS, and what is NOT a video capture card (analog capture, of VHS or Super-8, so i can copy to PC and record a DVD).

Any thoughts?

Is my TV Tuner card "not" a video capture card? 

thanks very much for any helpful information?

---

### Post by steefjeqv on 2008-07-27
Hi,

It seems that your tuner card has input functions, as you can use it with an s-video connection from another source.

To be sure, use the following command in your terminal :

sudo dmesg | grep v4l

If the output is something like : "registered device video0", then you may have a go at capturing your video tapes.

I've got no experience in video capture but you can give DVR a go :

sudo apt-get install dvr avifile-divx-plugin avifile-mad-plugin avifile-mjpeg-plugin avifile-player avifile-utils avifile-vorbis-plugin avifile-win32-plugin avifile-xvid-plugin avifile-vorbis-plugin avifile-win32-plugin avifile-xvid-plugin

To start it (using terminal) :
dvr-qtgui

There's also a possibility using TvTime and mplayer. It's partially terminal based.

[http://forum.videohelp.com/topic307679.html]("http://forum.videohelp.com/topic307679.html")

Greetings,
Steven

---

