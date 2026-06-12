---
title: "pvr-250 remote and mythmovies porblems"
date: 2008-05-18
forum: Mythbuntu
---

### Post by ctucker10 on 2008-05-18
I've been using Mythbuntu for a week but, I am not new MythTV. I briefly tried Knoppmyth and I used Mythdora for about 2 years before checking out this distro.

Anyway, after installing Mythbuntu I found that I had to tweak the remote control configuration--a Hauppauge PVR-250 A415-HPG remote control--to make the buttons work the way I wanted.

Yesterday, after allowing a software update, I found that my remote no longer worked the way I had configured it. I also noticed another minor annoyance: whenever I select Mythmovies from the Information Center menu the frontend crashes, kicking me back to the XFCE desktop.

I have two questions. How do I reconfigure the remote? The file I edited, I think it was /etc/lircd.conf, is not the same format that it was last week. And, does anyone have any ideas on why Mythmovies is crashing. There is a transcoding job in progress but, I don't think my processor is being taxed too heavily when navigating menus while transcoding a recording.

Any help you can provide it appreciated. By the way, Mythbuntu is a great distro for installing MythTV.

---

### Post by ctucker10 on 2008-05-18
I figured out part of what I asked about.

The file I needed to edit for configuring my remote control is ~/.lirc/mythtv. My particular remote is referred to as "Hauppauge_350" in this file. The format of the file is easy enough to understand. I made the changes I desired then restarted the lirc daemon. That part of my orginal problem is resolved.

As for the Mythmovies module crashing? It's not a big deal. I'll try to figure that one out when I get more time.

---

