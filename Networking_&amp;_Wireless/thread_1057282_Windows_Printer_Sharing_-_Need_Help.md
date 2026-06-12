---
title: "Windows Printer Sharing - Need Help"
date: 2009-02-01
forum: Networking &amp; Wireless
---

### Post by rss7 on 2009-02-01
Hello - I am new to Linux.  I am trying to access a shared printer that is attached to a WinXP machine.  After weeks of scanning this forum I( have confirmed that I have Samba installed (I installed using the How To guide).  Also, I can browse to the WinXP machine from my Ubuntu 8.10 linux machine by using smb://192.168.1.3 in a browser, so I know I can get to the the WinXP machine from my home network.  I have Ubuntu version 8.10 with all new updates installed.  When I try to add a printer using Samba, The utility finds the shared printer, and appears to load the driver.  When I try to print a test page, I get "NT_ACCESS_DENIED" error, then it says "unable to connect to CIFS host after 3 tries".  Please help.  This is my 2nd post - first post got zero responses.  Please help.

---

### Post by dmizer on 2009-02-01
You don't need to configure samba to connect to windows printers.

Just use the printing administrative tool (System --> Administration --> Printing) in your menu to search for and configure the network printer.

---

### Post by Robin Kinney on 2009-02-05
I had a very similar problem with a strange solution.  The LAN address to the printer in my case is smb://MSHOME/SANDRA/Printer where MSHOME is the name of the windows workgroup, SANDRA is the name of the XT machine hosting the printer and Printer is the name of the shared printer on that machine.  I had recently switched from my ISP as the source for DNS (Domain Name Service) to OpenDNS.  For some strange reason my machine was going out on the Internet and trying to access one of OpenDNS's servers for printing.  This is so wierd I can't believe it's a bug so I'm doing more investigation before submitting.

To see if you have the same problem, Open a terminal window and submit to the print queue directly by typing:  
smbspool smb://workgroup_name/computer_name/shared_printer_name 1 user_name test_name 1 file_name
where workgroup_name, computer_name, and shared_printer_name are self explanatory.  If the meaning of the arguments are not clear, leave them off and the OS will tell you the proper command format.  You will need to create a file named "file_name" or use a printable file in its place.   

In response, the OS will indicate exactly where it is trying to get access to print.  If it is trying to gain access out on the Internet then you have the same problem as I.  If not, maybe it will shed light on your specific problem.

My solution was to not use OpenDNS and if anyone else can shed light on the issue, please post.

Please post your results to this thread if you share my problem.  Again, I'm trying to determine if this is a bug.

Good luck.

---

### Post by steveneddy on 2009-02-05
> **dmizer said:**
> You don't need to configure samba to connect to windows printers.

Just use the printing administrative tool (System --> Administration --> Printing) in your menu to search for and configure the network printer.

This will pretty much solve most issues connecting to printers.

I wonder how the OP is doing?

---

### Post by saultpastor on 2009-02-05
> **Robin Kinney said:**
> I had a very similar problem with a strange solution.  The LAN address to the printer in my case is smb://MSHOME/SANDRA/Printer where MSHOME is the name of the windows workgroup, SANDRA is the name of the XT machine hosting the printer and Printer is the name of the shared printer on that machine.  I had recently switched from my ISP as the source for DNS (Domain Name Service) to OpenDNS.  For some strange reason my machine was going out on the Internet and trying to access one of OpenDNS's servers for printing.  This is so wierd I can't believe it's a bug so I'm doing more investigation before submitting.

To see if you have the same problem, Open a terminal window and submit to the print queue directly by typing:  
smbspool smb://workgroup_name/computer_name/shared_printer_name 1 user_name test_name 1 file_name
where workgroup_name, computer_name, and shared_printer_name are self explanatory.  If the meaning of the arguments are not clear, leave them off and the OS will tell you the proper command format.  You will need to create a file named "file_name" or use a printable file in its place.   

In response, the OS will indicate exactly where it is trying to get access to print.  If it is trying to gain access out on the Internet then you have the same problem as I.  If not, maybe it will shed light on your specific problem.

My solution was to not use OpenDNS and if anyone else can shed light on the issue, please post.

Please post your results to this thread if you share my problem.  Again, I'm trying to determine if this is a bug.

Good luck.

Thanks for posting this I had the same problem it seems ](*,)

