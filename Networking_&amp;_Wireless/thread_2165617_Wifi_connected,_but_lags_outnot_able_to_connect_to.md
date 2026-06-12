---
title: "Wifi connected, but lags out/not able to connect to anything."
date: 2013-08-05
forum: Networking &amp; Wireless
---

### Post by Teethdude on 2013-08-05
After connecting to any wireless hotspot, I can browse the internet for awhile and Boom! It lags out. The whole time it claims it is conected and working, but nothing loads. Websites, router, LAN, Samba shares, can't connect to anything.&nbsp;<br><br>Here is some info:<br>HP Pavilion g6 series<br>CPU:&nbsp;Intel® Pentium(R) CPU B950 @ 2.10GHz × 2&nbsp;<br>GPU:&nbsp;Intel® Sandybridge Mobile&nbsp;<br>Wireless: (according to ```
sudo lshw -C network
```)<br><div>```
 &nbsp;*-network &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&nbsp;</div><div>&nbsp; &nbsp; &nbsp; &nbsp;description: Wireless interface</div><div>&nbsp; &nbsp; &nbsp; &nbsp;product: RTL8188CE 802.11b/g/n WiFi Adapter</div><div>&nbsp; &nbsp; &nbsp; &nbsp;vendor: Realtek Semiconductor Co., Ltd.</div><div>&nbsp; &nbsp; &nbsp; &nbsp;physical id: 0</div><div>&nbsp; &nbsp; &nbsp; &nbsp;bus info: pci@0000:01:00.0</div><div>&nbsp; &nbsp; &nbsp; &nbsp;logical name: wlan3</div><div>&nbsp; &nbsp; &nbsp; &nbsp;version: 01</div><div>&nbsp; &nbsp; &nbsp; &nbsp;serial: ac:81:12:ba:c3:2f</div><div>&nbsp; &nbsp; &nbsp; &nbsp;width: 64 bits</div><div>&nbsp; &nbsp; &nbsp; &nbsp;clock: 33MHz</div><div>&nbsp; &nbsp; &nbsp; &nbsp;capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless</div><div>&nbsp; &nbsp; &nbsp; &nbsp;configuration: broadcast=yes driver=rtl8192ce driverversion=3.8.0-27-generic firmware=N/A ip=192.168.1.105 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn</div><div>&nbsp; &nbsp; &nbsp; &nbsp;resources: irq:16 ioport:4000(size=256) memory:c2500000-c2503fff</div><div>
```<br>So I really don't know what to think of it. read some other post, but they were all for lower Ubuntu versions (11.04 on average) and didn't seem to help.<br>Thanks in advanced for your help.</div>&nbsp;

---

### Post by praseodym on 2013-08-05
Try the driver version 0012.0207.2013 from Realtek 
```

sudo apt-get install --reinstall build-essential linux-headers-$(uname -r) linux-headers-generic
wget media.cdn.ubuntu-de.org/forum/attachments/39/19/5443987-rtl_92ce_92se_92de_8723ae_88ee_0012.0207.2013.tar.gz
tar xvf 5443987-rtl_92ce_92se_92de_8723ae_88ee_0012.0207.2013.tar.gz
cd rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013 
make
sudo make install
sudo depmod -a
sudo update-initramfs -u
sudo cp -r firmware/* /lib/firmware  
```
Reboot.

---

