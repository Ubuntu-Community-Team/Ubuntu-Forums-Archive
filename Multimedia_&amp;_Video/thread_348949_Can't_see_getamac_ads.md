---
title: "Can't see getamac ads"
date: 2007-01-29
forum: Multimedia &amp; Video
---

### Post by arizonagroovejet on 2007-01-29
So when I go to [http://www.apple.com/uk/getamac/ads/](http://www.apple.com/uk/getamac/ads/) I get a big blank space where I ought to be seeing the amusing antics of Mitchell and Webb.

Kubuntu Edgy, Firefox 2.0.0.1, Totem Web Browser Plugin 2.16.2, w32codecs_20061022-0.0_i386.deb installed.

Anyone?

cheers,

mike

---

### Post by david_2001 on 2007-01-29
Screenshot-0.png shows what you're missing and Screenshot-1.png shows how I did it.  The w32codecs don't work with totem, as far as I know, but do work with the mozilla-mplayer plugin.  The trick to making it functional is, after installing mozilla-mplayer, to delete the various links to the totem plugins in /usr/lib/firefox/plugins (libtotem-basic-plugin.so etc.).  Of course, do an about:plugins in firefox first to check that you won't be losing anything you need by eliminating the totem plugins!

---

### Post by arizonagroovejet on 2007-01-29
I actually dumped mplayer-plugin in favour of the totem one a while back because I was fed up of mlpayer-plugin hanging Firefox.

Anyhow I've installed mplayer-plugin and uninstalled totem-plugin but still there's a blank space where the ad should be.

I had totem-xine installed and I thought xine could use the w32 codecs so assumed totem could. Though in the course of looking at this issue I realised totem-xine was no longer installed but something called totem-gstreamer is. So I removed that too. I was able to re-install totem-xine, but then selecting totem-mozilla for install caused Adept to mark totem-xine for removal and totem-gstreamer for installation again. I'll look at what that's about when I'm not so tired.

Also mplayer-plugin decided it wanted to play RealPlayer streams (E.g. BBC News) but failed to actually do so. Removing  mplayerplug-in-rm.* from /usr/lib/firefox/plugins gave the RealPlayer streams back to the RealPlayer plugin.

---

### Post by david_2001 on 2007-01-29
Yes, that's quite a complicated history for this time in the evening.  Xine will use the w32codecs, provided that it knows where they're installed (and every application that uses libxine has it's own settings file to be set.  Gah!)  And I dumped realplay for mozilla-mplayer because, for me at least, it's much better at streaming video from the BBC's news site.  Ho hum...

---

### Post by arizonagroovejet on 2007-01-30
Doh. Adblock.

The mplayer plugin plays the ads fine, once I added an exclusion rule to adblock for [www.apple.com](www.apple.com). Something in the Filterset.G list of adblock rules was blocking them.

The mplayer plugin still won't play Real streams like from news.bbc.co.uk, but as previously mentioned it's easy to stop it trying to.

The stability of mplayer plugin seems a lot better than when I last used it too.

---

### Post by david_2001 on 2007-01-30
> **arizonagroovejet said:**
> Doh. Adblock.
I would never have thought of that!  I used to use AdSubtract under Windows when I connected to the internet via a pay as you go dialup service but since I got broadband I've been lazy and haven't bothered.

---

