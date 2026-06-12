---
title: "Wireless freezes my computer. Should I switch to ndiswrapper?"
date: 2010-07-28
forum: Networking &amp; Wireless
---

### Post by luisito on 2010-07-28
Since I upgraded to Lucid, I am dealing with serious instabilities related to my wireless card. What happens is that when there is a lot of wireless activity the computer freezes. It is a complete freeze, the mouse stops moving, if something was coming out of the speakers it keeps echoing, and the only solution is to turn off the computer.

The bug seems to coincide with the one listed in here
[https://bugs.launchpad.net/ubuntu/+bug/573704?comments=all](https://bugs.launchpad.net/ubuntu/+bug/573704?comments=all)
but it is not solved and there seems to be no activity around it.

My wireless card is Intersil ISL3890/ISL3886. My whole computer is an HP z555. I'm thinking that is should be a bug in the wireless adapter driver, which is p54pci. The only solution I can think of is to blacklist it and set up ndiswrapper. I am not very comfortable with this solution since a native linux driver should be better than ndiswrapper. What do you think I should do?

---

### Post by luisito on 2010-07-28
I did it. I switched to ndiswrapper. I'm not proud of this solution, but it seems to be working well now.

My original problem seems to be related to this kernel bug
[https://bugzilla.kernel.org/show_bug.cgi?id=11386](https://bugzilla.kernel.org/show_bug.cgi?id=11386)
Hopefully, it will be solved in future kernel releases.

---

