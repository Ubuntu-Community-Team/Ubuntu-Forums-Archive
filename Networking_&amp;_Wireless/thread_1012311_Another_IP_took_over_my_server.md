---
title: "Another IP took over my server"
date: 2008-12-15
forum: Networking &amp; Wireless
---

### Post by b18b on 2008-12-15
I am running a windows network and have an Ubuntu 7.10 box setup for web applications, 4 websites, and a few other functions.

The Router/firewall is a SonicWall with IP 192.168.0.1, the active directory server (192.168.0.2), a windows terminal server on 192.168.0.3, and the Ubuntu box is on 192.168.0.4.

Then the rest of the computers and printers.

The 192.168.0.2 (windows AD) is setup as the DHCP server and has a fixed range of 192.168.0.150-250 for serving.

Today I started getting telephone calls that the at Ubuntu box was no longer accessible and the users were getting some sort of login.  I did a quick check and it was no longer online.  A quick nmap showed that port 80 was the only one open and it also returned some sort of Adaptec controller (not exactly where and how I got this).

To my recollection there is nothing on my network using an Adaptec controller of any kind.  

I do have an installation of an NEC voip server being put in, but it should be using IP's around 192.168.0.50-120.  I have not yet accessed this box but when I disconnected it from the network, all seemed to clear up.  No one was in today to service this unit or made any changes and it has been up for a week or 2.

I guess my question is how can I go about tracking down where this other device came from? I have a call in to the tech that is putting in the NEC voip system.

This is a bad thing since this webserver is heavily relied on for mission critical applications.  Are there any suggestion on how I can prevent this from happening again? 

If it is as easy as putting on a device with the same IP as another device, any rogue individual with a network port can take down my server.

Any thoughts or suggestions?

---

### Post by lensman3 on 2008-12-15
>I am running a windows network and have an Ubuntu 7.10 box setup for web applications, 4 websites, and a few other functions.

>The Router/firewall is a SonicWall with IP 192.168.0.1, the active directory server (192.168.0.2), a windows terminal server on 192.168.0.3, and the Ubuntu box is on 192.168.0.4.

Then the rest of the computers and printers.

The 192.168.0.2 (windows AD) is setup as the DHCP server and has a fixed range of 192.168.0.150-250 for serving.

This IP range "192.168.0.0/24" is for one of the unroutable Class C IP address.  This number is reserved and can only be used behind a firewall.  It's lucky that it has worked this long. It sounds like to me somebody outside your networks Sonicwall is using 192.168.0.2 too and grabbed the IP number.

1) I would suggest you move your IP range up to something like 192.168.143.0-255.  On NAT devices you can spoof the address range by guessing that the IP range behind the NAT is 192.168.0.0-255. Nobody changes the factory default which was 192.168.0.0.

2) Set up the computers on your network to have an IP address that is associated with NIC number.  This is more work for the admin but is more secure.

3) I think what is happening is that your IP provider has another DHCP server and that one is winning.  You may have done a zone transfer to the outside server and now it is the "boss".

4) You might try blocking DHCP requests on your sonicwall.  I think that a DHCP request is 0.0.0.0 so you need to set up a firewall that blocks requests from the Internet.

Hope this helps.

---

