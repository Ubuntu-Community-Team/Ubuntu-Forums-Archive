---
title: "Need Help Installing Sprint Sierra Wireless USB EVDO Modem"
date: 2009-05-04
forum: Networking &amp; Wireless
---

### Post by Poppa0418 on 2009-05-04
Hello,

First off, I am VERY new to Linux/Ubuntu. I have been using it for about a week. (I am not even using it, this is a friend's laptop that I am attempting to help him with)

Ok so, I am using a Dell mini 9 netbook with Ubuntu 8.04 Hardy installed. Wired and Wireless networking both work fine. I am trying to install this USB Sprint aircard 589U by Sierra Wireless. 

I downloaded and went throught the guide that Sprint.com has provided. This guide suggests using KPPP which I cannot install on this laptop because it is not supported on my computer type (lpia). 

After some research, I found out I was able to use Gnome-PPP, after reading some posts, i got it to work! (At least i think i did) It dialed, and gave me a valid ip address. 

So i wanted to make sure it was working correctly and that the aircard was giving me internet access and not the wireless, so i disabled the wireless and restarted the laptop. Since I have done this, I have not been able to get the laptop to detect the aircard.  Ive read a million posts and tried a thousand methods, none of which seem to work.

the output of my dmesg is as follows:

usb 2-1: new full speed USB device using uhci_hcd and address 3
usb 2-1: configuration #1 chosen from 1 choice
usb-storage: device ignored
sierra: probe of 2-1:1.0 failed with error -5
usb  2-1: USB disconnect, address 2
usb 2-1: new full speed USB device using uhci_hcd and address 3
usb 2-1: configuration #1 chosen from 1 choice
scsi5 : SCSI emulation for USB Mass Storage devices
usb-storage: device found at 3
usb-storage: waiting for device to settle before scanning
usb-storage: device scan complete
scsi 5:0:0:0: Direct- Access      Sierra  Wireless Storage 2.31 PQ: 0 ANSI : 2
sd 5:0:0:0: [sdbd] Attached SCSI removable disk
sd 5:0:0:0: Attached scsi generic sg1 type 0


The result of lsusb is as follows:

root@sdot:~# lsusb
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 1199:0025 Sierra Wireless, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 005 Device 002: ID 0c45:63e4 Microdia 

so it recognizes it,  but when i open gnome-ppp and try to detect the modem on any and all devices i get  no modem found on your system or cannot detect modem

The most recent 'method' i've tried was disabling the airprime drivers by blacklisting it?
Like ive said i'm very new to this and i just copy and paste what it says to do in the threads. 

Any help would be greatly appreciated. Thanks.

---

### Post by Poppa0418 on 2009-05-07
bump? Please help. I am completely lost. 

I can see the modem attached in lsusb with the correct vendor and product IDs, but when i run dmesg, i get

sierra: probe of 4-2:1.0 failed with error -5

and it is not attached to any tty/USB* 

Please help, i need a professional, an expert!

---

### Post by Poppa0418 on 2009-05-11
**Bump** 

I need a guru!

---

### Post by Poppa0418 on 2009-05-12
**bump** 

How many times do i have to bump this to find someone who knows something?!?!

---

### Post by Poppa0418 on 2009-05-18
*bump*  ANYONE???

---

### Post by GeorgeVita on 2009-05-18
Hi **Poppa0418**,

The main reason that somebody does not answers is possibly that cannot help you or did not reach your posts. I am using some search strings which are not included into your posts so your last bump catched from my eye today!

Let's try to summarise:

You are using Ubuntu 8.04, trying to connect a Sprint Sierra USB EVDO modem and from **lsusb** you see: **1199:0025 Sierra Wireless, Inc. **

After confirming above status try from terminal:
sudo modprobe usbserial vendor=0x1199 product=0x0025

and then try: **ls /dev/ttyU* /dev/ttyA***

Post here the results to follow up!

Regards,
George

---

### Post by Poppa0418 on 2009-05-18
George, thank you so much for replying.

the results of ls /dev/ttyU* /dev/ttyA*  

are as follows:

sdot@sdot: -$  ls /dev/ttyU* /dev/ttyA*
ls: cannot access /dev/ttyU*: no such file or directory
ls: cannot access /dev/ttyA*: no such file or directory

---

### Post by GeorgeVita on 2009-05-18
Can you try again the following:

Boot without the modem, wait for the system to stabilise, DISABLE WIRELESS (right click to network manager icon & untick "enable wireless"), open a terminal window:
**sudo modprobe usbserial vendor=0x1199 product=0x0025**
attach the modem, wait 15 seconds, **dmesg** and then **ls /dev/ttyU* /dev/ttyH***.

Post the ls /dev/... output and the last 10-15 lines of dmesg regarding usb or drivers.

EDIT: Also from [http://ubuntuforums.org/showthread.php?t=779652](http://ubuntuforums.org/showthread.php?t=779652) I found
[www4.sprint.com/pcsbusiness/downloads/Sprint_Mobile_Broadband_Setup_Guide.pdf](www4.sprint.com/pcsbusiness/downloads/Sprint_Mobile_Broadband_Setup_Guide.pdf)
which possibly describes your initial tries.

G

---

### Post by Poppa0418 on 2009-05-18
George! Great Success! Finally!

So I am guessing my problem was:

1) I had the modem constantly plugged in at boot
2) I wasnt doing modprobe usbserial vendor and product each time i booted.

