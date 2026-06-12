---
title: "CANT GET THE WIRELESS TO WORK! Ethernet works fine!"
date: 2012-08-12
forum: Networking &amp; Wireless
---

### Post by jasonroberts18 on 2012-08-12
I cant seem to find a fix for my wireless issues. I have a Realtek wireless card and I have an HP 2000 (I think that is the model number) laptop. The internet works just fine when I plug in an ethernet cable but the wireless wont connect or allow me to turn off airplane mode.  Do I need to install additional drivers?? What is realtek hasnt sent any new drivers?! I have the current LTS distro. Can anyone help?? 

Thank you again. 

Best,

Jason

---

### Post by Finnicella on 2012-08-14
Hi Jason,
Can you give me the output of these commands?
```
sudo lshw -C network
```
```
iwconfig
```
and
```
sudo rfkill list all
```
With these commands we can see your wireless card and if there are some blocks on it.
Bye and sorry for my english. :)

---

