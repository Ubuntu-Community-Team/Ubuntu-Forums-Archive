---
title: "wireless"
date: 2010-05-11
forum: Networking &amp; Wireless
---

### Post by Hogeyfur on 2010-05-11
Just installed Xubuntu 10.04 today and cant get my wireless USB adapter to work 

First thing i did was the same steps i used to make my last linux install to work (Ubuntu 9.10)

here is what i did 
```

sudo -s -H

cd etc/modprobe.d

nano blacklist.conf

I blacklisted these modules in the blacklist.conf file

blacklist rt2800usb
blacklist rt2x00usb
blacklist rt2x00lib 

sudo su 
echo rt2870sta >> /etc/modules
exit

```i then rebooted

My wireless adapter now shows up but will not connect when i enter my password. I just get the connection in process loop and eventually it will ask me for my password again

I had a quick look in the etc directory and cant see the modules directory 

should the modules directory be there or is it under a differrent name in Xubuntu?

any help would be most appreciated

  P.S. the steps i follwed were given to me from a more experianced linux user and i have no idea how they came about the information to make my wireless work for Ubuntu 9.10

---

