---
title: "Trouble setting up a HP C4795 Wireless Printer for Wireless"
date: 2009-12-24
forum: Networking &amp; Wireless
---

### Post by xtiano77 on 2009-12-24
I purchased an HP C4795 printer. I plugged it into the USB port and Linux picked it up right away. I able to print just about anything I need or want; however, I am having trouble setting up for wireless so both my Desktop and Laptop can use it. I tried running the wireless setup on the printer menu and it shows a WIFI Secure Network option but it doesn't give me any option to access that menu. I tried the following steps:

System
Administration
Printing
New
Printer
Network Printer
AppSocket/HP JetDirect

Now, there are two text boxes to the right, one for the Port number which displays 9100, and the other for "Host" which is blank. After some looking around, I found several posts where it says that the "Host" refers to the Printer's IP address; however, right now I am unable to figure out the printer's IP address.  Can anyone help me out in setting up this printer? Thanks in advance for your help.


Both computers are running Ubuntu 9.10

This computer:
Inter Dual Core Quad Processor
2GB Memory
500 GB Hard drive
Netgear Rangemax Wireless Router

Update:

I am not sure how I got it to work, but I did. This briefly what I did:

1. reset the router to factory settings.
2. customized it for my home.
3. re-plugged the printer to the computer.
4. ran the hp-setup wizard and followed the instructions.
5. Once done, unplugged the printer, tried it and it worked!

Funny, I tried steps 3 to 5 on three prior occasions and it didn't work. I can only guess it was the resetting of the router that made the difference.  Thanks anyway!

---

### Post by ZeroEx on 2009-12-29
I'm running 9.10 and have an hp c4580  there is no "Wireless Setup" in the options.  I'm hoping there's some ubuntu printer configuration software that I can use to configure my printer to connect to my hidden, encrypted network?

FIXED:

followed instructions at this post

[http://travelswithubuntu.blogspot.com/2009/09/wireless-printing-with-hp-photosmart.html](http://travelswithubuntu.blogspot.com/2009/09/wireless-printing-with-hp-photosmart.html)

---

