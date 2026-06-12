---
title: "Router and Cable internet connecting problems"
date: 2006-04-26
forum: Networking &amp; Wireless
---

### Post by norm on 2006-04-26
Hi,

I looked through all the other posts but did not see any that seemed related to my problem.

I am using an SMC Barricade router to connect to a cable box, Terayon TJ715. 

When Ubuntu starts my eth0 board seems to be running correctly but I cannot connect to the internet. If I shut off the cable box and the router and then restart them eth0 then seems to allow connection to the internet.

I have this same problem when I boot into WindowsXP after being in Ubuntu and have to shut down the router and cable box and restart them. I never had this problem before between Suse Linux and Windows. I am assuming there is a problem in Ubuntu seeing the mac address needed to connect to the cable.

Any suggestions on what to try?

Thanks,
Norm

---

### Post by mips on 2006-04-27
Drop the interface then bring it back up again (ifdown ifup) without switching anything off and see what it does.

---

### Post by norm on 2006-04-27
Hi mips,

I tried the ifdown and ifup, but that did not allow the connection. If I power it off and back on it usually works.

I did discover that it is a DSN problem as when it is not working I can reach sites by entering the numbers instead of the name.

What is strange is that the settings all seem to be the same working or not working. When I check the resolv.conf it shows the router as the nameserver each time and I can ping the router and internet I just cannot ping a name address.

Norm

---

### Post by mips on 2006-04-27
norm,

Ok, thx 4 mentioning the DNS issue.

Could you try and manually configure your resolv.conf with your ISPs DNS server IP addresses and remove your router address.

If this does not work try disabling IPv6:
```
sudo mv /lib/modules/$(uname -r)/kernel/net/ipv6/ipv6.ko /lib/modules/$(uname -r)/kernel/net/ipv6/ipv6.ko.bak

sudo depmod -a
```

---

### Post by norm on 2006-04-27
Hi,

I had already disabled Ivp6 and will try adding the other DNS servers to the resolv file. I will have to reboot and see if I can stop it working again. :p 

Norm

---

### Post by norm on 2006-04-27
Hi mips,

Changing the nameserver to the IPS server seems to work. Now how do I get this to stay in the resolv.conf since it seems to be re-written each time I start.

Thanks again,

Norm

---

### Post by norm on 2006-04-27
mips, thanks for all the help. I found another thread that showed how to edit the dhcp client file and added the IPS name servers to that and they are now showing in my resolv.conf file and the internet seems to be working just fine.

Thanks again,
Norm

---

### Post by mips on 2006-04-28
norm,

A few people have experienced your problem. I have seen the fix for the dhcp client somewhere but can't remember the link.

Could you please post a link here so if others also have the problem they would know where to look.

Thanks
mips

---

### Post by norm on 2006-04-28
Hi mips,

I was not able to find the thread again, but this is what I did.

sudo gedit /etc/dhcp3/dhclient.conf

Scroll down till you find the line #Prepend domain-name-servers remove the # sign if it is present and also remove your router address if present and then add your name servers separated by a comma followed by a semi-colon.

Example:

68.10.16.25,68.10.16.30,68.9.16.30;

Save the file and then reboot and you should see the new name servers in the resolv.conf file.

I hope this makes sense as I am still new to ubuntu and there is probably a way to run the configuration without rebooting, I just don't know it.

Norm

---

