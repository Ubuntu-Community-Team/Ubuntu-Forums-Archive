---
title: "Jerky 1080p playback"
date: 2009-01-21
forum: Mythbuntu
---

### Post by nicoloks on 2009-01-21
Hi All,

I've been using MythBuntu on my HTPC for a while, and it has been happy playing pretty much any 720p HD content I throw at it. I recently upgraded my TV to a Full HD plasma and have now found that my HTPC is really struggling playing 1080p content (apart from HDTV). Xine almost works, but VLC and mplayer are unusable. My system specs are pretty modest, but I thought though would have been capable of rendering 1080p content;

AMD X2 3800+
Onboard Geforce 6150 SE 256MB DDR II
2 x 512MB PC6400
Onboard Realtek ALC888 7.1 HD Audio

In my search to find improved performance I came across XvMC, and the Envy project which I installed. This seems to have gone ok as doing a ```
glxinfo|grep "direct render"
``` returns a value of yes, which I assume means it is working. However after reading some more I am not sure how much XvMC will help me as from what I understand it offers acceleration for MPEG2 only (which is why I assume HDTV works so well). 

Most of my 1080p content is in an mkv container using the vc-1, Xvid or x264 codecs. Short of transcoding this content to MPEG2 is there anything I can do improve the performance?

---

