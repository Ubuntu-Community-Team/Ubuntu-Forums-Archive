---
title: "Wifi not connecting with Ubuntu 12.04, on Thinkpad e420s"
date: 2012-12-14
forum: Networking &amp; Wireless
---

### Post by chandanjc1 on 2012-12-14
Hi,

I just upgraded my Lenovo Thinkpad e420s to Ubuntu 12.04 LTS. But the Wifi works only sometimes. It doesn't connect other times (it tries for some 2 mins and prompts for password again). I tried various solutions:

1) Installed the driver from Realtek for RTL8188CE
2) Blacklisted acer_wmi  ([http://ubuntuforums.org/showthread.php?t=1902216](http://ubuntuforums.org/showthread.php?t=1902216))
3) Tried this solution as well: [http://ubuntuforums.org/showthread.php?p=11573648#post11573648](http://ubuntuforums.org/showthread.php?p=11573648#post11573648)

But none of them fix the issue. Any suggestions? 

Thanks.

---

### Post by chili555 on 2012-12-14
I'm not quite sure why you would attempt the fix in the link you posted, clearly for Broadcom cards, if you have a Realtek. *Do* you have a Realtek? Please open a terminal and run and post:```
lspci -nn | grep 0280
```>  Blacklisted acer_wmi ([http://ubuntuforums.org/showthread.php?t=1902216](http://ubuntuforums.org/showthread.php?t=1902216))Was acer-wmi loaded and preventing a connection before you blacklisted it? It is not, as an example, on either of my two Lenovo Thinkpads.

---

### Post by chandanjc1 on 2012-12-14
Yes mine is Realtek. It looked like blacklisting the acer-wmi had fixed the issue the last time on my Thinkpad. Hence I tried the same. Here's the output of the command you asked for:
07:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176] (rev 01)

Any help appreciated. Thanks.

---

### Post by chili555 on 2012-12-14
> 1) Installed the driver from Realtek for RTL8188CEDid the compile go well? Any warnings or errors? May we see:```
modinfo rtl8192ce | grep srcversion
```Is your router set to WPA and WPA2 mixed mode? WPA2 only, not mixed mode, is preferred.

---

### Post by chandanjc1 on 2012-12-14
Yes, the install did go well. Here's the output:
srcversion:     DD4F3D83A75531AC98862F2.

The router was set to WPA. I changed it to WPA2, but still no luck.

---

### Post by chili555 on 2012-12-14
Please try, temporarily:```
sudo modprobe -r rtl8192ce
sudo modprobe rtl8192ce swenc=1
```Better, worse, the same?

---

### Post by chandanjc1 on 2012-12-15
Okay that worked :). Thanks a lot. I hope it doesn't keep getting disconnected. Will update you in sometime.

---

### Post by chili555 on 2012-12-15
If you'd like to make it persistent, please do:```
sudo gedit /etc/modprobe.d/rtl8192ce.conf
```Add a single line:```
options rtl8192ce swenc=1
```Proofread, save and close the text editor. You should be all set, but post back if we can help you further.

Please use thread tools at the top to mark Solved.

---

### Post by chandanjc1 on 2012-12-15
Unfortunately it got disconnected again after an hour or so, and the same two commands won't make it work again. Any suggestions?

---

### Post by chili555 on 2012-12-15
You might try a newer driver version from the compat-wireless suite. Please check here: [http://ubuntuforums.org/showpost.php?p=12372687&postcount=18](http://ubuntuforums.org/showpost.php?p=12372687&postcount=18)

You needn't make the change in sw.c and you will modprobe rtl8192ce, not cu.

---

