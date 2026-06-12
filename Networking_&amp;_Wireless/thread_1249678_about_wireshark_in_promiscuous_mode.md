---
title: "? about wireshark in promiscuous mode"
date: 2009-08-25
forum: Networking &amp; Wireless
---

### Post by Riddermark on 2009-08-25
Just got wireshark on 9.04 and have not been able to capture any packets.  I ran as root and had a few questions about promiscuous mode.  I assume that it is a security risk to run wireshark as root do to the promiscuous mode that will allow all traffic to move through your wireless card.  Is this promiscuous mode changed back to default configuration after wireshark is shut down or packet transfer is stopped?  I was just wondering if promiscuous mode stays in effect after the program is shut down?

thanks

K

---

### Post by jonobr on 2009-08-25
Hello


Couple of responses here,


> I assume that it is a security risk to run wireshark as root do to the promiscuous mode that will allow all traffic to move through your wireless card. 

Not sure its a security risk. Running as root means you have to be an admin to sniff packets. So it makes sense that this function is protected from normal users. You can run wireshark as a normal user, but will not have the ability to sniff packets.


> 
Is this promiscuous mode changed back to default configuration after wireshark is shut down or packet transfer is stopped? 


No i believe if you close wireshark and restart, promisc mode will still be checked 

> 
I was just wondering if promiscuous mode stays in effect after the program is shut down?


As mentioned above, yes I believe it is

> 
thanks

K


Hope this helps

---

### Post by Riddermark on 2009-08-25
So if I use wireshark in promiscuous mode and close the program/reboot the machine am I still in promiscuous mode?  If so, do i have to use the ifconfig command to change it back to default?  Also, how would you check to see if you are in promiscuous mode or not?

Thanks

K

---

### Post by jonobr on 2009-08-25
Hello


Im wondering if we are on the same page here.

Im attaching a capture of promisc mode on my eth adapter.
You can unckeck the box and save/apply.
(capture->select interface and then options.)
Apologies if Im misunderstanding the question

---

### Post by Riddermark on 2009-08-25
Yes, that is the same screen that I used, with the capture in Promiscuous mode box checked.

---

### Post by Riddermark on 2009-08-25
Let me apoligize for not being clear with my original question.  I was thinking that since wireshark needs to run as root, that maybe the changes it makes to run in  promiscuous mode stay that way.  I was concerned that after running wireshark in promiscuous mode that it would stay that way, if I was running wireshark or not.  Kind of like the same way that changes are made to IPtables with Firestarter.  The changes are made the first time you run the Firestarter and stay that way, wether you have firestarter running or not.  Sorry about the confusion and thanks for your help.  

thanks

K

---

