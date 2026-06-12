---
title: "Automounting NAS drive and Windows 7 share on startup, after login and via wireless"
date: 2012-03-11
forum: Networking &amp; Wireless
---

### Post by Mizo_Mizo on 2012-03-11
Hey!

Well, the title says pretty much it all - I'm running Ubuntu 11.10 on my laptop and have a PC running Windows 7 and a WD MyBookworld (Blue Rings) NAS storage connected to the router so that all three machines are in the same network, which I access  connect to with my laptop via Wi-Fi. 

Now, when I access the PC or the external hard drive (the NAS) *graphically*, it all works fine and gets mounted. What I want specifically is that a Windows-shared folder in the PC and the NAS storage are mounted automatically after I login and the Wi-Fi connection is established, so that I don't have to mount them myself via Nautilus.

I naively tried editing fstab but then noticed it just wouldn't work because it would run before connection was established. A simple "mount -a" script scheduled to run on startup won't do the trick either. The three devices are on the same network range and, as I said, the problem is just to automate the process of mounting the shares so that they're damn ready without my having to stupidly click on the icons so that they get mounted.

I must be missing something here, but nearly any post I found was concerned with wireless connections, and those that weren't didn't help me much. Any help is very welcome!

---

