---
title: "About controlling fans."
date: 2011-03-15
forum: Multimedia Software
---

### Post by umpat on 2011-03-15
Hello everyone...  I was having some problems with playing youtube videos or using flash content. Whenever I use youtube for longer than 15 minutes, google chromium will crash with and hear the fan running very fast and is hot. 
I tried installing imsensors via terminal but I am not sure if I did it right or not.  But when I type sensors on terminal I get the following 
acpitz-virtual-0
Adapter: Virtual device
temp1:       +44.0°C                                    

k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:  +51.0°C                                    
Core0 Temp:  +47.0°C                                    
Core1 Temp:  +50.0°C                                    
Core1 Temp:  +46.0°C     .
So I suppose I have installed the imsensors correctly. But when I try to add imsensors on panel, I can't find it.
Also when i type fan, I get the follwing message 
 fan: laptop does not have cooling fan or kernel module not installed.
BTW my computer have following specs
AMD turion 64 x2, 1.8
RAM 1 GB
HP pavillion DV 9000. 

Also my webcam is not working . 
I installed additional drivers from system menu, everything else but webcam is not working .
Thank you all

---

### Post by no2498 on 2011-03-15
open a terminal type htop click enter
it tells you how to install it
after installed type htop click enter
go look at a video look at htop as its playing 
see what is using the most memory and cpu

this gives you something that may need fixed 
a place to start

---

### Post by Yellow Pasque on 2011-03-16
Playing video through the Flash plugin is notorious for overheating systems. Check out flash-aid FF extension or find some other way to save the flash video and play it in a native video player.

As for the fan thing, laptops generally use ACPI to control the fan.

---

### Post by umpat on 2011-03-18
Thank you for your reply. I tried installing the flash FF extensions but didn't worked.
But for youtube I found a software called minitube which plays all the youtube video and you can download the videos as well. So don't have to worry about flash no more.

---

