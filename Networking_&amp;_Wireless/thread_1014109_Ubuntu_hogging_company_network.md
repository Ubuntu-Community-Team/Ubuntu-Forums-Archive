---
title: "Ubuntu hogging company network"
date: 2008-12-17
forum: Networking &amp; Wireless
---

### Post by yekibud on 2008-12-17
At my new job I requested an Ubuntu machine.  On the second day I was embarrassed when I found out that my synaptic update downloads were causing the network (windows machines on a T1) to come to a crawl!

I know very little about networking and am at a loss as to how to troubleshoot this issue.  I ran the tc wondershaper script as a temporary work-around, but that only throttles HTTP.  I am going to need to transfer files via SSH/FTP as well.

Any help would be greatly appreciated.  I've been using Ubuntu for years at home and in small companies, but I'm going to have difficulty advocating Ubuntu at my new company if I can't get past this issue.

Thanks.

---

### Post by utnubuuser on 2008-12-17
I read something similar in another post, (couldn't tell you which though), and the problem turned out to be something related to Windows' cache/swap equivalent.
Wish I could remember which post.
I suppose what I'm getting at is that it might be worth your while to check how the Windows machines are handling the network rather than what Ubuntu is or isn't doing.

---

### Post by yekibud on 2008-12-17
Thanks for the reply, utnubuuser.

I didn't have any luck searching the forums for that post.

Don't know where to start figuring out how the Windows machines are handling the network in a way that would relate to this issue.

---

### Post by yekibud on 2008-12-29
**Update**

Installed Fedora 10 and confirmed that this is not an Ubuntu specific issue.  Still, it's a sad situation for Linux, because now I have to convince my IT manager to spend some time figuring out why the Linux machine is not behaving while all the other Windows boxes are.

Lord help me if I have to use Cygwin again to at least get some shell utilities...

---

### Post by yekibud on 2008-12-29
I think I may have figured this out!  I think it has something to do with this new machine having a Gigabit ethernet card.  I changed the MTU of my ethernet adapter to 500.  I tested downloading the latest kernel with the default 1500, and the network came to a crawl again (>3 sec pings and timeouts).  Then I changed the MTU to 500, removed the kernel, downloaded it again, and... voila!  The network didn't feel a thing.

Still, I wonder why I had to do this?  I thought 1500 was the 10/100 standard.  So if I was sending 1500 byte packets, why would this cause the network hardware to freak out?

Hm... Anyway, now I'm running Fedora - guess I could go back to Ubuntu, but I think I'll try Fedora for a while.

---

