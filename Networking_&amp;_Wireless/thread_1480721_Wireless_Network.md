---
title: "Wireless Network"
date: 2010-05-11
forum: Networking &amp; Wireless
---

### Post by markinmadison on 2010-05-11
Ok, I am new to setting up a wireless network, so bear with me. I just bought a Cisco wireless router and the little USB plug ins (which if I may say, are overly expensive). I can not figure out how to install the router. It is a Linksys E1000 Wireless N Router. I tried to load the software via wine. No luck doing that. I also checked out on Linksys's website and they don't give any info on linux or Ubuntu. Does someone out there know something? Or should I just take this one back and purchase something else?

Thanx...Mark

---

### Post by chili555 on 2010-05-11
Please see page 13 of the Users Guide. From your Ubuntu computer, connect an ethernet cable to any of the LAN ports on the router. Open a terminal and do:```
sudo ifconfig eth0 192.168.1.2 up
```Now open Firefox and enter in the address bar:  [http://192.168.1.1](http://192.168.1.1)

Use the user name and password in the User Guide and then you can access and set up the router's administrative pages.

Please see attached.

---

### Post by markinmadison on 2010-05-11
Ok, but there wasn't a users guide in the package. It is all on disk that won't go past looking for a "network connection".

---

### Post by chili555 on 2010-05-12
Do I take that to be, "Yay, it works!" Do you need more guidance?

---

### Post by markinmadison on 2010-05-12
I called Cisco and they told me that since I have Linux, they won't support in talking to me. I told them that I will never purchase another Cisco or Linksys product again. I also told them that they had better get their act together and start supporting Linux because of so many people sick of the Windows Games.

I have since put the router back in the box and it will be taken back to Best Buy for return. I am feeling very computer ignorant. Why can't Ubuntu make it very easy just like the rest of the program. Or then again, it could be my ignorance again. 

I do thank everyone for their feedback, and help with this problem. I have never setup a wireless system and as of right now, I probably never will.

---

### Post by markinmadison on 2010-05-12
btw, I did put the IP address in FF. It did go to a setup menu but was at a loss from there.

---

### Post by ilikeyourflannel on 2010-05-12
Network devices are generally platform independent.  I doubt you will find any mainstream consumer grade router manufacturer that offers support for linux.  

If you got to the setup menu you might be most of the way to where you want to be.  What do you want to setup on your router?

---

### Post by chili555 on 2010-05-12
> **markinmadison said:**
> btw, I did put the IP address in FF. It did go to a setup menu but was at a loss from there.We'd be glad to guide you. Most routers will have the same issue; a Windows setup disk and a browser interface which is available for the Linux/BSD/geek crowd. The process is fairly straightforward, actually.

---

