---
title: "WD N600 router review"
date: 2013-08-02
forum: Networking &amp; Wireless
---

### Post by kurt18947 on 2013-08-02
[FONT=Verdana, sans-serif]This is a review of a Western Digital WD600 router.  I've had an itch to experiment with the NAS-lite-like functions offered by routers with USB ports.  Most have been more than I've wanted to spend.  We were in WalMart a few days ago and there was a basket of these router marked down to $39.99 and had a USB port. Hmmm.  I decided I'd bring it home, be careful to keep all the bits so be able to return it if it sucked too bad.[/FONT]
 

 [FONT=Verdana, sans-serif]It sucks but not too bad.  It's clearly intended for the consumer market.  The passwords for both the router & FTP/SMB servers are limited to 15 characters.  Huh?  And this fact was not documented except in a firmware download so I wasted a good amount of time creating a longer password, going through all the setup changes, save no error messages.  Log out and I couldn't log back in, I kept getting a “user name or password is incorrect” type message.  Grrrr.[/FONT]
 

 [FONT=Verdana, sans-serif]The hardware seems pretty decent.  Two networks that would have separate SSIDs and passwords.  I haven't enabled the 5 ghz. Network; I don't know that I have any adapters that are dual frequency capable and don't really need speed beyond 150 mbps.[/FONT]
 

 [FONT=Verdana, sans-serif]The firmware seems pretty rudimentary.  This is replacing a Linksys wrt-300N with DD-WRT.  It felt sorta like going from gnome2 to vanilla gnome3.  The basics are there – SIP firewall, port forwarding QoS, etc. etc. but there's nowhere near the choices of DD-WRT and the short password makes me wonder if there are other security weaknesses.  It'd be great to see someone port one of the 3[SUP]rd[/SUP] party firmwares to this device.  It uses an Atheros chip so that may complicate things vs. the more common Broadcom.  I'm daisy chaining this device downsteam from a Verizon Actiontec MI424WR so that may help some with security.  Having two firewalls enabled doesn't seem to be causing an issue so far.  I believe the WiFi speed & range is better than the Linksys it replaced.  I have an ethernet cable running from a lan port on the Actiontec to a lan port on the Western Digital.  There is a network connection present but the router doesn't detect it and as a result can't contact a time server, I also can't register it online.   The linksys in the same configuration did recognize the internet connection and was able to contact a time server.
[/FONT]
[FONT=Verdana, sans-serif]   	 	 	 	   [/FONT]

[FONT=Verdana, sans-serif]The USB port is recognized by 12.04 & 13.10.  A USB storage device is recognized.  Filezilla connects no problem.  Trying to log in via Nautilus ->connect to server via FTP yields this result:[/FONT]
 

 > [FONT=Verdana, sans-serif]The link “SanDisk_Cruzer_Blade_30” is broken. Move it to Trash?[/FONT]

 

 [FONT=Verdana, sans-serif]	This link cannot be used because its target “/var/tmp/storage/SanDisk_Cruzer_Blade_30” doesn't exist.[/FONT]
 

 [FONT=Verdana, sans-serif]I haven't researched this yet so may be posing a question in the future if I come up empty.  Filezilla connects no problem at all but it'd be nice to be able to connect via Nautilus/Files as well.  Trying to connect via smb says[/FONT] [FONT=Verdana, sans-serif] username/password are bad.[/FONT]

 [FONT=Verdana, sans-serif]
I think it's worth what I paid for it but not much more.  [/FONT] 

  [FONT=Verdana, sans-serif]
[/FONT]

---

