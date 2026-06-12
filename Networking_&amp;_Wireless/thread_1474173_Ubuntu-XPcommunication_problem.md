---
title: "Ubuntu-XP:communication problem"
date: 2010-05-05
forum: Networking &amp; Wireless
---

### Post by Chemham on 2010-05-05
[FONT=Calibri][SIZE=3]I am a new convert to Ubunto  --  The problem I am having is I cannot get one computer with Ubuntu 9.10 and another computer with Windows XP to communicate properly.  Originally I had two XP machines and they did communicate properly so the router and the wireless I am using seem to be set up fine.  One of these XP machines was converted to Ubuntu 9.10.  Actually I have come a long way with this and just need a last bit of help to get it going properly.[/SIZE][/FONT]
[FONT=Calibri][SIZE=3] [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]Each machine can be successfully pinged with the other machine.  The Ubuntu machine sees the XP machine just fine.  It sees all the shared folders and files.  The XP machine is not permitted to enter what it sees on the Ubuntu machine. [/SIZE][/FONT]
[FONT=Calibri][SIZE=3] [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]With Ubunto when I hit Network, I can see listed:[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]a) Guest-Dell-Laptop (the name of the machine running Ubuntu)[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]clicking on guest-Dell Laptop I can see all the shared folder and files on the Ubuntu machine[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]b) LenovoT61P (the name of the XP machine)[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]clicking on this I see all the folder/files on the XP machine[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]c) PS-6D7282 (this is the wireless print server on the XP machine[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]d) Windows Network[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]clicking on Windows Network I see Workgroup (the name of the workgroup on the XP machine)[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]clicking on Workgroup, I can see Guest-Dell-Laptop (again, this is name of the Ubunto machine) and I can see both LenovoT61P & PS-6D7282 (the name of the wireless print server on the XP machine).[/SIZE][/FONT]
[FONT=Calibri][SIZE=3] [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]Right clicking on items a, b, c, & d above, it will not allow to me see the Permissions.[/SIZE][/FONT]
[FONT=Calibri][SIZE=3] [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]All is working OK so far with the possible exceptions of the Permissions issue.[/SIZE][/FONT]
[FONT=Calibri][SIZE=3] [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]With the XP machine when I drill down to Windows Microsoft Network, I can see:[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]Guest –Dell-laptop server (Samba, Ubuntu) (GUEST-DELL-LAPTOguest-Dell-laptop server (Samba, Ubunutu))[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]This is exactly how it appears![/SIZE][/FONT]
[FONT=Calibri][SIZE=3]When I click on this, however, I get a message that this sever is not available and that I may not have permission to access it.  It also says the parameter is incorrect.[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]I can also see LenovoT61p (the XP machine) & my wireless print server- PS-6D7282.[/SIZE][/FONT]
[FONT=Calibri][SIZE=3] [/SIZE][/FONT]
[SIZE=3][FONT=Calibri]So the bottom line is that the Windows XP machine sees the Guest-Dell-Laptop computer (running Ubunto) but I seem not to have permission to enter it.  And, the Ubunto machine will not let me see Permissions for all the choices it gives when I look in Network.  [/FONT][/SIZE]
[FONT=Calibri][SIZE=3] [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]Some additional info:[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]I think the Firewall on Ubuntu machine is disabled.  How do I check for sure?[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]The router does have a firewall but not sure if this relevant.[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]Both machines have wireless Internet access.[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]In smb.conf, I kept workgroup = WORKGROUP.  I made no mods to this file.[/SIZE][/FONT]
[FONT=Calibri][SIZE=3] [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]My guess is that I have to set something up on the Ubuntu machine to allow my XP machine to see all.[/SIZE][/FONT]
[FONT=Calibri][SIZE=3] [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]I hope I did not sound like I know too much about Linux.  I am new to all this.[/SIZE][/FONT]
[FONT=Calibri][SIZE=3] [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]Any help is greatly appreciated,[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]Chemham[/SIZE][/FONT]

---

### Post by Chemham on 2010-05-06
[SIZE=3][FONT=Calibri]Can anyone help me to get my Windows XP machine to see my Ubuntu (9.10) machine?  They both can ping each other OK.  The Ubuntu machine sees the XP machine and folders/files ok.  I do have Samba & Swat installed.  [/FONT][/SIZE]
[FONT=Calibri][SIZE=3] [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]Any help is greatly appreciated,[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]Chemham[/SIZE][/FONT]

---

### Post by Iowan on 2010-05-07
Threads merged.
Is windows using the "WORKGROUP" workgroup?

---

### Post by Chemham on 2010-05-07
Iowan,
Yes,windows is using the "WORKGROUP" workgroup.
Tks,
Chemham

---

### Post by Chemham on 2010-05-08
[FONT=Calibri][SIZE=3]Well, I figured out a solution to this problem. Maybe this will help others.[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]It looks like my XP machine did see the Ubuntu machine all the time.  The way I got to access the Ubuntu machine is this way:[/SIZE][/FONT]
[FONT=Calibri][SIZE=3] [/SIZE][/FONT]
[SIZE=3][FONT=Calibri]On the XP machine click the start button, click run and type in:
[COLOR=black][[COLOR=#0066cc]\\IPOFMYUBUNTUCOMPUTER[/COLOR]]("file://ipofmyubuntucomputer/")[/COLOR][/FONT][/SIZE]
[FONT=Calibri][SIZE=3]Now I see all of my shared folders on my Ubunto machine.  Crisis is over![/SIZE][/FONT]
[FONT=Calibri][SIZE=3] [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]I do have a question however.  On the XP machine, when I drill down to Windows Microsoft Network, I can see listed the name of the Ubuntu machine (guest-Dell-laptop) but when I click on this, however, I get a message that this sever is not available and that I may not have permission to access it.  It also says the parameter is incorrect.  Why is this?  [/SIZE][/FONT]
[FONT=Calibri][SIZE=3][/SIZE][/FONT] 
[FONT=Calibri][SIZE=3]If there is a simple way to resolve this, this would good too.  [/SIZE][/FONT][FONT=Calibri][SIZE=3]Any help is greatly appreciated,[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]Chemham[/SIZE][/FONT]

---

