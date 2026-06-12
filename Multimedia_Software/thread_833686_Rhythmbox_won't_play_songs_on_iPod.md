---
title: "Rhythmbox won't play songs on iPod"
date: 2008-06-18
forum: Multimedia Software
---

### Post by Neureo on 2008-06-18
I'm using the Ubuntu Live CD. I plugged in my iPod classic and all of my music showed up fine in Rhythmbox, but when I go to play something, nothing happens. The bar that shows where you are in the song doesn't move at all...nothing happens. 

This is what it ends up looking like--

[IMG]http://i30.tinypic.com/2dtr7ty.png[/IMG]

I already tried ```
sudo apt-get install ubuntu-restricted-extras
```but I think there were a few errors. 

Does anyone know how to fix this? I really want to listen to my songs! 

Thanks!

---

### Post by kostkon on 2008-06-18
> **Neureo said:**
> I'm using the Ubuntu Live CD. I plugged in my iPod classic and all of my music showed up fine in Rhythmbox, but when I go to play something, nothing happens. The bar that shows where you are in the song doesn't move at all...nothing happens. 

This is what it ends up looking like--

[IMG]http://i30.tinypic.com/2dtr7ty.png[/IMG]

I already tried ```
sudo apt-get install ubuntu-restricted-extras
```but I think there were a few errors. 

Does anyone know how to fix this? I really want to listen to my songs! 

Thanks!
Go to *System -> Administration -> Software Sources* and check if the *Multiverse* repository is enabled. If it isn't, activate it and then try again to install the *ubuntu-restricted-extras* package.

You'll have to do the above every time you run the Live CD.

---

### Post by Neureo on 2008-06-18
Yes, it is...

I tried uninstalling then reinstalling ubuntu-restricted-extras, and grabbed a screencap of the error: 

[IMG]http://i25.tinypic.com/2ykhv7k.png[/IMG]

(By the way--I know I'll have to repeat this process with every reboot off the CD. I'm systematically checking out the aspects of Ubuntu I'd use every day: word processing, web browsing, text editing, and so forth, now music listening. :) ) 

Thanks again!

---

