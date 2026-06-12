---
title: "WiFi Broken After Update"
date: 2012-07-27
forum: Networking &amp; Wireless
---

### Post by waltkerr on 2012-07-27
I use an Edimax 7811 WiFi dongle in the USB port of my laptop. Running 12.04 LTS. It was running fine until an Ubuntu update last night. Now the WiFi dongle won't power up. The same dongle runs fine in WinXP (dual boot). I reinstalled the driver but no change. Not sure how to proceed. Thanks for your help!

Here's lsusb:

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 7392:7811 Edimax Technology Co., Ltd EW-7811Un 802.11n Wireless Adapter [Realtek RTL8188CUS]

---

### Post by Finnicella on 2012-07-28
try to see if there are some blocks with
```
sudo rfkill list all
```
if you find some of them give this command
```
sudo rfkill unblock all
```
let me know how it works.
Bye

---

### Post by waltkerr on 2012-07-28
The list command comes back to the prompt with nothing listed. The USB ports work fine with other devices (thumb drives). The wifi dongle never powers up as usual when booting Ubuntu. Toggling the laptop wifi on/off switch makes no difference.

---

### Post by waltkerr on 2012-08-04
Today I restarted my laptop with the original 12.04 live CD and the Edimax wifi dongle powered up and worked! So, I went ahead and reinstalled 12.04, replacing the existing 12.04. The wifi dongle worked for a while then would timeout. Removing and reinsterting it would wake it up and it would work for about 5 minutes then go out again. I then downloaded the RealTek drivers from their site and re-installed the driver by running "install.sh". At this point, the wifi has stayed working longer than before. We'll see how it goes. I have not added the RTL8188CU driver to my modules file, nor have I blacklisted the built-in RealTek driver as I read in a post that 12.04 didn't need this. Thanks for you help. Hopefully it is fixed.

---

### Post by Finnicella on 2012-08-05
> **waltkerr said:**
> Today I restarted my laptop with the original 12.04 live CD and the Edimax wifi dongle powered up and worked! So, I went ahead and reinstalled 12.04, replacing the existing 12.04. The wifi dongle worked for a while then would timeout. Removing and reinsterting it would wake it up and it would work for about 5 minutes then go out again. I then downloaded the RealTek drivers from their site and re-installed the driver by running "install.sh". At this point, the wifi has stayed working longer than before. We'll see how it goes. I have not added the RTL8188CU driver to my modules file, nor have I blacklisted the built-in RealTek driver as I read in a post that 12.04 didn't need this. Thanks for you help. Hopefully it is fixed.

I hope too. Bye

---

### Post by waltkerr on 2012-08-10
After my previous reply, my WiFi still was not working properly. It would sometimes work fine for a few minutes then would start prompting me for my network passkey every few minutes and finally would disconnect completely. All this time is was running fine under WinXP (dual boot laptop).

I bumped into "NDISWrapper The Ultimate Guide" (excerpts are posted online) in one of the Ubuntu forums and read it carefully. I noticed I had not blacklisted the kernel driver for my wifi adapter correctly. In my blacklist.conf file I had added a line:
```

rtl8192cu
```

The line should have read:
```

blacklist rtl8192cu
```

Then I installed the newer driver which was functioning fine in WinXP:
```

sudo ndiswrapper -i net8192su.inf
```

Lastly, I edited /etc/modules to run ndiswrapper at bootup. 

I rebooted and my Edimax (Realtek drivers) USB Wifi adapter has been running fine ever since.

Thanks folks for your help.
:)

---

