---
title: "No audio on Cinelerra"
date: 2009-01-05
forum: Multimedia Software
---

### Post by ghicking on 2009-01-05
Hi everyone

I've installed cinelerra 4 on Ubuntu 8.10.  It resides in /usr/bin.  I've put lbimpeg3 in the same directory. I have change the settings/preference/ausio to Esound and nominated port 7007. I can load files and play them on the compiler, but there is no sound output.  Can anyone tell me what to try next?

Graham

---

### Post by JacePriester on 2009-01-11
I had the same problem and fixed it. Choose ESound as the driver, enter "front" as the server, and "0" as the port.

I'll walk you through my solution.

1. Checked to see if 7007 was indeed the right port.
Ran 'sudo nmap 127.0.0.1 -p1-65535' and no server was found at 7007.

2. Installed paman, paprefs, and padevchooser, and pavumeter to play with PulseAudio settings.
Determined by digging through paman menus that Rhythmbox was connecting to "front:0", so I figured this would work.

3. It did!

On a side note, I was playing with audio coming from my digital camera which apparently has stuffed all the audio in the Left channel (or is Cinelerra handling mono sound wrong, or something?) , and my left channel on my speakers is not working due to a broken wire so I had to plug in headphones. Thought this could *possibly* be an issue for you as well since we typically use this type of program for editing videos coming from cameras.

Good luck!

---

### Post by zander1013 on 2009-01-23
is it a "must" to put libmpeg3 in the same dir?

i set things the same way in my install but the audio is over driven? such that it is very garbled. i hate to change the location of things like that unless i must.

please advise.

-zander:(

---

### Post by zander1013 on 2009-01-24
well,

it looks like the lib file does not have to be in /usr/bin. the sound is working. it works for mpegs but not .avi format created by my flip aqua. which has only one microphone.

can anyone suggest a way to overcome this limitation of using the flip cam?


-zander

---

### Post by ghicking on 2009-01-28
Thanks everybody

I stumbled on a solution.  I had to reinstall the OS after my PSU went down during a write.  When it came to Cinelerra, I realised that I was downloading from the wrong place. By putting this repo into the sources third party list (System -> Administration -> Software Sources)

[http://akirad.cinelerra.org akirad-intrepid main](http://akirad.cinelerra.org akirad-intrepid main)

I could install Cinelerra from Synaptic with all the dependencies sorted out automatically and a version tweaked to work with Debian/Ubuntu.

I hope that helps you all out with your various problems.

Thanks again

---

### Post by GlennW on 2009-08-20
Hey guys,I don't know if this quite the right place to discuss this (admin re-direct if necessary). 

I found that I could install Cinelerra from Synaptic so the whole compiling thing was unnecessary and obviously not so messy. Everything went very well. 

The only issue I have, other than attempting to scale the steep learning curve, is that any avi files that I have taken with my digital camera are highly distorted during playback in Cinelerra. 

I can transfer the same files to my office laptop and use Windows Movie Maker and the playback there is as it should be. I would much rather use Cinelerra if possible.

Is there a work-a-round for this distortion issue?

Thanks. Oh, try to keep it simple as I'm still quite new to Linux.

---

### Post by GlennW on 2009-08-21
Well, I found a temporary fix. Using ffmpeg (WinFF gui) I converted my avi files to dv files. The distortion is non existent. A great by product of this conversion is that the quality of the file is enhanced.

ciao.........

---

