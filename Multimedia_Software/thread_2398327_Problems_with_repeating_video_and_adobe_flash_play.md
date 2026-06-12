---
title: "Problems with repeating video and adobe flash player"
date: 2018-08-10
forum: Multimedia Software
---

### Post by numberman768 on 2018-08-10
I have two problems with playing videos. Different problems for different media players I guess.

The first problem is that when I watch videos it will play for ~20 seconds and then go back to the start, again and again. If I try to skip forward it just replays that ~20 seconds from the start. It didn't do this before the last time I updated software which was 2 days ago (done through ubuntu software)

The second problem is that when I try and watch videos on twitch it says I have to click to allow Flash player to work. However when I try and click it does nothing and I can't watch the video. I have flash player enabled by default so I shouldn't have to click it. This happens on different websites too. I have even tried adding them as exceptions but still the problem persists. This also wasn't a problem until I last updated software. According to [https://helpx.adobe.com/flash-player.html](https://helpx.adobe.com/flash-player.html) I have the latest flash configured properly but clearly something is wrong.

If anyone can help it'll be appreciated, getting rather annoying not being able to sort it out.

Browser: Problem happens in them all but i'm using opera
OS: Ubuntu 18.04

---

### Post by Dennis N on 2018-08-10
> The second problem is that when I try and watch videos on twitch it says I have to click to allow Flash player to work. However when I try and click it does nothing and I can't watch the video. I have flash player enabled by default so I shouldn't have to click it. This happens on different websites too. 

Change permissions on the web page with flash content from "ask" to "allow" flash: 
In FF, right-click on web page > View Page Info > Permissions > Run Adobe Flash > (uncheck) "use default" and check "allow".

---

### Post by numberman768 on 2018-08-10
> **Dennis N said:**
> Change permissions on the web page with flash content from "ask" to "allow" flash: 
In FF, right-click on web page > View Page Info > Permissions > Run Adobe Flash > (uncheck) "use default" and check "allow".

What you said about firefox got the sound to play but the video displays only a black screen. As for Opera It still wants me to click to allow when it is checked "allow" in settings and as a result doesn't work.

Thanks for replying.

---

