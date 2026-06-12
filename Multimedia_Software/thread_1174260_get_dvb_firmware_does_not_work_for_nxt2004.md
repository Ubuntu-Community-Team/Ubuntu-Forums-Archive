---
title: "get_dvb_firmware does not work for nxt2004"
date: 2009-05-30
forum: Multimedia Software
---

### Post by Osakibill on 2009-05-30
I am trying to get the FW for my AVerHDTV A180. I have done this successfully before for other installs. However now when I run
```
 sudo ./get_dvb_firmware nxt2004
--2009-05-30 14:48:28--  http://www.aver.com/support/Drivers/AVerTVHD_MCE_A180_Drv_v1.2.2.16.zip
Resolving www.aver.com... 219.87.67.11
Connecting to www.aver.com|219.87.67.11|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
2009-05-30 14:48:29 ERROR 404: Not Found.

wget failed - unable to download firmware at ./get_dvb_firmware line 372.

```I also tried to get  this file directly by: 
```
sudo wget http://www.aver.com/support/Drivers/AVerTVHD_MCE_A180_Drv_v1.2.2.16.zip
--2009-05-30 14:52:40--  http://www.aver.com/support/Drivers/AVerTVHD_MCE_A180_Drv_v1.2.2.16.zip
Resolving www.aver.com... 59.124.45.51
Connecting to www.aver.com|59.124.45.51|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
2009-05-30 14:52:40 ERROR 404: Not Found.


```I have tried this over a few days with the same results.  Anybody got an idea of how I get this FW somewhere else?

Has Avermedia removed this driver from its site?  I couldn't find any info there.

Thanks,
Bill

---

### Post by JanCeuleers on 2009-06-07
Get your script to fetch the file from here instead:

[http://www.avermedia-usa.com/support/Drivers/AVerTVHD_MCE_A180_Drv_v1.2.2.16.zip](http://www.avermedia-usa.com/support/Drivers/AVerTVHD_MCE_A180_Drv_v1.2.2.16.zip)

(From a helpful post on the mythtv-users mailing list by Michael T. Dean)

---

