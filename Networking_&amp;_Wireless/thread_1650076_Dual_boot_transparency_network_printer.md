---
title: "Dual boot transparency: network printer"
date: 2010-12-21
forum: Networking &amp; Wireless
---

### Post by Eaglebird on 2010-12-21
Hi,

I have a headless machine set up on my LAN which is dual boot, Ubuntu 10.04 SE and Windows.

I have a printer attached to it. (HP Deskjet D1500 series)
I also have a shared folder located on the machine.

Through SMB I've been able to recreate the share in Ubuntu to point to the share on Windows. When the machine is in either OS, the share can be resolved, browsed, edited, etc, from \\host\sharename.

Through SMB I've also been able to share a printer attached to the machine (and print to it). I have a problem though:

When the machine is in either OS, it is possible to use the same scheme to access the shared directory. This is not true with the printer. 
When in Windows: 
[LIST]
My Windows 7 x64 machine can connect to the printer, look for drivers, and when it doesn't find drivers in \\host\print$, it uses its own.
My W7x64 machine can print a test page, and any other pages for that matter.
My W7x64 machine lists the printer as "HP Deskjet D1500 series"
I do not have to re-add the printer.
[/LIST]

When in Ubuntu:
[LIST]
I have to re-add the printer to my W7x64 machine.
I have to specify the driver to use, regardless of whether I use the same print$ directory.
Re-adding the printer gives me a network printer by the name of the printer, not the description (e.g. "HP Deskjet D1500 series")
[/LIST]

My goal is to mimic the transparency of the shared directory, so whereas I've created a shared directory in Windows that persists between OSs, I want to create the network printer to persist across OSs.
I can print to the printer in either OS, but the "printer" I have when the dual boot machine is in Ubuntu is NOT the "printer" I have when it's in Windows.

I need to accomplish this to avoid booting the machine into Windows for a client to print something. It seems very odd that I can make Apache, PHP, MySQL, shares, and common files persist/be identical between OSs, but not network printers.

I've worked this for a few days now, exhausting what I can in information on SMB and CUPS to no avail. I am exhausted myself. If you need more information please let me know, I look forward to fixing this.

---

### Post by Eaglebird on 2010-12-21
shameless bump

---

### Post by slooow on 2010-12-21
Not really sure what your problem is. A headless windows machine? Is that a windows server?
Do you want to print from a windows machine to a ubuntu server which has a printer attached? Please clarify.

---

### Post by Eaglebird on 2010-12-22
> **slooow said:**
> Not really sure what your problem is. A headless windows machine? Is that a windows server?
Do you want to print from a windows machine to a ubuntu server which has a printer attached? Please clarify.

I have a server that dual boots between Ubuntu and Windows.
Attached to it is a printer shared to the LAN.
I want to make the appearance of the printer when the server is in Ubuntu the same as that of its appearance when it's in Windows.

---

