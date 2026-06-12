---
title: "How to get 5.1 surround over hdmi with GTX560ti"
date: 2011-04-03
forum: Multimedia Software
---

### Post by MasterZ on 2011-04-03
Hi, 

I'm trying to configure 5.1 surround sound on my new HTPC. 
I have an Nvidia GTX560ti and I managed to configure Stereo over HDMI through the following HOWTO (I've written it;) )
[http://ubuntuforums.org/showthread.php?t=1720294](http://ubuntuforums.org/showthread.php?t=1720294)

Now I want to go 1 step further and configure 5.1 surround sound. 

What I tried to do simply is to edit /etc/pulse/daemon.conf
and I added this at the end of the file:
```
default-sample-channels = 6
```

I did not make any additional configuration, no .asoundrc or whatever. 
The result is that it does work; I have sound coming out of my 6 speakers, and the output of:
```
speaker-test -D plughw:1,7 -c6 
```
gives the expected results and each speaker is triggered correctly according to the output of the command (front, center, right, rear-right, rear-left, lfe) 

The problem is that in every application that I tried (VLC and XBMC) when I play a 5.1 encoded DVD I'm getting the channels mixed-up. 
Center channel is output from the rear-left speaker, and others are also mixed up, but it's difficult to say which is where...

Do you know how I could maybe remap the channels correctly ? 
And could someone explain why the output is correct with the spaker-test command and not in other applications? 

Thanx,
Masterz

---

### Post by MasterZ on 2011-04-21
Ok, After some research (well 2 weeks...) I finally managed to do this. 

At first I thought Alsa was the issue but then I read a lot on the subject and I found out that the command:
```
speaker-test -D plughw:1,7 -c6
```
did indeed produce correct results, but this command:
```
speaker-test -D default -c6
```
would output my channels mixed-up.

So going through pulseaudio seemed to produce the error... 

I found-out this [guide]("http://ubuntuforums.org/showthread.php?t=795525") (outdated since 2009, but I still had a look) and I managed to remap my channels by editing /etc/pulse/default.pa and replacing this line: 
```
load-module module-alsa-sink device=hw:1,7 
```
by this line:
```
load-module module-alsa-sink device=hw:1,7 channel_map=front-left,front-right,rear-left,rear-right,front-center,lfe
```
(I had to play around swapping the channels to get it right)

Now, output through the default device works fine and every channel is where it should be. 


That was hard, 
MasterZ.

---

### Post by MasterZ on 2011-04-21
Now I have another question: 
If I'd like to switch from analog 5.1 output to bitstreaming the audio and letting my receiver do the Dolby decoding, what steps should I follow ? 

Thanx,
MasterZ

---

