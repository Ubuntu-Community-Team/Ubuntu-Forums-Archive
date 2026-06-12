---
title: "USB Modem [DLink DSL200]"
date: 2005-03-19
forum: Networking &amp; Wireless
---

### Post by shmk on 2005-03-19
I installed eciadsl and I have followed all the procedures to install and set.

Because I couldn't find a good synch file in the default ones, I made a new my_synch.bin file with this procedure:
[http://eciadsl.flashtux.org/doc.php?file=eciadsl_install&doc_lang=en&view=html#Synch-_002ebin-creation](http://eciadsl.flashtux.org/doc.php?file=eciadsl_install&doc_lang=en&view=html#Synch-_002ebin-creation)

After I finally get the synchro but the connection is blocked at passage 4 of 5, when start to send rows like  [LCP ConfReq Id=0x01 magic<......>]  and at the end give LCP Timeout

I tried with RFC and LLC, with HDPC active or not but the result is the same.

I have "eciadsl 0.10" on Ubuntu Hoary Preview (downloaded 2 days ago) and a DLink DSL200 usb modem (over atm).

---

### Post by shmk on 2005-03-20
After one hundred tentatives finally I got connect to internet  :o 

I don't know "what" I did to make it happen but surely I :
- removed and reinstalled all eciadsl package;
- installed "pppoe" package got from debian site (this is strange but ubuntu on default installed only "pppoeconfig" packet but not "pppoe");

 =D>

---

