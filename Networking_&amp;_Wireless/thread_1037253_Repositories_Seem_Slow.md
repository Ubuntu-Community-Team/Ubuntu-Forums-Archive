---
title: "Repositories Seem Slow"
date: 2009-01-11
forum: Networking &amp; Wireless
---

### Post by wsmoser2004 on 2009-01-11
For some reason, whenever I try to download updates from my house, they download painfully slow - around 300 B/s is very common.  Usually the download starts fairly fast - 160 Kb/s but then plummets down until it is under 1 Kb/s.  If I am lucky, it will occasionally go back up to 160 Kb/s for a while, but then drop back down again.  

I don't believe it's a problem with my installation - when I upgraded to Intrepid I took my laptop in to work and the update downloaded fast.  I am thinking it must be a problem with my ISP, or my connection, or something.  However, I don't know where to start looking for the problem.

Other downloads seem fast - at least HTTP downloads.  I have a DSL connection, and my top speed is usually around 165-170 Kb/s.  I have already tried to "Select best server" and that does not fix it.  The United States server seems to be the fastest for me overall.

As an example, I just tried to check for new updates.  After about 15 minutes of waiting, I gave up and clicked "Cancel"...and that was just downloading the package info!  The estimated time remaining to finish downloading the package info was over 5 hours.  When I tried to actually download and install the updates, the download time remaining was something above 32 days.  

I have also removed all third-party repositories from my list, which didn't seem to help.  

Does anyone know how I might go about diagnosing this problem?  Is it my ISP?  My connection (wireless, WPA-PSK, DSL)?  Something else?

Thanks!

---

### Post by wsmoser2004 on 2009-01-18
I played around with this problem a little more, and I discovered that I was wrong - it is not just the repository downloads that are slow.  Most other downloads are slow as well.  For example, I tried to test my connection's speed at speedtest.net, and 9 times out of 10 the test won't even complete.  It gets stuck "downloading," usually around 50%.  

However, I've narrowed it down to something with my Ubuntu installation.  If I reboot the same laptop to Windows XP, everything is fine.  All other computers in the house seem to be fine, including another running Ubuntu.  I've put in a different wireless card and tried hooking the laptop via a wired connection, and neither of those worked.  I've also tried disabling IPv6 and my firewall, and neither of those did the trick either.  If I use a LiveCD, everything seems to work fine there as well.

I am running out of ideas...

---

