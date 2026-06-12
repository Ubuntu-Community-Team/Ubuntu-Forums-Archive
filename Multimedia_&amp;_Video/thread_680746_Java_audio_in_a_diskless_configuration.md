---
title: "Java audio in a diskless configuration"
date: 2008-01-28
forum: Multimedia &amp; Video
---

### Post by stevejesus on 2008-01-28
Hi,

I have a very curious issue having to due with Java on Debian at work.  In the company I work for, we use a piece of proprietary software written in Java that handles thousands of streaming clips of compressed audio (ULAW) one after the next.  Previously, we used Windows XP machines with no issues.  Recently we have switched to Linux in the interest of security (we handle sensitive info).

Here is what seems to be the issue.  I have a Gutsy machine running at my desk from which I do my administrative work.  I tried to load up our ware and attempt to "handle" some of these clips.  The method by which our client software receives audio is rather clumsy, so what will happen is one piece of audio will exit a queue and deliver itself to the client.  After that audio has been handled, the next in the queue will deliver itself, sometimes slightly "on top" of the previous piece of audio.

Windows seems to handle this clumsy delivery system just fine.  Linux however is a completely different experience.  One piece of audio delivers itself to the client, and then, when handled, the next piece of audio will deliver itself, BUT refuses to play until the previous piece has completed in full.  This creates a GIANT problem in our business.

Here are the things I suspected initially...

Alsa on a stock Gutsy kernel cannot handle this torrent of compressed audio well enough.  So, I tried to use Ubuntu Studio's real-time kernel.  This didn't solve anything.   I was hoping that I would be able to connect it somehow to JACK, but could not find a way.  Our client software is not JACK-ware, and it seems that JAVA itself is also not JACK-aware.  So then, moving on...

My company has designed a custom Linux distro based upon Damn Small Linux.  We had to push it out of the gate prematurely in order to meet the security demands of our clients, so now we are stuck with a broken ware on over 60 machines!

So, I got to thinking some more.  Perhaps this may be an issue with OSS.  It certainly brought back memories of 2002!  Listening to an .ogg in XMMS only to have a deluge of 'ding, ding, ding' from GAIM due to all the messages I would recieve during playback of an audio track.

But...  ALSA is enabled by default in the 2.6 kernel, but provides an OSS emulation layer to support legacy apps, and ofcourse, whatever still demands OSS.  So this leads me to believe that perhaps JAVA is trying to connect to OSS.  That audio is then handled by ALSA's emulation, but NOW, only the audio handled by this app is handled one event at a time, while ofcourse I  can play any events I want on top of it via ALSA...

Does this make any sense?  

So, the environment is JAVA 6 with an ASLA sound-server using a generic AC-97 style soundcard.  So, basically the same on the diskless config and the Ubuntu config.  

Is there a way that I can check how JAVA is passing off audio events to the sound card?  And if so, is there a way I can change how JAVA handles these audio events?

This could literally make or break my company.  Any ideas would be sincerely appreciated.

---

