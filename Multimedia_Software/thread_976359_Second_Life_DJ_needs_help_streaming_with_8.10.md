---
title: "Second Life DJ needs help streaming with 8.10"
date: 2008-11-09
forum: Multimedia Software
---

### Post by rhosigma on 2008-11-09
I am a DJ in second Life. While using windows I streamed to a shoutcast server using Sam Broadcaster. I am now using ubuntu 8.10 and would love to find a simple program to do the same thing. The only thing I have gotten to work was winamp with wine, this is working but I would like something that will run more native. I have tried exaile but cant get the icecast/shoutcast plugin to work. I am NOT using my PC as a server. All I need to do is put in the shoutcast server I stream to, load my play list and stream, seems simple, but I have never successfully gotten it to work, I have tried amarok, VLC, exaile, etc. Does anyone stream to a shoutcast server easily through a GUI application? I’m new to Linux and don’t know much as far as the terminal goes....again I would love to just open an application, have my playlist, enter the server I want to stream to and press play. Anyone help with step-by-step directions?? I would greatly appreciate it
Thank You

---

### Post by Naiki Muliaina on 2008-12-07
I would like to know this awnser to this too. IDJC just doesnt work for me. Ive had problem after problem that ive managed to work through, but it doesnt seem to work even when everythings been followed to a T.

---

### Post by polki@mac.com on 2008-12-09
Would MuSE work for you?

Description I found:

MuSE Streamer description
	 
MuSE is a user-friendly tool for network audio streaming.

MuSE is a user-friendly tool for network audio streaming.

MuSE provides the free software community with a user friendly but powerful tool for network audio streaming, making life easier for indypendent free speech online radios.

MuSE is an application for the mixing, encoding, and network streaming of sound: it can mix up to 6 encoded audio bitstreams (from files or network, mp3 or ogg) plus a souncard input signal, the resulting stream can be played locally on the sound card and/or encoded at different bitrates, recorded to harddisk and/or streamed to the net.

When sent to a server, the resulting audio can be listened thru the net by a vast number of players available on different operating systems.

To be operated MuSE offers graphical interfaces and a documented commandline interface in the good old unix style.

Here are some key features of "MuSE Streamer":

· Mixes up to 6 channels + 1 soundcard input channel simultaniously
· decodes and mixes both ogg and mp3, from files or network streams
· encodes at different bitrates and sends multiple mp3 or ogg streams to icecast, shoutcast and darwin servers.
· offers two different intuitive user interfaces and a documented command line interface
· play, stop, pause/resume, position and volume for each channel, looping thru playlists and reconnecting automatically to lost server connections
· efficient multithreaded architecture with emphasys on performance to support older CPUs
· reusable API interface to the core mixing engine permits to adapt new interfaces

Requirements:

· libogg 1.0
· LAME 3.93.1
· GTK+
· Ncurses

Stream servers supported:

· Litestream lightweight and efficient mp3 streaming server
· Icecast mp3 and ogg streaming server
· Darwin Streaming Server with Icecast emulation
· Shoutcast mp3 streaming technology

---

### Post by Naiki Muliaina on 2009-01-31
Intresting proggy, ive been running the main SC program to broadcast shoutcast recently (see sig). Ill give MuSE a go :) Thanks for the link Polki

---

### Post by markbuntu on 2009-02-01
djplay is designed for dj streaming.

---

### Post by Naiki Muliaina on 2009-02-02
It uses JACK, thats what gave me so much problems with IDJC ^^

---

### Post by markbuntu on 2009-02-02
I saw something somewhere about a network dj app that uses pulseaudio but I can't remember its name. It definitely was not in the ubuntu repos through.

---

### Post by wolfear on 2009-02-17
I'm at wits end on this too. I'm having to dual boot XP just so I can DJ in SL.
I'm using SAM for the moment.

I use OSS and trying to get IDJC is no go. Last time I tried getting it set up all the **** of getting Jack to work borked the rest of my system.
When I finally did get it working, I lost all sound in other parts of my system, including SL.

Tried Winamp thru Wine also, but couldn't stand it.

Hopefully someone, somewhere has an idea.

---

### Post by Naiki Muliaina on 2009-02-18
Read the guide linked to in my sig. No setting up or anything. Download it, fill in the blanks on the conf file (IP, Port, ETC), make a play list and your away.

---

### Post by wolfear on 2009-02-19
> **Naiki Muliaina said:**
> Read the guide linked to in my sig. No setting up or anything. Download it, fill in the blanks on the conf file (IP, Port, ETC), make a play list and your away.

