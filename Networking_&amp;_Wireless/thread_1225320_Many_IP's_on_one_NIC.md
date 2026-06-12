---
title: "Many IP's on one NIC"
date: 2009-07-28
forum: Networking &amp; Wireless
---

### Post by KillRob on 2009-07-28
[COLOR=black][FONT=Verdana]Hello,[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]I want to use Ubuntu Server 9.04 as a Firewall.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]We got 2 Subnet's from our ISP. The first is /29 and the second is /24 in size.[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]Now I want do add about 15 IP's to the external NIC and use DNAT to forward the traffic to our DMZ.[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]Assigning 9 IP's is not a problem. I simple use[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]sudo ifconfig eth1 add xxx.yyy.zzz.2[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]sudo ifconfig eth1 add xxx.yyy.zzz.3[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]sudo ifconfig eth1 add xxx.yyy.zzz.4[/FONT][/COLOR]
[COLOR=black][FONT=Verdana].[/FONT][/COLOR]
[COLOR=black][FONT=Verdana].[/FONT][/COLOR]
[COLOR=black][FONT=Verdana].[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]But this does not work for more than 9 IP's, right :confused:[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]With a SUSE-Based old Firewall you can add several address lines to the config file.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Ubuntu does not allow this...[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]Thank you[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Robert[/FONT][/COLOR]

---

### Post by comandrei on 2009-07-28
```

sudo ifconfig eth1:virtual ipadress 

```

---

### Post by KillRob on 2009-07-28
Thanks for the answer but this only works from eth1:0 to eth1:9...
eth1:10 does not work anymore ...

---

### Post by KillRob on 2009-07-29
I double checked everything and now it works.
I'm not shure what I have changed but now my eth1 has 20 IP's
 
Thanks a lot

---

