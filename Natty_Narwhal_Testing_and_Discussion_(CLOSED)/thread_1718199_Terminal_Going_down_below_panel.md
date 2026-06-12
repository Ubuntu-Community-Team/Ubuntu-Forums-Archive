---
title: "Terminal Going down below panel"
date: 2011-03-31
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by desaivarun_104lts on 2011-03-31
Hi 

I am using Ubuntu Natty Narwhal which is in alpha stage,today the beta version will be release.I have updated my system.

The  problem is with unity,when i open some applications,mainly terminal,the terminal goes down below the upper panel,and i am unable to find the icons(Max,Min,Close).I cant close them or minize them.I have to close by using alt+f4.

Only,few applications will open under the panel.exp are terminal,updatemanager..I dont know why it is happening.

Any Help  would be usefull for me.It happen only in unity,not in classic ubuntu

[http://ubuntuone.com/p/kHy/](http://ubuntuone.com/p/kHy/)          please check the screenshot.

---

### Post by wolfen69 on 2011-03-31
Try "grabbing" the terminal window by pressing Alt+left click to drag it where you want it, close it, then open it again.

---

### Post by Joeb454 on 2011-03-31
Moved to Natty Testing & Discussion.

Whenever I've had this happen, it's often due to compiz crashing. Are you able to use the terminal at all to restart compiz?

---

### Post by mc4man on 2011-03-31
It's close to  100% sure that a fresh install would stop this..
Otherwise maybe it will stop for one reason or another, though probably not

You may get some relief by switching window placement from smart to random in ccsm > place windows > placement mode

Once and a rare while I've had  similar 'something is happening that shouldn't' go away by deleting all files in here and restarting. 
~/.compiz/session/
(though usually do a fresh install weekly anyway, at least for the rest of beta 1

---

### Post by jerrylamos on 2011-03-31
Running the 29 March .iso, open "terminal".
Top line on the screen is the usual Unity applet on the left, the word "terminal" next, and some other applets and time on the right.

Second line is really the top line of the terminal window.  Says jerry@USB-HD2 in the middle, minimize full screen close on the top right, and some muddy little applet on the top left.

I use Clearlooks from appearance to put the buttons on the top right.

Anyway on early Alpha/Beta releases always use the latest one you can get since fixes (and bugs!) are coming in daily.

Jerry

---

### Post by Quackers on 2011-03-31
compiz --replace from the Alt + F2 run box sorts this out for me, although it hasn't happened for some time now.

---

### Post by r-senior on 2011-03-31
I sometimes get this after a Compiz crash (and as recently as yesterday).

Yet another way to recover the terminal window is to hit the window switcher (or Super-s if you prefer), then drag the terminal window to the centre of one of the desktops.

EDIT: Perhaps we should start calling the Super key the Unity key? :)

---

### Post by desaivarun_104lts on 2011-03-31
> **wolfen69 said:**
> Try "grabbing" the terminal window by pressing Alt+left click to drag it where you want it, close it, then open it again.

Hi Wolfen,


Alt+left click not working,the hand icon is not showing to move the window..

---

### Post by desaivarun_104lts on 2011-03-31
> **mc4man said:**
> It's close to  100% sure that a fresh install would stop this..
Otherwise maybe it will stop for one reason or another, though probably not

You may get some relief by switching window placement from smart to random in ccsm > place windows > placement mode

Once and a rare while I've had  similar 'something is happening that shouldn't' go away by deleting all files in here and restarting. 
~/.compiz/session/
(though usually do a fresh install weekly anyway, at least for the rest of beta 1
@mc4man

Wow,Its worked like a charm..Thanks a lot...

---

### Post by stanz on 2011-03-31
where might a person find ccsm?

---

### Post by 5149.5 on 2011-03-31
> **stanz said:**
> where might a person find ccsm?

Software center at first. Then Apps > Tweaks and themes.

---

### Post by mc4man on 2011-03-31
> **stanz said:**
> where might a person find ccsm?
The full name is 
compizconfig-settings-manager

(do not try to install the 'simple' version (simple-ccsm

---

### Post by stanz on 2011-04-03
Got it thanks...
used that before, then stopped- and forgot.
Couldn't get the 'simple' version anyway,,, due to natty & depend issues.

---

