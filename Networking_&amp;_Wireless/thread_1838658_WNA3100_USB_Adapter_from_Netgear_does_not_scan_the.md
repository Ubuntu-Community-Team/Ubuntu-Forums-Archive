---
title: "WNA3100 USB Adapter from Netgear does not scan the wireless networks."
date: 2011-09-04
forum: Networking &amp; Wireless
---

### Post by ramkrishna.a@gmail.com on 2011-09-04
Hi, This is my first post at this forum. I have purchased Netgear WNA3100 wireless adapter and I tried to configure it via ndiswrapper. Below are some of the results
1. ra975x@myUbuntu:~$ ndiswrapper -l
    bcmwlhigh6 : driver installed
	device (0846:9020) present
--> It says dreiver installed and also identified the Device.
2. ra975x@myUbuntu:~$ lsusb
    Bus 002 Device 003: ID 0846:9020 NetGear, Inc. 
--> Device is identified.
3. ra975x@myUbuntu:~$ nm-tool
--> This does not display the device in the result. 

What is that I am still missing ?

Rama.

---

### Post by ramkrishna.a@gmail.com on 2011-09-04
Ok. At last got it working. Some silly mistakes I thought I did in the process. Thanks for info that I got from various Ubuntu sources. 

Yesterday: (This did not work)
Had WNA3100 USB Adapter. Plug N play is not possible so had to rely on NDISwrapper method. 
1. Installed NDISwrapper latest release candidate from 
   [http://sourceforge.net/projects/ndiswrapper/files/testing/1.57-rc1/](http://sourceforge.net/projects/ndiswrapper/files/testing/1.57-rc1/)
2. Installed the CD on windows 7(Later realized it was a mistake). Copied the bcmwlhigh6.inf and bcmwlhigh664.sys from system32/driverStore/FileRepository/bcmwl* folder to ubuntu box.
3. Ran the process on installing with ndiswrapper. I did not notice any error and ndiswrapper -l showed both the device and driver installed but the device failed to light up. No trace of wireless connection with any command. And gave up

Today: (This one worked.... surprisingly)
1. Replaced WNA3100 with WNDA3100v2 thinking it might help as per wireless usb adapter docs on Ubuntu forums. 
2. Inserted the Adapter in to the slot but system failed to recognize. 
3. Now realized that I had wine installed on my system. Then inserted the driver cd in Ubuntu box and wine started it up. It does not install the drivers but it neatly unpacks the installer and gives you the filer needed, bcmwlhigh5.inf and bcmwlhigh564.sys under the folder /home/ra975x/.wine/drive_c/Program Files/NETGEAR/WNA3100/Driver/WinXP2000
4. Notice that the file names are with '5' and compared to '6' which I installed yesterday. The wine property is set to WinXP mode. ( This is imp to configure wine to WINXP, else it extracts the installed with '6' and it is not compatible with Ubuntu). 
5. Used ndiswrapper again to install the bcmwlhigh5.inf driver. 
6. Plugged in the device and surprisingly .. wireless showed up and ..... I am connected. :). I have spent 3 days on this. 

Now I think WNA3100 too would have worked had I installed bcmwlhigh5.inf instead of bcmwlhigh6.inf.Let me know if any one tried out this process.

Hope this helps some one.

Rama.

---

