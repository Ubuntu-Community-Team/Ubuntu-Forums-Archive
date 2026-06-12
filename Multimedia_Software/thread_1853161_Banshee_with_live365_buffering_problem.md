---
title: "Banshee with live365 buffering problem"
date: 2011-10-01
forum: Multimedia Software
---

### Post by vajorie on 2011-10-01
I'm using ubuntu 11.04 o a relatively old netbook (eeepc 701 4GB). I installed using the server iso and the ubuntu-netbook package. 

Banshee works fine: plays my local music without problems, as well as jamendo, magnatude, xiph.org. 

However, almost every station on live365.com (using the liveradio plugin/extension) stutters and gets stuck at "0% buffering" after the ads have played (ads play fine for some reason). 

Google revealed many folk having similar problems but no solutions. I tried fixing this with gstreamer-properties as well as investigating if this is a memory or cpu issue: it seems not to be. I have about 700MB free memory and cpu use does not go above 65% or so. My internet speed is fine. I have free disk space too. 

Somehow, buffering settings seem not to fit live365's tastes. 

Any ideas?

---

### Post by mendhak on 2011-11-10
Did you ever find a solution to this?  I've noticed the same problem for me when using Live365.com radio stations.  I'm using the same plugin.

---

### Post by vajorie on 2011-11-11
> **mendhak said:**
> Did you ever find a solution to this?  I've noticed the same problem for me when using Live365.com radio stations.  I'm using the same plugin.

Unfortunately, no. I ended up jotting down a few nice radio stations I found through Banshee and switching to mpd...

---

### Post by freakalad on 2012-08-20
I'm trying to listen to my MPD stream (pushed out via HTTP on LAN) on Banshee, but I get the same result.
It loads the HTTP stream metadata OK, but fails to play media (keeps buffering to 0.0%).

The same MPD HTTP stream works OK in other players, such as VLC & Chromium browser (& mobile)

- incidentally, the same issue seems to be present in Rhythmbox

---

