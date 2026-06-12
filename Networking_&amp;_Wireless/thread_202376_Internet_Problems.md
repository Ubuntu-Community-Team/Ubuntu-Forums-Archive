---
title: "Internet Problems"
date: 2006-06-23
forum: Networking &amp; Wireless
---

### Post by tprzepiorka on 2006-06-23
i recently installed Ubuntu 6.06 and i cant seem to get the internet working properly. Some sites it will load for a long time and show limited content other sites it wont work at all. I have a wired, broadband connection. Pinging most sites seems to work fine. thank you

---

### Post by jhofmann on 2006-06-24
When I hear the words "long time", I immediately think of a problem with the nameserver.  Did the connection work better with another computer?  
In other words, is the connection known to be fast?

Have you looked at the configuration in System->Administration->networking  ?
Perhaps you are supposed to supply a nameserver in the DNS form.

Wish I could be more specific.

---

### Post by eholly on 2006-06-27
I have had similar problems.  ipv6 seems to be the difirence between sites.  Turning it off seems to cure the problem.  Waiting 2-3 days works too.  (several re-boots ?)

modify  the /etc/modporbe.d/aliases file. You have to sudo -i first.

But then re-boot is required.

alias net-pf-10 ipv6 off
alias net-pf-10 off
alias ipv6 off
#alias net-pf-10 ipv6

IPV6 slows down the IPV4 environment if the router does not understand IPV6 and for most people IPV6 is not needed.

So, add the 3 lines, comment out the orginal, save and re-boot.

Firefox and Thunderbird will respond 3 to 4 times faster


                  E Holly

---

