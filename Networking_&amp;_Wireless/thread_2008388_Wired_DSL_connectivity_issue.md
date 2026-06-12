---
title: "Wired DSL connectivity issue"
date: 2012-06-22
forum: Networking &amp; Wireless
---

### Post by TheCadaver on 2012-06-22
Just a bit ago, my home was struck by lightning and seemed to have friend my router. We had a backup router and plugged that in. All the wireless connections around the house are working, except for the DSL on my main desktop. After clicking on "Network Connections", I've got no idea what to do. No matter what I type into any of the boxes, the "apply" option gets greyed out. Could the lighting strike have broken my desktop's wired port, too, or am I just doing something wrong? Basically, I don't know how to connect to my router in a wired connection, shouldn't it be automatic?

---

### Post by kurt18947 on 2012-06-22
If you open 'network connections', what do you see?  When I click on the 'network' icon in the upper right corner (running gnome-shell) I see one box labeled 'wireless'.  It shows on.  This icon does not show network adapters that are not active.  On other distros I've had indicators that show up whether they're active or not.  

When I click 'network connections' I see 5 tabs. The first two are wired and wireless.  My wired tab is blank - no ethernet connection, using wifi - the wireless tab shows a connection.  Your wired tab should show something.  If not,  it's probably powered off for whatever reason.

If you had a lightning strike it's hard telling what may have gotten fried.  If it got the router and there's an ethernet cable running from the router to the PC's ethernet adapter I wonder if your ethernet adapter could have gotten damaged.

---

### Post by TheCadaver on 2012-06-22
When clicking "Network Connections", there's Wired, Wireless, Mobile Broadband, VPN and DSL. Here's a screenshot. [IMG]http://i.imgur.com/4L2op.png[/IMG] I tried one time already, hence the "Wired Connection 1, last used - never", but it doesn't seemed to work. I entered the mac adress, full with the colons and whatnot. Not exactly sure what to do from here.

---

### Post by steeldriver on 2012-06-22
If you are connecting using the default wired connection to a router with DHCP then you shouldn't need to enter anything, especially not the MAC (unless your router has MAC filtering enabled and you need to spoof it for some reason) - if it doesn't work out of the box then a few of the possibilities are:

1. the substitute router is not configured as a DHCP server

2. you previously edited your 'Wired connection 1' to some non-standard configuration (e.g. static IP rather than DHCP) that conflicts with the setup of the substitute router (e.g. a conflicting IP or different subnet)

3. something unrelated to the new router e.g. a driver update that has broken your interface

Physical damage is possible but unlikely I would think

You can run ifconfig and nm-tool in a terminal to see what config you currently have

---

### Post by TheCadaver on 2012-06-22
Something I just noticed. My desktop has a see-through side. Before, when my internet cable was plugged in, there was a small green LED on the motherboard, next to the port. The LED isn't on in this case, as if it doesn't recognize that it's plugged in, or perhaps just broken, I'm not sure.

Anyhow, here's a screenshot of my terminal after running those commands. [IMG]http://i.imgur.com/AuIlB.png[/IMG] how would I configure this router into a DHCP router if it isn't? And, the "Wired Connection 1", as far as I know, has been set to DHCP settings where available as an option. I haven't done any driver updates, so I doubt drivers have any part in this.

---

