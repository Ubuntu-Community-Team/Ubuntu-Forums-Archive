---
title: "dmesg eth0 ipv6 duplicate address detected"
date: 2010-02-18
forum: Networking &amp; Wireless
---

### Post by jhardydj on 2010-02-18
As the title says, I have been getting that message in dmesg and also not able to ping anything.  If I boot into say clonezilla, I get the same thing when trying to bring my network up (eth0)... if I move the network cable to a 9.10 box sitting beside the 9.04 box it works.  So it appears it is only on this machine (no matter what OS).  Oh one more thing, If I plug directly into the modem it seems to grab an IP address and everything seems to work, but not with the router.  

I am not using network manager, and this only started happening when I have been messing around trying to get my wireless working.  

I notice when i do a dhclient eth0 , it does the "configuring devices" etc.. then where it shows the loading samba it hangs before assigning my static IP.  If I am connected directly to the modem , it does not hang and the process is pretty quick.

I hope that is enough info to get some help.. Oh , when dmesg shows ipv6 duplicate address detected, what address is it referring to?  What can I check?

Thanks :)

---

### Post by Iowan on 2010-02-18
I can see that it won't be long until I will need to learn IPv6... About all I might suggest is to check **ifconfig -a** to see what addresses are in use.

---

### Post by katie-xx on 2010-02-18
[SIZE=2][COLOR=Blue]Hi
You might want to take a look at this article
[/COLOR][/SIZE][http://timesinker.blogspot.com/2009/11/karmic-ipv6-global-address-problems.html](http://timesinker.blogspot.com/2009/11/karmic-ipv6-global-address-problems.html)
[SIZE=2][COLOR=Blue] Kate[/COLOR][/SIZE]

---

### Post by jhardydj on 2010-02-18
I am using 2.6.30 jaunty .. does this still apply?  and I am not using ipv6 either , only ipv4.  where did this ipv6 come into play all of a sudden? My box was perfectly fine last week :(

Thanks again for the help

Jay

---

### Post by Iowan on 2010-02-18
> **jhardydj said:**
>  and I am not using ipv6 either , only ipv4.  where did this ipv6 come into play all of a sudden?Ahhh - I thought you were setting up IPv6 network (sorry). IPv6 has been in Ubuntu for awhile - although most of us haven't really started using it (and some have disabled it...).

Wonder if wired and wireless somehow have same IPv6 address?  But modem or router shouldn't matter. wired/wireless/router - two of them the same???

---

### Post by jhardydj on 2010-02-18
I have my cable modem plugged into the router.. and my jaunty box wired , but does have a wireless card in it that usually just disable.

Jay

---

