---
title: "Remote Connection"
date: 2008-12-09
forum: Networking &amp; Wireless
---

### Post by esculayd4724 on 2008-12-09
Hi,

I am trying to set up a remote connection between my laptop which runs Ubuntu, and my desktop which runs on XP.  I tryed to connect from the terminal server client on Ubuntu but it didn't work for me. How do I connect to my desktop properly from my Ubuntu computer?  

Thanks.

---

### Post by jonobr on 2008-12-09
Hello

Assuming  your network is not the problem (ie you can ping from ubuntu to xp)
Have you enabled remote desktop on your xp machine?
I think its disabled by default.

Once done you should be able to connect using rdp on the ubuntu machine, unless you have something blocking the RDP port.

If you have a second machine running windows It would be worth your while checking with that.

---

### Post by esculayd4724 on 2008-12-09
I am going to go check to see if XP is blocking it, but I don't think it is.  Also, I am connected to my router which my desktop is the main computer for, so both computers have the same ip address. How can I make that work?

---

### Post by jonobr on 2008-12-09
Hello

Im not sure what your saying,

Are you saying that you have to machines using the one IP address?
Ie when you do ifconfig -a on your ubuntu terminal window is that the same as ipconfig on the windows box?

If so, thats probably your problem,
IP addresses need to be unique.
Its like having two houses on a street with the same address,

Mr posty wont be a fan of yours:p

---

### Post by MagnumGI on 2008-12-10
Here is what I would check for:

1. Can you ping the XP host?
2. Is port 3389 listening on the XP host?
3. Is you XP firewall blocking you?
4. Are you logging in to the RDP session using the XP administrator credentials, or as someone who is a member of the localgroup "Remote Desktop Users"?

---

### Post by superprash2003 on 2008-12-10
presuming its under a LAN..hopefully this guide should help [http://prash-babu.blogspot.com/2008/05/how-to-remote-control-windows-pc-from.html](http://prash-babu.blogspot.com/2008/05/how-to-remote-control-windows-pc-from.html)

---

