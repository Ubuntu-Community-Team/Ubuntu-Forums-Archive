---
title: "Building the Bridge eth0 - eth1"
date: 2011-04-07
forum: Networking &amp; Wireless
---

### Post by DaltonXJ on 2011-04-07
OK I was going about connecting these to servers the wrong way..
 
Here goes.
As in my search for a gateway of somesort I ran across IPCop firewall.[http://www.ipcops.com/phpbb3/index.php](http://www.ipcops.com/phpbb3/index.php) . I was browsing thier forums and seen something called a bridge. so I googled it and lo and behold that seemed like what I needed... so here goes my atemp to Build the Bridge for the 2 servers.....
 
what i'll be useing. (if anyone has suggestions please chime in!)
 
First Server ( **Alaska** )
 
Extra Parts Box
Running: **Ubuntu 10.10 Server**
AMD 1ghz box
670+ mb
2 - 80gb WD HDD's
1 - NIC = eth0 dhcp from router
1 - NIC = eth1 out to second server
will be headless after setup..
 
Second Server ( **HPDL360G3** )
 
HP Proliant DL360 G3 Server
Running: **Ubuntu 10.10 server**
2 - Xion 3.6 Ghz Proc.
2 GB mem soon to be 4GB( waiting on E-Bay )
2 - 10/100/GB NIC's
NIC1 = eth0
NIC2 = down ( may use later to add another server )
2 - 76.2 GB HDD's running in Raid 5 status.( set by HP StartSmart Software )
 
------------------------------------------------------------------------------------------------------------
 
OK Here we go........
 
Ok so I have started with a clean slate.
 
brought down all controllers (eth0,eth1, **[COLOR=red]vbr0 <---(don't know what this is). <---found out this is for the virtual that installs[/COLOR]**

just left **loopback up**
 
so starting with entering these commands.
 
[EMAIL="xxxx@xxxxx:~$ifconfig"]xxxx@xxxxx:~$ifconfig[/EMAIL] eth0 0.0.0.0
 
[EMAIL="xxxx@xxxxx:~$ifconfig"]xxxx@xxxxx:~$ifconfig[/EMAIL] eth1 0.0.0.0
 
[EMAIL="xxxx@xxxxx:~$brctl"]xxxx@xxxxx:~$brctl[/EMAIL] addbr crossbridge
 
[EMAIL="xxxx@xxxxx:~$brctl"]xxxx@xxxxx:~$brctl[/EMAIL] addif crossbridge eth0
 
[EMAIL="xxxx@xxxxx:~$addif"]xxxx@xxxxx:~$addif[/EMAIL] crossbridge eth1
 
[EMAIL="xxxx@xxxxx:~$dhclient"]xxxx@xxxxx:~$dhclient[/EMAIL] crossbridge
 
OK going to see if it all works now.

---

### Post by DaltonXJ on 2011-04-07
OK so far good.
 
I can ping from HPDL360G3 to [www.google.com]("http://www.google.com") and to my laptop 192.168.1.x network.
 
I can ping from Alaska to [www.google.com]("http://www.google.com") and to my laptop 192.168.1.x network
 
I can ping both from my laptop. HPDL360G3 (192.168.1.x from dhcp) & Alaska (192.168.1.x from dhcp).
 
now to install a few goodies to beable to work from the laptop so they can be headless...
 
going to do a reboot test and see what happens....

---

### Post by DaltonXJ on 2011-04-07
ok did reboot and didn't come back online so a little more research and found out needed to add something to the interfaces file..
 
 
Add this info to the /etc/network/interface
 
sudo vi /etc/network/interface
 
[FONT=Courier New]# The bridge network interface(s) [/FONT]
[FONT=Courier New]auto br0 [/FONT]
[FONT=Courier New]iface br0 inet static [/FONT]
[FONT=Courier New]address 192.168.1.2 [/FONT]
[FONT=Courier New]network 192.168.1.0 [/FONT]
[FONT=Courier New]netmask 255.255.255.0 [/FONT]
[FONT=Courier New]broadcast 192.168.1.255 [/FONT]
[FONT=Courier New]gateway 192.168.1.1 [/FONT]
[FONT=Courier New]bridge_ports eth0 [/FONT]
[FONT=Courier New]bridge_fd 9 [/FONT]
[FONT=Courier New]bridge_hello 2 [/FONT]
[FONT=Courier New]bridge_maxage 12 [/FONT]
[FONT=Courier New]bridge_stp off [/FONT]
 
[FONT=Courier New]#auto eth0 [/FONT]
[FONT=Courier New]#iface eth0 inet dhcp[/FONT]

 
 
 
[FONT=Courier New]rebooting now to see if it;s gonna work...[/FONT]
 
[FONT=Courier New]And it works!!!! It's amazing what you can find on the net....[/FONT]

---

### Post by DaltonXJ on 2011-04-07
OK now to add webmin so I can do a little fixin on this systems

---

