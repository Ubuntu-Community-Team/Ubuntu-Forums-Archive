---
title: "Network printing via Belkin all-in-one print server"
date: 2009-08-30
forum: Networking &amp; Wireless
---

### Post by potatan on 2009-08-30
Hi,

I have a Belkin All-In-One network print server, which I have hardwired into my router (not using wireless at the moment).  I can ping it fine, on 192.168.1.66, the web-based print server config screen is accessible and working.  The printer itself is an HP PSC1300 series, which works fine when plugged directly into the PC's USB port.

Just for completeness, here are the settings of the print server:

```
Printer Status
	Manufacturer :  	hp
	Model Number :  	psc 1300 series
	Printing Language Supported :  	LDL,MLC,PML,DYN
		

  System Information
	Device Name : 	MFD8FAE9 	Raw Printing : 	Enable
	All-In-One Print Server Name : 	MFD8FAE9 	IPP Printing : 	Enable
	Model Type : 	F1UP0002 	LPR Printing : 	Enable
	Firmware Version : 	3.2.26 		
	MAC Address : 	00:17:3F:D8:FA:E9 		
	USB Port Number : 	1 		
	LPT Port Number : 	No 		
	Wireless Lan Status : 	Auto 		

  Wireless Configuration
	Mode : 	Infrastructure 	BSSID : 	00:00:00:00:00:00
	Channel Number : 	0 	Encryption : 	WPA-PSK TKIP
	Status : 	Disconnected 	ESSID : 	
```

I have upgraded the Belkin firmware to the latest version.

If I add an LPD/LPR printer with the IP address, then it gets recognised fine and shows up as connected / idle in the printer configuration.

But when I print a document or a test page, it processes the job, connects to the IP address, then fails with a message in printer config dialog of:

```
Printer State: Idle - /usr/lib/cups/backend/lpd failed
```

CUPS error log says:

```
/var/log/cups$ tail -f /var/log/cups/error_log
D [30/Aug/2009:20:36:16 +0100] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)
D [30/Aug/2009:20:36:16 +0100] cupsdReadClient: 10 POST / HTTP/1.1
D [30/Aug/2009:20:36:16 +0100] cupsdAuthorize: No authentication data provided.
D [30/Aug/2009:20:36:16 +0100] Get-Printer-Attributes ipp://localhost/printers/HP-PSC-1300
D [30/Aug/2009:20:36:16 +0100] cupsdProcessIPPRequest: 10 status_code=0 (successful-ok)
D [30/Aug/2009:20:36:16 +0100] cupsdReadClient: 10 POST / HTTP/1.1
D [30/Aug/2009:20:36:16 +0100] cupsdAuthorize: No authentication data provided.
D [30/Aug/2009:20:36:16 +0100] Get-Printer-Attributes ipp://localhost/printers/HP-PSC-1300
D [30/Aug/2009:20:36:16 +0100] cupsdProcessIPPRequest: 10 status_code=0 (successful-ok)
D [30/Aug/2009:20:36:16 +0100] cupsdCloseClient: 11

```

I can think of maybe two things - first the log mentions no authentication data provided, though I have had this all working before and can't remember ever having provided any logins etc. (PC has been rebuilt since)

The only other thing perhaps, is that the printer config asks me to provide a queue name, offering "dummy" and "dummy2" as options, but I don't think there is a queue name involved as there is only one USB port on the print server.  I have, however, tried setting this to dummy, dummy2, and then tried L0, L1, 0, and 1 (trying things from other postings on the subject).

This is rather annoying as I have definitely had the printer connected and working before, though this may have been using Ubuntu 8.10 - I am now running 9.04.

Anyone any ideas?

Many thanks in advance

---

### Post by potatan on 2009-09-02
bump

---

### Post by potatan on 2009-09-09
bump again - anyone any idea where to start looking?

TIA

---

### Post by potatan on 2010-03-08
Hello - been a while since I took a look at this.  I've converted one of my machines to Lucid development branch to see if that has had any effect on my problem, but still no luck.

Are there any printing or networking experts out there?  Or preferably experts on network printing!

Thanks in advance.

---

### Post by mark bower on 2010-03-08
No expert here, but I did setup my system of 3 computers as described below using CUPS.  Perhaps it might help as my Print Server is connected to a router.  The key for me was working thru Sys/Admin/Printing.  Different settings were established on different computers as noted further below.

