---
title: "VNC or SSH -X"
date: 2007-11-27
forum: Mythbuntu
---

### Post by Calash on 2007-11-27
I notice that a lot of people use VNC for managing there headless Mythbuntu systems.  When on Fedora I had this setup and while it worked ok, I found that the setup was quite a pain, and the VNC shell would run slowly at times.


With my current setup I have been using SSH -X to terminal into my Myth box, then I can load GUI apps by calling them from the command line.  Using a keyfile I can lock it down as well, so only I can SSH into the box.

So, my question is what remote management solution do people prefer and why.  This is more out of curiosity than anything else, as I am quite happy with the SSH setup.


Thanks

---

### Post by Yoooder on 2007-11-27
A big difference in the way the two work, and the value that they provide is in what you get when you log in.

When you connect to a VNC server you are connecting to an established desktop session, so if I wake up and am physically at the computer and leave open a webpage then later when I VNC in I will view the desktop just as if I were still in front of the PC.

When you SSH in it will provide you with a clean slate, basicallly your same user account is logged in multiple times.

Of course this is a really general overview, and with some playing around you might be able to make one behave like the other.  I personally prefer using SSH since I typically remote in from work, and it makes sense for me to start with a fresh session.

---

### Post by superm1 on 2007-11-27
For me, this all boils down to what administrative tasks I need to be doing.

If they are items that will be needing no GUI, I always use normal SSH.

If they will need a GUI, it depends if they will be a fullscreen app to me as well as if i'm working wirelessly.

SSH -X is brutally slow over wireless, so in that case VNC.
If its a full screen app, I prefer VNC too so that I don't have to run it fullscreen.

---

### Post by road2elysium on 2007-11-27
> **superm1 said:**
> For me, this all boils down to what administrative tasks I need to be doing.

If they are items that will be needing no GUI, I always use normal SSH.

If they will need a GUI, it depends if they will be a fullscreen app to me as well as if i'm working wirelessly.

SSH -X is brutally slow over wireless, so in that case VNC.
If its a full screen app, I prefer VNC too so that I don't have to run it fullscreen.

Pretty much same here.  If it doesn't require a GUI, I'll just SSH in.  If a GUI admin is required, VNC for me.  I like being able to view the desktop if I'm going to be using the GUI.

---

### Post by Calash on 2007-11-27
I never had any slowness issues, but to be fair the only time I have tried to use it on Wireless is with my old iBook g3....so I probably did not notice any slowness issues :)

Good point on the full screen apps, especially something like Mythsetup.  I do not mind it much myself, but I can see the benefit of having that restricted to the VNC windows.

---

### Post by uopjohnson on 2007-11-27
I third that.  SSH is for quick commands.  VNC is for anything that requires GUI or multiple screens open..  I also use vnc when my laptop is closer that the remote control.

---

### Post by ubnewbie2 on 2007-11-27
> **Calash said:**
> I notice that a lot of people use VNC for managing there headless Mythbuntu systems.  When on Fedora I had this setup and while it worked ok, I found that the setup was quite a pain, and the VNC shell would run slowly at times.


With my current setup I have been using SSH -X to terminal into my Myth box, then I can load GUI apps by calling them from the command line.  Using a keyfile I can lock it down as well, so only I can SSH into the box.

So, my question is what remote management solution do people prefer and why.  This is more out of curiosity than anything else, as I am quite happy with the SSH setup.


Thanks

I use ssh for terminal access but haven't tried x forwarding.  How do you do that?

---

### Post by Calash on 2007-11-28
Instead of using 

$ssh host

use 

$ssh -X host

This will enable the X forwarding.  Then run a gui command from the terminal and it will open up as a window.  You may have to gksu first to get root privileges for things such as update manager or the Mythbuntu control center but it works very well.

If you setup a public/private SSH key you get an extra level of security to the setup.  I disabled the login and just use a password encrypted key for access and have had no problems yet with it.  I did have some people try to hack SSH once, but since it was not setup to accept passwords it just failed.

Both methods are a great way to remotely manage your MythTV system.

---

### Post by newlinux on 2007-11-28
When I'm at home on my local network I use ssh -X for pretty much all administration. It is fast enough for me, and even over my wireless connection it is fast enough. When I am connecting from outside my LAN I used to use VNC, but I have found nxserver to be so much faster and cleaner, and allows me to create a completely new X session and reconnect to it.

For security over the WAN I have employed denyhosts, and security by obscurity (changed the default port #) - as nxserver uses ssh and compression.

---

