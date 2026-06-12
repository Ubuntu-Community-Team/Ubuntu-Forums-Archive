---
title: "Guest to Host networking problem"
date: 2010-11-05
forum: Networking &amp; Wireless
---

### Post by chaorace on 2010-11-05
Ok I managed to (with much hackery) turn my old CDMA phone into a modem, unfortunately it requires windows drivers. No problem, I decide to boot up my XP pro 86X on virtual box, but this is where my problem began... I managed to connect to my modem device in XP and I can connect to the Internet IN XP, but the host (linux ubuntu) didn't detect the connection and remained disconnected. A minor setback which can be remedied by a guest to host network... so I shut XP down and toggled settings and enabled a second virtual network adapter (the first one being so the guest can use the hosts connection) and due to my lack of networking knowledge I became lost upon all the options. After a quick consult of the help guide, I tried the bridged adaptor, but ubuntu didn't really do anything about it except acknowledging that vboxnet0eth0 exists in network-admin. Then, I decide: sc**w it, I'll just try setting up a host-only adaptor to create the network instead, and I failed in a very similar manner except it shows vboxnet0  instead. 

Overview:
HARDWARE:
Host OS: Ubuntu Maverick Meerkat beta 86X
Guest OS: Win XP Pro SP3 86X
Virtualisation software: VirtualBox closed-source edition

What I want to do:
set up a network between Host and Guest so the host can access the Internet through the wireless modem connected to the guest

What I've done:
1) Set up a dial up connection via wireless modem in XP guest
2) Set up a virtual network adapter
3) ran S**t out of Luck

Please feel free to ask for more information, but please reply fast as I only have a short window of opportunity to make this work before going away from home in a few hours!

---

### Post by chaorace on 2010-11-05
just realised that this should go in the virtualisation section instead... Oh MR admin!\\:D/

---

### Post by chaorace on 2010-11-05
BUMP: I really need help... I mean seriously, what does it take to get a reply around here?](*,)

---

### Post by chaorace on 2010-11-07
ok... well I found  solution! Ok I totally forgot that connection manger had a mobile broadband option! so all I did was click the mobile broadband tab than create  new connection. I just followed the setup and connected my phone and it all worked! None of this virtualbox junk! Anyway..... bye!

---

