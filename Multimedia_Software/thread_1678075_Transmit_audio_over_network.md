---
title: "Transmit audio over network"
date: 2011-01-29
forum: Multimedia Software
---

### Post by MG2R on 2011-01-29
Here's my situation:

I have a laptop running Ubuntu 10.04 LTS which is connected to a wifi home network. In my bedroom I have a data server running Ubuntu 10.04 LTS which is also connected to the same network and connected to a stereo with speakers across the room. Is it possible to play music on my laptop but, instead of playing it through the speakers of my laptop, transmit the audio stream over the network to the data server which plays the music on the big stereo?

If it is possible, how do I do it? :)

Thanks!

---

### Post by lidex on 2011-01-30
If you have pulseaudio installed on both, paprefs (pulseaudio preferences) should do the trick.
```
Alt+F2
paprefs
```
To install using terminal:
```
sudo apt-get install paprefs
```

---

### Post by MG2R on 2011-01-30
OK, have been fiddling with the settings and now, I have NO audio, at all... crap!

Help?

---

### Post by Afisamuleal on 2011-01-30
Hi,

Could you post a description of the actions you took, when the last time you know your sound worked was, and what you have changed since then?

Are you sure that the pulseaudio daemon is running?

[Here]("http://ubuntuforums.org/showthread.php?t=1572854") is a thread which may or may not be related.

---

### Post by MG2R on 2011-01-31
Well, I have actually no idea of what I have done. It something to do with creating an RTP sender on the laptop and an RTP receiver on the server. I remember I clicked the 'create seperate device for RTP'-box and then switched in the non-pulseaudio volume control thingy the output from my speakers to the RTP device... This (logically) killed my audio on the laptop and I could see an audio signal going through the RTP channel in the pulseaudio volume control, output devices tab. However, nothing came through at the server side...

Now, I've kinda unchecked every check box I found and my audio is up and running again on my laptop.

I want to be able to simply switch the output device from local speakers to server speakers on my laptop... 
Any thoughts?

---

