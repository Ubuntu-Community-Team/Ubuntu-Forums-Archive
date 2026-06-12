---
title: "Home Network: Samba vs. Ubuntu Server?"
date: 2010-03-08
forum: Networking &amp; Wireless
---

### Post by gohargod on 2010-03-08
I have 4 PCs in my house running off of my Uverse dhcp server: 3 Ubuntu desktop installs and one XP install (my work laptop). Right now, everything works great, so I'm hesitant to change...but I'd like to add file/printer sharing and I'm wondering what the best option is.

Unfortunately, I don't have a lot of experience with Ubuntu. Should I replace one of the Ubuntu Desktops with Ubuntu Server? Should/can I just download Samba and install it on one of the Ubuntu desktops? What other options should I consider?

Any thoughts/guidance/links would be appreciated.

---

### Post by adam814 on 2010-03-08
I'd just install samba on one (or all for that matter) of your desktops.  Ubuntu Server is very nice for what it was intended for (headless servers running somewhere in a rack in a datacenter), but I wouldn't opt for it over a usable desktop in a home network.

---

### Post by savanna on 2010-03-09
In Linux land, the difference between a "server" and a "desktop" is just the packages you add/remove ie unlike Windows you're not constrained to one once you've installed.

The Ubuntu server/desktop DVD's are just provided as a convenience - useful packages for a "desktop", etc.

To convert Ubuntu desktop to an "SMB server" you could (optionally) just disable/remove X, and install the samba server packages.

HTH.

---

### Post by johnson.d on 2010-03-09
For Sharing a file/printer using Ubuntu, desktop version with Samba installed would suffice.

File/Printer Sharing from Ubuntu:

1) Install Samba using the following:

$ apt-get install samba

2) Edit the /etc/samba/smb.conf file and see if these lines are uncommented,add these lines if not present for printer sharing.

[ printers]

comment = All Printers
path = /var/spool/samba
browseable = no
printable = yes

And add these lines for file sharing

[<share-name>]

path = /<share-name>
browseable = yes

Restart the Samba service by using the following command;

$ sudo /etc/init.d/samba restart.

Configuring the shared printer on a Windows Client:

i) Start menu-> Printers and faxes -> Add a printer
ii) A window will open click next
iii) Select "A network printer, or a printer attached to another computer" and click next
iv) Select "Connect to this printer (or to browse for a printer, select this option and click next)" 
Enter \\< ip-address >\<printer name as in ubuntu> and click next
v) It will connect to the printer and may say that the driver is not installed (if driver is present in Windows xp it will proceed without driver installation)
vi) Install the drivers
vii) It will prompt "Do you want to this printer as the default printer?". Select your choice an click next
viii) Click finish.

Configuration the shared printer on a Ubuntu Client:

1) Go to Gnome menu-> System-> Administration-> Printing.
2) A window will open, Click new.
3) Another Window will open. At devices, drop down Network printer, Click Windows Printer via Samba.
4) At the right hand side, There will be a box with 'smb://'. Here enter the ip-address and the printer name as follows:
smb://<ip-address>/<shared-name of the printer>
5) Choose the driver and finish the installation.

---

### Post by Peter09 on 2010-03-09
Try the following url on the machine with the printer (if its Ubuntu)
 
> [http://localhost:631](http://localhost:631)
It should strart the Cups utility which allows you to configure sharing for the printer.

---

