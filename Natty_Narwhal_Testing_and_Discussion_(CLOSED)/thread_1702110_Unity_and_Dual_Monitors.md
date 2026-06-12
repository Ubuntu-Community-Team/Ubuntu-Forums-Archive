---
title: "Unity and Dual Monitors"
date: 2011-03-07
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by gdonwallace on 2011-03-07
So I decided to download the Alpha 3 of Natty this morning.  So far it looks pretty good.  It will take some getting used to though.  Not real comfortable with the search from the "Ubuntu" button.  I do like the idea of a unified menu though.  That also brings up my question, and what may cause me to use a different desktop.  How does Unity work with a dual monitor setup?  Is the unified menu only on the "Main" monitor, does it stretch across the top of both menus or do the programs on the second monitor continue to look like they did pre-Unity...they have there own menu.

---

### Post by castrojo on 2011-03-07
Right now the menu shows up on the primary monitor, which is a killer for me too, I just turn off the global menu on my dual system.

It's supposed to have a menu on each monitor, but the bug isn't fixed yet: 

[https://bugs.launchpad.net/unity/+bug/683084](https://bugs.launchpad.net/unity/+bug/683084)

---

### Post by hamax on 2011-03-08
Is it possible to turn on the global menu just for applications that are maximized and on the primary monitor?

---

### Post by gdonwallace on 2011-03-08
I guess I will have to keep an eye on the bug report then.  It wont keep me from getting the final release when it hits, but I will end up using either Gnome original, or another desktop.  Been playing around with a couple alternatives on my laptop to get a feel for them.  

Thanks for the info

---

### Post by jerrylamos on 2011-03-08
Unity Absolute Mess with external monitor on netbook Acer Aspire.

External monitor at 1024x768 works fine with Meerkat.

Unity Natty somehow occupies an 800x600 box on lower left corner of the 1024x768.  Various other artifacts show up on the rest of the 1024x768.

Crucially, the cursor thinks it is on 1024x768, so selecting a blank space up high on the left somehow starts one of the launchers on the lower left.

Busted big time.  Such a mess I didn't see how to do an ubuntu-bug.

*** update!

With update linux-image-2.6.38-6 external monitor now working on netbook Acer Aspire.

After update the 1024x600 netbook screen and the 1280x1024 external monitor mirrored some sort of off center 800x600 screen.  That enabled going to Applications Monitors turn off mirror, turn off laptop screen, then set external monitor to 1280x1024.  Worked fine in both Unity desktop and Classic desktop.

Solved for my purposes.

Jerry

---

### Post by anmar on 2011-03-11
I have a thinkpad x201 with ultrabase and I have an asus 25" LCD hooked up. When running unity, the desktop is a mess. With the default GNOME, it works fine. 

I didn't file a bug since I know Unity has a ways to go regarding dual screens. However, X is another story. I find it less stable and had some regressions that I filed a bug a about. 

BTW, I am using Intel driver.

---

### Post by jerrylamos on 2011-03-12
See my *** update above.  Unity now running on external monitor O.K. at update that included 2.6.38-6.  Now my intent is to run the big external monitor.  I don't try to use both screens at once.

Jerry

---

