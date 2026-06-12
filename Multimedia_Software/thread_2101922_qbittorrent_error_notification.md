---
title: "qbittorrent error notification"
date: 2013-01-05
forum: Multimedia Software
---

### Post by yadayada2 on 2013-01-05
Dear all

I have a problem with qbittorrent. Actually it works great. But sometimes, when I select some files from a torrent for download and other I select not, at some point qbittorrent halts the download and states that one of the files or directories, which I never wanted to download anyway is not there. So it gives me an I/O error. I don't mind that.

But what bothers me is that annoying notification field in the upper right corner of my screen, which states this error notification. It shows up, holds for a few seconds, then briefly disappears and is back there within 2 or 3 seconds. I have killed qbittorrent (even via killall). I checked ps -ax with grep, but there was no qbittorrent threat left. But this damn notification keeps coming until I log out and in again.

Can you tell me how to get rid of that stupid field when it comes up again?

Best regards

---

### Post by yadayada2 on 2013-01-09
Does no one have a clue?

---

### Post by eagleestar on 2013-06-07
Ubuntu 13.04

I'm was having the same issue I think, but fixed it. 

It gave yeah some sort of I/O error and then the name of the torrent plus path. I figured it gives me error because I was downloading to my slave hard drive which I didn't open up (mount?) before starting up Qbttorent. So the root of the problem I think its that you tell it to download to a "non existen" location. 

I had the infinite loop popup I/O message even after opening up the slave hard drive, even after it was downloading. 

Fix: 

Go to the application System monitor, then the processes tab and close *************

I forgot specifically which one I closed but it was not a Qbttorent one, I think it said Infosomething. You'll see it, just try a few. 

Before that the only solution was to restart ubuntu.

---

### Post by eagleestar on 2013-08-13
> **eagleestar said:**
> I think it said Infosomething. You'll see it, just try a few. 

This happened to me again today. The application to kill is called notify-osd
Once you kill it the pop up goes away.

---

