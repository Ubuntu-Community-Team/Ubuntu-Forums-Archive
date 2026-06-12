---
title: "How to setup ubuntu server as an UPnP media renderer?"
date: 2010-07-27
forum: Multimedia Software
---

### Post by justnoise on 2010-07-27
Hi,

I have been trying to find something that does this for some time now and discussions on IRC didn't turn up anything usefull - thats why this post for a prolonged discussion ;-)

I have Ubuntu Server 10.4 installed (no X) and am trying to use it as an upnp media renderer. I would like to be able to playback their music on the servers soundcard from various devices. Thus it would be nice to have the ubuntu server expose an upnp media-renderer which one can use as an output device.

Is there a suggestion on which software to use?

What I already have working is an upnp media-server (mediatomb) with ampache, but this isn't really what I'd like since I don't have as much disk-space on the server as I have on the various computers.

Thank you very much!

---

### Post by justnoise on 2010-08-10
How can I improve this question?

---

### Post by phr0ze on 2010-08-16
> **justnoise said:**
> How can I improve this question?

I'm not sure what you are actually trying to do because I don't know where a sound card comes into play on the server side. 

But why not mount the other media sources on the server (shared folders) then publish them via media tomb?

It works fine and is great if the server itself doesn't have the storage.

---

### Post by justnoise on 2010-08-20
Late reply, sorry didn't expect anyone to answer anymore - so thank you for your input :-)


What I am trying to do is:
* start rythmbox on remote ubuntu
* select music-files on remote ubuntu
* select server in kitchen as playback device
* listen to music in kitchen

The same thing should be working with a windows xp-7 machine as well.

Also I would like to use any machine to "intercept" the music being played by another machine :-)


Is that clear enough? I hope so :-(


As for MediaTomb: as you mentioned - the files have to be available somehow, through mounting a remote device is a good idea. However it doesn't solve the control problem, right now I am using ampache, but it would be much cooler if they could just use their local player to skip a song.

Thank you again for helping.

---

### Post by putt1ck on 2010-08-25
Hi

I think XBMC answers your needs, and I understand next release of Amarok will also act as a full-featured UPnP Renderer. 

I tried a bunch of ways to get a remote controllable Renderer and nothing worked until XBMC.

Do 

sudo add-apt-repository ppa:team-xbmc/ppa 

(note that the above adds unofficial K/Ubuntu software sources)

sudo apt-get update

sudo apt-get install xbmc

Can be run (effectively) headless also if you're using a hidden box (e.g. mini-ITX fanless PC) attached to an external DAC. See [http://forum.xbmc.org/showthread.php?t=41138](http://forum.xbmc.org/showthread.php?t=41138) for more on that.

Appeared instantly in the Cidero Controller, so should appear in others.

---

