---
title: "printing issues"
date: 2005-12-19
forum: Networking &amp; Wireless
---

### Post by RBH on 2005-12-19
i have a microsoft home network with several pc's on it. i have since gotten this linux box on that microsoft network. i can see all the computers and shared folders, files, etc. i need to get connected to the printer shared by my network. i went through the linux printer setup and it sees the printer, which is located on a windows xp box. it had the drivers installs and but it wont print a test page. i have been to hp website and found linux drivers and software for the printer and went through the whole process of installing them using the terminal. again, it sees the printer and everything looks like it sets up, but fails to print a test page. it says the job is printing and i have no errors on my printer. i have also tried just printing a text doc with the same results.

any suggestions? thanks

i will add, i have shut the firewall down on the xp machine this printer is hooked to, and i have installed the components for allowing unix printing on that xp machine. the only thing i question is maybe the fact this printer is hooked to the xp machine by usb. could this be an issue?

---

### Post by Koybe on 2005-12-19
Try going on to [http://www.linuxprining.org](http://www.linuxprining.org), dowload the ppd file associated to your printer, and put it in /usr/share/cups/model/, restart cups services (cupsys i think) and select the new file for you printer.

*cross your fingers* :D

---

### Post by RBH on 2005-12-19
maybe thats where i am messing up. i am choosing windows printer under the options when adding a printer, since the printer is on a windows box. when i choose windows printer, it sees the computer the printer is on, and it sees the printer. i have been to the site you have linked and downloaded the file for this printer. when it asks to install the driver i tried the default one and i have tried the downloaded one. the printer says its ready, and everything seems fine. it give me no errors when test printing and my printer logs no errors, it just nothing happens. i will try what you suggested and see where it gets me. thanks.

---

### Post by RBH on 2005-12-20
weeeeeeeeeeeeelllllllllllllllllll, several days of fighting with this i finally have a resolution that worked. i bought a second printer just for my linux boxes!:D 

after alot of headaches i found it was the xp box denying access to the printer. i had shut the firewall off, installed unix printing components, had file and print sharing on and still it kept blocking me. i have no idea what else in xp could be changed but i said to heck with it and just bought a second printer and now the world is right. if anyone reads this and has a solution let me know, but for now i have surrendered.

---

### Post by hobbes_opus on 2006-01-09
If it makes you feel any better, I found the same situation with Breezy and a Windows ME shared printer.  The good news was that it worked on Hoary Hedgehog, the bad news is that it hasn't worked since installing Breezy.

Hmmm.

---

### Post by firecat53 on 2006-01-09
I managed to get the printer (USB connected) attached to my XP box able to print from the Linux machines. I originally did it all from the gnome printer setup, other than setting up samba. You need the smbfs package on your Linux machine, and I created a user on my Linux box with the same username as the username on the XP box that's always logged in. If you have the printer shared on XP and samba set up correctly, a smbtree should show you the name of the printer. The key is getting the name and location of the printer exactly correct.
My XP box is named "business" and my /etc/cups/printers.conf file looks like
```
# Printer configuration file for CUPS v1.1.23
# Written by cupsd on Sat Dec  3 11:20:44 2005
<DefaultPrinter PSC-2175>
Info PSC-2175
DeviceURI smb://username:password@BUSINESS/hp2175
State Idle
Accepting Yes
JobSheets none none
QuotaPeriod 0
PageLimit 0
KLimit 0
</Printer>

```

It does work :) Although I do understand your frustration......it took me awhile to figure it out.

Scott

---

### Post by Norradj on 2006-01-13
Thank you "firecat53"!

I have been struggling this issue for some time and I thought that it was not an easy solution available. (using Ubuntu breezy)


Printer in a win xp (USB) Brother HL 2030  (network name BrotherH)

0. Enable in global settings from printer set up meny: "find network printer"
(This has to be done first to open the printer port to network)
1. New printer
2. tick network printer and choose "windows SMB-printer".
3. Password authentication will be required for host connection.
4. The host will show up with its name, and pick that.
5. Step down to printer and write your printer network name, user name and password for the win xp with the printer.
6. print test page.

---

