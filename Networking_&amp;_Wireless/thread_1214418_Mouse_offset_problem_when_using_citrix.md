---
title: "Mouse offset problem when using citrix"
date: 2009-07-15
forum: Networking &amp; Wireless
---

### Post by linuxwonder on 2009-07-15
Hi All: I have been using Citrix to my work computer for a couple of weeks. It works OK with the exception of the annoying mouse offset. I have to position the mouse pointer above any button or menu item in order to select that item. Has anyone besides me noticed this problem?

Thanks.

---

### Post by giocogio on 2009-11-18
Any luck with this mouse offset issue? I'm seeing the same thing and was wondering if you solved it.

---

### Post by williamschrist on 2010-01-08
Hello, today I had the same problem: The mouseclick was about 20mm away from the mouse position. It only happens when I use the Citrix App seamless with maximized window. when I restore the window to original size, the mouse position is correct.
I am using Citrix ICAClient 11.0 in Ubuntu 9.10 64 Bit.

Greetings
Thomas

---

### Post by wjoyce on 2010-01-25
Got the same problem here.  Damned annoying as its the only thing stopping me from moving over to Ubuntu fulltime...

---

### Post by wjoyce on 2010-01-27
After a bit of playing around, it appears that switching the visual effects setting to none solves the mouse offset problem for me.  Anyone else care to try it?

---

### Post by scottc229 on 2010-04-25
I tried turning off visual effects and got nothing. I was wondering if it has something to do with the settings for the monitor size.

---

### Post by linuxwonder on 2010-09-20
SOLVED!!!

make sure you have everything set to full screen mode

---

### Post by Bennyba on 2010-11-01
Hi all,
I am new to this forum so forgive me if I elaborate too much.
I ran into this problem, found a workaround, and I thought I should share the knowledge. I hope it help someone.

My workaround it to NOT maximize the application in question. You can however drag it to a size close to maximum.

I run a machine with Ubuntu 10.04, GNOME desktop, on a dual monitor  system. I connect to Citrix to read email using MS Outlook, which is  corporate standard. 

The problem has some relation to Ubuntu desktop menus and taskbars. When  I had Outlook maximized on the left monitor (1280x1024), then I  observed the mouse offset. You have to point the mouse approx. 7 mm  below the menu item you want. This seems to hold for all items in the  Outlook window. 

Then I tried to Restore Down the Outlook window, and noticed the mouse  offset was gone. I tried dragging to resize the window, to see how far I  could go. My Ubuntu dekstop has got the "standard" taskbars(panels), at  the top and the bottom of the screen. Although these were on the right  monitor, there seemed to be an invisible limit for drag-resizing the  window on the left monitor, which had no panels. As if the panel was  still there. The width of a panel correspond quite nicely to the mouse  offset. If you Maximize the Outlook window, it goes beyond these  borders, and then you get the mouse offset problem.

Please note, this has been seen on single monitor systems also, so has  nothing to do with if you have dual monitors. But it seems to have  something to do with GNOME panels/taskbars.

I haven't had time to play more with it, but it would be nice to hear if anyone finds time to do so.

I'd be glad to try the solution "set everything to full screen mode", but I am not quite sure what "everything" refers to.

best regards

---

### Post by Spalding on 2010-11-17
> **wjoyce said:**
> After a bit of playing around, it appears that switching the visual effects setting to none solves the mouse offset problem for me.  Anyone else care to try it?
Thank you!  Worked for me in Ubuntu 10.04.  I had similar problems in previous versions of Ubuntu and turning off effects worked there also.

---

### Post by jtrickey on 2011-01-27
+1 for the "turn off visual effects".

I'm using a HP notebook with a smaller screen (1280X800), disabling them did the trick for me in 11.04.  Thanks for the tip!  :)

---

### Post by oldblueday on 2011-03-09
It also worked for me. Thanks for the information. Though I did rather like the fancy effects, I can live without them until/if it gets fixed.

---

### Post by ejarg7 on 2011-04-25
The offset problem is really a pain, but there's an easy fix to this. Open CompizConfig Settings Manager, under Utility->Workarounds, check "Legacy Fullscreen Support".  That should do it. I'm running citrix with Natty now and it works great.  :)

---

### Post by sentinelace on 2012-02-16
I am running 11.10 and adding the workaround fullscreen but still have the issue :(

---

### Post by smad777 on 2012-02-28
ISSUE RESOLVED!

"Log in selecting "UNITY 2D" has resolved the issue for me".


My Issue:
===========
I am using ubuntu 11.10 (desktop). Tried connecting to my office n/w using citrix ICA client ( with google chrome browser) and encountered this mouse offset issue. After googling around, I tried the below option and it worked. 

By default, I used to log in to "UNITY" and facing this mouse offset issue. 

Resolution: I tried to log in to "UNITY 2D" and this has resolved the issue.

I hope this works for every one. All the best!

Thanks,
SMAD777

---

### Post by mutzelpiddi on 2012-07-02
I am running Ubuntu 12.04 and activating the "Legacy Fullscreen Support" solved the issue.
Thank you!

---

