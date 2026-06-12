---
title: "Wireless issue on DHCP renewal"
date: 2005-12-22
forum: Networking &amp; Wireless
---

### Post by greenway on 2005-12-22
On several PC's I am using WLAN usb adapters with a SiS163u chipset and every few hours they loose connectivity to the WLAN and therefore internet. After looking at the syslog, this seemed to happen after the DHCP lease expires; the NIC then keeps on broadcasting requests for a new lease but doesn't get one.

Then, after running ifdown and ifup it just gets a new lease. First I thought this problem was caused by the DHCP server, however PC's running with other USB adapters don't seem to have this problem.

Any suggestions anybody, getting kinda tired of manually getting a new network configuration from the server...

tnx

-mattijs

---

### Post by greenway on 2005-12-23
Wow, all those reactions! Great! Thanks all!

---

### Post by djgenesis on 2005-12-23
Are you using ndiswrapper with your USB? Are you connected directly to the internet or are you using a router?

---

### Post by kedmanee on 2005-12-29
You could simply let the DHCP-Server give a longer leasetime. Or any reason not to do so? Your people aren't endless in office.

---

### Post by 0MG on 2005-12-29
Is hardcoding IPs an option?

It's more of a bandaid than a cure, but it might help depending on what your network looks like.

---

### Post by greenway on 2006-01-03
Thanks for replying guys; giving out longer leases is not going to work because our linksys WAP can only give out leases for max one day.

Going for a pure static network is not a good idea since we have many guests coming over who want to use the internet and don't feel like wasting my time providing them which network information all the time. And letting the DHCP server give out a few static IP's to the hosts which are always on the network is also not going to work since the linksys acts as the DHCP server and it doesn't have this option.

I thinking about letting the linksys WAP only function as gateway and setup another hosts as a decent DHCP server.

---

### Post by kedmanee on 2006-01-05
Do those clients run Linux, you could have run a script checking the connection after a period and do the ifup command when necessary.

---

### Post by greenway on 2006-01-10
[QUOTE=kedmanee]Do those clients run Linux, you could have run a script checking the connection after a period and do the ifup command when necessary.[/QUOTE]

Thanks for your input! For now I put the troublemaking PC's on a static IP and have another server handing out DHCP leases for other hosts connecting to the network. 

If this happens again in the near future I will defenitely try a bash script solution.

---

