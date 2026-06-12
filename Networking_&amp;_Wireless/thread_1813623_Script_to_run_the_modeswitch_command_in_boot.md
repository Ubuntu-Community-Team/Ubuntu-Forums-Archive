---
title: "Script to run the modeswitch command in boot"
date: 2011-07-28
forum: Networking &amp; Wireless
---

### Post by drpjkurian on 2011-07-28
Hi
I am having one Huawei EC156 modem for my wireless broadband connection. Everytime when I boot the machine, I have to run the following commands in the terminal. The commands are as follows
```
 cd /etc/usb_modeswitch.d
``` followed by 
```
sudo usb_modeswitch -I -W -c 12d1\:1505

```

I would be very grateful if I can have a launcher which run this script automatically in terminal by clicking on it.

Thanks in advance

---

### Post by drpjkurian on 2011-07-28
bump

---

### Post by jayadeep on 2011-07-28
Script to run the modeswitch command in boot
steps
1.Open the gedit
2.Type the two commands which you want to run in two separate lines.
3.save the file with the extension  **.sh** on the disk where ever you want and make this file **as executable** in the **properties**
4.Then right click on the desktop
5.**Create new -link to application**
6.Give your desired name
7.Go to the **properties** of the new link on desktop 
8.Go to **application**
9.Give the path of file with the extension **.sh** in the **command** box
10.Go to **advanced options** 
11.Tick the coloumns of **run in terminal **and **run as a different user**
12.Hit **ok**



open the link created on the desktop 

type the password if required

enjoy........

---

### Post by drpjkurian on 2011-07-29
Thanks Jayadeep
 You have done a wonderful job...........

---

