---
title: "browsers wont load webpages wiht static IP but network works"
date: 2009-12-04
forum: Networking &amp; Wireless
---

### Post by kostaben on 2009-12-04
Hi Forum,

So this is what is happening: If i use DHCP everything works fine. If i assign a static IP , Firefox and Midori wont load any page (server not found, cannot resolve hostname) while i am sure there is active internet connection cause i see all these from a remote desktop.

Any ideas?

---

### Post by sikander3786 on 2009-12-04
I have not ever tried to assign a Static IP to Ubuntu. However I used to assign my Windows desktop a Static IP. What happened was that the IP that was assigned by DHCP to my NIC, if I assigned the same IP as a static one to my Workstation, Internet Connection used to go on sweetly. If I assigned some other IP that was not assigned by DHCP to my NIC, the Internet Connection will hang up.

Try to check you DHCP assigned IP and then set the same as static one. By the way why do you want to assign a static IP? Might be there is some other solution.

---

### Post by kostaben on 2009-12-04
The static IP i assign is the same with the one DHCP assings. And an update: i can ping my router but can not ping google!

---

### Post by sikander3786 on 2009-12-04
Well I can't help you any more as I haven't been throught this before. Why do you want to set a static ip? Are you using two networks?

---

### Post by hardfire_avk on 2009-12-04
ok! this maybe the problem. You have to give your DNS Settings too. just try to get to google's website with it's IP address. it will work, most probably.

To setup DNS settings
System—>Administration->Networking
Click on DNS tab
then input your DNS

restart your interface then. This should work.

---

### Post by kostaben on 2009-12-04
Well, the truth is because i can´t stand something not working as it should in my computer :) which is mostly cause i am playing with linux.
On the other hand i got two computers one Ubuntu and one fedora and i want remote desktop for both (obviously they are in the same lan).
Another reason is to be able to leave an open port for Deluge.

---

### Post by kostaben on 2009-12-04
Yes! i put the DNS and everything is fine. Thank you.

---

