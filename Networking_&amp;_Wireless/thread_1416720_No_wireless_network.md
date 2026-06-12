---
title: "No wireless network"
date: 2010-02-26
forum: Networking &amp; Wireless
---

### Post by Sutieday on 2010-02-26
Today I just installed ubuntu 9.10 and completely reformated my dell laptop. After that my computer was cleared and I can't use my built in wireless card. Now I have to just connect my laptop with a wire to access the internet. Is there any wireless network cards that I can buy, (like on amazon.com) that will allow me to go wireless?
 
Please I really need help!

---

### Post by chili555 on 2010-02-26
> Is there any wireless network cards that I can buy, (like on amazon.com)That wouldn't be very fun. Why don't we fix up the card you have? First, let's learn what kind of card it is. Please open Applications -> Accessories -> Terminal and do:```
lspci -nn
```Post the result, or just the wireless part, if you can tell, and we'll have a good idea of how to proceed.

---

### Post by Sutieday on 2010-02-26
I have 2 network cards:

 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)

Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)

Ubuntu 9.10 tells me that the wireless card is disabled, but I am not sure how to enable it since I don't have a windows partion.

---

### Post by chili555 on 2010-02-26
Is there any option to activate Hardware Drivers in System -> Administration -> Hardware Drivers?

---

### Post by Sutieday on 2010-02-26
There was an option to activate the wireless driver, I did it but there was no change. Also I have a Brodcom B43 wireless driver that I think is the problem to why I can't get s wireless connection.

---

### Post by chili555 on 2010-02-26
Are you connected to the internet by ethernet? In order to download certain files when you activate, you may need to be connected.

---

### Post by Sutieday on 2010-02-26
Yes, I am using an ethernet cable to keep my laptop connected to the internet.

---

### Post by chili555 on 2010-02-26
Please open the terminal again and do:```
sudo apt-get install b43-fwcutter
```You will be asked to automatically fetch and install the firmware into the right location.

Detach the ethernet cable and reboot. Then click the Network Manager icon and see if your wireless is working.

---

### Post by Sutieday on 2010-02-26
No, That didn't happen to me. I wasn't alerted about a firmware upgrade. I think I might have to manually install the firmware. Do you know what is the problem?

P.S. The wireless network card is on, but I think Ubuntu is not using it.

---

### Post by chili555 on 2010-02-26
Let's try a bit harder. Please do:```
wget http://downloads.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2
tar xjf broadcom-wl-4.150.10.5.tar.bz2
cd broadcom-wl-4.150.10.5/driver
b43-fwcutter -w /lib/firmware/ wl_apsta_mimo.o
```Now, detach the ethernet cable and do:```
sudo rmmod -f b43 ssb
sudo modprobe b43 ssb
```*Now* does your wirless work?

---

### Post by Sutieday on 2010-02-26
Ok, I am new to ubuntu so i don't know how to open the 
[http://downloads.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2](http://downloads.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2)

---

### Post by Sutieday on 2010-02-26
> **Sutieday said:**
> Ok, I am new to ubuntu so i don't know how to open the 
[http://downloads.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2](http://downloads.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2)

So I opened the terminal and put in the code and I get this message: This file is recognised as:
  ID         :  FW13
  filename   :  wl_apsta_mimo.o
  version    :  410.2160
  MD5        :  cb8d70972b885b1f8883b943c0261a3c
Extracting b43/pcm5.fw
failed to open file: Permission denied

---

### Post by chili555 on 2010-02-26
You just have to copy and paste the commands I gave you into the terminal. wget goes out on the internet and grabs the required file, tar unpacks it, etc., etc.

---

### Post by Sutieday on 2010-02-26
> **chili555 said:**
> You just have to copy and paste the commands I gave you into the terminal. wget goes out on the internet and grabs the required file, tar unpacks it, etc., etc.

I did that but it says: This file is recognised as:
  ID         :  FW13
  filename   :  wl_apsta_mimo.o
  version    :  410.2160
  MD5        :  cb8d70972b885b1f8883b943c0261a3c
Extracting b43/pcm5.fw
failed to open file: Permission denied

I think I am denied from making changes. Even though I am the admin.

---

### Post by chili555 on 2010-02-26
May I assume this is the step that wouldn't run?```
b43-fwcutter -w /lib/firmware/ wl_apsta_mimo.o
```Please try:```
sudo b43-fwcutter -w /lib/firmware/ wl_apsta_mimo.o
```

---

### Post by Sutieday on 2010-02-26
> **chili555 said:**
> May I assume this is the step that wouldn't run?```
b43-fwcutter -w /lib/firmware/ wl_apsta_mimo.o
```Please try:```
sudo b43-fwcutter -w /lib/firmware/ wl_apsta_mimo.o
```

They new code works but when I put in this code: 
sudo rmmod -f b43 ssb
sudo modprobe b43 ssb 

Then I get this error: ERROR: Removing 'ssb': Resource temporarily unavailable

---

### Post by chili555 on 2010-02-26
I believe your ethernet card also uses the module *ssb*. Since your ethernet is in use, *ssb* doesn't want to let go. The simple fix is to detach the ethernet cable and reboot. Now does your wireless work? Have we saved a trip to Amazon?

---

### Post by Sutieday on 2010-02-26
> **chili555 said:**
> I believe your ethernet card also uses the module *ssb*. Since your ethernet is in use, *ssb* doesn't want to let go. The simple fix is to detach the ethernet cable and reboot. Now does your wireless work? Have we saved a trip to Amazon?

Nope, I still get the error message even though I unplugged my ethernet cable. When I press enter to the error message I get this: 
FATAL: Error inserting b43 (/lib/modules/2.6.31-19-generic/kernel/drivers/net/wireless/b43/b43.ko): Unknown symbol in module, or unknown parameter (see dmesg)

When I right click the network icon on the panel, I see that the wireless network option is unchecked and I am not able to check it.

---

### Post by chili555 on 2010-02-26
Please do:```
dmesg | grep -e ssb -e b43
```Post the result.

---

### Post by Sutieday on 2010-02-26
[    1.461606] b43-pci-bridge 0000:02:03.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.614389] ssb: Sonics Silicon Backplane found on PCI device 0000:02:03.0
[    2.576378] ssb: Sonics Silicon Backplane found on PCI device 0000:02:00.0
[   19.404975] b43-phy0: Broadcom 4318 WLAN found (core revision 9)
[   20.109160] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[   20.230266] b43 ssb0:0: firmware: requesting b43/pcm5.fw
[   20.255889] b43 ssb0:0: firmware: requesting b43/b0g0initvals5.fw
[   20.298641] b43 ssb0:0: firmware: requesting b43/b0g0bsinitvals5.fw
[   20.784616] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[   20.900770] Registered led device: b43-phy0::tx
[   20.900795] Registered led device: b43-phy0::rx
[   20.900819] Registered led device: b43-phy0::radio
[   20.938532] b43-phy0: Radio hardware status changed to DISABLED
[  294.519307] b43: Unknown parameter `ssb'
[  318.436865] b43: Unknown parameter `ssb'
[  328.302999] b43: Unknown parameter `ssb'

