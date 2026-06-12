---
title: "Network manager 0.7"
date: 2008-12-22
forum: Networking &amp; Wireless
---

### Post by quikone8 on 2008-12-22
Does anyone know if this is fixed yet?  For some reason w/o it I cannot get online, even with reconfiguring the file.  The problem seems to be that with NM only dhcp works.  If I remove NM I can only see eth0 but seemingly no connectivity.  Also eth1 does not show up and I get a phantom vnet0, I am wondering if vnet0 is part of my problem.

Any help would be appreciated,

Ron

---

### Post by quikone8 on 2008-12-22
bump

---

### Post by bab1 on 2008-12-22
See [http://www.arachnoid.com/linux/NetworkManager/index.html]("http://www.arachnoid.com/linux/NetworkManager/index.html")

Please wait 24 hours before bumping.  :-)

---

### Post by quikone8 on 2008-12-23
Thanks for both replies.  

The first one especially with the link is very good in its explanation of what NM is doing.

And thanks for the for the bump advice.

---

### Post by superprash2003 on 2008-12-23
presuming you solved your problem , please mark thread as SOLVED under thread tools..

---

### Post by quikone8 on 2008-12-23
> **superprash2003 said:**
> presuming you solved your problem , please mark thread as SOLVED under thread tools..

I don't know that this is solved.  Is the problem with NW 0.7 and the fact that it will not hold static ip's solved?  Also, how about the problem with extremely slow speed if one or more nic's are active?

---

### Post by superprash2003 on 2008-12-24
you should probably try installing old network manager.. [http://prash-babu.blogspot.com/2008/11/how-to-enable-roaming-mode-in-ubuntu.html](http://prash-babu.blogspot.com/2008/11/how-to-enable-roaming-mode-in-ubuntu.html) .. follow till step 4 ..
 there have been issues with the new network manager..although people have claimed that it has been fixed..

---

### Post by superprash2003 on 2008-12-24
you should probably try installing old network manager.. [http://prash-babu.blogspot.com/2008/11/how-to-enable-roaming-mode-in-ubuntu.html](http://prash-babu.blogspot.com/2008/11/how-to-enable-roaming-mode-in-ubuntu.html) .. follow till step 4 ..
 there have been issues with the new network manager..although people have claimed that it has been fixed..

---

### Post by frankelr on 2008-12-24
Tried to replace problematic NM .7 by following the roll back instructions
given several times in this thread.... apt-get tells me I already have the  
most recent NM version.  I sure would like some help on how to roll back
to the earlier NM release....

thankx 
bob

---

### Post by frankelr on 2008-12-24
Other posts have shown how to edit /etc/network/interface
to get things working and also how to edit this file to setup a static ip.
The down side of this is that while networking "works: you still have a red triangle on your network manager icon (which basically tells you that NM is not in command of networking) and NM also does not give any information about your connection) if you still need to use static ips, as I do, this is a work around for lan's with many home routers.  My router is an old 
D-link 604, it and my other routers allow you to bind an ip address to a specific mac address.  If you enable this feature ubuntu still thinks is has dynamic addressing and the new NM shows no errors, while the router ensures that your computers also receive the same ip address assignment!

Hope this works for you, I'm moving on to my next "bug"

Bob

---

### Post by quikone8 on 2008-12-26
Thank you everyone that helped with this.  I had gotten so frustrated by this little piece of software and the fact that it had the entire system down that I opted to roll back to 8.04.  So now at least I have my email server back.  

If anyone has some recommendations, I would really like to avoid getting NM back again, so when the Update Manager has available updates, what should I avoid?

---

