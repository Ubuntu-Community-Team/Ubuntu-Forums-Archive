---
title: "Problem with IP over serial"
date: 2009-04-15
forum: Networking &amp; Wireless
---

### Post by lectivo on 2009-04-15
Hi;

I have a problem trying to communicate two computers through a null modem cable and IP.

First at all I have to say that I am able to communicate these computers through serial using the minicom and/or GTKterm, and because of that I have checked that there is no problem neither in the cable nor in the interfaces.

The problem is when I want to communicate these computers using PPP. When I try to communicate them using ppp, I use the following command in both computers:

pppd -detach nocrtscts lock <Local IP:Remote IP> <Serial Port> <BitRate> 

I use nocrtscts because I have found that the computers are unable to communicate though serial when using hardware flow control. The values of Serial port and BitRate were tested using minicom.

When I launch this command the PID is created, but the PPP0 interface is not created. I also have checked that the computer is not trying to send any information through the serial port. 

But the most strange thing is that the message saying that the ppp0 interface is created and it is trying to connect the LCP appears when I have the Xubuntu 8.10 virtualized in an VMware which is NOT (important thing)connected to the serial port of the computer, because when I connect the guest OS COM to the computer's COM, this message doesn´t appear to me and the ppp0 interface is not created, that is, I have the same behaviour than in the case of the host computer.

I have read a lot in internet but I am unable to find the solution. Even I have a similar problem when I try to communicate them using SLIP. In case anyone could help to me ...

Thank you very much

Lectivo

Thanks

---

