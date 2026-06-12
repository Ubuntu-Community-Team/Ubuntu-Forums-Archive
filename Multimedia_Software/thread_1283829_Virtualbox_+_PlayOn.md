---
title: "Virtualbox + PlayOn"
date: 2009-10-05
forum: Multimedia Software
---

### Post by tnunamak on 2009-10-05
I've been setting my approaching-outdated desktop computer up as a server and am also trying to get it going as a media center. Here are some specs
-Nvidia 6800gs graphics card
-2gb memory
-Pentium D 805 (predecessor to the core 2 duos)

I'm running Xfce to keep the overhead low. What I'd like to do is run PlayOn in VirtualBox, either in Windows 7 or XP. I'm wondering whether it makes a difference which of those two OS's I use, and how much memory I should allocate to it.

I've currently got Windows 7 with about 800mb memory allocated on a bridged connection uploading at about 400-500KB/s. In both XBMC and my PS3, video is laggy at best (especially Netflix, which is horrible).

Should I switch to XP? Give more memory to the virtual OS? Less? Will it just not work?

It's very unfortunate that Netflix isn't supported in Linux. Otherwise I'd probably be just fine. Thanks for the help!

---

### Post by beastrace91 on 2009-10-05
Yes it is :/

Have you tried running IE6/7 through Wine? From what I have read online if you really need the netflix support just run Winblows :(

~Jeff

---

### Post by tnunamak on 2009-10-06
I've heard that it won't work in wine for multiple reasons having to do with DRM and ActiveX, etc. 

I'm really trying not to use windows is because I want to avoid rebooting my server to a different OS when I want to use it for media. I might even go so far as to install Windows as a host OS and run Linux as a guest on a VM if I have to. I'd really like to avoid it though.

---

### Post by beastrace91 on 2009-10-06
Oh, if this is the case give the Windows VM a go first. I'd just give it just under half of your total RAM (840 or so) and deff use XP as Win7 still uses alot of RAM like Vista did.

But note - performance for videos/3d in virtual machines you are always going to see a sizeable performance drop...

~Jeff

---

