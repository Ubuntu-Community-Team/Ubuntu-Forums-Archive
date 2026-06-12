---
title: "Gstreamer with 3gpp"
date: 2008-08-02
forum: Multimedia Software
---

### Post by steviefordi on 2008-08-02
I am new to ubuntu, having installed it a while ago I've only just broken my MS windows shackles and have started to use Ubuntu as my main OS.

I am using gutsy, trying to play video taken from my mobile phone. The file (according to the file manager) is 3GPP with a .mp4 extension. The problem is I get no sound when playing through totem. I can play them fine in Mplayer but would rather use Totem.

I've installed all the gstreamer plug-ins I can find but to no avail. Launching Totem from the CLI gives me:

sh: jackd: not found
** Message: don't know how to handle audio/AMR, codec_data=(buffer)0000001164616d7248455241000010000f, rate=(int)8000, channels=(int)1
** Message: Missing plugin: gstreamer|0.10|totem|Adaptive Multi Rate (AMR) decoder|decoder-audio/AMR (Adaptive Multi Rate (AMR) decoder)
no application found
** Message: No installation candidate for missing plugins found.

Any help would be greatly appreciated....

Oh, and I've also tried totem with the xine backend but xine doesn't like my PC and I couldn't install the extra plug-ins.

---

### Post by kpkeerthi on 2008-08-02
[https://bugs.launchpad.net/ubuntu/+source/gst-plugins-ugly0.10/+bug/184555](https://bugs.launchpad.net/ubuntu/+source/gst-plugins-ugly0.10/+bug/184555)

---

### Post by steviefordi on 2008-08-03
Ok, thanks for that. As I understand it then - Gstreamer does have a plug-in for this audio type, but it's not included in the Ubuntu Gstreamer packages.

If this is so, can I install the bad and ugly packages myself without using any of the package managers?

Alternatively what can I use to convert my 3GPP to a free format and include the sound?

---

