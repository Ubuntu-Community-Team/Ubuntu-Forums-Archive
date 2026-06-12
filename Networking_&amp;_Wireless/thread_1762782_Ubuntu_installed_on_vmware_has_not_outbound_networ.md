---
title: "Ubuntu installed on vmware has not outbound network"
date: 2011-05-19
forum: Networking &amp; Wireless
---

### Post by toolmania1 on 2011-05-19
Hello,

I installed Ubuntu 11 onto VMWare Server 2.  

I am able to ping my Ubuntu installation from my desktop computer.  However, I cannot ping out from the VMWare image running Ubuntu. 

I cannot hit any internal or external pages coming out of the VMWare image running Ubuntu using the Firefox browser.  

In VMWare, I have the NIC set to Bridged.  

I ran a traceroute and it appears that I was hitting our network router and even going a little further to some att.net site.  So, in the traceroute, I was getting out to some part of the internet.  Also, there were a bunch of "no" and "reply" that fill up in the traceroute results.  

I have tried both DHCP and a known good static ip for my nic in Ubuntu.  For each of those, Ubuntu says that they are connected.  Neither of these have made a difference as I still could not hit internet sites in Firefox and could not ping out to internal or external addresses.

I checked to see if ufw was on by default and it was not.  I ran sudo ufw status I saw that it was inactive.  

We started to install VMWare tools also, but got stuck where we were told we need the path to the C headers because it was using the gcc compiler at /usr/local/gcc.  That directory does not exist though.  

I know this was a lot of information.  I can clarify if need be.  Any ideas for me to try?  I also run Ubuntu at home, so I am not a newb to Ubuntu.  I can follow ideas if you have any for me to try.

---

### Post by toolmania1 on 2011-05-19
Also, under System -> Administration -> System Monitor, Total Sent is 206 Kib and Sending shows "0 Bytes /s".  Receiving is showing constant activity of several hundred bytes / s with a total of 4.6 MiB.

---

### Post by Nyrobie on 2011-05-19
I ran into that same C headers from when I was using fedora I fixed it by pointing it directly to the file with the headers. Although it still wasn't able to install the file sharing capabilities =/. 

Don't know what to say about the network though other than I use the NAT and that works great I still haven't wanted to bother doing the research to get bridged to work when NAT works fine.

---

### Post by toolmania1 on 2011-05-19
Nyrobie, 



Thanks for the reply.  I set the NIC to NAT in VMware, and presto, magically I also have internet.  I do like to learn, but, I feel the same as it is not worth trying to find out why bridged is not working in this case.  Anyways, thanks.



> **Nyrobie said:**
> I ran into that same C headers from when I was using fedora I fixed it by pointing it directly to the file with the headers. Although it still wasn't able to install the file sharing capabilities =/. 
 
Don't know what to say about the network though other than I use the NAT and that works great I still haven't wanted to bother doing the research to get bridged to work when NAT works fine.

---

