---
title: "custom launcher flashes for 5 seconds"
date: 2011-04-17
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by davidmohammed on 2011-04-17
Hi there,
  if I create my own launcher and drag this into the unity "dock" - the icon flashes for about 5 seconds when I click it.  This stops me from being able to click on it again within 5 seconds. Any ideas what I need to do to allow me to click on it within that time-frame?

i.e.

right click the desktop - create launcher.

In the command type 

echo "hi"

(n.b. just an example - it doesnt matter what command is written here it seems)
drag and drop the launcher into the unity doc

---

### Post by terry_gardener on 2011-04-17
when you create a launcher using right click on desktop and create launcher make sure that it works first by double clicking the desktop icon before dragging to the launcher. 

i have just tried creating an icon using this method and it works ok, 

when i use you example select application in terminal and type the command the terminal flashes up then disappears. 

the example i did that worked is: 

right click desktop and create launcher. 
leave the drop down at application.
give it a name.
under the command click browse and select a pdf file.
you should have the path to the pdf file in the command field. 
at the beginning of this field type evince 

so you should have evince /path/to/file.pdf
click ok 

double click the desktop icon to make sure it works if it does drag to launcher and then open and it should work fine. 

Note: due to the fact that we have not picked a icon then there will not be one in the launcher, it will just be blank where the icon would be.

---

### Post by davidmohammed on 2011-04-17
hmmm - curious.

This is what I'm trying to run

I does work fine - just have to wait 5 seconds between clicks...

```
xte "keydown Super_L" "key w" "keyup Super_L"
```

n.b. you need to install the package xautomation to get this to work.

---

### Post by terry_gardener on 2011-04-17
sadly i don't think you are going to get round this.
 
i think the cleaner solution would be open ccsm goto scale plugin and then select binding tab and assign a screen corner to do this task. 

then when you move the mouse to the corner of your choice it scales all apps that are open. which is the same as pressing the super+w key on the keyboard.

---

