---
title: "Using Intel® PRO/Wireless 3945ABG Card"
date: 2009-02-10
forum: Networking &amp; Wireless
---

### Post by tej.sarup on 2009-02-10
Hi there,

I am totally new to Linux/ Ubuntu. I have loaded Ubuntu 8.1 into my Vista machine with the 'Intel® PRO/Wireless 3945ABG' card. I have not been able to get it to work properly yet. 
I have read various threads regarding similar problems but have not been able to figure it out.:confused:

My laptop has a Wireless on/off button. On putting it on the Bluetooth comes on (detected by Ubuntu) but the wireless part of it does not, i am not even able to see the wireless networks in the area...

Please help out!! 

Thanks in advance

---

### Post by pdtpatrick on 2009-02-10
when you say you loaded it into ubuntu -- does that mean you installed it via vmware? if so then wireless won't come up. 

However if you dual booting then check out the ubuntu community documentation for wireless information on the intel 3945.

meanwhile please run the following and output it

sudo lshw | grep -i intel

dmesg | grep -i intel 

and post those in the forum

---

