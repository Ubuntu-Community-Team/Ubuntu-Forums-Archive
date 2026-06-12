---
title: "sharing a printer"
date: 2010-03-04
forum: Networking &amp; Wireless
---

### Post by c0nfusedami on 2010-03-04
I've been looking around the forum for a while and have not found a really good way to network my printer that is connected to my Ubuntu 9.10 computer. I'm trying to access this printer from two apple macs running OSX 10.5, a windows XP PC, and a windows 7 pc. I've tried using cups and samba both individually and together. I would appreciate any suggestions.

---

### Post by Easy Limits on 2010-03-04
You could always buy a cheap ($35) print server from your local computer store and connect it to your network.  I have Ubuntu, XP, Vista and Mac on my network and the print server takes care of the head aches.

---

### Post by c0nfusedami on 2010-03-04
I would really like to using my linux computer to do it. I know it's possible I just don't know how.

---

### Post by Fire_Chief on 2010-03-05
I've had excellent success using [this site]("http://www.kremalicious.com/2008/06/ubuntu-as-mac-file-server-and-time-machine-volume/") to setup Appletalk on my Ubuntu box to allow my wife's Macbook to print to the printer. It's pretty solid. The page also includes file server access but I've not been able to make that work yet.

Regarding the share with the Windows systems, [this thread]("http://ubuntuforums.org/showpost.php?p=1561331") suggests the CUPS method and it being faster/more reliable than using samba.

Cheers!

---

### Post by c0nfusedami on 2010-03-06
regarding apple talk is that only for file sharing or could it be configured to share printers too?

---

### Post by Fire_Chief on 2010-03-06
Works for printing from Macs as well as file sharing.

---

### Post by c0nfusedami on 2010-03-06
when I attempt to install netatalk with the synaptic package manager I get this error.

E: libpam-cracklib: subprocess installed post-installation script returned error exit status 1

Anyone know what it means?

---

### Post by johnson.d on 2010-03-08
You can try using Samba for sharing the printers Connected to Ubuntu 9.10 Machine using the following steps:

1) Configuration on Ubuntu side:

Edit the /etc/samba/smb.conf file and see if these lines are uncommented,add these lines if not present

[ printers]

comment = All Printers
path = /var/spool/samba
browseable = no
printable = yes

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

3) You can configure the shared printers from samba in a mac client using the following link:

[http://support.apple.com/kb/HT3049](http://support.apple.com/kb/HT3049)

4) In case you are using Ubuntu client you can use the following steps:

1) Go to Gnome menu-> System-> Administration-> Printing.
2) A window will open, Click new.
3) Another Window will open. At devices, drop down Network printer, Click Windows Printer via Samba.
4) At the right hand side, There will be a box with 'smb://'. Here enter the ip-address and the printer name as follows:
smb://<ip-address>/<shared-name of the printer>
5) Choose the driver and finish the installation.

---

### Post by c0nfusedami on 2010-03-08
Now that's an answer that could not be more perfect. I'm going to give those steps a try and I'll post the results.

---

### Post by c0nfusedami on 2010-03-09
Thank you. Samba worked perfectly for my windows XP computer however I couldn't get my apples to print from it. It saw the printer however it never got authorised to use it. I'm going to attempt netatalk unless someone has a way around this issue.

---

### Post by c0nfusedami on 2010-03-09
Update: 
I got my apple computers to print by going into /etc/samba/smb.conf as a supper user and setting the [profiles] to... 

[profiles]
   comment = Users profiles
   path = /home/samba/profiles
   guest ok = yes
   browseable = no
   create mask = 0600
   directory mask = 0700

This was originally commented out and also the guest ok was set to no. My understanding of these commands is that you can set it up so that only those who you have desinated able to use your printers are able to. thank you everyone for your help.

---

