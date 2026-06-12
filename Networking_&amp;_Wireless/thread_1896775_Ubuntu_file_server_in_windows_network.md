---
title: "Ubuntu file server in windows network"
date: 2011-12-17
forum: Networking &amp; Wireless
---

### Post by donmi on 2011-12-17
Hi there,

beginner with UBUNTU is looking for help to integrate an UBUNTU file server in a windows network (windows 2003 server with w7 workstations)

Thx.

donmi

---

### Post by mikewhatever on 2011-12-17
Check out 'Samba Server' howtos, for example,
[https://help.ubuntu.com/11.04/serverguide/C/samba-fileserver.html](https://help.ubuntu.com/11.04/serverguide/C/samba-fileserver.html)

---

### Post by donmi on 2011-12-18
Thanks.

this is a start...

---

### Post by inobe on 2011-12-18
1) we need to install samba if it's not already installed, open terminal and type

```
sudo apt-get install samba
```

that command will install samba and the service will also be enabled.

2)"optional" we need to create a samba user name and password to secure your share from outsiders, you need do this if you to access your linux shares with password authentication, in terminal type

```
sudo smbpasswd -a usernamehere
```

replace "username" with your actual account user name, for example /home/**bob**

hit enter and type a password that is not the same as your user account, you will not see the password as it's typed, you will need to enter the same password twice.

3) we need to make a shared folder that outsiders will have access to, in terminal type

```
mkdir /home/username/shares
```

replace username with actual username, and the shares name can be anything, example /home/billybob/pronShares :lol:

4)encase you didn't follow these direction well' you can at least fix what is broken, or simply start over, to have this benefit we need to backup your current smb.conf encase you wan't to restore it later, in terminal type

```
sudo cp /etc/samba/smb.conf ~
```

5) now lets edit your smb.conf, in terminal type

```
sudo gedit /etc/samba/smb.conf
```

when gedit opens up with your smb.conf' scroll down to the end and add this replacing username with your actual user name!

```
[shares]
path = /home/username/shares
available = yes
valid users = username
read only = no
browsable = yes
public = yes
writable = yes
```

example: ```
[pronShares]
path = /home/billybob/pronShares
available = yes
valid users = billybob
read only = no
browsable = yes
public = yes
writable = yes
```

now click save and close.

6) now lets restart samba, in terminal type

```
sudo restart smbd
```

the terminal will output when samba starts back up we can test for errors, type

```
testparm
```

that command will check smb.conf for errors, if the output says "loaded services file ok" you are in good shape.

now you can go to a windows machine or whatever and access your linux box, you will need your user name and password you created earlier in order to access the server.

```
testparm
```


note: on some desktop environments, the text editor is different, on kde it's kate, gedit for ubuntu........

this configuration was often used on kubuntu and has worked flawlessly.

---

### Post by Morbius1 on 2011-12-18
> **inobe said:**
> 
6) now lets restart samba, in terminal type

```
sudo /etc/init.d/samba restart
```
You might want to change that to:
```
sudo restart smbd
```There is no "samba" service ( at least not in Ubuntu ) - it's now smbd and nmbd.

And "samba" is not in init.d any longer it's now an upstart job. Doing it the old way through init.d will still work but you'll get yelled at ;)

---

### Post by inobe on 2011-12-18
> **Morbius1 said:**
> You might want to change that to:
```
sudo restart smbd
```There is no "samba" service ( at least not in Ubuntu ) - it's now smbd and nmbd.

And "samba" is not in init.d any longer it's now an upstart job. Doing it the old way through init.d will still work but you'll get yelled at ;)

yeah, i was coming back to correct that, you beat me to it:p

---

### Post by inobe on 2011-12-18
testing it on a system works well, here a testparm dump

```
xxxx@beast-dev:~$ sudo testparm
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[shares]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

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

[print$]
        comment = Printer Drivers
        path = /var/lib/samba/printers

[shares]
        path = /home/xxxx/shares
        valid users = xxxx
        read only = No
        guest ok = Yes
xxxx@beast-dev:~$ 

```

edit: checked on windows machines, perfect working linux server, even dragged files over and watched them appear on the other machines without refreshing!

---

### Post by Morbius1 on 2011-12-18
I don't know how applicable all this is to the original posters requirements - he's listed a Windows 2003 Server in the mix - but it's become kind of refreshing in this forum to see someone with a [global] section that looks like the default. People seem to go out of their way to distort the default settings to such a point that it becomes inoperable and then wonder why. :wink:

---

### Post by inobe on 2011-12-18
i think the op is suggesting on removing 2003 once the ubuntu file server is found useful.

---

