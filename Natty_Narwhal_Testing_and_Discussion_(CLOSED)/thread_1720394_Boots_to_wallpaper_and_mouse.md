---
title: "Boots to wallpaper and mouse"
date: 2011-04-03
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by bcoffield on 2011-04-03
Hi all, I installed the daily build from yesterday to my hard drive.  Installation went great. 

When I boot up though, it takes me in and all I see are my wallpaper and the mouse.  I can move the mouse.  I can't restart x, reboot etc. I have to power off with the button on my laptop.

I have an older ati radeon mohility card.  I don't know if that's the issue.  Happy to provide any system details etc (but please tell me how to find them for you :)

---

### Post by davepoth on 2011-04-03
This seems to be a fairly common problem. Press Ctrl-Alt-T to bring up the terminal, and then load either unity or gnome-panel.

---

### Post by bcoffield on 2011-04-03
Oh okay, great.  I tried searching for this issue before posting but I guess I didn't do the best job lol.

when i drop to terminal what command do I run?  

xwin unity ? or something like that?

---

### Post by davepoth on 2011-04-03
just "unity", or "gnome-panel".

---

### Post by beameup on 2011-04-03
alt-ctrl-del will let you restart. I had the same issue with an Acer Aspire One.
Had to install the compiz-config-settings-manager and enable the unity plugin.
You can do this by selecting "Classic Ubuntu" in the drop down from the menu  at the bottom of the login screen, and login to a session with that. Then open Synaptic and search for that utility above and install it.

May be another way to accomplish that, but it worked for me.

---

### Post by bcoffield on 2011-04-03
Okay, thanks.

I was hoping to return to mark this thread solved... but...

However, my next two boots didn't even get me as far as the wallpaper.  It hung on the boot screen where it says ubuntu and has the dots below it.  My mouse appeared and was moveable, but I saw no dots progressing.  It was hung there and I had to do a hard poweroff... (and I did let it sit for a long time, just in case it would eventually move past the screen)

Any thoughts?

---

### Post by davepoth on 2011-04-03
What happens when you ctrl-alt-t?

---

### Post by bcoffield on 2011-04-03
I tried that and nothing happens.... seems pretty locked up.

---

### Post by beameup on 2011-04-03
Could try booting into recovery mode. When you get a prompt  do  *sudo apt-get update*  then *sudo apt-get upgrade* and see if you missed anything.

---

### Post by bcoffield on 2011-04-03
Hmm... I can't seem to get it to boot into recovery.... it goes from BIOS str8 into ubuntu and my trying to hit any various keystrokes doesn't do anything ...

---

### Post by beameup on 2011-04-03
ESC is the key to get to the menu selection, need to change the display time on it and I'm not sure how. Maybe someone else knows right off the back.
When you have a dual boot system GRUB will display for awhile. When it's a straight up install it breeezes right through the GRUB menu.

---

### Post by cariboo on 2011-04-03
The key to show the grub menu was changed in grub2, now hold down the shift key durnig post. The default time out is 10 seconds, but as beameup, said, you won't see the grub menu if you only have one os installed.

---

### Post by beameup on 2011-04-04
> **cariboo907 said:**
> The key to show the grub menu was changed in grub2, now hold down the shift key durnig post. The default time out is 10 seconds, but as beameup, said, you won't see the grub menu if you only have one os installed.

yea, thanks for that. Something I haven't had to do in a long time, obviously.

---

