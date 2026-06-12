---
title: "Putting screen to sleep stops connectivity?"
date: 2010-02-20
forum: Networking &amp; Wireless
---

### Post by Chris-Chicken on 2010-02-20
Hello all,

It has come to my attention that if my laptop's screen (not the computer itself) is put to sleep, then connectivity stops until it is woken up again.

This is very annoying!

Any ideas on how to prevent this / how to work out why it happens would be most appreciated!!

Thanks in advance,

Chris.

Ubuntu (NBR) 9.10, running in a HPmini1030nr, Broadcom wireless card.

---

### Post by puppywhacker on 2010-02-20
First check the settings in the BIOS. In ubuntu you can change the power settings in the system / preferences / power management.

The situation you describe sounds like a lid switch policy or other sleep policy, which makes the whole computer sleep when you close the screen. network only goes down when the computer goes down. Network is not related to the Screendrivers directly.

---

### Post by Chris-Chicken on 2010-02-20
Well, in the Power Management dialogue box, the screen (not the computer) is set to be 'put to sleep' after 30 mins, or when the lid is closed. When this happens (on AC and battery) connectivity seems to be suspended (based on Transmission <bit torrent client> activity).

The "Put computer to sleep when inactive for..." option is set to "Never"......

I'm pretty sure it is the screen setting, as it's set to ten minutes when on battery, and I have the same problem there.....

Could the system somehow be putting itself to sleep instead of just the screen? I have no idea how to check this. 

Thanks again. :)

---

