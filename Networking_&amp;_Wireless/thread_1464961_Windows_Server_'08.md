---
title: "Windows Server '08"
date: 2010-04-28
forum: Networking &amp; Wireless
---

### Post by matrixorbital on 2010-04-28
ok, i have a very specific situation that i need help on.  I am a fairly ignorant Ubuntu user, though I have version 9.10 installed on my laptop.  For a school project, I need to create a Windows Server '08 client/server domain that includes a Linux client(wired).  

the network address i am using is 172.20.0.0
I subnetted this out with a subnet mask of 255.255.240.0
the subnet i am using for the linux portion is 172.20.112.0
I want my laptop to have the IP address 172.20.112.2
Server IP address is 172.20.32.2

I have all 3 of my cisco routers configured correctly.  I have no problem joining the domain with a Vista client, but I cannot seem to join the Linux machine.  
the 3 routers Fast Ethernet ports IP addresses are

[LIST=1]
[*]172.20.48.254(vista clients on this subnet)
[*]172.20.32.254(the server is on this subnet)
[*]172.20.112.254(linux on this subnet)
[/LIST]

I am not using DHCP, I am statically assigning IP addresses for this project.  I have tried using Likewise (GUI) to join the domain, but I get an error stating that the my laptop cannot locate the domain controller

I need help

[LIST=1]
[*]Assigning a static to the Linux machine (either through the command line or GUI)
[*]Join the domain through either likewise or some other means.
[*]you can email me @ [EMAIL="matrixorbital@msn.com"]matrixorbital@msn.com[/EMAIL] if you need more info
[*]the FQDN is Outdoorsman.com
[*]the name of the server is: outdoorsmanServer
[/LIST]
I have been using Ubuntu for 6 months as a casual user and I would really like to know more about Linux. Go ahead and respond if you will like you are talking to a total idiot.  I can speak idiot :lolflag:

Thanks in advance

---

### Post by Iowan on 2010-04-29
I found [this]("http://www.ghacks.net/2010/04/21/join-a-ubuntu-machine-to-a-windows-domain/") article about domain-joining. [This]("https://help.ubuntu.com/9.04/serverguide/C/likewise-open.html") one deals with Likewise.
Network Manager should be able to help with a static address - otherwise, use */etc/network/interfaces*... but NM doesn't always play nicely with "interfaces" file.

---

### Post by matrixorbital on 2010-04-29
> **Iowan said:**
> I found [this]("http://www.ghacks.net/2010/04/21/join-a-ubuntu-machine-to-a-windows-domain/") article about domain-joining. [This]("https://help.ubuntu.com/9.04/serverguide/C/likewise-open.html") one deals with Likewise.
Network Manager should be able to help with a static address - otherwise, use */etc/network/interfaces*... but NM doesn't always play nicely with "interfaces" file.

thank you very much...

---

### Post by redmk2 on 2010-04-29
> For a school project, I need to create a Windows Server '08 client/server domain that includes a Linux client(wired). 

I was under the impression that the forum does not help with users homework.  How are you going to learn if you don't go through the drill?

---

### Post by Iowan on 2010-04-30
From CoC:
> While we are happy to serve as a resource for hints and [COLOR="red"]for asking questions when you get stuck and need a little help[/COLOR], the Ubuntu Forums should not be thought of as a homework service. Please do not post your homework assignments expecting someone else to do it for you. Any such threads will be taken offline and warnings or infractions may be issued.  "Helping" is not prohibited, but where "a little help" becomes "do it for you" is somewhat gray.

---

