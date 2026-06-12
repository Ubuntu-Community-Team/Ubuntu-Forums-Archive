---
title: "iwlagn causing kernel panic"
date: 2011-06-20
forum: Networking &amp; Wireless
---

### Post by f_padia on 2011-06-20
I believe the network driver (iwlagn) on my laptop is causing kernel panic upon resume from suspend. I dont have any problems in normal use of the laptop but when I wake it from suspend all I get it is a flashing caps lock key which I have read means kernel panic. 

Im not 100% that its iwlagn but I disabled iwlagn using modprobe -r iwlagn and there wasnt any kernel panic upon resume from suspend. But when I re-enabled iwlagn it started again.

I've seen that there have been similar problems in the past but all the threads were from 2008 so I thought those problems must've been fixed with later versions of iwlagn so I'm not sure why its happening to me now. I have a HP pavilion dv5 laptop running Ubuntu 11.04. The network panic only started about a week ago. Perhaps some update caused this.

Can anyone help please?

---

