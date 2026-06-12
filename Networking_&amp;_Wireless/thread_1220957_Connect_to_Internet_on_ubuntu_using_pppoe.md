---
title: "Connect to Internet on ubuntu using pppoe"
date: 2009-07-23
forum: Networking &amp; Wireless
---

### Post by rahulsingh.nitrkl on 2009-07-23
Hi, I am new to ubuntu/linux. Installed it today. I have a HP laptop. 
Intel(R) PRO/100 VE Network Connection. Can anyone tell me how to connect to internet.
In WINDOWS, I have a broadband connection and connect via PPPOE. 

Also, please tell me if i can share files with windows users on the network. Please explain
in detail as i am a total newbie. I am still reading the introduction pages of ebooks on ubuntu. Please help soon.

---

### Post by Kobalt on 2009-07-23
Hello,

To connect with a PPPOE connection open the Terminal and enter the following command to configure your connection (that will be very simple):
```
sudo pppoeconf
```

In order to share a file, right-click on it and select "share", it will give you instructions on how to proceed.

---

### Post by superprash2003 on 2009-07-23
you can also check out system->preferences->network connections and go to the DSL tab. first ensure you can access the modem via http

---

