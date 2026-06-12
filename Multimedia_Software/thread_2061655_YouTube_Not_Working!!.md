---
title: "YouTube Not Working!!"
date: 2012-09-23
forum: Multimedia Software
---

### Post by Nathan1199 on 2012-09-23
The problem I am having is that when I try and watch YouTube Videos they all get speeded up. As you can from the Pic's Below the time(Top Left) elapses by 30 seconds but the video elapses 1 minutes and 16 seconds.

[ATTACH]224559[/ATTACH]

[ATTACH]224560[/ATTACH]

The same problem is true for other browsers(chromium). The Pic's Below Show the Same Problem but on Different Video and in Chromium.

[ATTACH]224561[/ATTACH]

[ATTACH]224562[/ATTACH]

Any help would be much appreciated.;)

---

### Post by orange2k on 2012-09-23
Some people had the same problem in this thread:

[http://ubuntuforums.org/showthread.php?t=1996584](http://ubuntuforums.org/showthread.php?t=1996584)

Some have fixed the problem by upgrading their graphics driver, which was in their case Nvidia...

Hope this helps...

---

### Post by Nathan1199 on 2012-09-23
Thanks That help. I have ATI Video Card.

---

### Post by exploder on 2012-09-23
There is a work around that would help you watch YouTube videos. First you need to enter a command into the terminal to fix a gstreamer bug with mp4's.

[http://www.webupd8.org/2012/06/fix-mp4-playback-in-ubuntu-1204.html](http://www.webupd8.org/2012/06/fix-mp4-playback-in-ubuntu-1204.html)

Next you need to add the MiniTube ppa repo and install the latest version of MiniTube.

[https://launchpad.net/~nilarimogard/+archive/webupd8](https://launchpad.net/~nilarimogard/+archive/webupd8)

I use MiniTube a lot even though I have no problems with YouTube and Flash. Your graphics drivers do appear to be the problem on your system and I am certain that you can resole it with the advice in the other responses. I wanted to give you the information about the mp4 fix and MiniTube because I thought it might help you out and you might like using it. I have really come to enjoy using MiniTube as it has some terrific features.

Edit: I did have problems with ATI graphics on my HP DV6 laptop. I got the graphics working by installing the ATI drivers with Jockey. The install failed, I rebooted, did the install again, they failed, rebooted again and the drivers were working even though Jockey said they were not installed. Not a very reliable solution by any means but before doing all of that every 3 or 4 boots I would get 9 login screens with lines through them and I had to do a hard reboot. Had this not happened with the open source drivers I would have just continued using them because when that problem did not appear they worked just fine. I am certain the advice given to you by the others in this thread should work better than my unusual solution, I just threw this out there in case nothing else worked for you.

---

