---
title: "Volume Control Lock Problem"
date: 2009-01-17
forum: Multimedia Software
---

### Post by johnzollo on 2009-01-17
HELLO!  Thanks for reading.

I am currently having a problem where when I change my volume the left channel will go back to zero.  In other words, the volume lock unlocks, and now the two channels can be changed separately. This is kind of frustrating when I just want to change the volume a little, and the entire left channel goes dead.

I'm running Ubuntu 8.04 (Hard heron w/updates) and a Stereo-link 1200 USB DAC usb audio device.

PLEASE HELP!!!  I'd appreciate anything you could do.  It's getting a little frustrating.:mad:

thanks  :guitar:
john

---

### Post by johnzollo on 2009-01-17
HELP!!!!!!!

bump +1:P

---

### Post by johnzollo on 2009-01-18
[COLOR="Red"][SIZE="6"]HELP!!!!!![/SIZE]

Iam still having this problem.  It's SSOOOOOO frustrating.  (I wish I had the money for Windows)  Anyway...

This problem only happens on the Stereo-Link 1200 USB audio device.  Another computer with a different sound card works fine.  I DON"T have the money for another sound card.  

ANYTHING you can do to help would be immensely appreciated!!!!

thank you!!!

john[/COLOR]:guitar:

---

### Post by markbuntu on 2009-01-18
This is a known bug with the alsa usb driver. You can get around that by using the pulseaudio volume control which is not effected. If you are not using pulseaudio or do not have the pulseaudio volume control or just want more information about controlling your sound better go here


[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

If you need more extensive help, go here

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by johnzollo on 2009-01-18
[SIZE="7"]THANK YOU!!!![/SIZE]

So far so good... Pulse seems to handle the "mixing" better.  The only thing I have to fox is the mixer on the panel (If you doble click that,the mixer in the window works perfect with pulse).   I think a reboot might help -- lemme try...

THANK YOU SOOO MUCH!!!!!  THANK YOU MARKBUNTU!!!!

Sincerely
john

---

### Post by johnzollo on 2009-01-18
Yes, changing to pulse *mostly* fixed the problem.  The control is a little jumpy, but that's about it.  Any word on if the bug will be fixed?  I really don't want to have to buy a new sound adapter.

thanks!
john

---

### Post by markbuntu on 2009-01-18
Well, it is fixed in Intrepid. Us Hardy users can just hope for an update from upstream to alsa 1.0.17 or 1.0.18 which we will probably get eventually.

You can do it yourself if you don't want to wait but there are some issues with kernel updates you will have to deal with if you do so do this at your own risk


[http://ubuntuforums.org/showthread.php?t=962695](http://ubuntuforums.org/showthread.php?t=962695)

I haven't updated my own Hardy installs with this so I won't be able to help you if you run into trouble. The pulseaudio controls work just fine for my usb headset.

---

