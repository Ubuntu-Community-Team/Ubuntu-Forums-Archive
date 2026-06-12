---
title: "SSH tunnel to remote host"
date: 2008-12-29
forum: Networking &amp; Wireless
---

### Post by shearn89 on 2008-12-29
hey all - a question about network protocols...

Here's the situation:

I live on campus at a school where my dad works. I'm not a pupil anymore, but i have a login, and using the home station I can get to facebook, twitter, etc etc.

I use my laptop on the wireless that the techies set up for us, except I can't authenticate on the network, meaning I can't get the privileges that my network login has - so no facebook/youtube/twitter.

I also can't ssh out to my uni network, since the firewall seems to block everything, including ssh. It lets skype and msn through though.

Basically, I want to (if its at all possible) tunnel from my laptop through the local firewall to university, where I can do as i please (use mercurial to update my bitbucket repo, check facebook, twitter, use git, etc etc), and then transfer files back to my laptop.

I think i would need to create a local tunnel that tunnels from port 22 - 80, then a remote one that does 80 back to 22, or something along those lines. Anyone familiar with ssh help me out?

I'm on msn if anyone wants to msg me, unfortunately no IRC due to the reasons above...

---

