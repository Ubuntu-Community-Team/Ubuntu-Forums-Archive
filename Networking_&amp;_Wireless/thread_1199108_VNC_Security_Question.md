---
title: "VNC Security Question"
date: 2009-06-28
forum: Networking &amp; Wireless
---

### Post by climhazzard on 2009-06-28
Hi all,

I am looking into building an inexpensive PC for an HTPC of sorts, and of course throwing Ubuntu on it.  I'm brainstorming some ways in which to control the PC once it is hooked up to the TV, and I thought it might be interesting to try using VNC on my iPhone for a remote.  

The issue I'm running into is that I cannot VNC over SSH via the iPhone, so I am concerned about leaving a security hole open.  I only wish to control the PC over my LAN, and will not be enabling port forwarding on my router.  Will this leave any (more than normal that is) security holes open?  I know VNC is inherently insecure, so I am hoping I can limit the connections to being within my own network.  

Thank you in advance,
-Evan

---

### Post by sirjoebob on 2009-06-28
Great question. Just ran into this myself. I am using an Ununtu-based home server/media PC and use VNC to connect to it over SSH. You can set up VNC to only allow connections on your local network (or just not open the port on your router). This keeps outside traffic out and you can connect to it from your iphone using wireless connection inside the home. 

This makes two assumptions:
1. you are running a wireless router
2. the iphone vnc client will connect to hosts using wifi

good luck and I hope I have been some help.

---

### Post by climhazzard on 2009-06-29
^Thank you for the reply, it is definitely helpful and you are indeed correct with your assumptions.

---

