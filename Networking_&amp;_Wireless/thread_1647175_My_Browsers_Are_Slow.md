---
title: "My Browsers Are Slow"
date: 2010-12-16
forum: Networking &amp; Wireless
---

### Post by Smallwheels on 2010-12-16
Months ago I installed Ubuntu 10.04. Firefox was so slow that it took 54 seconds to open a new page on a web site. I downloaded Opera. It had the same problem. I put it all aside for a few months. When I went back to the computer and installed one of the updates that came out over the past few months, both browsers had sped up to near normal speeds for a slow computer using Windows. I know Ubuntu is faster than Windows. 

My computer is an HP 2.3 GHz AMD Sempron LE1300 with 2 GB RAM. Firefox works faster on the Vista partition (this is dual booted with Vista). I want to get the browsers working at a normal speed. I expected that speed to be at least as fast as the Vista side. 

Before I go any farther down this road of repair I want to try uninstalling Opera and Firefox and reinstalling them. Since this is my first foray into Linux I need to learn how to do this one browser at a time. I didn't see either of these in the software center with the remove buttons so how do I do it? 

This seems like a logical step to getting them working faster. Now that the previous update fixed something to speed them up a bit, maybe reinstalling them will get them working properly. If this works then I can finally start using Ubuntu as my main OS. 

Thank you for your help.

---

### Post by Smallwheels on 2010-12-18
Was this question too basic? Is everybody assuming that it is so easy that someone else will reply?

Any proper answer will do. I'll report the results after I reinstall the browsers.

---

### Post by chili555 on 2010-12-18
> **Smallwheels said:**
> Was this question too basic? Is everybody assuming that it is so easy that someone else will reply?

Any proper answer will do. I'll report the results after I reinstall the browsers.You clearly said, in your first post that, "Before I go any farther down this road of repair I want to try uninstalling Opera and Firefox and reinstalling them." I think we are waiting for the result before we propose a solution. Was that not what you meant?

Of course, I imagine the more experienced guys are doubting it's an issue with the browser at all and that there is an issue with the network card's driver or, perhaps, the DNS servers.

In this post, you've said you'll report after you reinstall the browsers. Again, the ball seems to be in your court, not ours.

