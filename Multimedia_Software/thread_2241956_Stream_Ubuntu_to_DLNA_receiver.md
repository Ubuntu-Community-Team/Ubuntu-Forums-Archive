---
title: "Stream Ubuntu to DLNA receiver"
date: 2014-08-29
forum: Multimedia Software
---

### Post by antoskail on 2014-08-29
Hi!

Ughh... 2 days searching passed...

What I have:
  1. Ubuntu 14.04 PC
  2. WiFi DLNA audio renderer with audio output. Something like USR-S12 device.

What I need:
  1. somehow to copy my audio stream (from Ubuntu) to that WiFi DLNA renderer (i guess it's renderer after all)
  2. somehow I need a trigger to switch off that stream to WiFi DLNA renderer
  3. in best case I would like to select stream directions i.e. Rhythmbox plays audio via WiFi renderer, VLC plays audio via integrated sound card.

What I have found:
  1. **rygel** looks like it can be used as DLNA server only (this means I can browse PC multimedia via any smart-phone, but can't play PC audio on remote device initiated by PC)
  2. **Coherence **really promissing, but latest version reffers to Python 2.5, but Ubuntu 14.04 has Python 3, as i knot whats leads to A LOT of compatibility issues. Honestly, I did not find way to run it on my Ubuntu 12.04 workstation at work...
  3. **I CAN **play audio from my smartphone on WiFi DLNA with no special apps (at least on HTC phones) this means problem is in PC
  4. I have found, that some guys did that work like [here]("http://forums.debian.net/viewtopic.php?f=6&t=107267#p511640") or [here]("http://oliversmith.io/technology/2012/01/10/streaming-audio-from-ubuntu-linux-to-a-dlna-player-blu-ray-or-ps3/"), but first gave no hint how to configure rygel for that and second looks something different, because there is no way to select my WiFi DLNA renderer

That would be REALY great, if someone could give a hint...

---

### Post by antoskail on 2014-09-19
I have found that I can run "GUPnP AV Control Point" and rygel.

After that in "GUPnP AV Control Point" I can select Renderer (remote speaker or mobile phone with BubbleUPnP installed) and choose media from rygel list.

phone with BubbleUPnP plays fine, but WiFi DLNA renderer does not ((

Moreover this does not allow to play youtube e.t.c. on remote speaker...

---

### Post by Nabeel_Moeen on 2015-01-04
trying to figure the same out, were you able to get this working satisfactorily? if so, can you share the instructions?

---

### Post by Keith_Beef on 2015-01-24
I've been trying to get my son's Sony SA-NS310 speaker to work with a few devices other than his iPod Touch. The idea is to be able to use Android phones or our Linux computers to play music stored on a NAS over that speaker.

I installed a few packages:
gupnp-dlna-tools
libgupnp-av-1.02
libgupnp-dlna-2.0-3
gupnptools
rygel

I started up gupnp-av-cp in the terminal and the interface appeared. It had already discovered my NAS and my son's speaker, the speaker was listed as the only "Renderer" available. It had got a list of the available music and I was able to browse to individual tracks. When I hit the play button,  music came from the speaker&#8230; I don't ever remember anything being this easy and straightforward! :D

BUT&#8230; but&#8230;

This only seems to work for certain tracks: those in MP3 format. Anything I have bought from Amazon works just fine. But anything I have ripped from my own CDs in OGG or FLAC format gets a "** (gupnp-av-cp:12395): WARNING **: no compatible URI found." in the terminal and no sound.

This is similar behaviour to what I see when trying to use Sony's own "remote control" app for Android, which leads me to think that both the Sony app and gupnp-av-cp are in fact just sending a URI to the speaker telling it to get and play a file, and it fails because the speaker does not know how to decode these OGG and FLAC files.

What I really need, I think, is something to control the NAS to send an audio stream out on the network, and to tell the speaker to catch that stream and render it.

I have Logitech Squeezebox Server running on the NAS; this can take any of the files on the NAS and sends out an MP3 stream on port 9000 to my Squeezebox boom. I can connect Firefox to the Squeezebox server by giving it the URL [FONT=Fixedsys]NAS.local:9000[/FONT] and this gives me the (*really* slow) interface to the server where I can set up a playlist. Now I point Clementine to [FONT=Fixedsys]NAS.local:9000/stream.mp3[/FONT] and play that stream. This should work for not only MP3, but for **all** formats of audio file that I have on there, just like it does for the Squeezebox, but for some reason I only hear music from Clementine when I add MP3 files to the playlist.

In fact, now that I've done a few more experiments, it seems like the Squeezebox Server is sending out a specific stream per device, because I can play one playlist to the Squeezebox Boom and another to Clementine on my Linux computer. But while the Boom plays the OGG and FLAC files just find, Clementine does not&#8230; which is really strange. It is not working how I thought it did.

---

### Post by Nutria on 2015-01-24
> **antoskail said:**
> Hi!

Ughh... 2 days searching passed...

What I have:
  1. Ubuntu 14.04 PC
  2. WiFi DLNA audio renderer with audio output. Something like USR-S12 device.

The USR-S12 is a bare PCB module.  What "system" does it plug itself into?

> What I need:
  1. somehow to copy my audio stream (from Ubuntu) to that WiFi DLNA renderer (i guess it's renderer after all)
  2. somehow I need a trigger to switch off that stream to WiFi DLNA renderer
  3. in best case I would like to select stream directions i.e. Rhythmbox plays audio via WiFi renderer, VLC plays audio via integrated sound card.

What I have found:
  1. **rygel** looks like it can be used as DLNA server only (this means I can browse PC multimedia via any smart-phone, but can't play PC audio on remote device initiated by PC)
  2. **Coherence **really promissing, but latest version reffers to Python 2.5, but Ubuntu 14.04 has Python 3, as i knot whats leads to A LOT of compatibility issues. Honestly, I did not find way to run it on my Ubuntu 12.04 workstation at work...

The standard Python in 14.04 is 2.7.

>   3. **I CAN **play audio from my smartphone on WiFi DLNA with no special apps (at least on HTC phones) this means problem is in PC
  4. I have found, that some guys did that work like [here]("http://forums.debian.net/viewtopic.php?f=6&t=107267#p511640") or [here]("http://oliversmith.io/technology/2012/01/10/streaming-audio-from-ubuntu-linux-to-a-dlna-player-blu-ray-or-ps3/"), but first gave no hint how to configure rygel for that and second looks something different, because there is no way to select my WiFi DLNA renderer

That would be REALY great, if someone could give a hint...

What's your **ultimate** goal?

Play music from your Ubuntu PC to your smartphone **and** a wireless Rythmbox?

---

### Post by Nutria on 2015-01-24
> **Keith_Beef said:**
> I've been trying to get my son's Sony SA-NS310 speaker to work with a few devices other than his iPod Touch. The idea is to be able to use Android phones or our Linux computers to play music stored on a NAS over that speaker.

Page 25 of the SA-NS310 manual: **Using DLNA (Digital Living Network Alliance)**

So... install a dlna server on Ubuntu that runs whether you're logged in or not.

Ubuntu happens to have such a lighweight dlna server, helpfully named: minidlna.

---

### Post by Keith_Beef on 2015-01-24
> **Keith_Beef said:**
> I've been trying to get my son's Sony SA-NS310 speaker to work **with a few devices** other than his iPod Touch. The idea is to be able to use Android phones or our Linux computers to play music stored on a NAS over that speaker.

> **Nutria said:**
> Page 25 of the SA-NS310 manual: **Using DLNA (Digital Living Network Alliance)**
Sony's manual is about as useful as a chocolate fireguard.

> So... install a dlna server on Ubuntu that runs whether you're logged in or not.

Ubuntu happens to have such a lighweight dlna server, helpfully named: minidlna.

If the Linux computer is switched on, then somebody is logged in. In any case, I don't really need to have a DLNA server running on it, because the NAS filesystems are mounted on the Linux box. Clementing gets the files like that and plays them to me. It's an interesting idea, though.

I had thought that the Squeezebox Server on the NAS was doing transcoding from OGG and FLAC to MP3 before sending it out as a stream to the Squeezebox Boom; I hoped that this would mean that the Sony speaker would be able to catch that stream, too. Unfortunately this seems not to be the case. DLNA turns out to be just another big can of worms. As the Sony manual's sole pearl of wisdom puts it: " You may not be able to play back some content with DLNA CERTIFIED products". In reality, this seems to mean "any mention of DLNA CERTIFIED on one product is absolutely no promise whatsoever of compatibility with any other product also marked DLNA CERTIFIED".

---

### Post by Nutria on 2015-01-24
> **Keith_Beef said:**
> In any case, I don't really need to have a DLNA server running on it, because the NAS filesystems are mounted on the Linux box.

????

> Clementing gets the files like that and plays them to me. It's an interesting idea, though.

???

> I had thought that the Squeezebox Server on the NAS

Is this a hacked bit of 3rd party kit?  (Like WD or something?)

> was doing transcoding from OGG and FLAC to MP3 before sending it out as a stream to the Squeezebox Boom;

What audio file formats does the Squeezebox Boom support?  If it natively understands OGG & FLAC, then no need for the SB Server to transcode.

> I hoped that this would mean that the Sony speaker would be able to catch that stream, too.

Where in your research did you find that the SA-NS310 can connect to Squeezebox Server?

> DLNA turns out to be just another big can of worms.

I've been using Ubuntu as a DLNA server to media players for 3+ years with great success.

> As the Sony manual's sole pearl of wisdom puts it: " **You may not be able to play back some content with DLNA CERTIFIED products**". In reality, this seems to mean "any mention of DLNA CERTIFIED on one product is absolutely no promise whatsoever of compatibility with any other product also marked DLNA CERTIFIED".

Your interpretation is wrong.

What it means is that a DLNA Server serving up media in a specific set of formats is not a guarantee that a DLNA client will understand those formats.  Which is completely reasonable.

You need something that transcodes on-the-fly to a DLNA server.  Plex seems to be what you need, but it requires that your PC run -- if not 24x7 -- then at least when your son is around and awake...
[https://apps.ubuntu.com/cat/applications/trusty/plexmediaserver/](https://apps.ubuntu.com/cat/applications/trusty/plexmediaserver/)

---

