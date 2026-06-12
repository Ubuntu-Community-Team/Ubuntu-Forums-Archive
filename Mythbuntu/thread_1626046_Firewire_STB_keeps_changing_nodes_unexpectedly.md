---
title: "Firewire STB keeps changing nodes unexpectedly"
date: 2010-11-19
forum: Mythbuntu
---

### Post by mrdek11 on 2010-11-19
Hi all,

I use a Comcast STB (Pace RNG110) via firewire, which was working great when I set it up.

I've noticed that after one or two times of trying to access it, the box will change firewire nodes unexpectedly.  When the computer boots up, it is on Host Adapter 0, Node 1, but after running for some time, plugreport shows it running on Node 0 (And I can access/watch TV on Node 0), but after the next reboot, it's thrown back to Node 1.

Does anybody have any ideas of how to force it to pick a node and stay there?

Thanks in advance for any light anybody can shed,
Derek

---

### Post by LowSky on 2010-11-20
check your settings in mythtv there is aetting that will reset the firewire connection if it thinks i looses connection

from the backend go to general setting, third page, last option on the page

---

### Post by mrdek11 on 2010-12-01
Thanks for the tip! I've been on vacation and only just got home to see your response and try it out.  It seems like when I have that option turned on, the firewire connection will just go down entirely rather than just switching nodes.  Any ideas?

Thanks again!

---

