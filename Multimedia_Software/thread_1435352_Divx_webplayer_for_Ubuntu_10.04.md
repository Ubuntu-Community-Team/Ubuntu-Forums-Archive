---
title: "Divx webplayer for Ubuntu 10.04"
date: 2010-03-21
forum: Multimedia Software
---

### Post by teejay17 on 2010-03-21
I have searched the forums and can't find the specific answer, so I will post the question here with the hopes to solicit a response: 
I have installed Ubuntu 10.04 beta and it is currently "stock." I would like to watch Divx videos on websites using Firefox. What is the easiest and simplest way to do this? 
Thanks in advance.

---

### Post by lovinglinux on 2010-03-21
See [Comprehensive Multimedia & Video Howto]("http://ubuntuforums.org/showthread.php?t=766683")

---

### Post by teejay17 on 2010-03-21
> **lovinglinux said:**
> See [Comprehensive Multimedia & Video Howto]("http://ubuntuforums.org/showthread.php?t=766683")
But that's for 8.04...not 10.04...and it's really overwhelming. 
I just need the simple procedure for strictly for the Divx web-player.

---

### Post by 2hot6ft2 on 2010-03-21
I don't know about 10.04 but this works in 9.10
> **jocko said:**
> The videos on that site works fine with gecko media player (a browser plugin that uses gnome mplayer and mplayer).
To install it, remove any browser media player plugin you currently have installed (totem-mozilla is installed by default, but you may have installed mozilla-mplayer or mozilla-plugin-vlc):
```
sudo apt-get remove totem-mozilla mozilla-mplayer mozilla-plugin-vlc
```
Install gecko media player:
```
sudo apt-get install gecko-mediaplayer
```
Then restart firefox and try it out.
From this thread
[Problems with Divx]("http://ubuntuforums.org/showthread.php?t=1429015")

I've even been uploading some Benny Hill DVD rips to [http://www.stagevu.com/](http://www.stagevu.com/)

---

### Post by teejay17 on 2010-03-21
> **lovinglinux said:**
> See [Comprehensive Multimedia & Video Howto]("http://ubuntuforums.org/showthread.php?t=766683")
Okay, I went and followed the directions for Part 1 and Part 2, finally choosing the Gecko installation for my media streaming. 
It is this site that I would like to get going more than any other. Everything else works--java and the code I have to enter--just not the Divx streaming.

---

### Post by lovinglinux on 2010-03-21
> **teejay17 said:**
> Okay, I went and followed the directions for Part 1 and Part 2, finally choosing the Gecko installation for my media streaming. I am still not able to stream Divx movies, specifically the videos on [ninjavideo.net. ]("http://www.ninjavideo.net")
It is this site that I would like to get going more than any other. Everything else works--java and the code I have to enter--just not the Divx streaming.

It seems you need to run a specific tool from that site to view it. The tool is probably for Windows only.

Anyway, that site is hardly a legal one, so providing instructions on this forums is not allowed and thus I will refrain myself from providing additional support. Sorry.

---

### Post by teejay17 on 2010-03-24
> **lovinglinux said:**
> It seems you need to run a specific tool from that site to view it. The tool is probably for Windows only.

Anyway, that site is hardly a legal one, so providing instructions on this forums is not allowed and thus I will refrain myself from providing additional support. Sorry.
It's alright. I figured it out and it works amazing.

---

### Post by loveandequality on 2011-04-28
What did you do?

---

### Post by marl30 on 2011-04-28
> **loveandequality said:**
> What did you do?

```
sudo apt-get install gecko-mediaplayer
```

This plugin usually does a better job of handling Divx streams.

---

### Post by FOSScula on 2012-03-11
just wanted to confirm that > *gecko-mediaplayer* is working fine for streaming divx content from many sites in firefox :)  --dont forget to check your plugins in firefox and enable/disable as necessary. works on laptop and desktop Xubuntu 11.10 32bit  &  Ubuntu 11.10 64bit respectively..

---

### Post by teejay17 on 2012-03-13
> **FOSScula said:**
> just wanted to confirm that gecko-mediaplayer worked for us as well for streaming divx content from some other sites as well :)  --dont forget to check your plugins in firefox and enable/disable as necessary.  Running xubuntu 11.10
Forgot about this thread. Yes, the Gecko player is the best, just make sure you install all the plugins. 
I will now be marking this thread as solved.

---

