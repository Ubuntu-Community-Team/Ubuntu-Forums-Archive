---
title: "Volume Control still missing from Indicator Applet"
date: 2010-06-25
forum: Multimedia Software
---

### Post by wearyroad on 2010-06-25
Hi all! 
Alright, at first, the volume control went missing from the indicator applet, but then re-adding it to the panel didn't do anything but add a mail/chat applet. So I tried to reset the indicator applet settings with this:

```
sudo apt-get remove indicator-messages
```
(Gotten from this thread: [http://ubuntuforums.org/showthread.php?p=9286680#poststop]("http://ubuntuforums.org/showthread.php?p=9286680#poststop"))

And now all that happens when I add the indicator applet to the panel is that the text: "No indicators" pops up where the mail/chat applet was before. Is there a way to get the volume applet back into the panel? Any suggestions appreciated!

---

### Post by VH-BIL on 2010-06-25
I found this:
[http://ubuntugenius.wordpress.com/2010/05/04/restore-missing-volume-button-to-system-tray-after-upgrade-to-ubuntu-10-04/](http://ubuntugenius.wordpress.com/2010/05/04/restore-missing-volume-button-to-system-tray-after-upgrade-to-ubuntu-10-04/)

This part may be helpful:
> Use Alt+F2 to open the Run Application app, paste gnome-volume-control-applet into the text field, and click the Run button (you can also enter the command into a terminal, but the button will disappear if you close the terminal). To get it to start automatically from the next reboot, go to System > Preferences > Startup Applications and add it as a new entry with a name like &#8220;Volume Button&#8221;.

---

### Post by wearyroad on 2010-06-26
Awesome, thanks for the link! Even though I couldn't follow it's directions, I got this work-=around right:

Running 
```
sudo apt-get install indicator-sound
sudo apt-get install indicator-messages
sudo apt-get install evolution-indicator
```
put the volume control right back in the indicator-applet, (rather than putting it in the notification area, like the links instructions show to do) put the evolution indicator back in the applet and set the messages right again. There may be a bug where the sound indicator is removed in upgrading to lynx... I dunno.

Running Alt-F2 didn't work for me, though, so I had to add the Run Application to the gnome panel from right-clicking on the panel and adding it from the list of apps.

---

### Post by Groucho Marxist on 2010-08-03
> **wearyroad said:**
> Awesome, thanks for the link! Even though I couldn't follow it's directions, I got this work-=around right:

Running 
```
sudo apt-get install indicator-sound
sudo apt-get install indicator-messages
sudo apt-get install evolution-indicator
```put the volume control right back in the indicator-applet, (rather than putting it in the notification area, like the links instructions show to do) put the evolution indicator back in the applet and set the messages right again. There may be a bug where the sound indicator is removed in upgrading to lynx... I dunno.

Running Alt-F2 didn't work for me, though, so I had to add the Run Application to the gnome panel from right-clicking on the panel and adding it from the list of apps.

Thank you so much for posting this! I had the same problem today and was able to solve my dilemma due to your instructions. :)

---

