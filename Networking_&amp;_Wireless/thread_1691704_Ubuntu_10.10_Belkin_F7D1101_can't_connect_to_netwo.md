---
title: "Ubuntu 10.10 Belkin F7D1101 can't connect to network"
date: 2011-02-20
forum: Networking &amp; Wireless
---

### Post by spladd on 2011-02-20
Hello all, total Linux noob here, on a fresh install of 10.10.
 
I'm using a Belkin F7D1101 USB adapter for my wireless internet, and I can't get the damn thing to connect.  I've installed ndiswrapper, ndisutils, and ndisgtk, then used the latter to install the driver that came with the CD (though I'm sure I'm using the right one, I've tried all the included drivers with no success).  The adapter itself is functioning fine, as I've used it on Windows XP with no issues.  It's just not communicating with Ubuntu very well. 
 
My issue isn't that I can't get it to show up and search for a network (as I've seen on several other posts about this adapter), but that I can't get it to actually connect to my router.  Using WEP 40/128, I enter the password, but after about a minute, I'm simply prompted for the password over and over.  I've restarted several times, even installed 10.04 just because I had no idea what to try, and no dice.
 
I've got a Wii and another laptop connected to the network with no problems, so I'm reasonably confident that the issue is somewhere on this PC (or with this adapter), and that I'm doing something waaaaaay wrong.  Any assistance would be appreciated! :)

---

### Post by amsterdamharu on 2011-02-20
Could you post the output of the following commands?
```
sudo lsusb -vv
```You need to post only the part of your wireless card.
```
rfkill list
sudo jockey-text
```If rfkill says it's not installed you can install it with the following command:
```
sudo apt-get install rfkill
```and the output of this one.
```
sudo ifconfig -a
sudo dhclient
```

To execute the command(s) you can press alt + F2, type gnome-terminal and click run. Then copy one command and paste it in the terminal (black screen that showed up after you clicked run). Use the mouse to paste commands in the terminal.
Then you can select all the text in the terminal, right click and select copy. When pasting it here please wrap it in code tags: &#91;code][COLOR=Red]Your pasted stuff[/COLOR]&#91;/code]

---

### Post by spladd on 2011-02-20
So apparently I didn't do enough research.  I followed the steps here:
 
[http://ubuntuforums.org/showthread.php?t=1522815&highlight=Belkin+F7D1101](http://ubuntuforums.org/showthread.php?t=1522815&highlight=Belkin+F7D1101)
 
and it's now working like a charm.  Thanks for your suggestions though, had the above procedure failed I would have definitely been in need of some assistance.  Thank you, Ubuntu community!

---

