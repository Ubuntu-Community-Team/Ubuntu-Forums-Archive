---
title: "Realplayer Firefox plugin issues"
date: 2006-11-20
forum: Multimedia &amp; Video
---

### Post by WebDrake on 2006-11-20
Hello all,

I'm having problems getting real media streams to play in Firefox.

If I go (for example) to the BBC site and try to listen on their "radio player", I get an error message:

**Totem could not play 'rtsp://rmlive.bbc.co.uk/bbc-rbs/rmlive/ev7/live24/radio3/live/r3_dsat_g2.ra'.**

Realplayer was installed via Automatix, and the nphelix.so and .xpt files are present in the /usr/lib/firefox/plugins directory.

The relevant entries in about:plugins appear to be,

Helix DNA Plugin: RealPlayer G2 Plug-In Compatible (compatible; Totem)

    File name: libtotem-complex-plugin.so
    The Totem 2.16.2 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
audio/x-pn-realaudio-plugin 	RealAudio document 	rpm 	Yes

RealPlayer 9

    File name: mplayerplug-in-rm.so
    mplayerplug-in 3.31

    Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer
    JavaScript Enabled and Using GTK2 Widgets

MIME Type 	Description 	Suffixes 	Enabled
audio/x-pn-realaudio 	RealAudio 	ram,rm 	Yes
application/vnd.rn-realmedia 	RealMedia 	rm 	Yes
application/vnd.rn-realaudio 	RealAudio 	ra,ram 	Yes
video/vnd.rn-realvideo 	RealVideo 	rv 	Yes
audio/x-realaudio 	RealAudio 	ra 	Yes
audio/x-pn-realaudio-plugin 	RealAudio 	rpm 	Yes
application/smil 	SMIL 	smil 	Yes

Helix DNA Plugin: RealPlayer G2 Plug-In Compatible

    File name: nphelix.so
    Helix DNA Plugin: RealPlayer G2 Plug-In Compatible version 0.4.0.622 built with gcc 3.3.5 on Jul 18 2006

MIME Type 	Description 	Suffixes 	Enabled
audio/x-pn-realaudio-plugin 	RealPlayer Plugin Metafile 	rpm 	Yes

Can anyone advise how to get Realplayer itself to play the real media streams?

I have tried removing mozilla-mplayer to no avail.  I also tried adding to the PATH references to /usr/lib/realplayer-10.0.8/ , and its  plugins directory, as well as /usr/lib/firefox/plugins, but to no avail.

Many thanks,

    -- Joe

---

### Post by WebDrake on 2006-11-20
Hmm.  I was too hasty to assume it might be something complicated.

In the end no serious fiddling was required, only (1) remove totem-mozilla and (2) remove any realmedia-related mplayer plugins.

---

### Post by majabl on 2006-11-24
> **WebDrake said:**
> Hmm.  I was too hasty to assume it might be something complicated.

In the end no serious fiddling was required, only (1) remove totem-mozilla and (2) remove any realmedia-related mplayer plugins.

I suspect I am having the same problem as you (and would also like to play BBC Radio!), but unfortunately I'm quite new to Ubuntu and don't know how to action your solution.  Would you mind sharing what I need to click on?

NB I'm running an installation of Edgy Eft and have not installed anything beyond what was installed when I first set up the system.

Thanks in advance!

---

### Post by nickmcg on 2006-11-26
Hi,

I'm running Edgy & had the same problem, and all I had to do was to remove totem-mozilla (thanks WebDrake).

Matthew,
Two ways of removing totem-mozilla.
1) use synaptic (System->Administration->Synaptic Package Manager), find totem-mozilla & remove it
2) open a terminal session (Application->Accessories->terminal) and type
```

sudo apt-get remove totem-mozilla

```

Note: Both these methods produce the heart-stopping message that ubuntu-desktop would also be removed. I went ahead anyway, and everything still seems to work.

Nick

---

### Post by richardward101 on 2006-11-27
Having a similar problem (once more, BBC player, go the BBC!). But I didn't want to remove the totem plugin, as its useful for other embedded content. It turns out that Firefox looks at the plugins in alphabetical order, so it tries "libtotem" before "nphelix" because totem (falsely) claims to support RealMedia streams.

So heres a solution that allows you to keep both:
```

cd /usr/lib/firefox/plugins
ls

```

make sure you have a file called nphelix.so and nphelix.xpt here (if not, find a guide on installing real with Firefox).  Now:
```

sudo ln -s nphelix.so aaanphelix.so
sudo ln -s nphelix.xpt aaanphelix.xpt

```

