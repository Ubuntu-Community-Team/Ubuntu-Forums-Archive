---
title: "samba isn't working"
date: 2009-12-17
forum: Networking &amp; Wireless
---

### Post by rkakkar on 2009-12-17
When I click the button, nothing happens. Any ideas?

---

### Post by cariboo on 2009-12-18
The error message says that you are trying to setup Samba as a regular user, you need to be root to install Samba. Try, pressing Alt-F2 and typing:

```
gksudo nautilus
```

This will start Nautilus in root mode allowing you to setup your Samba shares

---

### Post by rkakkar on 2009-12-18
> **cariboo907 said:**
> The error message says that you are trying to setup Samba as a regular user, you need to be root to install Samba. Try, pressing Alt-F2 and typing:

```
gksudo nautilus
```

This will start Nautilus in root mode allowing you to setup your Samba shares

nothing seems to happen there too .. i'm using kubuntu ...

---

### Post by rkakkar on 2009-12-20
> **cariboo907 said:**
> The error message says that you are trying to setup Samba as a regular user, you need to be root to install Samba. Try, pressing Alt-F2 and typing:

```
gksudo nautilus
```

This will start Nautilus in root mode allowing you to setup your Samba shares


ok i tried this .. but it still doesn't do anything. the following error is thrown though:

```

findServiceByDesktopPath: fileshare.desktop not found
QSocketNotifier: Invalid socket 18 and type 'Read', disabling...
```

---

### Post by mikewhatever on 2009-12-20
Looking closely at the screenshot, you seem to be on Kubuntu, using Dolphing and not Nautilus, the default file browser in Ubuntu. I am not at all familiar with Kubuntu, perhaps you need to run Dolphine as root, which is strange, be careful wit that. You don't need <gksudo nautilus> to set up samba sharing in Ubuntu. Anyway, do tell us what Desktop Environment you are running and what version.

---

### Post by Iowan on 2009-12-20
[This]("http://www.psychocats.net/ubuntu/graphicalsudo") page mentions: > 3. There are also some graphical applications that simply will not run with the sudo command. Kate, for example, can be run as
kdesu kate
but cannot be run as
sudo kate

---

### Post by rkakkar on 2009-12-20
> **mikewhatever said:**
> Looking closely at the screenshot, you seem to be on Kubuntu, using Dolphing and not Nautilus, the default file browser in Ubuntu. I am not at all familiar with Kubuntu, perhaps you need to run Dolphine as root, which is strange, be careful wit that. You don't need <gksudo nautilus> to set up samba sharing in Ubuntu. Anyway, do tell us what Desktop Environment you are running and what version.

hi dude .. yup i already mentioned [kubuntu] in my threat title and in my profile .. and check my post right above yours to see the problem i'm facing .. thanks ...

---

### Post by rkakkar on 2009-12-20
> **Iowan said:**
> [This]("http://www.psychocats.net/ubuntu/graphicalsudo") page mentions:


thanks .. but i've worked around the gksudo problem .. please check the problem i'm facing with samba...

---

### Post by rkakkar on 2009-12-21
I'm unable to share a folder .. 

when i click 'configure file sharing' (see screenshot), nothing happens!

the following error is thrown:

```

findServiceByDesktopPath: fileshare.desktop not found
QSocketNotifier: Invalid socket 18 and type 'Read', disabling...

```

---

### Post by bodhi.zazen on 2009-12-21
Just a few suggestions.


First, you need to log off an back in after installing the samba server.

Second you need to have permissions to the share in offer to share it.

Third, you should not share your $HOME directory, rather a directory within $HOME.

If it is not working , what directory are you trying to share and what are the ownership and permissions?

---

### Post by rkakkar on 2009-12-21
> **bodhi.zazen said:**
> Just a few suggestions.


First, you need to log off an back in after installing the samba server.

Second you need to have permissions to the share in offer to share it.

Third, you should not share your $HOME directory, rather a directory within $HOME.

If it is not working , what directory are you trying to share and what are the ownership and permissions?


1. It still the same after restarting.

2. This is what I am trying to set, but the dialog to configure file sharing isn't opening. It throws the following error in the terminal:

```

findServiceByDesktopPath: fileshare.desktop not found
QSocketNotifier: Invalid socket 18 and type 'Read', disabling...

```

3. The directory I'm trying to share is:

```

/home/rahul/Desktop/Transfers

```

and the permission as of now are:

```

drwxrwxrwx 6 rahul rahul 4096 2009-12-20 23:08 Transfers

```

---

### Post by Zorael on 2009-12-21
KDE seems to support some form of user-specific filesharing that I don't understand.

Anyway, you need the **kdenetwork-filesharing** package. After installing it you should get a Samba option in System Settings wherein you can configure system-wide shares. Check the Advanced tab.

---

### Post by Zorael on 2009-12-21
Cross-post of [http://ubuntuforums.org/showthread.php?t=1358053](http://ubuntuforums.org/showthread.php?t=1358053).

---

### Post by cariboo on 2009-12-21
Please don't create multiple threads on the same subject, I have merged your two threads.

---

### Post by rkakkar on 2009-12-21
> **Zorael said:**
> KDE seems to support some form of user-specific filesharing that I don't understand.

Anyway, you need the **kdenetwork-filesharing** package. After installing it you should get a Samba option in System Settings wherein you can configure system-wide shares. Check the Advanced tab.


this worked! but its asking me to install smb or nfs servers. so which package should i install?

---

### Post by bodhi.zazen on 2009-12-21
smb == samba

nfs == Network File Shares.

Either will work, IMO samba is more secure, although it is a bit slower.

---

### Post by rkakkar on 2009-12-22
> **bodhi.zazen said:**
> smb == samba

nfs == Network File Shares.

Either will work, IMO samba is more secure, although it is a bit slower.

thanks!! this worked :)

---