If you'd like to explore the driver and DNS, Please open a terminal and post:```
sudo lshw -C network
cat /etc/resolv.conf
```

---

### Post by Smallwheels on 2010-12-18
Here is what I wrote "Before I go any farther down this road of repair I want to try  uninstalling Opera and Firefox and reinstalling them. Since this is my  first foray into Linux I need to learn how to do this one browser at a  time. I didn't see either of these in the software center with the  remove buttons so how do I do it?"

Once I know how to remove these browsers one at a time and reinstall them I'll be able to report what happened. Remember that I wrote that on this same computer Firefox and a different browser work much faster on Vista. That means the signal is still going through the same DSL modem and doing a much faster job. That is why I know that the problem is within Ubuntu. 

I'll try that other command in terminal once this is out of the way. If they're still slow then with your help this problem will be figured out and fixed.

---

### Post by chili555 on 2010-12-18
If you are unwilling to accept the possibility that the browser is not actually the problem, then here is what you do. Open System > Administration > Synaptic. Search for firefox, mark it for complete removal and press Apply.

I assume you downloaded the .deb file for Opera. Open Applications > Accessories > Terminal.

By default, downloads go to either Downloads (for later Ubuntu versions) or your desktop. In the terminal, do:```
cd Desktop
```Substitute Downloads if that's where the .deb file is located. Next, do:```
sudo dpkg -P opera
```We will await your further report.

---

### Post by Smallwheels on 2010-12-18
I found the Firefox file where you said it would be. Thanks. It seems that there are many other things associated with Firefox within this application. If I select it for removal a window comes up saying other things will be removed too. 

If they are removed and I go to the Mozilla site to download the program again, will these other programs also come with it or must they come from Ubuntu again?

---

### Post by chili555 on 2010-12-18
They will not come with the Mozilla package and certain features may not work properly. The version in Ubuntu is fine-tuned for Ubuntu. If networking is working correctly (ahem!), Firefox is plenty fast. The downloaded one-size-fits-all version is likely to be no better and possibly not as good.

---

### Post by TBABill on 2010-12-18
Ok, I just downloaded Opera 11 and it flies. I use Chromium from the repo and it is as fast. However, a default Firefox install is just incredibly slow (scrolling in particular) and I have 4GB RAM and a core i3 CPU. So I followed this link and followed the optimization steps and Firefox flies as well now. I wish it were fast by default, but it's just not. But this can help... [http://ubuntuforums.org/showthread.php?t=1193567&highlight=firefox+optimization+thread](http://ubuntuforums.org/showthread.php?t=1193567&highlight=firefox+optimization+thread)

---

### Post by Smallwheels on 2011-03-24
With the latest Firefox version being available I've updated all of the browsers on my computer using 10.04. Now all of them are working as fast as they are supposed to work. 

Something was wrong with their initial installation with the ISO file, otherwise why would all of them be slow until updates to them were made available? 

Here is a link to a thread that gives good instruction on how to get Firefox 4 working on Ubuntu: 

[http://ubuntuforums.org/showthread.php?t=1712298](http://ubuntuforums.org/showthread.php?t=1712298)

It is almost time for me to transition away from my Mac Book and move to Ubuntu on my HP that is dual booted with Vista. I still need Microsoft to run some programs and watch the streaming video from Netflix' Starz Cable channel. 

I have two more problems to overcome with Linux. One is to find a way to synchronize all of my bookmarks/favorites between all computers. Chrome failed in this regard. I'll try the new Firefox and see if it can do a better job.

The other thing is to get a feature I love on my Mac Book on Ubuntu. Leopard can magnify the entire screen by pressing the control key with the scroll wheel (or button depending on the mouse). I love doing that. It is much better than magnifying a single browser window that then needs to be manipulated with the scroll bars to center the magnified part of the screen I want to view.

---

### Post by Naggobot on 2011-03-24
> One is to find a way to synchronize all of my bookmarks/favorites between all computers.


I might recommend using some web based bookmark system. Fancy term might be "cloud".  

I personally use [Diigo ]("http://www.diigo.com")but I do not know if better alternatives are available. 

Might be a good issue for another thread.

---

### Post by mdshann on 2011-03-24
Maybe there was a problem when you burned the CD. Did you burn it at the slowest speed possible? Another thought that comes to mind is when you did updates there may have been an update to the networking drivers or DNS that fixed the issue. I doubt that either browser was at fault if the problem occurred in both of them.

I believe chrome allows you to sync your bookmarks to your google account and then you attach all your chrome installs to your account. I used to use Foxmarks add on in Firefox to sync the bookmarks on all of my Firefox installs. Not sure if this is still around.

---

### Post by Smallwheels on 2011-03-27
> **mdshann said:**
> Maybe there was a problem when you burned the CD. Did you burn it at the slowest speed possible? Another thought that comes to mind is when you did updates there may have been an update to the networking drivers or DNS that fixed the issue. I doubt that either browser was at fault if the problem occurred in both of them.

I believe chrome allows you to sync your bookmarks to your google account and then you attach all your chrome installs to your account. I used to use Foxmarks add on in Firefox to sync the bookmarks on all of my Firefox installs. Not sure if this is still around.

There was a problem with burning the ISO DVD. I don't recall which recorder I used but it malfunctioned. There was a place for me to select the speed but it wouldn't allow me to make the selection. I could move my cursor over the speed selection but it wasn't recognized as a functioning button. When the disc was burning there was a box showing the recording speed at maximum speed instead of the slowest speed. 

I downloaded 10.04 about two months after it was available. With the problems I was having with it I just left it alone for long periods of time. I only came back to it when I was in the mood to fool with it. Sometimes a month or two would go by. 

Within one of those times there were some huge updates done. One of them changed the way Ubuntu appeared when it opened. It added Gnome and some other boxes to the bottom of the opening screen. It was when that occurred that the browsers sped up from taking 54 seconds to change pages to just 12 seconds. It was a huge improvement but still three to five times slower than my other computer. 

When Opera 11 was available I downloaded it and Opera began to run fast. I downloaded Chrome and it worked fast from the start. Only when Firefox 4 became available did it too begin to operate normally. 

Chrome bookmarks won't sync with my bookmarks on my other computer. The bookmark folders that get transferred are all empty. I'm disappointed. 

Opera just doesn't work on some sites and nobody has been able to help me get Quicktime videos to play on it.

Dropbox is working just fine between the Mac Book and the HP Ubuntu OS. Yay something works right the first time it is installed ...so far.

---

