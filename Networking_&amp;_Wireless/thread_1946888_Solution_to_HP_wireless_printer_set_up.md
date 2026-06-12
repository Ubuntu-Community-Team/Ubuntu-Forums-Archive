---
title: "Solution to HP wireless printer set up"
date: 2012-03-25
forum: Networking &amp; Wireless
---

### Post by 23senick on 2012-03-25
[FONT=Arial][SIZE=2]Had problems getting HP printers connected wirelessly? I experienced huge frustration and the instructions and prompts didn’t help much. With HPLIP and HPLIP Toolbox I would get so far in the process to connect a wireless printer then it would always say “&#65279;An I/O error occurred.  Please check the USB connection to your printer and try again”  This is enormously frustrating - I got a laptop and a wireless printer so I wouldn’t have to print in particular rooms, connect cables etc ![/SIZE][/FONT]

        [FONT=Arial][SIZE=2]I assume you do need HPLIP installed, haven’t tried sorting without.[/SIZE][/FONT][FONT=Arial][SIZE=2]  First, look through your printer’s network settings and get it to display its address, a series of numbers like 192.150.1.2  [/SIZE][/FONT][FONT=Arial][SIZE=2]
[/SIZE][/FONT]
        [LEFT][FONT=Arial][SIZE=2]Next, in your laptop you need to go into Printing  (the CUPS printer configuration - system-config-printer).  This is in “system" if you’re in Xubuntu or Lubuntu.  Once you open the printer configuration, click add printer, then click on “network printer" which should give you a drop down list of options.  Select the option Find Network Printer.  In the box marked “Host" enter the address 192....etc.  Click “Find.”  Immediately you get some options - IPP and App Socket/HP JetDirect. [/SIZE][/FONT]
[FONT=Arial][SIZE=2]
[/SIZE][/FONT][/LEFT]
        [LEFT][FONT=Arial][SIZE=2]But be patient - wait for a moment, and you will get another option HPLIP - select this. Click on “forward” and after searching for drivers, it should install.  You need to fill some boxes (naming the printer) and the only issue here is don’t leave spaces in the name - it doesn’t like that.  Click Finish...hey presto, working network printer![/SIZE][/FONT]
[FONT=Arial][SIZE=2]
[/SIZE][/FONT][/LEFT]
        [LEFT][FONT=Arial][SIZE=2]Maybe all the above was obvious to everyone else, but I haven’t seen a how-to which explains these steps!  Hope this helps someone.  [/SIZE][/FONT][/LEFT]

---

### Post by mr_niceguy on 2013-02-07
Thank you!

Wish I could mod your answer up in Google ranking. This one works just as explained.

---

### Post by wildmanne39 on 2013-02-07
Old thread closed.

---

