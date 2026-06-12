---
title: "Huawei EC1262 Strange problem."
date: 2010-09-07
forum: Networking &amp; Wireless
---

### Post by harbhag on 2010-09-07
Hi everyone, I am having Reliance Netconnect Braodband+ connection and it uses Huawei EC1262 modem to connect. The problem is that sometimes it gets identified correctly and my internet works but sometimes it doesnot. 
I have already installed wvdial, usb-modeswitch and usb-modeswitch-data according to the tutorial at the link below 
[http://community.linuxmint.com/tutorial/view/97](http://community.linuxmint.com/tutorial/view/97)

My internet works if the output of **lsusb** is as below 
```
Bus 002 Device 007: ID 413c:8160 Dell Computer Corp. 
Bus 002 Device 006: ID 413c:8162 Dell Computer Corp. 
Bus 002 Device 005: ID 413c:8161 Dell Computer Corp. 
Bus 002 Device 004: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 002 Device 003: ID 12d1:140b Huawei Technologies Co., Ltd. 
Bus 002 Device 002: ID 8087:0020  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 0c45:6461 Microdia 
Bus 001 Device 002: ID 8087:0020  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

But it does not work if the output of **lsusb** is as below
```
Bus 002 Device 007: ID 413c:8160 Dell Computer Corp. 
Bus 002 Device 006: ID 413c:8162 Dell Computer Corp. 
Bus 002 Device 005: ID 413c:8161 Dell Computer Corp. 
Bus 002 Device 004: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 002 Device 003: ID 12d1:1446 Huawei Technologies Co., Ltd. 
Bus 002 Device 002: ID 8087:0020  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 0c45:6461 Microdia 
Bus 001 Device 002: ID 8087:0020  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

I think my modem is not getting switched correctly by [B]usb-modeswitch
[/B].

If more information is required from my side then please tell me.
I would highly appreciate any help.
Thanks

P.S: I am using Dell Inspiron N5010 Laptop and OS is Ubuntu 10.04.1 64bit.

---

### Post by wesleybailey on 2010-09-07
I had to whip out [MELD]("http://meld.sourceforge.net/")(a great program that compares files and documents) to spot the difference between the two outputs.

Output 1 - Working
Bus 002 Device 003: ID 12d1:**140b** Huawei Technologies Co., Ltd. 

Output 2 - Not Working
Bus 002 Device 003: ID 12d1:**1446** Huawei Technologies Co., Ltd. 

I took a look at the tutorial you followed and noticed something interesting in the /etc/usb_modeswitch.conf.


```
# Huawei, newer modems

DefaultVendor= 0x12d1

DefaultProduct=0x1446

TargetVendor= 0x12d1

TargetProduct=140b

```

I'm just using logic, but if it were me I would edit change the 
```
# Huawei, newer modems

DefaultVendor= 0x12d1

DefaultProduct=**0x140b**

TargetVendor= 0x12d1

TargetProduct=140b

```

Latest Tutorial: [How Do I Open a .uif file in Linux? ]("http://wesleybailey.com/articles/uif-to-iso-converter")

---

### Post by harbhag on 2010-09-07
I have changed the file as you said , but still its not working properly. I think its something have to do with the usb-modeswitch as its to getting switched properly.

---

### Post by harbhag on 2010-09-09
Somebody please help, its very urgent.

---

### Post by harbhag on 2010-09-14
Well now my problem is solved. Here is the solution.
Remove usb-modeswitch and usb-modeswitch-data using apt-get.
Then download the source for the both from the official website and install according to the instructions given on the website and reboot.
If anyone have problem installing then ask me for help in this thread or email at [email]harbhag[dot]sohal[at]gmail[dot]com[/email]

---

### Post by harbhag on 2010-09-15
I have also posted the solution on my blog, you can visit the link below for the solution.
[http://harbhag.wordpress.com/2010/09/14/reliance-netconnect-broadband-on-ubuntu/](http://harbhag.wordpress.com/2010/09/14/reliance-netconnect-broadband-on-ubuntu/)

---

