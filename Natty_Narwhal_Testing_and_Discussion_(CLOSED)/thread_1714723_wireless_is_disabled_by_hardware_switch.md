---
title: "wireless is disabled by hardware switch"
date: 2011-03-25
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by dklean15 on 2011-03-25
i have 10.04 on my computer right now. decided to download natty.  the Internet does not show up. instead it says: wireless is disabled by hardware switch.  so i went back to 10.04 and it works perfectly fine. i have a compaq cq 60, 64 bit .. any ideas on how i can fix this? anything will will be greatly appreciated!

---

### Post by cariboo on 2011-03-25
Did you turn the wireless switch off and on?

---

### Post by buzzmandt on 2011-03-25
laptop? if it is it should have a wireless switch or button.  press it and see what happens

---

### Post by Reiger on 2011-03-25
Try, rfkill list and sudo rfkill unblock $device.

---

### Post by donniezazen on 2011-03-26
I am sorry but i have been telling there are serious problems with wireless on natty. I have tried all this but none worked.

Please add yourself to this bug to gain developer's attention.

[https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/712053](https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/712053)

---

### Post by shuttleworthwannabe on 2011-03-26
yah, on my Dell Vostro 3700 (flippen broadcom wireless device) the wireless works perfectly (using the built in STA BoradCom drivers autodetected), but the LED lights are off--I am hoping there will be a bug fix for this as I have seen many other people with the same problem (mainly with Acer and HP hardwares).

---

### Post by cariboo on 2011-03-26
I use a HP/Compaq netbook with Broadcom chipset, the switch works, and the led color changes from blue to amber when wireless is disabled..

I'm starting to find that there isn't any consistency in Broadcom chip sets. What works for one system model doesn't work for another even if it has the same chipset number.

---

### Post by stevevai on 2011-04-14
> **Reiger said:**
> Try, rfkill list and sudo rfkill unblock $device.

This worked for me. Thanx.

---

