---
title: "Some noob questions about mythbuntu"
date: 2009-03-03
forum: Mythbuntu
---

### Post by Daremo_06 on 2009-03-03
I am fairly new to Ubuntu and Linux in general, and have been working on setting up a desktop system with Ubuntu.  While showing the Ubuntu site to a co-worker, I noticed Mythbuntu.  

So I am very interested as one of the projects I had on the back burner was a total home entertainment system controlled by a PC.

So I am curious what the recommended hardware platform is for Mythbuntu?  Also whats the recommended video card?  I have been struggling with a ATI 9250 dual screen setup for my standard Ubuntu, so I have learned about the problem with some video drivers no longer being supported.

Thanks!

---

### Post by perspectoff on 2009-03-03
To be perfectly honest, I don't see the advantage of Mythbuntu. I installed it last month, but it was inferior to installing Kubuntu and then using the MythTV package by itself.

I personally have used LinuxMCE for some time, because it has home automation, VOIP (PBX phone system) and other functions built in, in addition to multimedia. It is an incredible system, but takes a lot of tinkering.

LinuxMCE also is best with specific hardware. It is for the "real" enthusiast.

Myth TV is probably best for the new multimedia inductee.

There are several alternatives listed at

Kubuntu guide ([http://kubuntuguide.org](http://kubuntuguide.org))

and

Ubuntu guide ([http://ubuntuguide.org](http://ubuntuguide.org))


I have to ask:

Why don't you just use a network drive to store videos and audio, then use a multimedia player (like VLC or MPlayer) and an audio jukebox (like Amarok) to view your videos and listen to your audio over your home network? 

It is easier than using MythTV or any other "multimedia" solution and is a lot less hassle. 

Watching TV online isn't all that easy with Myth TV, either, and TV content is most easily viewable through web browsers, these days (like Hulu, for example), anyway.

In the final analysis, MythTV and all the others are merely "window dressing" and don't add anything to functionality and to me are huge time sinks. To be honest, I have stopped using them. (I only like LinuxMCE for the home automation, really).

---

### Post by nickrout on 2009-03-03
yes if you are not recording broadcast TV then myth is underutilised as a multimedia box. I'd be going for xbmc from what i have seen of it.

But if you want to record TV its the bees knees and very flexible too.

Recommended hardware depends on what media you want to play. Almost any computer will play SD. It takes grunt to play HD. It takes hard drive space to store it.

Also depends a lot on what you are playing into (does your screen, be it projector, TV, monitor etc) have hdmi inputs? DVI? VGA? s-video? composite? 

Do you have a 5.1 or greater sound system and want your videos and dvd's playing in all their surround sound glory?

Lastly in terms of video card you probably want an nVidia card that will do vdpau. Its a new technology which enables a lot of work usually done by the CPU to be done on the video card. It produces fantastic results in terms of lowering cpu usage and increasing video quality. The mythtv wiki has info on what cards are supported, and indeed on what hardware is good.

---

### Post by scary_jeff on 2009-03-03
That's a bit of a harsh review!

If you are just trying to watch TV and play audio from your desktop PC, which you also use for all your office apps, emails, etc, then yes, there's probably not much point in using mythtv.

However, if you want a genuine 'appliance' type device, which connects to your TV, mythtv is fantastic. It does take effort to make everything work how you want it, but in the end you have a slick interface for doing any media-centric tasks you choose.
This is especially true if you are using an infra red or other remote control; using separate apps for each function is possible, but extremely clunky compared to using mythtv, where everything is in one consistent interface.

As nickrout says, for anything relating to watching and recording broadcast TV, myth is really excellent.

If you are getting a brand new system, I would also recommend an nVidia graphics card, one that supports VDPAU as nickrout said. If you want to get started with some hardware you have lying around and just add a TV tuner, the minimum requirements are pretty low. There's more information in the mythtv wiki.

As for mythbuntu or ubuntu+mythtv, the advantage of mythbunutu is that all the plugins are installed for you, and all being well, it should be easier to set up. It also uses less RAM, although this won't be much of an issue if you are buying new hardware. On the other hand, ubuntu+mythtv gives you a full ubuntu desktop to use (you can install ubuntu desktop with mythbuntu, but I had problems with that).

---

### Post by newlinux on 2009-03-03
+1 for XBMC if you are not going to doing TV show watching and recording. I run both Myth and XBMC (XBMC when I want to showoff with the Aeon skin). After the tweaking... I use myth everyday on multiple TVs in my house... It has been completely worth it for me. 

to the average user it is just like using the DVD player or cable box. It is controlled by the rekote and others in my household with no knowledge of the system use it just fine too... It's good "glue" for all your multimedia needs.

---

### Post by Daremo_06 on 2009-03-03
Alright I guess i need to be slightly more specific.

1.  I was envisioning a core system that ran my home systems, so that would be itunes (or equiv), something for dvd playback (right now just have a standard tv, no plasma or flatscreen yet, SVGA would be what it would take).  I dont have a surround sound system yet, could you build one using a PC and an amp? or do you need the specialized outputs of surround sound reciever?  And ideally I would like to run it via IR remote AND touchscreen ( i have a couple laying around at work not doing anything productive :D ).

2.  New hardware will be at a min, mostly recycled stuff, I figure the main expense is going to be the video board anyways, everything else I have is your standard 2-3GH dual core intel ect ect.  So I guess I would want a fairly advanced video card, and with that a powersupply with enough wattage for it...

Any suggestions on preferred vendors?  I am thinking nVida or GForce card of some sort...  

Thanks!

---

### Post by Caps18 on 2009-03-03
For audio throughout my house, I have a mac and the remote app on my ipod touch.  By using the wifi network, I can control it from anywhere.

For TV (digital over-the-air), which accounts for 95% of what I watch, the $20 year price with Mythbuntu/Schedules Direct is the absolute best way to go.  I have my one Mythbuntu box hooked up to two LCD screens and one projector.  There is one remote to use to control it(actually I have two of the same remotes).

It was fairly easy to setup, and it has organized my video/movie collection as well.

---

