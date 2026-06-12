---
title: "SmartLink Modem -"
date: 2006-07-06
forum: Networking &amp; Wireless
---

### Post by cnu on 2006-07-06
I have a AMD64 bit processor and installed Dapper 6.06 64bit on it. I have a smartlink modem and followed the instructions in [https://help.ubuntu.com/community/DialupModemHowto#head-99945ca8c47f732b848a274e8dc6d0f5f8a2ce5c](https://help.ubuntu.com/community/DialupModemHowto#head-99945ca8c47f732b848a274e8dc6d0f5f8a2ce5c) which has special instructions to install in Dapper.
I downloaded the slmodem-2.9.11-20051101.tar.gz file and did make.
I got a very long list of errors. I have attached the screen listing as a gzipped txt file.
I would like to know what is wrong with this.

---

### Post by cnu on 2006-07-06
Atlast I configured my internet.
I installed Dapper i386 on my 64 bit proc. Then I followed the instructions as in the documentation([https://help.ubuntu.com/community/DialupModemHowto#head-99945ca8c47f732b848a274e8dc6d0f5f8a2ce5c)](https://help.ubuntu.com/community/DialupModemHowto#head-99945ca8c47f732b848a274e8dc6d0f5f8a2ce5c)).
At first there were some hiccups, but they were due to the failed dependencies.
After I solved them, I could make wvdial dial. But when it got connected to my ISP, and the Login prompt came, it just lost carrier and redialled. 
I just put the Stupid Mode = 1 in the wvdial.conf file and got connected.
I think I must write a nice howto on that.

---

### Post by cnu on 2006-07-08
Here is how I installed smartlink modem in Ubuntu Dapper.
[http://www.fslog.com/2006/07/08/smartlink-modem-in-ubuntu-dapper/](http://www.fslog.com/2006/07/08/smartlink-modem-in-ubuntu-dapper/)

---

