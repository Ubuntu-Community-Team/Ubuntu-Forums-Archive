---
title: "Computers With Static IP Addresses Are Being Assigned Dynamic IP's"
date: 2009-04-10
forum: Networking &amp; Wireless
---

### Post by umechanism on 2009-04-10
I have the following equipment in my home network:

Nintendo Wii - Wireless Connection
Laptop (Ubuntu 8.10 / XP) Wireless Connection
Desktop (Ubuntu 8.10) - Wireless Connection via Linksys USB network adapter
Desktop (Ubuntu 8.10) - Wired with Ethernet Cable
Router - Linksys WRT54G

All machines, except the Wii, are configured to have static IP addresses.  I configured the two Linux machines' network connections by editing their **/etc/network/interfaces** file and assigning the IP address.  

So, with all that said, what clued me in that I may have a network problem is the fact that pinging from one computer to the other over my LAN yields a "No Trace Route to Host" error.  So I Googled around looking for a solution and found some interesting comments over in the Linksys forums that were discussing the DHCP tables which prompted me to check mine.  These tables are located in the Linksys Router.  I have attached an image of my table.

In my case, the DHCP table should be empty except for the Wii video game because I did not assign it a static IP address.  All other machines in my network have been assigned static IP addresses and should therefore not appear in this table.  Yet, they do and I believe this is the cause of the "No Trace Route To Host" error that I get when pinging.

I'm a bit clueless as to what is going on or what I should do to fix it.  The effect of the situation is that I can not communicate with other Linux computers on my network.  I've tried SSH, FTP, Ping, etc...but I can not communicate with them but each of them can access the Internet.

I could use some help here.

Thanks!

---

### Post by steeleyuk on 2009-04-10
Two things to get started:

1) Delete the DHCP table entries for the statically assigned devices in the router.
2) To just double check something, ensure that an option along the lines of 'Wireless Isolation' or 'Access Point Isolation' is disabled, again within the router.

---

### Post by lisati on 2009-04-10
You might find that part of the solution will require some setting at the router end. 

After running into the occasional IP conflict I told my router to assign fixed IP addresses to the specific MAC addresses that the gear I normally use have, apply settings, and restart the connection at the PC end (the equivalent of XP's ipconfig /release followed by ipconfig /renew)

---

### Post by chili555 on 2009-04-10
May we have a peek at any of your **/etc/network/interfaces** on one of the machines that gets assigned a dynamic address? For comparison, here is my working-perfectly file:```
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet static
address 192.168.1.108
netmask 255.255.255.0
gateway 192.168.1.254
wireless-essid mylilrouter
wireless-key 096CxxxxxxxxxxxxxxxAFE open

#auto eth0
iface eth0 inet dhcp
```Some details have been obscured.

I also use static addresses outside the range of the DHCP server. In other words, if the DHCP settings are to start at x.101 and assign up to five addresses by DHCP, then my first static address starts at x.106.

---

### Post by umechanism on 2009-04-10
Sure thing:

```
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

#iface eth0 inet static
#address 192.168.2.114
#netmask 255.255.255.0
#gateway 192.168.2.1

auto wlan1
iface wlan1 inet static
address 192.168.2.114
netmask 255.255.255.0
gateway 192.168.2.1
wireless-key s:JENNY8675309
wireless-essid SWING

#auto wlan0

auto eth0
michael@Ubuntu:~$ 


```

---

### Post by umechanism on 2009-04-10
> **steeleyuk said:**
> Two things to get started:

1) Delete the DHCP table entries for the statically assigned devices in the router.
2) To just double check something, ensure that an option along the lines of 'Wireless Isolation' or 'Access Point Isolation' is disabled, again within the router.

Done.  No change as far as being able to ping the computer goes.

---

### Post by umechanism on 2009-04-10
> **umechanism said:**
> Sure thing:

```
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

#iface eth0 inet static
#address 192.168.2.114
#netmask 255.255.255.0
#gateway 192.168.2.1

auto wlan1
iface wlan1 inet static
**address 192.168.2.114**
netmask 255.255.255.0
gateway 192.168.2.1
wireless-key s:JENNY8675309
wireless-essid SWING

#auto wlan0

auto eth0
michael@Ubuntu:~$ 


```

Also, please note that in the above text, I specified a *_static_* IP address of **192.168.2.114** but the router's DHCP shows this computer with an IP address of **192.168.2.101** which was dynamically assigned. :confused:

---

### Post by umechanism on 2009-04-10
I restarted my network services and got an error message.  Does this give a clue?
```
sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          Error for wireless request "Set Encode" (8B2A) :
    SET failed on device wlan1 ; Invalid argument.
 * Starting portmap daemon...
 * Already running.
   ...done.
 * Starting NFS common utilities
   ...done.
mount.nfs: mount point /media/20gig does not exist
                                                                          * Stopping NTP server ntpd
[ OK ]
michael@Michael-Ubuntu:~$    ...done.
 * Starting NTP server ntpd
   ...done.

```

---

### Post by lensman3 on 2009-04-11
The /etc/init.d/network is broken!!!!

Anybody using it (network) needs to unhook from the rc?.d SYS5 setup using chkconfig.  Then setup the network using static IP address.  Unfortunately on my system I have to hand start the static scripts using "/sbin/ifup eth0".  I haven't figured out how to start it automatically during book.  I start the network at run-level 3 which is at the text login.  If you boot to run-level 5, it will take a while to bring up the X11-GUI interface because of TCP/IP timeouts.

"/etc/init.d/network" is not ready for prime time.  If anybody as a fix I'd like to know it.

---

### Post by chili555 on 2009-04-11
> **umechanism said:**
> Sure thing:

```
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

#iface eth0 inet static
#address 192.168.2.114
#netmask 255.255.255.0
#gateway 192.168.2.1

auto wlan1
iface wlan1 inet static
address 192.168.2.114
netmask 255.255.255.0
gateway 192.168.2.1
wireless-key s:JENNY8675309
wireless-essid SWING

#auto wlan0

auto eth0
michael@Ubuntu:~$ 


```

Your key, prepended with **s:**, tells us its an ASCII key. However, it's 12 characters and ASCII keys are either 13 characters, for 128-bit WEP or 5 characters for 40-bit WEP. I suggest you refine your key. I'd bet the error will disappear, as well.

Why it falls back to DHCP and connects is a mystery!

---

