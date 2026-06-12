---
title: "Audio is a problem in Ubuntu"
date: 2009-11-09
forum: Multimedia Software
---

### Post by urdrwho on 2009-11-09
Ok, I've been spending far too long playing around trying to get Ubuntu to stream online radio stations.  Sadly, it is a Windows world and I've never encountered such problems with Windows.

Load this codec and that codec, run scripts to get the stuff is not fun any more.  I'm trying to migrate to Ubuntu but if I can't listen to my talk radio shows...............Ubuntu "ain't gonna happen" for me.

I didn't think I would need to become a scripting expert to get the stuff to work.  I'm still not sure why I can't get this to work for me:

Install Mplayer and Multimedia Codecs (libdvdcss2,w32codecs,w64codecs) in Ubuntu 8.04 (Hardy Heron)

[http://www.ubuntugeek.com/install-mplayer-and-multimedia-codecs-libdvdcss2w32codecsw64codecs-in-ubuntu-804-hardy-heron.html](http://www.ubuntugeek.com/install-mplayer-and-multimedia-codecs-libdvdcss2w32codecsw64codecs-in-ubuntu-804-hardy-heron.html)

I'm using Ubuntu 9.10.

A bit PO'd and frustrated.

---

### Post by michy99 on 2009-11-09
Have you tried rhythmbox? Plays radio fine for me.

---

### Post by urdrwho on 2009-11-09
The stations I want to listen to are regular radio stations that stream their stuff over the net. I haven't tried rhythm box.

Just went here to get it and oh crap, it is a bin file.  Compile, make an exe and all that is something that is to new for me to worry about.  I don't get this open source community?  Am I missing it?  Is it just cool to send stuff that isn't immediately executable and I don't see the humor?

> **michy99 said:**
> Have you tried rhythmbox? Plays radio fine for me.

---

### Post by PaulInBHC on 2009-11-09
On my 9.10 install, Applications> Sound and Video> Rhythmbox is already installed.
I listen to KFI AM 640 Los Angeles online. They have their own player popup and it works fine in 9.10.

---

### Post by andrew.46 on 2009-11-10
Hi urdwho,

> **urdrwho said:**
> Load this codec and that codec, run scripts to get the stuff is not fun any more.  I'm trying to migrate to Ubuntu but if I can't listen to my talk radio shows...............Ubuntu "ain't gonna happen" for me.

I can appreciate your frustration. Could you give a few of these radio streams that are giving you trouble?

Andrew

---

### Post by VertexPusher on 2009-11-10
> **urdrwho said:**
> Just went here to get it and oh crap, it is a bin file.  Compile, make an exe and all that is something that is to new for me to worry about.  I don't get this open source community?  Am I missing it?  Is it just cool to send stuff that isn't immediately executable and I don't see the humor?
The humor is in the fact that you registered in April 2007 but still don't seem to know how to install compiled executables with the package manager. Rhythmbox comes preinstalled with Ubuntu, but even if it didn't, the package manager would be the first place to look for it.

---

### Post by urdrwho on 2009-11-10
I registered back then but never installed a Ubuntu OS.  It wasn't until the last week or so that I installed a Ubuntu.  So that should out the install compiled executables in the correct light for you.  Yes it would be humor if I've spent 3 years on an OS and not know how to do it but that isn't what took place.

And yes, I have Rhythmbox on my applications/sounds. 

Within the past week or so I did install/compile and executable.  It just isn't first hand nature yet. 

> **VertexPusher said:**
> The humor is in the fact that you registered in April 2007 but still don't seem to know how to install compiled executables with the package manager. Rhythmbox comes preinstalled with Ubuntu, but even if it didn't, the package manager would be the first place to look for it.

---

### Post by urdrwho on 2009-11-10
This is one of them:

[http://wbal.com/listen/player.asp](http://wbal.com/listen/player.asp)


This is another one of them:
[http://player.cumulusstreaming.com/Audioplay.html?WSBA-AM](http://player.cumulusstreaming.com/Audioplay.html?WSBA-AM)

The WBAL I can get to play if I remove Totem and a few others.  But I won't get a graphical that allows me to adjust volume levels, etc. I just get sound and I can see the url address.

The WSBA is Silver Light dependent but it has a basic player button.  Even in basic player I get no streams.

> **andrew.46 said:**
> Hi urdwho,



I can appreciate your frustration. Could you give a few of these radio streams that are giving you trouble?

Andrew

---

### Post by gradinaruvasile on 2009-11-10
Also there are VLC, Exaile, Audacious (to name a few) that can be installed easily and has support for streaming radio. I personally like Exaile.
The default movie player (totem) also has support for these.

Be aware of PulseAudio (may cause problems) though if using non default sound applications. Check if they have support for it.

---

### Post by urdrwho on 2009-11-10
When I tried the two stations on Rhythmbox, with WSBA it went looking for a plugin but never found one; the WBAL didn't even try to run, it just said, "Your GStreamer installation is missing a plug-in".  It didn't try to find a plugin or tell me which plugin is needed.

Sigh!?!?!?!?

The WBAL

> **PaulInBHC said:**
> On my 9.10 install, Applications> Sound and Video> Rhythmbox is already installed.
I listen to KFI AM 640 Los Angeles online. They have their own player popup and it works fine in 9.10.

---

### Post by gradinaruvasile on 2009-11-10
> **urdrwho said:**
> When I tried the two stations on Rhythmbox, with WSBA it went looking for a plugin but never found one; the WBAL didn't even try to run, it just said, "Your GStreamer installation is missing a plug-in".  It didn't try to find a plugin or tell me which plugin is needed.

Sigh!?!?!?!?

The WBAL

Well if WSBA is this one: [www.wsba910.com](www.wsba910.com), then you are out of luck because they have a silverlight (Microsoft Flash essentially) based player and silverlight doesnt work under Linux (Moonlight doesnt really work for anything).

---

### Post by urdrwho on 2009-11-10
I've gotten the WSBA to stream in Amarok.  I had to look at the webpage to strip out the exact URL.  This is the URL that will play: [Http://live.cumulusstreaming.com/WSBA-AM](Http://live.cumulusstreaming.com/WSBA-AM).  Now I can get my local news.

I tried to look and find the exact URL for the WBAL page but can't find it.

Amarok is streaming the audio but the sound is a bit jerky. 


> **gradinaruvasile said:**
> Also there are VLC, Exaile, Audacious (to name a few) that can be installed easily and has support for streaming radio. I personally like Exaile.
The default movie player (totem) also has support for these.

Be aware of PulseAudio (may cause problems) though if using non default sound applications. Check if they have support for it.

---

### Post by urdrwho on 2009-11-10
Actually this morning I did get WSBA to stream using this address:[http://live.cumulusstreaming.com/WSBA-AM](http://live.cumulusstreaming.com/WSBA-AM).  I've also done a lot of codec install and uninstall stuff.

WBAL will stream now but I get no interface - see attachment. 

> **gradinaruvasile said:**
> Well if WSBA is this one: [www.wsba910.com](www.wsba910.com), then you are out of luck because they have a silverlight (Microsoft Flash essentially) based player and silverlight doesnt work under Linux (Moonlight doesnt really work for anything).

---

### Post by PaulInBHC on 2009-11-10
The KFI player that I mentioned before would not work tonight. Short story, I closed Firefox and started over. That fixed it.

---

