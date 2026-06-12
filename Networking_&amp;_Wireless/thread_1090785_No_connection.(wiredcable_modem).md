---
title: "No connection.(wired/cable modem)"
date: 2009-03-08
forum: Networking &amp; Wireless
---

### Post by codya517 on 2009-03-08
I was in another thread before, but I guess it stumped people. I know it stumped some linux users over irc and the like. So I figured I'd make my own thread this time and see if anyone can figure it out.

The cable modem is not equipped with a router. It's connected to a windows(xp) machine and works just fine. "Always On" Local Area Connection. But when hooked up to my Linux machine (new to linux)It says it connects if I input all the data manually but it doesn't... If I set it to auto DHCP, it hangs and disconnects at "requesting address..." blah blah.

And to throw in another issue, if I accidently leave in the ethernet cable (cat5e) it automatically reconfigures my connections to "ifupdown (eth0)" which is a "read only" file and cannot do anything and will not allow me to recreate the "auto eth0" connection. In order to fix this, I need to reinstall Ubuntu. I'll post the terminal outputs for both machines. (ifconfig and ipconfig /all)

Windows IP Configuration
        Host Name . . . . . . . . . . . . : xxxxxxxxxxxx
        Primary Dns Suffix  . . . . . . . :
        Node Type . . . . . . . . . . . . : Hybrid
        IP Routing Enabled. . . . . . . . : No
        WINS Proxy Enabled. . . . . . . . : No
        DNS Suffix Search List. . . . . . : atlanticbb.net
Ethernet adapter Local Area Connection 2:
        Connection-specific DNS Suffix  . : atlanticbb.net
        Description . . . . . . . . . . . : Intel(R) PRO/100 VE Network Connection
        Physical Address. . . . . . . . . : 00-16-76-0F-EC-A9
        Dhcp Enabled. . . . . . . . . . . : Yes
        Autoconfiguration Enabled . . . . : Yes
        IP Address. . . . . . . . . . . . : 207.255.211.80
        Subnet Mask . . . . . . . . . . . : 255.255.248.0
        Default Gateway . . . . . . . . . : 207.255.208.1
        DHCP Server . . . . . . . . . . . : 207.255.0.137

And here is the ifconfig in it's current state (weird ifupdown crap)

eth0      Link encap:Ethernet  HWaddr 00:1f:d0:d3:fa:69  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:4048650427 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:219 Base address:0x8000 

eth0:avahi Link encap:Ethernet  HWaddr 00:1f:d0:d3:fa:69  
          inet addr:169.254.10.46  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:219 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:498 errors:0 dropped:0 overruns:0 frame:0
          TX packets:498 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:31316 (31.3 KB)  TX bytes:31316 (31.3 KB)

Any ideas? The issue seems to be the fact that it's not getting any communication from the dhcp server. But I have entered everything in manually and checked dozens of times and still nothing.

thanks for any help in advance.

---

### Post by Iowan on 2009-03-08
It may not help - but *shouldn't* hurt... try cycling power to the modem (unless this causes the problem you mentioned). Sometimes they "lock onto" the MAC address of a specific machine.

---

### Post by codya517 on 2009-03-09
Hmmm it didn't work. Nothing actually seemed to happen at all.

any other ideas? I'm stumped.

---

### Post by Iowan on 2009-03-09
Well, so much for the quick-fix...
The "read only" file seems odd - what is the name (and have you tried deleting it with **sudo rm filename**?  
The avahi address means DHCP didn't work... but you knew it had a problem.  Unfortunately, the address avahi hands out (thus the "successful connection message) is in a subnet of it's own (thus the lack of access to anything else).
There are several threads containing "Waiting for DHCPOFFER"... but I haven't seem many solved.  Seems like ACPI can cause issues... There are some posts about turning it off in GRUB - I'll need to look around for one (some).

---

### Post by codya517 on 2009-03-10
well i didn't try to delete it through the terminal. But Reinstalling ubuntu fixed it, as it wouldn't let me add eth0 back to it. Oddly enough I did a test and tried to reproduce that issue and now I can't heh. I'm getting frustrated with the lack of cooperation from linux and this modem.

---

### Post by codya517 on 2009-03-13
So I fixed it or should I say it fixed itself.

I tried to use a router, to get around the fact the modem doesn't want to play nice with another computer. The first router, the modem did not like and did the same thing to my linux comp. But the second router I tried worked absolutely flawlessly. Plug n use and it connected without any problems at all on auto dhcp. hehe

the router? a Linksys WRT150N Wireless-N. It has wireless capabilities but also routes wired ethernet as well :)

---

