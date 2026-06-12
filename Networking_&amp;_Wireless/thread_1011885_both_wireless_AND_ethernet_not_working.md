---
title: "both wireless AND ethernet not working"
date: 2008-12-15
forum: Networking &amp; Wireless
---

### Post by endlessness on 2008-12-15
hello, 

I have the latest ubuntu (8.10), that I installed as dual boot in my acer 5920 that had vista factory-installed..  The vista was showing some problems connecting to the internet so I thought I might as well check linux out, and got this one..

It all looks perfect but the internet just wont work. It detects my hardware perfectly, and even detects the network and says ' connected' , but I cant open any webpage or pidgin or anything

In windows, also neither were working, but then I changed the dns configuration of the ethernet to one that was working with another computer in the house, and it works.. I tried the same thing with wireless and it didnt work.  In Ubuntu, howhever, using the same DNS does not work even in the ethernet!

I used the graphical network options, I am new to linux in general so I dont know yet the commands in terminal. I selected the option (automatic dhcp address only)  or something of the sort, to just put the dns.. It didnt work

what else can I do? What can I test? thanks a lot


(btw the wireless router is d-link  DI-624... It works with other computers here, just not with mine.. And my computer does work, including the wireless, in a public hotspot near the house, so its not a hardware problem either)

---

### Post by razy60 on 2008-12-15
If you open network manager does the information look correct when compared to another pc you have at home, i.e ip address(should have a different final digit XXX.XXX.X.?) the rest of the info should be the same. if you are using wireless does the info match that of your home router or not,
 if you go to system-network- is auto ticked,
 in wireless have you entered the correct security information. is it using your home network info and not the wifi hotspot details.
just a few things to check before delving into things like terminal

Raz

---

### Post by endlessness on 2008-12-15
ok wireless is working

I forced an ip and reset the router before trying.. now it works (both on vista and linux)  thanks a lot!

---

