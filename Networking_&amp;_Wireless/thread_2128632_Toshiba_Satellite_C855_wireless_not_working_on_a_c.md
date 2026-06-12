---
title: "Toshiba Satellite C855 wireless not working on a clean install, Ubuntu 12.04 LTS"
date: 2013-03-23
forum: Networking &amp; Wireless
---

### Post by bruti on 2013-03-23
sudo lshw -C network

```
  *-network UNCLAIMED     
       description: Ethernet controller
       product: AR8162 Fast Ethernet
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 10
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi msix bus_master cap_list
       configuration: latency=0
       resources: memory:b8400000-b843ffff ioport:2000(size=128)
```

I cannot even detect my wireless network, which I know is running (I have other devices connected).

---

### Post by bruti on 2013-03-24
For what it's worth, I am coming from Linux Mint (cinnamon).  I had this same issue when I tried installing Ubuntu 12.10, Fedora, and even just Debian.  I eventually installed linux mint, and I could connect to the internet right off the bat.  I would prefer to use ubuntu over linux mint, however, otherwise I would stay there (considering the wireless works without issue)

---

### Post by bruti on 2013-03-26
I hate to keep bumping my own thread -- but I hate to not be able to use my laptop at school even more :)

As an update:  I cannot connect to the internet through an ethernet cable either.

---

### Post by chili555 on 2013-03-26
Your thread title refers to wireless however your details are for ethernet:> -network UNCLAIMED     
       [COLOR="#FF0000"]description: Ethernet controller[/COLOR]
       product: AR8162 Fast Ethernet
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 10
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi msix bus_master cap_list
       configuration: latency=0
       resources: memory:b8400000-b843ffff ioport:2000(size=128)Can you please run and post:```
lspci -nn | grep 0280
```

---

### Post by bruti on 2013-03-26
Hello again, chili.

I just found that command laying around on the forums so I used it in hopes that it'd help some how.

```
lspci -nn | grep 0280
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176] (rev 01)

```

I have tried downloading the RTL8188CE from my PC, then installing on the laptop.  It did not work.

---

### Post by chili555 on 2013-03-26
> Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [[COLOR="#FF0000"]10ec:8176[/COLOR]]Your device is covered by the driver rtl8192ce in 12.10. Does the module exist in 12.04? Please run and post:```
modinfo rtl8192ce | grep 8176
```

---

### Post by bruti on 2013-03-26
modinfo rtl8192ce | grep 8176
alias:          pci:v000010ECd00008176sv*sd*bc*sc*i*

---

### Post by chili555 on 2013-03-26
> **bruti said:**
> modinfo rtl8192ce | grep 8176
alias:          pci:v000010ECd00008176sv*sd*bc*sc*i*That suggests you have a working driver that claims your device. Is an interface created, ideally wlan0?```
iwconfig
```Is the switch on?```
rfkill list all
```Are there any interesting messages in the logs?```
dmesg | grep -e wlan -e rtl
```

---

### Post by bruti on 2013-03-26
```
iwconfig
lo        no wireless extensions.
```

```
rfkill list all
```
(no results)

```
dmesg | grep -e wlan -e rtl
[   10.854222] rtl8192ce: ****** This B_CUT device may not work with kernels 3.6 and earlier
[   10.854224] rtl8192ce: Using firmware rtlwifi/rtl8192cfwU_B.bin
[   11.007679] rtlwifi: Firmware rtlwifi/rtl8192cfwU_B.bin not available
```

---

### Post by chili555 on 2013-03-26
> rtlwifi/rtl8192cfwU_B.bin not availablePlease see post #20 here. You have the same problem and require the same fix.  [http://ubuntuforums.org/showthread.php?t=2123074&page=2](http://ubuntuforums.org/showthread.php?t=2123074&page=2)

---

