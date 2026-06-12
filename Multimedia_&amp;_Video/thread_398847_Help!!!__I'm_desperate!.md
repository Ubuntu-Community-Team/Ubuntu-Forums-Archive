---
title: "Help!!!  I'm desperate!"
date: 2007-04-01
forum: Multimedia &amp; Video
---

### Post by PyroMessiah on 2007-04-01
Okay, I'm going to try to explain this as best I can.   I'm at my wit's end.

I'm trying to record from cassette tape into mp3.  It's a bunch of lectures from my father in law's professor from years ago that he wants to save digitally.  This is easy enough to do in windows with a program called LP Recorder and a simple male-male mini-cable going from the headphone jack of my stereo to the front line-in on my computer.  

Thing is, I don't want to have to use windows anymore and the only thing keeping it on my computer is that I simply can't get this to work in Ubuntu and I've been trying for months on and off.  All of the suggestions I've seen so far have to do with the alsa mixer and drivers.  But, when I fire up alsa mixer, you see that there are bars above the things you can change....such as above "PCM" (whatever that is) there is a bar graphic and I can make it go up and down.  

Above "Line" there is nothing.  In fact, the only ones I have the option to change are PCM and PC Speaker.  Above some, like "Center" there is a green "00" but I am not able to change anything.  Above Line there is nothing.  Hitting up and down only changes it to "CD" or rear or front mic.  So, I am unable to change the volume of the input source....I guess actually it is not letting me have an input source at all.  

Anyway,  I desperately want to rid myself of Windows but I just can't figure this out.  I even learned how to change and rpm into a deb package to install the latest alsa driver, but the problem remains unchanged.  Please, please help and remember to speak in dummy terms as I am very, very unskilled in Linux.

---

### Post by reclusivemonkey on 2007-04-01
Have you tried the "Preferences" in Gnome Mixer? You should be able to tick some of the capture boxes in there and get your Line-In to appear in the recording tab.

---

### Post by johnc4510 on 2007-04-01
I have converted many cassettes to mp3 by using single male male adapter. The app you need is audacity. You can record the cassette via the line in and then export it as an mp3.

---

### Post by PyroMessiah on 2007-04-01
Audacity doesn't work either.  I get this message:  "Error while opening sound device".

This is ***incredibly*** frustrating and the reason why I don't switch from windows.  Somebody out there must have had this problem before, right???

---

### Post by johnc4510 on 2007-04-01
In Audacity:

Edit>Preferences>Audio IO

Check that Playback and Recording show a device in the dropdown

Mine is /dev/dsp

Also close all other sound devices: XMMS Mplayer etc.

---

### Post by PyroMessiah on 2007-04-01
> **johnc4510 said:**
> In Audacity:

Edit>Preferences>Audio IO

Check that Playback and Recording show a device in the dropdown

Mine is /dev/dsp

Also close all other sound devices: XMMS Mplayer etc.

Tried changing it to /dev/dsp and I get the same error.  :confused: 

I'm about ready to bash my own brains in.  This sucks.  I'm starting to wonder why I am bothering with ubuntu.

---

### Post by KevlarSoul on 2007-04-01
Have you tried this: [http://jackaudio.org/](http://jackaudio.org/)


HAve you tried this:

"I figured out a rather unorthodox solution for this - apparently the sound chipset goes over the USB buses, which you'll see if you type lsusb in the terminal. If you're using Edgy, go to the multimedia preferences and select USB audio for all the outputs and inputs. It should work then."

THIS IS YOUR AUDIO INFO:
8 Channel Azalia controller integrated in Intel ICH6 Chipset
 &#8226;  8-channel audio codec C-Media 9880L
 &#8226;  Compliance with Azalia 1.X spec
 &#8226;  Support Multi-Streaming function
 &#8226;  Support Universal Audio Jack (only Front Audio Jack)

---

### Post by johnc4510 on 2007-04-01
Ok, here a wiki page for your problem:

[http://audacityteam.org/wiki/index.php?title=Linux_Issues](http://audacityteam.org/wiki/index.php?title=Linux_Issues)

---

### Post by PyroMessiah on 2007-04-01
> **KevlarSoul said:**
> Have you tried this: [http://jackaudio.org/](http://jackaudio.org/)


"...If you're using Edgy, go to the multimedia preferences and select USB audio for all the outputs and inputs. It should work then." 

I'm not using Edgy, I'm using Feisty and there is no such option.  I'll try that Jack thing.  Thanks.

---

### Post by PyroMessiah on 2007-04-01
> **johnc4510 said:**
> Ok, here a wiki page for your problem:

[http://audacityteam.org/wiki/index.php?title=Linux_Issues](http://audacityteam.org/wiki/index.php?title=Linux_Issues)


Thanks, but this isn't an Audacity specific problem.  I can't get line-in sound or recording with any software at all.

---

### Post by PyroMessiah on 2007-04-01
Installed jack and I can't find it anywhere.  ](*,) ](*,) ](*,) ](*,) ](*,)

---

### Post by fenian on 2007-04-01
It could be a permissions problem try...

> sudo rm /dev/dsp;ln -s /dev/dsp0 /dev/dsp  
sudo chmod 666 /dev/dsp0
sudo chmod 666 /dev/dsp 


#also try /dev/dsp1,2,etc.

---

