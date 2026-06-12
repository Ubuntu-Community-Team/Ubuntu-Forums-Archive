---
title: "Can't access Windows Network when I could before, (Maybe IP issue)"
date: 2010-09-09
forum: Networking &amp; Wireless
---

### Post by willoww39 on 2010-09-09
Hi,

New user in the last couple of weeks, (Ubuntu 10.04, GNOME Desktop).

I installed it on my relatively new DELL Vostro 1220 laptop and the boot time from pressing the button to web access across wireless has gone from 2.30, (W7), to 30 seconds.  Wow - how valuable is this to me!

But, I had to have my cable modem changed last week due to a fault and had to use IPCONFIG/IPRELEASE commands within Windows, (talked through the process by my service provider), and now my Ubuntu laptop can see the web but can't access the Windows network - it knows it's there, (at least the icons are there under Networking).

I've tried a couple of commands I've read about but no luck.

It won't take me long to reinstall it, but I would rather solve the issue if I can.

Any ideas??

Thanks in advance.

---

### Post by sikander3786 on 2010-09-09
What happens when you try to access any of the computers in the Windows Networks. Does it give an error message? What is it? Seems like an authentication issue to me.

Can you ping a Windows box from Ubuntu?

---

### Post by willoww39 on 2010-09-09
The error is: Unable to mount location. Failed to retrieve share list from server.

Sorry, I don't know how to ping any of my Windows machines.

---

### Post by sikander3786 on 2010-09-09
Go to System > Administration > Network Tools. Go to the ping tab, type Windows box ip address and see if there is any response.

[COLOR="Red"]**Edit:**[/COLOR] Also take a look here. It might help.

[http://ubuntuforums.org/showpost.php?p=7157868&postcount=12](http://ubuntuforums.org/showpost.php?p=7157868&postcount=12)

---

### Post by willoww39 on 2010-09-09
Ubuntu transmitts 5 and receives 5 back, 100% successful packets

---

### Post by willoww39 on 2010-09-09
Thanks, tried the changes suggested in [http://ubuntuforums.org/showpost.php...8&postcount=12]("http://ubuntuforums.org/showpost.php?p=7157868&postcount=12"), but it just takes longer to come up with the same error.

The whole system was fine until I changed the cable modem and released the IP address.

---

### Post by sikander3786 on 2010-09-09
Are there any firewalls? Is it a cable modem that you replaced or a router? If it is a router, it might have a built-in firewall that is limiting your access.

---

### Post by willoww39 on 2010-09-10
It was just the cable modem that was replaced, everything else including the router is the same, just rebooted after the Windows IPCONFIG /RELEASE.

I've just turned off the firewall on the Windows box I'm trying to access and it makes no difference.

---

### Post by willoww39 on 2010-09-10
I just checked all of the IP addresses that access my router and have found that the IP address is the same on the Windows boot as it is the Ubuntu boot.  Could this be causing the router a problem?

I get full network access with the Windows boot, but none with Ubuntu, but I do get web access.

---

### Post by jpepin on 2010-09-10
This sounds like a simple IP address assignment issue.  

If you have 2 different machines with the same IP address, on the same network, at the same time, you will definitely have conflicts. 
 
I assume you're router is set up to assign IP addresses via DHCP, and that both machines are set up to be assigned IP addresses (ie they are not assigned static IP addresses).  

My first step in troubleshooting would be to turn off both computers, reboot the router, and then restart each computer. 

If you do have a static IP address assigned to either machine, make sure it doesn't conflict.

---

