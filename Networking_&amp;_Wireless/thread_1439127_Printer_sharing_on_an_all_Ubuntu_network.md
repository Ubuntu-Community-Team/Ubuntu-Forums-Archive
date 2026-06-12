---
title: "Printer sharing on an all Ubuntu network"
date: 2010-03-25
forum: Networking &amp; Wireless
---

### Post by Mylorharbour on 2010-03-25
Guys,
I have a printer which used to be connected to a Windows PC. We printed ok to that via a wi-fi router and Samba from our various Ubuntu laptops. However, as the Windows machine is used less and less we've connected the printer to an Ubuntu desktop. We can file-share ok but how do the laptops set this printer up? The only options we seem to come across are for a local printer or a Windows one via Samba.

Could someone point us in the right direction?

Thanks

---

### Post by zerkig on 2010-03-25
Hi

You need to mention the make and model of the printer. 

I have two HP printers set up on karmic 9.10 a HP LaserJet P1005 and HP Photosmart c4380.  This is what I did but it will probably expose my noob status

1) Configure the wireless router to enable PnP  (Not sure about how safe that is but the photosmart is a PnP printer). Unplug router for 10 seconds and plug in again.

given the last step I probably did not need to do the following
2) I configured the pc with the LaserJet to have a static IP
3) I configured the Photosmart to have a static IP

4) installed hplip on the pc with the laser jet  which automatically set up CUPS (it should be listening on port 631 by default)
5) for the P1005 I had to tinker with loading firmware to the printer on every boot.
6) system --> administration --> printing   
         1) add the laserjet 
         2) check the shared in properties
         3) in the server settings check publish

on the laptops install hplip add printers and away you go.

Hope that was helpful or relevant

---

### Post by johnson.d on 2010-03-26
You can try using Samba for sharing the printers Connected to Ubuntu 9.10 Machine using the following steps:

1) Configuration on Ubuntu machine in which the printer is connected.

Edit the /etc/samba/smb.conf file and see if these lines are uncommented,add these lines if not present

```
[ printers]

comment = All Printers
path = /var/spool/samba
browseable = no
printable = yes
```

After editing the file, restart Samba service using the following command:

```
$ sudo /etc/init.d/samba restart
```

2) Configuration on windows client:

i) Start menu-> Printers and faxes -> Add a printer
ii) A window will open click next
iii) Select "A network printer, or a printer attached to another computer" and click next
iv) Select "Connect to this printer (or to browse for a printer, select this option and click next)" 
Enter \\< ip-address >\<printer name as in ubuntu> and click next
v) It will connect to the printer and may say that the driver is not installed (if driver is present in Windows xp it will proceed without driver installation)
vi) Install the drivers
vii) It will prompt "Do you want to this printer as the default printer?". Select your choice an click next
viii) Click finish.
ix) Try printing from Windows machine.

2) In case you are using Ubuntu client you can use the following steps:

1) Go to Gnome menu-> System-> Administration-> Printing.
2) A window will open, Click new.
3) Another Window will open. At devices, drop down Network printer, Click Windows Printer via Samba.
4) At the right hand side, There will be a box with 'smb://'. Here enter the ip-address and the printer name as follows:
smb://<ip-address>/<shared-name of the printer>
5) Choose the driver and finish the installation.
6) Now try printing from the Ubuntu System.

---

### Post by Mylorharbour on 2011-01-13
An old thread I know guys but  would you believe I've only just got this working reliably? I've been having major problems with networking over the last few months, thinking it was a lack of Ubuntu/Linux knowledge, but it turned out I had a faulty router (Netgear DG824PN) which kept losing attached devices. Installed a new router and up came the network.

So, having cracked that I turned again to this old chestnut. Johnson.d almost fixed it but I needed to make one more change to smb.conf (in blue below)


```
[printers]
comment = All Printers
browseable = no
path = /var/spool/samba
printable = yes
[COLOR="Blue"]guest ok = yes[/COLOR]
; read only = yes
create mask = 0700 
```

Cheers guys

---

