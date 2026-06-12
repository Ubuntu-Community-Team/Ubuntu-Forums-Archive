---
title: "Belkin F7D1102 Surf Wireless Micro Usb Adapter-Ubuntu 12.04"
date: 2012-06-04
forum: Networking &amp; Wireless
---

### Post by heat33330 on 2012-06-04
I have a Belkin F7D1102 Surf Wireless Micro Usb Adapter,it shows up in Ubuntu 12.04 but my connection shows up with only one bar(My connections fast and shows up full bars on other machines) and when I'm connecting it doesn't connect but says that it is connecting.Can someone help me?

---

### Post by heat33330 on 2012-06-07
Bump!

---

### Post by heat33330 on 2012-06-26
Bump!

---

### Post by heat33330 on 2012-08-04
Bump!

---

### Post by heat33330 on 2012-08-10
Now it won't connect at all :confused: :( .

---

### Post by heat33330 on 2012-09-22
Any help?

---

### Post by lillypad on 2012-09-22
For these little things you need to use the RealTek drivers instead of ndiswrapper
You can determine your realtek driver name from using lsusb in terminal.

I got something like this:
```
Bus 001 Device 009: ID 050d:2103 Belkin Components F7D2102 802.11n N300 Micro Wireless Adapter v3000 [Realtek RTL8192CU]
```RTL8192CU is the driver name on the realtek website.

User Chili55 Posted this answer from [here]("http://ubuntuforums.org/showthread.php?t=2053044&page=2").

Hook up the ethernet and let's compile the latest from Realtek. Please open a terminal and do:

```
sudo apt-get remove --purge ndiswrapper* 
sudo apt-get install linux-headers-generic build-essential 
```Now grap the file here: [http://www.realtek.com.tw/downloads/...Downloads=true]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true") 

Download it to your desktop and right-click it and select Extract Here. Now back to the terminal:

```
cd Desktop/RTL81 
```Press the Tab key and the remiander will fill in automatically. Press Enter. 

```
sudo su 
chmod +x install.sh 
./install.sh 
modprobe -r rtl8192cu 
modprobe 8192cu 
exit 

```If it works correctly, we'll need to amend the blacklist file.

Hope that puts you guys in the right direction remember to modify these instructions for your driver and perhaps it might work.

-Lilly

---

### Post by heat33330 on 2013-01-05
> **lillypad said:**
> For these little things you need to use the RealTek drivers instead of ndiswrapper
You can determine your realtek driver name from using lsusb in terminal.
 
I got something like this:
```
Bus 001 Device 009: ID 050d:2103 Belkin Components F7D2102 802.11n N300 Micro Wireless Adapter v3000 [Realtek RTL8192CU]
```RTL8192CU is the driver name on the realtek website.
 
User Chili55 Posted this answer from [here]("http://ubuntuforums.org/showthread.php?t=2053044&page=2").
 
Hook up the ethernet and let's compile the latest from Realtek. Please open a terminal and do:
 
```
sudo apt-get remove --purge ndiswrapper* 
sudo apt-get install linux-headers-generic build-essential 
```Now grap the file here: [http://www.realtek.com.tw/downloads/...Downloads=true]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true") 
 
Download it to your desktop and right-click it and select Extract Here. Now back to the terminal:
 
```
cd Desktop/RTL81 
```Press the Tab key and the remiander will fill in automatically. Press Enter. 
 
```
sudo su 
chmod +x install.sh 
./install.sh 
modprobe -r rtl8192cu 
modprobe 8192cu 
exit 

```If it works correctly, we'll need to amend the blacklist file.
 
Hope that puts you guys in the right direction remember to modify these instructions for your driver and perhaps it might work.
 
-Lilly
 
Hi, thanks for the reply, I think it worked! What driver do I have to blacklist and how do I do it? (Sorry for the *very* late reply).
 
EDIT: It's not working now, I'm running 12.04 by the way. The driver shows up as active but not currently in use.

---

### Post by heat33330 on 2013-01-06
It connects to WiFi now but is very slow and the driver shows up as "activated but not currently in use".
 
EDIT: Not working again...

---

