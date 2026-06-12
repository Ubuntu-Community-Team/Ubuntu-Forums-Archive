---
title: "How/Where to get snd-pcm1-oss?"
date: 2006-04-06
forum: Multimedia &amp; Video
---

### Post by johnpipe on 2006-04-06
Hi, I've found a way to get the old soundblaster working, but it crashes X (locks up keyboard, HD spins incessantly) 8 seconds after login!  Maybe the module snd-pcm1-oss would prevent this; it is said that it's required for OSS sound, but I can't find it!

The crash happens from snd-sb16 (without snd-pcm1-oss), disabling it prevents the crash, tried to substitute snd-sb-common for snd-sb-16 but that doesn't provide sound.

I've installed every package for 386 from synaptic, but still no snd-pcm1-oss; does anyone know what package provides this? I don't know how to find this out.

Thanks in advance,

johnpipe

---

### Post by johnpipe on 2006-04-06
I have just checked the kernel config file in /boot/; it seems the kernel is <em>not</em> configured for snd-pcm1-oss, only for snd-pcm-oss. 
It probably wouldn't have helped the problem of snd-sb-16, anyway; despite all the configuration references I've seen saying "do this" for ISA non-pnp, I don't believe snd-sb16 is supposed to be for non-pnp ISA cards.

Not sure why the ubuntu stock kernel isn't configured for snd-pcm1-oss.

Looks like if I want sound on ubuntu  I'll just have to break down and buy a new soundcard;  the older distributions on the other partitions run the old card OK. That will take a while however; the $$$ for a brand-new card are, unfortunately, not available.

Thanks,  Johnpipe

---

