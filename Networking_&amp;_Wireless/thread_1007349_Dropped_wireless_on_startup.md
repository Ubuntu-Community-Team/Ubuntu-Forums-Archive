---
title: "Dropped wireless on startup"
date: 2008-12-10
forum: Networking &amp; Wireless
---

### Post by bobterri on 2008-12-10
I've got a Dell Inspiron 6000 laptop with IP2200 wireless card.  At work, when I boot up, the networkmanager applet shows I'm connected to my WPA2 access point at 90%.  When I open Firefox I cannot access the internet.  If I reboot it connects properly with no problems.

At home on a WPA2 access point I never have this problem.  When I go out to a coffee cafe with free wireless I never have this problem.  

Any ideas anyone?

---

### Post by Titan8990 on 2008-12-10
Instead of rebooting, try just restarting networking. My guess is your wireless interface still has an IP address from your home and needs something invoke the dhcp client to attain a new address.

To restart networking:


sudo /etc/init.d/networking restart

---

### Post by bobterri on 2008-12-10
Thanks Titan 8990.  I'll give it a try.

---

### Post by bobterri on 2008-12-16
For two or three days, I had no problem with accessing my wireless access point at work.  Even after being on-line at home the night before, in the morning at work I was able to access the work wireless access point with no problem.

So, this morning at work, I tried to get online but it didn't work.  I tried Titan 8990's suggestion. I typed "sudo /etc/init.d/networking restart" in a terminal.  I typed in my password and it said "OK," but it didn't work.

Any more thoughts?

---

### Post by bobterri on 2008-12-17
Would wicd be worth a try?

---

### Post by bobterri on 2008-12-18
Wicd didn't make a difference.  Same problem.  It's interesting, when I issue any command with sudo /etc/init.d/networking stop|start|restart|force-reload none of them seem to do anything.  

Does anyone have a clue what is going on?  

Today when I tried to get on the internet at work it did the same thing as described in my opening post, however, I had not been on any other access point such as home or a coffee shop.  

It's such a hassle to have to reboot the laptop to get internet.

---

### Post by P235 on 2008-12-18
Hi there, I seem to share a similar situation with you, and my thread did not have much luck:

[http://ubuntuforums.org/showthread.php?t=1014097](http://ubuntuforums.org/showthread.php?t=1014097)

I find that shutting my laptop down completely, then starting it up again usually works the best.  The "ctrl-alt-backspace" command does not bring the wireless back up, and having my laptop restart is not as consistent as shut down.

---

### Post by bobterri on 2008-12-18
Yes, P235.  It seems similar.  Thinking of trying Fedora 10, just to see if the problem shows up in that distro.  Been hearing good things about F10.

---

### Post by P235 on 2008-12-19
For what it is worth, there are other threads concerning this problem with other users.  I found another a while ago here:

[http://ubuntuforums.org/showthread.php?t=1000871](http://ubuntuforums.org/showthread.php?t=1000871)

I am not sure if there is an active bug report though.  I have tried the suggestion to start up with another kernel, but as I mentioned above, shut down is the best solution.  It does not seem to matter which kernel is selected.

---

