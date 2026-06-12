---
title: "setting up WPA with orinoco gold card"
date: 2006-02-11
forum: Networking &amp; Wireless
---

### Post by skitxoz on 2006-02-11
Hello,

I have an orinoco (avaya) gold 802.11b card and am running ubuntu on a powerbook g4.

I am following the tutorial from this page to setup WPA:

[http://www.ee.surrey.ac.uk/Personal/G.Wilford/WiFi.html](http://www.ee.surrey.ac.uk/Personal/G.Wilford/WiFi.html)

I've been successful for most of the way but am at a stopping point when I try and edit the /etc/sysconfig/network-scripts/ifcfg-eth1 file

I don't have a sysconfig folder in /etc

How could this be?  What packages can I run to setup this folder structure.

Where are my eth0 and eth1 settings being housed now?

thank you,
Dan

---

### Post by mpvano on 2006-02-11
That's where they live in Redhat (and some redhat derived) Installations. I'd be careful if I were you, there are other serious differences between Redhat's network scripting and Ubuntu's.

I don't believe Ubuntu uses any such scripts.

Most of the corresponding functionality in ubuntu networking scripts are in /etc/networks, but as I say, be careful there's really no resemblance at all in the way they work.

The majority of the configuration settings for debian/ubuntu networking are in a file called /etc/network/interfaces, and there are directories in /etc/networks where scripts can be placed for automatic execution during if-up and if-down.

These perform a similar function to the redhat scheme, but theirs is much more complex with support for multiple profiles and network administration applet that they wrote and maintain...

Try man ifup, man interfaces, and man ifconfig to learn how the debian scheme works. There's also some documentation in the /usr/share/doc/ directories that correspond to those package names....

hope this helps you figure out the corresponding differences...

Mario

---

### Post by skitxoz on 2006-02-12
Great, thanks Mario.  It looks like the tutorial i was following was indeed for RH. 

I'll do some more researching into the RH/Debian differences as I am a recent convert from RH to ubuntu.

---

