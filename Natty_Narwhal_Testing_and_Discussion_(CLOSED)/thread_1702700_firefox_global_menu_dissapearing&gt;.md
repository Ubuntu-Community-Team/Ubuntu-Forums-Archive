---
title: "firefox global menu dissapearing?&gt;"
date: 2011-03-08
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by ELD on 2011-03-08
Just seeing if i need to report a bug or if it's already reported.

My firefox beta global menu randomly disappears and i have to close and re-open, anyone else getting this?

---

### Post by dino99 on 2011-03-08
all is fine here, maybe check your system:

sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a
sudo dpkg-reconfigure firefox

---

### Post by chrisccoulson on 2011-03-08
That's not going to help.

There is an issue with the Unity updates yesterday where menus sometimes disappear after minimizing a window, which I'm currently investigating

---

### Post by ELD on 2011-03-08
> **chrisccoulson said:**
> That's not going to help.
 
There is an issue with the Unity updates yesterday where menus sometimes disappear after minimizing a window, which I'm currently investigating
 
That happens to me, i'm pretty sure it is exactly that.
 
It still has the name of the application in the bar, but you hover over and when the menu usually displays it goes blank.

---

### Post by Kirk M on 2011-03-08
This is also happening to me and has been for awhile especially when Firefox starts up maximized. I simply collapse Firefox into an un-maximized window and then maximize it again and the global menu is available and works normally again.

---

### Post by sgage on 2011-03-25
> **Kirk M said:**
> This is also happening to me and has been for awhile especially when Firefox starts up maximized. I simply collapse Firefox into an un-maximized window and then maximize it again and the global menu is available and works normally again.

That doesn't work for me. I am still having this problem. I did remove firefox-globalmenu, which works out fine. But I'd like to see them fix the globalmenu...

---

### Post by _Narcisse_ on 2011-04-05
I get this bug too on an updated beta 1. The global menu consistently disappears when the Firefox window is minimized. 
Should I (we) report the bug on Launchpad ?

Thanks

---

### Post by cor2y on 2011-04-05
Same here, the only fix i have found is to restart firefox, the firefox global menu seems to be buggy but its still beta so we will see.

---

### Post by ELD on 2011-04-05
> **_Narcisse_ said:**
> I get this bug too on an updated beta 1. The global menu consistently disappears when the Firefox window is minimized. 
Should I (we) report the bug on Launchpad ?
 
Thanks
 
Report the bug and link is to it so we can comment on it with our findings (i can't as i'm at work).

---

### Post by _Narcisse_ on 2011-04-05
I reported it here: [https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/751772](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/751772)
Hope I did it the right way, tell me if I didn't. I reported it with Apport as a firefox-globalmenu bug but it filed it as firefox bug.
Maybe it should have been submitted under Unity.

EDIT: Obviously it was already submitted because it was marked as invalid and duplicate of [Bug #718926]("https://bugs.launchpad.net/ubuntu/+source/bamf/+bug/718926").

---

