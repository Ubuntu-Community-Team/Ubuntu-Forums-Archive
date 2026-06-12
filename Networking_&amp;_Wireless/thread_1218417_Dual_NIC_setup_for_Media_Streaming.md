---
title: "Dual NIC setup for Media Streaming"
date: 2009-07-20
forum: Networking &amp; Wireless
---

### Post by yogiman.uk on 2009-07-20
Hello

I wonder if someone could offer me some advise.

I used to use Windows with 2 nics in my pc:-

NIC 1 (1GB) was wired into my switch and gave me access to my local network and my router for Internet.

NIC 2 (100MB) was wired using a crossover cable to my DSM320 Media Streaming Box.

The method worked very well as the software for the DSM320 allowed me the option of selecting the NIC that it would use for the Media Streaming.  Thus my media was not affected by other jobs I was doing on the computer.

Now I obviously use Ubuntu.  I am confused!  I have tried setting NIC 1 as DHCP from my router and NIC 2 to a fixed IP and neither my Media streaming NIC nor my normal network nic seem to work.

The best example of this is that when both nics are connected I lose internet?

Can anyone tell me how I am to get both nics working and retain my internet connection.

Internally the nics are setup as follows:-

NIC 1

IP: 192.168.1.65
Subnet: 255.255.255.0
Gateway: 192.168.1.254

NIC 2

IP: 10.0.0.1
Subnet: 255.0.0.0

If anyone feels like a soldier of fortune and you think you can help!

Thanks


Yogiman!

---

### Post by superprash2003 on 2009-07-21
post output of** route -n** and **ifconfig **from the terminal .are you able to ping the networks of both interfaces?

---

