---
title: "Flash player 9/10"
date: 2009-01-16
forum: Multimedia Software
---

### Post by xnerdx on 2009-01-16
(Umm I kinda posted this in the wrong section:) can anyone here help)

Hey, in the past with my 8.10 beta version system I had multiple problems with flash. At the time I could see video but no audio, after the final release Java started working appropriately and then it was fine. Well since then I have chosen to revert back to my 8.04 system, I just find it more comfortable. Now the problem is that I have both flash player 9 and 10 installed, I have disabled 10 and just tried running 9 to load up youtube flash video's or pandora.com (Gnome Internet Radio) and all my flash sections come up as very large gray play buttons, when pressed the browser seems to be attempting to load the video, but just in a horrible buggy way. With Pandora.com all of firefox stops responding, screen fades to gray. Then when the screen comes back the pandora loading bar has yet to move any further and on refresh does the same thing. I have tried just running flash player 10 and it doesn't do anything at all, the pandora radio application section on the screen is MIA. I have run them both at the same time as well and get the gray box of doom. Also with the youtube videos if I am lucky the bar will go right to the end and start to buffer about 2 seconds on the end, then if moved back to the front it will attempt to buffer but when played the video is lagged back a couple seconds and still runs choppy even then. Please if anyone knows of a way to fix this I would be very pleased.

---

### Post by wolfen69 on 2009-01-17
i know what *i* would try, but it is up to you if you want to. 

go to synaptic and completely remove flash or however you want to remove it. completely remove firefox. go to home folder and Ctrl-H. delete the .mozilla file.

open terminal and:
```
sudo apt-get clean && sudo apt-get autoremove
```
then reinstall firefox.
then go [here]("http://get.adobe.com/flashplayer/") and download the .deb for ubuntu and click to install. restart firefox.

something is obviously broken between firefox and flash, so a fresh start may help.

---

### Post by gandaran on 2009-01-17
xnerdx
when you disable adobe flash 9 you also disable any other adobe flash version installed like flash 10, all adobe flash are disabled!
that large play button is not adobe flash, it's swfdec flash you also have installed and is the one firefox is using, get rid of it, use synaptic to completely remove it, see if gnash flash is also installed, if you want flash to work properly you only can have one version of flash installed!

---

### Post by xnerdx on 2009-01-17
Thanks guys I just removed every trace of flash player and mozilla firefox. Reinstalled them both and flash works perfect now.

---

