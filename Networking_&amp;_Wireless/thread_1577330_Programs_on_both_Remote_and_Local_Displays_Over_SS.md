---
title: "Programs on both Remote and Local Displays Over SSH?"
date: 2010-09-18
forum: Networking &amp; Wireless
---

### Post by mangy_mathan on 2010-09-18
I have two laptops, both running Ubuntu 10.04. My goal is to be able to use computer A as a presentation screen remotely from computer B. Meaning I want people to be able to see what I'm doing on computer A.

 I have figured out how to access computer A from computer B using SSH, as well as X forwarding. However, programs initiated through the tunnel open on computer B, and not on A.

I have figured out that by using export *DISPLAY=:0* I can get programs to open on computer A. However, I can't see them from computer B.

My question is, how can I get programs to display on both the local and remote screens.

The idea is that my friends and I will be playing Dungeons and Dragons long-distance, and I want to be able to commandeer my friend's laptop to display maps and play music, but I want to be able to see what I'm doing on his screen.

How might I go about doing this, or is there a better way than using SSH tunneling? If possible, I prefer SSH.

---

