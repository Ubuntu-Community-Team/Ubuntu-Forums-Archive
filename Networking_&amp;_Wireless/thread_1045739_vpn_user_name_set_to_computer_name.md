---
title: "vpn user name set to computer name"
date: 2009-01-20
forum: Networking &amp; Wireless
---

### Post by oatesj77 on 2009-01-20
hi there, i have a vpn problem that i'm not sure about.

working with ubuntu 8.1, fresh install, added network manager and network-manager-pptp

i'm trying to connect to a windows vpn at work using network-manager and create vpn. set up my vpn connection through desktop GUI (create new connection > vpe > etc), with user name, password and gateway address.

the problem i'm having is the user name that i set in my connection is not being used, rather when i try and connect, the vpn uses my computer name. i know i'm hitting the network, our IT guys said they saw me trying to connect, but the user name was coming in as xxxx-laptop, which is my computer name.

so i'm guessing there is some sort of setting that is trying to use my computer's credentials rather than the ones i'm setting in my connection.

any help would be great, this is the ONLY thing standing between me continuing to use Linux or having to go back to XP :(

thanks

*edit* 
solved this by creating new vpn connection and initiating via *sudo pon myNewConnection nodetach*
am now vpn'd in, but now have a new set of problems mounting network drives.

---

