---
title: "Mythbuntu reports no UPnP when configuring backend"
date: 2010-05-25
forum: Mythbuntu
---

### Post by petatkinson on 2010-05-25
I started with a fresh install of 10.04 and Myth.Downloaded and installed as instructed as requested.I ran the backend and am being told that the backend cannot ping the server as no UPnP found.It gives me the option to sign on localhost, user name and password.This is a single machine installation frontend and backend.Port 3006 is reported as the default port being used.Card is working perfectly under Kaffeine.Can anyone suggest what I could change or what I  could be doing wrong.

---

### Post by williammanda on 2010-05-25
> **petatkinson said:**
> I started with a fresh install of 10.04 and Myth.

Did you install Ubuntu and then mythbuntu control centre or mythbuntu?

> I ran the backend and am being told that the backend cannot ping the server as no UPnP found.

Is this during when you first start the backend setup?

> It gives me the option to sign on localhost, user name and password.

Is this also when you first start the backend setup?

> Port 3006 is reported as the default port being used.

Where are you finding this information at? Did you create that port number?This isn't a standard number used.

What parts of the mythbuntu control centre have you installed? Please be specific as to the order of what you did.

I would advise you to give more detail, maybe take some snapshots of the points in question.

---

### Post by petatkinson on 2010-05-26
*Did you install Ubuntu and then mythbuntu control centre or mythbuntu?*

Yes


[I]Quote:
I ran the backend and am being told that the backend cannot ping the server as no UPnP found.  

Is this during when you first start the backend setup?[/I]
Yes


[I]Quote:
It gives me the option to sign on localhost, user name and password.  

Is this also when you first start the backend setup?[/I]
Yes


[I]Quote:
Port 3006 is reported as the default port being used.  

Where are you finding this information at? Did you create that port number?This isn't a standard number used.[/I]

No this is being generated for me at page 1 of the configuration during the Myth backend setup

*What parts of the mythbuntu control centre have you installed? Please be specific as to the order of what you did.*

I downloaded Mythbuntu from the Mythbuntu website.I chose the option for installing over 10.04 desktop

*I would advise you to give more detail, maybe take some snapshots of the points in question.*

I remember going through a similar problem while trying to install through the ver.7.xx of Ubuntu.I have never had a working DVB-S card in Ubuntu only an analogue capture card.I think the problem lies between the port and the MySQL database so I need to be able to edit the MySQL database and settings.Maybe you could point me in the right direction

---

### Post by petatkinson on 2010-05-26
Found the file I was looking for mysql.txt.Myth applies its own password, in this case a mixture of letters and numbers so I copied exactly the contents of this file and got passed the database sign on problem.Now all I have to do is to get Myth to work.

---

### Post by Eruaran on 2010-08-19
I'm trying to set up an Ubuntu based media center for someone and I must say this is just ridiculous. It is WAY to technical and hard, not just for some people, for MOST people. And here's the thing: It's ordinary folk who want things like this, but there's no way I'm going to recommend a Linux based media center when setting it up is just so ridiculously hard.

---

### Post by ian dobson on 2010-08-19
> **Eruaran said:**
> I'm trying to set up an Ubuntu based media center for someone and I must say this is just ridiculous. It is WAY to technical and hard, not just for some people, for MOST people. And here's the thing: It's ordinary folk who want things like this, but there's no way I'm going to recommend a Linux based media center when setting it up is just so ridiculously hard.

Hm, thats interesting (nothing to do with this thread but anyway). My assistant at work has built a windows based PVR using Media Portal and when I see the problems he had, it's not much better/worse than Linux/MythTV.

Regards
Ian Dobson

---

### Post by LowSky on 2010-08-19
> **ian dobson said:**
> Hm, thats interesting (nothing to do with this thread but anyway). My assistant at work has built a windows based PVR using Media Portal and when I see the problems he had, it's not much better/worse than Linux/MythTV.

Regards
Ian Dobson

Windows Media Center on Windows 7 is much easier to configure than MythTV. I will vouch for that. MythTV just some advantages like no DRM, no tuner restrictions, much more add-ons, oh and its free.


Back to the problem at hand

If you can reinstall mythtv from synaptic. make sure you create a user name and password you can remember for MySQL, otherwise you can get stuck on parts like this.

For any machine I use as a backend I tend to lock the IP adress form the router, that way it cant accentally change. And on the backend under general setitngs I type ***localhost*** for the IP address. this way the machine knows to use

If you can check mythbuntu control center and make sure the machine is registered as the primary backend, sometimes t gets installed as a secondary for some reason.

---