Is there a way I can automate this? I think i saw it in one of the other threads but not sure which one it was.

btw I am posting this reply while connected on my usb modem and im so excited! haha thanks so much!!!

---

### Post by GeorgeVita on 2009-05-18
Well done!

Yes you can. You must create a .rules file:

From terminal run: **sudo gedit /etc/udev/rules.d/90-newEVDO.rules**
copy paste the following lines:

[B]ACTION!="add", GOTO="evdo_End"
#
SUBSYSTEM=="usb", SYSFS{idProduct}=="0025", SYSFS{idVendor}=="1199", GOTO="evdo_Modem"
#
LABEL="evdo_Modem"
RUN+="/sbin/modprobe usbserial vendor=0x1199 product=0x0025", MODE="660", GROUP="dialout"
#
LABEL="evdo_End"
[/B]

Save and Exit from gedit.

Reboot and have fun!
G

---

### Post by Poppa0418 on 2009-05-18
Once again thank you George!!!

Now that I am connected i have 2 more small problems.

One - when i first get connected and open firefix, it defaults to offline mode, i have to go to file and uncheck offline mode every time i boot up

two - my speed is very slow. i took a speed test and it came to 15kbps  slower than a regular dial up modem, even though this is supposed to be broadband. Im guessing it could just be i dont have good reception where I am? or is there a setting i can change?

---

### Post by GeorgeVita on 2009-05-18
Firefox Offline mode (copied from other thread):
> **rmrfstar said:**
> To follow up (although no one will likely read this), I believe the correct way to disable offline mode in Firefox is:

1) Start Firefox
2) In the address bar, type about:config
3) Search for "offline"
4) Toggle (double-click) browser.cache.offline.enable to "false"

About speed: usually there is a led showing the connection (GPRS/3G/...). It is better to start a connection after the High Speed color.

What is the actual way you are connecting? Do you have any config file (as /etc/wvdial.conf)? If there is any Baud Rate make it 460800.

A final note: Upgrading to 8.10 you could haave the option of Network Manager 0.7 which works well. If you choose 9.04 (recent version) it is better to read other posts before you try because there are a lot of changes affecting 3G modems.

ALSO write down the number of this thread to come back in the future...

Regards,
George

---

### Post by Poppa0418 on 2009-05-18
George, once again thanks for everything. You were amazing. I was getting ready to either sell this netbook or throw it out the window altogether! Thanks so much. take care and God bless you.

---

