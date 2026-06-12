---
title: "Huawei E156g"
date: 2009-05-19
forum: Networking &amp; Wireless
---

### Post by Meads on 2009-05-19
Any ideas how i can get the huawei e156g modem working in ubuntu 7.10?

I have tried using wvdial and followed the instructions but i get some sort of error about /dev/ttyusb0 not existing.

---

### Post by GeorgeVita on 2009-05-21
Hi **Meads**,
if you insist to manage the connection with the old 7.10 post here some test results.

Boot without the modem, wait for the system to stabilize, attach the modem, wait 20 seconds, open a terminal window and try:

[B]dmesg
lsusb
ls /dev/ttyU* /dev/ttyA*[/B]

Post here the last 10-15 lines of dmesg (concerning /dev/tty... and usbserial or option driver).
Post the output of the other two commands.
Post all your /etc/wvdial.conf

The **dmesg** command will show all system activity after inserting the modem, **lsusb** will show all USB peripherals attached and their vendor/product IDs and **ls /dev/tty...** will list any configured serial communication ports.

Regards,
George

---

### Post by Meads on 2009-05-23
> **GeorgeVita said:**
> Hi **Meads**,
if you insist to manage the connection with the old 7.10 post here some test results.

Boot without the modem, wait for the system to stabilize, attach the modem, wait 20 seconds, open a terminal window and try:

[B]dmesg
lsusb
ls /dev/ttyU* /dev/ttyA*[/B]

Post here the last 10-15 lines of dmesg (concerning /dev/tty... and usbserial or option driver).
Post the output of the other two commands.
Post all your /etc/wvdial.conf

The **dmesg** command will show all system activity after inserting the modem, **lsusb** will show all USB peripherals attached and their vendor/product IDs and **ls /dev/tty...** will list any configured serial communication ports.

Regards,
George

Thank you for taking the time to help me, i was using the old 7.10 version of ubuntu due to having it on cd already and not being able to download the latest version because i am on mobile broadband and it would of just ate a way at my monthly allowance.

I found a site were i can buy Linux ditrobutions on cd for £2 which is what i did and it was plain sailing once installed i was prompted to choose my network and away i went. 

I am posting from ubuntu 9.04 using my E156G modem.

Thanks.

---

