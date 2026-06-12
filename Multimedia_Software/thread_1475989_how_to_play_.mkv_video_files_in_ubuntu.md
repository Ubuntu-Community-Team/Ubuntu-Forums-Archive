---
title: "how to play .mkv video files in ubuntu"
date: 2010-05-07
forum: Multimedia Software
---

### Post by maizuddin35 on 2010-05-07
Hey linux peeps!

I have this one video files format .mkv
I've tried playing it at vlc but I can't hear a thing, and I tried to play it on others video player, but they just didn't work.
Anyone know how ?

I'm now using Ubuntu Lucid Lynx

---

### Post by Naggobot on 2010-05-07
First I must admit that I am no expert of this matter (or any other if it comes to that) but from the bits and pieces I have gathered  .mkv indicates a Matroska container

[http://www.matroska.org/](http://www.matroska.org/)

Now if I quess right the problem is not .mkv but the contained video and its codec. 

Do you have restricted extras installed?

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

Package contains some common patent encumbered codecs and you could try it if it is legal at your area.

---

### Post by maizuddin35 on 2010-05-07
how do I check if I installed it already or not?

---

### Post by Naggobot on 2010-05-08
From top menu select

system->administration->synaptic package manager

(System asks for password)

In Synaptic there is a quick search box in the top / center. To this box write

```
ubuntu-restricted
```

This operation filters the view so that the package should be visible. 

If the package is not visible then you need to add the relevant repository. This is done in synaptic by just simply selecting 

settings -> repositories

In the first tab just click every box except source code. 

After you close the tab click top left reload button to refresh the view. This should now bring up the restricted extras package  if you still have the quick search filter text in the box. If not then rewrite it. 

My apologies for not including the instructions in the first post. I was in a bit of a hurry. Hope this helps.

---

### Post by maizuddin35 on 2010-05-08
In my package manager the *ubuntu-restricted-extras* has been installed. 
the .mkv video files can still play, but lacking of sound, and some when I play at VLC there are no sound at all

---

### Post by strikoo on 2010-05-08
install gnome mplayer or open with totem player and install drivers that it offers.

---

### Post by mistermentality on 2010-05-08
I`m a newb but maybe I can help? I`ll try anyways.

First off to find what audio codec is in use, so you can post it here in case it is the problem, when playing the video go to the tools menu and choose the media information option to show you the video and audio info such as what video and audio type it is.

If VLC plays the video then you should be able to go into the programs preferences menu and change the settings as if it plays the video it should also play the audio.

Either try changing the default audio output method (I changed mine from Pulse to Alsa because on another linux os Pulse resulted in random screeching sounds over videos and Alsa didn`t).

It is possible the mkv is badly formatted or maybe damaged, although more likely that for some reason the audio codec is either not installed or is not being used.

If I recall correctly it is possible to make VLC use specified decoders via the preferences menu and it`s advanced option.

If the audio codec shows up with a name it should mean Ubuntu knows what it is and therefore with some preference adjustments in vlc should be able to work.

---

### Post by maizuddin35 on 2010-05-08
@strikoo: I've done installing mplayer . but when i click the play button, there is nothing happen.

---

### Post by strikoo on 2010-05-10
> **maizuddin35 said:**
> @strikoo: I've done installing mplayer . but when i click the play button, there is nothing happen.

you need to open the video file that you want to play or right click on video-open with and choose mplayer

---

### Post by hsoulen on 2010-05-10
Hi folks.

I use Smplayer (front end for mplayer) which takes some of the "geek" out of mplayer.

Available in Synaptic.

Also, if you have a 9000+ series NVidia card and the latest proprietary drivers you can use VDPAU and enjoy HD mkv files as well.

Cheers,

Hank

---

