---
title: "Update Regulatory Domain/CDRA"
date: 2010-10-24
forum: Networking &amp; Wireless
---

### Post by munkymac on 2010-10-24
I've got a Samsung NC-10 running Maverick. I purchased it in the US, and am now in France. I'm running into troubles connecting to certain networks, because they are broadcasting on channels 12 or 13. 

After a bunch of research, it seems that it's not a driver issue, and may/may not be a hardware issue (something about the EEPROM), but that it could have something to do with the regulatory domain that CDRA is sending to the kernel. While I sort of understand what the second half of that sentence means, I don't possess the technical accumen to do anything about it. 

Has anyone (most likely ex-pats) run into this problem and found a way to get around it?

I know that this has to be the problem, because my Android phone was unable to connect to the same networks until I changed the regulatory domain settings to scan channels 12 and 13, and then it connected immediately.

---

### Post by munkymac on 2010-11-01
On the off chance that it would work, I tried installing the driver from Samsung's Italy site (my friend has an NC10 that he purchase in Italy that is able to connect without problems to the same channels). I used ndiswrapper, and now I can scan 14 channels (initially, when I ran iwlist, only 11 would show). However, I still can't get even see the network at the place I'm staying for the next two weeks. 

What else can I do?

Here's my iwlist output: 

```
aaron@aaron-NC10:~$ iwlist channel
lo        no frequency information.

eth0      no frequency information.

wlan0     14 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 14 : 2.484 GHz
          Current Frequency:2.432 GHz (Channel 5)

usb0      no frequency information.

```

---

