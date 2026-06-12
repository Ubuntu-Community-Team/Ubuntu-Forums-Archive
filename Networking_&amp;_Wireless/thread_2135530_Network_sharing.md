---
title: "Network sharing"
date: 2013-04-14
forum: Networking &amp; Wireless
---

### Post by bigdes on 2013-04-14
Could anybody please help me i've just purchased a hp eprint printer. Everything is working except whenever I go to scan a document from the printer to a shared folder a message comes up on the printer " cannot connect to \\computername\sharedfolder\documents. Make sure the remote computer is turned on" It is showing up on the gigolo as documents on bigdes80-desktop. Is there any settings I need to apply to allow the printer to scan to the sharefolder on my computer. I'm using ubuntu 12.10 :confused:

---

### Post by Morbius1 on 2013-04-14
> It is showing up on the gigolo as documents on bigdes80-desktop. Is  there any settings I need to apply to allow the printer to scan to the  sharefolder on my computer. I'm using ubuntu 12.10 
You host name is 1 character too long for Samba / SMB. You can change the name for network purposes by:

Edit smb.conf as root:
```
gksu gedit /etc/samba/smb.conf
```
Add the following line under the workgroup line in the [global] section:
```
netbios name = bd80-desktop
```
[COLOR=#0000cd]*Doesn't have to be that exact name but keep it at 15 characters or less in length*[/COLOR]
Then restart samba services:
```
sudo service smbd restart
sudo service nmbd restart
```
Every time you restart samba the network has a fit so wait 5 minutes before trying to connect to the share.

---

### Post by bigdes on 2013-04-14
I have got the samba name changed when into gigolo to set the bookmark name as bd80-desktop /hit auto-connect/ service type SSH/ printer IP address/ added printer port/ folder: documents/ entered my computer user name and hit add. An Error message was then displayed stating  "Connection refused by server" Just wondering does anybody have any solutions and is the proper way to confirgure the network sharing. Just a note that the printer is wireless. Have a tv and dvd player connected to the computer and no issues with them and they are wired. I was just wondering is the problem to do with the printer being wireless.

---

### Post by Morbius1 on 2013-04-14
You are confusing me by your references to Gigolo since that is used to connect to a someone else's share not your own. And I'm not sure what SSH has to do with any of this.

I'm doing this from memory but don't you have to define the network folder that you want to scan to on the printer itself?

That means you have to create a samba share on the Ubuntu machine and point the printer to that share. Based on your posts it's : \\bd80-desktop\documents

Maybe if you post the output of the following commands it will clear things up:
```
testparm -s
```
```
net usershare info --long
```

---

### Post by bigdes on 2013-04-15
Sorry about confusing the issue I'm still fairly new to ubuntu and I'm always learning. I can scan things from the computer to the printer but I can't scan from the printer to the computer. You will see that it mentions below about the 2tb don't worry about that as is being shared with the tv and dvd player. It is just the document folder that I want to share with the printer.


bigdes80@bigdes80-desktop:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
    netbios name = BD80-DESKTOP
    server string = %h server (Samba, Ubuntu)
    map to guest = Bad User
    obey pam restrictions = Yes
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    unix password sync = Yes
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    dns proxy = No
    usershare allow guests = Yes
    panic action = /usr/share/samba/panic-action %d
    idmap config * : backend = tdb

[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    print ok = Yes
    browseable = No

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers
bigdes80@bigdes80-desktop:~$ net usershare info --long
[des]
path=/home/bigdes80/Documents/des
comment=
usershare_acl=Everyone:F,
guest_ok=y

info_fn: file /var/lib/samba/usershares/sharedfolder is not a well formed usershare file.
info_fn: Error was Path is not a directory.
info_fn: file /var/lib/samba/usershares/2tb hard drive is not a well formed usershare file.
info_fn: Error was Path is not a directory.
[Documents]
path=/home/bigdes80/Documents
comment=
usershare_acl=Everyone:F,
guest_ok=y

info_fn: file /var/lib/samba/usershares/action 4 is not a well formed usershare file.
info_fn: Error was Path is not a directory.
bigdes80@bigdes80-desktop:~$ 


Thanks very for all your help I really appreciate it.
Des

---

### Post by Morbius1 on 2013-04-15
OK, you have 2 samba shares - samba usershares to be specific - meaning that you created them from Nautilus so Linux permissions have already been adjusted.

Try to connect to them from the Ubuntu machine itself. For example:
```
nautilus smb://bd80-desktop/documents
```
If that doesn't work try it this way:
```
nautilus smb://bd80-desktop.local/documents
```
And if that doesn't work try it by ip address:
```
nautilus smb://192.168.0.100/documents
```
[COLOR=#0000cd]*Changing 192.168.0.100 to the ip address of the ubuntu machine.*[/COLOR]

Which ever one works is the one you want to use on the printer to point to the Ubuntu machine:
\\bd80-desktop\documents
\\bd80-desktop.local\documents
\\192.168.0.100\documents

---

### Post by bigdes on 2013-04-15
Got the shared folder opening from the command using **nautilus smb://bd80-desktop/document **but the printer network folder setup doesn't reconize it. But it reconises it this way**\\bd80-desktop\documents**. But the terminal doesn't reconise it. So I'm sitting with two commands that works on one or the other. But it would great to have one command that wouldn't conflict with the computer or the printer. Below is the two copy's of the screen with the two different commands. 
Any solutions please 
[-o<


Scan  >  Network Folder Setup **Network Folder Setup**

 

       **Scan to Computer**


[LIST]
[*]»[Webscan]("https://192.168.1.80/#hId-pgWebScan") 
[/LIST]

**Scan to E-mail**


[LIST]
[*]»[Scan to E-mail Setup]("https://192.168.1.80/#hId-ScanToEmailOverview") 
[*]»[Outgoing E-mail Profiles]("https://192.168.1.80/#hId-EmailAccounts") 
[*]»[E-mail Address Book]("https://192.168.1.80/#hId-EmailContacts") 
[*]»[E-mail Options]("https://192.168.1.80/#hId-CommonEmailData") 
[/LIST]

**Scan to Network Folder**


[LIST]
[*]»[Network Folder Setup]("https://192.168.1.80/#hId-NetworkFolderAccounts") 
[/LIST]



       Modify the fields marked in red, and then click "Next". Fields marked with '*' are required.
[LIST]
[*]Network Path: Invalid input. 
[/LIST]

  **Step 1 of 4: Network Folder Information**

   Display Name *


 Network Path *
[B]\\bd80-desktop\documents
[/B]

  The device might need to authenticate itself on your network before  it can save scanned documents to a network folder. Enter your Windows  username and password to allow this authentication to take place so that  the device can have write access to the selected network folder.
 
    User Name
xxxxxxxxx


 Password
xxxxxxxxx
  **Note:** To protect the device and the network, the browser is  capable of communicating with the device using a standard, HTTPS  connection over an encrypted Secure Sockets Layer (SSL). In addition,  the device can support up to 128-bit encryption for servicing HTTPS.  These credentials are stored encrypted in the device memory.
 



 


Scan  >  Network Folder Setup **Network Folder Setup**

 

       **Scan to Computer**


[LIST]
[*]»[Webscan]("https://192.168.1.80/#hId-pgWebScan") 
[/LIST]

**Scan to E-mail**


[LIST]
[*]»[Scan to E-mail Setup]("https://192.168.1.80/#hId-ScanToEmailOverview") 
[*]»[Outgoing E-mail Profiles]("https://192.168.1.80/#hId-EmailAccounts") 
[*]»[E-mail Address Book]("https://192.168.1.80/#hId-EmailContacts") 
[*]»[E-mail Options]("https://192.168.1.80/#hId-CommonEmailData") 
[/LIST]

**Scan to Network Folder**


[LIST]
[*]»[Network Folder Setup]("https://192.168.1.80/#hId-NetworkFolderAccounts") 
[/LIST]



       [COLOR=#ff0000]Modify the fields marked in red, and then click "Next". Fields marked with '*' are required.[/COLOR]
[LIST]
[*][COLOR=#ff0000]Network Path: Invalid input.[/COLOR] 
[/LIST]

**Step 1 of 4: Network Folder Information**

   Display Name *




 [COLOR=#ff0000]Network Path *[/COLOR]


**nautilus smb://bd80-desktop/documents**


  The device might need to authenticate itself on your network before  it can save scanned documents to a network folder. Enter your Windows  username and password to allow this authentication to take place so that  the device can have write access to the selected network folder.
 
    User Name

xxxxxxxx


 Password
xxxxxxxx
  **Note:** To protect the device and the network, the browser is  capable of communicating with the device using a standard, HTTPS  connection over an encrypted Secure Sockets Layer (SSL). In addition,  the device can support up to 128-bit encryption for servicing HTTPS.  These credentials are stored encrypted in the device memory.

---

### Post by Morbius1 on 2013-04-15
> **bigdes said:**
> Got the shared folder opening from the command using **nautilus smb://bd80-desktop/document **but the printer network folder setup doesn't reconize it. But it reconises it this way**\\bd80-desktop\documents**. But the terminal doesn't reconise it. So I'm sitting with two commands that works on one or the other. But it would great to have one command that wouldn't conflict with the computer or the printer. Below is the two copy's of the screen with the two different commands. 
Any solutions please 
What you are describing is the way 2 different types of clients access a shared folder. Windows ( and the printer is acting like a Windows client ) accesses a Samba share with a \\host\share. UNIX and Linux access it with a //host/share. And Nautilus on a Linux client always has to specify the protocol so it becomes smb://host/share. That's just the way it works. Windows always had things backwards ;)

---

### Post by bigdes on 2013-04-15
> **Morbius1 said:**
> What you are describing is the way 2 different types of clients access a shared folder. Windows ( and the printer is acting like a Windows client ) accesses a Samba share with a \\host\share. UNIX and Linux access it with a //host/share. And Nautilus on a Linux client always has to specify the protocol so it becomes smb://host/share. That's just the way it works. Windows always had things backwards ;)

Ah well I suppose I can live with it. As ubuntu still beats windows a million times over. 
Thanks a lot for all your help
Des

---

