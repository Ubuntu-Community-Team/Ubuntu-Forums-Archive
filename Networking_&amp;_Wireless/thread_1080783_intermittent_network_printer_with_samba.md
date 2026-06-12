---
title: "intermittent network printer with samba"
date: 2009-02-25
forum: Networking &amp; Wireless
---

### Post by cr0wn3r on 2009-02-25
My network consists of 
- 2 vista desktops
- 1 xp desktop
- 1 ubuntu desktop 8.10 intrepid
all connected via a gigabit switch.

The switch is connected to a wireless router which adds vista laptops to the network as well.

Amongst other things, the Ubuntu machine is acting as a large network drive and, using Samba, is doing a great job. It is accessible to all the other machines at good speeds.

Recently I added a printer (HP Deskjet 5550) to the Ubuntu machine and have been trying to use that through Samba as a shared resource on the network, but I have run in to lots of problems:

- It works with most of the machines, but not all the time. Sometimes I send print jobs to it and they just disapear without even showing up on the CUPS jobs list.

- When it does work it is often (but not always) really slow, taking anything up to 5 minutes to start printing a small text file.

- After setting up the windows machines to print to the printer over the network, normally quick tasks take ages. For example, with the printer installed for my main Vista desktop it takes 2 minutes every time to open a small image in photoshop, or create a new blank canvas. If I delete the printer using the Vista control panel then it goes back to normal and those tasks are virtually instant. 

- If I view the printer queue from a windows machine I get the warning "failed to open, retrying" or "Printer not accessible" in the top of the info window that opens.

If I install the printer directly on to a PC, using the same driver, I have none of those problems when I print locally, so I dont think it's a driver problem. My network is perfectly happy playing divX video files straight from a Samba share so I dont think theres a major issue with the quality of the network in general.

I would be so greatful for some help. I really dont know what to look for, or how to troubleshoot this.

For the record, I have tested with all antivirus and firewall software disabled and it hasnt made any difference.

Thanks

---

