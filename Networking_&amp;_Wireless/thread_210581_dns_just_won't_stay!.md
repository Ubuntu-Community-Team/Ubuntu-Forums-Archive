---
title: "dns just won't stay!"
date: 2006-07-07
forum: Networking &amp; Wireless
---

### Post by linuxpimp on 2006-07-07
Hi all

So i took the plunge and migrated a business machine from 'another Linux OS' to "Dapper" and am VERY happy.

I ma running Dapper 6.06 32bit on an amd64 bit machine.

I connect to the www via another machine/gateway nad the gateway machine's IP is the default DNS which is bad.

I change this manually via >> System>>admin>>network but these settings do not stay, they work until i logout/reboot.

Please assist.

LP

---

### Post by the guest on 2006-07-07
Step 1;  Go to System=>Administration=>Synaptic Package Manager and make sure you do not have the packages"Resolv", "Pump" or 'DNSMasq" installed. If you do completely remove them(make sure to completely remove, not just remove).

Step 2;  Go to your terminal and type 
```
gksudo gedit /etc/resolv.conf
``` 
and change whatever is there with;
nameserver xx.xxx.xx.xxx
nameserver xx.xxx.xx.xxx
(replace the x's on the top line with your primary DNS, and replace the x's on the second line with your secondary DNS).

Step 3; Go to your terminal and type
```
gksudo nautilus
```
and find the /etc/resolv.conf icon and right-click go to properties then permissions and tick all the read box's and all the execute box's. Now you have to lock that in so it doesnt reset. Go to your terminal and type;
```
chattr +i /etc/resolv.conf
```
Reboot your system and enjoy the net!

THE GUEST;)

---

### Post by linuxpimp on 2006-07-07
Duh!!!

Way too much time using GUI! I missed the basics!

Thanks

LP

---

### Post by the guest on 2006-07-07
No worries, and the program you have to completely remove is "Resolvconf" not Resolv.

---

