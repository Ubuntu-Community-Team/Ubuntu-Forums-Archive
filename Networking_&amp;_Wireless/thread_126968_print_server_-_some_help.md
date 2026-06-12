---
title: "print server - some help?"
date: 2006-02-07
forum: Networking &amp; Wireless
---

### Post by myke on 2006-02-07
I have a Dlink wifi card which was detected automatically as well as a dlink wireless router.  Dlink seems to be one of the very hardware folks who actually seem to work with linux compatibility.   My network at home is stand-alone - it's not connected to any desktop computer.  It runs own it's own directly from the cable modem and router.  Anyway ... the only part I haven't had is the ability to print wirelessly.   Soooo ... I purchased a Dlink DP-G310 print server as their stuff has been good to me and it even notes in the manual that it works with both linux and my usb printer (an Epson C42 UX).   

OK ... I've used the web based set up utility and it's detecting my printer just fine.   My laptop is wirelessly communicating with the print server just fine.  Only problem is ... when I sent something to the printer, it says in the monitor that it's printing but nothing ever comes out.

I've even called dlink support and they weren't helpful.  I can't figure out what's going on.  Any suggestions as to how to get it printing?  Anyone have familiarity and success with using wireless print servers with Ubuntu?

---

### Post by myke on 2006-02-08
Please someone help with this!  I've checked it out under the xp side of my dual boot and was able to get it working easily!   Don't let xp win out!!  Seriously, from the web based set up, I can send a test page to the printer fine.  However, when printing from even the text editor, I get nothing.   The difference between the winxp set up and ubuntu seems to be that in win after configuring the print server, you have to inset up a special port for the printer to be found wirelessly.  I wrote all of the settings down from the win boot up but i can't figure out how to add the separate port for the printer to connect wirelessly in ubuntu.  Anyone have any how to do this???   If it'll help, this is the url to the print server with dlink and it has a pdf version of the manual so you can see the xp and web config settings if it'll give a clue how i can fix this.  

Thanks for helping if you can.

[dlink dp-g310 print server]("http://www.dlink.com/products/?sec=1&pid=313")

[install guide in pdf for dp-g310]("http://www.dlink.com/products/support.asp?pid=313&sec=1#quickInstallGuides")

---

### Post by einstein on 2006-02-08
I am having a similar problem with involving a DLink DI-824VUP, which is a wireless  vpn router with built in print server.  Windows computers, wired and wireless Win98's and WinXP's, print no problem.  LInux will print directly to the printer no problem.

Out of dozens of attemps after setup changes, the best I have achieved is two entries in the router log indicating print requests from the Linux computer.

I am convinced the problem is in the Linux computer network print setup.  Extensive Googling on the matter has returned nothing of use.  My inquiry here a couple of days ago has returned zero responses.

---

### Post by hollinch on 2006-02-08
Don't know if it is any help to you, but I have been having problems using Linux and a Linksys wireless print server myself. Likewise, printing from Windows was not a problem, printing from Linux using the Windows-only Linksys documentation didn't work. The Linksys helpdesk I called was instructed never to offer advice on Linux issues. Great service...

