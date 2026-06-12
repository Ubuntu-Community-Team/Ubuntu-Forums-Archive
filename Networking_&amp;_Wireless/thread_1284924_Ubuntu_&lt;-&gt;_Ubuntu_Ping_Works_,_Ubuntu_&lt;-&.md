---
title: "Ubuntu &lt;-&gt; Ubuntu Ping Works , Ubuntu &lt;-&gt; Windows - no Ping"
date: 2009-10-07
forum: Networking &amp; Wireless
---

### Post by michael_r on 2009-10-07
Dead Ubuntu users

I have 2 computers, connected through a router (Netgear router).
In computer 1 I have Ubuntu installed.
In computer 2 I have dual boot - Windows and Ubuntu.

If I use Ubuntu in both computers the network works properly.
If I use Ubuntu and Windows there is no ping.

There is no firewall installed in windows, no windows firewall enabled, nothing .. :/

The IP address of computer 1 is 192.168.2.3
The IP address of computer 2 is 192.168.2.212
Mask is same in both computers 255.255.255.0

Any help would be appreciated,

Thanks
Michael

---

### Post by prshah on 2009-10-07
> **michael_r said:**
> Dead Ubuntu users I don't think they can give you much of a response... ;)

> **michael_r said:**
> 
In computer 1 I have Ubuntu installed.
In computer 2 I have dual boot - Windows and Ubuntu.
If I use Ubuntu in both computers the network works properly.


There is clearly a network misconfiguration in the Windows system. If it is wireless, then it is probably not connected to the access point, with a manually assigned IP address.

To confirm, post your windows ipconfig command output; click start-Run, and give the command ```
cmd.exe
```, then, in the black screen that opens up, give the command```
ipconfig /all
``` and post back the output.

---

### Post by michael_r on 2009-10-07
> **prshah said:**
> I don't think they can give you much of a response... ;)


hehe .. whooopsy ...  :)

here is the ipconfig /all output:

C:\WINDOWS\system32>ipconfig /all



Windows IP Configuration



        Host Name . . . . . . . . . . . . : AUDIOPC

        Primary Dns Suffix  . . . . . . . :

        Node Type . . . . . . . . . . . . : Hybrid

        IP Routing Enabled. . . . . . . . : No

        WINS Proxy Enabled. . . . . . . . : No



Ethernet adapter Local Area Connection:



        Connection-specific DNS Suffix  . :

        Description . . . . . . . . . . . : NVIDIA nForce Networking Controller

        Physical Address. . . . . . . . . : 00-11-09-92-8C-20

        Dhcp Enabled. . . . . . . . . . . : No

        IP Address. . . . . . . . . . . . : 192.168.2.212

        Subnet Mask . . . . . . . . . . . : 255.255.255.0

        Default Gateway . . . . . . . . . : 192.168.2.212

        Primary WINS Server . . . . . . . : 192.168.1.2



Michael

---

### Post by prshah on 2009-10-09
> **michael_r said:**
> Primary WINS Server . . . . . . . : 192.168.1.2

This is the only thing that seems out of order (different subnet). Try disabling (clearing) this and see if the problem goes away... if it doesn't, put it back.

Post back if you want more details on how to clear this setting.

---