Interesting. But not useful for me. I have to be able to DJ, which means taking requests, talking to the venue, shuffling songs according to the crowd, etc.
This just seems to play a pre-prepared list.

---

### Post by Naiki Muliaina on 2009-02-20
The playlist / conf file can be changed while its playing. Then you can simply kill and restart the trans file. Little bit to much for some :) 

My next project will be making an attempt at getting the VLC streamer working. Wish me luck ^^

---

### Post by subaruwrc01 on 2009-02-24
Hate to change the subject, but I was wondering what version of Second Life you are using, what version of Ubuntu you are using, and what video driver you are using?

I've tried using the SL viewer found on the SL site, but it doesn't run well.

---

### Post by wolfear on 2009-02-26
> **subaruwrc01 said:**
> Hate to change the subject, but I was wondering what version of Second Life you are using, what version of Ubuntu you are using, and what video driver you are using?

I've tried using the SL viewer found on the SL site, but it doesn't run well.

I have several veiwers available on my system including the current default release, the Hippo Viewer (for OSGrid), and the Cool Viewer.
My preference is the current 1.21.6 stable version of the [Cool Viewer]("http://sldev.free.fr/")

I just got the 1.22.9 Cool Viewer (experimental) but haven't had time to check it out yet.

Video is an ATI HD2600XT using the restricted drivers.

If you are having problems with the current viewer release, there is a 1.19 version of the Cool Viewer which is less resource intensive.

---

### Post by wolfear on 2009-02-26
> **Naiki Muliaina said:**
> The playlist / conf file can be changed while its playing. Then you can simply kill and restart the trans file. Little bit to much for some :) 

My next project will be making an attempt at getting the VLC streamer working. Wish me luck ^^

True. It's doable, but not practical in a busy environment.
This probably isn't practical either but I finally solved my issue by using a old, spare box I had sitting here.

I did a 8.04 server install and then installed the icecast2 server (mainly because I'm cheap and didn't want to pay for shoutcast in SL anymore) and proftp.

Then I threw Openbox on it and used Synaptic to install idjc and the required sound components.

As an aside, I also now have my OpemSim Server running on the same box and connected to OSGrid.

I've been DJ'ing in SL without issue for the past several days.

Main hassle is I only have 1 headset so I have to plug it into the server box when I DJ and plug speakers into my main box so I can hear SL.

I have no idea why idjc caused such an issue on my main box unless it was because I run OSS instead of PulseAudio.

---

### Post by Naiki Muliaina on 2009-02-26
Im using the Second Life OMVViewer [**_(click here to see repo guide)_**]("http://naiux.wordpress.com/2008/11/30/cracking-news-on-second-life-front/")

I dont think its so much IDJC thats the problem. I think its JACK. Ive tried a few another couple of DJ programs on Linux, but every time i install JACK i just have epic nightmares! I truly hate that piece of software.

---

### Post by subaruwrc01 on 2009-02-28
I installed Cool Viewer, and it wasn't wanting to work very well at all.

I installed OMViewer and have no complaints, but I cannot get Voice chat to work.

---

### Post by subaruwrc01 on 2009-03-06
Bump

---

### Post by Naiki Muliaina on 2009-03-07
Try asking in the games area. Most folk hang about in forum areas they know about ^^

---

### Post by wolfear on 2009-03-10
> **Naiki Muliaina said:**
> Im using the Second Life OMVViewer [**_(click here to see repo guide)_**]("http://naiux.wordpress.com/2008/11/30/cracking-news-on-second-life-front/")

I dont think its so much IDJC thats the problem. I think its JACK. Ive tried a few another couple of DJ programs on Linux, but every time i install JACK i just have epic nightmares! I truly hate that piece of software.

You could very well be right about JACK.
ON side note...i haven't heard of the OMVViewer before. Does it incorporate the bug & UI fixes like cool viewer does?
I'm open try it out so long as I don't have to use that horrendeous default UI like the standard viewer.

---

### Post by wolfear on 2009-03-10
> **subaruwrc01 said:**
> I installed Cool Viewer, and it wasn't wanting to work very well at all.

I installed OMViewer and have no complaints, but I cannot get Voice chat to work.

If you are running PulseAudio, you might be in for a fun time getting voice working.
Some people have no issues, other (like me) give it up and use a different sound system

---

### Post by johnh10000 on 2009-07-18
> **Naiki Muliaina said:**
> Read the guide linked to in my sig. No setting up or anything. Download it, fill in the blanks on the conf file (IP, Port, ETC), make a play list and your away.

don't sopose you know of one for icecast?

---