### Post by bruti on 2013-03-26
Unfortunately, I am not getting the same results that the other posted was getting.  The first time I followed the instructions in that post, "Enable Wireless" appeared.  However, no networks were found.  I rebooted my laptop and the router as he did, but now the "Enable Wireless" option is gone again.  Redoing the steps did not yield any results (the enable wireless option doesnt even appear now)

---

### Post by chili555 on 2013-03-27
Let's follow the same diagnostic process:```
dmesg | grep rtl
lsmod | grep rtl
iwconfig
```Thanks.

---

### Post by bruti on 2013-03-27
Sure thing.

```
dmesg | grep rtl
```
```
 lsmod | grep rtl
rtl8192ce              53780  0 
rtl8192c_common        47696  1 rtl8192ce
rtlwifi                65273  1 rtl8192ce
mac80211              475488  3 rtl8192ce,rtl8192c_common,rtlwifi
cfg80211              181041  2 rtlwifi,mac80211
```
```
iwconfig
lo        no wireless extensions.
```

---

### Post by chili555 on 2013-03-27
Let's retrace the firmware step:```
ls -al /lib/firmware/rtlwifi
```Then please reboot and let me see:```
dmesg | grep rtl
```Thanks.

---

### Post by bruti on 2013-03-27
```
ls -al /lib/firmware/rtlwifi
total 456
drwxr-xr-x  2 root root   4096 Mar 26 18:53 .
drwxr-xr-x 62 root root   4096 Feb 13 17:09 ..
-rwxr-xr-x  1 root root   2115 Mar 26 18:57 Realtek-Firmware-License.txt
-rw-r--r--  1 root root  13540 Mar 26 18:57 rtl8192cfw.bin
-rwxr-xr-x  1 root root  14800 Mar 26 18:57 rtl8192cfwU_B.bin
-rwxr-xr-x  1 root root  14818 Mar 26 18:57 rtl8192cfwU.bin
-rw-r--r--  1 root root  16014 Jul 20  2012 rtl8192cufw.bin
-rwxr-xr-x  1 root root  20526 Mar 26 18:57 rtl8192defw_12.bin
-rw-r--r--  1 root root  22978 Mar 26 18:57 rtl8192defw.bin
-rw-r--r--  1 root root  80208 Mar 26 18:57 rtl8192sefw.bin
-rwxr-xr-x  1 root root  88856 Mar 26 18:57 rtl8192sefw.old.bin
-rw-r--r--  1 root root 129304 Jul 20  2012 rtl8712u.bin
-rwxr-xr-x  1 root root  22996 Mar 26 18:57 rtl8723fw_B.bin
-rwxr-xr-x  1 root root  11662 Mar 26 18:57 rtl8723fw.bin
```



```
dmesg | grep rtl
[   10.033514] rtl8192ce: ****** This B_CUT device may not work with kernels 3.6 and earlier
[   10.033516] rtl8192ce: Using firmware rtlwifi/rtl8192cfwU_B.bin
[   10.197612] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   10.197839] rtlwifi: wireless switch is on

```

I'm not exactly sure how that changed anything.. but I am currently posting from the laptop that couldn't previously connect to the internet.  What is this magic?

---

### Post by chili555 on 2013-03-27
> **bruti said:**
> [CODE]

I'm not exactly sure how that changed anything.. but I am currently posting from the laptop that couldn't previously connect to the internet.  What is this magic?I'm not sure. Perhaps it needed a little encouragement, also known as a reboot!

I'm glad it's working by whatever means. Have fun!

---

### Post by bruti on 2013-03-27
I just find it odd that it did not work after the first reboot, but it did after the second.
You've effectively troubleshooted and solved an issue for me in regards to my PC and Laptop wireless issues.

I'm beginning to think there is no wireless issue you can't solve ;)

Edit:  Marked as solved.
Thank you very much, it would have been terrible to keep going to school without wireless!

---

### Post by chili555 on 2013-03-27
> I'm beginning to think there is no wireless issue you can't solve I wish it were so. There are a few I've lost over the yaers. Thanks for your nice comments.

---

