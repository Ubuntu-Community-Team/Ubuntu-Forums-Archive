---
title: "MythTV Questions"
date: 2015-02-21
forum: Mythbuntu
---

### Post by nick168 on 2015-02-21
Hey guys,

I apologize this is technically in the wrong section, as I am running Ubuntu Server, not Mythbuntu. But I figured you guys would probably also know a lot about MythTV. So here's my question:

I have an Ubuntu Server (14.04.01 LTS) that I am currently using as a file share (Apache2) / download server (transmission). Now I want to add a TV Tuner to the server, and I want it to be able to stream live TV/my videos from a web browser. Yes, I understand how to setup MythTV backend and frontend so I can use a Windows application to stream, but I'd rather have it broadcast to a port on the server. Is this possible with MythTV? And if so, I have a couple more questions:

Let's say I am broadcasting ESPN or something via http and I'm looking at it on my web browser. Then my friend types in that port number on his browser, will he be watching the same thing I am watching? Or will it be possible for him to watch a channel, and me to watch a different channel? And my final question... regardless of whether or not the whole web browser thing is possible, what kind of tuner will be compatible with Ubuntu Server? I'm running it on a Dell Optiplex 755 (pretty old, uses DDR2), but I'm pretty sure it has a PCI-e (x1), PCI-e (x16) and two PCI slots. I see cards ranging from like $20 - $200... so I'm completely lost in that aspect.

Thanks,
Nick T

---

### Post by TheFu on 2015-02-22
I don't use Myth.

Tuner support really comes down to how you need to get the TV signal for your location.  There are 3 main ways
* CATV (encrypted QAM or Clear-QAM?)
* Satellite
* OTA ATSC

I would strongly suggest NOT using an internal tuner at all. Get a network tuner. Ceton and Hauppauge have great options for CATV and OTA.  Cannot talk about encrypted QAM myself. I thought that required Windows Media Center to work, thanks to DRM, but I've heard rumors that people have gotten the Ceton to work.

The modern Hauppauge network tuners are DLNA servers, so any DLNA client should be able to connect on the LAN and watch a channel, provided there is an available tuner with access to the desired channel.

---

### Post by nick168 on 2015-02-22
So you're saying, as long as I have a compatible tuner card, I should be able to install any DLNA client on the Ubuntu Server? How would this be available to watch on the Windows side of things? Using a browser or would I have to settle for Windows Media Player?

And also, I have no idea what my TV signal is... I live in a dorm, and I would use a coax straight from the wall to the tuner. I don't currently have a TV so I can't check the model number of that TV or anything. I thought it was ATSC, but you didn't mention that one so I'm not sure anymore.

---

### Post by TheFu on 2015-02-22
> **nick168 said:**
> So you're saying, as long as I have a compatible tuner card, I should be able to install any DLNA client on the Ubuntu Server? How would this be available to watch on the Windows side of things? Using a browser or would I have to settle for Windows Media Player?

And also, I have no idea what my TV signal is... I live in a dorm, and I would use a coax straight from the wall to the tuner. I don't currently have a TV so I can't check the model number of that TV or anything. I thought it was ATSC, but you didn't mention that one so I'm not sure anymore.

What I'm saying is if you get a networked tuner that provides a DLNA server then **any** DLNA client can connect and use it on the network.  SmartTV, Bluray player, android phone/tablet, Windows, OSX or Linux PCs. No "server PC" needed.  That is handy for live TV viewing - recording TV is different and that is where having a Myth backend comes in.

**You need to know the signal type and whether it is encrypted or not before doing anything else.** ESPN is generally a cableTV thing, and where I live, all cable TV is encrypted. It wasn't always. Slowly, Comcast encrypted more and more channels until my media center became worthless, so I cut that TV cord and switched to antennas for TV reception. The sports I care about are NOT on ESPN or any TV channels offered by cable here. Live Sports and Food Shows are the primary reasons to keep cableTV here. Movies, TV series, etc. can be gotten easier, without commercials, for less money with online subscriptions than CATV.

[http://www.mythtv.org/wiki/Recording_Digital_Cable](http://www.mythtv.org/wiki/Recording_Digital_Cable) - covers it well.
I have (2) HDHR3s here to record OTA ATSC using antennas in the attic. This model does not support DLNA at all - the HDHR4 does, but if you need CableCARD support, then the 3-tuner *HD Homerun Prime* is what you want (or something similar). Be certain to carefully read that link.

If the signal is analog ... I can't help. 2009 was the last analog here.

---

### Post by nick168 on 2015-02-24
Okay, this is a lot of great info. I'll look into it tomorrow when I'm not sleep-deprived. Let you know if I have any more questions.

Thanks for everything!

---

