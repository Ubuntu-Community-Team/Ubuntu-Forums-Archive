---
title: "Connecting to an Ubuntu server"
date: 2010-11-09
forum: Networking &amp; Wireless
---

### Post by petersull on 2010-11-09
Hi, I am new to Ubuntu and not well versed in setting up devices, so looking for some clues.

I have a laptop with Ubuntu 10.10 and have been given a secondhand server device with Ubuntu 10.10 Server installed. I want to use device this for extra storage. The server is just a box about one third the height of a desktop pc case with a cd drive and hard disk but without a monitor or keyboard. It has all the usual sockets but no connections other than the mains lead.

I have the server, laptop and router all in the same room so the wifi signal should be at max strength. The server has been previously set up (by others) to work with my router/laptop ip addresses (provided by me), but until now the setup has not been tested. 

The server is switched on, and on the laptop I type into terminal 

'ssh adminuser@192.168.1.253'

(as per the instructions I have with the server device) and then I expect to be asked for a password which I have also been given. After the ssh command it says

'port 22: No route to host'

I have searched the various forums, and Youtube tutorials etc. but cannot find anything directly relating to my specific problem area.

Can someone please give me an idea how to progress further with this and gain access to the device?

Thanks in advance.

---

### Post by SeijiSensei on 2010-11-09
Most likely answer is that the machine you're trying to connect to isn't at 192.168.1.253 or that it's not running an SSH server.

In the terminal, try "ping 192.168.1.253".  Do you get replies?  If not, that's not the correct IP address.  In that case, I'd suggest you install **nmap** on the laptop from the Ubuntu repositories, then try running "nmap -sP 192.168.1.0/24" from the terminal.  This will scan the entire 192.168.1.x network and list all the visible devices and their IP addresses.

Let us know how it goes.

---

### Post by petersull on 2010-11-09
Thanks Seijisensai,

ping gives 'Destination host unreachable'

and this is the output of the following command...

nmap -sP 192.168.1.0/24

Starting Nmap 5.21 ( [http://nmap.org](http://nmap.org) ) at 2010-11-09 15:02 GMT
Nmap scan report for 192.168.1.1
Host is up (0.00092s latency).
Nmap scan report for pete-pc-u (192.168.1.42)
Host is up (0.00053s latency).
Nmap done: 256 IP addresses (2 hosts up) scanned in 2.51 seconds

It seems to have found my laptop and another address, what does this mean?

Best regards,
Pete.

---

### Post by pricetech on 2010-11-09
The "other" IP is your router.  Your storage box doesn't appear to be connected.

You said that power is the only connection on the storage box ??  You'll need a network connection of some kind to make it work.  Is it supposed to be wireless ??

---