---

### Post by dmizer on 2009-02-05
> **Robin Kinney said:**
> My solution was to not use OpenDNS and if anyone else can shed light on the issue, please post.

You can enable NetBIOS with OpenDNS as long as you have /etc/nsswitch.conf correctly configured. Order DOES matter in this file, so if you put wins in front of dns, then your NetBIOS names will resolve before DNS (before OpenDNS can interfere), like so:
```
# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         compat
group:          compat
shadow:         compat

hosts:          files [COLOR="Red"]wins[/COLOR] dns
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis
```

OpenDNS has an "[typo correction](http://www.opendns.com/homenetwork/solutions/guide/)" feature, where it sends you to a search page if you typo a URL. Unfortunately, this behavior is identical with NetBIOS names (which of course have no DNS entry).

Edit:
Alternatively, you can sign up for an OpenDNS account and use it for local DNS resolution as well.

---

### Post by Robin Kinney on 2009-02-06
Your information about Name Service Switch is extremely helpful.  When I first experienced the problem, a search through the forums showed many people with NT-ACCESS-DENIED problems with printing.  Although a local vs. Internet DNS is only one of many soruces of the problem, I wanted to post to not only help me but potentially others.  This demonstrates the power of forums and their ability to prevent non-bugs from being reported.  I hope it helps rss7 who started the thread as well.  Nice work, dmizer!

PS -- Although a Internet source of local donain names resolution is an option, I think I'll correct my order.  I'm all for keeping traffic off the Internet when possible.

---

### Post by rss7 on 2009-02-06
Thanks for the replies.  My first attempt at sharing a Windows machine was to use the "System/Administration menu to add a printer.  I was amazed at how easy I thought this would be.  I was able to browse to the WinXP machine and actually found the printer.  I clicked on the printer and then clicked "verify" and that is where I got the NT_ACCESS_DENIED error.  That failure lead me down the path to trying to do something with SAMBA.  In response to the suggestion of using the smbspool command, unfortunately I was not able to understand every command argument, but I pasted the command into a terminal window anyway and when I did so, the response said it was trying to print connect to 67.63.55.3:445.  I have no idea where that address is, so maybe I do have some sort of open DNS problem.  My problem is that I have no idea what OPen DNS is.  Sorry - but I am still lost.
Thanks all - I hope someone can help!

---

### Post by rss7 on 2009-02-08
Hi - I got it to work. What I had to do was go to System-Admin-Printing-New-Add Windows Printer Via Samba. It found the shared printer and it loaded a driver. The new info is that I had to right-click on the printer, click on properties, then enter the device URI, which was smb://192.168.1.101/printer2, where 192.168.1.101 is the IP address of the winxp machine and "printer2" is the name of the shared printer. I then clicked "print test page", and magically the test print showed up on the printer!

Thanks all..

---

### Post by Robin Kinney on 2009-02-11
Good work.  Soon you'll be helping others in the forum.  OpenDNS is an Internet service for DNS, Domain Name System, that translates domain names such as OhioStateUniversity.org, into an IP address.  Usually your Internet Sevice Provider provides this service but you can get it also on the Internet.  Perhaps 67.63.55.3 is where you get DNS services.  That's what dmizer was telling us about the nsswitch.conf  After "hosts" is the list of places to translate names into address.  His advice was that it's order-specific.  No matter, You solved it.

---

### Post by ggarretson1 on 2009-02-17
I have a toshiba laptop loaded with 8.10 and vista loaded tower in the office i can not print to the brother printer in the office when i try to set it up in the the network via samba when it goes to look for the brother model# and driver it is not listed.It is a MFC-7420

Any ideas? GGarretson1

---

