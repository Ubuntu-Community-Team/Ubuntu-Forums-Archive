---
title: "Ubuntu and Remote Login"
date: 2009-01-15
forum: Networking &amp; Wireless
---

### Post by UNME on 2009-01-15
Hi,

I am always running between my machine (base location) and my clients machine (client location).
when I am at clients location, I need to remote login to my machine in base location.

I am using VNC for this but have following problems:

1 VNC asks at base location "Allow or refuse connection" but now I am at clients  location so I have to run to my base machine to allow me to remotely connect

2 When I have connected to my machine from clients location, I want my machine at base location get locked (this is what I saw happening with MSTSC on windows).

3 Sometimes I am not able to connect to my base machine, these random failures makes lot of trouble for me.

Can anyone help me here. Some tweak or other application that can help.

SSH can be used but I need graphical login 

Thank You :KS

---

### Post by movingover on 2009-01-15
In Ubuntu System Preferences, you can uncheck the box that asks for user permission when you VNC in. This will allow anyone who knows your VNC password to remote in without running back to the machine in question.

If you need this more secure (recommended), you can block the VNC port with any firewall like Firestarter, and use SSH to tunnel in. From another ubuntu machine this is pretty easy:

[http://ubuntu-tutorials.com/2007/06/12/vnc-over-ssh-securing-the-remote-desktop/](http://ubuntu-tutorials.com/2007/06/12/vnc-over-ssh-securing-the-remote-desktop/)

And there are plenty of other options, for example I VNC over SSH from windows using a program called PuTTY, you can google around to see more info.

Hope this helps.

---

