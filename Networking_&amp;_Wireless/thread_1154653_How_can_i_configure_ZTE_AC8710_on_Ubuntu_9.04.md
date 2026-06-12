---
title: "How can i configure ZTE AC8710 on Ubuntu 9.04"
date: 2009-05-10
forum: Networking &amp; Wireless
---

### Post by CoolApputty on 2009-05-10
hi ,

Can anyone tell me how to configure ZTE AC8710 Wireless USB modem on Ubuntu 9.04.
I would like the system to detect the modem automatically. I am now using Windows for browsing/ internet as i dont have another connection i am not able to connect to internet from Linux...
(Iam new to Linux so am not even aware of the things which many might think as basic)

PLZZ help.

---

### Post by shivathreya on 2009-07-16
Do you still need help? Contact me.

Shiva

---

### Post by Gotfreek on 2009-07-22
> **shivathreya said:**
> Do you still need help? Contact me.

Shiva

Hello. I have same problem, please help.

Best regards.

---

### Post by Gotfreek on 2009-07-22
I've corrected /boot/grub/menu.lst 

title      Ubuntu 9.04, kernel 2.6.28-11-generic[COLOR=green] custom[/COLOR]
uuid      ed10446b-cb31-473d-8e97-1224c179e150
kernel      /boot/vmlinuz-2.6.28-11-generic root=UUID=ed10446b-cb31-473d-8e97-1224c179e150 ro quiet splash [COLOR=green]usbserial.vendor=0x19d2 usbserial.product=0xffff[/COLOR]
initrd      /boot/initrd.img-2.6.28-11-generic
quiet 

But it isn't working properly

---

### Post by jyothishsv@rediffmail.com on 2009-07-25
I'm a new ubuntu user. From what i could understand till now, the value of usbserial.product should be detected as 0xfff1 for the device to be recognized as a modem. (usbserial.product=0xfff1)

You can use usb_modeswitch to do that.

For the setup of zte ac8710 using Reliance netconnect broadband, i found the following link useful:

[http://outbackwifi.blogspot.com/2009/06/howto-connect-to-internet-using-zte-ac.html](http://outbackwifi.blogspot.com/2009/06/howto-connect-to-internet-using-zte-ac.html)

Thanks

---

