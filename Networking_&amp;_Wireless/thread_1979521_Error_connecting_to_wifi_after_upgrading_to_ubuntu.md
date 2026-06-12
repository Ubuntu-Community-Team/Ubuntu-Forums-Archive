---
title: "Error connecting to wifi after upgrading to ubuntu 12.04"
date: 2012-05-13
forum: Networking &amp; Wireless
---

### Post by Bobi86 on 2012-05-13
I have recently upgraded to ubuntu 12.04 from 10.04 in my lenovo laptop. I face the below issue  after upgrade.
I was unable to connect to the wifi i.e: there is no wireless network detector showing up.
i have reinstalled the Broadcom STA wireless driver available in the  systems tools -> additional drivers. But even then it doesn't work.

Thanks in advance.
Regards,
Balaji

---

### Post by Bobi86 on 2012-05-13
hi all...
Try this.. This fixed my issue.

sudo apt-get install linux-firmware-nonfree sudo modprobe -r b43 sudo modprobe b43

---

### Post by Bobi86 on 2012-05-20
hi all,
      i need to run this command "sudo modprobe b43" every time i login to the computer for the computer to show the presence of wireless adapter in the network manager. 
some kindly help me fix this. i do not want to run this command again and again when i login to my system.
Thanks in advance.

Regards,
Balaji R.

---

### Post by wildmanne39 on 2012-05-20
Hi, please do:
```
sudo su 
echo b43 >> /etc/modules 
exit
```
Reboot.
Thanks

---

### Post by Bobi86 on 2012-06-16
Hi.. Thanks it worked. 

but the wifi connection password is being prompted everytime now. is there any way to make the password remembered? so dat i don need to give the password manually every time i login?

Thanks in advance.

---

### Post by wildmanne39 on 2012-06-16
If you set your system to login automatically it will do that for security and we are not suppose to tell people how to change that because it makes your system vulnerable.
Thanks

---

