---
title: "Can't enable Mobile broadband connection"
date: 2010-10-20
forum: Networking &amp; Wireless
---

### Post by Chauhan Ankit on 2010-10-20
Hello all,
I am new to linux, so i downloaded ubuntu 10.10 for learning purpose. All goes well, i installed it successfully.
The problem which i face is that when i connected my mobile broadband device, ubuntu detects it and i have succesfully made the connection.
But the network Manager is showing "disable" Mobile Broadband connection. I tried to put a check on Enable Mobile Broadband but can't check it. So i can't access Internet in ubuntu.
-> I think some offline package installation should be there to resolve the problem, or some console commands.:confused:
-> I tried to use the (wvdial) which i use at Backtrack. but i think ubuntu did not have.:(
Help me guys to connect to Internet:)
Thanks

---

### Post by alexfish on 2010-10-20
hi
when the connection is established with Network Manager
right click on Network Manager and select Connection Information

Post contents of

IP Address :
Broadcast Address:
Primary DNS:
Secondary DNS:

alexfish

---

### Post by wrenchy54110 on 2010-10-29
I have this exact same problem.  I was able to set up a connection and select the correct device but when I look under the network connections icon it says the mobile broadband is disabled.  When I click on it to enable mobile broadband the window closes but nothing changes.  It will not enable.  

Please advise.

Regards,

Frustrated...

---

### Post by Echtesatir on 2010-10-31
Hi, Same problem on HP mini 5101..

---

### Post by stevpm on 2010-11-13
SAME HERE Samsung RF510... Ubuntu 10.10

---

### Post by tankyank on 2010-11-14
Ok I use a sprint mobile broadband card usb model . Right click the network manager . Click on edit connections . I don't use anything but my broadband card . You will see auto etho . Highlight that and uncheck connect automatically . Next click on mobile broadband and then click on add . Then choose your company . Follow the prompts .

---

### Post by ravi89 on 2010-12-19
To enable Mobile broadband this is the solution AFAIKW and it works for me(HUAWEI BSNL):

```

   sudo gedit /etc/rc.local

```

and add the following line before the line 'exit' :
##Note: Include appropriate modprobe cmd.
```

  sudo modprobe usbserial vendor=0x12d1 product=0x1010

```
If you are using  modprobe **** and then wvdial cmd, then I hope it will work for you.

---

