---
title: "Can't get window to open completely"
date: 2011-01-07
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by DougieFresh4U on 2011-01-07
This is a complete up to date kernel .12
AMD 5200 x2
ATI Radeon HD3200
Stock install with no 'extras'
When ever I open any thing, it does not open to 'full size' and I can not access the top of any screen as it's hidden under the top panel, so I can't access any buttons to enlarge window to 'full' screen. Kind of difficult to move between tabs as they are hidden under top panel as well.
Would be happy to hear of any 'magic' to get this figured out.
Thanks

---

### Post by cariboo on 2011-01-07
I had the same problem with firefox the other day, all I did was kill firefox, and restart it, problem solved.

---

### Post by smuthavarapu on 2011-01-07
I was having this problem when i connected to External Monitor, thats was with the Initial install.

but problem gone after upgrading to latest kernal version.

---

### Post by DougieFresh4U on 2011-01-07
> **cariboo907 said:**
> I had the same problem with firefox the other day, all I did was kill firefox, and restart it, problem solved.
No luck with trying that. I can't even 'grab' the bottom corner of window to enlarge.

---

### Post by dino99 on 2011-01-07
have had this problem last week, and i think its something about "saved last settings". Try to move these windows to catch either top or bottom & resize them , then might need to close them. Or try a whole reconfiguration:

sudo dpkg-reconfigure -phigh -a
(could be long, dont stop it)

or: sudo dpkg-reconfigure gnome-panel
or: metacity --replace &
or: compiz --replace &

at last: delete .gconfd (/home) and reboot (probably the easiest way)

---

### Post by ronacc on 2011-01-07
can you move the window around with alt + lmb and drag ? and are you using compiz ?

---

### Post by DougieFresh4U on 2011-01-07
> **ronacc said:**
> can you move the window around with alt + lmb and drag ? and are you using compiz ?

Forgive my ignorance but you lost me on 'lmb'
No compiz
Thanks

---

### Post by Yougo on 2011-01-07
he means left-mouse-button ;-)

did it work?

here's a list of keyboard shortcuts for managing windows (it's for ubuntu 7.04 i see, but i believe it still applies):
[https://help.ubuntu.com/7.04/user-guide/C/keyboard-skills.html](https://help.ubuntu.com/7.04/user-guide/C/keyboard-skills.html)

with alt+F7 you can move the window
with alt+F8 you can resize the window

---

### Post by ronacc on 2011-01-07
lmb means left mouse button  if you hold the alt key and click (and hold) the left mouse button anywhere in the window you can drag it.
 
try restarting your window manager sometimes on startup i don't have the top window bar showing (where the buttons are ) restarting the WM brings them back , compiz for me , metacity if you arent using compiz . in a terminal ```
 metacity --replace & 
```

---

### Post by DougieFresh4U on 2011-01-07
> **Yougo said:**
> he means left-mouse-button ;-)

did it work?

here's a list of keyboard shortcuts for managing windows (it's for ubuntu 7.04 i see, but i believe it still applies):
[https://help.ubuntu.com/7.04/user-guide/C/keyboard-skills.html](https://help.ubuntu.com/7.04/user-guide/C/keyboard-skills.html)

with alt+F7 you can move the window
with alt+F8 you can resize the window
Thanks, no work though
> **ronacc said:**
> lmb means left mouse button  if you hold the alt key and click (and hold) the left mouse button anywhere in the window you can drag it.
 
try restarting your window manager sometimes on startup i don't have the top window bar showing (where the buttons are ) restarting the WM brings them back , compiz for me , metacity if you arent using compiz . in a terminal ```
 metacity --replace & 
```
now that worked, I can see all that I am supposed to see :p
off topic ronacc: I can remember Narcoossee Road  down off Goldenrod and going down under the Beeline which I see they changed the name to Beachline, silly name :confused:

---

### Post by ronacc on 2011-01-07
if you've ever been down narcossee rd and seen the narcossee hardware store I'm about 1 mile from there .

---

