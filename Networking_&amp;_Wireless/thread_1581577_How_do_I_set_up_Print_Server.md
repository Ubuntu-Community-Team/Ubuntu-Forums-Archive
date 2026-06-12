---
title: "How do I set up Print Server"
date: 2010-09-25
forum: Networking &amp; Wireless
---

### Post by siabost on 2010-09-25
Hi,

I recently came across an old Epson DX5000 Printer/Scanner which works fine via USB.

It also had a Netgear PS121v2 USB Print Server attached - [http://kb.netgear.com/app/products/model/a_id/2517](http://kb.netgear.com/app/products/model/a_id/2517)

Instructions for Windows set-up are given at the above link - how do I do this in Ubuntu 10.04?

I have a Netgear DGN2000 Wireless-N ADSL2 Router and I'm hoping I can access the Epson Printer from other PCs on my local wireless network.

Many thanks.

---

### Post by SeijiSensei on 2010-09-25
Try connecting the print server to one of the wired ethernet ports in the back of your router.  It should be assigned an address via DHCP.  You can usually confirm that by looking in your router's management console and seeing the list of connected hosts.

As I recall, the Netgear I used to use supported a variety of protocols including the Internet Printing Protocol that CUPS uses.  Once you know the print server's IP address, see if you can connect to it using the printer manager in Ubuntu.  (You can also try the handy web interface to CUPS at [http://localhost:631/](http://localhost:631/), but you may have problems obtaining root permissions that way.)  

If IPP doesn't seem to work, you might be able to use an SMB connection or even the old HP JetDirect protocol, both of which CUPS supports.

Once you get this running successfully, I'd tell your router to give the Netgear device a fixed IP address.  Otherwise if it gets disconnected somehow, it won't necessarily have the same address, and all your printing configurations will fail.

---

### Post by siabost on 2010-09-25
Hi SeijiSensei,

Thanks.

I looked in the Attached Devices in my router with Print Server plugged in and powered up but it doesn't appear.

However, there was a "diag" button on the print server which printed out the following:

Hardware ID: 05604683C3
Firmware Version: 1007
Protocol ID: 006E
Server Name: PS20C51ASERVER
Mac Address: 00C00220c51a

Appletalk Info:
Printer Type: 
PS20C51ASERVER: Laserwriter
TCP/IP Info:
IP Address: 192.168.1.65
Subnet Mask: 255.255.255.0
Gateway Address: 192.168.1.254
Email Server IP Address: 0.0.0.0
Printing Account Name: N/A
Redirect Account Name: N/A

SMB Info:
Domain Name:

I suspect my router can't find it because it's on a fixed IP of 192.168.1...... and my system is on 192.168.0......

Any way I can get round this?

Thanks.

---

### Post by mark bower on 2010-09-25
no expert here.  i have a D-Link DP-301 Print Server (PS) attached to my printer (HP LJ 4); the PS is wired to the router.  my primary computer is also wired to the router, the other computers are located across the house and connect wirelessly.  with this arrangement, the primary computer does not have to be turned on in order for the other computers to "talk" to the printer.  

i set up as follows, using Ubuntu 9.10, the same for each computer:

Sys>Admin>Printing>New (get "searching for printers")
select Network Printer
select your PS which should be recognized
forward
select your printer make . . .

my guess is setting up on 10.4 should be the same as 9.10

mark

---

### Post by SeijiSensei on 2010-09-26
The [instructions for Mac OS X]("http://kb.netgear.com/app/answers/detail/a_id/2752") suggest you might be able to change the server's static address using the Windows utilities.  Take a look at the [reference manual](http://kb.netgear.com/app/answers/detail/a_id/2146).

---

### Post by siabost on 2010-09-28
Hi all,

Got it sorted.

Plugged the Print Server directly via network cable into my PC (after temporarily setting my PC to a fixed address of the same type as that set on the Print Server - 192.168.1...).
Got access the the PS's built-in web-type configuration and set it to DHCP.
Re-set my PC, plugged the PS into my network, the Netgear router picked it up and assigned it an address, I reserved that address for it & just used the Ubuntu printer tool to locate the printer on the network - & bingo, wireless printing.

Thanks for all your help.

---

### Post by UpsideDownFace on 2010-10-04
Hi all

I have been struggling for several days to get an Edimax PS-1206U Print Server to work with linux.
It is working with my mac-book. I did this to make it work :-

Plug PS-1206 into router and HP laserjet 1300 printer.
$ sudo arp -s 192.168.1.2 00:00:B4:D2:F4:61
$ (type in password)
$ ping -c 3 192.168.1.2

the ping gave a satisfactory response,
so I went into "System Preferences" and told it "Add new printer"
I think I needed to restart the mac-book, but I can now print directly from the mac-book, and also via the net from my Ubuntu 8.04 LTS linux.

But I want to print when the mac-book is not switched on

So I have done the "sudo arp ..." from my linux machine and then gone into "System > Administration" and told it there's a new printer on 192.168.1.2
But it has asked me for details I don't know.
So far I have failed to guess what settings are needed.

The machine is seeing the printer, but is sending print files to the great printer in the sky.

My mac-book is also dual booted with Ubuntu 10.04 Netbook, and doesn't work with the print server - so it's obviously a software problem.

Anybody got any suggestions please?

---

### Post by siabost on 2010-10-04
Hi,

Once I knew the IP address of the print server I just went to System/Administration/Printing/Network Printer/Find Network Printer, typed the print server IP in the box and clicked "find". After a few seconds it found the print server and its port.

When it does find it click "forward" to select your Printer driver (it will try to do it automatically first) - or the closest to it. Once installed you will have the option to print a test page.

The above is for Ubuntu 10.04.

Best of luck.

---

