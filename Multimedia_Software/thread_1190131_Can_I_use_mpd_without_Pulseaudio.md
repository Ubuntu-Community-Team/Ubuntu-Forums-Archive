---
title: "Can I use mpd without Pulseaudio?"
date: 2009-06-17
forum: Multimedia Software
---

### Post by chris_andrew on 2009-06-17
Hi,

I've installed mpd and Sonata, but don't want to use Pulseaudio.  When I've googled for a how-to, they all mention Pulseaudio.

Can anyone tell me whether I can run mpd without it?  

Cheers,

Chris.

---

### Post by mcduck on 2009-06-17
> **chris_andrew said:**
> Hi,

I've installed mpd and Sonata, but don't want to use Pulseaudio.  When I've googled for a how-to, they all mention Pulseaudio.

Can anyone tell me whether I can run mpd without it?  

Cheers,

Chris.

Yes, and it actually uses Alsa unless you specifically configure it to use Pulseaudio instead.

My tip for installing & configuring MPD is to skip all the guides, they just make it more complicated than what's necessary. Just install the packages (at least MPD and some client) , symlink your music directory into MPD's defaut directory (/var/lub/mpd/music) and in most cases you have a working setup without even touching the configuration file.. ;)

---

