---
title: "No Internet Access Through Ubuntu but FTP/SSH/APACHE Works"
date: 2010-03-15
forum: Networking &amp; Wireless
---

### Post by zap1989 on 2010-03-15
Hey guys,

I'm relatively new to Linux.  I have a new webserver and bought a dual-port NIC for it ([http://www.startech.com/item/ST1000SPEXDP-Dual-Port-PCI-Express-Gigabit-Ethernet-NIC-Network-Adapter-Card.aspx](http://www.startech.com/item/ST1000SPEXDP-Dual-Port-PCI-Express-Gigabit-Ethernet-NIC-Network-Adapter-Card.aspx)).  

I'm having problems installing the r8169/r8168 drivers (not sure exactly which it is) for this card because they won't compile (using the drivers you can download from the link I provided).  I have a 2.6.x kernel (don't remember exactly the version, one of the later ones though).  I followed the instructions in the README step by step.  When attempting to compile (using "make clean modules" under root), I receive a bunch of errors about the "net_device" structure not having certain parameters.

I did some research, and all I could find was info about how the latest versions of 2.6.x kernel no longer support compatibility with the net_device object.  With that, I'm not sure what to do!  I've contacted tech support and am waiting to hear back.

Now, I have another problem. After trying things to solve that issue, I've plugged back into the original built-in network port.  I can connect to the server through the website (apache), FTP, SSH, etc; however, if I physically go on the server and try to open any website through Firefox or use any of the Ubuntu software package tools, it acts as if it has no internet connection.  (If I ping a site, ie google.ca, I do receive a response).  I can also connect to the modem/router of my ADSL connection.

If you have any ideas for either problem, do let me know!  Thanks!


Edit:

One thing to note, I did try running a "patch" script provided by [http://acm.cse.lehigh.edu:8080/~jhw204/hardy-r8168]("http://acm.cse.lehigh.edu:8080/%7Ejhw204/hardy-r8168")  to help solve the dual-port NIC problem.  But that didn't seem to do much (I restarted with connection to the card but got no internet and couldn't connect to modem).

Edit 2:
More specifically, there error looks like

'struct net_device' has no member  XXXXX

---

### Post by zap1989 on 2010-03-15
Ok, so the internet problem seems to have mysteriously fixed itself.

However, I still am unable to use the new dual NIC card. 

Using the patch-script from the link I provided, it does compile and work, but when I restart it isn't connecting.  From System > Administrator > Network tools, my network devices consist of LO, eth0, eth1, eth2_rename

Only eth0 has an IP.  This is because right now I have my LAN plugged into the built-in network port, and an outside line plugged into one of the ports on the dual-port NIC card.

Do I need to do something special to enable this?  What is the "eth2_rename"?

---

### Post by zap1989 on 2010-03-15
Solved!

So,  newer drivers were needed.  The latest for my particular card were found on Realtek's website.  This allowed me to compile the drivers.


Then, you must go to /etc/network/interfaces and make sure there is:
[FONT=monospace][I]
[/I][/FONT]auto eth1[I]
iface eth1 inet dhcp

[/I]for  every connection you have (ie eth0, eth1, eth2, etc)

---

### Post by Iowan on 2010-03-15
[[SOLVED]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")?
There's some question as to whether Network Manager still works with */etc/network/interfaces*. Are you successfully using Network Manager and  */etc/network/interfaces* concurrently?

---

### Post by zap1989 on 2010-03-17
I"m new to Linux.  I don't think I actually have Network Manager?

But, although I am able to use my dual NIC card now, and I can connect to my webserver from outside...if I actually go on the server and try to use the internet (FireFox, "wget", updates, software manager, etc)...it gets no internet connection.  But I can ping domains.  Any ideas for that?

---

### Post by Iowan on 2010-03-17
Most recent Desktop releases of Ubuntu (since Hardy Heron - 8.04) come with Network Manager - dunno about Xubuntu, Kubuntu, etc. Servers don't include a desktop, so they still use */etc/network/interfaces*... but desktop can be added.

---

### Post by zap1989 on 2010-03-18
Yeah, I checked, and Network Manager definitely isn't installed.  I'll have to try installing manually and see where that gets me

---

