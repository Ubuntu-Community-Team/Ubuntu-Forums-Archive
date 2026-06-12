---
title: "Sharing Folder &amp; Printers on 9.10 desktop"
date: 2010-03-18
forum: Networking &amp; Wireless
---

### Post by winhaung on 2010-03-18
Can I share Folder & Printers on 9.10 Desktop? I want to use that shared folder & printers from windows. Thz

---

### Post by johnson.d on 2010-03-19
Yes, you can share folders and printers from Ubuntu 9.10 Desktop to be accessible from windows. You can use Samba to share folders and printers.

I) You can use the following steps to share folders and printers from Ubuntu Desktop:

1) Samba installation:

You can install Samba using the following command:

```
$ sudo apt-get install samba
```

2) File Configuration:

Edit the /etc/samba/smb.conf file and see if these lines are uncommented,add these lines if not present. These lines enables sharing of printer.

```
[ printers]

comment = All Printers
path = /var/spool/samba
browseable = no
printable = yes
```

Now to share the folder you need to append the following lines:

```
[<share-name>]

path = /<share-path>
read only = no
browseable = yes
guest ok = yes
```

Restart the service now using the following command:

```
$ sudo /etc/init.d/samba restart
```

Now you have shared the folders and printers using Samba.

II) Adding the printer to the windows client:

i) Start menu-> Printers and faxes -> Add a printer
ii) A window will open, click next.
iii) Select "A network printer, or a printer attached to another computer" and click next
iv) Select "Connect to this printer (or to browse for a printer)", select this option and click next. 
Enter \\< ip-address >\<printer name as in ubuntu> and click next.
v) It will connect to the printer and may say that the driver is not installed (if driver is present in Windows xp it will proceed without driver installation).
vi) Install the drivers.
vii) It will prompt "Do you want to this printer as the default printer?". Select your choice and click next.
viii) Click finish.

---

