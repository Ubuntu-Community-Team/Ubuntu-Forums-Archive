---
title: "Jaunty 9.04 Still Can't See XP shared Printer? My FIx:"
date: 2009-06-08
forum: Networking &amp; Wireless
---

### Post by Malfini on 2009-06-08
[SIZE=2]History: I could see the other computer on a home network but couldn't print to LPT1 on the XP box.

Earlier I posted with an [/SIZE][SIZE=2]**"Unable to connect to CIFS host" **problem. I tried to specify the printer by its IP address and I mistakenly had 3 slashes (smb:///192...) Once I corrected that I got a "**Bad Device URI". **Then I found this from the MS site [edited]:[/SIZE][INDENT][FONT=Arial][SIZE=2]Windows XP supports the use of long printer names [including] names that contain spaces and special characters... if you share a printer over a network, some clients will not recognize or correctly handle the long names, and users may experience problems... with names longer than 31 characters.[/SIZE][/FONT]

[FONT=Arial][SIZE=2] For shared printers, the entire qualified name (including the server name, for example \\PRINTER2\PSCRIPT) must be fewer than 31 characters [and should] [/SIZE][/FONT][SIZE=2]not include spaces or special characters[/SIZE][/INDENT][SIZE=2]So on the XP box I renamed the printer from "Brother HL-1440 series" to "BROTHER", and then entered **smb://SERVER/BROTHER**[/SIZE] [SIZE=2]and all was well.[/SIZE] (It seems under Windows printer properties a printer has a name and a "share name", a bit conusing, but I changed both.)
[SIZE=2]
Hope this helps somebody else.[/SIZE] [SIZE=2]Peace.[/SIZE]

---

### Post by superprash2003 on 2009-06-08
good job..sharing...

---

