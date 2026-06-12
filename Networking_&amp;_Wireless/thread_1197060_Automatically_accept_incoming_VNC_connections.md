---
title: "Automatically accept incoming VNC connections?"
date: 2009-06-25
forum: Networking &amp; Wireless
---

### Post by m.ike on 2009-06-25
Is there a way to make Ubuntu automatically accept incoming VNC connections so I'll be able to accept my computer from anywhere with an active Internet connection without having to accept each and every time? I checked the 'Configure network automatically to accept connections,' althought it still doesn't seem to be working. The UPnP function on my router is enabled so as of right now I'm completly clueless on what the problem might be.

---

### Post by cph05a on 2009-06-25
Have you tested this by accepting the connection?

Some VNC Viewer clients require you to specify the screen number, others assume its 0. Try ether adding or removing :0 to your address when you connect.

---

### Post by m.ike on 2009-06-25
I just tried that and it didn't work, I still have to walk in here in order to accept connections.

Edit: I'm using RealVNC to connect from a windows box to my ubuntu box if that means anything.

---

### Post by cph05a on 2009-06-26
If it works by accepting connections, then everything should be okay as far as your router is concerned. It also means you're doing everything correctly from RealVNC.

From vino, make sure "allow others to view your desktop" is checked, "allow others to control your desktop" is checked, and "Ask for confirmation" is unchecked. 

[IMG]http://www.bani.com.br/wp-content/uploads/2008/10/vino01.png[/IMG]

You can get to this dialog box by going to System>Preferences>Remote Desktop or by running "vino" from the terminal.

---

