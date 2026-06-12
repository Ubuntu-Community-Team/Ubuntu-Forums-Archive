---
title: "Latest Ubuntu Netbook on Eee PC - various problems"
date: 2011-03-30
forum: Networking &amp; Wireless
---

### Post by u_b_u_n_t_u on 2011-03-30
Hi

I have 2 major problems which I hope you can help me with.

Firstly, I have setup my mobile Huawei  E220 HSDPA Modem / E270 HSDPA/HSUPA Modem with the wizard, which made it very easy.

However, the Modem is mostly not recognized when inserted into the USB. I simply can not see it the network connection overview. Occasionally it works and I am sometimes asked to provide the PIN although I have typed it in the settings for Mobile Broadband via Network Manager.

If I do a lsusb I see:

Bus 003 Device 005: ID 12d1:1003 Huawei Technologies Co., Ltd. E220 HSDPA Modem / E270 HSDPA/HSUPA Modem

... annd I do not see the modem in the file management as an usb storage.

usb-modeswitch is installed

Any suggestions as to  what to do?

The other problem I'm facing is with bluetooth. I have paired my headset to use it with A2DP to hear music. The first time I do the pairing all is working fine,  but in reboot and when selecting the headset (saved when paired) it is not possible to connect to the headset. If deleting the headset  entry and doing the pairing again it is working again.

UPDATE: Now working

After reading this [http://ubuntuforums.org/showthread.php?t=1605484](http://ubuntuforums.org/showthread.php?t=1605484) I changed  /etc/usb_modeswitch.conf and added:

DefaultVendor=0x12d1
DefaultProduct=0x1003
HuaweiMode=1

That is it! Now I can see the modem and behaves as it should

---

