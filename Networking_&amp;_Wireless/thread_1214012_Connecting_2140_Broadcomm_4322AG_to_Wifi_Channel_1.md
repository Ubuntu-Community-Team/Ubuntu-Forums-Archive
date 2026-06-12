---
title: "Connecting 2140 Broadcomm 4322AG to Wifi Channel 13?"
date: 2009-07-15
forum: Networking &amp; Wireless
---

### Post by kitenski on 2009-07-15
I just spend many hours trying to track down why my HP Mini running Windows 7 wouldn’t connect to my home Wifi network when I set my channel to 13.

After installing varying drivers, I still couldn’t get it to work, so eventually I searched the registry for Broadcom, and found 3 entries with a Country setting of US. I changed these to GB, re-booted and my HP Mini can now see my Wifi network on channel 13.

So I now have the same problem since I installed UNR, my 2140 cannot connect or even see my home Wifi network. 
 
WiFi is working as I can see some neighbours Wifi networks.
 
I read the FAQs and if I do a
 
sudo iwconfig eth1 channel 13
 
I get an error
 
Error for wireless request "Set Frequency" (8B04)
SET failed on device eth1 ; Invalid argument.
 
I am guessing the solution is similiar to the above, ie tell the 2140 I am in the UK and to look for Wifi Channels above 10!

Can anyone tell me how I do this with UNR?

Thanks in advance,

Greg

---

### Post by kitenski on 2009-07-17
Can anyone help here? If I change my network to use channel 6 it works fine, but then a music server I have on the edge of my network doesn't work, so I really need Ubuntu on channel 13!
 
Cheers,
 
greg

---

### Post by kevdog on 2009-07-17
You might have to apply a kernel patch to get the higher channels -- Im not sure.

---

