---
title: "Dual Boot Network Problem"
date: 2011-07-07
forum: Networking &amp; Wireless
---

### Post by LooBieola on 2011-07-07
Hi everybody,

I have a system that is dual booting Ubuntu 11.04 and OSX86.  The Ubuntu system was working great, but today I had to use the Mac side for awhile, and now when I reboot into Ubuntu it doesn't seem to be able to find the network.  After a period of scanning I get the "Wired Network Disconnected" message.  I wondered if it had something to do with my router being confused by multiple "machines" using the same MAC address (though not simultaneously).  However, even after restarting the router, I don't seem to have any internet in Ubuntu.  If I boot into OSX it works with no problems.

Anyone have any ideas what could be causing the issue?

I can give the results of ifconfig if they would be useful, but there's nothing out of the ordinary.  Ubuntu seems to know that the network card exists and what it is, it just can't get an IP address from the router.

I also tried sudo dhclient eth0 to no avail.

Thanks in advance for any help!

---

### Post by headvampyre@hotmail.co.uk on 2011-07-08
If it boots into OSX fine, then its not the router. Try setting a static IP on both the OS's, or configure your router to only give your machines MAC that IP.

---

### Post by LooBieola on 2011-07-08
Hey, thanks for the reply.  I managed to figure out the issue.  I'll post it here in case anybody else runs into the same thing.

From what I found out, the problem appears to be with dual booting and the Realtek 8169 family of network cards.  Apparently when the non-linux OS shuts down it puts the network card into a disabled state and due to some linux driver shortcoming, Ubuntu can't successfully re-enable the network card when it boots (other OSes can).

The solution for me was to completely shut down and even remove the power cable from the machine for 10 seconds.  By doing that the network card completely powers off and Ubuntu is able to power it back up on next boot.

---

### Post by LooBieola on 2011-07-08
For anyone interested in more details... here's a link to the post from which I got the solution.

[http://ubuntuforums.org/showthread.php?t=538448](http://ubuntuforums.org/showthread.php?t=538448)

---

