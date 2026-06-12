---
title: "tightvnc problems"
date: 2009-06-09
forum: Networking &amp; Wireless
---

### Post by rcoe74 on 2009-06-09
Hi all, I'm sure this is the situation where somewhere out there is the forum post or tutorial which will tell me how to do what I'm trying to do - but each one seems to assume a little bit of knowledge that I don't have.... all help very gratefully received.

I have a desktop box which I want to use as a media server. I want to be able to have it in a cupboard without monitor or keyboard etc. - so I'm trying to set it up so I can use VNC to control it.

The desktop is running Jaunty. I've installed ssh & tightvncserver on the desktop. I didn't uninstall any other VNC or remote desktop applications which I've read in one or two tutorials so if I need to do that let me know. The desktop connects via a network cable to a wireless router.

The client is a laptop running Intrepid. I installed xtightvncviewer on the laptop. I forwarded port 22 on the router to the desktop and I can successfully SSH from within my LAN to the desktop and I can SSH from work using Putty in Windows. 

Now I want to run a VNC session with desktop as server and laptop as client. As I understand it the secure way to do this is to do it via an SSH tunnel. Alternatively I could do it directly by forwarding port 5900 on my router to the desktop. But I'm confused about the different switches after the SSH command and how to set up the tunnel correctly. I'm also confused about whether I need to forward port 5900 when I'm trying to connect from within the LAN. It's also not clear to me whether I have to run tightvncserver on the desktop directly prior to setting up the SSH tunnel (which seems to defeat the object) or what order to do "run tightvncserver" "setup SSH tunnel" "run xtightvncviewer".

If a tutorial says "localhost" in a line of code do I type local host or is that 127.0.0.1?

Sorry I know these are basic questions. Need a little bit of handholding!

Thanks for all tips or of course directions to a good tutorial or forum post that my searching hasn't found.

Richard

---

