---
title: "Setting up a content filtering system - help!"
date: 2010-12-28
forum: Networking &amp; Wireless
---

### Post by Matt_Shimwell on 2010-12-28
Hi all,

I'm new to the forums (as you can see by my post count) and have been fiddling around with Ubuntu for a couple of months (specifically the FOG system). I've been tasked with creating a content filtering system that will prevent wired and wireless users from accessing certain sites. The most logical way of doing this that I could think of is as follows:

Internet (via Modem Router)
|
|
eth0 on Ubuntu machine
|
eth1 on Ubuntu machine
|
|
Wired/wireless access point
|
|
Client PCs

I hope I can explain myself as much as best I can here. I know relatively little about this whole process; it just looks to me to be the most logical way of doing it. I'll also point out I have all the hardware I mentioned above (2 network cards, access point, etc). I've been fiddling with dhcp3-server, dansguardian and squidproxy for days now but I think it's just my lack of knowledge that is preventing me from understanding how the process works and thus how I can achieve what I want. Is there anyone that could take the time to explain as verbosely as possbile how this whole process works!? Even better if someone could point me to a guide. If there is an easier way of achieving a content filter, please, let me know, but I assumed this was going to be the easiest way as everything can be controlled from one machine rather than having to modify settings on the clients, which I cannot do as the client machines will be owned by people moving in and out of the accomodation where this system will be based.

I'd really appreciate any help that will get me any closer to my goal. If anyone would like to know more about what hardware I have, what methods I have tried, please give me a shout!

Thanks in advance,

Matt Shimwell

---

