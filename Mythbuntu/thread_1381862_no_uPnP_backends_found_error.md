---
title: "no uPnP backends found error"
date: 2010-01-15
forum: Mythbuntu
---

### Post by angelsguitar on 2010-01-15
Hi. I'm currently configuring for the first time a Mythbuntu 9.10 system at home (I'm a regular Ubuntu user, but this is my first time dealing with MythTV and Mythbuntu). Basically I'm configuring a main backend with front end connected to my DirecTV STB using a Hauppauge PVR 150.  I'll be adding additional frontends to this setup too.

In summary, I installed Mythbuntu 9.10 on the machine as a primary backend with frontend.  Did all the standard configurations of the backend and frontend using the installer's wizards. Replaced network manager with wicd and assigned a static ip address to the machine (to make it easier for others frontends to connect).  Both the backend and frontend on the same machine are pointed to the same ip address, which is the static ip address I assigned the machine using wicd.  

However, everytime I boot the machine I get the setup screen that asks me to choose a language (it guives a long list with English at top preselected).  When I choose English, it then gives me the following error message in a dialog box:

"No uPnP backends found"

After that, it takes me to the Database configuration settings (same as the first two configuration pages on the frontend general setup). Since I already configured this, I always click next until it finishes.  After, that, the frontend is launched without problems.

I'm able to watch TV using the frontend on that machine, and even on remote frontends, but everytime I boot those computers I get the same prompts and error message.

How can I prevent this from happening everytime I boot the computer? Thanks in advance for helping a MythTV/Mythbuntu noob like me :D

---

### Post by angelsguitar on 2010-01-18
Well, I added an additional wireless laptop frontend.  Same problem on it to.  I can watch TV on the remote frontend but always get the language configuration screen, "no uPnP backends found" message and database configuration screen.

Any help is very welcome

---

### Post by ahood on 2010-01-18
Hello,

I can think of two potential causes.

A. Gateway/router does not have static IP address, thus it has problems routing information to the backend machine.

B. Frontend is trying to connect over the network to the backend, which is on the same machine, but the machine itself hasn't completed connecting to the network wirelessly. By the time you complete the wizard, which is simply confirming the data already entered, the machine has successfully configured itself to the network and everything works.

C. Both?

Below are a couple of forum posts that might help.

[[COLOR="Blue"]**[SOLVED] Frontend Autostart issues**[/COLOR]]("http://ubuntuforums.org/showthread.php?t=835763&highlight=wireless+frontend+delay")

[[COLOR="Blue"]**[SOLVED]  9.10 - after reboot Database error can not connect/ No UPnp**[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1350988&highlight=wireless+frontend+delay")

[[COLOR="Blue"]**ION Frontend 2 Problems,**[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1378621&highlight=wireless+frontend+delay")

I hope one of the above helps.

If you find a solution, please post it.

With kind regards,

---

### Post by angelsguitar on 2010-01-21
> **ahood said:**
> Hello,

I can think of two potential causes.

A. Gateway/router does not have static IP address, thus it has problems routing information to the backend machine.

My router does has a static ip address assigned.  But I'll verify this, just in case.

> **ahood said:**
> B. Frontend is trying to connect over the network to the backend, which is on the same machine, but the machine itself hasn't completed connecting to the network wirelessly. By the time you complete the wizard, which is simply confirming the data already entered, the machine has successfully configured itself to the network and everything works.

This may be true for the backend/frontend machine, but I'm having the same problem with remote frontends too.  I mean, once I turn on the backend, and it's all up and running, if I turn on another frontend machine on the network, I will get the same prompts and error message.

I will look into the links you provided anyway; maybe I overlooked something.  Thanks for all your suggestions.

Update;  Well, I was wrong: the remote frontends DO work perfectly after the backend is running. Seems the problem is in the frontend/backend machine only.

---

### Post by angelsguitar on 2010-01-22
> **ahood said:**
> 

[[COLOR="Blue"]**[SOLVED] Frontend Autostart issues**[/COLOR]]("http://ubuntuforums.org/showthread.php?t=835763&highlight=wireless+frontend+delay")


Well, thanks ahood.  The above thread solved the issue.  As you said, the frontend was being launched too early.  Giving a few seconds of delay solved the issue.

---

