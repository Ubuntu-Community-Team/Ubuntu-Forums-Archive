---
title: "desperation. Gutsy fglrx = blank/black screen after splash loads"
date: 2008-01-25
forum: Multimedia &amp; Video
---

### Post by carotids on 2008-01-25
Installed fglrx drivers without any obvious complications.

After the slash screen (i am assuming when x starts), I just get a blank black screen.  I can not drop to terminal and I eventually have to hard reboot.

vesa works fine.

ATI 2600.

my horizsync and vert refresh are correct in my monitor section.

I am running DVI from my monitor to my video card.

I have been playing with this for 3 days now.  I just reinstalled everything and I am hoping that some poor soul will help me.

thank in advance.

carotids

---

### Post by maheshasolkar on 2008-01-25
> **carotids said:**
> Installed fglrx drivers without any obvious complications.

After the slash screen (i am assuming when x starts), I just get a blank black screen.  I can not drop to terminal and I eventually have to hard reboot.

vesa works fine.


My problem may be slightly different - I used to get a blank screen immediately, even before I logged in, no splash.

My Xorg log had a an error message indicating that the default depth was set to 8 and the new fglrx driver did not like that. I added 'DefaultDepth 24' to the Screen section of /etc/X11/xorg.conf. That fixed my situation.

Maybe your problem is related - although I have my doubts.

HTH,
Mahesh.

---

### Post by Yellow Pasque on 2008-01-25
Is your card AGP? fglrx doesn't seem to like AGP cards. BTW, what version of fglrx are you using, the one that comes with Ubuntu or something downloaded from ATI?

As suggested, install fglrx and boot up. When you hit the black screen, press Ctrl+Alt+F1 and see if you drop back to a terminal. If so, save your log file so you can post it and we can look at it. To save your file to the desktop:
> cp /var/log/Xorg.0.log ~/Desktop

---

### Post by spitf1r3 on 2008-01-25
I had the same problem after installing drivers (8.01)
So I've insatlled drivers in recovery mode with envy (latest ones) and it worked.
But everything is terribly slow (of course I don't have direct rendering), can anyone help?

---

### Post by harold4 on 2008-01-25
I'm also stuck with the same terribly slow render.  

Dell sent me a laptop with an ATI x1400 when I ordered an Nvidia card.  A few days until NVidia goodness (which is besides the point)

---

### Post by rosegarden78 on 2008-01-25
I, the insignificant, would try related articles on these forums:

Restoring Xorg.conf from backup
Data recovery from Live CD
Mounting partitions
Replacing Xorg
How to backup home folder

---

### Post by spitf1r3 on 2008-01-25
So what forums you're talking about?
You didn't gave any address..

---

### Post by rosegarden78 on 2008-01-26
I now I'm just saying sound like you need to make a backup of /home just in case.  I can't remember the exact forums I used but the Xorg X server can be reinstalled and the /etc/X11/xorg.conf file usually has a backup~ file in the same directory.  Since I'm not a mind reader I was painting with a broad stroke.  I just participated in an article where one user commented how some people want to be spoon fed answers instead of finding them on Google.  I admit the forum search function leaves room for improvement.  You can always use a LiveCD to access your partitions.  Sounds like you just need to install Ubuntu again with a slow-burnt 4x cd-r.   Sorry I can't be of any technnical assistance to you good luck.

---

### Post by spitf1r3 on 2008-01-28
> **rosegarden78 said:**
> Sounds like you just need to install Ubuntu again with a slow-burnt 4x cd-r.
Hmmm I don't think so... don't forget we AREN'T using Windows but ubuntu, and mostly we DON'T need to reinstall, cause there is always a way to fix it.
Keep that in mind, when you want to advise anyone else to reinstall.
BTW, there's no need to backup home when reinstalling Ubuntu, when you have /home on a separate partition.
And that comment with slow-burnt cd is really funny xD:lolflag:

---

### Post by v912485 on 2008-02-03
spitf1r3 I think I have a similar problem, did you manage to solve it?

---

### Post by Giannis68 on 2008-02-03
i solve this problem when disable Visual Effects
System-->Preferences-->Appearance
Visual Effects-->None

---

### Post by v912485 on 2008-02-03
The special effects are disabled so that's not causing the problem.

---

### Post by Giannis68 on 2008-02-03
verify your your driver installation
run fglrxinfo command
:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9700 PRO
OpenGL version string: 2.1.7276 Release

[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)

---

