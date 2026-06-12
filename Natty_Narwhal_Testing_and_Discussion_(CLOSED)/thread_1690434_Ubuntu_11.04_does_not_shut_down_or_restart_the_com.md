---
title: "Ubuntu 11.04 does not shut down or restart the computer properly"
date: 2011-02-18
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by CookieNinja on 2011-02-18
Anyone else have a problem where they shut down or reboot their 11.04 install, and find that when the computer restarts (either automatically as part of the restart option, or manually if the computer has just been shut down), their monitor is remains on stand-by.

The only solution seems to be pressing the reset button on my computer to get the computer to output to the monitor. This problem only happens when 11.04 is shut down or restarted, it doesn't happen with any of my other installed operating systems (Windows 7 & Fedora 14) or 10.10 when it was running on the same computer.

It's almost as if something's not been cleared during the shut down process that prevents the graphics card (Nvidia 9800 GT + nouveau driver) being used, and pressing the reset button the PC somehow clears it.

Not the best description, but hopefully enough for someone to be able to tell me if it's already been reported or not.

---

### Post by mc4man on 2011-02-18
Saw some 'odd' behavior on a desktop w/ nouveau 3d drivers and nvidia - except this was on start up. The monitor would go from active to standby to active.
Got rid of that by going to a text boot - removing quiet splash from the GRUB_CMDLINE_LINUX_DEFAULT= in etc/default/grub
maybe try that
> 
# [COLOR="Blue"]If you change this file, run 'update-grub' afterwards to update[/COLOR]
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT=""
GRUB_CMDLINE_LINUX=""


---

### Post by CookieNinja on 2011-02-18
> **mc4man said:**
> Saw some 'odd' behavior on a desktop w/ nouveau 3d drivers and nvidia - except this was on start up. The monitor would go from active to standby to active.
Got rid of that by going to a text boot - removing quiet splash from the GRUB_CMDLINE_LINUX_DEFAULT= in etc/default/grub
maybe try that

Might be that a less fancy shut down process, without the graphics, is the way to go then.

I've got a mostly decent desktop with unity working now, so I'm going to try rebooting it one more time before starting to look into it some more.

---

### Post by tgrundle on 2011-03-14
I have been experiencing this as well.  Have you found any solution?  I was thinking about opening a bug report if you haven't already.

---

### Post by rbrick49 on 2011-03-14
my computer is doing the same thing i have to hit the reset buttonn to reboot I have put it down to my graphics card ati 6950 not having proper ati driver yet windows shuts down and reboots fine 10.10 maverick was doing the same thing until i installed the ati driver for it

---

### Post by Harry33 on 2011-03-15
> **CookieNinja said:**
> 
...
It's almost as if something's not been cleared during the shut down process that prevents the graphics card (Nvidia 9800 GT + nouveau driver) being used, and pressing the reset button the PC somehow clears it.
...


Does nvidia-current_270.29 work OK with your setup?
You are using xserver 1.10 rc2 (no xorg-edgers PPA)?

---

### Post by shid007 on 2011-04-09
Well this also happens to me, but I have all the fancy stuff like Plymouth turned off so I see what actually (partially :)) happens... it just drops me with console login and waits... so if I press ctrl+alt+del it restarts and if I press powerbutton shortly it normally shuts down...

Ther is probably something hanging in there, I haven't figured out what it is yet...

---

### Post by Shai Hulud on 2011-04-12
Same problems here. I'm not using Plymouth so like shid007 i'm dropped off at a command-line login screen. I have to login and use "sudo halt" or "sudo poweroff now" to shutdown my system completely. I'm using Kubuntu, but it seems that the problem is in the base.

---

### Post by apple_and _linux on 2011-04-12
Same problem here, and I can't tell what's causing it.  When I try to shut down/reboot, my screen goes black fairly quickly, but then some sort of fan in the computer starts whirring at high speed (a fan I never hear otherwise) and even when I leave it for several minutes, the computer does not progress pass that point.  I'm guessing it'd be a graphics issue, since Plymouth hasn't been working for me since I upgraded from 10.10.  (As a sidenote, I've always had troubles with Plymouth and had to run some little script to get start-up/shut-downs to look normal.)  Is there any log I can look at to tell what might be causing the problem?

---

### Post by searayman on 2011-04-12
dido, I too have this shut down issue

---

### Post by Makeveral on 2011-04-15
I also have this problem... Searching on google i found this:

add apm power_off=1 to /etc/modules

This fixed the shutdown but restart is still not working and i'm not really sure if it's ok to add that line :confused:

---

### Post by john mason on 2011-04-15
Although my story is no different from you all guys but i am also the victim of same.
Waiting for the solution now.

---

### Post by dino99 on 2011-04-15
> **Makeveral said:**
> I also have this problem... Searching on google i found this:

add apm power_off=1 to /etc/modules

This fixed the shutdown but restart is still not working and i'm not really sure if it's ok to add that line :confused:

file a bug report: ubuntu-bug linux
(need an account on launchpad first)

---

### Post by ernstblaauw on 2011-04-15
I filed a bug report:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/762203](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/762203)

Please comment to this report and vote that you're having this problem too (of course, only if you have this problem ;)). Hopefully, the developers can track down this issue.

---

### Post by Wobbo on 2011-04-17
I have the same problem, I thought it was a motherboard problem, I had to install 10.04 to use my Ati 6950. I couldn't install 11.04 directly so i had to install 10.10 and update it to 11.04. Only the problem when shutting down/starting up Bios gives an error still remains. Every device connected by USB remains active after shut down.

---

### Post by apple_and _linux on 2011-04-18
Got a plymouth update sometime in the last couple days and it seems to be fixed.  Cheers, Ubuntu team!  :D

---

### Post by Shai Hulud on 2011-04-20
After one update things are fine with my machine :)

So try updating if you still have the problem.

---

### Post by rbrick49 on 2011-04-20
from the update a couple of days ago my amd x64 machine is ok thanks devs

---

### Post by CookieNinja on 2011-04-25
My problem also appears to have gone away. One less grump about the forthcoming release :-)

---

