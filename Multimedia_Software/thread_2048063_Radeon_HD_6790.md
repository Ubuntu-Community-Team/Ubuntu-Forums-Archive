---
title: "Radeon HD 6790"
date: 2012-08-26
forum: Multimedia Software
---

### Post by Idefix82 on 2012-08-26
I just installed a Radeon HD 6790. Before that, I was only using the on board card, and even before that, I had the Radeon 6770 in there. I still had the proprietary driver installed.

When I started up the computer with the new card, the command lspci showed that I had a "Radeon HD 6700 Series" card. I thought that this was not sufficiently specific and that the driver was not recognising the new card properly, so I deinstalled the proprietary driver with the aim of reinstalling it after a reboot. Alas, after reboot, Ubuntu would not boot at all, not even in recovery mode. The computer crashed in the course of booting and the monitor would lose any signal.

So I took out the new card again (actually, I only detached it from the power supply, but left it in the slot), started up with the on board card, installed the proprietary driver again, shutdown, attached the HD 6790 again, and started up. Now, I can again boot into Ubuntu, and the lspci command again returns "Radeon HD 6700 Series".

**Question 1:** Is that the correct output or does it mean that the card is not being properly recognised?

**Question 2:** I haven't heard or read anywhere that Ubuntu cannot handle the card without the proprietary driver. I couldn't boot from the Live CD with this card either. How do people install Ubuntu with this card in the first place? Could someone explain this behaviour to me?

---

