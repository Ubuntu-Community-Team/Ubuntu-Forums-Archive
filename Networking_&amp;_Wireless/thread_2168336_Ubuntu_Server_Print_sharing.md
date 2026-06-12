---
title: "Ubuntu Server Print sharing"
date: 2013-08-17
forum: Networking &amp; Wireless
---

### Post by richaustin on 2013-08-17
Hi All

I've installed Ubuntu Server on a spare box, which I intend to use headless (I do have a monitor attached at the moment and a connection through VNC). I've managed to get a connection to a XFCE desktop on the Server via VNC. That works fine. What I can't get to work is print sharing.

1. I included the Print Server whilst installing the system. 
2. On the Server, via VNC, I can see the Printer (its a HP F2180 Deskjet) in XFCE, but the Settings dialogue doesn't open.
3. On my Ubuntu desktop I can see the Server if I click on Browse Network in Nautilus. I can't connect though because the dialogue mentions Workgroup etc. 

I do wonder if it might be an idea to re-enable the GUI on the Server - I disabled GDM because I want the box to be headless - and setup through Gnome or XFCE? I'd prefer to know how to do it all via CLI though tbh.

Basically I just need a rough guide to how to go about sharing the printer (files too if possible) from the Ubuntu Server. Prefferably from the CLI since the dialogue isn't working in XFCE (an answer to that issue would be great!). I don't really want to use Samba, although I did install it since I might need it later.

I know my way around in Linux, I just haven't setup a server before. Any help, pointers, good links that don't blind with science etc. would be more than welcome!

Thanks
Richard

---

### Post by Azdour on 2013-08-17
I'm guessing that including the Print Server means it installed CUPs.

Have you tried to access your print server via your browser: http://<server_ip>:631 ?

---

### Post by tgalati4 on 2013-08-17
When you install a desktop environment, you get all kinds of goodies including automatic publication of printers using Avahi/Bonjour which probably didn't get loaded in a headless server installation.  As a work-around, log into your server from a webpage:  [http://YourserverIP:631](http://YourserverIP:631) as Azdour suggested.  Click on the printer and make sure the sharing box is checked or click "Publish Printer" depending on what menu you are on.

---

### Post by richaustin on 2013-08-17
Thanks for the help. I think you're both totally right about the fix for this issue. I tried:

[http://192.168.1.6:631/](http://192.168.1.6:631/)

Firefox just returns "Unable to connect". I'll look into that and figure it all out now I know what to look for. Happily I discovered my webserver works perfectly while I was trying the above.

Thanks
Richard

---

### Post by richaustin on 2013-08-17
Actually, thanks to you guys, I found the answer in a matter of minutes at this URL:

[http://awaos.awanowa.jp/en/2010/09/cups_on_ubuntu_for_ubuntu_and_win_client/](http://awaos.awanowa.jp/en/2010/09/cups_on_ubuntu_for_ubuntu_and_win_client/)

---

### Post by tgalati4 on 2013-08-18
You are now an expert.  Thanks for sharing.  Minimal, headless, servers means that you have to roll up your sleeves and do the configuration yourself.  I often recommend installing the desktop for server use and just don't boot into the desktop for production use.  You can still remotely display a graphical desktop and you have all of the configuration frameworks loaded and somewhat functional.

---

