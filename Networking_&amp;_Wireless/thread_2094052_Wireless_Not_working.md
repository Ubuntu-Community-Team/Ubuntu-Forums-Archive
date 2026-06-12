---
title: "Wireless Not working"
date: 2012-12-12
forum: Networking &amp; Wireless
---

### Post by RedEyedFiiend on 2012-12-12
Hi everyone! Im quite new to ubuntu, and i recently installed 10.04 from my brothers old disk. I noticed that the wireless was not working, so i upgraded to 12.04 in some stupid hope that it would help, but of course, it didnt.

Ive been roaming around on loads of forums, but haven't yet found a solution... 
Ive also tried NDISwrapper, but it didnt work either..
Ive tried updating AND searched for em using additional drivers, but yet, no avail.

Help is MUCH appreciated, since i hate sitting on here with an ethernet cable... 

Of course, i will need to give you some code, of the errors, but just tell me what to type into the terminal

Thanks in advance :)

---

### Post by Stormlord on 2012-12-12
Hi.  I have given some advice on the correct installation and usage of ndiswrapper over here:  [http://ubuntuforums.org/showthread.php?t=2093995](http://ubuntuforums.org/showthread.php?t=2093995)

Type sudo ifconfig -a in your terminal and check if wlan0 is in the list.  If you can see only eth0 and lo, try installing your Windows drivers through ndiswrapper.  Ndiswrapper is not a driver by itself.  :)

---

### Post by RedEyedFiiend on 2012-12-12
yes, i know that Ndiswrapper aint a driver, Ive tried using it! When i did it says "hardware present:Yes"
But still, Wireless wont work :/.
I tried doing sudo ifconfig -a           just now, and it didnt include wlan0 in the list :/ Only eth0.

I looked a bit into the link you sent, i dont have any other driver in "additional drivers" exept for a ATI driver. Nothing at all.

---

### Post by Stormlord on 2012-12-13
Yes, you're right.  The part about Additional Drivers is not relevant with your issue.  I thought the other info about Windows driver installation and complete ndiswrapper installation might help you.  :)

---

### Post by TBABill on 2012-12-13
First we need to know what device you are trying to get working. Can you open a terminal and give us the output of ```
lspci
``` I'm assuming it's an internal PCI device, but if it's a USB device, then it's ```
lsusb
``` And to see what drivers are active, also give us the output of ```
lsmod
``` Then we can give advice on what may help.

---

