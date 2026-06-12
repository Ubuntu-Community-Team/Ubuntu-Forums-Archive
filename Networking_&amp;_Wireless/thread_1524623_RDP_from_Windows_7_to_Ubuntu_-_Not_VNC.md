---
title: "RDP from Windows 7 to Ubuntu - Not VNC"
date: 2010-07-05
forum: Networking &amp; Wireless
---

### Post by AP0ll0UK on 2010-07-05
Hi

I'm wondering if anyone can provide me with some recommendations please.

I have a Ubuntu 10.4 Media Server running XBMC, this is connected to my Tv and I'd like to leave it this way but run tasks in the background through the GUI.

I have a Windows 7 laptop which I would like to RDP [or something like] from into my Ubuntu server, without interferring with the interactive session on my Ubuntu server which will be displaying XBMC. I can't use VNC as this would interfere with XBMC.

Does anyone have any suggestions to any apps I can use to do this please? I heard good things about FreeNX but couldn't get it to work for someone.

---

### Post by carsonrose on 2010-07-05
> **AP0ll0UK said:**
> Hi

I'm wondering if anyone can provide me with some recommendations please.

I have a Ubuntu 10.4 Media Server running XBMC, this is connected to my Tv and I'd like to leave it this way but run tasks in the background through the GUI.

I have a Windows 7 laptop which I would like to RDP [or something like] from into my Ubuntu server, without interferring with the interactive session on my Ubuntu server which will be displaying XBMC. I can't use VNC as this would interfere with XBMC.

Does anyone have any suggestions to any apps I can use to do this please? I heard good things about FreeNX but couldn't get it to work for someone.

Have you tried putty? I use it on Win 7 all the time...

---

### Post by AP0ll0UK on 2010-07-05
Hi 

Thanks for your reply.

I use Putty for SSH but I still need Gnome desktop.

Thanks again.

---

### Post by carsonrose on 2010-07-05
Have you tried "ssh <username>@<ip address> -X"   This will start the X server.... should be able to start a remote gnome session from there..... You can always google "VNC Win 7 to Ubuntu"

[http://www.techotopia.com/index.php/Remote_Access_to_the_Ubuntu_Linux_Desktop](http://www.techotopia.com/index.php/Remote_Access_to_the_Ubuntu_Linux_Desktop)


Cheers!

---

### Post by carsonrose on 2010-07-05
> **AP0ll0UK said:**
> Hi 

Thanks for your reply.

I use Putty for SSH but I still need Gnome desktop.

Thanks again.
You could also try rdesktop

---

