---
title: "Mythbuntu, or Ubuntu with Myth Installed?"
date: 2009-03-17
forum: Mythbuntu
---

### Post by AboveTheLogic on 2009-03-17
Hi all-

I've been reading and reading about how I want to build my HTPC. I've decided that I will run Linux with Myth TV. I've been using Kubuntu for a little while now and am pretty familiar with it. I loaded Mythbuntu onto a virtual machine to test it out and I like how lightweight it is.

My issue, though, is that my HTPC will not just be an HTPC. It will also be a file server, and will handle my torrents. So, I plan to have it boot into a 'myth' user on the console session for the TV, and I will access another user in another session to handle the other tasks, like running Vuze. I will probably use FreeNX for this.

My current decision is how I want to go about this route. I can simply install Mythbuntu, add another user, and start adding packages.... OR I can just install k/ubuntu and add the myth package, then somehow configure the myth account to auto-login and launch mythtv.

I'm leaning towards the latter, but am wondering if anyone can give me reasons to go with the former.

Thanks!

---

### Post by nickrout on 2009-03-17
> **AboveTheLogic said:**
> Hi all-

I've been reading and reading about how I want to build my HTPC. I've decided that I will run Linux with Myth TV. I've been using Kubuntu for a little while now and am pretty familiar with it. I loaded Mythbuntu onto a virtual machine to test it out and I like how lightweight it is.

My issue, though, is that my HTPC will not just be an HTPC. It will also be a file server, and will handle my torrents. So, I plan to have it boot into a 'myth' user on the console session for the TV, and I will access another user in another session to handle the other tasks, like running Vuze. I will probably use FreeNX for this.

My current decision is how I want to go about this route. I can simply install Mythbuntu, add another user, and start adding packages.... OR I can just install k/ubuntu and add the myth package, then somehow configure the myth account to auto-login and launch mythtv.

I'm leaning towards the latter, but am wondering if anyone can give me reasons to go with the former.

Thanks!

I would use mythbuntu and then add whatever else you like. k/ubuntu adds stuff you will never need.

When you set up mythbuntu you DO add another user (like a normal install). That user runs the frontend and mythtv user runs the backend. "user" can do other things as well, and I log in as user over ssh and run bittorrent clients that way (usually rtorrent, a command line client, very good too). I run rtorrent under screen so I can log out and back in again and rtorrent is still running.

---

### Post by AboveTheLogic on 2009-03-17
I do like the idea of having a minimal OS that does just what I want it to do.

I'm a big fan of KDE, but not so much of a fan of all the crap that comes along with it. I would like a simple KDE interface with a few things like firefox, thunderbird, and bit torrent... nothing else.

What you are saying about one user running the front end and another running the backend is interesting... on the test box I ran I didn't notice that. I saw that one user logged in and ran the front end... and honestly, I'm not sure how the backend was being run, I'm still new to myth.

I'm also toying around the idea of only running myth back end on the box and XBMC on the console session with the myth plugin... and simply doing most of the admin remotely with a laptop. My wife really likes and is used to XBMC. XMBC will do live TV, guide, and watch recordings.... all that it won't do is schedule recordings.

SO MANY OPTIONS!

Thanks for the feedback, I'll do some more thinking.

Anyone got any info on how I can install the latest version of KDE on myth for remote sessions WITHOUT also installing the bundled stuff that goes along with it?

Also, I'm wondering if there would be a simple way with a remote to switch back and forth between myth front end and XBMC front end, maybe by switching from tty1 to tty2. I plan to research this as well...

---

### Post by nickrout on 2009-03-17
1. you do not need kde on a machine you sit 10 feet away with and control via a remote.

2. You can set up a menu entry on your mythfrontend to run xbmc. When you exit xbmc you will return to the frontend. Alternatively you can just run xbmc on login and forget mythfrontend (if you are so inclined). mythbox (the xbmc plugin to access myth) does support scheduling, and so does mythweb. 

3. I am not sure how you distinguish "kde" from "bundled stuff". Apart from the fact that kde (or any desktop manager) is a waste of time on a myth machine, you need to work out what you actually want, and simply install it vis apt-get, aptitude or any of the other pacakage managers.

---

### Post by AboveTheLogic on 2009-03-17
I do not intend to use KDE from the TV, but I would like to use it when logging in to the background session remotely with FreeNX.

I'm happy to hear that I can launch XBMC and return to MythTV with the remote, that sounds like a good way to go. 

I read elsewhere that XBMC didn't support scheduling for MythTV yet, but what I was reading could have been outdated, I'll definetely give it a try. Mythweb is what I meant when I said I would do admin from a laptop.... I guess I wasn't very clear on that.

What I mean by bundled stuff, is when I installed KDE on my gnome-based ubuntu install in the past, a lot of KDE applications came with it. I don't remember the names, but it was applications like a browser, email client, IRC, etc. etc.... all things I do not want. 

If I can, I'd like to simply get the KDE desktop, with just a few apps, so I can use that remotely.

Maybe I will just scrap the whole idea if I end up liking the desktop environment that mythbuntu has.

Thanks for the input.

---

### Post by nickrout on 2009-03-17
[http://code.google.com/p/mythbox/](http://code.google.com/p/mythbox/)

> Beta 1 (SVN 851) Released
       Changelog

    * new : recording schedules can now be created from the 'TV Guide' screen by clicking on a program
    * new : recording schedules can now be edited from the 'Recording Schedules' screen 

Installing just bits of kde is not something I can help with. you could try installing kde-core but I am not sure if that will give you enough. 

Why not stick with the desktop provided by mythbuntu and add the apps you want? Logging in graphically to a myth system should be rare enough that you can surely put up with xfce (its really not bad).

Why not do your torrenting over ssh?

---

### Post by AboveTheLogic on 2009-03-17
Wow, great! Well, if XBMC can do all that, I may not even have use for the myth front end at all... I'll still play with it though.

kde-core, ay? If that will give me just the environment with the menus (similar to the xfce that comes with myth), that might just be what I'm looking for. I'll have to try it on my test machine.

Honestly, for me, logging into the myth system graphically is something that I would do everyday. Usually, I do it from work when I'm bored so I can play around (current its a windows box). Also, I forgot to mention, I will need DVD-DL burning support that I can do from this remote session, and probably other things I'm not remembering now (which is why I was considering ubuntu with myth installed).

torrenting over ssh... I haven't tried it and don't know much about it, but I'm not sure it sounds very interesting to me... I haven't been a fan of command based torrent clients in the past

---

### Post by AboveTheLogic on 2009-03-17
Ahh, I installed kde-core on my virtual mythbuntu test machine and it works fine.

The default user (myth) can log into KDE and still load mythtv. I need to play with it a bit more because KDE takes longer to load... I would like the myth user to log into xfce, and my other user to log into kde via NX. 

I do, indeed, have a stripped down KDE desktop with only a few things installed, and I can just install the few items I want/need.

Thanks for the help, I'm definetely on the right track. I'm sure I'll be doing some more reading about handling sessions properly, though.

---

