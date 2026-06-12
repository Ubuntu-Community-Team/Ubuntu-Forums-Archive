---
title: "Printing to networked printer"
date: 2012-06-25
forum: Networking &amp; Wireless
---

### Post by Crispness on 2012-06-25
hi

I'm moving a process from an old solaris box to a new ubuntu virtual machine.

Its a print process and on the solaris box the script uses this line


		lp -d $3 /pathtofile/$2.ps

$2 is the name of the project to pront
$3 is the name of the printer

The system here is a traditional windows network with the solaris box running as a black box in the corner. All the printers are connected to Win2003 and Win2008 servers so the $3 would tend to be in a format such as

dexitool:a4plainbw

where dexitool is the server name and a4plainbw is the print queue name.

The print queues are traditional windows print shares with LPD printing enabled.

And printing like this has worked fine for c. 10 years

But when I execute the same line on the new Ubuntu VM I get the following response
lp: The printer or class does not exist.

then I try
crispness@Julius:/usr/local/bin/sgl$ lp -d -D5 dexitool:a4plainbw /path2file/dk000001.ps

and I get

lp: Error - unable to access "dexitool:a4plainbw" - No such file or directory

crispness@Julius:/usr/local/bin/sgl$ ping dexitool
PING dexitool (192.168.0.101) 56(84) bytes of data.
64 bytes from dexitool (192.168.0.101): icmp_req=1 ttl=128 time=3.05 ms
64 bytes from dexitool (192.168.0.101): icmp_req=2 ttl=128 time=0.672 ms

etc

So it can see the server. But I'm not sure it can see the print queue.

lpstat -a returns nothing.

So what am i doing wrong?

Thanks

---

