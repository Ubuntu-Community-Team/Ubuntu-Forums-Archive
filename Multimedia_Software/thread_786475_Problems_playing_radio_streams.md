---
title: "Problems playing radio streams"
date: 2008-05-08
forum: Multimedia Software
---

### Post by Gevatter Tod on 2008-05-08
When i play radio streams in Hardy Heron (e.g. from Shoutcast) I get horrible glitchings in the sound. Every second or so it seems like you are listening a scrachted CD. I have tried almost all available media players (BMPx, Audacious, XMMS, Amarok, Rythmbox), used a different sound card but the problem persists.
In Gutsy, i never had this kind of problem.

The soundcards I have tried have are Ensoniq (ES1371) and Nvidia HDA (AD198x). Mp3 files from harddisk play perfect. Here is an example stream that produces the glitches and scratches when playing: [http://www.schwarze-welle.com/play.m3u](http://www.schwarze-welle.com/play.m3u)

Can anyone help me? 

Thanx a lot!

---

### Post by Gevatter Tod on 2008-05-27
Does no one have any idea?

---

### Post by thorgal on 2008-05-27
works fine on my debian sid system (but the stream is not of high quality though, too agressive to the ears ... ;) ). Could be a network issue. Have you checked this ? are you using a wireless LAN ?

---

### Post by Gevatter Tod on 2008-05-29
No, I use DSL connection with squid proxy. With Gutsy, I had no such problems.

Some programms allow to increase the stream buffer, I also tried this without an effect.

Can it be a codec problem? Normal mp3 files play just fine.

UPDATE
It seems that squid is causing the problems. I have convinced my admin to grant me a direct access to the radio streaming site and now it works without glitches. Has anyone else experienced that problems with squid, too?

---

### Post by Delphinus on 2010-11-19
Sorry for the thread dredge but I'm trying to find a solution to this. This is definitely related to squid, as the same audio distortion occurs when playing the stream on a windows machine (foobar2000) via a squid proxy (ubuntu server).

The problem doesn't occur if you are using a proxy/firewall stream link, eg: **[http://ice.somafm.com/beatblender](http://ice.somafm.com/beatblender)**
But if you use the normal stream link: **[http://voxsc1.somafm.com:8384](http://voxsc1.somafm.com:8384)** then the distortion happens (but only when using the squid proxy).

The **[pfsense discussion]("http://forum.pfsense.org/index.php?topic=17084.0")** indicates it might be related to the shoutcast titles?

---

### Post by tgalati4 on 2010-11-19
Could be a DNS name lookup issue.  Perhaps the proxy must continually look up the name because of a down or slow DNS server.  That might slow the stream and cause glitches.

---

### Post by Delphinus on 2010-11-19
The distortion happens multiple times a second, so I don't think its DNS. Also doing a dig on the hostname responds very quickly. And manually adding the dns entry to my router so its cached locally doesn't help either.

---

