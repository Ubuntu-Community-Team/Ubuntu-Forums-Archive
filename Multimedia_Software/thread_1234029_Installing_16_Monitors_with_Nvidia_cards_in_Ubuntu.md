---
title: "Installing 16 Monitors with Nvidia cards in Ubuntu"
date: 2009-08-07
forum: Multimedia Software
---

### Post by ekisamo on 2009-08-07
Hi Guys, I have set up a dual processor Lenovo workstation (Intel X58) with Ubuntu, and have 2 x Nvidia NVS450 and 2 x NVIDIA NVS 420, each one of these cards can only take 4 monitors, so far I have been able to get 12 monitors working, the NVS420 kept being dropped off.....does anyone has an idea on how will I get the fourth card to show up with the 4 monitors?

---

### Post by tgalati4 on 2009-08-07
In a terminal:

$dmesg | tail

Do you get 16 monitors for a short period and then they drop off?

Sounds like a bus problem.  You could try rearranging the cards to see if the same slot keeps dropping.

I'm guessing you are pushing what the southbridge (I/O) bus is capable of.

Put your finger on it, I bet it's toasty.

Also measure your voltage 5V and 12V.  You could also be running out of power. Any dips below 5V and 12V will cause strange problems.

---

### Post by ekisamo on 2009-08-07
No I have only been able to get 12 monitors working from the 3 video cards - 2xNVS450 and a 1xNVS420. And they don't drop, I left them on for a while they are still working fine. The south bridge is fine, there is a customer got all 16 monitors to show up with ubuntu, with the same Nvidia cards as the ones I'm using here....do you know how to look up in ubuntu to make sure that all the cards do show up?

---

### Post by tgalati4 on 2009-08-07
sudo lspci -vv
dmesg | more   (look for errors)

---

