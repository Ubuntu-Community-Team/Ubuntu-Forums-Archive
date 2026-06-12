---
title: "Stream video (only) from PC on TV over LAN and PC-sound on speakers"
date: 2015-11-04
forum: Multimedia Software
---

### Post by adrhc on 2015-11-04
Hi, I would like to know if it's possible (and how) to stream/render-somehow a movie from PC on a TV over LAN while the movie also is running on the PC. 

My ultimate goal is in fact to render the movie on TV (with or without sound) while playing the sound on my 5.1 speakers from my PC.
if the PC is also playing the movie is not an issue for me.
It the TV receive also the sound stream it's no issue for me because I have means to disable it on TV.

I could try to start the movie on PC and TV simultaneously and I'd achieve the result desired but it's difficult to do that perfectly - usually I get a delay of about 0.1s - 1s between players.

I talk about streaming but this is only a possible solution; if other exists then it's welcome.

Any idea ?

PS: the solution must not include buying new hardware/appliances/devices though I would accept buying new wires of any kind if required
PS: I can't output sound to speaker directly from my TV (TV has optical output while speakers only have RCA connectors)
PS: I have Genius 5.1 2002 year model speakers
PS: for me (tried with Samsung 32H5500 smart TV and Samsung LE37C650L1WXXH) doesn't work [this]("http://realmike.org/blog/2015/05/27/wip-mirror-your-linux-desktop-to-your-tv/")

---

### Post by blm-ubunet on 2015-11-05
The close source implementations of this idea are:
chromecast, Airplay
With iApple/Airplay you can choice the audio & video renderer devices (separately).

DLNA
Many modern TVs can act as DLNA clients where you browse a server from the client & control playback from client.
But many modern TVs also support being DLNA media renderers. The difference being the control point is not the renderer (TV). Some LAN connected AVR/HT-amps act as media renderers.
There is an audio chromecast device to allow this on old amps..
AFAIK Kodi supports being a media renderer.

Control point s/w:
Close source of course.
FOSS is thin on the ground; gupnp-av-cp gupnp-universal-cp might work for you.
BubbleUPnP (android closed source) is commonly recommended.

The DLNA server side is no problem.

---

### Post by SeijiSensei on 2015-11-05
I've used DLNA to stream movies from an Ubuntu machine running minidlna to both TVs and phones with DLNA support.  However to have them display on both devices requires some form of screen mirroring software I believe.  If you don't need to display the material on both the PC and the TV at the same time, and your TV supports the DLNA protocol, then download minidlna from the repositories and give that a try.  It's pretty trivial to configure.  You just add an entry to minidlna.conf like this:
```
media_dir=V,/media/yourarchive
```
and it will make the contents of the /media/yourarchive available to any devices on the same network subnet.  The "V" tells the client the contents of that directory are videos.  You can have multiple entries with "P" for pictures and "A" for audio as well.

Your TV will need to have support for any codecs and containers the content is stored with.  Modern TVs can handle H.264 encodes in MP4 and nowadays often in the Matroska (.mkv) container as well.  (Sony has been less willing to support open standards like Matroska because they see it as a medium that pirates use.  My LG TV has no such restrictions.)  If your TV only supports a limited number of formats, there is software that can do on-the-fly transcoding.  The makers of BubbleUPNP for Android now offer such a [server]("http://www.bubblesoftapps.com/bubbleupnpserver/"), and it runs on many different platforms including Linux.  [PS3mediaserver]("http://www.ps3mediaserver.org/") is another option.

---

### Post by blm-ubunet on 2015-11-06
The OP wasn't requiring video on PC & TV simultaneously. Quite the opposite.

There a loads of DLNA server solutions but that is only one part of a system & the easiest to solve.

What I suggested was using a DLNA control point (gupnp-av-cp etc).
Using the laptop/tablet as the DLNA media "control point" to push to a media renderer device (AVR, TV, PC) from any server (local file, NAS, PC).

I believe BubbleUPNP "control point" app can push audio & video to different renderers (just like Airplay) but this is prob. the non-free version.

---

### Post by adrhc on 2015-11-06
@SeijiSensei
Thanks, but how your solution would help me to render PC-to-speakers synchronously with playing the dlna-movie ? (I already have a DLNA server on my PC).

@blm-ubunet
Thanks, but I'm not sure I understand you; based on what I understand please see below my comments.
I can't use iApple/Airplay or BubbleUPnP because I want to "send" (streaming or else - it doesn't matter for me) sound and video from my PC directly to TV & speakers. Airplay and BubbleUPnP seems to work only on mobile devices but not on PC.
gupnp-av-cp and gupnp-universal-cp seems to be related to GUPnP and helps to build an UPnP device which I don't intend to do.
FOSS - I can't find what this is.

PS: I added some new information to the initial post just for clarification

---

### Post by SeijiSensei on 2015-11-06
My TV is connected directly to my audio system via HDMI to my [receiver](https://www.amazon.com/gp/aw/d/B007JF8FD8/). The receiver is also connected to a PC via HDMI. Usually I just play content stored on the computer through the receiver so the video appears on the TV, and the audio is sent to the speakers. (The machine connected to the TV also runs the DLNA server to stream to other locations and devices.) Is an arrangement like that not an option for you?

"FOSS" is an acronym for "free and open-source software." It's not an application.

---

### Post by adrhc on 2015-11-06
Thanks, but indeed it's not an option for me though it would work.
I don't want to have an additional device (especially when it comes to a big one) besides the PC, TV and speakers.

PS: for me something bigger than a 300ml glass is something too big :)

---

### Post by blm-ubunet on 2015-11-06
DLNA is a consumer electronics group that tries to make sure their own products will not work with anyone else..
AIUI It uses UPnP protocol.
Airplay & Chromecast are "closed system" implementations of what you want to do. Just examples that's all. You can't use them without buying some of their hardware.
At least Chromecast & audiocast devices are cheap & seem to be well supported (so far). These devices will be very useful when SmartTVs stop being smart which will only be in a few years.

BubbleUpnp as a "control point" seems to be available on mobile devices. That's how most people want it to work & they need to generate a revenue stream.
Others inc. Kinsky, ToasterCast, Flipps, Gizmoot (all Android?)

Try install "gupnp-av-cp" & see if it finds your TV as a media renderer.. try to send a media file & stop/play/pause it..
The program is in the std repositories & it's free.
```
sudo apt-get install gupnp-tools
gupnp-av-cp
```

Finding a control point that can make the server route the audio & video to separate media renderers is going to be much more difficult.

**In the past** you have been able to do this with Airplay (control point) on Apple h/w to MythTV/Kodi (media renderers) on PCs. And Kodi will run on a lot of different h/w including  SmartTVs.

---

