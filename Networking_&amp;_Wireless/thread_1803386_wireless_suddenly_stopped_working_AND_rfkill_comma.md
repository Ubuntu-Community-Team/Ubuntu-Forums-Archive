---
title: "wireless suddenly stopped working AND rfkill command not working!"
date: 2011-07-13
forum: Networking &amp; Wireless
---

### Post by bringingdadaback on 2011-07-13
Hello everyone,

When originally installing 11.04 I had problems getting my Ralink 5390 wireless card to work. Fortunately that was solved thanks to some helpful users here in the forums.

Today my computer froze completely and I had to turn it off via the power switch. When I turned it back on, wireless was no longer recognized! My iPod can connect to the network just fine, so it must be an Ubuntu problem. There are no problems with my ethernet connection either.

I researched this and found several threads about blocking and unblocking wireless devices using the rfkill command. Well, unfortunately for me the rfkill command **doesn't work**. When I type sudo rfkill list or sudo rfkill unblock all, nothing happens; it just returns me to my bash prompt. I even tried uninstalling and reinstalling rfkill...nothing.

Getting quite desperate here and would appreciate any help you can provide!

---

### Post by bringingdadaback on 2011-07-13
when I run lshw -c network, wireless is shown as "unclaimed."

does that mean that the patches I applied from [this thread]("http://ubuntuforums.org/showthread.php?t=1779005&highlight=ralink+5390") are no longer functioning?

---

