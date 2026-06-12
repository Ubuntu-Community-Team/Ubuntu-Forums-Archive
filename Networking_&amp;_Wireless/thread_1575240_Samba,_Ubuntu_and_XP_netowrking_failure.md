---
title: "Samba, Ubuntu and XP netowrking failure"
date: 2010-09-15
forum: Networking &amp; Wireless
---

### Post by DrLunk on 2010-09-15
Here is an overview of my system, consisting of two computers, a D-Link router and a ZyTel 660 DSL modem/router.  Computer One (Comp1) is dual booting XP and Ubuntu 8.04. Computer Two (Comp2) is booting only Ubuntu 8.04.  For years, I had been running and networking both of these computers with XP.  Both have been using static IPs. In order to have Static IPs and forward certain ports, I had to configure the D-Link router as an Access Point and use the ZyTel as the defacto router for the network. 
 
The Static IP info for the two computers is: 
Comp1
IP ADR    192.168.2.20 
Subnet    255.255.255.0 
Gateway   192.168.2.1 
DNS       208.67.222.222     208.67.220.220  

Comp2 
IP ADR    192.168.2.21 
Subnet    255.255.255.0 
Gateway   192.168.2.1 
DNS       208.67.222.222     208.67.220.220  

The name of the workgroup is the default WORKGROUP.  On Comp2, I have used Nautilis to share a single test directory called "TEST2"; under /home/drlunk As Comp1 is a dual boot configuration, in XP I used Windows Explorer to share a test directory on a NTFS volume called "Test-NTFS".  Booting into Ubuntu on Comp1, I used Nautilus to share a ditectory called "TEST1" under /home/drlunk.  On both computers, I have Samba installed under Ubuntu.  

Here is what I have experienced from the first day.  When Comp1 is booted into XP and using Windows Explorer, I can access Comp2 and transfer files with no problems. However, from Comp2, pulling up Nautilis I cannot access the XP machine.  I forget the precise error message at the moment.  

When Comp1 is booted into Ubuntu, no network access is possible.  From either machine, I get the error: "Unable to mount location: Failed to retrieve share list"  I have been researching this for days and tried various edits of smb.conf, hosts and such with no success.  I even tried doing away with the Static IPs and reverted back to DCHP.  It keeps coming back to from XP, I can access Ubuntu, but I can't get Ubuntu to access XP and I cant get the two Ubuntus to network at all.  For the moment, I have restored smb.conf and hosts back to their default conditions, restoring the Static IPs and using the XP boot on Comp1 to handle any file sharing between the two machines.  This is hardly ideal.  

As an aside, both machines in either XP or Ubuntu can access the Internet with no problems.  Ideally, I want these two machines to be able to share files whether it is XP to Ubuntu or Ubuntu to Ubuntu.  Also, as this is a local network, I do not want to be bothered with having to type in a password to transfer files between my two machines.  Any help or insights will be greatly appreciated.

---

### Post by DrLunk on 2010-09-15
Fellas, looking through [your exchanges]("http://ubuntuforums.org/showthread.php?t=1567896") reads like this should all be fall down simple.   Unfortunately, I've been fighting these various issues for 2 weeks with no success.   Here is my setup.  I have two computers (call them Comp1 and Comp2), connected together with a D-Link router (configured as an Access Point) and a ZyTel 660 DSL modem/router.  The configuring of the D-Link as an Access Point was necessary so that the ZyTel would actually handle the routing functions and so that I could setup Static IPs for both computers and forward some ports.  This configuration has worked flawlessly for 2 years with both computers running XP.    For Comp1, here are the parameters for the Static IP: 192.168.2.20 255.255.255.0 192.168.2.1 208.67.222.222 208.67.220.220    And for Comp2: 192.168.2.21 255.255.255.0 192.168.2.1 208.67.222.222 208.67.220.220   The WORKGROUP for the network is wretchnet and is the only 'special entry' in smb.conf on both machines.    Comp1 is configured as a dual boot of XP and Ubuntu 8.04.  Comp2 boots only Ubuntu 8.04.  To date, if I boot Comp1 into XP. I can access shared directories on Comp2.  However, Comp2 cannot access the shared directories under XP.  And when both computers are booted into Ubuntu, no shared directories on either computer can be accessed.    In Nautulis, when I select on Network, the workgroup WRETCHNET does display.  Clicking on that, I get the error message:   Unable to mount location   Failed to retrieve share list from server.    Following your posts, I did the Terminal work on both computers of     sudo apt-get update && sudo apt-get install samba     Both computers did pull down and install the packages.  On rebooting both computers, the Update Manager alerted me of an update package of:   libsmbclient     I installed this on both computers and rebooted both into Ubuntu.  I still cannot access shares from one Ubuntu machine to another.  I can still boot up Comp1 into XP and access the Ubuntu shares on Comp2.  But I still can not access the XP shares from Comp2.     Can you please tell me what the problem is?

---

### Post by Iowan on 2010-09-15
Merged thread/post
From Code of Conduct:
> Please do not cross post, or post the same thing in multiple locations.
I presume you've tried bypassing XP's firewall...
When Comp1 is booted into Ubuntu, does it have an IP address (**ifconfig -a** from a terminal)?

---

### Post by CharlesA on 2010-09-15
Helps to not post a huge wall of text, which is hard to read and understand.

---

