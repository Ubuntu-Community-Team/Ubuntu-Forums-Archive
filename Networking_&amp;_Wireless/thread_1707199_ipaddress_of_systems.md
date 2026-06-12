---
title: "ipaddress of systems"
date: 2011-03-15
forum: Networking &amp; Wireless
---

### Post by Rakeshvijayan on 2011-03-15
Hi friends 

In  my working environment have 40 system .Its ip address is given manually

to connect each for lan connection .40 are not using ubuntu while other using 

windows .My question is there any package to trace ips of entire system 

its for reduce conflict

---

### Post by CharlesA on 2011-03-15
Why not just use DHCP? With 40 systems, it would make it way easier to manage.

---

### Post by Rakeshvijayan on 2011-03-15
> **CharlesA said:**
> Why not just use DHCP? With 40 systems, it would make it way easier to manage.

because I dont have dhcp server have only bsnl modem on there dhcp service have some 
problem for serving ip

---

### Post by wojox on 2011-03-15
> **Rakeshvijayan said:**
> 40 are not using ubuntu while other using windows .

So then their all using Windows? Is this a trick question? :P

---

### Post by CharlesA on 2011-03-15
> **Rakeshvijayan said:**
> because I dont have dhcp server have only bsnl modem on there dhcp service have some 
problem for serving ip
I see. IMHO If you have the infastructure for 40 machines, you should have a box running DNSmasq at least.

Anyway, in answer to yer original question, you can use nmap to scan a range of ip addresses, but it'll only really tell you if they are windows or linux boxes.

---

### Post by Rakeshvijayan on 2011-03-15
This not a trick question  ,here two admin one is  me .I am tring to remove windows and using linux but he love windows and he is burden for me he give the same ip of my linux 
machine to  the window .I need to monitor the ip of the entire system .....

how can I give the command in terminal using nmap my IP range starts from 192.168.1.1 to 192.168.1.255[SIZE=2]

 **sudo apt-get install nmap **[/SIZE]


After installation I using this command 

[SIZE=2]**sudo nmap -sP 192.168.0.1-254 **[/SIZE]

---

### Post by Rakeshvijayan on 2011-03-15
This is the result that I got  Thanks  friends for the quick replay

---

### Post by Rakeshvijayan on 2011-03-15
Another question I have is it possible to  recognize  which os using the ip 
and computer name

---

### Post by CharlesA on 2011-03-15
You'd have to have a list of the MAC unless you wanted to go to each machine.

That's why DHCP is so handy, it is way easier to keep track of which machine has which IP address.

EDIT: Or make up a list of what machine has which IP address, since they are all static.

---

### Post by Joeb454 on 2011-03-15
*Thread moved to **Networking & Wireless***

---

### Post by dineshs on 2011-03-15
> because I dont have dhcp server have only bsnl modem on there dhcp service have some problem for serving ip Most of the BSNL modems are DHCP enabled by default.Modems like Huawei MT882 ,MT841 etc are not, but you can enable it by entering the modem menu.Some modems are preset to a DHCP range of 192.168.1.2 to 192.168.1.32 ie for 31 machines.You can set the range for 40 machines.

---

### Post by Rakeshvijayan on 2011-03-16
Ok Tahnks

---

### Post by Rakeshvijayan on 2011-03-19
Sorry friends am back again with the same problem 

I tried to install nmap on ubuntu 10.10 I count find the package . How can I install nmap on my new pc..here is the result

---

### Post by gerowen on 2011-03-19
Angry IP Scanner may solve your problem, lots of built-in and customizable fetchers/launchers, and it's got a GUI.

**[Website](http://www.angryip.org/w/Home)**

[img]http://www.angryip.org/wiki/images/e/e4/Ipscan-linux.png[/img]

---

### Post by gerowen on 2011-03-19
> **Rakeshvijayan said:**
> Sorry friends am back again with the same problem 

I tried to install nmap on ubuntu 10.10 I count find the package . How can I install nmap on my new pc..here is the result

Nmap has a gui called "zenmap" that is in the repos.  Make sure you have the "Partners" repos enabled in your Software Center.

---

### Post by Rakeshvijayan on 2011-03-19
let me know is nmap is not available in repository I had installed in 10.04

---

### Post by Rakeshvijayan on 2011-03-19
This is the result that I got when I tried to install it from the preferred site

---

### Post by Rakeshvijayan on 2011-03-19
see the result of zenmap,,I think some thing is happend to my UBUNTU ,I cant update it from terminal .its ok from gui

---

### Post by gerowen on 2011-03-19
To run Angry IP Scanner, just download the JAR file, then right click it and open it with Sun Java 6 Runtime.  If you don't have Sun Java installed I recommend installing it because the openjdk is still pretty crappy in my experience.  It's also in the repos.  Here's a screenshot:
[img]http://adams-family.homeip.net/images/angry-java-open.png[/img]

To find zenmap in the repos try making sure you have all the right repos checked.  Click "Settings" then "Repositories".  Screenie:
[img]http://adams-family.homeip.net/images/synaptic-repos-menu.png[/img]

Make sure you have all of the correct repos selected.  Here's screenies of mine:
[img]http://adams-family.homeip.net/images/repos-tab1.png[/img]
[img]http://adams-family.homeip.net/images/repos-tab2.png[/img]

Then you may have to reload the packages to update the database with info from newly selected repos.  Here's a screenie of where the option is in synaptic:
[img]http://adams-family.homeip.net/images/synaptic-reload.png[/img]

---

### Post by Vishal Agarwal on 2011-03-19
In the terminal issue "arp". it will show you all  the connected network IP

---

### Post by Rakeshvijayan on 2011-03-21
I need  a monitoring tool ,To scan which ip is using more bandwidth on my network .
which one is the good for me .

Thanks

---

### Post by Rakeshvijayan on 2011-03-22
angry ip only show which machine is up it not showing the traffic of the network


please help me

---

### Post by conneco on 2011-03-22
I know this is a bit late in the day but, ubuntu can be a dhcp server for your network

And you wont be able to monitor bandwidth unless all traffic is passed through your ubuntu box, if you make it a proxy server for internet you can monitor, plus theres a packet sniffer called ettercap its really good at that stuff you can monitor connections bandwidth etc but if you don't have it setup on a proxy then it can only monitor connections between the box its installed on and the hosts communicating with that specific box,

It can by rights use arp poisoning to read all connections on the LAN without being a proxy but it will slow down your entire lan and  on 40 machines it will be dramatic, ARP poisoning is mainly used for hacking and its damm good at it.

---

### Post by gerowen on 2011-03-22
Two options I use.

1) Wireshark is a program that monitors all traffic on a particular network interface.  The only downside is that, if you are connected through a router or switch that doesn't blast all traffic over every port, you may not see everything that gets passed around.

2) DD-WRT firmware for wireless routers supports bandwidth tracking/monitoring, and even keeps bar graphs showing the total usage over the last day(s) and month(s).

---

