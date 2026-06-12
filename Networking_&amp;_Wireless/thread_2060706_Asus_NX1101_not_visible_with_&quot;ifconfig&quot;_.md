---
title: "Asus NX1101 not visible with &quot;ifconfig&quot; in Ubuntu 12.04"
date: 2012-09-20
forum: Networking &amp; Wireless
---

### Post by fitzpatrickcote on 2012-09-20
Hi,
i'm not able to get my 10/100/1000 network card Asus Nx1101 (IP Plus Corp IP1000) working in Ubuntu 12.04 Server. When i type ifconfig i only get my other 10/100 network card that i've installed temporarily. If i type lspci, i see that the network card is detected. 

When i try to install the drivers for this card i'm getting the error:

"gcc -D__KERNEL__ -DMODULE -O -Wall -Wstrict-prototypes -I/usr/include  -DUSE_IO_OPS  -D_COMPAT_WITH_OLD_KERNEL  -c -o ipg_main.o ipg_main.c
In file included from ipg_main.c:159:0:
ipg.h:101:26: fatal error: linux/config.h: No such file or directory
compilation terminated.
make: *** [ipg_main.o] Error 1"

I think that the linux/config.h does not exist anymore in Ubuntu 12.04 ... is this right ? Do i have something to change in the files ?

On my other system with Ubuntu 11.10 this network card is working well.

Thank you for your help,
Patrick

---

### Post by einonm on 2012-09-21
Can you post the output of 'sudo lspci -vv'?

---

### Post by fitzpatrickcote on 2012-09-21
Hi einonm, here is the log in attachment.

Thank you for your help,
Patrick

---

### Post by steeldriver on 2012-09-21
Hi Patrick, I think your initial diagnosis is correct - that file has been removed from the more recent kernel headers

You *may* be able to get the module to build by either removing that #include OR by faking the file (I don't think it contains anything that is not elsewhere - web searches seem to indicate it was just a wrapper for autoconf.h at the point when it was removed) 

HOWEVER there may be a whole lot of other problems considering the source seems to be out of date - are you sure that's what you want to do? are there no other options to get a more up-to-date driver?

---

### Post by einonm on 2012-09-23
> **fitzpatrickcote said:**
> Hi einonm, here is the log in attachment.

From the log, it looks like the driver (ipg) is already installed and running (the output of 'lsmod' should confirm this), so the problem lies elsewhere, assuming that the driver is working correcly. So I wouldn't worry about building a driver.

ifconfig would not show the interface if it were 'down'. To see if the interface is available, run 'cat /proc/net/dev/' from the command line. You should see a list of all interface names in the leftmost column...apparently all the trendy people are now using 'ip link show' to do the same, as 'ip' is being pushed to replace 'ifconfig'.

Assuming that the interface is called 'eth0' (it may not be!), you can bring up the interface by running 'sudo ifconfig eth0 up'.

---

### Post by fitzpatrickcote on 2012-09-25
Hi,
thank you steeldriver and einonm for your help. 

einonm, you are right, the driver is installed and running. I managed to bring the interface (eth1) up. But now, i am facing a new issue:
I had to add the following lines to the /etc/network/interfaces file: 
"auto eth1
iface eth1 inet dhcp"

I can get the ip address from the dhcp server and ping myself, but I can't ping the router or any other addresses on my network or on the internet. If I modify the interfaces file to :
"auto eth1
iface eth1 inet static
address 172.x.x.x
netmask 255.255.255.0
gateway 172.x.x.x"

and then restart /etc/init.d/networking I get :
"RTNETLINK answers: No such process
RTNETLINK answers: File Exists
Failed to bring up eth1."

If I do "ifconfig" my static ip is assigned to my interface eth1, I can ping myself but i can't ping the router or any other address. And if I bring back my interfaces file to :
"auto eth1
iface eth1 inet dhcp"

and restart the /etc/init.d/networking ... and type ifconfig ... (this is very weird) my static ip stay assigned to my interface eth1. I can ping myself and the router but I can't ping any other internet address. The name is resolved but i receive :
"From mynameserver.local (eth0.ip.address) Destination Host Unreachable". --(I think this is just the response from my router that is trying to talk with myservername (who is linked to eth0 ip address) ??)--

If I restart again the networking service, I get the dhcp ip address and I am back to the start of the loop.

Should I change something else to another file to get my eth1 interface working properly ?

Thank you very much,
Patrick

---

### Post by fitzpatrickcote on 2012-09-28
Finally, i got it working. It was my fault. 

First, i setted 2 gateway in my interfaces configuration. 
Second, i forgot to put my 10/100 network card down. So now, this is working very well.

Thank you for your help,
Patrick

---

