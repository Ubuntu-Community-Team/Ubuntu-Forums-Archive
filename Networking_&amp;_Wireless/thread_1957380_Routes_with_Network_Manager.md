---
title: "Routes with Network Manager"
date: 2012-04-12
forum: Networking &amp; Wireless
---

### Post by bercy on 2012-04-12
Hi,

I have two nics, eth0, eth1.

I also have two internet connections, one for each nic.

I want the default internet connection to be the one connected to eth0, and eventually I'll have a bridged VM with its own connection through eth1.

When I boot, the default route is currently eth1.

I know I can change it by using the "route" command to delete the default route and then add a new one.

That works.

The problem is that when I reboot, the old default route comes back.

How do I make my route changes permanent ?

I've read in many places that I need to add route commands in /etc/network/interfaces, but I've also read that if you're using Network Manager it wouldn't necessarily work ?

So the question is, how to make this route change permanent knowing that I use Network Manager ?

Tks.

---

### Post by Ms. Daisy on 2012-04-13
I couldn't find where network manager stores its settings so I still don't know how to do this through terminal.

But you can make the permanent change through the GUI.  Click on the network manager applet, choose edit connections.  Pick the connection you want permanent & click on 'edit'. (on the window that opens you'll find whether it's eth0 or eth1). There's a box at the top of the window that says "connect automatically," choose that one.

---

### Post by Damascushead on 2012-04-13
I second ms. Daisy.
 
But if that doesn't work you could always edit bashrc to make the change for you at login :p

---

