---
title: "Laptop Graphics Card ATI 4650"
date: 2009-08-14
forum: Multimedia Software
---

### Post by machiavell1 on 2009-08-14
Hello

I just recently purchased a Toshiba laptop with an ATI Radeon Mobility 4650HD graphics card.  I installed Ubuntu 9.04 x64. The card shows up when I run lspci in the terminal, but the only resolution available to me is 1024x768.  How do I fix this (if that's possible)?  There seems to be little information on this card available.

---

### Post by happyisland on 2009-08-14
Hi,

I have the same card in the Vaio FW I got last week. The solution for me was fglrx, and then selecting the hardware driver from the System>Administration>Hardware Drivers menu.

---

### Post by machiavell1 on 2009-08-15
Thanks for the response.  Did you use the fglrx from the Ubuntu repositories?

---

