---
title: "Trash Crash"
date: 2011-04-18
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by FootySr on 2011-04-18
OK I've come across my first issue. 

I was thinking it would be a good idea to drop my Downloads folder in the Unity bar, if nothing else just to fill up the bar some and so I'd have a quick link to it. :)

So I open my Home folder, drag my Downloads folder to the Unity bar but the bar doesn't open up so that I'd be able to drop it in. No problem, I just dropped the Downloads folder back on the Home Folder in the Unity bar. Now I have an alias to the Downloads folder in my Home folder where my actual Downloads folder is. 

No problem I'll just toss the alias in the trash. I can't remember if I right-clicked "Move to Trash" or if I just dragged it down. Either way, I right click on the Trash icon in the Unity bar and select "Empty Trash". FREEZE! Arrow still moves but nothing is clickable. 

I push my computers reset button, Ubuntu fires back up. I'm thinking probably just a glitch so once the desktop is back up I right click the Trash in the Unity bar and select "Empty Trash". FREEZE! Again the arrow still moves but nothing clickable. I do notice that the desktop arrow as I drag it around gives me the edge of a window icon, you know so I can expand or move a window. I could actually find the bottom right corner of this invisible window and resize it. Strange. Reset button.

Once the desktop is back up I left click on the Trash icon in the Unity bar to open the window. Click on the "Empty Trash" button in the window and the trash empties as expected. 

All is now fine. 

I looked around in the Log File Viewer thinking something would pop out at me but honestly everything in there is just above my head. Any ideas where I might actually find something that might be useful to anyone that knows? 

Thanks all! Back to playing now! :)

Jake

---

### Post by VMC on 2011-04-18
I get the freeze also and I am completely updated. Usually it happens right after I boot up. Also the icon is not right. Time for a bug report I suppose.

Oddly, if I run bleachbit, the trash gets emptied and the trash icon is restore and no freeze. So it must be something inside my home folder that's the problem.

---

### Post by wgarcia on 2011-04-19
This is a bug targetted to get fixed in the next Unity update:

[https://bugs.launchpad.net/unity/+bug/761643](https://bugs.launchpad.net/unity/+bug/761643)

---

### Post by VMC on 2011-04-19
> **wgarcia said:**
> This is a bug targetted to get fixed in the next Unity update:

[https://bugs.launchpad.net/unity/+bug/761643](https://bugs.launchpad.net/unity/+bug/761643)

Thanks. I'm not sure that's the same bug. It states that Unity crashes and restarts. Mine locks up the computer and a reboot is necessary. I'll wait for the fix in updates and see if that fixes my issue.

---

### Post by FootySr on 2011-04-19
This sounds a bit more like what I may have experienced. 
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/745830](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/745830)

However, I'm to tired and stupid to figure out how to do a "stack trace" at the moment. :D
Try again tomorrow. ;)

---

### Post by wgarcia on 2011-04-19
VMC: I think what gets locked is the graphical session, if you do CTRL-ALT-F2, log in, and ran 

sudo service gdm restart

you should be able to restart the unity session without logging out. 

In my case it was also freezing Unity completely, not restarting it.

---