Hardware/Software:
Dlink DP-301P print server attached on rear of HP Laserjet 4 Plus 
DP-301P connected to Linksys WRT54G router via ethernet cable  
MAC addr of DP301P: 00:02:B0:dF:6E:C4
Ubuntu 9.10  

1) Delete existing printers:   
	Sys>Admin>Printing>select>properties>delete

2) Locate the network printer on the network:
	Sys>Admin>Printing>New>Click Network Printer>select PS-DF6EC4-P1>select forward
	(where PS-DF6EC4 is the discovered DP-301P, and description is "LPD network printer via 	DNS-SD)

3) Select the printer and its driver on the next screen
	New Printer Screen>click select from database>select HP>scroll to and select HPLJ4>select hpijs pcl3[en]>forward
	
4) Print test page to verify screen.  Select yes to verify setup.

Some notes:
On one of three computers, the DP-301P installed with the following URI:
	Device URI:  dnssd://PS-DF6EC4-P1.printer._tcp.local/

But on two of three computers, the DP-301P installed with the following URI:
	Device URI:  ipp://192.168.1.1105:631/printers/HPLJ4-printserver

I cannot determine what forces the different settings.  Both configurations print just fine.

In step 2, the complete list of options to select is,
	PS-DF6EC4-P1
	Find Network Printer
	AppSocket/HP JetDirect
	IPP
	LPD/LPR Host or Printer
	Windows or Samba

---

### Post by potatan on 2010-03-09
Thanks for that - it set me thinking, and I've finally figured it out.  I'll post the solution here for anyone with the same problem (or even me when I forget what I did in a year or two...)

What I did was to try telnet-ing to various ports that I had seen mentioned, to see what the all-in-one device was listening on.  The most promising one was 9100, so I went through the config settings and set the printer to an App socket printer using HPIJS, at:

socket://192.168.1.66:9100

Test page printed - hurray!

Marking as solved.

---

### Post by mark bower on 2010-03-09
I would definitely like to see your sequence using telnet.  I know nothing re telenet, but curious.  Incidentally, I went to using print server via wifi, versus bluetooth, because I could not get the signal strength needed for various computer locations beyond walls.

mark

---

### Post by potatan on 2010-03-11
Hi, this is how the telnet looked:

```

paul@antec:~$ telnet 192.168.1.100 9000
Trying 192.168.1.100...
telnet: Unable to connect to remote host: Connection timed out

paul@antec:~$ telnet 192.168.1.66 9200
Trying 192.168.1.100...
telnet: Unable to connect to remote host: Connection timed out

paul@antec:~$ telnet 192.168.1.66 9100
Trying 192.168.1.100...
Connected to 192.168.1.100.                **<----- Success!**
Escape character is '^]'.
^]

telnet> quit
Connection closed.
paul@antec:~$ 

```

I'm not sure where I found out that 9100 was significant, and it may only be for this printer or manufacturer, but it worked for me.

I've attached a screenshot of the settings dialog showing configuring the printer.

cheers
Paul

---

### Post by mark bower on 2010-03-12
thanks for the telnet post (so i could see the format).  well, your post prompted me to experiment a little.

when i leave the port off the telenet entry (9100), i get the following when i hit the correct IP and pressing return after "C4":

rocky@ray:~$ telnet 192.168.1.103 
Trying 192.168.1.103... 
Connected to 192.168.1.103. 
Escape character is '^]'. 


************************************ 
*  Welcome to D-Link Print Server  * 
*         Telnet Console           * 
************************************ 

Server Name    :  PS-DF6EC4 
Server Model   :  DP-301P+ 
F/W Version    :  3.50# 
MAC Address    :  00 22 B0 DF 6E C4 

[Main Menu] 
1 - Server Configuration 
2 - Port Configuration 
3 - TCP/IP Configuration 
4 - AppleTalk Configuration 
5 - Display Information 
6 - Tools 
7 - Save Configuration 
0 - Quit 

Enter Selection: 

also, and _very significantly_, when i enter [http://192.168.1.103](http://192.168.1.103) the Dlink server firmware pops up, showing all sorts of LAN information and all computers on the system.  i'm guessing your print server would respond the same?

mark

---

### Post by potatan on 2010-03-14
If I try and connect with telnet but no port specified, I get a timeout.  But yes, I can browse to the web-based management interface by pointing ym browser at the IP address.

---

