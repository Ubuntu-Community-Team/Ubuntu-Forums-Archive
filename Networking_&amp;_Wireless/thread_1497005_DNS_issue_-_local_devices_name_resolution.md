---
title: "DNS issue - local devices name resolution"
date: 2010-05-30
forum: Networking &amp; Wireless
---

### Post by Teknor on 2010-05-30
In my home network, My Ubuntu 10.04 LTS (fully up to date) is having trouble being able to ping other computers by their computer names instead of by their IP#s.  I've checked over the settings of the router (D-Link that provides wired and wireless connectivity, DNS, Gateway, etc.) and I'm pretty sure it is set correctly.  My Ubuntu system is a dual-boot (Ubuntu and XP), the other computers are all XP except for one which is running Windows 2000 Pro.  All the other computers are able to ping each other by name, and can ping this one by name when it's in XP or when it's in Ubuntu. 

But this computer (when in Ubuntu) cannot seem to ping the other computers by name.  Some it can be pinged by name from the Ubuntu system if I include the .local to the name, but others do not.  I have checked and compared the network settings on each of the computers to make sure they were set identically (only the computer name is different).  All of the XP systems are DHCP configured, The Win2000 is set static and is also reserved at the router.  NONE of them have any of the computers listed in a hosts file.  I want to avoid editing hosts files if I can.

There are seven computers in all.  Only the Ubuntu has difficulty pinging other computers by name.

What should I check?  What can I set?  Please help.  I would like to know what it is that I'm missing.

---

### Post by capscrew on 2010-05-30
> **Teknor said:**
> In my home network, My Ubuntu 10.04 LTS (fully up to date) is having trouble being able to ping other computers by their computer names instead of by their IP#s.  

Do you really mean ping by COMPUTER (NetBIOS) name?  The DNS (host) name is different than the Windows COMPUTER (NetBIOS) name.  
> 

I've checked over the settings of the router (D-Link that provides wired and wireless connectivity, DNS, Gateway, etc.) and I'm pretty sure it is set correctly.  
What are the DNS settings in the D-link for?  Does it list the local hostnames?  Or is it for setting the ISP (WAN) side DNS servers?> 

My Ubuntu system is a dual-boot (Ubuntu and XP), the other computers are all XP except for one which is running Windows 2000 Pro.  All the other computers are able to ping each other by name, and can ping this one by name when it's in XP or when it's in Ubuntu. 

But this computer (when in Ubuntu) cannot seem to ping the other computers by name.  Some it can be pinged by name from the Ubuntu system if I include the .local to the name, but others do not.
It really sounds like you hava multiple naming services running at the same time.  The .local is most likely from Ubuntu running Avanhi.  This service claims the .local DNS suffix.  See [**_here_**]("http://avahi.org/wiki/AvahiAndUnicastDotLocal").

It also sounds like you have Windows Share discovery configured on your Windows computers.  This would allow you to ping them by name but it does not have to be through DNS, rather through NetBIOS calls.

Ubuntu natively does not understand NetBIOS.  But if you install Samba for file sharing then it will.  I run Samba for file sharing and can ping all hosts from all of my Ubuntu hosts.  If I turn off Network Discovery (NetBIOS) on my Windows hosts I loose the ability to ping them.  So I know I am using both types of name resolution.


> 

I have checked and compared the network settings on each of the computers to make sure they were set identically (only the computer name is different).  All of the XP systems are DHCP configured, The Win2000 is set static and is also reserved at the router.  NONE of them have any of the computers listed in a hosts file.  I want to avoid editing hosts files if I can.

There are seven computers in all.  Only the Ubuntu has difficulty pinging other computers by name.

What should I check?  What can I set?  Please help.  I would like to know what it is that I'm missing.
Check to see what name resolution services is really running on at least on the Ubuntu host and one of the Windows hosts.  

Beside carefully looking at what you have configured, I would install Wireshark on both.  With Wireshark you will be able to see what is being used.  You will also be able to see if/when Ubuntu is trying to resolve a Windows name.

---

