---
title: "Networking trouble with Virtual box"
date: 2009-07-07
forum: Networking &amp; Wireless
---

### Post by shredder12 on 2009-07-07
Hi fellas,
         I have been trying to create a virtual working environment on my computer. I used 2 versions of backtrack ( 1 and 3 ). Using the NAT feature of Virtual Box I was able to provide Internet connectivity  to both the virtual machines. 

         But the IP of both the machines were same even though they were assigned different mac addresses.

          And for my purpose I need both the machines to have different IP addresses so that they may be able to recognize each other (as different systems Ofcourse ;) ).

Some help please !!!

---

### Post by terazen on 2009-07-07
Have you tried manually assigning ip addresses?

Try checking on the dhcp server what mac address it sees when you boot up each OS.

---

### Post by shredder12 on 2009-07-07
> **terazen said:**
> Have you tried manually assigning ip addresses?

Yes, I tried doing that too. Initially they had this ip address 10.0.2.15 so i tried to assign them 10.0.2.16 and after that when i tried to ping it said network unreachable..

> **terazen said:**
> 
Try checking on the dhcp server what mac address it sees when you boot up each OS.

Well, I am not sure about the dhcp server we are talking about but if its the one provided by the virtual box under the name of NAT then yes, they were assigned different mac ids.

I have checked it  using ifconfig on both systems. I have even tried restarting the dhcp service on both the machines so that they might get a different ip this time but things don't seem to change.

---

### Post by terazen on 2009-07-07
Read through some documentation so I could try to do this myself to test and it appears it's a bit complicated with virtualbox.  Apparently you need to use bridged mode instead of NAT through scripts you have to write.

[http://ubuntuforums.org/showpost.php?p=2723644&postcount=15](http://ubuntuforums.org/showpost.php?p=2723644&postcount=15)
[http://www.virtualbox.org/wiki/Advanced_Networking_Linux](http://www.virtualbox.org/wiki/Advanced_Networking_Linux)

Personally I'd just install vmware with one of their free linux licenses.  I haven't used this guide myself, but it may be worth a look.

[http://www.xgrr.de/wordpress/2008/02/25/convert-virtualbox-vdi-to-vmware-vmdk](http://www.xgrr.de/wordpress/2008/02/25/convert-virtualbox-vdi-to-vmware-vmdk)
Greg's post(#13) mentions how to do it using linux.

---

### Post by superprash2003 on 2009-07-08
did you check the DHCP range of your router? ideally , configuring virutal box to NAT should give all virtual machines a unique ip!!

---

### Post by shredder12 on 2009-07-08
> **superprash2003 said:**
> did you check the DHCP range of your router? ideally , configuring virutal box to NAT should give all virtual machines a unique ip!!

I am a little confused with this dhcp router. So, could you please tell me how should i check the range..??

---

### Post by terazen on 2009-07-08
The 10.0.2.15 ip address is what you get by default in virtualbox NAT mode.  It's not from his router.

---

### Post by superprash2003 on 2009-07-09
could you post the output of **ifconfig** from all your virtual machines.. if they are windows machines then post output of **ipconfig** .this is to know the ip addresses of all those machines

---

