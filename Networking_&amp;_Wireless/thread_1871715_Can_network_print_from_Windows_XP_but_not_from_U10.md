---
title: "Can network print from Windows XP but not from U1004"
date: 2011-10-29
forum: Networking &amp; Wireless
---

### Post by Trapper on 2011-10-29
U-1004

I have a u1004 machine on a static local IP that provides printer services for other machines on my local network. Those machines also have static IP's. Those machines also have Windows XP and U-1004 installed. Uniquely, all the windows installs can access the print server and print. None of the U-1004 installs will. I've pinged from u1004 to the print server on all the machines successfully. I've taken it a step further and done a telnet on port 631 to the print server from the u1004 installs and had successful access via port 631.

Each u1004 install found my HP C4600-series printer when I set them up for network printer but none of them will actually access the printer to print. They say the are sending the job to be printed but nothing arrives at the print server and nothing gets printed. After a length of time ( 5 minutes or more) a message window pops up on the u1004 client saying the job was successfully printed, however nothing actually prints out on the network printer. What am I missing?

---

