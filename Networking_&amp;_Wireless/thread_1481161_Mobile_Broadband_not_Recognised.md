---
title: "Mobile Broadband not Recognised"
date: 2010-05-12
forum: Networking &amp; Wireless
---

### Post by beetleman64 on 2010-05-12
I recently made a clean install of Ubuntu 10.04 and my mobile broadband no longer works. When I plug it in, the set-up wizard does not appear, and even when I run the wizard manually, the modem is not recognised. I know the modem works as when the laptop ran 9.10 it all worked perfectly.

For the record, it is a Huawei E1550 and has  3 Mobile Broadband Pay-as-you-go.

---

### Post by damnbiker on 2010-05-12
Is it showing up as an auto ethernet connection (eth0 or eth1)?  I am having the same problem with my HTC maple, I have been able to configure a mobile broadband connection manually but when i plug in my phone it isn't recognized as a mobile broadband connection.

---

### Post by alexfish on 2010-05-12
> **beetleman64 said:**
> I recently made a clean install of Ubuntu 10.04 and my mobile broadband no longer works. When I plug it in, the set-up wizard does not appear, and even when I run the wizard manually, the modem is not recognised. I know the modem works as when the laptop ran 9.10 it all worked perfectly.

For the record, it is a Huawei E1550 and has  3 Mobile Broadband Pay-as-you-go.

hi 

with the modem connected , try these commands from the terminal and post the results

code:

dmesg | grep -e "modem" -e "tty"

this will list the modem the ports only

code:

lsusb

for the device listing 


from the system menus / disc utility can you post a screen shot of what it shows ,{grab the current window}

thanks in advance 

alexfish

---

### Post by beetleman64 on 2010-05-20
output:

[    0.000000] console [tty0] enabled

---

### Post by alexfish on 2010-05-20
removed

---

### Post by alexfish on 2010-05-20
hi

still need the results of, from the terminal , ensure the device is connected

code:

lsusb

for the device listing

also 

from the  system menus / disc utility can you post a screen shot of what it shows  ,{grab the current window}

thanks in advance

alexfish

---

