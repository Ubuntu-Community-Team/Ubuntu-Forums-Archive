---
title: "Streaming video help"
date: 2007-08-08
forum: Multimedia &amp; Video
---

### Post by Virgofenix on 2007-08-08
Can anybody view the embedded video here: [http://www.apple.com/imac/ads/](http://www.apple.com/imac/ads/)

I can't inside Firefox. I tried using the MediaPlayerConnectivity plugin to view it in VLC. Clip plays for a few seconds then freezes though the time is still progressing.

Using the GNOME UI with Feisty Fawn.

---

### Post by ruibernardo on 2007-08-08
I had no problems in viewing it. I have vlc installed too, but Totem did reproduce it too. Check if you got the right packages installed here:

[Enabling Multimedia in Feisty (HOW-TO)]("http://ubuntuforums.org/showthread.php?t=413626")




---

### Post by endre on 2007-08-08
I have the same problem, trying to watch the exact same videos!

When I open the page, the only thing that comes up is a black window, and if I right-click it, I find out that it insists on using Totem!! This despite me installing VLC and editing the settings of Firefox, telling it to use VLC for everything. I have even uninstalled Totem completely, and still it insists on using it! Arrgh!

Problem is, of course, that Firefox does not even list ".mov" in its list of formats, so I can't force it to use VLC in this particular case.... 

The only way I can watch anything in .mov format now is to copy the location and paste it into VLC "open network stream." Not exactly handy...

And yes, I have been through all the codecs, only that I use Xine and not Gstreamer....

Any ideas?

---

### Post by ruibernardo on 2007-08-08
> **endre said:**
> 
And yes, I have been through all the codecs, only that **I use Xine and not Gstreamer**....
Any ideas?

The recommended packages are GStreamer. Please check the link on my previous post.

---

### Post by Virgofenix on 2007-08-11
That did it. Thanks. Was Ubuntu supposed to have trouble playing streaming video out of the box?

---

### Post by ruibernardo on 2007-08-11
> **Virgofenix said:**
> That did it. Thanks. Was Ubuntu supposed to have trouble playing streaming video out of the box?
If you use free and open codecs it shouldn't. But Ubuntu doesn't support proprietary and closed codecs for legal reasons, so you have to install them if you're fine with them.

---

### Post by Chappy7777 on 2007-08-17
> **Virgofenix said:**
> That did it. Thanks. Was Ubuntu supposed to have trouble playing streaming video out of the box?
-----------------------------------------
Not to start any hassle here, but I for one seriously doubt that Ubuntu puts out anything that is "supposed to have trouble". It's a free OS and a work in progress. 

There are programs running on my Feisty that I thought I'd never get running. I even uninstalled 7.04 and reinstalled 6.06 I was having so much trouble. But after reading thru these forums and some trial and error I managed to get the problem fixed and am now using Feisty again.

As was already stated, there are some files Ubuntu can only let US decide to download using Synaptic. If that box with the "this is a legal issue yada yada" pops up, make sure and allow it to download. Of course, on 2nd thought, that decision is each user's to make. The point is, it's not Ubuntu's.

Most of us are using linux because we are sick of the way Wind---s forces us to do things. 

Anyhow, no hard feelings, it was just the way you worded this that got me thinking of what a gift Ubuntu has been to this computer guy and how I enjoy not having to be in bondage to M$.

---

### Post by phenest on 2007-08-17
A tip for those using Feisty 7.04:

If the video doesn't play, it's usually a lack of codecs. Right click the window where the video should be playing in Firefox and select Open with Movie Player from the menu. When Movie Player Starts, at will complain there is no codec to play it and will suggest what to download. Download all the suggestions and it should play. Sometimes, it may suggest some more. Download them and when it begins to play, go back to Firefox and refresh the page.

Ta da!

---

### Post by Virgofenix on 2007-08-20
> **Chappy7777 said:**
> 

Anyhow, no hard feelings, it was just the way you worded this that got me thinking of what a gift Ubuntu has been to this computer guy and how I enjoy not having to be in bondage to M$.

I apologize if my wording is abrasive. I'm still trying to grasp what Linux is and how it does things. It has been like learning how to swim again and drowning a few times.

Thanks to all of epimeteo's comments.

---

