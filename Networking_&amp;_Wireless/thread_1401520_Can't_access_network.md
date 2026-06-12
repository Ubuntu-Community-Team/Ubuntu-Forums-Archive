---
title: "Can't access network"
date: 2010-02-08
forum: Networking &amp; Wireless
---

### Post by monkeyking009 on 2010-02-08
Hello All

I recently installed Ubuntu 9.10 on my laptop. I generally really impressed and pleased with it.

However,

I also have a Desktop running Windows Vista SP2 but I'm unable to access the shared folders on the network. In return I'm also unable to access my Ubuntu laptop from Windows. I know there is a connection because my laptop shows up in the Network Manager in Windows, but when I try to open it the connection it fails (times out?).

I have allowed the IP's and opened the necessary ports in the firewall in both Windows and Ubuntu (using Firestarter).

I've manually set up the Samba File Sharing ([http://ubuntuguide.org/wiki/Ubuntu:Karmic#Samba_File_Sharing](http://ubuntuguide.org/wiki/Ubuntu:Karmic#Samba_File_Sharing)) using method 2 with no errors.

When I run //192.168.1.2 in Windows the connection opens and shows me the shared folders in Ubuntu. However, when I try to open the folders it can't.

**Summary**: I can see both the Windows and the Ubuntu machines in the network but trying to access the shared folders times out.

I'll really appreciate the help. Thanks in advance,

- Erik

---

### Post by Morbius1 on 2010-02-08
Let's go after the Linux share access problem first. Please post the output of the following commands:

Open **Terminal**
Type **net usershare info**
Type **sudo net usershare info**
Type **testparm -s**
Type **nmap -sT 192.168.0.100/22**
[COLOR=Blue]*Change 192.168.0.100 to the ip address of the machine you're using.*[/COLOR]

You may not have nmap installed but when you issue the nmap command it will ask you if you want to install it - you do. Once it's installed run the nmap command again.

---

### Post by monkeyking009 on 2010-02-08
Hello Morbius1 and thanks.

This is the output copy/pasted directly from the terminal:

erik@erik-3810TG:~$ net usershare info
erik@erik-3810TG:~$ sudo net usershare info
erik@erik-3810TG:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
Processing section "[printers]"
Processing section "[print$]"
Processing section "[Documents]"
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

[Documents]
    path = /home/erik/documents
erik@erik-3810TG:~$ nmap -sT 192.168.1.4/22

Starting Nmap 5.00 ( [http://nmap.org](http://nmap.org) ) at 2010-02-08 13:28 CET
Interesting ports on 192.168.0.21:
Not shown: 921 closed ports, 78 filtered ports
PORT   STATE SERVICE
22/tcp open  ssh

All 1000 scanned ports on 192.168.0.31 are filtered (552) or closed (448)

All 1000 scanned ports on 192.168.0.41 are filtered (573) or closed (427)

Interesting ports on 192.168.1.4:
Not shown: 998 closed ports
PORT    STATE SERVICE
139/tcp open  netbios-ssn
445/tcp open  microsoft-ds

Interesting ports on 192.168.1.5:
Not shown: 990 filtered ports
PORT      STATE SERVICE
80/tcp    open  http
135/tcp   open  msrpc
139/tcp   open  netbios-ssn
443/tcp   open  https
445/tcp   open  microsoft-ds
554/tcp   open  rtsp
2869/tcp  open  unknown
5357/tcp  open  unknown
10243/tcp open  unknown
49155/tcp open  unknown

Nmap done: 1024 IP addresses (5 hosts up) scanned in 1017.28 seconds
erik@erik-3810TG:~$ 

- Erik

---

### Post by Morbius1 on 2010-02-08
(1) Share definition

```
[Documents]
    path = /home/erik/documents
```Unless you created it yourself there is no /home/erik/documents.
There is a /home/erik/Documents though.
You might want to go into smb.conf and make the small "d" a big "D".

When you done editing smb.conf , restart samba: **sudo service samba restart**

Also, that is probably the shortest share definition I've ever seen. It will work but it's depending on the following implied defaults:

browseable = yes
guest ok = no
writeable = no

So as it stands, it requires authentication to access and is read only. Is that what you intended?

If you are requiring a username and password to access this share have you set up a username and samba password on the linux box?

(2) nmap

There's a lot of "filtered" ports mentioned. That usually means a firewall or a hyperactive windows antivirus is in the way.

Can you tell me what ip belongs to what machine:
192.168.0.21
192.168.0.31
192.168.0.41
192.168.1.4
192.168.1.5

192.168.1.4 and 192.168.1.5 look about right. Hopefully those are your Windows and Linux boxes

(3) Experiment

Try to use Simple Sharing on one of your other folders in your home directory and allow guest access. It's the easiest to access.

Open Nautilus
Right Click on say ... /home/erik/Pictures
Select "Sharing Options"
Check off all three boxes

Then see if Windows can access that share.

---

### Post by monkeyking009 on 2010-02-08
(1)(3)

Ok, I'm getting somewhere now. Changing the small "d" to a big "D" made the Windows command //192.168.1.4 work and I now have access to to the Ubuntu laptop from the Windows desktop through that command. In addition, when I setup new shares from Nautilus they show up in Windows as well with the defined privileges.

I should have mentioned, I supplied a username and password to samba before editing smb.conf, using the command:

sudo smbpasswd -a erik

I am still not able to access the Ubuntu share from the Windows Network folder but that is not important. Access to the Ubuntu shares from Windows is therefore solved. However, I'm still not able to access the windows shares from Ubuntu. Is it possible to do the same thing on Ubuntu, like "connect to server" and set the server type to Windows share? If yes how?

(2)

192.168.1.4 is the Ubuntu laptop
192.168.1.5 is the Windows desktop

I'm not a 100 % sure what the other IP's belong to. However, my wireless router is connected to a larger network of which I have no control. My best bet is that the other IP's are outside my own private network.

-Erik

---

### Post by monkeyking009 on 2010-02-08
Ok I figured it out. The problem was not caused by connectivity but the fact that my Windows shares was protected by a password.

The solution:

Access to Ubuntu laptop from Windows desktop:
In windows run the command //192.168.x.x where the x.x is the laptop.

Access to Windows desktop from Ubuntu laptop:
"Places" -> "Connect to Server"
Service type: Windows share
Server: 192.168.x.x (where x.x is the desktop)
"Connect"
User name: <insert-windows-user-name>
Domain: WORKGROUP/<insert-computer-name>
Password: <insert-windows-password>
"OK"

Thank you very much for your help Morbius1. I really appreciate it!

- Erik

---

