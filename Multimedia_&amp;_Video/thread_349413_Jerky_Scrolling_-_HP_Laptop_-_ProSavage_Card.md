---
title: "Jerky Scrolling - HP Laptop - ProSavage Card"
date: 2007-01-30
forum: Multimedia &amp; Video
---

### Post by nerm on 2007-01-30
Hello,

I have installed Edgy on a friends laptop (5/6 yr old HP) and everything has gone reasonably well. However I have encountered slow, jittery vertical scrolling in apps such as Firefox.

I think that the scrolling issue is related to the graphics card (ProSavage PM133) and it's drivers.

Does anyone have any advice as to what I could do to try and resolve this problem, should I try and get hold of some relevant drivers? change the defualt resolution?
 
I have spent a couple of hours investigating the probem online but to no avail - it would seem the graphics card is a a bit outdated and not being either Nvida or ATi seems to lack the support of other big name cards.
 
My knowledge of this stuff is very basic so any information however obvious would be of great benefit.

Neal

---

### Post by nerm on 2007-01-30
Hi All,

After more ferreting about on forums I think I have managed to solve the problem. Although my solution is probably the least elegant it worked for me.

I carried out the steps below.

1. Identify what graphics card was on the machine by looking at System > Administration > Device Manager (Identified it was a ProSavage PM133).

2. Discovered by visiting this website [http://www.die.net/doc/linux/man/man4/savage.4.html]("http://www.die.net/doc/linux/man/man4/savage.4.html")  that the 'Savage' driver needed to be installed on my machine.

3. Then discovered that I could fiddle with the graphics setup by typing the following n the command line:```
sudo dkpg-reconfigure xserver-xorg
```

4. Selected the 'Savage' driver from the list presented and answered the questions presented to me with the default options.

5. Rebooted the machine and could scroll smoothly.

Cheers,

---

