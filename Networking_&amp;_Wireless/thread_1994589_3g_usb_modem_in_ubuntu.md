---
title: "3g usb modem in ubuntu?"
date: 2012-06-03
forum: Networking &amp; Wireless
---

### Post by siddardhab on 2012-06-03
Hi,

I am from India and I have setup ubuntu and I have this Aircel 3g usb modem.I connected the usb modem and tried the inbuilt Network manager for mobile broadband.Even though the carrier is listed,I tried all the possible connections,but it wasn't getting connected.

When i used the same usb modem in Windows ,I noticed a folder called Linux in it.The readme file says 


> --How to Install---------------------- 
* You need login as root *
 
1. Run "tar jxvf linux_install.tar.bz2"

2. Run "./install" in TERMINAL to install MobilePartner 
   eg: # bash /<path>/install 
    
3. If you had installed this software in your system before, you will get a prompt: "The software is exist, do you want overwrites? ([Y]/[N])", enter "y" to overwrites or "n" to exit. 
 
4. If you do not had installed this software in your system before, you will get a prompt: "Please input the install path[/usr/local/Mobile_Partner]:". Then you can input install path(fullpath), or you may using the default path(/usr/local/Mobile_Partner) by press ENTER direct 
 
5. Finish installing 
 
--How to run-------------------------- 
* From shortcut in desktop 
 
* Run MobilePartner in your install path 
   eg: # /<install path>/MobilePartner 

 
* Plug in your device, it will run automatically (Not supported in Xandros)
I copied the Linux folder to a pendrive and 'cd' into the corresponding directory and logged in as root and when i tried the following command 

> tar jxvf linux_install.tar.bz2I get the following 

> tar (child): linux_install.tar.bz2: Cannot open: No such file or directory
tar (child): Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error is not recoverable: exiting now
What should i do?

Thanks.

---

### Post by Mudito on 2012-08-21
Try this:

Open the file browser, go to the folder where the files are, left click with your mouse on the linux_install.tar.bz2 file and select "Extract here"

It will create a folder with the same name as the file, browse into the folder right click anywhere and select "Open in Terminal" 

Write "sudo sh install" or "sudo ./install", not sure which one works, it will then ask for your password.

Hope it works!

---

### Post by Kujua on 2012-12-23
I got my Aircel datacard to work on Ubuntu.
Device model: Huawei E303S
Distro: Kubuntu 12.04, Ubuntu 11.10

Try the following steps:
Run the install command like this:
> sudo bash <path to Aircel>/Linux/install
Use the default install directory (/usr/local/Aircel)

Now reinsert the datacard. Aircel application should start automatically. If it doesn't, configure ppp as given here: [http://www.huaweidevice.co.in/Downloads/Linux-Installation-User-Guide.pdf](http://www.huaweidevice.co.in/Downloads/Linux-Installation-User-Guide.pdf)
You can skip the installation and GUI configuration section (Need only section 4).

---