Now, Firefox should load aaanphelix.so first, and use that for the BBC site, and then fall back to libtotem.so for other sites. 

Hope that helps!

(ps, this should make any plugin work alongside real:, mplayer, vlc, xine, etc)

---

### Post by richardward101 on 2006-11-27
majabl:
If you haven't installed any software yet you may find [ubuntuguide.org]("ubuntuguide.org") useful. Particularly the section about "automatix" It'll install just about anything you could want.

PS, you BBC lovers may find the following good:
[How to capture real audio streams for later.]("http://www.elsewhere.org/journal/archives/2004/09/25/howto-capture-streaming-audio-for-later/")

If you put a little time in you can write a script that'll download them straight from Firefox for later use on mp3 players etc.

---

### Post by christooss on 2006-11-27
richardward I have done that but than mplyer was still in about:plugins player for rm files. Than I have removed mplayer-rm* and now no program is in charge for rm files

---

### Post by christooss on 2006-11-27
richardward can you post ~/.mozilla/plugins.dat ?

---

### Post by richardward101 on 2006-11-27
my aboutLplugins lists helix as the realstream player. Do you definately have nphelix.so in you /usr/lib/firefox/plugins/ directory?

---

### Post by christooss on 2006-11-27
HM

I have preformed a clean install. Not for realplayer problem but other things.

So whan I installed Real Player from official package GoldBIn from real.com Than I have preformed

sudo ln -s nphelix.so aaanphelix.so
sudo ln -s nphelix.xpt aaanphelix.xpt

But nothing happend. I havent installed any media players before. Only realplayer. It drives me nuts that I can't fix this :(

this is ls from /usr/lib/firefox/plugins/

aaanphelix.so                libtotem-gmp-plugin.xpt
aaanphelix.xpt               libtotem-mully-plugin.so
flashplayer.xpt              libtotem-mully-plugin.xpt
libflashplayer.so            libtotem-narrowspace-plugin.so
libtotem-basic-plugin.so     libtotem-narrowspace-plugin.xpt
libtotem-basic-plugin.xpt    libunixprintplugin.so
libtotem-complex-plugin.so   nphelix.so
libtotem-complex-plugin.xpt  nphelix.xpt
libtotem-gmp-plugin.so

---

### Post by richardward101 on 2006-11-27
try ```
sudo apt-get remove totem-mozilla
```
see if real streams work then?

---

### Post by christooss on 2006-11-28
No it doesn't work :(

about:plugins is now almost empty :(

---

### Post by drphilngood on 2006-11-28
I was getting the same error and found that Mplayer Firefox-plugin plays real media streams, fine.

Just follow this guide to replace totem with mplayer:

[HOWTO: replace totem with mplayer]("http://ubuntuforums.org/showthread.php?t=76946")

Good luck!

---

### Post by richardward101 on 2006-11-28
Ok well it appears theres something wrong with the Realmedia installation. I would suggest using the version in the repositories. Remove the one you've got installed (search the forum or Google for how if you have trouble). then add the line:
```
 deb http://archive.canonical.com/ubuntu dapper-commercial main
```
to /etc/apt/sources.list
Now do:
```
sudo apt-get update
sudo apt-get install realplay
```.
Now restart firefox and see what gives.

---

### Post by richardward101 on 2006-11-28
ok I think that may not work any more as of EDGY.
 what happens when you type cat /usr/lib/firefox/plugins/nphelix.xpt

---

### Post by christooss on 2006-11-28
> **richardward101 said:**
> ok I think that may not work any more as of EDGY.
 what happens when you type cat /usr/lib/firefox/plugins/nphelix.xpt

I get terminal full of many "random" characters

---

### Post by richardward101 on 2006-11-28
can you play files in the stand alone realplayer?

---

### Post by christooss on 2006-11-28
Yea they do

---

### Post by christooss on 2006-11-28
realplayer plugin works in old mozilla. Very interesting. nphelix.so shows to same location that firefox do.

hm

---

### Post by christooss on 2006-11-29
OK its working now in Firefox to.

I have went through all the steps in this howto

[https://help.ubuntu.com/community/RealplayerInstallationMethods](https://help.ubuntu.com/community/RealplayerInstallationMethods)

And I have installed realplayer wiht deb package.

Now I have to check why sound doesn't work but that is matter to discuss here :)

---

### Post by deputyjones on 2006-12-01
thanks Chris the install guide worked for me too.

---

