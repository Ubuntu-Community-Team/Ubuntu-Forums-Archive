---
title: "help about TP-Link TL-WN721N  ath9k_htc"
date: 2010-06-15
forum: Networking &amp; Wireless
---

### Post by yoyu007 on 2010-06-15
I have TP-Link TL-WN721N usb wifi netcard,thd dirver should be ath9k_htc

[http://wireless.kernel.org/en/users/Drivers/ath9k_htc](http://wireless.kernel.org/en/users/Drivers/ath9k_htc)

and my system is Linux version 2.6.35-2-generic (buildd@yellow) (gcc version 4.4.4 (Ubuntu 4.4.4-4ubuntu1) ) #3-Ubuntu SMP Thu Jun 10 03:23:06

my kernel config enabled ath9k_htc:
CONFIG_ATH_COMMON=m
CONFIG_ATH9K_HW=m
CONFIG_ATH9K_COMMON=m
CONFIG_ATH9K_HTC=

and i downlad AR9271 - ar9271.fw,place ar9271.fw in /lib/firmware.


but the system cant regconize the netcard,i just find jocky log:

DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ath9k_htc', 'jockey_handler': 'KernelModuleHandler'}


pls tell me what should I do?

thank you,and sorry for my bad English

---

### Post by Peter09 on 2010-06-15
Here is a link thats suggests a solution
 
[http://leonardom.wordpress.com/2010/05/24/install-wireless-usb-adapter-tl-wn721n-driver-on-ubuntu-10-4/](http://leonardom.wordpress.com/2010/05/24/install-wireless-usb-adapter-tl-wn721n-driver-on-ubuntu-10-4/)

---

### Post by yoyu007 on 2010-06-16
thank you very much,I will try

---

### Post by Bucky Ball on 2010-06-16
Have you plugged in an ethernet cable and gotten your updates? TP-Link should work after doing that. Should detect the card.

Also, after doing that, check System->Administration->Hardware Drivers. Anything in there disabled?

---

### Post by yoyu007 on 2010-06-23
thanks for all your reply

It is my wrong,i downloaded the bad ar9271.fw file.

I found sometime i got the file about 4k,and sometime is 48.1k,and sometime is 50k

and the 50k file is right

thanks for all

---

### Post by setan666 on 2010-07-10
> **yoyu007 said:**
> thanks for all your reply

It is my wrong,i downloaded the bad ar9271.fw file.

I found sometime i got the file about 4k,and sometime is 48.1k,and sometime is 50k

and the 50k file is right

thanks for allwhere you get the 50k file ? I only got the 48.1k file

---

### Post by samarthmath on 2013-02-11
the 50.1 kb file is there by the name of htc_9721.fw

[http://wireless.kernel.org/download/htc_fw/1.3/]("http://wireless.kernel.org/download/htc_fw/1.3/")

---

### Post by Bucky Ball on 2013-02-11
[B][I]Thread Closed

Reason:[/I][/B] Necromancy. Old thread put to bed. For any contempory issues please post a new thread.

---

