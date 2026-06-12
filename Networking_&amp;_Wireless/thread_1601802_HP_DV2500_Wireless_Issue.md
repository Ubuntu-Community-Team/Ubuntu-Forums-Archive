---
title: "HP DV2500 Wireless Issue"
date: 2010-10-20
forum: Networking &amp; Wireless
---

### Post by JMac50 on 2010-10-20
I just installed a fresh copy of Ubuntu 10.10 on a HP DV2500 laptop.  Everything installed as expected but I am having some wireless issues I was hoping somebody could assist me with.  I am able to connect to my network via wireless with no issues.  However, when I attempt to browse the internet it will not connect to any pages.

Obviously when I connect it via CAT 5 all works as expected.  Any ideas on how to solve my wireless issues?

Thanks,

James

---

### Post by maximmai on 2010-11-27
Yea, I have been having the same issue and unable to resolve it. The following items are what I have tried:

1. I tried different versions of Ubuntu: { 8.04, 8.10, 9.04, 9.10, 10.04, 10.10, IBM OCDC 10.04, IBM OCDC 10.10 beta }. Wireless works in none of them, and also, in 8.10, 9.04, the ethernet doesnt work either.
I have also waking up the device, unlocking it (both the soft lock and hard lock), but still.


2. Windows 7 professional edition (64), wireless works after upgrading the driver.

3. Tried installing Windows XP pro (32), installation failed. 

I will paste some information about the system tonight/tomorrow, see we if we can sort something out.

Cheers,

Maxim Mai - [email]maxim.sl.mai@gmail.com[/email]

>>> 2010-11-27
I just had a thought in mind: would it work if we try the amd-64bit edition?

>>> 2010-11-28
ok, so that worked: I installed the amd 64 edition of ubuntu 9.04 on hp dv2500. And the wireless card finally started working. After the installation, the wireless icon shows something like "missing driver", then after few seconds, the Hardware Drivers manager pops up and prompts the recommended driver for the wireless adapter: Broadcom STA wireless driver. (wired thing is, it doesnt even need the inter net to get the driver out from the repository).

and also, I tried upgrading it to 9.10 from 9.04, unfortunately, the wireless issue came up right after the upgrading. So I had to do a fresh installation of amd64 ubuntu 9.04 again. sigh.

before that, I have also tried the amd64 ubuntu 10.10, 10.04, 9.10....

so that's the update. Wish you luck.

and sorry for bumping up such an old thread.

Cheers,

Maxim Mai - [email]maxim.sl.mai@gmail.com[/email]

---

