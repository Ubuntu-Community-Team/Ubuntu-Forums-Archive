---
title: "Trying to view the remote desktop"
date: 2012-07-11
forum: Networking &amp; Wireless
---

### Post by valvegrid on 2012-07-11
I feel a bit stupid asking this, but here goes. I have set up a VPN connection to my companies server and it says it connects, then what? How do I actually view the remote desktop? I used to view it a few years ago but I can't for the life of me remember how, it is something really easy I know, so I hope someone take pity on me, thanks  ):P

---

### Post by Kirk Schnable on 2012-07-12
You'll need software installed to view the remote desktop.  There are a few types of software out there that do this that come to mind:

VNC Servers
RDP Servers
NX Servers
TeamViewer

VNC is probably what you want.  You should be able to find one quickly in Apt.

RDP can be done on Ubuntu with x11rdp.  However it doesn't access the remote screen, it opens another session behind-the-scenes and gives you a remote desktop.

NX can be done with NoMachine's NX or with FreeNX easily.  It has the same basic functionality of RDP, providing a virtual console rather than direct access to what's on the screen.

TeamViewer can do what VNC can do, provide access to exactly what's on the screen, but TeamViewer is intended for remote support\assistance more than permanent remote access.


Do some Googling, this should get you started!

Kirk

---

### Post by valvegrid on 2012-07-12
Thanks Kirk, I think our company server is playing silly billy's at the moment, I'll try those when its settled down again.

---

### Post by valvegrid on 2012-07-14
KRDC works.

---

### Post by valvegrid on 2012-07-24
I know I've marked this as resolved, but it wasn't really, but after talking to our companies IT we have managed to get it working. The IT guy doesn't know much about Linux, but between us we have worked it out.

It is as simple as setting up the VPN to connect to the remote server then to check to make sure it's working go to one of the "what is my IP address" web sites and it should return the IP address of the company server.

To actually see the shared files on the server open Nautilus file manager and go to File>Connect to server and for the type of server pick Windows share, then you need to know what the local address is of the server which IT should be able to give you it will be something like 192.168.x.x the two x's are the last numbers that are given by IT. Type those into the Server field at the top and click connect. In my case it connected and got all the details from the server like the domain name automatically. The shard drive appears as an icon on the panel on the left.

It was so simple I don't know what all the fuss was about.

---

