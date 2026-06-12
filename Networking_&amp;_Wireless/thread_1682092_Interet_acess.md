---
title: "Interet acess"
date: 2011-02-05
forum: Networking &amp; Wireless
---

### Post by mishra.sandip on 2011-02-05
Hi
 
Could you pleaseme out.
 
I have installed Virtual BOX on windows 7.Ubuntu i have installed on virtual box. Now i want to access internet from the Ubutu VM.Please help.
 
Regards
Sandip

---

### Post by wojox on 2011-02-05
Ethernet or Wireless connection?

---

### Post by mishra.sandip on 2011-02-05
Ethernet Connection !!  My windows 7 is running on DHCP and getting IP address below
 
Ethernet adapter Local Area Connection:
   Connection-specific DNS Suffix  . :
   Link-local IPv6 Address . . . . . : fe80::95b7:70b5:e594:a64a%11
   IPv4 Address. . . . . . . . . . . : 122.50.244.34
   Subnet Mask . . . . . . . . . . . : 255.255.252.0
   Default Gateway . . . . . . . . . : 122.50.244.1

---

### Post by grahammechanical on 2011-02-05
An operating system installed in a virtual machine does not directly access the computer's hardware. So, on your machine Ubuntu can only access the modem through Virtual Box which in turn uses Windows 7. Since, your connection is working in Windows 7 it should be possible for Ubuntu to also connect.

It is my guess that you will have to adjust some settings in Virtual Box to allow or give Ubuntu permission to access the ethernet adapter on the motherboard. What does the Virtual Box help program say you should do?

Regards.

---

### Post by drdos2006 on 2011-02-05
Set Virtualbox up to have a Bridged connection in the Network setup.
Then Windows will be on the same subgroup as your Ubuntu machine.

regards

---

### Post by mishra.sandip on 2011-02-06
Hi thanks !!
 
Virtual Box Netwokr Adapter set on NAT or Bridge Mode and 
 
Ubuntu Network seetings to DHCP (Automatic.).

---

