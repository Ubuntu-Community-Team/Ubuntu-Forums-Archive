---
title: "Hardware detection in Ubuntu vs Slackware (+Slackware help)"
date: 2011-02-04
forum: Networking &amp; Wireless
---

### Post by vacco on 2011-02-04
This post has two parts. First the part that might look a little misplaced on this forum, but which I hope someone may still know a thing or two about:

I have installed Slackware (alongside Ubuntu and Windows 7) to have something to play around with and hopefully learn a thing or two.
I am able to get KDE up and running, but in the interfaces list under network preferences, neither my wireless nor my wired network card shows up. Both cards show up correctly in lspci:
```
03:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe (rev 10)
09:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)

``` (this is from lspci in Ubuntu, but it is pretty much similar in Slackware.
If anyone who drops by this thread happens to know something about getting these things to work, your knowledge would be appreciated. I think this is my first experience with a distro where the *wired* network does not work out of the box.

This challenge has caused me to wonder about the second part of this post.
What is it that makes Ubuntu good at hardware detection? I know the Linux kernel should detect most hardware, but if that was the whole truth, there would be no difference between distributions in this aspect, correct?

---

### Post by andrew.46 on 2011-02-14
Perhaps on your Slackware partition try installing wicd, you will find it in the /extra directory of your installation media. Install it by using the *installpkg *command and then try your network setup from within wicd itself. Further Slackware problems might be better served by going here:

[http://www.linuxquestions.org/questions/slackware-14/](http://www.linuxquestions.org/questions/slackware-14/)

Bear in mind there is a very different approach on the Slackware forums than is seen here :).

---

