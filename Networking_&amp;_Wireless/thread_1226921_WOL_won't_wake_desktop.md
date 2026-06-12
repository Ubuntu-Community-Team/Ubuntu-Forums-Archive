---
title: "WOL won't wake desktop"
date: 2009-07-30
forum: Networking &amp; Wireless
---

### Post by naggis on 2009-07-30
I have a desktop dual booted with windows xp and linux mint 7 (ubuntu 9). My laptop has linux mint 7 and wakeonlan installed.
I can suspend the desktop (s3 sleep) and wake it up easily from the keyboard when it is running either xp or mint. When the desktop is running xp it can be woken from the laptop using the wakeonlan magic package. But when the desktop is running in mint, it cant be woken using the same magic package.
As the desktop can be put to sleep and woken by the above means it suggests that the hardware and BIOS are ok. So the problem must be with the mint (ubuntu) software.
I  have searched the net and found a number of possible solutions, none of which has worked so far. 
I am a newbie to ubuntu and particularly to using a terminal. At the moment when I use the terminal I can follow step by step instructions but really don't understand why - which is a problem. Naturally the more I use it the more understanding I get.
So I could really do with some help to sort this problem. Have you any thoughts?
Thanks for any help.

---

### Post by martinbaselier on 2009-07-30
The following command should turn on the wakeonlan function:
sudo ethtool -s wol g

Try running it, turn the machine off and test if it can be woken.

If this works, open rc.local
sudo gedit /etc/rc.local
and put in the command before exit 0, like this:

sudo ethtool -s wol g
exit 0

Then save the file and exit.

---

### Post by naggis on 2009-07-30
I tried running the line you suggest but got the following error message - 
$ sudo ethtool -s wol g
ethtool: bad command line argument(s)
For more information run ethtool -h
I tried running ethtool - h but it just didn't make any sense to me. 
I have already tried to write that line in the folder you suggest but hadn't tried it first. In my own defence I should say that I didn't know that you could test it or how. But now I do! 
Is it a bad command for my machine or is there something stopping the line working?

---

### Post by martinbaselier on 2009-07-30
Sorry, forgot an argument:

**sudo ethtool -s eth0 wol g**

I assume your lan is on eth0.

In rc.local you don't need sudo, since it's already executed as root. It won't hurt if you add it. It's just not necessary.

To get help on commands use **man**, in this case **man ethtool**. It's much more informative. 

To test it, just turn off the machine and try if you can wake it from another machine. I thought that was obvious, that's why I did not explain it any further.

---

