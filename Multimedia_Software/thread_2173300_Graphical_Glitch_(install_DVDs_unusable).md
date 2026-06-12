---
title: "Graphical Glitch (install DVDs unusable)"
date: 2013-09-08
forum: Multimedia Software
---

### Post by Halifax on 2013-09-08
I recently decided to reinstall Ubuntu on my laptop after years of not using it (Ubuntu, not the laptop). I can't seem to install 13.04 or 12.04 without this graphical glitch that pops up before anything else shows up. It renders the OS unusable. I can't run a liveCD or even install it. I tried an older CD I had arounf the house of 8.04, which worked great. I downloaded 11.04 and it had the same glitch. I'm attempting to try 10.04.4 right now. My laptop is an Asus G60JX. In attempting to research this a Google Images search yielded someone else with the same model (not a common model) with the same issue and no resolution for the problem. The interesting thing is that whatever the version, and apparently whatever the laptop (this person's was identical to mine), the glitch screen is always exactly the same. They're identical. It's not just random static, like it would seem at a glance. Has this happened on any other models of laptop? Could it be related to the specific GPU? All the hardware is in good working order - I recently played a few games on it for a while to make sure it was up to the task of an upcoming LAN party.
[ATTACH=CONFIG]246120[/ATTACH]
Anyone have any idea? I can't boot or install Ubuntu 11.10 or later. I'm working my way back through releases until I find the most recent version that works. I specifically know 8.04 works and 11.10, 12.04, and 13.04 don't. I should also mention again that there is nothing wrong with the hardware - 8.04 and Windows 7 both work just fine.

---

### Post by Bucky Ball on 2013-09-08
*Thread moved to **Multimedia & Video**.*

DO NOT go backwards. You are delving into dangerous territory which is NOT supported, hasn't been for ages, and will be running a vulnerable system which is a security risk. Stick with 12.04 LTS and up and let's try to fix that. Definitely DO NOT go to a LAN party with an unsupported release. You are begging for major trouble if you do. ;)

In 12.04 LTS (supported until April 2017, incidentally) can you get to the screen that lets you 'Try Ubuntu', 'Install Ubuntu' etc? If so, get there, hit F6 and choose 'nomodset', continue to 'Try Ubuntu'. How'd that do?

PS: Please use paragraphs for clarity. It will improve your chances of getting help. ;)

---

### Post by Halifax on 2013-09-09
Update: 10.04.4 is installing as I type this, so it works (can't get that far in other versions). So some difference between 10.04.4 and 11.10 that persisted through 13.04 is causing this problem to occur. I know nothing of the changes or how to fix whatever problem this may be, unfortunately. Any suggestions? I'd like the latest version but I have a feeling that even if an apt-get upgrade to 13.04 is possible it would just have the same problem after the upgrade.

---

### Post by Bucky Ball on 2013-09-09
No upgrade through update manager is possible in unsupported releases.

---

### Post by Halifax on 2013-09-09
On 12.04 with the nomodeset option it appears to be working so far. I actually got to a screen where I can initiate an installation. We'll see how this goes. Gotta love those hidden option menus.

And I do apologize, I'm in no shape to be effectively communicating. It's been a rough week.

I'm aware of the security risks of outdated OSs, but I'm more concerned with actually getting an operational OS to begin with. XD

---

### Post by Halifax on 2013-09-09
Installed successfully. You made that seem downright simple. Thanks!

---

### Post by Bucky Ball on 2013-09-09
Excellent news! To help others, could you mark the thread as solved (if you're satisfied it is) from Thread Tools at top right. Cheers. 

I love it when a plan works out! ;)

PS: Before marking as solved you might want to try a reboot and see if it breaks. If it does, post back and we can get back into the install again and make the nomodset option permanent so it will stick on reboot. (Also easy.)

---

### Post by Halifax on 2013-09-09
No, it works after a reboot just fine. It was apparently just the CD that had the issue with my laptop, not the proper installation. Everything's working fine (except the fact that I only gave myself 10 measly GB for Linux when I installed Windows, but whatever).

---

### Post by Bucky Ball on 2013-09-09
Great it doesn't break after reboot.

The 10Gb could be fine if you store your personal info on another partition. You can get exotic and create symlinks inside the /home directory to folders elsewhere.

Have you got room on the drive? Free space? You can also make a little space before of after the / partition and expand the / partition into it. (I know that is getting a bit off topic in this thread but if you need a hand with that post a new thread regarding it and stick a link here so I can have a look later.)

Unless you are intending on installing a heap of apps 10Gb could be fine though. How much does Gparted show the install is using right now with a fresh install? I have everything I need (not necessarily suit you, of course, and a minimal install running xfce4 desktop environment) and am using 7.75Gb approx. All personal stuff lives on other partitions elsewhere. ;)

---

