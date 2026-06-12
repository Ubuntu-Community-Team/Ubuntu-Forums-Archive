---
title: "Wired Ethernet working but no Wireless"
date: 2012-09-16
forum: Networking &amp; Wireless
---

### Post by CWied1394 on 2012-09-16
Hey all, I'm new to Ubuntu and really like it so far, but the only problem I'm having is connecting to wifi.

Now I got tired of trying to just let it connect, so I connected a wired Ethernet cable and it works perfectly. 

Is there anybody that could help me solve this problem please?

Info:
- windows XP
- Ubuntu 12.04 LTS (dual boot)
- Linksys wireless

Now, I have the Linksys installer CD but I can't figure out how to get it to go through the installation process. It says something along the lines of it isn't a .zip file and I can't do anything with it. I can see all the files that are in the CD, but I can't run it through the installation process like I could on XP.

---

### Post by Galdov on 2012-09-16
not sure why excactly, because has happened to me very randomly, but sometimes when I just install Ubuntu cant see the wireless connections, it happened just today, so I did the same and conected the eth0 (wired connection), then i run the update manager, download and installed all the updates, and after reboot there was my wireless WPA2 connection

maybe you have luck with that, otherwise i have not idea

---

### Post by CWied1394 on 2012-09-16
> **Galdov said:**
> not sure why excactly, because has happened to me very randomly, but sometimes when I just install Ubuntu cant see the wireless connections, it happened just today, so I did the same and conected the eth0 (wired connection), then i run the update manager, download and installed all the updates, and after reboot there was my wireless WPA2 connection

maybe you have luck with that, otherwise i have not idea

That's what I've done. I installed all the updates and looked to see if I have any drivers that I need to install. There was an update for my NVIDIA graphics card so I enabled that, but was nothing there about a wireless card.

---

### Post by CWied1394 on 2012-09-16
Also, the wireless adapter I'm using is a Linksys WUSB54G v.4.

---

### Post by dandnsmith on 2012-09-17
> **CWied1394 said:**
> 
Info:
- windows XP
- Ubuntu 12.04 LTS (dual boot)
- Linksys wireless

Now, I have the Linksys installer CD but I can't figure out how to get it to go through the installation process. It says something along the lines of it isn't a .zip file and I can't do anything with it. I can see all the files that are in the CD, but I can't run it through the installation process like I could on XP.

I think that, as is the usual case, the Linksys CD will have an installer for Windows but not for any linux.

There may be a set of installable files on the Linksys site - or you might have to investigate ndiswrap together with the .inf file which Windows uses.

---

### Post by CWied1394 on 2012-09-18
> **dandnsmith said:**
> I think that, as is the usual case, the Linksys CD will have an installer for Windows but not for any linux.
 
There may be a set of installable files on the Linksys site - or you might have to investigate ndiswrap together with the .inf file which Windows uses.
 
I've downloaded the current version of ndiswrapper, but I'm having trouble installing it. I'm no computer expert, so the instructions that I look up are a little complex for me.

---

### Post by jimbosbees on 2012-09-18
how do i find my post of yesterday and combine it with this site"thread??"
to recap; a beginner i need step by step help, lead by my hand, in all actions,functions on this forum.
I have changed att dsl to att uverse, 2-wire gateway router to motorola nvg510
switched xp pro, vista, and win 7 wireless by changing SSID and wireless key to match.  The uverse installer adjusted the security setting in the uverse wireless router to admit the xp pro wireless.
Problem; my ubuntu 12.04 and 10.04 worked wireless on dsl but i can not understand what enter to the settings to connect wireless.
the ubuntu still work,connect to internet, if i attach internet cable from router.
I have no knowledge nor understanding of command line functions.
   Any suggestions and ideas will be appreciated, if they are on my level of understanding.
email correspondence also appreciated for help.

---

### Post by dandnsmith on 2012-09-19
jimbosbees - I think that [this](http://ubuntuforums.org/showthread.php?t=861388) may be the one (got by going to your profile and looking for othr posts - but you should use your own thread, and not interrupt one already in mid-flow!

---

### Post by dandnsmith on 2012-09-19
> **CWied1394 said:**
> I've downloaded the current version of ndiswrapper, but I'm having trouble installing it. I'm no computer expert, so the instructions that I look up are a little complex for me.
If you're on Ubuntu, then you should have used the package manager to do the download and install in one go - then all you have to do is find out where to put the inf file to get it used (I think, after install of the package, you should find a configuration option to set everything up, but it is a while since I tried anything like that)

Does that help, or is there something to add which would help?

---

