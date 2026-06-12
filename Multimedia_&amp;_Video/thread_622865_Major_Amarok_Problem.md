---
title: "Major Amarok Problem"
date: 2007-11-25
forum: Multimedia &amp; Video
---

### Post by helliewm on 2007-11-25
What is wrong with Amarok I am unable to launch it
?. See Screenshot 

I have the same problem on my laptop too. I have tried completely uninstalling it and that has not helped.

Helen

---

### Post by koleoptero on 2007-11-25
That screenshot isn't helpful. Next time take a screenshot with a delay of 1-2 seconds.

---

### Post by Whiffle on 2007-11-25
dcopserver isn't running.  Thats all I know.

---

### Post by helliewm on 2007-11-25
I removed CRossover Office as that was the last thing I installed. That has stopped the dcopserver message. But now when I load Shoutcast Radio I get this messages. 

Any ideas?

Helen

---

### Post by helliewm on 2007-11-25
Edit better Screenshot. THis occurs when I try to load Shoutcast Radio

---

### Post by helliewm on 2007-11-25
Rebooted all this now fine. It was something to do with Crossover. As when I search files for "dcopserver" Crossover tried to open the file. Removing CRossover and a reboot solved the problem. I please I was still at the trial phase and had not paid for it. I will stick to Wine.

Helen

---

### Post by n3tfury on 2007-11-25
> **koleoptero said:**
> That screenshot isn't helpful. Next time take a screenshot with a delay of 1-2 seconds.

next time you decide to take a SS, listen to this advice, thanks.

---

### Post by helliewm on 2007-11-25
Problem was Amarok get sticking its "pop ups" over the Screenshot so I could not adjust the seconds. They also stayed there and I could not move them at all. It was acting almost like when you get Windows virus and nothing behaves itself.

---

### Post by kodoku on 2007-11-25
since you're running gnome... try running kdeinit, then follow up with amarokapp

---

### Post by Lostincyberspace on 2007-11-25
you can also just press the Printscreen button (first of the three little buttons to the right of f#'s) and it will take a screen shot for you.

---

### Post by -grubby on 2007-11-25
I believe you press the pause/break button and then the print screen/sys RQ button

---

### Post by Lostincyberspace on 2007-11-25
> **nathangrubb said:**
> and then I believe you press the pause/break button and then the print screen/sys RQ button

:confused:

I don't know what you are meaning but the image below has an arrow to the key, you have to open it in another tab to see the arrow,

---

### Post by msinkm on 2007-11-29
If you have the same problem I did, you might have a problem with the permissions on the .kde folder in your home folder.  I have run into this problem a couple of times.  For some reason, the folder gets created with root privileges with owner as root.  To fix it, enter the following commands in a terminal:

sudo chown -R [COLOR="Red"]user:user[/COLOR] ./.kde

where [COLOR="Red"]user:user[/COLOR]

is your user id and group.  I had these problems with kde under ubuntu until I did this. 

Good luck!

---

### Post by crazy ivan on 2007-12-04
I have the same problem.
I added amarok to session>starting. Removed it later. But now it still starts up everytime, from time to time it says "could not connect to network socket",, "dcopserver"..., hangs up And it crashes "tomboy". Since I changed rights for ".kde" it crashes everytime.

If I start tomboy and amarok by hand however, there is no such problem. Im confused.

---

