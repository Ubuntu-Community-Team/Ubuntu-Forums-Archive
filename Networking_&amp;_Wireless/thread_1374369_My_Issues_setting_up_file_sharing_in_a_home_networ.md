---
title: "My Issues setting up file sharing in a home network"
date: 2010-01-06
forum: Networking &amp; Wireless
---

### Post by hakan8470 on 2010-01-06
hakan@hakan-desktop:~$ smbtree
WORKGROUP
    \\HAKAN-LAPTOP           hakan-laptop server (Samba, Ubuntu)
cli_start_connection: failed to connect to HAKAN-LAPTOP<20> (0.0.0.0). Error NT_STATUS_BAD_NETWORK_NAME
    \\HAKAN-DESKTOP          hakan-desktop server (Samba, Ubuntu)
        \\HAKAN-DESKTOP\deluge             
        \\HAKAN-DESKTOP\IPC$               IPC Service (hakan-desktop server (Samba, Ubuntu))
        \\HAKAN-DESKTOP\print$             Printer Drivers

one hour later. dont change anything.

hakan@hakan-desktop:~$ smbtree
WORKGROUP
    \\HAKAN-DESKTOP          hakan-desktop server (Samba, Ubuntu)
        \\HAKAN-DESKTOP\deluge             
        \\HAKAN-DESKTOP\IPC$               IPC Service (hakan-desktop server (Samba, Ubuntu))
        \\HAKAN-DESKTOP\print$             Printer Drivers

what can i do?

---

### Post by johnson.d on 2010-01-07
To check if the samba share is accessible at all, you can try connecting the smb share to the laptop through Nautilus in Ubuntu by typing smb://HAKAN-LAPTOP/< share name >. If it is connecting, it will be prompting for the login credentials. If this works we can troubleshoot smbtree output further.

The first output of smbtree indicates to the samba server being not accessible.

---

### Post by Morbius1 on 2010-01-07
Post the output of the following commands please:

Open **Terminal**
Type **net usershare info**
Type **testparm -s**

---

### Post by hakan8470 on 2010-01-07
> **johnson.d said:**
> To check if the samba share is accessible at all, you can try connecting the smb share to the laptop through Nautilus in Ubuntu by typing smb://HAKAN-LAPTOP/< share name >. If it is connecting, it will be prompting for the login credentials. If this works we can troubleshoot smbtree output further.

The first output of smbtree indicates to the samba server being not accessible.

Thanks jhones.d.. 

I tried. didnt work. while Desktop can ping laptop, laptop can't Desktop. I' ll look up another treads. My problem can be about router.

---

### Post by hakan8470 on 2010-01-07
> **Morbius1 said:**
> Post the output of the following commands please:

Open **Terminal**
Type **net usershare info**
Type **testparm -s**

hakan@hakan-desktop:~$ net usershare info
[deluge]
path=/home/hakan/Deluge
comment=
usershare_acl=Everyone:F,
guest_ok=n

hakan@hakan-desktop:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
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

