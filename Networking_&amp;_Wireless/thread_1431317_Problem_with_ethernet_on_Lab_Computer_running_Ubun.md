---
title: "Problem with ethernet on Lab Computer running Ubuntu at Research University/Hospital"
date: 2010-03-16
forum: Networking &amp; Wireless
---

### Post by kotoro on 2010-03-16
using an old mac notebook the same ethernet port works fully with internet, so I know the network isn't down anymore.

The network went down completely for a few minutes and when they brought it back up, the Ubuntu machine can no longer access the internet. It correctly recognizes when the network is plugged in.
(in this room there is only 1 active ethernet port and the PC is often unplugged to give access for the laptop). However, despite the fact that Ubuntu recognizes that it is connected to a network, after the short outage, it has lost the ability to connect to the internet. It was working just fine previously. What do I do?

(I haven't knowingly configured or installed anything that would change the network function, but something may have been installed as a dependency of something else. Otherwise it is an out-of-the-box configuration). There is no wireless card as the machine is an elderly Dell. 

(The Ubuntu OS was a fresh install performed last night, after their windows install got a virus and they agreed to have linux installed because they didn't really need windows and the machine was slow as hell running all the bloatware).

---

### Post by kotoro on 2010-03-16
The netowrk acts exactly the same from a boot on linux live using the CD, so I think they changed something on the network that caused the network to reject attempts to go outside from this computer, which is probably unrecognized  because it is new (previously with windows would have looked different to the network). Does anybody have any suggestions for what I can tell the helpdesk tech when they arrive?

---

### Post by memilanuk on 2010-03-16
Since you say the old Mac laptop worked before and still works now, I'd take a look at the network settings on it i.e. is it looking some place particular for its DHCP info, etc.  It might be informational to use an application like Wireshark to observe the actual traffic that goes back and forth between your Ubuntu desktop and rest of the network - it might give you an idea of what you're missing.

---

### Post by kotoro on 2010-03-17
Turns out it was what I thought in the last post. When I was backing up important files through an ftp connection prior to the Ubuntu installation, I tripped a network security protocol that scheduled an automatic block on that computer to occur the next morning. The computer had been reporting itself virus infected and the network sensed virus-like activity so it shut down the outbound connections.

---

