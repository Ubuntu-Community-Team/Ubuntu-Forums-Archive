---
title: "Trouble Connecting To Workgroup And Printer"
date: 2010-05-18
forum: Networking &amp; Wireless
---

### Post by X-Windows on 2010-05-18
First time Linux user here, so please bear with me. I have recently installed Ubuntu 10.04 64-bit and am very impressed at what an excellent OS it is :). However I am having trouble connecting to my wireless network/printer. Breakdown of my setup: Modem > Router > Vista x64 PC > HP Printer. The printer is shared off my wireless network, not the router (does not have a seperate IP address). I have no trouble connecting and printing to it off my duel boot Windows, I just *can't* connect to it with Ubuntu. I am also unable to connect to my workgroup, probably part of the issue. When I go to Places > Network > Windows Network I can see my workgroup name, but when I open my workgroup it takes ~1 min then returns this error: "**Unable to mount location** **Failed to retrieve share list from server**". Also I am unable to ping my workgroup's computer name "ping COMPUTERNAME" does not work, but "ping 192.168.1.x" does.
 
Why would Windows be able to see and print to this and Ubuntu cant?
 
I do have Samba installed, it shows a shared directory "/var/lib/samba/printers" with read/write permissions and visibility. Aside from that I dont see anything to do.
 
I'm stumped here, after hours of Googling this, I found no solution. I would love to transition over to Linux as I am fed up with Windows, but not before I "test the waters" as it were. Being unable to print off networked windows printer is a huge setback :(.

---

### Post by X-Windows on 2010-05-18
Half the problem is resolved. For anyone else with this problem, here is what I did to use a windows networked printer. Applications > Ubuntu Software Center > Uninstalled Samba (probably unnecessary). System > Administration > Printing > Server > New > Printer > Network Printer > Windows Printer via Samba. Here is where I messed up before. In the smb:// box the syntax is _*IPAddress/Printername*_. In my case it was ***192.168.1.2/HP OfficeJet G85***. For some reason my printer does not show up in the Browse wizard next to the text field.

I still am having errors trying to open my workgroup. The only thing I have left to do is configure file sharing with my windows box and I'll be one happy penguin! :P

---

