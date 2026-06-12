---
title: "BSNL Broadband connection problems"
date: 2010-06-08
forum: Networking &amp; Wireless
---

### Post by vishwasmeshram on 2010-06-08
hi.......
i m new to the ubuntu so guys plz help me to sort out this......
i have a bsnl broadband connection which works on windows fine. but not working in ubuntu. I configure my ethernet connection with proper ip add but still not able to access the internet .........
plz help me i m waiting...

---

### Post by dineshs on 2010-06-08
pl let us know the model name of your modem and how you are connecting in windows

---

### Post by prshah on 2010-06-08
> **vishwasmeshram said:**
> proper ip add but still not able to access the internet

What exactly is the problem you are facing? Are you able to browse? Or is browsing slow? How do you know you are not connected? Wired or wireless?

Please post more information about your setup so that we can suggest relevant steps.

I was also using BSNL broadband, and I faced an MTU issue. I could connect to the 'net, use torrents, etc, but could not access a number of sites reliably. I found the solution, you can read about it here: [[SOLVED] Firefox/Epiphany/Lynx not loading certain websites.]("http://ubuntuforums.org/showthread.php?t=718709")

However, this may not be applicable to you. Please post back with more information about how your connection is configured.

You can also get this information from Windows: Click Start-Run, give the command```
cmd
```, press enter. Now give the command ```
ipconfig /all
``` and copy and paste the output for more relevant steps on how to configure your Internet in Ubuntu.

---

### Post by vishwasmeshram on 2010-06-09
> **prshah said:**
> What exactly is the problem you are facing? Are you able to browse? Or is browsing slow? How do you know you are not connected? Wired or wireless?

Please post more information about your setup so that we can suggest relevant steps.

I was also using BSNL broadband, and I faced an MTU issue. I could connect to the 'net, use torrents, etc, but could not access a number of sites reliably. I found the solution, you can read about it here: [[SOLVED] Firefox/Epiphany/Lynx not loading certain websites.]("http://ubuntuforums.org/showthread.php?t=718709")

However, this may not be applicable to you. Please post back with more information about how your connection is configured.

You can also get this information from Windows: Click Start-Run, give the command```
cmd
```, press enter. Now give the command ```
ipconfig /all
``` and copy and paste the output for more relevant steps on how to configure your Internet in Ubuntu.
thanks for your reply .........
now i m able to access internet but it uses different ip 
and when i m trying to assign ip manually ......i cant give the gateway 
what should i do?
my modem is  DNA-A211-I

---

### Post by dineshs on 2010-06-09
ITI DNA modem comes DHCP enabled by default.You need not configure IP manually.
Please post the output of
```
ifconfig -a
```
> now i m able to access internet but it uses different ip
and when i m trying to assign ip manually ......i cant give the gateway 
Can you explain where and how you are trying to do this? Pl also let us know how you are connecting in windows.Do you use a PPPoE dialler with username and password to connect/disconnect (Called modem in bridge mode)

---

### Post by GIRI MURALI on 2010-07-03
I recently bought  a modem from BSNL.Along with that I got tutorial to connect BSNL broadband in Ubuntu from them.download it
[http://www.beubuntu.co.cc/2010/06/how-to-connect-bsnl-broadband-in-linux_27.html](http://www.beubuntu.co.cc/2010/06/how-to-connect-bsnl-broadband-in-linux_27.html)

---

