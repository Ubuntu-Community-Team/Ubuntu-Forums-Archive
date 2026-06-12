---
title: "Audio Playback on remote host with ESD?"
date: 2006-08-23
forum: Multimedia &amp; Video
---

### Post by lodp on 2006-08-23
I'm running Kubuntu Dapper, and I'd like to have audio playback via the USB sound card attached to my router. I was wondering whether there's some sort of unified solution to get all sound output via that sound card.

My router runs the EsounD daemon.

Up to now, i've only got it to work with xmms (which sucks at video playback) and mplayer (but only on the commandline verision-- kmplayer lacks the esd remote host field and gmplayer just freezes upon playback when i set it to esd and enter a remote IP). This situation is totally unpleasant -- i'd rather use one single player with a decent GUI.

Also, i don't know how i would get the mplayer plugins for firefox to work with remote playback -- you can select esd output in the properties, but there's no field for a remote IP.

Is there some other way to get all sound via the remote host?

---

### Post by lodp on 2006-10-02
*bump*

---

### Post by lodp on 2006-12-07
alright, i pretty much got it figured out now... took quite a while, but i finally got there..if anybody is interested in having a more comprehensive guide on how to switch from crappy sound on laptop speakers to super-awesome sound from your stereo attached to your wireless usb-router, please let me know.

so here's the short version of my findings:

basically, you can get it to work with any application that has an Esound (esd) output plugin.

i use KMplayer with the mplayer engine for video, and amaroK for music playback. for the web, i have firefox's "MediaPlayerConnectivity" start the stand-alone kmplayer.

**KMplayer**


there's a field labeled "additional command line arguments" in Configure Kmplayer > General Options > Mplayer. i entered the following line there:

```
-ao esd:192.168.1.1
```

(you have to hit return before pressing the in order for the line to stay put, dunno why). restart. this will select esd output to the IP 192.168.1.1, which is my router, where the loudspeakers are attached with a USB audio card.


**amaroK**

start amaroK with the following line (in kubuntu, just edit the item in the start menu):

```
export ESPEAKER=192.168.1.1&&amarok %U

```

this does the same thing as the line in KMplayer, only i think it talks to esd directly, instead of informing the engine.

---

### Post by Chessmaster on 2008-02-26
Hi there,

> if anybody is interested in having a more comprehensive guide on how to switch from crappy sound on laptop speakers to super-awesome sound from your stereo attached to your wireless usb-router, please let me know

I would love to know how to do this! I have a ASUS wl-500g and a 3D USB audio adapter (which from the ASUS wl-500g forums are compatible). I can connect to the router wirelessly no problems and print wirelessly via the router as well. 

I have installed latest firmware on router but am not sure how to upload the EsounD daemon onto the router. I only have dial-up so the router is not connected to the net so I am not sure how I go about loading ESD onto the router. Any ideas? I can mount my USB stick on the router and access that directory via Putty but I have no idea how to load the EsounD binary from the USB etc.

A step-by-step guide would be fantastic if you are offering! 

Cheers. I look forward to hearing my replica Airport! :)

---

### Post by Chessmaster on 2008-02-27
Ok, 

so I got EsounD loaded (and running) from my USB stick onto the router in the /usr/local folder after following different instructions on the WL-500g forums . I also set XMMS to play audio to my routers IP 192.168.1.1. When I press play it connects to the router and sends a signal.

Problem is that all I get from the output of my USB audio card is a single pitch / tone. No music, just a constant single pitched note. 

Any ideas how to resolve this? As I say, I am getting output from the audio player to the router but no music. The single tone stops and starts when I play and stop the player so I know that the signal is getting through. 

Could this be a sampling rate problem? 

Any ideas?

Cheers

---

