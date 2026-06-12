---
title: "network manager OR router suddenly stopped working"
date: 2010-11-25
forum: Networking &amp; Wireless
---

### Post by fazza on 2010-11-25
Right so yesterday my internet worked fine.

Today - no connection at all. The light for my cable on the router doesn't even show up.
I originally had indicator-network installed, so when the internet first stopped working, I tried a few other options such as tethering to my phone via usb and bluetooth (which I have successfully used in the past). However, these didn't work, and I figured that as connman is still in beta, maybe that was why.
So I reinstalled network-manager and network-manager-gnome via a usb stick, uninstalled indicator-network, and rebooted the computer.

Still no internet.

When I click on the applet, it says "No network devices are available". This is odd, as I definitely have a network device... it is part of the motherboard.

So I thought I'd do the SMARTlan test or whatever it's called. It's part of my BIOS, so I ran that and it returned results that I (kinda) expected: when the cable wasn't plugged in, it returned one set of results. When it was only plugged into my computer (and not the router), it returned another set of results. And when it was plugged into both my computer and the router, it returned a third set of results. So that leads me to believe the cable itself is fine.

And when I move the cable to a different port on the router, nothing changes. The corresponding light still doesn't come on.

So the only problem I can find is in the network-manager, telling me there are no network devices. The BIOS can see the ethernet port and the cable. And the router is functioning perfectly for my parents' computer and my ps3.

And I have checked the cable to my computer for physical damage - it follows the same path as the one to my ps3, and on top of that, nothing physical can possibly have happened to it in the last day.

Oh and ftr, this happened once before, except I don't think the network devices were lost. And though I tried, I didn't do anything to fix it - it just suddenly worked again.
This doesn't look as hopeful.

So any help would be appreciated thanks :)

---

### Post by uncaspi on 2010-11-25
Try to ping your network card by bringing it up and assign static ip.
First issue sudo /sbin/ifconfig
Lets say you see eth0 then bring it up manually
sudo /sbin/ifconfig eth0 192.168.1.111 up
ping -c4 192.168.1.111
If not exist or if the card doesn't show up pleased post the content of
sudo nano /etc/udev/rules.d/70-persistent-net.rules

---

### Post by fazza on 2010-11-26
Okay thank you.
Well all of those commands work. In fact, the output of /sbin/ifconfig is exactly the same, before and after bringing the interface up. I think it was already saying the interface was up: "UP BROADCAST RUNNING MULTICAST".

But suddenly the internet is connected again :)

However... the network manager is still telling me there aren't any network devices available. I can edit connections, and even add connections, but I can't start them because of this.

---

