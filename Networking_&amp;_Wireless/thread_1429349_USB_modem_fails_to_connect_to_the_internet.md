---
title: "USB modem fails to connect to the internet"
date: 2010-03-13
forum: Networking &amp; Wireless
---

### Post by mohamed.fouad on 2010-03-13
I have a Huawei E1550 USB modem it is detected and it connects through the normal connection maneger but when I open Firefox it say server not found although i have set firefox to automatically detect proxy.:confused:

---

### Post by medo55 on 2010-04-22
try to sue DNS resolver 
8.8.8.8
8.8.4.4

---

### Post by alexfish on 2010-04-22
Hi  
 
for gsm connections try leaving network settings to NO PROXY 

if still not working

 you can set Ipv4 settings via Network Manager to Automatic (ppp) address only and enter the address in the DNS servers box separated with a &#8220; , &#8220; without the quotes ,you can use open nics or the address as above, for open nics search Internet with same title ( note some ISP's  will not allow the use of open nics )

 

 

  to stay with your ISP , have a look in the /etc/ppp/resolv.conf . The addresses may be there This is different to the etc/resolv.conf  as returned by the network manager,  so they can be entered as above ,maybe ask your ISP
 

   or check on your system the file called &#8220;serviceproviders.xml&#8221; the actual database used by the NM have a look through this file until you find your details of your country and ISP and pay plan it should show the named server addresses
 

 the above can have its problems if your ISP changes servers so you could try what I have done here
 

 post #23
 

 [http://ubuntuforums.org/showthread.php?t=1331660&page=3](http://ubuntuforums.org/showthread.php?t=1331660&page=3)
 

 try both methods to see which works best
 

 regards
 

 alexfish

---

