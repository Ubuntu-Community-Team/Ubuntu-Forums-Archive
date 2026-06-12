---
title: "Applications-System-Places missing from my panel.."
date: 2011-04-12
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by midhunbose on 2011-04-12
hi guys.

i recently installed ubuntu natty beta 1. i cannot find the Applications-System-Places in my panel and i am finding it difficult to launch my applications which are not there in the launcher.. please help!!!

---

### Post by Rex Bouwense on 2011-04-12
I had this problem and here is the solution that worked for me.
[http://ubuntuforums.org/showthread.php?t=1368543](http://ubuntuforums.org/showthread.php?t=1368543)
Enjoy.

---

### Post by seawolf167 on 2011-04-12
You can also reset the panels to their default by opening a terminal (hit [ALT][F2], then type in *gnome-terminal*) and entering the following commands

```
gconftool –-recursive-unset /apps/panel
rm -rf ~/.gconf/apps/panel
pkill gnome-panel
```

---

### Post by TexasRussian on 2011-04-12
I'm pretty sure 11.04 (Natty Norwhal) doesn't have the typical Applications-Places-System menus. Instead it has 'lenses' you need to click the BFB (Big Freaking Button) on the top left of the screen, it has the Ubuntu symbol on it. Then you should be good from there..

---

### Post by computerandu on 2011-04-12
For launching the application click on the Ubuntu logo on the top left.

If you want other stuffs like the system tools, synaptic manager etc ...click on the turnoff button (on the top right)...the last option in this drop down is "system settings"...click on it and you can see all the "System" applications.....:P

---

### Post by midhunbose on 2011-04-12
thanks for the replies..

i tried typing in the name of an installed application in the BFB search box but nothing is shown.. i also have Media apps, Internet Apps, More Apps and Find Files grayed out.

---

### Post by Elfy on 2011-04-12
move to natty

---

### Post by midhunbose on 2011-04-12
@forestpiskie 

i am using natty beta ....

---

### Post by rajeev1204 on 2011-04-12
Ubuntu uses a new interface called unity now, and you need to click on the items on the left panel to find things.

In the top left, type what you need and it will display stuff.

If you see the last 2 items on the left panel at the bottom, they are your applications and files and folders menu.Try those and see if you are comfortable with it.Also all application windows now have the menu at the top panel ,so move the mouse over to the top panel to view/use the menus.

Wont take much time to learn it.If you dont like it just log out and during login , at the bottom select 'ubuntu classic' and login again.You will have the old style menus back.

---

### Post by Elfy on 2011-04-12
> **midhunbose said:**
> @forestpiskie 

i am using natty beta ....

I know, that's why the thread was moved from ABT, which is for released versions - as are all the normal support forums, to the development forum.

At some point we will stop moving development version threads, but that point has not been reached yet.

---

