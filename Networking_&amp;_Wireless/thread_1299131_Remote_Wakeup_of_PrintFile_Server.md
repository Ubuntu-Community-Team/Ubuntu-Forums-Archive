---
title: "Remote Wakeup of Print/File Server?"
date: 2009-10-23
forum: Networking &amp; Wireless
---

### Post by dbsoundman on 2009-10-23
I've got an old desktop machine in my living room running Ubuntu, and I was thinking of moving my printer out there to serve as a print server, since my roommate and I are now sharing my printer. What I was hoping to do was be able to leave the machine on but let it go into standby/suspend mode after a certain amount of time, but then have it wake up when it receives a print job, or if I access it via SSH or something like that. Is there a way to do this? I *think* that computer has wake-on-LAN capabilities but I'm not sure; I haven't been able to get it to work yet but I haven't put much effort into it. I'm also thinking that WOL isn't the answer, though, since it involves having to send that magic key thing to wake it up. I'm just looking to streamline the process and save some energy at the same time. Thanks for your help!

-Dan

---

### Post by tzicatl on 2009-10-24
> **dbsoundman said:**
> I've got an old desktop machine in my living room running Ubuntu, and I was thinking of moving my printer out there to serve as a print server, since my roommate and I are now sharing my printer. What I was hoping to do was be able to leave the machine on but let it go into standby/suspend mode after a certain amount of time, but then have it wake up when it receives a print job, or if I access it via SSH or something like that. Is there a way to do this? I *think* that computer has wake-on-LAN capabilities but I'm not sure; I haven't been able to get it to work yet but I haven't put much effort into it. I'm also thinking that WOL isn't the answer, though, since it involves having to send that magic key thing to wake it up. I'm just looking to streamline the process and save some energy at the same time. Thanks for your help!

-Dan

Without WOL I can think of inetd or xinetd and some power management scripting.

Noe

---

### Post by dbsoundman on 2009-10-28
Could you elaborate a bit on this? The main reason I wanted to avoid WOL is simply because it looks like you have to manually send the "magic packet" every time you want to wake up the remote machine, plus I don't even know if WOL works, I tried it once and nothing happened. Basically this would have to work such that any user with any OS within the network who has the IP address for the printer can print from it. So, my roommate running vista could use it, my laptop running ubuntu could use it, etc. I'm also not tied to having it all the way at S4 powersave; if it has to be on a lower powersave mode so be it, I'm just hoping to make it slightly more efficient.

-Dan

---

### Post by allanlewis on 2009-11-23
*bump*

---

### Post by egpetrich on 2010-02-06
This is actually a research topic right now, which gives me the idea that it isn't very easy:

[http://research.microsoft.com/en-us/um/people/ranveer/docs/somniloquy.pdf](http://research.microsoft.com/en-us/um/people/ranveer/docs/somniloquy.pdf)

The linked paper describes an architecture for setting up a network proxy; the proxy takes the place of a sleeping computer and maintains a network presence. The authors are interested in using the proxy for stuff like BitTorrent, but they also talk about using the proxy to wake up the primary computer when requests come in.

Based on what I've read there (and not on much beyond that), I'm thinking that a wake-on-LAN method is your only way to have a server that reaches S3 or deeper without additional hardware.

I've been thinking about this a bit recently, since I have a file server for which I'd like to reduce power consumption. Thoughts include using a startup program on the client to send wake-on-LAN when the client boots, and then having the server stay awake as long as it has a Samba share open.

---

