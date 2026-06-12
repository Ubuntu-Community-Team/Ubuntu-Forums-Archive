---
title: "Problem with remote desktop to XP machine"
date: 2010-11-20
forum: Networking &amp; Wireless
---

### Post by Newbie2910 on 2010-11-20
I have my main box, Ubuntu 10.04lts, and I am trying to use remote desktop viewer to see the desktop on a Windows XP machine.  The machines are side by side  The Ubuntu box is hardwired to my network router, and the XP machine is  connected via wireless.  Both get to the internet fine, and I can ping the Ubuntu box from the XP box.  But, I cannot ping the XP box from the Ubuntu box, and Remote Desktop Viewer won't establish a connection to the VNC server I have running on the XP box.

Since the Ubuntu box can ping the router, what might my issue be?

---

### Post by spiky001 on 2010-11-20
I take it you are pingin the correct ip on xp box

---

### Post by Newbie2910 on 2010-11-20
Yes, reading IP using IPCONFIG on the XP machine then attempting to ping it from the Ubuntu box.  No luck.

Works the other way though...

---

### Post by spiky001 on 2010-11-20
All i can think of is the router blocking it with a firewall, Maybe some1 else can shed some light

---

### Post by Newbie2910 on 2010-11-20
I am able to go into the router setup, and it has its own diagnostics.  The router too is unable to ping the XP machine.

I have turned off the Windows Firewall no difference.

---

### Post by Newbie2910 on 2010-11-20
Ah ha! Quick restart of the router did the trick.  Why, I don't know.

thx for the help.

---

### Post by spiky001 on 2010-11-20
Good, mark thread as solved all done:popcorn:

---

