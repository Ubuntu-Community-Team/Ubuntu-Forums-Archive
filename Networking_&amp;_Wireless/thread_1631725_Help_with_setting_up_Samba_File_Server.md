---
title: "Help with setting up Samba File Server"
date: 2010-11-27
forum: Networking &amp; Wireless
---

### Post by grenadingbadger on 2010-11-27
I'm trying to set up an old computer that was donated to my by an aunt to hold my external hard drives and use it as a file server so i can use them from anywhere within my house. However I can not seem to get the samba server to broadcast/be seen by my ubuntu installation, nor my  windows installation.

I've read the manual, to an extent, but I feel as if I am missing something. All I want is to have it to where I can just type in \\server\ and bring up my files to access without having to worry about passwords. 

Here is the config file:

```
[global]
workgroup = WORKGROUP
netbios name = GrenadingBadger
security = share

[data]
comment = Data
path = /media/Badgers
read only = no
guest ok = Yes
```
The result of running ```
$ smbclient -L sERVER 
``` :

```

    Server               Comment
    ---------            -------
    BRWC417FE4CD1CB      
    GRENADINGBADGER      
    SERVER               Samba 3.5.4

    Workgroup            Master
    ---------            -------
    WORKGROUP            SERVER
```
Where grenadingbadger is my computer, and the BRWC... is the printer.

---

### Post by grenadingbadger on 2010-11-27
Any ideas?

---

### Post by capscrew on 2010-11-28
> **grenadingbadger said:**
> Any ideas?

Not sure what manual you read:  I find [**_[COLOR="DarkSlateGray"]Samba by Example[/COLOR]_**]("http://www.samba.org/samba/docs/man/Samba-Guide/") to be the best howto for Samba beginners.  It will take you from the most basic basic to much more complex install configurations. 


You can always run [COLOR="DarkSlateGray"]***smbclient ***[/COLOR]or [COLOR="DarkSlateGray"]***smbtree ***[/COLOR]with more verbose debugging using the [COLOR="DarkSlateGray"]***-d ***[/COLOR]switch (i.e. smbtree -d6)

---

### Post by grenadingbadger on 2010-11-28
Yeah, I did take a look at the manual for a good hour or so. Maybe I missed somethin in my setup.... :/

---

### Post by Penguin=) on 2010-11-28
Try reading the manual again, im sure you have missed something.

---

### Post by capscrew on 2010-11-28
> **grenadingbadger said:**
> Yeah, I did take a look at the manual for a good hour or so. Maybe I missed somethin in my setup.... :/

What I recommended is not the manual.  It's a very detailed HOWTO by one of the Samba engineers.  It goes from the most basic to PDC type configurations.

If you missed something then you need to understand how the system works and have an idea of what you want to achieve.  Try reading what I suggested.  you might even have to start over.  That does not mean you have to reinstall Samba.  

Everything for non GUI configured shares is done with smb.conf.  There is a duplicate of the smb.conf is located at: /usr/share/samba if you did not make a copy before you modified the one at /etc/samba/smb.conf.

If you need descriptions of the parameters used in the smb.conf file, you can find complete explanations **_[COLOR="DarkSlateGray"][here]("http://www.samba.org/samba/docs/man/manpages-3/smb.conf.5.html")[/COLOR]_**.


Edit: If you want some debug then try ```
smbclient -L server -d6 
```

---

