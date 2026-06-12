---
title: "Thin vertical coloured lines over picture on some channels only (DVB tuners)"
date: 2012-01-06
forum: Mythbuntu
---

### Post by ubnewbie2 on 2012-01-06
I have just clean installed Mythbuntu 11.10.  I have it all up and running except, some channels (and I think it's only/mainly the High Definition channels) have thin vertical coloured lines partially obscuring the picture.  The other channels are perfect. This is while watching live TV (Haven't tried recording yet)

My setup uses an nvidia video card and I have loaded the proprietary drivers.  My 3 tuners are all DVB tuners.

Edit:  ran a quick test recording.  The thumbnail it shows is perfectly clear, but playing the recording shows the same vertical lines as live TV.

---

### Post by ubnewbie2 on 2012-01-06
I've been fiddling with the setup and I think I found a way around it.  I went into the setup TV playback profiles.  It was set to CPU+, so I changed it to CPU++, because that used the same method for all resolutions.  Now it seems to work on all channels.


Is this a reasonable way to fix it, or should I find out why CPU+ didn't work?

---

### Post by nickrout on 2012-01-08
If your nvidia card does vdpau, you should use that profile. 

[http://www.mythtv.org/wiki/VDPAU](http://www.mythtv.org/wiki/VDPAU)

---

### Post by ubnewbie2 on 2012-01-08
> **nickrout said:**
> If your nvidia card does vdpau, you should use that profile. 

[http://www.mythtv.org/wiki/VDPAU](http://www.mythtv.org/wiki/VDPAU)


Unfortunately it's a 7050, so too old, but thanks for the tip, as I might upgrade the card sometime.

---

