---
title: "make a wired internet conection"
date: 2009-01-12
forum: Networking &amp; Wireless
---

### Post by Kerato on 2009-01-12
I want to make a internet connection with ubuntu.
but for security i have to set the following things:
ip: 10.0.0.2
subnet mask: 255.255.255.0
gateway: 10.0.0.1
DHCP: 10.0.0.1
DNS: 10.0.0.1
if I don't the computer wont establish a connection.
I prefer not to work with the terminal.
can somebody please help me? 
(some screen-shots for showing me were I can put those codes would be nice)

---

### Post by theDaveTheRave on 2009-01-12
Kerato,

you need to get a hold of network manager,

it is normally in the system | admin section of the menu, then look for network manager.

It is a gui front end to setting the /etc/network/interfaces file.

If you don't have network manager (unlikely as it is part of a standard installation), you can find it in synaptic, just search for network manager and it should be in the list.

sorry I can't give screen shots, but my current terminal doesn't have network manager, and I don't have access to one that does due to a power board failure on my pc.

Again sorry if I'm not being very helpfull, 

there is [this page in the documentation]("https://help.ubuntu.com/8.04/internet/C/internet-basic-procedure.html") but again no screen shots.

Hopefully however it will be enough to get you connected via a static IP

There is [this page]("http://ubuntuforums.org/showthread.php?t=954368") of mine, that explains how to do static ip using the command line, and how to get the required information for puting into network manager.

I hope all this helps, I'll check back tomorrow to see if you are still having issues, right now I need to feed the body so as i can continue to feed the brain with its required fix of internet forum postings!

David

---

### Post by Kerato on 2009-01-14
i tried but i just don't get it.

one of my friens said that i have to use the terminal 'cause that's the only way it will work.
i just want to surf the net. :cry: please help.

---

### Post by superprash2003 on 2009-01-14
hope this helps [http://www.prash-babu.com/2009/01/how-to-setup-static-ip-in-ubuntu.html](http://www.prash-babu.com/2009/01/how-to-setup-static-ip-in-ubuntu.html)

---

### Post by Kerato on 2009-01-20
it helps but every time i fill in the netmask (255.255.255.0)(dunno if it is the same as sub netmask)and press ok the netmask turns to 24.
how i filled it in:
[IMG]http://i253.photobucket.com/albums/hh64/kynnin/Screenshot-EditingWiredconnection1.png[/IMG]

how it ends up:
[IMG]http://i253.photobucket.com/albums/hh64/kynnin/Screenshot-EditingWiredconnection2.png[/IMG]

---

### Post by Iowan on 2009-01-20
/24 is just CIDR (Classless Inter-Domain Routing) notation for 255.255.255.0 - both mean the first 24 bits are the network, the last eight are for the local machines.

---

### Post by Kerato on 2009-01-21
i still don't have an internet connection.
what can be wrong?

---

### Post by ajcham on 2009-01-21
Is your router set up properly? If your router has a browser-based configuration dialog you should be able to access it by navigating to **[http://10.0.0.1](http://10.0.0.1)** in a browser.

---

### Post by Kerato on 2009-01-21
i think it is 'cause when i start up on windows it works just fine.

---

### Post by ajcham on 2009-01-21
Do you currently have any other devices connected to the router, or is it just the one computer?  I'm wondering if the 10.0.0.2 IP address may have already been assigned.

Even if it's just one computer, that would mean you are dual booting, so Windows most likely connects with a different hostname than Ubuntu. Depending on how your router is set up, 10.0.0.2 may be reserved for the hostname on the Windows installation.

Try a different IP address - just replace the 2 with anything from 3 to 254.

---

### Post by Kerato on 2009-01-22
it helped thanks all!!!

---

