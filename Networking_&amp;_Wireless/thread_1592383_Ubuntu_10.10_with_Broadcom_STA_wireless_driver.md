---
title: "Ubuntu 10.10 with Broadcom STA wireless driver"
date: 2010-10-10
forum: Networking &amp; Wireless
---

### Post by taabouzeid on 2010-10-10
The only problem i had with ubuntu since i purchased my laptop Dell inspiron 1564 is the wireless driver.

[LIST]
[*]In Ubuntu karmic koala I had to enable Broadcom STA wireless driver from System > Admin > Hardware drivers.
[*]In Ubuntu lucid lynx i had to do that before installtion from the live cd, otherwise i had no luck installing the driver even with wired connection available.
[*]In Ubuntu Maverick Meerkat i did as lucid lynx, it worked for the live session but not after installation. The solution was to disable bcmwl-kernel-source package from synaptic package manager then reinstall it ! I am not sure what's the problem exactly but that's how it worked for me. 
Before the last step i received an error logged in /var/log/jockey.log like that
```
2010-10-10 21:27:45,207 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
```
[/LIST]
So anyone finding this problem you can try this out

---

### Post by virtual_m on 2010-10-29
I have the same problem. I'll try is it work.
btw my notebook is Toshiba Satellite L650 14f, with the same w-lan card


EDIT: Thx. It's work!

---

### Post by jdamianb on 2010-11-22
Hello!

I own a HP Touchsmart Tx2 and I had The same problem Until I tried this solution. Thank You!

BTW, why if the new driver is b43 instead of bcm43 it is not automatically installed :S ... 

Greetings!

---

### Post by hajisep on 2011-04-18
had the same problem in Compaq-CQ40 and solved.
Thank you very much! Really appreciate it!

---

### Post by pritam_par on 2011-07-20
I too have faced the same problem and it is solved in following.
Go to synaptic manger.
Search for "bcmwl".
Install it. Before this you may need to enable the restricted software repository.

---

