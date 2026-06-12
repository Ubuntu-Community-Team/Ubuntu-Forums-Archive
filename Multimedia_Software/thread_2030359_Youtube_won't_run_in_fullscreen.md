---
title: "Youtube won't run in fullscreen"
date: 2012-07-20
forum: Multimedia Software
---

### Post by chris282 on 2012-07-20
Using Ubuntu 12.04 on single monitor.  Clean reinstall yesterday, have been messing about getting things to work since then, so I'm sure I've done something to muck it up, but no idea what.  Watched Youtube video in fullscreen earlier today, can now expand but will not extend to fullscreen.  Thoughts/ideas?

---

### Post by shantiq on 2012-07-21
maybe try   right click on youtube video while it plays /settings / untick hardware acceleration


see if that helps

---

### Post by chris282 on 2012-07-21
Thanks shantiq, but that hasn't made a difference.

Additional: I am only experiencing this problem when using Chrome browser, not Firefox.

---

### Post by NikTh on 2012-07-21
Hi , 
try to use youtube/html5  , and see if fullscreen works there. 
Go here --> [http://www.youtube.com/html5/](http://www.youtube.com/html5/) and click "Join the html5 Trial" , then click at Youtube's logo and try to see a video in fullscreen. 
If this work , then probably its a problem with adobe flash player settings.

Regards

---

### Post by chris282 on 2012-07-21
Hi Nik.  I have joined the trial, but no change.

---

### Post by NikTh on 2012-07-21
> **chris282 said:**
> Hi Nik.  I have joined the trial, but no change.

Hi , 

what is the behavior when you click fullscreen mode ? and what browser you use ? 
Is this problem related to youtube only ? 

Regards

---

### Post by chris282 on 2012-07-22
When I click fullscreen the Youtube screen flickers and goes blank, and then returns at the same size.  

The same things happened when I tried to watch video at the BBC iPlayer website - [http://www.bbc.co.uk/iplayer/](http://www.bbc.co.uk/iplayer/).

I am using Chrome.  This doesn't happen using Firefox.

---

### Post by NikTh on 2012-07-22
> **chris282 said:**
> When I click fullscreen the Youtube screen flickers and goes blank, and then returns at the same size.  

The same things happened when I tried to watch video at the BBC iPlayer website - [http://www.bbc.co.uk/iplayer/](http://www.bbc.co.uk/iplayer/).

I am using Chrome.  This doesn't happen using Firefox.
Hi , 

Ok , then . I understand this is a specific problem with Google Chrome browser . 
**You didn't mention this in your fist post !**

You can wait someone who knows better the Google Chrome browser to help you. 
I don't use Google Chrome. (i prefer Chromium , FF and Iceweasel) 

Thanks

---

### Post by chris282 on 2012-07-22
I mentioned it in the second post, but thanks for your help anyway.

---

### Post by linux_paul on 2012-07-23
This worked for me:

> so the issue I am having the newest flash plugin is causing the issue which version 11.3

That being said what you need to do is go to chrome://plugins in your browser and disable all the flash plugin and re-enable the previous version which is 11.2


Source: [http://askubuntu.com/questions/161353/ubuntu-12-04-fullscreen-video-dual-screen](http://askubuntu.com/questions/161353/ubuntu-12-04-fullscreen-video-dual-screen)

---

### Post by viperdvman on 2012-07-26
> **linux_paul said:**
> This worked for me:




Source: [http://askubuntu.com/questions/161353/ubuntu-12-04-fullscreen-video-dual-screen](http://askubuntu.com/questions/161353/ubuntu-12-04-fullscreen-video-dual-screen)

I actually had a different problem with my Chrome v20. I run dual displays on my Ubuntu, KDE desktop environment installed on top of it. My problem in with YouTube in Chrome was that when I went to fullscreen, no matter which of my 2 monitors I had the window on, it would only show the left half of the full-screen video on the right side of the screen. Sucks big time. And Chrome was the only browser I had this problem in. In Firefox, it worked just fine.

So I went into **chrome://plugins** and disabled the Flash 11.3 plugin and enabled the Flash 11.2 one (you have to click on "+ Details" on the right hand side of Plugins to see it). And that fixed that problem completely.

So in your case, Flash is most likely the culprit and not Chrome.

Goes to show how much Flash can suck sometimes.

---

### Post by nealmcb on 2012-08-22
Thanks - [http://www.youtube.com/html5/](http://www.youtube.com/html5/) worked for me.

I'm using these versions:
  tools/about chrome: Version 21.0.1180.81 beta
chrome://plugins/
 Shockwave Flash Version:	11.2 r202

Of course that won't help with other sites that are still using that cursed blot on the open web called flash....

---

### Post by donjoe0 on 2012-11-17
Actually what solved it in my case was *leaving* the HTML5 trial that I was already enrolled in. :)

---

