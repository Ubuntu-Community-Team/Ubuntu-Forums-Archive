---
title: "Bad VNC Connection"
date: 2008-04-22
forum: Mythbuntu
---

### Post by MARKYB0Y on 2008-04-22
Hi All,

I have enabled VNC on my mythbuntu box, however when I connect to it the image on the remote pc is unreadable, a scattered image.

any ideas what might be causing it?

I have tried TightVNC, RealVNC and UltraVNC viewers all with the same result so I assume it is an issue with the mythbuntu server?

[[IMG]http://img206.imageshack.us/img206/8268/vncmythbuntudy8.th.png[/IMG]](http://img206.imageshack.us/my.php?image=vncmythbuntudy8.png)

---

### Post by The Odometer on 2008-04-22
I had a similar problem and I think I fixed it by making the screen resolution on both the Remote PC and the server the same. (I think I had my server set at 640 x 480 so I could read it on the TV, and my remote PC is at 1024 x 768.) Once I set the server to 1024 x 768, it cleared up.

---

### Post by MARKYB0Y on 2008-04-23
Odometer, you could be on to something here

I have tried changing the resolution on the server bt it made no difference on the remote pc

using UltraVNC I am able to see the connection details and it says the Desktop Geometry is 1360*768, now I have tried changing my remote pc's resolution to 1280x1024 to match the MythBuntu server but still no good, even tried 800x600

any ideas how to change the NVC settings to make it use a particular resolution?

thanks

---

### Post by The Odometer on 2008-04-24
In my case, the resolutions of my desktop (myth server) and laptop computers match exactly.

Another thing I'm using is x11vnc for my server, not the default vncserver that came with mythbuntu. I could never get vncserver to work for me...so I just installed x11vnc--and set it to autostart. I also uninstalled vncserver.(Plus, I think I read today that vncserver is not working with the new upgrade.)

I've been able to view it using both realvnc and tightvnc applications. 

I hope this helps...

---

### Post by straxus on 2008-04-25
Check your xorg.conf for a line that begins with the word "virtual".  It's usually under the 'screen' or 'display' sections if it's there at all.  if it exists, comment it out.  It worked for me.

---

### Post by MARKYB0Y on 2008-04-25
Hi Straxus, can you give me the full path as to where this file exists, as I said I have zero knowledge of Ubuntu so its all new to me

Odometer, I may have to resort to this is Straxus' reply doesnt work, dont suppose you could russle up an idiots guide as to how to install in on MythBuntu?

thanks

---

### Post by The Odometer on 2008-04-25
Here's a link to what I did:

[http://www.ubuntu-unleashed.com/2007/10/setup-vnc-server-for-ubuntu-gutsy.html](http://www.ubuntu-unleashed.com/2007/10/setup-vnc-server-for-ubuntu-gutsy.html)

This was after uninstalling vncserver. Vnc-Java allows you to actually view your computer using an internet browser, rather than a VNC Client. I still use Tight VNC to view mine--but you don't have to. It just makes it easier to use all along.

Hope this helps--if not--no worries.

---

