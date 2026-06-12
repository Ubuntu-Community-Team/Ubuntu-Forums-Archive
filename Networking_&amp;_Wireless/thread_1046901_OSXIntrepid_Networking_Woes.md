---
title: "OSX/Intrepid Networking Woes"
date: 2009-01-21
forum: Networking &amp; Wireless
---

### Post by codfish45 on 2009-01-21
I am trying to do file sharing between a Mac OSX Tiger and Intrepid over a wireless network.  I have tried various methods: NFS netatalk/appletalk, and fugu, but none have worked so far.   I cannot get Ubuntu to see the mac in the Network folder, and vice versa.  I was able to work this out with Windows XP without too much difficulty, and this is one of my last "everyday" migration issues.

I am using a Netgear wireless G router with WPA enabled.

One ray of hope: I can successfully ping the Ubuntu machine from the Mac, even if I cannot do it the other way.

Any thoughts??

---

### Post by codfish45 on 2009-01-22
Well, things have improved slightly:  I found an alternate IP address for the Mac that was PINGable, and setting permissions for Avahi for each user lets my machine show up on the network for the Mac, but I still cannot access one computer from the other, even with sharing turned on, and I cannot for the life of me get Ubuntu to see the mac.
Please help!

---

### Post by Kobalt on 2009-01-22
Enabling the Samba (windows file sharing, from the pref. pane of OS X) on both machine should give you the ability to use shared folders... I do it with my two Macs and my eeePC. Did you try this?

---

### Post by codfish45 on 2009-01-22
It's enabled on both machines, but it doesn't work.

---

