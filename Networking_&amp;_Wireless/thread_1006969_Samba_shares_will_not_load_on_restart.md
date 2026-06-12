---
title: "Samba shares will not load on restart"
date: 2008-12-09
forum: Networking &amp; Wireless
---

### Post by joshag1 on 2008-12-09
I have been having one heck of a time with network and printer shares. Once I think I have it then it disappears. 

i have managed in the past to get my xp machines to see the local printers on the ubuntu 8.10 machine but never got them to print. Always get the "connection interrupted" message.

i watch the status of my printers and realize that every time i restart or reboot the printers don't maintain their "published" status. i have to go back and and not set the permissions but just "OK" them. Why??? None of my shares are ever seen on the xp machines. I have read and re-read every post i can find on the web and still i am unable to config my samba???

Should it really be this hard???

---

### Post by superprash2003 on 2008-12-10
post output of smbtree from terminal

---

### Post by joshag1 on 2008-12-10
not gonna lie about being a novice here. I really need to rephrase my problem:

Shares seem to be there (can find ubuntu pc on xp but not able to browse). 
It is my printers that are giving me the most grief. Not presently worried about file sharing from this pc.

Using 8.10, I go to sys-admin-printing. I can see all my printers including the default. When I go to each one individually the are all set up to share. When I check the policies, I am told that the printer is not published. When I check the server settings it is checked to "share connected printers". I hit OK and everything is again published. Close the printer window and exit, go back in and again nothing is published. The settings are not staying.

I tried the smbtree and was told that this was a smbclient function. I am running samba server.

---

### Post by superprash2003 on 2008-12-11
smbtree command is used to view local shared folders and printers .. did you try typing smbtree in the terminal?didnt you get an output?

---

### Post by joshag1 on 2008-12-11
sorry, just reloaded 8.10. Was first using a version calling itself "ubuntu extreme". I do however have the same problem. 

smbtree output:

WORKGROUP
	\\XMAS           		Laptop
cli_start_connection: failed to connect to XMAS<20> (0.0.0.0). Error NT_STATUS_HOST_UNREACHABLE
	\\UBUNTU-OFFICE  		ubuntu-office server (Samba, Ubuntu)
		\\UBUNTU-OFFICE\downloads      	
		\\UBUNTU-OFFICE\music          	
		\\UBUNTU-OFFICE\public         	
		\\UBUNTU-OFFICE\Photo-Printer-720	Dell  Photo Printer 720
		\\UBUNTU-OFFICE\Photosmart-8400-series	HP Photosmart 8400 series
		\\UBUNTU-OFFICE\IPC$           	IPC Service (ubuntu-office server (Samba, Ubuntu))
		\\UBUNTU-OFFICE\print$         	Printer Drivers

Thanks in advance.....

BTW, I do enjoy your tutorials!

---

### Post by joshag1 on 2008-12-11
Shares are now loading after ubuntu reload.

---

### Post by superprash2003 on 2008-12-12
has the printer also started working?? your printer seems to be shared.. while creating a network printer in windows xp to connect to ubuntu, does windows successfully see the ubuntu printer?? if not mention its full link i.e. \\UBUNTU-OFFICE\Photo-Printer-720 Dell Photo Printer 720 or \\UBUNTU-OFFICE\Photosmart-8400-series HP Photosmart 8400 series .. also post output of cat /etc/samba/smbusers

---

### Post by joshag1 on 2008-12-12
I can see the printers but cannot get them to print. Get a "connection interupted" message?

Seems that upon seeing them xp wants to load the drivers from the host. Linux drivers obviously make xp uspet so I use windows drivers for them. Printing a test page is when I get the message about connection/

---

### Post by superprash2003 on 2008-12-13
doesnt windows find the driver automatically??

---

### Post by joshag1 on 2008-12-13
XP always looks to the host for the drivers and if it can't get them then install manually. I have installed manually so there is no problem with object recognition just communication. Just seems that as soon as a job is sent, communication breaks???

---

