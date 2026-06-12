---
title: "Setting up a print network via CUPS"
date: 2009-01-29
forum: Networking &amp; Wireless
---

### Post by Scunnered on 2009-01-29
It has been suggested that I use CUPS to network my Epson Stylus R265 printer in order to let my partner access it from her XP laptop.

When Google displayed "***CUPS web interface on Ubuntu has no network printer autodiscovery -- "snmp" backend is disabled***" this went totally over my head and sent me running to the forum.

Firstly is the above statement still valid or in version 8.10 is the printer autodiscovery enabled?

If it is disabled how do I go about setting up a network?  Is there an idiots guide available as I am totally new to Ubuntu.

I am attempting to keep the peace as my partner is fed up running back and forward to print her work at my desk. This method looks really good to a Scot as it appears fiscally efficient in relation to a wireless printer.

Your kind assistance will be appreciated

---

### Post by icheyne on 2009-01-29
[http://www.kdedevelopers.org/node/2127](http://www.kdedevelopers.org/node/2127)

---

### Post by Scunnered on 2009-01-30
Many thanks Iain

I saw that item but as it was KDE I did not follow through as I am working with Gnome and am totally unsure of what works with which.

I followed through on what you advised and was told that file existed and the CUPS information confirmed that my printer was the default.

Having got that far down the road where do I go from here.  How do I get the XP laptop to print on the R265?

Ian

---

### Post by icheyne on 2009-01-30
KDE and Gnome are just user interfaces. CUPS is a back-end system that is common to both Kubuntu and Ubuntu, so this command should work.

The instructions on this web page should let you print in Windows XP using Ubuntu as the print server.

[https://help.ubuntu.com/community/NetworkPrintingFromWinXP](https://help.ubuntu.com/community/NetworkPrintingFromWinXP)

More help here:

[https://help.ubuntu.com/community/Printers](https://help.ubuntu.com/community/Printers)

---

### Post by Neural oD on 2009-01-30
cups is good - from xp the easiest way that i found was to point it to an ip address. lets say the ip address of your machine is 166.20.20.1 then in xp - point to it using something like this //166.20.20.1/printers/name-of-your-shared-printer. 
hope my syntax is correct - haven't done this for a while - but hopefully it will put you on the right path. Others may have an easier - better solution

---

### Post by Scunnered on 2009-01-30
icheyne & Neural oD 

My thanks to you both for your assistance.

Can we assume that I am as thick as the proverbial two planks and treat me accordingly.  

**Iain**

I was able to work through the first part of the instructions in 8.10 but I fell totally at the wayside with the Windows XP. 

I initially deleted the EPSON Stylus Photo R265 from the XP printers folder and then went to add a printer. I then attempted to **type in for the printer URL:**   

it is at this point that things go totally wrong.  Please correct me on this as I can't get my head around what is being conveyed.

http://<hostname>:631/printers/<printername> is shown as being required so I assumed that what was required was :

[http://ian-laptop:631/printers/EPSONStylusPhotoR265](http://ian-laptop:631/printers/EPSONStylusPhotoR265) but this only displayed an error message.  I substituted my IP address using the figures only and again nothing.

When I check the System > Administration > Printing > Properties >Settings the description is the full printer name as shown and the location is ian-laptop so it looks if I have provided the correct information.

Where am I going wrong?  Sorry to be such a pain.

---

### Post by icheyne on 2009-01-30
Sorry, but I do not have an XP machine, so I can't tell you exactly how to do it.
Try **browsing** for shared printers or in the add printer wizard try something like this:
```
\\servername\printername or \\servername\printers\printername.
```

---

### Post by Scunnered on 2009-02-01
Thanks Iain

It is just like the thing that like myself you are working purely in Linux.
I am guddling along with Google but so far I am still seeking a resolution.

Will keep on trying 

THanks again

Ian

---

### Post by cariboo on 2009-02-01
To setup a printer using the cups web interface, just open your browser and type:

[http://localhost:631](http://localhost:631)

Once the web interface is open. click on the Administration tab then click add printer, it should auto detect your printer, and from there it is just a matter of filling in the blanks. It isn't that much harder then setting up a printer in Windows.

Jim

---

