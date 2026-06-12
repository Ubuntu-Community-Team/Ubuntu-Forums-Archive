---
title: "Stream sound over network"
date: 2010-11-23
forum: Multimedia Software
---

### Post by VanJoe on 2010-11-23
here's my situation. I have a Internet radio box that can play audio streams if given the correct url or ip address and on the same router I have my computer. I want to stream my audio out onto the local network from this computer. In other words ideally I would have a virtual sound card that instead of outputting it to speakers put it online. I think pulseaudio is capable of this, I am just not sure how.  I know that I can use vlc for some things, but I would simple solution for all my audio. any ideas?

---

### Post by VanJoe on 2010-11-23
bump

---

### Post by xc3RnbFO8P on 2010-11-23
> **VanJoe said:**
> here's my situation. I have a Internet radio box that can play audio streams if given the correct url or ip address and on the same router I have my computer. I want to stream my audio out onto the local network from this computer. In other words ideally I would have a virtual sound card that instead of outputting it to speakers put it online. I think pulseaudio is capable of this, I am just not sure how.  I know that I can use vlc for some things, but I would simple solution for all my audio. any ideas?

If you know the url, you can use VLC.
Media> Streaming> Network (add url) click stream button
(next)
Choose HTTP then Add (IP Address)
To get your computer Address, right click on the network icon in panel "Connection Information" on top copy the IP Address
Paste in Address and just use the 8080  Port.
(Check) Activate Transcoding 
choose Audio mp3  (next)
(stream)

On your Client PC, open up VLC and select Open Network Stream
or Movie Player>  Open Location
write your IP Address 192.168.?.???:8080

---

### Post by VanJoe on 2010-11-23
Vlc only works for single files i would like a solution that pipes all of my audio to a stream

---

### Post by atlanta800 on 2010-11-24
I spent all day figuring this out and finally got it working. The solution is a combination of the pulseaudio monitor interface with Icecast2 and Darkice.

Note: These instructions are for Ubuntu 10.10 Maverick Meerkat. It may work on other versions, but no promises.

First you need to get pavucontrol ("PulseAudio Volume Control". It's in the repos). Fire it up, go over to "Input Devices". In the drop down menu on the bottom right select "Monitors". Now you will see (depending on your hardware) something along the lines of "Monitor of Internal Audio Analog Stereo". Ensure that this is NOT muted (mine was by default) and turn the volume on it all the way up. If you are playing audio, you should see the bar below volume control moving with the audio you're playing. Also, it may be a good idea to make sure that "Set as fallback" is selected. Now Pulseaudio should be configured correctly.

From here you need to install icecast2 and darkice (both in the repos). Setup is fairly straightforward, use Google and the man pages if you can't figure it out. The important thing to do is make sure you have
```
...
device = default
...
```
in your darkice.cfg. Now you can connect any computer to your icecast server and you should hear every sound that is generated from your computer (literally everything: system sounds, youtube videos, audio players, you get the idea).

If you've connected to your icecast server and still don't hear anything ensure a few things:
[LIST]
[*]the audio on your "server" system isn't muted (this will also mute the monitor device)
[*]your darkice.cfg is configured properly (device = default worked perfect for me)
[*]if you still hear no sound, load up pavucontrol again, go to the "Recording" tab and ensure that you see "Alsa plug-in [darkice]" and that it is ALSA Capture from "Monitor of..." where ... is your output device and that the bar below it is moving with your audio output.
[/LIST]

Good luck and enjoy. If you're still having troubles, let me know and I can write up some more detailed instructions.

---

### Post by rgoatcabin on 2011-05-22
Thanks very much for the instructions, I've been trying to get something like this to work for a long time.

I'm using 10.04, trying to stream the audio from my laptop to a desktop, which is hooked up to my stereo.  

I followed your instructions through installing darkice and icecast2.  But I don't know how to configure them.  Can you give more info on how to configure/set them up.  I'm also unclear as to what those programs do, exactly. Does one provide the audio stream and the other sends it over the network?  

I had set up pulseaudio at one point, which did send my audio over the network.  But the sound coming out of the client desktop would speed up and slow down and change pitch, like a record spinning at a constantly changing speed.  

Thanks!

---

### Post by nothingspecial on 2011-05-23
> **VanJoe said:**
> Vlc only works for single files i would like a solution that pipes all of my audio to a stream

vlc will stream a playlist. Used in conjunction with fapg you can start a stream easily. For example if you want to stream an album, where all the songs are in one directory, cd to that directory and do something like this

```
fapg --format=m3u --output=./playlist.m3u . && cvlc playlist.m3u --sout '#standard{access=http,mux=ogg,dst=192.168.1.10:8080}'
```

Then in your player put ```
http://192.168.1.10:8080
```

Change the ip address for the ip address of the computer that is doing the streaming........

......and alias it because you don't want to have to type that lot out every time (let alone remember it). You should be able to modify that to your needs. 

If you want to skip tracks and stuff you'll have to use the gui vlc, because afaik cvlv doesn't support keybindings.

---

### Post by haiku88 on 2012-02-24
a very old thread but after failing to get  VLC streaming working on my own I found a solution someone else posted on another forum a ways down this page...works great and VLC streams all system audio as 320kbs MP3

[http://forums.slimdevices.com/showthread.php?t=49584&page=16]("http://forums.slimdevices.com/showthread.php?t=49584&page=16")

---

### Post by aeiah on 2012-02-24
i just use mpd and set it to output to http

---

