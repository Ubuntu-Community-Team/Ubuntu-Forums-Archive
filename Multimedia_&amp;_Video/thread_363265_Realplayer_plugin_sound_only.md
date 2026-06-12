---
title: "Realplayer plugin sound only"
date: 2007-02-16
forum: Multimedia &amp; Video
---

### Post by Bloch on 2007-02-16
The video content on the BBC site and on the RTE site [http://www.rte.ie/](http://www.rte.ie/)
both used to play. That is to say, I eventually got the plugins to work. But now suddenly there  is audio only and no image. I have RealPLayer 10.8.0.805.   It works fine as a stand-alone player.
The plugin displays the RealPlayer logo (i.e. it is definitely not the mplayer plugin which purports to play real media but never worked) and plays the sound, but no image.

Can someone check to see if these sites are working?

Another point: I am pretty sure, but cannot prove, that the RTE site mentioned their content can be played on linux witht he real player, but now any reference to linux has been removed.

---

### Post by Red Knuckles on 2007-02-17
> **Bloch said:**
> The video content on the BBC site and on the RTE site [http://www.rte.ie/](http://www.rte.ie/)
both used to play. That is to say, I eventually got the plugins to work. But now suddenly there  is audio only and no image. I have RealPLayer 10.8.0.805.   It works fine as a stand-alone player.
The plugin displays the RealPlayer logo (i.e. it is definitely not the mplayer plugin which purports to play real media but never worked) and plays the sound, but no image.

Can someone check to see if these sites are working?

Another point: I am pretty sure, but cannot prove, that the RTE site mentioned their content can be played on linux witht he real player, but now any reference to linux has been removed.

I got video but no sound in RealPlayer. Why???:confused:

---

### Post by Red Knuckles on 2007-02-18
I got video and sound from [http://www.rte.ie/](http://www.rte.ie/) and [http://www.bbc.com](http://www.bbc.com) now. The mplayer plugin is playing video with sound. For the radio pages I uninstalled RealPlayer and installed gxine, gxine-plugin, kaffeine-plugin. For these 2 websites gxine works for me. For [http://www.npr.org](http://www.npr.org) kaffeine works.
:guitar: :lolflag:

---

### Post by Red Knuckles on 2007-02-18
I've just figured out how to get sound from RealPlayer in Firefox and Swiftfox:

sudo aptitude install alsa-oss
sudo kwrite /usr/lib/realplay-10.0.8/realplay

edit this line [It's line 73]

$REALPLAYBIN "$@"

to read:

aoss $REALPLAYBIN "$@"

reboot and you should have sound in RealPlayer on the mentioned web sites.
:guitar: :lolflag:

---

### Post by Bloch on 2007-02-23
The realplayer plugin now works properly again. The clips on the RTE and BBC websites mentioned work fine.

They definitely didn't work last week - in fact even when the .smil files were opened dircetly with RealPlayer there was the same problem: sound but no video.

I'm glad they are working again but have no idea why they stopped working for a month and suddenly started again - I did not alter any relevant files on my system.

I run standard Dapper 6.06, firefox, and with realplayer installed by automatix or by synaptic - there was the same problem either way until today.

---

