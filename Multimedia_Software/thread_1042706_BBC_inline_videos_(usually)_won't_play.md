---
title: "BBC inline videos (usually) won't play"
date: 2009-01-17
forum: Multimedia Software
---

### Post by IainPurdie on 2009-01-17
First, the problem. On the BBC News page, I see the image to "click here" with the iPlayer logo in the middle. I click on it and the video clears, to be replaced by the typical Flash "dots in a circle" logo telling me (theoretically) that the file is buffering. In the status bar, I get "Transferring data from visualscience.external.bbc.co.uk".

And that's it. I've left videos for quite literally *hours* and they've never started.

Having said that, once in a blue moon one of them plays. Time and time again. Works like a charm. But I'd say it's maybe one in twenty or less.

I'm running Hardy with the latest version of Firefox (3.0.5). Plugins I have installed are:

Default Plugin
Demo Print Plugin for unix/linux
DivX Broswer Plug-In
Java Plug-in 1.6.0_07-b06
mplayerplug-in 3.50
QuickTime Plug-in 6.0 / 7
RealPlayer 9
Shockwave Flash 10.0 r15
Windows Media Player Plugin 3.50

Any thoughts?

---

### Post by hansdown on 2009-01-17
Hi 
IainPurdie.
There are some helpful links .

[http://www.google.ca/search?q=bbc+videos+in+ubuntu+8.04&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.ca/search?q=bbc+videos+in+ubuntu+8.04&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

---

### Post by RJARRRPCGP on 2009-01-17
> **IainPurdie said:**
> First, the problem. On the BBC News page, I see the image to "click here" with the iPlayer logo in the middle. I click on it and the video clears, to be replaced by the typical Flash "dots in a circle" logo telling me (theoretically) that the file is buffering. In the status bar, I get "Transferring data from visualscience.external.bbc.co.uk".

And that's it. I've left videos for quite literally *hours* and they've never started.

Having said that, once in a blue moon one of them plays. Time and time again. Works like a charm. But I'd say it's maybe one in twenty or less.

I'm running Hardy with the latest version of Firefox (3.0.5). Plugins I have installed are:

Default Plugin
Demo Print Plugin for unix/linux
DivX Broswer Plug-In
Java Plug-in 1.6.0_07-b06
mplayerplug-in 3.50
QuickTime Plug-in 6.0 / 7
RealPlayer 9
Shockwave Flash 10.0 r15
Windows Media Player Plugin 3.50

Any thoughts?

I dunno what to say except that it's often caused by internet connection problems, often because your internet connection degraded. 
You may have a bad router or cat cable.

---

### Post by IainPurdie on 2009-01-17
I've been through about 6 tutorials and so far have only succeeded in taking up about an extra 100Mb in hard drive space and breaking the QuickTime plug=ins so that I can't watch the trailers on the Apple site any more...

And the network connection is definitely not the issue. The problem's followed me from the UK to France and across 6 resorts, using wi-fi and cabled connections (with different cables). Given that it's only the BBC site and that I can access every other website with no issues, I doubt that's the problem.

*sigh*

:(

---

### Post by IainPurdie on 2009-01-19
Strange. Done a reboot and now they all seem to work, I assume as a result of one of the many things I ended up downloading and installing.

Mind you, now my Quicktime videos won't play inline... But I guess that's more fiddling and another thread!

---

### Post by hansdown on 2009-01-19
I'm sorry to give you another tutorial IainPurdie.

Just trying to help.

[http://rclermont.blogspot.com/2008/01/quicktime-video-in-firefox-on-ubuntu.html](http://rclermont.blogspot.com/2008/01/quicktime-video-in-firefox-on-ubuntu.html)

---

### Post by IainPurdie on 2009-01-19
Help is always appreciated! Sadly, the "gstreamer0.10-gl" package mentioned in the link you pointed at isn't in any repository that I'm scanning. The post is also from a few months ago and if there's one thing I've spotted it's that video format problems seem to change every couple of weeks. It's best to look for a very recent fix.

---

