---
title: "Wifi weirdness 10.04 featuring the iwl3945 and the rtl8187"
date: 2010-12-15
forum: Networking &amp; Wireless
---

### Post by Kernelingus on 2010-12-15
I'm still noobish, but I'm a determined wifi experimenter and have stumbled up something that has me stumped...

My trusty Dell laptop has the Intel iwl3945 a/b/g onboard, and I use it most of the time.  (Works like a charm.)  But I also have one of those nifty, brand-less Chinese dongles that has a Realtek 8187 inside and an external SMA connector, which is handy for long-range situations, testing homebuilt antennas or whatever.

I recently ubgraded to Lucid from Hardy and noticed some weird new behaviors at the kernel level.  Specifically:

(1) If I plug in the RTL8187, it automatically registers the device, puts it into 'Managed' mode and goes looking for a network to associate with, even if the IWL3945 is already associated with a network.  Usually, this results in each respective adaptor becoming associated with a different network, which at first was a cool and pleasant surprise, however mystifying as to what's happening, routing-wise, under the hood.  (I'd love it if someone cared to explain.)  The RTL8187 just shows up as 'wlan1', and the IWL3945, as ususal, as 'wlan0'.  What's going on here?

(2) If I try taking one of the adaptors down (with ifconfig), it comes back up on its own.  (Very frustrating.)  I'd like to be able to have one running (for my network) and be able to mess around and experiment with the other.  But it keeps wanting to come back up, and when it does, it comes up in managed mode and goes looking for a network.  How do I get it to stop this?

---

### Post by Kernelingus on 2010-12-15
(Badump) ^ bump.

---

