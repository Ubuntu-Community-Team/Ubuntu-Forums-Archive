---
title: "Totem plugin for Firefox only play video from the start"
date: 2010-09-15
forum: Multimedia Software
---

### Post by ked on 2010-09-15
Sometimes for web TV one is offered a menu where the video is divided into sub chapters where you can jump right to this part of the video by clicking in a chapter menu (very similar to playing a DVD). Well, this does not work for me. Clicking a sub chapter only set the video to play from start, and sliding the bar only freezes the player with a white screen.
Anyone else experienced this, or know about a link for a solution of the problem?
I'm running 10.04 (64b), Firefox 3.6.9, with the latest Totem-plugin.

Cheers,
ked

---

### Post by lovinglinux on 2010-09-15
I use such services all the time on multiple sites and it works for me. Nevertheless, videos are flash based. I never saw a video that has chapters if they use other plugins like Totem. BTW, I use gecko-mediaplayer.

Get [FLASH-AID](https://addons.mozilla.org/en-US/firefox/addon/161939/), an extension to remove conflicting flash plugins and install the proper version according to your browser architecture.

Also check [Comprehensive Multimedia & Video Howto]("http://ubuntuforums.org/showthread.php?t=766683").

---

### Post by ked on 2010-09-17
> **lovinglinux said:**
> I use such services all the time on multiple sites and it works for me. Nevertheless, videos are flash based. I never saw a video that has chapters if they use other plugins like Totem. BTW, I use gecko-mediaplayer.

Get [FLASH-AID](https://addons.mozilla.org/en-US/firefox/addon/161939/), an extension to remove conflicting flash plugins and install the proper version according to your browser architecture.

Also check [Comprehensive Multimedia & Video Howto]("http://ubuntuforums.org/showthread.php?t=766683").
Hmm, my browser choose to play with Totem, but can I change this to some other player that may work? Here is a link to some of what I'm trying to watch. 

[http://www.nrk.no/nett-tv/klipp/666827/](http://www.nrk.no/nett-tv/klipp/666827/)

From the menu on the left you're supposed to choose different elements of the program. I'm only able to pick the date for the program, and clicking anything beyond that just force the program to run from the start.

---

### Post by lovinglinux on 2010-09-17
> **ked said:**
> Hmm, my browser choose to play with Totem, but can I change this to some other player that may work? Here is a link to some of what I'm trying to watch. 

[http://www.nrk.no/nett-tv/klipp/666827/](http://www.nrk.no/nett-tv/klipp/666827/)

From the menu on the left you're supposed to choose different elements of the program. I'm only able to pick the date for the program, and clicking anything beyond that just force the program to run from the start.

You would have to remove totem plugin and install another. Nevertheless, it probably won't work. I tested it with gecko-mediaplayer and the result is the same. Probably that web site requires some functionality not availble in generic Linux media plugins.

---

