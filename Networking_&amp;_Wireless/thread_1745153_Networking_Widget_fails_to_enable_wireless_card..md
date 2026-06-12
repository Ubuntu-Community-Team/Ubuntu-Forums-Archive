---
title: "Networking Widget fails to enable wireless card."
date: 2011-04-30
forum: Networking &amp; Wireless
---

### Post by Ironlenny on 2011-04-30
I just upgraded to natty last night, and everything is working fine execpt for the network manager.  I can enable and configure the wireless card via bash, but the network manager widget will not manage the wireless card.

When I first boot up, the "Enable wireless" check box is greyed out.  After I enable the card via the terminal, the "Enable wireless" check box becomes ungreyed, but every time I click it, it instiantly unchecks itself.  I feel like Currly from the Three Stoogies.  Check, uncheck, Check, uncheck.  Mmmmph. "Slaps face repeatedly."

Has anyone one encountered this problem?  Any suggestions?

---

### Post by linuksamiko on 2011-05-01
I'm having the same problem. I thought this might be a general problem but it look like it is only a KDE related bug.

This is really anoying and yesterday it worked after a few times of disabeling and enabeling the network but today it wouldn't work at all anymore.

I would be glad too if somebody had a solution for this

---

### Post by linuksamiko on 2011-05-01
I gues I found something [here]("https://bugs.launchpad.net/ubuntu/+source/plasma-widget-networkmanagement/+bug/762443"). I will try it out right now.
Basicly it say there are some issues with the old plasma-widget-networkmanagement and the new network-manager-kde. Since I upgrade my computer now for quite a few releases there might be some old packages left over. I give it a try.

---

