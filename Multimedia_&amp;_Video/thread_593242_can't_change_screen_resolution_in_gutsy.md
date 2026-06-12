---
title: "can't change screen resolution in gutsy"
date: 2007-10-27
forum: Multimedia &amp; Video
---

### Post by grahams on 2007-10-27
Seen a few similar posts to this, but no fix yet. 

In feisty I could change my screen res when needed. 
In gutsy I can't Is there a way to work around this? is it submitted as a bug or is it a feature?

---

### Post by grahams on 2007-11-03
bump 

is anyone able to change their screen resolution in Gutsy?

---

### Post by orange2k on 2007-11-03
Go to administration-screens and graphics.
Set your monitor type and all resolutions your monitor can support will become available...

Thats how it worked for me in Gutsy - I didn`t even have to view my xorg.conf file...

---

### Post by grahams on 2007-11-03
thanks for the reply.

Yeah I tied that, There is no choice for a Compaq evo n610c laptop screen. Even when I try to force it to a lcd 1400x1050 it always comes back to plug and play and i'm stuck at the same res.

Gutsy so far is a disappoint. I'm close to relaoding feisty or base debian

---

### Post by Roaster on 2007-11-04
> **orange2k said:**
> Go to administration-screens and graphics.
Set your monitor type and all resolutions your monitor can support will become available...

Thats how it worked for me in Gutsy - I didn`t even have to view my xorg.conf file...

I had the same problem with my resolution on an Acer AL1916W and your answer worked great for me, thanks

---

### Post by grahams on 2007-11-07
Hi Roster

Was your monitor recognized or did it just come up as "plug and play" as mine does?

---

### Post by grahams on 2007-11-24
Bump

My laptop screen is found only as 'plug n play' and I can not resize it from the native 1400x1050.

Has anyone found a work around for this?

---

### Post by circuz_phreak on 2007-12-29
ya, everytime i change the settings they just revert back to the old ones without changing.  When I do a test, it works...but than clicking ok just reverts it all back.  Very annoying, would love to know a fix.

---

### Post by bwtranch on 2007-12-29
I tried it too. It just reverts back. I think I have a conflicting ATI driver still mucking up the works. I installed a new nvidia card for Christmas, but so far, no gas. I have never had anybody on this forum actually help me solve a problem. I've done it for other people. But, everything I've had a problem with, I did it myself. Most of the stuff they tell you to do is outdated by the time it gets to us poor smucks anyway.:twisted:

---

### Post by webbie180 on 2008-01-09
Same here, using samsung syncmaster 710v.

---

### Post by zxscooby on 2008-01-09
I have a similar problem with my compaq presario v2000 ,i can change screen size and resolution any time i want as long as it isnt the right one for my panel , when i select the correct size and/or widescreen , it reverts it back to 800x600. 
i can get it close enough but images are still a little squashed

---

### Post by dashiznit on 2008-02-05
when i first installed ubuntu gutsy on my hpdv6000 and  configured my nvidia drivers i was able to set the resolution up until i downloaded the newest kernel update it was fine now it only recognizes as plug and play. i need to fix this if anyone finds a fix please let me know.

---

### Post by joehill on 2008-02-20
Same problem with an nvidia card.  I can change the screen resolution either with "Screen Resolution" (in Preferences) or "Screens and Graphics" until I'm blue in the face, it has no effect on the resolution and when I open up the dialog again, it always comes back to the same resolution.  My xorg.conf file has all the right resolutions, but I'm only able to use the highest one.

---

### Post by joehill on 2008-02-20
Just ran "sudo dpkg-reconfigure xserver-xorg" and selected "nvidia" driver and all resolutions I wanted, then restarted X.  I can now select my resolution, but emerald no longer works.  I'll keep trying to see what I did wrong.

Edit:
Oh, I forgot, every time you reconfigure xorg with nvidia, you have do do this afterwards for emerald to work:
sudo nvidia-xconfig --add-argb-glx-visuals -d 24
Now it works.

---

### Post by grahams on 2008-05-07
Solved

add the following to xorg.conf in the device section

Option "NoDDC"

---

### Post by Afrodiziak on 2008-06-04
I have the same issue. I'm running 8.04 and don't have screens & graphics under administration, where should I look?

---