However, using LinuxQuestions ([http://www.linuxquestions.org](http://www.linuxquestions.org)) I found out the correct way to configure my system to print to the print server. This [link]("http://www.linuxquestions.org/questions/showthread.php?t=172001") helped me out. The print server (WPS54GU2) has two ports, one parallel and one USB2. The things I had to do to get it to work properly:

1. Set the Linksys print server to a fixed IP address (it defaulted to a DHCP address)
2. Create a new LPD-queue on the Linux system
3. Enter the IP address of the Linksys print server
4. Use as queue names L1 or L2, depending which port is required. L1 for parallel, L2 for USB2.
5. Install the correct driver for the printer connected to that port.

That simple it was. I got on the wrong foot because the documentation talked about P1 and P2 as print queues, but for some reason you have to use L1 and L2 under LPD... ?

As said, it may not help your situation, but it's better to mention than not to.

Cheers, Jaap.

---

### Post by einstein on 2006-02-08
hollinch;

Thanks for your input!  I suspect your info may be the missing bit I have been looking for.  Everything I have been able to find so far says to use ports like usb, usb0, usb1, lp, lp0, lp1 and so on.

I will check it out this evening and let you all know what happens.

Regards, Dennis

---

### Post by einstein on 2006-02-08
This may or may not help some light on the issue (I could not wait to get home to do some more investigating so I shut down WinXP and rebooted with Ubuntu Breezy live CD).

At the office I have a DLink DP-G321 print server with two USB and one parallel ports.  I have only an Epson Stylus C66 attached (on the first USB port).  Upon Ubuntu up and running, I configured eth0 with static 192.168.0.1 and Workgroup ID (the computer's specs for WinXP).  BTW, I noticed that Samba was then configurred for me so that I could see other network 'puters.

I then added an LPD printer on IP 192.168.0.6 (print server static IP) and port PS-B4C585-U1, which is how Windoze addresses the printer.  I spec'd the Epson Stylus C64 driver, hit the Print Test Page and...?  A test page printed without hesitation.

The thing is, this does not solve my problem on my DLink DI-824VUP.  Windoze addresses the printer via 192.168.nnn.nnn/USB0.  However, when I spec this to Ubuntu I get zip.

Regards, Dennis

---

### Post by myke on 2006-02-08
[QUOTE=hollinch]Don't know if it is any help to you, but I have been having problems using Linux and a Linksys wireless print server myself. Likewise, printing from Windows was not a problem, printing from Linux using the Windows-only Linksys documentation didn't work. The Linksys helpdesk I called was instructed never to offer advice on Linux issues. Great service...

However, using LinuxQuestions ([http://www.linuxquestions.org](http://www.linuxquestions.org)) I found out the correct way to configure my system to print to the print server. This [link]("http://www.linuxquestions.org/questions/showthread.php?t=172001") helped me out. The print server (WPS54GU2) has two ports, one parallel and one USB2. The things I had to do to get it to work properly:

1. Set the Linksys print server to a fixed IP address (it defaulted to a DHCP address)
2. Create a new LPD-queue on the Linux system
3. Enter the IP address of the Linksys print server
4. Use as queue names L1 or L2, depending which port is required. L1 for parallel, L2 for USB2.
5. Install the correct driver for the printer connected to that port.

That simple it was. I got on the wrong foot because the documentation talked about P1 and P2 as print queues, but for some reason you have to use L1 and L2 under LPD... ?

As said, it may not help your situation, but it's better to mention than not to.

Cheers, Jaap.[/QUOTE]

I believe that actually might solve my problem as it is similar to how I made it work with xp, adding a separate port for the printer when it is used wirelessly.  It is a usb epson and will occasionally, though rarely, be used directly via usb.  However, IF I can get it working, it will primarily be used wirelessly via the print server.  I'm unsure, however, how to add the new print queue.  Can you lead me through this endeavor??  I'd appreciate the help. (and I hope this works)

---

### Post by hollinch on 2006-02-08
Hey Myke, that is not too difficult, only had to logoff and select English as language, as my Ubuntu defaults to Dutch...

If you go to System->Administration->Printing, then add a New Printer, select Network Printer->Unix Printer (LPD), you can provide the IP address and queue name (L1 or L2 in my case). After that it checks if the remote queue is accessible, and asks you for the printer manufacturer and model. That's about it.

Hope this helps.

Cheers, Jaap.

---

### Post by myke on 2006-02-08
OK ... when I go there under step 1 it has boxes for "host" and "queue".  I assume the Ipp for the printer  the print server goes under "host"?  And when you put it in, what format do you use?  the IP # only or something like "ipp://"?
Under queue, do you just print the name by itself??  Such as just "L2"?   And forgive my noviceness here ... but where do I look to find the exact queue name for my printer port so I'm sure I have it correctly?  I have a laptop with 2 usb ports and no parallel.

Hey, I'm new at this linux stuff (relatively) ... but I learn quick.

---

### Post by hollinch on 2006-02-08
Myke, how exactly do you want to use your printer, connected via the USB port of your computer but made available for wireless PCs to print to, or connected via a dedicated print server like my situation?

Cheers, Jaap.

---

### Post by myke on 2006-02-09
Sorry I responded to this a bit late ..

Hey, I definitely wanted it via a dedicated print server like yours.  Over the last couple of days of messing with it, the solution turned out to be quite simple.  You actually clued me in on how to do it ...

I chose 'network printer'  then the drop down 'unix printer (LPD)' .

I simply added the print server's ip # into the host box.

Queue box I filled with the ip # preceeded by 'IP_'      ... worked like a charm.  I'm using an Epson inkjet printer which I already had but I've purchased a b/w laser on ebay that was noted on the dlink website as being compatible with the print server.

I'd say to anyone:  go with DLink routers, wifi cards, and print servers if at all possible.  They seem to be the most compatible out of the box with Linux and  they're the only company I've seen to advertise as Linux friendly.

---

### Post by hollinch on 2006-02-10
Great, Myke. I'll keep that in mind; I have to get myself a new wireless card anyway (see my other [thread]("http://ubuntuforums.org/showthread.php?t=126858")), so I guess it is best to pick up a D-Link.

You see, Manufacturers, it helps to be friendly towards F/OSS! 

Cheers, Jaap.

---

### Post by Audesse on 2006-02-11
Hey guys - I'm trying create a wifi printserver setup as well, and I'm wondering if anyone has had any success with the: 

Motorola WPS870G Print Server 
 [ and/or ] 
Konica Minolta 1350W Laserjet.

Ubuntu has the 1350W driver already handy, but, having tried all of the above methods of communicating over the printserver, I've still not been successful - not even a test page.

I'm afraid that this printer simply might not play nicely with anything other than a cabled connection. Can someone please verify this or prove me wrong?

Thanks

---

### Post by Flashman69 on 2006-02-17
My very first post!!!!

Just to say thanks for your discourse on the problems you had with getting your Ubuntu machines to print to a print server, it helped me solve mine :-D 

I have a Linksys wireless router with 3 XP boxes connected, one wirelessly and after a few hiccups this Dell lappy running Ubuntu 5.10, also wirelessly. I also have an Ellink router with a built in print server and I decided to link the routers together and use an old printer to connect to it. Great, the Ellink provided all that I needed to get a Windows box to connect but could I get the Dell to print? And it still won't print a test page :confused: 

I have, however, managed to print an openoffice document with great success, so again thankyou for your exchange, it pointed me in the right direction.

Flash

---

### Post by oldlag on 2006-02-17
einstien, many thanks for this thread. I also have a D-Link DP-G321 with an HP 5940 and following your instructions the Tes page printed!!

---

### Post by sarah.bartnik on 2008-03-20
> **Audesse said:**
> Hey guys - I'm trying create a wifi printserver setup as well, and I'm wondering if anyone has had any success with the: 

Motorola WPS870G Print Server 
 [ and/or ] 
Konica Minolta 1350W Laserjet.



I'm not sure if you ever figured out how to connect to the Motorola Print Server. I did.

I have:
Motorola WPS870G Print Server 
Brother HL-1435 laser printer (USB connection)

I used the LPD connection. I entered the IP address of the server and the name of the printer (which was plugged into the USB port, so it was L2). I used the driver recommended for this printer (the Brother 1250 I believe). It works.

---

