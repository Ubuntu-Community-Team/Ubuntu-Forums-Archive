---
title: "HP Laptop WLAN issues"
date: 2011-01-04
forum: Networking &amp; Wireless
---

### Post by Luckybob on 2011-01-04
Hi, I've installed ubuntu as the sole operating system as windows vista was so unstable on the laptop. There were issues prior to installing ubuntu with wifi but now wifi is totally unrecognisble. ie it cannot even find the network card with ubuntu which was happening just before I got rid of windows.

Is there a driver or something I can do....I am able to connect to the internet via an ethernet cable which isn't the best really as I rather be sat on the sofa watching the TV while I type and not sat behind on a short cable:(

Can anyone help - I'm completely new to this - tried running the update manager which is busy installing stuff but still no joy - HELP!!!!

---

### Post by Chuyg9 on 2011-01-04
Write on the Terminal and tell us what it says
[PHP]lpsci[/PHP]

---

### Post by Bucky Ball on 2011-01-04
Hold everything Luckybob. Are you using 10.10 and kernel 2.6.35-24??? You will find the kernel version when you boot into the machine and are looking at the options. Entry at the top of the list and the number at the end of that line. There are known issues and bug reports. One of the issues is that it crashes Broadcom wireless cards. Many HP machines use this card. 

Try 10.04 LTS if this is the situation. You'll find a smoother ride as a bit more stable.

Chuyg9: 'Write on the terminal' is not really enough information for a new user. OP probably doesn't know what you're on about. ;)

Maybe:

Applications->Accessories->Terminal and type in:

```
lspci
```(not 'PHP code'; that is a different thing) and look for a line that begins with a number and 'Network Controller'. Something like this:

```
03:00.0 Network controller: **Realtek Semiconductor Co., Ltd. RTL8191SEvB Wireless LAN Controller (rev 10)**
```Generally somewhere near the bottom of the output. We only need to know the bit I have in bold. :)

---

### Post by PatchesTheCaveman on 2011-01-04
Hi Luckybob!

Likely you have to install the Broadcom drivers.  To do that, go to System > Administration > Additonal Drivers, click on the Broadcom STA wireless driver, and click Install.

Like Bucky Ball said, there is a problem with the 2.6.35-24 kernel on Ubuntu 10.10 that breaks Broadcom wireless card, as well as a laundry list of other devices.  Make sure you don't install the linux-image-2.6.35-24-generic update if you can.  If you think you did, follow the instructions I provided in this post to make sure you have the broken kernel and fix it:
[http://ubuntuforums.org/showpost.php?p=10312711&postcount=5](http://ubuntuforums.org/showpost.php?p=10312711&postcount=5)

---

