---
title: "Remote Desktop doesn't work remotely"
date: 2009-07-22
forum: Networking &amp; Wireless
---

### Post by brian_hayward on 2009-07-22
I am running Ubuntu 9.04 on my desktop.  I tried to use the Remote Desktop functionality but it won't work.  I create an ssh tunnel (through putty on windows or the command line on a Linux box), and I have all my ports are forwarded correctly.  When i use a VNC viewer to view my Ubuntu Desktop, I can view the desktop but I can't interact with it at all remotely.  If I try to drag windows, open the Applications menu, or try to do anything it won't reflect on the remote screen.  However, when I was away for a weekend and testing everything to see if it ran correctly my girlfriend just happen to be walking by my computer screen and saw windows wandering aimlessly around my computer screen and menus being pulled down (which totally freaked her out) so it would seem that my ubuntu machine that i log into is getting the commands from the remote computer but the results aren't getting sent back to my remote computer (i.e. if i try to drag a window, it doesn't appear to move on the remote computer).  does anybody have any ideas as to what is going on?  

I have a suspicion that my internet connection is too slow but that shouldn't be an issue since i have cable internet, and i also dumb down the settings on my vnc viewer to lower quality.  Is there a way i can test to see if my internet connection is too slow?  Does anybody know the minimum connection speed to run Remote Desktop?  Any help or suggestions are greatly appreciated.  Thanks.

---

### Post by martinbaselier on 2009-07-22
Have you tried using vnc on your local network?

---

### Post by superprash2003 on 2009-07-22
try disabling compiz fusion or extra effects in ubuntu

---

### Post by brian_hayward on 2009-07-22
How does a person disable compiz, i've been trying to figure it out but i can't by roaming around Ubuntu.

---

### Post by Sock puppet on 2009-07-22
> **brian_hayward said:**
> How does a person disable compiz, i've been trying to figure it out but i can't by roaming around Ubuntu.

Preferences -> Appearance -> Visual Effects

Select None

---

### Post by brian_hayward on 2009-07-24
> **superprash2003 said:**
> try disabling compiz fusion or extra effects in ubuntu

Disabling the compiz fusion worked and it all works fine now.  Thanks.

---

### Post by Conzo on 2009-07-24
> **superprash2003 said:**
> try disabling compiz fusion or extra effects in ubuntu


I also was Having this problem  and by turning off the extra effect on the host machine that work well .....
Next Step is Getting my windows box at work to remote view ,,Wish Me luck !


Thanks for all the Wisdom and time Everyone Put into these forums! 
Conzo

---

