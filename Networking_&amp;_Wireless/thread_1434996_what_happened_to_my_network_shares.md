---
title: "what happened to my network shares?"
date: 2010-03-21
forum: Networking &amp; Wireless
---

### Post by RasterBurn on 2010-03-21
earlier today my wife went to move some video files from her computer to mine which isn't a problem its actually quite normal as my computer is hooked up to the HD TV and well unfortunately in the network my computer doesn't seem to see either computers network share (both computers are running UBUNTU 9.10 with SAMBA) it sees there is a windows network but unfortunately cant access it, but from her computer she can see both machines and has my public folder mounted on her computer i know samba is running on both computers can i ran nmap against her computer and it showed the 2 samba ports, and as for my computer well, i am trusting that samba is running purely on the basis that she can see my computer and connect to it. Does anyone have any idea whats going on?

---

### Post by Rocus on 2010-03-21
I have this problem also. It has been described at more places in this forum.

When I clicked 'Places', 'Network 'I used to get a list of machines in my network. Clicking on one of these machines brought up a list of samba shares. That recently changed in a 'Windows Network' icon and under that a list of windows domains. Clicking on such a domain reguires apparently a username and password but is always unsuccesfull.

The samba server in my case is a Netgear NAS with samba running and allowing guest access. On my machines running Ubuntu 9.10 this used to work bus alas.. no more.

I suspect an update of samba or a kernal update is the reason.

Somewhere on this forum somebody suggested to click on 'places'and then çonnect to server...'and then bookmark this connection. That worked as far as the file share is concerned. I see and can access the file shares.

The real reason of this problem is still unclear to me.

Another aspect of this problem is that when I try to install a samba printer on my ubuntu system, it does not find the (samba) printer share. Sometime ago ubuntu found the samba printer immediately on my netgear and I could install it as a samba network printer (I then had problems installing the driver for this printer a Pixma 3600 but that is another story which I could solve with the help of this forum).

Somewhere was suggested to reinstall a samba confuguration file /etc/samba/smb.conf but that did not work but I am almost convinced that there must be the problem.

Is there a samba expert who can help us??

---

### Post by Fenris_rising on 2010-03-21
I had this to. But mysteriously the list of machines/shares re appeared overnight. It also killed my ssh capability at the same time which also started working again. Perhaps an update issue?

regards

Fenris

---

### Post by RasterBurn on 2010-03-21
well, yesterday i couldn't even get into "windows network" to see if my shares were in there, today (after my computers been running all night, i didn't shut it down) i can access "windows network" and navigate through there to the shares, I am not to concerned with sharing the printer through samba, after all thats what i have cups and IPP (Internet printing protocol) for :D

---

