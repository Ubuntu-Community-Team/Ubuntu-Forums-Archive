---
title: "WPA Issue - connecting OK but no internet"
date: 2012-10-28
forum: Networking &amp; Wireless
---

### Post by aigljd on 2012-10-28
Hi guys,

I'm new to the amazing world of ubuntu and I have yet to solve some issues to get my OS fully working ! 

I can connect to WPA networks (especially my university one) but thereafter I cannot access the internet and my web browser just send me to an error page stating I'm not connected to the web.

I'm on Ubuntu 12.10 w/ Gnome environment.

Do you guys have any idea of how I could configure my WPA network access ?

Thanks a lot !

---

### Post by chili555 on 2012-10-28
Is it a WPA issue or, more likely, a wireless driver issue, chili asks rhetorically. Please open a terminal and run and post:```
lspci -nn | grep 0280
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

---

### Post by aigljd on 2012-10-28
01:00.0 Network controller [0280]: Intel Corporation Centrino Advanced-N 6235 [8086:088e] (rev 24)

Here's what I get !

---

### Post by chili555 on 2012-10-28
Please try an experiment:```
sudo modprobe -r iwlwifi
sudo modprobe iwlwifi 11n_disable=1
```If it helps, we can write one quick file and make it persistent.

---

### Post by aigljd on 2012-10-30
This code seems to work ! 

Thanks ;)

---

### Post by chili555 on 2012-10-30
I expect you'd like to make it permanent so you don't have to begin each day entering terminal commands. Please do:```
sudo gedit /etc/modprobe.d/iwlwifi.conf
```Add a single line:```
options iwlwifi 11n_disable=1
```Proofread, save and close gedit. You should be all set.

Please use thread tools at the top to mark Solved. The searchers will appreciate it.

---

### Post by aigljd on 2012-10-30
Ok thanks !

---

### Post by KegHead on 2012-11-15
> **chili555 said:**
> I expect you'd like to make it permanent so you don't have to begin each day entering terminal commands. Please do:```
sudo gedit /etc/modprobe.d/iwlwifi.conf
```Add a single line:```
options iwlwifi 11n_disable=1
```Proofread, save and close gedit. You should be all set.

Please use thread tools at the top to mark Solved. The searchers will appreciate it.

Hi chili555!

I need help setting up wpa/wep.

Do you know of a great guide for wifi newbies?

Thanks!

KegHead

---

### Post by chili555 on 2012-11-15
> **KegHead said:**
> Hi chili555!

I need help setting up wpa/wep.

Do you know of a great guide for wifi newbies?

Thanks!

KegHeadNo, I don't. However, if you'd like to start a new thread and tell us more about what you're trying to do, we'll be glad to help.

---

### Post by Sauli on 2012-12-27
The suggested commands 
> sudo modprobe -r iwlwifi
sudo modprobe iwlwifi 11n_disable=1
solved my problem too. 

My problem started quite unexpectedly after changing the WPA password on my Acer laptop. With Ubuntu 12.10. the laptop connected to the WLAN access point but no traffic was delivered, not even pings did get through. After booting in Windows Vista everything worked fine, so it was obvious that it was a Ubuntu problem.
Before this I had never had issues with the WLAN with 12.10 or with any earlier version.

Thanks for help.

---

### Post by INe35 on 2013-01-22
Hi. I have recently installed Ubuntu 12.10 and have been tring to get the wireless to work for a few days now. It shows it is connected to my router, yet I have no internet connection when I go to firefox. My wireless network uses a WPA/WPA2 connection. Can you help me out Chili?

---

### Post by chili555 on 2013-01-22
> **INe35 said:**
> Hi. I have recently installed Ubuntu 12.10 and have been tring to get the wireless to work for a few days now. It shows it is connected to my router, yet I have no internet connection when I go to firefox. My wireless network uses a WPA/WPA2 connection. Can you help me out Chili?
Please provide the infomation I requested in post #2.

---

