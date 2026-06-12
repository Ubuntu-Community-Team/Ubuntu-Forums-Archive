---
title: "can scan for connections and connects but no internet use"
date: 2012-03-16
forum: Networking &amp; Wireless
---

### Post by AlFro on 2012-03-16
Hi... just installe ubuntu yesterday-Awesome! I only have one issue yet to resolve. I have verivon fios and there wireless connection setup. ubuntu says it is connected and active. I can scan and return available connections using wifi radar, but for some reaon it comes back with cannot connect to server whenever im using firefox. Also, it doesnt display any bars. 
 
It works fine when using an ethernet cable.
 
settings
 
Ad-hoc
mtu automatic
automatic DHCP
wpa & wpa2 security
 
Any ideas folks?

---

### Post by Helicopter MTP on 2012-03-17
AlFro,

On the top right part of your screen try to right-click on your wifi then left-click on the 3 or 4 items that pertain to the network, i.e. Connect to network, etc.  Sometimes when you first install this step has to be done to make the wifi work.

I hope that works for you.

---

### Post by AlFro on 2012-03-17
Thanks fro the quick reply. Unfortunately I enabled all thos previously. No luck. Got any more suggestions :)
Thanks
ALFro

---

### Post by Rick.B9 on 2012-03-17
From my experience, it's usually been a permissions issue.  Right-click on the applet in the system tray at lower right of screen.  Click "Edit Connections", then click "Wireless".  Click to highlight the relevant connection and click "Edit".  In the lower left of the window make sure "available to all users" is checked.   I'm not sure if you'll have to log out for this to take effect, but you may have to.

Another thing, you may need to go into the "Users and Groups" program to add yourself to the "Connect to wireless and ethernet networks".  That's Users and Groups>your_username>Advanced Settings, then find the checkbox for connecting to networks.  You'll have to type in your password at some point.

You also should change from Ad hoc to Infrastructure.

---

### Post by AlFro on 2012-03-17
the odd thing is that it sais connection establish

---

### Post by Rick.B9 on 2012-03-17
Well, that's why I think it might be permissions based.  Ethernet always works for me, but I've had to enable the "available for all users" checkbox before.  It's seeing and establishing the connection, but not allowing you to use it.  Go see if the checkbox is ticked.

---

### Post by AlFro on 2012-03-17
[FONT=Times New Roman][SIZE=3]All available users is checked, I gave myself access to everything and still don&#8217;t have access to the internet. A challenge, this one is ;) [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Thanks for the ideas. Please let me know if you can think of anything else.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]AlFro[/SIZE][/FONT]

---

