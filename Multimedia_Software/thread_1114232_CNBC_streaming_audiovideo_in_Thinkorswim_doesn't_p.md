---
title: "CNBC streaming audio/video in Thinkorswim doesn't play"
date: 2009-04-02
forum: Multimedia Software
---

### Post by FinFoot on 2009-04-02
Hello Everyone,

I am currently running gOS 3.1 (Ubuntu 8.04) on an older AMD machine with only minor problems.  I have installed Thinkorswim.com charting software for following the stock market by using Wine.  Everything works except for the CNBC streaming audio/video media player.  I have installed VLC media player for the stream but I get NO audio or video.  Any suggestions?  Thanks in advance.

---

### Post by ssc351 on 2009-04-08
So I was having the same issue and went on the live help.  The gave me the mms feed so you can play it in VLC or mplayer but I guess the link changes on a daily basis.  So no luck...I put in a request to make in linux available but since its a microsoft feed...ya you get the idea.  

The windows version uses an integrated windows media player with an mms feed.

Maybe if enough people put requests in something will happen but doubtful.

---

### Post by twdsje on 2009-09-21
I have a solution for this issue.  I figure I might as well post it despite how old this post is since I kept running across this page in my google searches.  I can't get thinkorswim desktop to work on my machine at work because of our firewall.  So I don't know anything about getting the player in the desktop application to work.  However, you can also access CNBC+ TV through ThinkorSwim's web based trading:

Make sure you install VLC media player with the plugin:

sudo apt-get update
sudo apt-get install vlc vlc-plugin-esd mozilla-plugin-vlc

Then all you need to do is log in to thinkorswim's web based trading.  Look in the upper left corner of the page.  There's a little tab with an arrow on it.  Expand that.  A sidebar similar to the one in the desktop app opens.  Click the hammer/wench icon on the gadget in the sidebar and change it to CNBC TV.

Hope that helps!

---

### Post by celem on 2009-12-03
It is not necessary to leave the desktopclient and login to thinkorswim's web based trading to view the video. There is an icon on the desktop client's video display that, when clicked, opens up a browser window with the video streaming away for you. See my attached partial screen capture.

PS: What is with the "using Wine" comment? Why not run the native Linux version from thinkorswim?

---

### Post by efflandt on 2009-12-03
Does thinkDesktop for Linux work in 64-bit, or only 32-bit?

---

### Post by celem on 2009-12-03
I am running amd64 - works fine. It is java based so it shuld run on most anything.

---

### Post by celem on 2009-12-03
Another thought - a couple of minor tweaks are required. Read:
[http://ubuntuforums.org/showthread.php?t=1345069](http://ubuntuforums.org/showthread.php?t=1345069)

---

### Post by josephuser on 2010-04-16
This still doesn't work.  I think one of the packages mentioned above are no longer included in Ubuntu Desktop 9.10.  Web version gives error when trying to play a .m3u file.  Help?

---

### Post by ssc351 on 2010-05-04
yo, not sure if this helps or not, but I had the same problem. I contacted the think or swim support desk and they said it wasn't supported for linux.  He also mention something about microsoft controlling the feed...not sure about that one.  But he also gave me the link which i was able to use with vlc, but i guess the link changes every couple of days.  So it stopped working eventually.  But give support a try and see if they will help

---

