---
title: "firefoxrc file empty--Flash sound problem"
date: 2008-09-21
forum: Multimedia Software
---

### Post by ISuckAtLinux on 2008-09-21
So, I can get all my sound working fine outside of Firefox (system sounds, Pidgin, etc.), but I can't seem to get the Flash sound in Firefox to work.  I know this has been solved to death, but I've been trying all the solutions, and this is what happens:

It seems as if for most people, what works is typing these commands:
> 
sudo aptitude install alsa-oss

That works fine.  Everything installs in a satisfactory manner.

> 
sudo gedit /etc/firefox/firefoxrc

That works fine as well.  It opens up the proper file.  Now comes the problem.  Apparently I should see:
> FIREFOX_DSP=”none”
somewhere in the file, and change the **none** to **aoss**.  Well, unfortunately for me, the file is completely empty.  So I tried adding the line and subsequently saving it, but I am confronted with this:
> 
**Could not save the file */etc/firefox/firefoxrc*.**
Unexpected error: File not found



Can someone help me?

---

### Post by Awareness on 2008-10-02
Same problem here. I use ubuntuzilla...

looking for my problem I found your thread... if i find a solution, ill drop by... ;)

---

### Post by anniet on 2009-08-20
i have the same problem. please let me know if you find something that works!

---

