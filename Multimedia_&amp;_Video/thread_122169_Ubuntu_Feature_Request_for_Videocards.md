---
title: "Ubuntu Feature Request for Videocards"
date: 2006-01-26
forum: Multimedia &amp; Video
---

### Post by SuperMike on 2006-01-26
I was sharing the Ubuntu experience with a coworker. He was impressed when he installed it on an older PC. Made it really zippy and the video looked fantastic. But then we decided to make it really powerful and install it on the latest, greatest IBM PC. Unfortunately we only had the 5.04 Ubuntu disc with us, so he would have to install that first and then I would show him the sources.list/apt-get dist-upgrade trick to move him to 5.10 Ubuntu.

The problem was that on the first go around where we took the newer IBM and got it to Ubuntu 5.04, the video would only go as far as 24 bit 600x480. It was almost not usable. Anything less than 800x600 these days is pathetic. I was embarassed because here I was bragging about the brilliance of Ubuntu. It was also embarassing as I had to *gasp* edit the confusing xorg.conf file by hand in order to try and put the video in 16 bit 800x600 (or hopefully higher) mode. Of course, that didn't work and I had to do CTRL+ALT+BACKSPACE, killall gdm, and gdm &, in order to try settings over and over again. After awhile, I told my friend in an Oz-like manner, "Look not to the man behind the curtain!" Man, that was embarassing.

Luckily, he had the wits about him to say, "Dude, why don't you just upgrade to 5.10 and see if that has better drivers?" Like, duh, what a smart one he was for never knowing Ubuntu before. Sure enough, that trick worked and I could take this brand spanking new IBM all the way to 24 bit 1024x768 and even a few steps higher in resolution.

So, what's my point? My point is that there needs to be a newbie-ready control panel or yast-like command tool one can load to attempt to try the video mode in a variety of settings to see if it will work. In order to bring Linux to a wider audience besides geeks like me, Ubuntu newbies should not have to learn the nasty guts of xorg.conf or know keystrokes like CTRL+ALT+BACKSPACE inside of X or even have to kill gdm and restart it again. There should be a handy little program that lets you do that quite easily.

In fact, I'd like to see that program as a default on a future Ubuntu. Also, if Ubuntu detects that it has gone into 8 bit color mode, or 640x480 video, it would be nice if the Ubuntu gnome desktop would automatically prompt, "Your video settings appear lower than standard. Do you wish to experiment with higher settings? You can always get back to these settings if this fails. [ ] Never prompt me again. [Yes] / [No]"

Do you agree?

---

### Post by SuperMike on 2006-01-26
In fact, as I think about this, I could almost build this thing myself. It would work like this:

1. You open the control panel in GNOME. I would build it with PyGTK (using Glade2 to help, of course). I've even got a skeletion PyGTK control panel script that I could edit and remake as this. I could call this like "Enhance Video Settings".

2. The control panel menu item actually would call a bash script that would call Python and load the PyGTK control panel script. I could use gksudo before that so that I could give this control panel some root access power.

3. The control panel would automatically scan the /etc/X11/xorg.conf file and show you what resolution and video mode you're in. It would then have a button beneath it that would say "Test Enhanced Video Settings".

4. Clicking that button, it would warn/prompt you that it needs to log you out and wants to know if you want to close your apps. If you choose yes, it would do "killall gdm" and throw you into a console-based menu (done with an ordinary Bash script and some VT100 commands to draw the screen nicely).

5. Once in the console-based menu, you could choose from a series of menu items showing you all the possible color depth/video resolution combos above 8 bit and 640x480. When you hit enter, it would backup your /etc/X11/xorg.conf file (using a time/date stamp) and edit it with these settings. The only xorg.conf section needing changing would be "Screen", for the most part. It would change it and then call "gdm &". 

6. It would then wait in the background to see if you logged in within so many seconds. If you did not, then it would assume your video settings did not work and it would do "killall gdm". Then, it would bring you back to the console menu.

7. If, however, you did login, it would automatically throw open the control panel again. And, you could either close it and it would not reopen on login again, or you could click the button on it to see if it could attempt another color depth/resolution change. At this point, you fall back to step 4 again. 

8. If you click the X (or Cancel) on the control panel instead, it would bring you to your Ubuntu desktop and leave you alone.

---

