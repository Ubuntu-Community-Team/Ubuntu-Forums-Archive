---
title: "BREAKTHROUGH r8169 , at least for me.."
date: 2009-06-12
forum: Networking &amp; Wireless
---

### Post by thieaux on 2009-06-12
For the last couple of days i was struggling to get my card to work at 1000mbs , no matter what i did seem to work, drivers, booting with flags, nothing seem to work.

My setup was a ubuntu 9.04 desktop, with a ga311 gigabit nic with rtl8169 chiposet v10, and a netgear gs105 gigabit switch.

at first i thought it was a doa card , but tried on a mac pro and windowx box, and it worked flawlessly. so it wasnt the card.

Last night i hooked it up directly to my mac pro, and presto!!!!!! GIGABIT LINK, i thought yeah this is normal, at first it would link up for a couple of seconds and then it would revert to 100mbs.

GUESS WHAT , it didnt , So the problem seems to be with the switch.....NOT EXACTLY, BECAUSE it worked on the mac and windows box with the same switch.... SO?

the problem is with the kernel supplied driver and the switch ,NOT THE CARD NOR THE CHIPSET, at least for me ...its an issue with the driver and the netgear switch or the chiset in the switch and the driver...

If you have the same issue try it without a switch and connect it directly to another pc and try your speed and see if you get it to link at 1000mbs..

My speed were sustained 25MBS with the eventual peek to 40MBS....if you have any ideas please post ..

I hope it helps someone...
:p

---

