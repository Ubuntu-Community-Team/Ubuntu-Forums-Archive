---
title: "Trouble accessing Ubuntu files from Windows 7"
date: 2010-12-01
forum: Networking &amp; Wireless
---

### Post by mortrca on 2010-12-01
I am trying to access the files and directories that are on my Ubuntu 10.10 computer from my Windows 7 computer. Both are connected to the same wireless router. I have installed and uninstalled Samba and rebooted both computers several times. I have no idea what I am doing wrong. Suggestions are greatly appreciated.

---

### Post by Morbius1 on 2010-12-02
Windows 7 represents a true challenge since it seems designed not to play well with others.

All I can suggest is that you make sure that the Ubuntu system can see it's own shares. The following command should show you all of your shares and errors if something is wrong:
```
smbtree
```The next command will tell you if your firewall is in the way:
```
sudo nmap -sS -sU -T4 192.168.0.100 
```Do it once for the Ubuntu machine with it's ip address and again for the Windows machine with it's ip address.
You may have to install nmap first:
```
sudo apt-get install nmap
```Finally make sure all your samba related services are running:
```
sudo service smbd status
``````
sudo service nmbd status
```If any of them are not running then start them, for example:
```
sudo service smbd start
```

---

### Post by pricetech on 2010-12-02
How did you configure Samba ??  I've had no problems accessing any of my Samba shares with Windows 7.  It all just plain works.

---

### Post by mortrca on 2010-12-02
Re: Morbius1

The "smbtree" command resulted in...nothing. Perhaps this is my problem? I have tried marking directories as shared in the past sometimes resulting in an error message sometimes not. Now if I try and share a directory it gives me:

"'net usershare' returned error 255: net usershare add: share name backup is already a valid system user name"

Running the second command you gave me results in:
"Starting Nmap 5.21 ( [http://nmap.org](http://nmap.org) ) at 2010-12-02 15:27 CST
Note: Host seems down. If it is really up, but blocking our ping probes, try -PN
Nmap done: 1 IP address (0 hosts up) scanned in 2.22 seconds"

4th command: "smbd start/running, process 1252"

5th command: "nmbd start/running, process 3182"

I'm new to this, so I wouldn't be surprised if I did something very wrong, what should I do now?

---

### Post by mortrca on 2010-12-02
> **pricetech said:**
> How did you configure Samba ??  I've had no problems accessing any of my Samba shares with Windows 7.  It all just plain works.

I didn't really, I kinda just hoped that it would work. If I remember correctly, I changed the workgroup name at some point and tried to understand why it asked which out of a list of approximately 20 users I wanted to give access to my shares.

---

### Post by Morbius1 on 2010-12-02
You've got a lot going on there.

[1] You got no output from smbtree even though smbd and nmbd are running. You also got no output from nmap. Both of those things points to perhaps a firewall getting in the way. If you've done anything with the firewall disable it. If you haven't done anything with the firewall then I'm not exactly sure what the problem is.

[2] "'net usershare' returned error 255: net usershare add: share name backup is already a valid system user name"

That's a quirk with Nautilus-share. It can't create a share name that matches an already existing user. If you run the following command you'll see that "backup" is an existing user:
```
cat /etc/passwd
```All you need to do is create another share name for that share, like .. mybackup , for example.

---

### Post by mortrca on 2010-12-02
> **Morbius1 said:**
> If you've done anything with the firewall disable it. If you haven't done anything with the firewall then I'm not exactly sure what the problem is.

I have made some changes to the firewall. After disabling it the output is:
```
WORKGROUP
    \\CHRISTOPHER-DESK        christopher-desktop server (Samba, Ubuntu)
        \\CHRISTOPHER-DESK\mybackup           
        \\CHRISTOPHER-DESK\business           
        \\CHRISTOPHER-DESK\PDF                PDF
        \\CHRISTOPHER-DESK\PDF_Printer        Virtual PDF Printer
        \\CHRISTOPHER-DESK\print$             Printer Drivers
        \\CHRISTOPHER-DESK\backup             
        \\CHRISTOPHER-DESK\IPC$               IPC Service (christopher-desktop server (Samba, Ubuntu))
```> **Morbius1 said:**
> [2] "'net usershare' returned error 255: net usershare add: share name backup is already a valid system user name"

That's a quirk with Nautilus-share. It can't create a share name that matches an already existing user. If you run the following command you'll see that "backup" is an existing user:
```
cat /etc/passwd
```All you need to do is create another share name for that share, like .. mybackup , for example.
Done

---

### Post by Morbius1 on 2010-12-03
Hopefully this is the only problem but your machine name is 1 character too long ( Samba rules not Linux rules ). "CHRISTOPHER-DESK" is 16 characters. It needs to be 15 characters or less.

The easiest way around this is to use Samba itself:

Edit smb.conf as root:
```
gksu gedit /etc/samba/smb.conf
```Add the following line to the [global] section of smb.conf:
```
netbios name = chris-desktop
```[COLOR=Blue]*It can be anything you want but it has to be 15 characters or less.*[/COLOR]
Save the file and back in the terminal restart samba:
```
sudo service smbd restart
```

---

### Post by mortrca on 2010-12-03
That fixed it. Is there something I can do to allow connecting without disabling the firewall?

---

### Post by Morbius1 on 2010-12-03
I'm not very knowledgeable about firewalls because I'm behind a router and don't use one on the PC itself.

If I remember correctly you should be able to enable the firewall again and then allow Samba:
From the Terminal:
```
sudo ufw allow Samba
```

---

### Post by mortrca on 2010-12-03
That worked perfectly. Thank you so much for your help.

---

### Post by Morbius1 on 2010-12-03
Trust me that firewall thing was a guess.

I'm relieved it worked :D

---

