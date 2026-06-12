---
title: "Video Resolution stuck @ 640x480 NVIDEA 8600 GT"
date: 2008-05-31
forum: Multimedia Software
---

### Post by Corban987 on 2008-05-31
I am a big newbie, however I have been plaing with Ubuntu for about 1 month and never had to ask for help as I could always find my answer in some search.  However this time I am stuck.

I have Ubuntu 8.04 with all the latest updates.
I tried installing some sound drivers and still had no success with audio, so I removed the SBLIVE card and re enabled the onboard sound that gave me some sound.
On the reboot Ubuntu only came up with 640x480 resolution.  Where previously it hade 1600x1200.
I have tried so many things to fix this and I cannot.
Now when I boot after removing the nvidea drivers and reinstall it comes up with running in low graphics mode and I cannot choose or save settings.

I am now at a loss.
I would give you more information, however I do not know what you need, Also as I am a noob please provide and terminal commands I should try.

Thans for any help

---

### Post by Ubuginer on 2008-05-31
> **Corban987 said:**
> I am a big newbie, however I have been plaing with Ubuntu for about 1 month and never had to ask for help as I could always find my answer in some search.  However this time I am stuck.

I have Ubuntu 8.04 with all the latest updates.
I tried installing some sound drivers and still had no success with audio, so I removed the SBLIVE card and re enabled the onboard sound that gave me some sound.
On the reboot Ubuntu only came up with 640x480 resolution.  Where previously it hade 1600x1200.
I have tried so many things to fix this and I cannot.
Now when I boot after removing the nvidea drivers and reinstall it comes up with running in low graphics mode and I cannot choose or save settings.

I am now at a loss.
I would give you more information, however I do not know what you need, Also as I am a noob please provide and terminal commands I should try.

Thans for any help

Have you tried this already?

in terminal type: sudo -s displayconfig-gtk
At least, that's how I got mine fixed.

---

### Post by Corban987 on 2008-05-31
I tried that, this is what I get
xxx@xxx-ubuntu1:~$ sudo -s dis
discover           diskseekd          display            
diskd              disown             displayconfig-gtk  
xxx@xxx-ubuntu1:~$ sudo -s displayconfig-gtk 
[sudo] password for xxx: 
from: can't read /var/mail/gettext
/usr/bin/displayconfig-gtk: displayconfig-gtk: line 7: syntax error near unexpected token `"displayconfig-gtk"'
/usr/bin/displayconfig-gtk: displayconfig-gtk: line 7: `gettext.textdomain("displayconfig-gtk")'
xxx@xxx-ubuntu1:~$

Also I think sonething else is crewed with the drivers.
I can not re enable the nvidia settings.  Each time I do on the reboot they become disabled.  See screen shot. 
I am wondering if all the correct software is installed as I may have tried something and removed the correct driver.

---

### Post by Corban987 on 2008-06-03
=I guess no one has any ideas. 

I reformatted and now 2 days later same thing.  I have not messed with drivers, installed anything new.  Ubuntu just boots to the default 640x480 resolution and its unusable.

---

### Post by Pjotr123 on 2008-06-03
Try this:
[http://ubuntutip.googlepages.com/bugsinubuntu](http://ubuntutip.googlepages.com/bugsinubuntu)
(number 2)

Does this help?

Greeting, Pjotr.

---

### Post by Corban987 on 2008-06-04
I think I solved this.
What it was - My monitor must be playing up.  Not sure why or how.  It seems after doing something it stops working at high resolutions, even on Vista.  I reformatted with VISTA and it still did not fix it, so I put the monitor on my other PC and it worked, so then I unplugged it and put it back onto UBUNTU and VISTA and they both worked on the next reboot.  Must be something goofy in the firmware of the monitor that locks it to 800x600 resolution.

Thanks for your ideas.
My monitor is a Chimei 22inch widescreen monitor.

---

### Post by mukiex on 2008-06-04
I'd say "search the forums" but I just tried that and couldn't find my own fix. With that out of the way, I hope this helps :

[http://ubuntuforums.org/showthread.php?t=805506](http://ubuntuforums.org/showthread.php?t=805506)

I also hope the info located therein hasn't already been posted in this thread. =(

---

