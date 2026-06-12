---
title: "How to makle internet working on ubuntu (it's already working on windows)"
date: 2006-05-24
forum: Networking &amp; Wireless
---

### Post by sidy on 2006-05-24
Hi there,

I have internet broadband (TISCALI), that is working on windows xp normally.
But it is not working on ubuntu, same desktop (40hd windows 40hd ubuntu).

Tiscali doesn't supply IP address, so I don't know how to make internet working on ubuntu without IP address. (seams to be dinamic).

SO, CAN U TELL ME HOW TO MAKE INTERNET WORKING ON UBUNTU WITHOUT IP ADDRESS?](*,) 

Thank you.

---

### Post by jml on 2006-05-24
Have you asked your internet service provider for the ip address?  The reason they may not give you one is that most ISP's do not assign a fixed IP address for their customers.  They dynamically assign them ones.  If you don't already have one, I would suggest getting a small router.  Linksys, NetGear and other companies make them.  There are three advantages to using one.  A router makes a pretty inexpensive hardware firewall and adds a layer of protection to your computer.  It allows you to share your high speed connection with other computers, and it dynamically assigns ip addresses to all connected computers so it makes connecting to the Internet easier.  Check with your ISP to see if they recommend a particular type of router, but really any standard one should work.  You may also want to check out the networking troubleshooting guide thats pinned to the top of this sub forum.  Hope this helps.

Joe

---

### Post by Iowan on 2006-05-24
How is Windows doing it - fixed IP or DHCP?  If fixed, you can copy the address to Ubuntu... if dynamic, Ubuntu should be able to handle that, too.

---

### Post by Peter C on 2006-05-24
I also use Tiscali Broadband and have failed to get it working with the Sagem 800 Modem.

The same applies when using the Speedtouch 330 with Tiscali Broadband, I get an error message in Ubuntu.

Tiscali Broadband works fine using Mandriva 2006 and PCLinuxOS when using a Speedtouch 330.

Tiscali Broadband also works using the Sagem under Mandriva 2006.

Ubuntu looks good but I've not succeded in getting  a working internet connection, which is disappointing.

---

### Post by jvictor on 2006-05-26
How does u physically connect ? is it a network cable (RJ-45) or is it some USB stuff that u plug onto the box. Just giving ur ISPs name doesnt help; because its local to ur area or country.plz give us the following info

1) Wt is the physical connection type 
2) Do u have a router at your home

U **cant** connect to the internet without an IP , so u need to copy that IP and DNS windows uses, ( also let us know is windows statically configuring the IP or is it using DHCP )

Also give us the o/p of

$less /etc/resolv.conf

$route

---

### Post by claytonc on 2006-05-26
Hi,

You should also check if your modem connects using a PPPoE connection. If it does, there is no need to assign a local IP to your NIC card. However an IP from your ISP is required. If you have a speedtouch modem (530, 530v6 etc) you can use the *Easy Setup* to configure the modem connect automatically.

---

### Post by aces21 on 2006-06-05
I use a sagem usb modem to connect to tiscali using dapper. I wrote a howto for setting it up [here]("http://ubuntuforums.org/showthread.php?t=144468")

Give it a go and post back if you have problems.

---

