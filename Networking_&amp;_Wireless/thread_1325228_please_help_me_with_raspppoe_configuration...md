---
title: "please help me with raspppoe configuration.."
date: 2009-11-13
forum: Networking &amp; Wireless
---

### Post by harshu2kz on 2009-11-13
hi!
i just installed ubuntu and its working great but i cant access the internet
:(, please help me figure it out.
i connect to the internet in win XP as follows-
- adding a pppoe over internet protocol (installing the raspppoe driver that as provided by my ISP)
- run-> typing 'raspppoe'> query available services>selecting my isp
the dialup shortcut gets created
-i provide the my username and password.

since i am new to ubuntu, please give me a step by step approach..

---

### Post by harshu2kz on 2009-11-14
hello!
it managed to detect my ethernet connection as active but only when i manually entered the server address, subnet mas etc...but  i have to dial the service with  my username and password after the ethernet connection is up. so, i also tired making a DSL connection. however, when i try to connect via dsl the ethernet gets disconnected and is connected back when dsl attempt fails.

---

### Post by driftertx on 2009-11-14
Have you tried bypassing this PPPoE connection and setting up the PPPoE dialing through a linksys-type router? Most of them come with support for PPPoE and usually work pretty well.

---

### Post by harshu2kz on 2009-11-17
hi, 
thanks a lot fr replying. could you please elaborate more on that?

---

### Post by harshu2kz on 2010-05-15
hi!
i managed to find a solution atlast! So in the spirit of ubuntu i'll  contribute what i learned.
As you might know my ISP is pacenet ( the details of how i connect to  the net are give in the 1st post). 
here are the steps for configuration-
1. download a pppoe client like roaring penguin .tar.gz package from here [http://www.roaringpenguin.com/products/pppoe](http://www.roaringpenguin.com/products/pppoe)

2. open terminal, navigate to directory where you have downloaded roaring penguin (command- **cd /<path>**)

3. in terminal, type "**./go-gui" **(package will be installed)
4. in terminal, type** "pppoe-setup" **and type accordingly.
  
5. again type "**sudo nautilus**" from file manager navigate to filesystem>etc>ppp

6. chap-secrets file should contain your username and password 

7.  pap-secrets file should contain username, servername, password
(pacenet people -servername will be the server you are dialing to. you can find that out by **ipconfig** in windows cmd. IP address is not required for us as it is dynamic)

8. pppoe.conf file should have proper username, AC name ie access concentrator name (the server name that you r dialing to ) and the Servicename (same as server name)

 and you are done!

this method is lengthy but i worked for me, if anyone of you has a shorter one please share :)
if any queries then please revert.

---

