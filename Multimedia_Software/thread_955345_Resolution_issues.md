---
title: "Resolution issues"
date: 2008-10-22
forum: Multimedia Software
---

### Post by MeLight on 2008-10-22
At the beginning... I had one ubuntu desktop (desktop A) and all was good, then I got another one (desktop B). It's graphics card is something nvidia compatible, the second one never installed that well and went low-rez (800x600) from the beginning, I didn't mind that much coz we use it mostly for background calculations. I got the two puters connected via a KVM to my screen, and now after I've installed some updates my main (A) desktop went 800x600 also!! How do I fix this? thanx

---

### Post by overdrank on 2008-10-22
> **MeLight said:**
> At the beginning... I had one ubuntu desktop (desktop A) and all was good, then I got another one (desktop B). It's graphics card is something nvidia compatible, the second one never installed that well and went low-rez (800x600) from the beginning, I didn't mind that much coz we use it mostly for background calculations. I got the two puters connected via a KVM to my screen, and now after I've installed some updates my main (A) desktop went 800x600 also!! How do I fix this? thanx

Hi and after the updates you may have to reinstall the nvidia drivers. You can start by looking under system, administration, hardware drivers make sure that the drivers are enabled and in use. Also you can use the keys alt, F2 and enter the command ```
gksu displayconfig-gtk
``` and adjust your resolution there.
Moved to Multimedia & Video :)

---

### Post by MeLight on 2008-10-22
The computer I really need to fix now is the A desktop which graphic card is intel945. I tried what you said:
A. I don't have Hardware Drivers under system > administration. I only have Restricted Drivers (which is probably irrelevant) I pushed, it told me my hardware doesn't need those :D
B. I ran the "gksu displayconfig-gtk" screen config. I tried to force some screens and resolutions but it wouldn't work, and it auto detects only plug n play 800x600 screen :(
Any help would be appreciated (as 3 lines of text cover half of the screen! I'm miserable lol)

---

### Post by overdrank on 2008-10-22
> **MeLight said:**
> The computer I really need to fix now is the A desktop which graphic card is intel945. I tried what you said:
A. I don't have Hardware Drivers under system > administration. I only have Restricted Drivers (which is probably irrelevant) I pushed, it told me my hardware doesn't need those :D
B. I ran the "gksu displayconfig-gtk" screen config. I tried to force some screens and resolutions but it wouldn't work, and it auto detects only plug n play 800x600 screen :(
Any help would be appreciated (as 3 lines of text cover half of the screen! I'm miserable lol)

Hi and yes the intel chipset will need no drivers. What do you mean by did not work. Did you try the test button. If that is the case sometimes the test does not work but when you log out and back in it will. How much memory does the system have and you may look at changing the amount share with the intel graphics in bios.

---

### Post by MeLight on 2008-10-23
Yes, I have tried the test button, and after reading your post I tried forcing another configuration, and relogin - it said Ubuntu is running in low rez mode (configure.., continue) I tried to configure again, didn't help, it goes back to the Plug n play 800x600 config. How would i go about changing the memory allocation? (I have 3.1 gigs on this machine)

---

### Post by orange72_camaro on 2008-10-24
I am having kinda the same issue on my desktop I just loaded with the 8.10 ubuntu and have another desktop with windows on it hooked through a KVM.  for some reason with the KVM connected I can only get 800x600 resolution.  when I go right to the monitor I can get up to 2048x1536 (which I love).  the Ubuntu computer has an nvidia geforce fx 5200.

---

### Post by joenelis on 2008-11-07
I have had exactly the same issue since upgrading to version 8.04.1 - whenever I have my monitor connected directly (fx5200 card and Viewsonic PS775 monitor), I get resolutions higher than 1280x1024.   However, as soon as I reconnect back through my KVM Switch, I am back to 800x600.  I use 1280x1024 and higher on the MS Windows systems that also use this KVM, so it is sure not a KVM issue in my case.  My /etc/X11/xorg.conf file still calls for a range of higher resolution, but when I boot through the KVM, I guess it never gets used. 

I've read that there is something new called bulletproofX which must have been added to protect those who need protected.  There has to be some way to disable this 'bulletproof' feature for we who do not need to be protected - it appears that a whole lot of us seem to need to know how to do it.

---

