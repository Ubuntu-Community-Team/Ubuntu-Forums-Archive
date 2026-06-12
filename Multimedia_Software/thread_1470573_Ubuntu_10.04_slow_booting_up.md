---
title: "Ubuntu 10.04 slow booting up"
date: 2010-05-03
forum: Multimedia Software
---

### Post by sandman3838 on 2010-05-03
Hey!
Ubuntu 10.04 seem too slow?  This wasn't an issue with 9.10.

After the GRUB Menu I get a blinking cursor and then the Xsplash Screen (I have an issue with that, but I'll explain that in a minute)

50 to 55 seconds later:

I get the Sign-in screen.

After signing in:

15 to 20 seconds later I'm at my desktop.

From what I have been reading about the speed of Ubuntu 10.04, something is wrong.  

Also, has anyone had their Purple Xsplash screen looking like its in safe mode?

I should mention that once I'm in Ubuntu, everything is just fine.

---

### Post by sandman3838 on 2010-05-03
Hello
Here is an update.....

It is still slow when going from the grub screen to the login screen?
Is there some sort or a log file that might list what is loading up?

However I did install the latest NVIDIA drivers and my issue with the unusually large purple Ubuntu screen is no longer an issue.

---

### Post by PostWax on 2010-05-04
Same problem here.  After login it takes 30 seconds for my desktop to come on.  Any ideas?



> **sandman3838 said:**
> Hello
Here is an update.....

It is still slow when going from the grub screen to the login screen?
Is there some sort or a log file that might list what is loading up?

However I did install the latest NVIDIA drivers and my issue with the unusually large purple Ubuntu screen is no longer an issue.

---

### Post by Rasa1111 on 2010-05-04
no idea.

 10.04 is faster to boot, faster to shutdown, and runs faster than anything else Ive seen or used.
Karmic was quick, but this is super quick.

[on an old dell dimension 2350]

When I turn on my computer.. I am on my desktop in no more than 10-15 seconds. 
[ 15 on a 'slow day']
when I shut it down, it takes about 3 seconds. 

pretty amazing..
wish it worked the same for everyone. 

pretty soon it will i think.

---

### Post by owenl on 2010-05-05
I had the same problem, I fixed it by turning off my FDD in my BIOS. It took gnome boot from entering password to desktop available from about 30 seconds to 2.

---

### Post by Rasa1111 on 2010-05-05
> **owenl said:**
> . It took gnome boot from entering password to desktop available from about 30 seconds to 2.

 haha, amazing isn't it!?!?

 Ive been using it for like a week and I still cant get over the quickness~  lol  :guitar:

---

### Post by sandman3838 on 2010-05-05
Thanks for the info.
I should mention that my Mother board is a Gigabyte GA-M55SLI-S4

owenl I have to ask.....
FDD  is that the floppy disk?

Thank you

---

### Post by betrunkenaffe on 2010-05-05
Wrong forum much?

---

### Post by sandman3838 on 2010-05-05
I went a head and disabled my FDD Floppy.
Didn't help.

However you mentioned that your issue was from "Login" to "Desktop"!

My issue is from the "Grub Menu" to "Login"?

I don't know if this is part of the problem?
But didn't some or all of KDE get loaded with Ubuntu 10.04?

I seem to have KDE in the Sessions options and I don't remember adding it in.  Also I did recently try LXDE, I think it was?  Personally, I'm not very impressed with either and I have been thinking about removing them both and staying with just Ubuntu.

Could that help.

betrunkenaffe........
As for the reason why I'm using this forum is because some of what I have read in relation to a distorted Xsplash screen was do to a bad install/setup of ATI/Nvida drivers when upgrading to 10.04.  The bad Xsplash screen was fixed when I did a removal and clean install of the NVIDIA drivers.  I thought it may have been my problem but instead it was only part of the problem.

---

### Post by Jonny87 on 2010-05-05
I too have had trouble with booting along with it taking its time when it does boot. I've had other issues.

[http://ubuntuforums.org/showthread.php?t=1474226](http://ubuntuforums.org/showthread.php?t=1474226)

I have the same motherboard, Rev 2.0.

---

### Post by ben2talk on 2011-01-08
Exaggerating doesn't help Ubuntu.
My desktop takes more than 15 seconds after turning it on just to get to the Grub screen - and a good 45 seconds on a fresh installation to reach desktop (which is pretty quick.

Some configurations do lead to slowdowns though, right now (having an Nvidia driver might be a factor) I get 50% cpu for Xorg, and have to kill and restart X to get it down to less than 5%. Also, recently I had a lot of disk thrashing after putting in my password AFTER my startup script ran (conky runs on the login background)long before the panel and docky appear...

Next up I'll edit my GRUB selection and add 'profile' at boot time..

---

### Post by sandman3838 on 2011-09-04
Not an issue with 10.10!

---