[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    browseable = No
    browsable = No

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers
hakan@hakan-desktop:~$

---

### Post by Morbius1 on 2010-01-07
That was my fault. I Didn't tell you which computer to run those commands from. Run them from HAKAN-LAPTOP.

[B]From HAKAN-DESKTOP:
[/B]
Go back into nautilus and click on all three options so that you enable guest access. If you really want authentication we can fix it later. For now just let's see if we can connect.

net usershare info should look like this when your done:
> hakan@hakan-desktop:~$ net usershare info
[deluge]
path=/home/hakan/Deluge
comment=
usershare_acl=Everyone:F,
[COLOR=Blue]guest_ok=y[/COLOR]

---

### Post by hakan8470 on 2010-01-07
> **Morbius1 said:**
> That was my fault. I Didn't tell you which computer to run those commands from. Run them from HAKAN-LAPTOP.

[B]From HAKAN-DESKTOP:
[/B]
Go back into nautilus and click on all three options so that you enable guest access. If you really want authentication we can fix it later. For now just let's see if we can connect.


ok! it must be.

hakan@hakan-desktop:~$ net usershare info
[deluge]
path=/home/hakan/Deluge
comment=
usershare_acl=Everyone:F,
guest_ok=y

hakan@hakan-desktop:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
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

[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    browseable = No
    browsable = No

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers
hakan@hakan-desktop:~$

---

### Post by Morbius1 on 2010-01-07
First, do the same thing in the laptop that I suggested for the desktop. Go back into nautilus > Sharing options > and select all three options to enable guest access. net usershare info should look like this:

> [sharethis]
path=/home/hakan/sharethis
comment=
usershare_acl=Everyone:F,
[COLOR=Blue]guest_ok=y[/COLOR]Second, I've come across the NT_STATUS_BAD_NETWORK_NAME problem three times now and the fix was the same. Can't guarantee it's the same cause but it's worth finding out.

The entire path to your share on the laptop has to allow read access. So in a terminal type:

**ls -dl /home/hakan**

The output should look like this: 

d[COLOR=DarkRed]r[/COLOR]wx[COLOR=DarkRed]r[/COLOR]-x[COLOR=DarkRed]r[/COLOR]-x 79 hakan hakan

The important thing here is that there be three "r"'s in the listing. If there are then the problem is something else. If they are not then post the output.

---

### Post by hakan8470 on 2010-01-07
> **Morbius1 said:**
> First, do the same thing in the laptop that I suggested for the desktop. Go back into nautilus > Sharing options > and select all three options to enable guest access. net usershare info should look like this:

Second, I've come across the NT_STATUS_BAD_NETWORK_NAME problem three times now and the fix was the same. Can't guarantee it's the same cause but it's worth finding out.

The entire path to your share on the laptop has to allow read access. So in a terminal type:

**ls -dl /home/hakan**

The output should look like this: 

d[COLOR=DarkRed]r[/COLOR]wx[COLOR=DarkRed]r[/COLOR]-x[COLOR=DarkRed]r[/COLOR]-x 79 hakan hakan

The important thing here is that there be three "r"'s in the listing. If there are then the problem is something else. If they are not then post the output.


ok..

hakan@hakan-laptop:~$ net usershare info
[sharethis]
path=/home/hakan/sharethis
comment=
usershare_acl=Everyone:F,
guest_ok=y

hakan@hakan-laptop:~$ ls -dl /home/hakan
drwxr-xr-x 41 hakan hakan 4096 2010-01-07 15:37 /home/hakan

---

### Post by hakan8470 on 2010-01-07
> **hakan8470 said:**
> Thanks jhones.d.. 

I tried. didnt work. while Desktop can ping laptop, laptop can't Desktop. I' ll look up another treads. My problem can be about router.

now. they can be ping each other.

---

### Post by Morbius1 on 2010-01-07
If you do an **smbtree** from the desktop do both machines now appear?

Post the entire output if you see any errors.

---

### Post by hakan8470 on 2010-01-07
> **Morbius1 said:**
> If you do an **smbtree** from the desktop do both machines now appear?

Post the entire output if you see any errors.


hakan@hakan-desktop:~$ smbtree
Enter hakan's password: 
WORKGROUP
    \\HAKAN-DESKTOP          hakan-desktop server (Samba, Ubuntu)
        \\HAKAN-DESKTOP\deluge             
        \\HAKAN-DESKTOP\IPC$               IPC Service (hakan-desktop server (Samba, Ubuntu))
        \\HAKAN-DESKTOP\print$             Printer Drivers

---

### Post by Morbius1 on 2010-01-07
Can you access the laptop share by ip address?

Open **Terminal**
Type [B]nautilus smb://192.168.0.100/sharethis

[/B][COLOR=Blue]Change 192.168.0.100 to the ip address of the laptop.


If you can't try to disable any firewalls you may have enabled.
[/COLOR]

---

### Post by hakan8470 on 2010-01-07
hakan@hakan-desktop:~$ nautilus smb://192.168.2.2/sharethis

(nautilus:23290): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed

---

### Post by Morbius1 on 2010-01-07
Never seen that error.

What if instead of using the terminal you just type 

smb://192.168.2.2/sharethis

directly into the location bar in nautilus?

---

### Post by hakan8470 on 2010-01-07
ok.. I want to give some info about. while desktop cmp is 64bit ubuntu 9.10, laptop 32 bit.

and now they dont ping. hosts Unreachable.

---

### Post by hakan8470 on 2010-01-07
> **Morbius1 said:**
> Never seen that error.

What if instead of using the terminal you just type 

smb://192.168.2.2/sharethis

directly into the location bar in nautilus?

:D in terminal &#305; can ping the 192.168.2.2
but status like this 
&#305; did it tree times. sorry.

hakan@hakan-desktop:~$ smb://192.168.2.2/sharethis
bash: smb://192.168.2.2/sharethis: No such file or directory
hakan@hakan-desktop:~$ smb://192.168.2.2/sharethis
bash: smb://192.168.2.2/sharethis: No such file or directory
hakan@hakan-desktop:~$ smb://192.168.2.2/sharethis
bash: smb://192.168.2.2/sharethis: No such file or directory

---

### Post by hakan8470 on 2010-01-07
> **Morbius1 said:**
> Never seen that error.

What if instead of using the terminal you just type 

smb://192.168.2.2/sharethis

directly into the location bar in nautilus?


sorry. Im late.

Could not display "smb://192.168.2.2/sharethis/".
Error: Failed to mount Windows share
Please select another viewer and try again.

---

### Post by Morbius1 on 2010-01-07
I've been trying to find a post anywhere that fits your circumstance and it's been tough.

(1) First you can ping and then you can't.

(2) You get a NT_STATUS_BAD_NETWORK_NAME error when you smbtree to the laptop and then you don't.

(3) Then you get a [I]Error: Failed to mount Windows share
Please select another viewer and try again[/I]. when trying to access the laptop.

Firewall? Router?

I did find this post which you might want to try: [http://ubuntuforums.org/showthread.php?t=1201327](http://ubuntuforums.org/showthread.php?t=1201327)

On the LAPTOP:

Open **Terminal**
Type **gksu gedit /etc/samba/smb.conf**

> change 
; interfaces = 127.0.0.0/8 eth0
by
interfaces = wlan0 127.0.0.0/8 eth0Save the file, exit gedit, and back in the Terminal type:

**sudo service samba restart**

If it doesn't work you can always go back and put a ";" in front of the line again.

---

### Post by hakan8470 on 2010-01-07
ok. I tried that. and status very well now. but I have some problem. each comp (laptop, desktop) is seeing only themselves. for example. laptop

hakan@hakan-laptop:~$ **smbtree**
Enter hakan's password: 
WORKGROUP
    \\HAKAN-LAPTOP           hakan-laptop server (Samba, Ubuntu)
        \\HAKAN-LAPTOP\sharethis          
        \\HAKAN-LAPTOP\IPC$               IPC Service (hakan-laptop server (Samba, Ubuntu))
        \\HAKAN-LAPTOP\print$             Printer Drive

but desktop wasn't there.

---

### Post by Morbius1 on 2010-01-08
I'm probably too obsessed in thinking this is some sort of firewall or router issue but I've got one more command you can try:

Open **Terminal**
Type **nmap -sT 192.168.0.100/22**

[COLOR=Blue]*Change 192.168.0.100 to the ip address of the machine you're using.*[/COLOR]

You may not have nmap installed but when you issue the nmap command it will ask you if you want to install it - you do. Once it's installed run the nmap command again.

You should get an output that looks something like this:
> Interesting ports on 192.168.0.1:
Not shown: 998 closed ports
PORT     STATE SERVICE
80/tcp   open  http
5678/tcp open  unknown

Interesting ports on 192.168.0.100:
Not shown: 997 closed ports
PORT    STATE SERVICE
139/tcp open  netbios-ssn
445/tcp open  microsoft-ds
631/tcp open  ipp

Interesting ports on 192.168.0.110:
Not shown: 997 closed ports
PORT    STATE SERVICE
139/tcp open  netbios-ssn
445/tcp open  microsoft-ds
631/tcp open  ipp
The important thing at this point in your problem is that 3 ip addresses are listed: the router, the desktop, and the laptop. 

I apologize that I don't have any quick answer here. I don't have a lot of experience with linux and wireless ( all the laptops here are windows and mac's ). It could be something obvious about wireless that I'm missing.

---

### Post by hakan8470 on 2010-01-08
[Morbius1]("http://ubuntuforums.org/member.php?u=982144")  Thank you for your attempts. You taught important things. I am new in ubuntu. We have tree computer. Laptop- desktop- my sister's desktop. and one router. We used to use windows two weeks ago. and now the ubuntu works all machine. we want to do all our works in ubuntu and look up others prosess. But now this is very important.   

Ok. Then..

take a look at..

it's my laptop

> 
hakan@hakan-laptop:~$** nmap -sT 192.168.2.[COLOR=DeepSkyBlue]2[/COLOR]/22**

Starting Nmap 5.00 ( [http://nmap.org]("http://nmap.org/") ) at 2010-01-08 15:20 EET

  Interesting ports on 192.168.1.252:[COLOR=Blue] (I dont know what is that may be DVB Card )[/COLOR]
Not shown: 993 closed ports
PORT     STATE    SERVICE
20/tcp   filtered ftp-data
21/tcp   filtered ftp
22/tcp   filtered ssh
23/tcp   filtered telnet
25/tcp   filtered smtp
179/tcp  open     bgp
1720/tcp filtered H.323/Q.931

Interesting ports on 192.168.2.1:[COLOR=Blue] (Router. all machine use this default route)[/COLOR]
Not shown: 995 closed ports
PORT     STATE SERVICE
21/tcp   open  ftp
22/tcp   open  ssh
23/tcp   open  telnet
80/tcp   open  http
1050/tcp open  java-or-OTGfileshare

Interesting ports on 192.168.2.2: [COLOR=Blue](laptop)[/COLOR]
Not shown: 996 closed ports
PORT     STATE SERVICE
139/tcp  open  netbios-ssn
445/tcp  open  microsoft-ds
4662/tcp open  edonkey
6881/tcp open  bittorrent-tracker

Interesting ports on 192.168.2.4: [COLOR=Blue](desktop)[/COLOR]
Not shown: 998 closed ports
PORT    STATE SERVICE
139/tcp open  netbios-ssn
445/tcp open  microsoft-ds

All 1000 scanned ports on 192.168.2.5 are closed [COLOR=Blue](other desktop.&#304;t was not open. )[/COLOR]

Interesting ports on 192.168.3.1:[COLOR=Blue] (Router. But I didnt understand the router have two ip adresses)[/COLOR]
Not shown: 995 closed ports
PORT     STATE SERVICE
21/tcp   open  ftp
22/tcp   open  ssh
23/tcp   open  telnet
80/tcp   open  http
1050/tcp open  java-or-OTGfileshare

Nmap done: 1024 IP addresses (6 hosts up) scanned in 181.65 second



---

### Post by hakan8470 on 2010-01-09
&#304;t's my desktop

> 
hakan@hakan-desktop:~$**[COLOR=Black] nmap -sT 192.168.2.[COLOR=DeepSkyBlue]4[/COLOR]/22[/COLOR]**

Starting Nmap 5.00 ( [http://nmap.org](http://nmap.org) ) at 2010-01-09 17:52 EET
Interesting ports on 192.168.2.1:
Not shown: 995 closed ports
PORT     STATE SERVICE
21/tcp   open  ftp
22/tcp   open  ssh
23/tcp   open  telnet
80/tcp   open  http
1050/tcp open  java-or-OTGfileshare

Interesting ports on 192.168.2.4:
Not shown: 998 closed ports
PORT    STATE SERVICE
139/tcp open  netbios-ssn
445/tcp open  microsoft-ds

Interesting ports on 192.168.3.1:
Not shown: 995 closed ports
PORT     STATE SERVICE
21/tcp   open  ftp
22/tcp   open  ssh
23/tcp   open  telnet
80/tcp   open  http
1050/tcp open  java-or-OTGfileshare

Nmap done: 1024 IP addresses (3 hosts up) scanned in 95.55 seconds




---

### Post by johnson.d on 2010-01-18
Please try the following steps and let me know if they help:

1) Check whether the network connection is consistent ( by pinging back and forth between all machines in your LAN )as there is no use in troubleshooting samba etc. when the basic network connectivity has problems. If there are problems fix them before working on samba further. Intermittent network connectivity problems can be due to faulty cables, hardware problems with NIC/PCI slot, and duplicate IP in the LAN etc.

2) Try disabling iptables and Apparmor both on the laptop and connecting client machine(desktop) for testing purpose and see if it makes any difference.

3) Try the following command from the desktop so that you can confirm whether the samba port is allowed through the network. You can type the command as:

nmap 192.168.2.2 (from the desktop)

If SMB port(445) is shown as open in the output, it will establish that there is nothing blocking SMB connection from the client to the server. (Access to the shares, of course, will be further determined by the samba configuration)

---

