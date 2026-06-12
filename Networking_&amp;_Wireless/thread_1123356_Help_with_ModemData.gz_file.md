---
title: "Help with ModemData.gz file"
date: 2009-04-12
forum: Networking &amp; Wireless
---

### Post by peterconway on 2009-04-12
Hi, I'm a newbie - I have Ubuntu booting and running from CD, but no luck connecting to internet. I think it's the internal modem is not responding to Linux. I have attached the file ModemData.gz as suggested in Linmodems help page.

anyone out there who can help please?

Regards,

Peter

---

### Post by chili555 on 2009-04-12
You have attached the program that does a scan of your modem to give you information about how to set it up and connect. To help, you need to see the output files from running this. Open a terminal and do:```
gunzip scanModem.gz
chmod +x scanModem
./scanModem 
```A text file will be created called *ModemData.txt*. Once you have read that file, you will have the information you need to proceed. Post back if you get stuck.

---

