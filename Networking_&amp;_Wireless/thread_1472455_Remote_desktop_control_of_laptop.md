---
title: "Remote desktop control of laptop"
date: 2010-05-04
forum: Networking &amp; Wireless
---

### Post by madwoollything on 2010-05-04
Just installed a clean copy of Lucid on a laptop. The only changes that have been made are to enter the wireless WEP code and enable remote desktop connections. Everything appears to be running as you would expect.

Here is the problem:

With a LAN cable connected to the laptop, I can connect remotely to this laptop and control the 'desktop' with no problems (using Ubuntu standard tools from another PC). If I unplug the LAN cable from the laptop and only use the configured wireless connection, it is no longer possible to remotely control the laptop. It is not possible to get a connection. This whole process is very 'repeatable'.

What is odd is that the laptop used to have 8.04 installed and there was no difficulty in connecting remotely and controlling the laptop when it was attached to the network with either LAN cable or wireless.

(Since discovering this I've tried out the same procedure on a laptop running 9.04 to discover the same issues.)

What else do I need to configure to allow 'remote control' of the 10.04 laptop when it only has a wireless connection to my network?

OR is this a bug that needs to be reported in Launchpad (some pointers on how to do this would be good)

Looks like this is already in launchpad [https://bugs.launchpad.net/ubuntu/+source/rdesktop/+bug/360038](https://bugs.launchpad.net/ubuntu/+source/rdesktop/+bug/360038)

---

