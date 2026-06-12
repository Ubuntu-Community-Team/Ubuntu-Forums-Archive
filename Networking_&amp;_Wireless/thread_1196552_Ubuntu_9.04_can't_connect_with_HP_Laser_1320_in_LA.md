---
title: "Ubuntu 9.04 can't connect with HP Laser 1320 in LAN"
date: 2009-06-25
forum: Networking &amp; Wireless
---

### Post by catinsunshine on 2009-06-25
Laptop&#65306;THINKPAD R400
Printer in LAN&#65306;HP Laser 1320
OS&#65306;Ubuntu 9.04/xp

I install Ubuntu 9.04 and XP on my labtop and install HP Laser 1320 on 192.168.0.20 in office LAN. In XP,I can use printer normally,but failed in Ubuntu 9.04.

I modify /etc/samba/smb.conf and change workgroup = ended with WORKGROUP111 which is our workgroup name.With command: ping 192.168.0.20&#65292;no feedback till ended with Ctrl&#65291;S&#12290; Only my labtop been founded in WORKGROUP111 and can not find others.

After added printer,it can't print the test paper and feedback:

unable to connect to CIFS host

connection failed:nt_status_access_denied

Searched with google,still can not solved.Pls kindly help to give your hand with many thanks~

---

### Post by imwithid on 2011-03-15
I am experiencing a similar problem.

I currently have my HP 1320tn printer hooked up via Ethernet (a DOT4 dual USB/Ethernet card).

I run a dual boot on all my computers with Windows XP x64 and Ubuntu 10.04.2 x64.

I have been using the HP LaserJet 1320 PCL6 Driver 61.074.561.43 - May 5 - 2008 under XP and have not had any problems. I manually add the printer, set up the location and port and it works flawlessly.

Printing via Ubuntu has been unpredictable and often does not work (unless wired via USB directly, but even then this does not always work).

I have looked everywhere to find a solution. I will attempt to systematically deduce the problem and post the results here as I eliminate each one.

---

### Post by imwithid on 2011-03-15
Having spent a couple of hours on the problem, it seems as though I've solved it for my printer. In case it helps anyone, I'll post here, my version. It's a bit long, but I wanted to be thorough.

If you already have a printer installed, you don't have to remove it, but you may as well (you can simply change the settings, but we'll start out clean and simple). In case it leads to problems, ensure the spool is clear. There are many ways of doing this (CL or GUI). Open up terminal (Alt+Ctrl+T) and type:

```
gksudo Nautilus
```

Go to File System > /var/spool/cups/ and delete all the cxxxxx files but do not delete the "tmp" directory. Why that is, I do not know. I remember reading it somewhere.

When it comes to HP printers, check to see the specifications on your printer; a quick search for "HP" and "1320" should get you to the official HP page and under "Print Languages" should state:

> 
HP PCL 6
HP PCL 5e
Postscript Level 2 emulation with automatic language switching

Next, open up Terminal (Alt+Shift+T) and type:

```
hp-probe
```

You should get something that looks like:

```
HP Linux Imaging and Printing System (ver. 3.10.2)
Printer Discovery Utility ver. 4.1

Copyright (c) 2001-9 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.


--------------------------------
| SELECT CONNECTION (I/O) TYPE |
--------------------------------

  Num       Connection  Description                                               
            Type                                                                  
  --------  ----------  ----------------------------------------------------------
  0*        usb         Universal Serial Bus (USB)                                
  1         net         Network/Ethernet/Wireless (direct connection or JetDirect)
HP Linux Imaging and Printing System (ver. 3.10.2)
Printer Discovery Utility ver. 4.1

Copyright (c) 2001-9 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.


--------------------------------
| SELECT CONNECTION (I/O) TYPE |
--------------------------------

  Num       Connection  Description                                               
            Type                                                                  
  --------  ----------  ----------------------------------------------------------
  0*        usb         Universal Serial Bus (USB)                                
  1         net         Network/Ethernet/Wireless (direct connection or JetDirect)
  2         par         Parallel Port (LPT:)                                      

Enter number 0...2 for connection type (q=quit, enter=usb*) ? 

```

Make a selection. In my case it was "1" and my output was:

```
  Device URI                                       Model                    Name     
  -----------------------------------------------  -----------------------  ---------
  hp:/net/hp_LaserJet_1320_series?ip=xxx.xxx.xxx.xxx  hp_LaserJet_1320_series  NPIC3B9E4

Found 1 printer(s) on the 'net' bus.
```

Copy the Device URI, in this case "hp:/net/hp_LaserJet_1320_series?ip=xxx.xxx.xxx.xxx".

Now that you have all the information you need, you can now add the printer.

[list=1][*]Go to System > Administration > Printing
[*]Add Printer [*]Select "Other" and type (or paste) the Device URI acquired using hp-probe and click Forward [*]Select "Generic" and click Forward [*]Select PCL 6/PCL XL Printer > Generic PCL 6/PCL XL Printer - CUPS+Gutenprint v5.2.5 Simplified [*]Click Forward then Apply and you're done![/list]

I found that if I chose PCL 5e that some files (larger, typically images) would fail to print. I was blown away as to how fast the Generic PCL 6 driver worked (it was better than HP's Windows driver). I have yet to fully test this driver but so far it looks good. I can have the HP P2055dn returned now that I have this old workhorse going again.

---