---

### Post by chili555 on 2010-02-26
Please open System -> Admin -> Synaptic and search for ndiswrapper and for bcmwl-kernel-source. If they are installed mark both for complete removal, including configuration files. Also, please post:```
ls /etc/modprobe.d | grep bcm
```We will get this monster tamed!

---

### Post by Sutieday on 2010-02-26
> **chili555 said:**
> Please open System -> Admin -> Synaptic and search for ndiswrapper and for bcmwl-kernel-source. If they are installed mark both for complete removal, including configuration files. Also, please post:```
ls /etc/modprobe.d | grep bcm
```We will get this monster tamed!

The code you just gave me is not working, I removed the programs though.

---

### Post by chili555 on 2010-02-26
> The code you just gave me is not workingGood! That means that what I was hoping was either not there or removed in Synaptic, is not there. Please reboot and give us a good report.

---

### Post by Sutieday on 2010-02-26
No, I didn't work. I don't know why ubuntu can not detect my wireless card.

---

### Post by chili555 on 2010-02-26
Let's try again:```
sudo modprobe b43 ssb
dmesg | grep -e b43 -e ssb
```Thanks.

---

### Post by Sutieday on 2010-02-26
Now I got: 
[    1.478729] b43-pci-bridge 0000:02:03.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.593403] ssb: Sonics Silicon Backplane found on PCI device 0000:02:03.0
[    2.564496] ssb: Sonics Silicon Backplane found on PCI device 0000:02:00.0
[   18.953010] b43-phy0: Broadcom 4318 WLAN found (core revision 9)
[   19.768059] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[   19.851117] b43 ssb0:0: firmware: requesting b43/pcm5.fw
[   19.893345] b43 ssb0:0: firmware: requesting b43/b0g0initvals5.fw
[   19.950474] b43 ssb0:0: firmware: requesting b43/b0g0bsinitvals5.fw
[   20.424144] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[   20.524706] Registered led device: b43-phy0::tx
[   20.524730] Registered led device: b43-phy0::rx
[   20.524754] Registered led device: b43-phy0::radio
[   20.524803] b43-phy0: Radio hardware status changed to DISABLED
[   20.525025] b43-phy0: Radio turned on by software
[   20.525029] b43-phy0: The hardware RF-kill button still turns the radio physically off. Press the button to turn it on.

How do I turn the thing on?

---

### Post by chili555 on 2010-02-26
Please try:```
sudo rmmod -f dell-laptop
```Any change in the wireless?

---

### Post by Sutieday on 2010-02-26
No change. But I get an error saying: ERROR: Removing 'dell_laptop': No such file or directory

---

### Post by chili555 on 2010-02-26
What make and model of Dell is it? Also, may I see:```
lsmod | grep dell
```Thanks.

---

### Post by Sutieday on 2010-02-26
> **chili555 said:**
> What make and model of Dell is it? Also, may I see:```
lsmod | grep dell
```Thanks.

Is is a Dell Inspiron B130 


dell_wmi                2564  0

---

### Post by chili555 on 2010-02-26
Does Fn+F2 change it?> The hardware RF-kill button still turns the radio physically off. Press the button to turn it on.You might also try:```
sudo rfkill unblock all
```Rerun:```
dmesg | grep b43
```See if there is any new activity after 20.525029.

Also, please do:```
sudo iwconfig wlan0 txpower auto
rfkill list
```Any good news?

I will have to see you tomorrow. Good luck!

---

### Post by Sutieday on 2010-02-26
Thank you soo much. It finally worked. The Fn+F2 helped. Thank you for all of you help and support!

---

### Post by alwalker1 on 2010-02-27
I have IBM Thinkpad t42 2373 and I installed unbuntu on the laptop. The wireless system did not come up. I'm new to linux and have no idea how to get it working. Is there some place where I can get help with the instalation  of my laptop software.

---

### Post by chili555 on 2010-02-27
> **alwalker1 said:**
> I have IBM Thinkpad t42 2373 and I installed unbuntu on the laptop. The wireless system did not come up. I'm new to linux and have no idea how to get it working. Is there some place where I can get help with the instalation  of my laptop software.Please start a new thread and we'll be happy to help.

I love my Thinkpads!

---

