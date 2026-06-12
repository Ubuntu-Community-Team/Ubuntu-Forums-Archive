---
title: "Trying to find 2nd public ip address on network"
date: 2010-02-15
forum: Networking &amp; Wireless
---

### Post by carsonrose on 2010-02-15
HOPEFULLY SOMEONE CAN HELP, IM LOST!!

I have a CENTOS server that I can ssh into using one of my public IP addresses I have memorized. I have to RDP into my windows server 2008 machine, but I don't know the public IP address of that part of the network. If I can ssh into my CENTOS server, which has a direct feed from my T1 (it goes from my T1 modem directly to my CENTOS server box), I can get into other Linux machines on the network. The other machines are also running into the switch, but the caveat is that I have my AT&T DSL going into a router with fire wall (port 3389 open and routed to the windows server 2008 machine) and then going into the same switch. 

So, my question is, since I have forgotten my other public IP, how would I find that IP from the command line of the CENTOS server box? 

I dont think it matters, but I am using an Ubuntu 9.10 on my home machine. I ssh into the CENTOS machine from the command line on the home Ubuntu machine. 

Can anyone tell me a command or group of commands that would tell me the public IP address of the DSL connection on my network?

---

### Post by ant2ne on 2010-02-15
Most DSL modems use dynamic IPs. That is, it can change. You could find out the IP of the device connected to the DSL device. Then run nmap on its subnet to find out the IP of the DSL device then log into the DSL device and find out the IP of its other interface. But that sounds like a lot of work.

If I were you I'd look into dyndns (dynamic dns) at dynddns.com.

---

### Post by carsonrose on 2010-07-14
> **ant2ne said:**
> Most DSL modems use dynamic IPs. That is, it can change. You could find out the IP of the device connected to the DSL device. Then run nmap on its subnet to find out the IP of the DSL device then log into the DSL device and find out the IP of its other interface. But that sounds like a lot of work.

If I were you I'd look into dyndns (dynamic dns) at dynddns.com.

Done and done...... Update... I got a static IP address for the DSL, installed a PF Sense Firewall and configured the DYNDNS client..... I still cant get the Dyndns to work with the pf sense and Ive managed to pretty much lock myself out of the network from out side the building... :)

In this world, if it isnt one thing its another..... :D

---

