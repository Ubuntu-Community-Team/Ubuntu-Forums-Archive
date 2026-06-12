---
title: "DNS doen't work Ubuntu 10.04"
date: 2010-06-06
forum: Networking &amp; Wireless
---

### Post by marcio123 on 2010-06-06
I want to connect to internet using my mobile phone (nokia 6300) via bluetooth

I paired phone with PC and then connected using networking manager (BT PANU)

In terminal 

ping 8.8.8.8 works great  (google dns)

ping any_web_address doen't work

so the problem is with DNS
I opened /etc/resolv.conf and noticed that there were 2 adresses that I could ping (?)  

I changed /etc/dhcp3/dhclient.conf 
prepend domain-name-address 8.8.8.8 

and it was added to recolve.conf after reboot but no change

I blacklisted ipv6 in modprobe -- no change 
(modprobe.d/blacklist add blacklist ipv6)

I can ping my phone 10.0.66.1   (/28)

any ideas ??

---

### Post by wojox on 2010-06-06
Try this

```
sudo cp /etc/resolv.conf /etc/resolv.conf.auto
```

```
gksudo gedit /etc/dhcp3/dhclient.conf
```

Add to dhclient.conf

```
prepend domain-name-servers 8.8.8.8,8.8.4.4;
```

Save, exit, and reboot.

---

### Post by marcio123 on 2010-06-06
I have done that (without 8.8.4.4) but no change :/


when I connect the same phone with usb cable it works without problems.

---

### Post by wojox on 2010-06-06
Then change it to this, your missing the semicolon:

```
prepend domain-name-servers 8.8.8.8;
```

Don't know other than that.

---

### Post by marcio123 on 2010-06-06
I used that:
prepend domain-name-servers 8.8.8.8; 

otherwise it wouldn't work (I wrote in 1 post that it was added in resolv.conf so it had been working)

---

### Post by dineshs on 2010-06-07
Did you try configuring DNS in NM ?ie
Right-click on the NM icon(two opposite arrows on top right) and then click on Edit Connections. 
Select the tab, wired 
select the ethernet connection you want and click edit(you can add the ethernet connection if not listed) 
select ipv4 
DNS 4.2.2.1 (or 8.8.8.8 )
then click apply

---

