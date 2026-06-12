---
title: "Vedio steam on one website not working"
date: 2009-07-25
forum: Multimedia Software
---

### Post by niceguy123 on 2009-07-25
Can someone help me figure out how to view this clip [http://www.jpost.com/servlet/Satellite?cid=1248277878283&pagename=JPost%2FJPArticle%2FShowFull](http://www.jpost.com/servlet/Satellite?cid=1248277878283&pagename=JPost%2FJPArticle%2FShowFull)

Other sites like youtube work fine on my browser, when I click this one it opens a new page with totem plug in but doesn't play the clip. I can't figure out what format its in or how to download it ether.

---

### Post by HappyFeet on 2009-07-25
I have every codec and use mplayer plugin, and it does not work for me either. There are a few streaming videos that will not play in linux. That is why I have XP installed in virtualbox, so I can watch NFL Network streaming. Oh well. Wish I could help more, but it probably won't work.

---

### Post by niceguy123 on 2009-07-25
> **HappyFeet said:**
> I have every codec and use mplayer plugin, and it does not work for me either. There are a few streaming videos that will not play in linux. That is why I have XP installed in virtualbox, so I can watch NFL Network streaming. Oh well. Wish I could help more, but it probably won't work.

Now that you bring that up. What do you suggest as the best option for running programs that need MS windows? Is virtulbox better then running wine or dual boot?

---

### Post by ajgreeny on 2009-07-25
The link you provided played OK on my jaunty box.  It seems that the stream is a WMV windows video. I got that information from the media tab of "Page info" in the Tools menus of firefox, so it should play OK for you too if you have the full w32codecs installed, and use the gecko-mediaplayer plugin instead of the (in my opinion) pretty useless totem plugin that's in firefox by default in ubuntu.

Try using that and see if it helps.

---

### Post by HappyFeet on 2009-07-25
> **niceguy123 said:**
>  Is virtulbox better then running wine or dual boot?

I think it is. Just make sure to get virtualbox from the website and not from the repos. [Download Virtualbox]("http://www.virtualbox.org/wiki/Linux_Downloads") Allocate as much memory as you can for windows (including video memory). I have tons of memory and a quad core cpu, and XP runs as well as a regular install. If you install guest additions after you install windows, you can get full screen as if it was a real install. 

I have 2 monitors and run xp on 1, and linux on the other. That way, xp does not get in the way of my "real work". If you have any questions about vbox, PM me or ask in the appropriate forum.

---

### Post by HappyFeet on 2009-07-25
> **ajgreeny said:**
> The link you provided played OK on my jaunty box.  It seems that the stream is a WMV windows video. I got that information from the media tab of "Page info" in the Tools menus of firefox, so it should play OK for you too if you have the full w32codecs installed, and use the gecko-mediaplayer plugin instead of the (in my opinion) pretty useless totem plugin that's in firefox by default in ubuntu.

Try using that and see if it helps.

I have (in my case) the w64codecs *and* gecko media player installed and it won't play for me. :-k

---

