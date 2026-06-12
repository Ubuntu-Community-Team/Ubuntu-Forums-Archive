---
title: "Vista shares not visible - but used to be!"
date: 2009-01-14
forum: Networking &amp; Wireless
---

### Post by mic1000 on 2009-01-14
I'm guessing that this might not be a problem on the Ubuntu side, but it's very infuriating and hopefully someone can help.

I've been able to see, browse and access shares from my Vista media center box from my Ubuntu laptop without problem since switching the laptop to Ubuntu (so I'm a newbie - sorry!).

Unfortunately the Vista box needed a complete reinstallation after needing a new HD, and since then I can no longer see the Vista file shares. The Vista shares can be accessed from another XP machine on the network (and vice versa), so the basics of the Vista sharing are there I think.

And on the laptop, browsing from Places>Network>Windows Network shows the workgroup correctly, clicking that shows the Vista machine, but then clicking that just gives an empty window - no shares!

I've searched around and it seems there have been a few Ubuntu issues which give the same result, but I had this working fine until I reinstalled Vista - I haven't touched a thing on the laptop!

Now, if I try to navigate directly by typing smb://mediacentre/<share> into the location bar, it will ask me for the username, domain and password of the share, so it looks like it can be found. I'm not sure what exactly I should type as neither my Vista or Ubuntu username/password work with either the domain field left blank or with the workgroup name, in any combination.

Any suggestions very much appreciated, as at the moment I'm cut off from most of my files, unless I sit using the Vista box.

Thanks,

Mark.

---

### Post by BuntuFreak on 2009-03-30
> **mic1000 said:**
> I'm guessing that this might not be a problem on the Ubuntu side, but it's very infuriating and hopefully someone can help.

I've been able to see, browse and access shares from my Vista media center box from my Ubuntu laptop without problem since switching the laptop to Ubuntu (so I'm a newbie - sorry!).

Unfortunately the Vista box needed a complete reinstallation after needing a new HD, and since then I can no longer see the Vista file shares. The Vista shares can be accessed from another XP machine on the network (and vice versa), so the basics of the Vista sharing are there I think.

And on the laptop, browsing from Places>Network>Windows Network shows the workgroup correctly, clicking that shows the Vista machine, but then clicking that just gives an empty window - no shares!

I've searched around and it seems there have been a few Ubuntu issues which give the same result, but I had this working fine until I reinstalled Vista - I haven't touched a thing on the laptop!

Now, if I try to navigate directly by typing smb://mediacentre/<share> into the location bar, it will ask me for the username, domain and password of the share, so it looks like it can be found. I'm not sure what exactly I should type as neither my Vista or Ubuntu username/password work with either the domain field left blank or with the workgroup name, in any combination.

Any suggestions very much appreciated, as at the moment I'm cut off from most of my files, unless I sit using the Vista box.

Thanks,

Mark.

I'm having the same exact issue, except that I'm using XP media center. Not only can my Ubuntu box cannot see it, other Vista Home Premium and XP Pro boxes cannot see it either.

---

### Post by lisati on 2009-03-30
Please pardon my tardiness in replying: distracted by the lady of the house who was muttering something about "Dr Phil is talking to you" (guess what's playing on TV now?) and I accidentally closed my browser by clicking on the "wrong" thing...... plus firing up two other machines in the household so I could check out where to look.....

The settings on VISTA can be found on the control panel: there should be a small link under the "Network and internet" heading. "Set up file sharing"

XP's control panel is organized a bit differently, for me clicking on "Network and Internet Connections", "Set up or change your home or small office network", and answering the Wizard's questions did the trick

---

