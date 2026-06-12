---
title: "Help Please with networking and smb.conf"
date: 2008-12-27
forum: Networking &amp; Wireless
---

### Post by Rockhoppers1964 on 2008-12-27
Hi Guys. new to this Ubuntu thing but did look at it a while back.... but no time then.

Back on it now and would dearly love to get it sorted and running in my home.... so want to move away from windows. !

Been looking at the forum for help and inspiration, appear to be having the common problem of getting 8.10 to network right. Have found that it may be down to the smb.conf file and the WORKGROUP string needing changed to MSHOME. but when i go in to the file to edit the string and try to save it, it says i do not have permission to save the changes, so what am i doing wrong.

I am set up as the first user ! so assume i have all rights ?

Is there an idiots guide to this networking setup ?

Thanks for your help and patience 

Andrew

---

### Post by dragos_iliescu_2005 on 2008-12-27
You must to login as root. Then you'll have the right to save the changes.

---

### Post by Iowan on 2008-12-27
Use **sudo nano** to edit the file - or for graphical editor **gksudo gedit**.
[https://help.ubuntu.com/community/SettingUpSamba]("https://help.ubuntu.com/community/SettingUpSamba")

---

### Post by Rockhoppers1964 on 2008-12-27
> **dragos_iliescu_2005 said:**
> You must to login as root. Then you'll have the right to save the changes.

Tried that and it kept chucking me out, said they had to be the right case... root and root... correct ?

Andrew

---

### Post by 2hot6ft2 on 2008-12-27
Give this a try
[http://ubuntuforums.org/showthread.php?t=218630](http://ubuntuforums.org/showthread.php?t=218630)

---

### Post by jesuspresley on 2008-12-27
In Ubuntu, you cannot login as root - the login option for root is disabled by default.

But you can enter ```
sudo -i
``` in the terminal, then enter the password of the "first" user. Hence, you can start any application from the terminal with root rights.

For example,
```

gedit /etc/samba/smb.conf
```

For beginners, I recommend to use the graphical configuration tool system-config-samba.

Keep on working on it, once you have found the right way it gets fairly easy.

---

### Post by Rockhoppers1964 on 2008-12-27
> **jesuspresley said:**
> 

For beginners, I recommend to use the graphical configuration tool system-config-samba.

Keep on working on it, once you have found the right way it gets fairly easy.

Where do i find the graphical tool ?

Andrew

---

### Post by mtopro on 2008-12-27
Try under the 'System' pulldown 'Administration'>'Samba'.  Login using the root password, then simply 'Add Share'.

One other learning curve thing came to me that I thought I would share..  If you are trying to add a Samba user, they must first be a user of the system under the 'System' pulldown 'Administration'>'Users and Groups'.  Once the user is setup there, the user can then be added in the Samba control panel.

---

### Post by Rockhoppers1964 on 2008-12-27
> **mtopro said:**
> Try under the 'System' pulldown 'Administration'>'Samba'.  Login using the root password, then simply 'Add Share'.

One other learning curve thing came to me that I thought I would share..  If you are trying to add a Samba user, they must first be a user of the system under the 'System' pulldown 'Administration'>'Users and Groups'.  Once the user is setup there, the user can then be added in the Samba control panel.

Yup, got the user set up for Sambashare.
Samba does not appear under the admin menu

?

Andrew

---

### Post by mtopro on 2008-12-27
That is a bit strange.  I have several versions of Ubuntu around here, and it appears there in every version, although I seem to remember getting the same advise to install from the command line, and I don't believe it installed everything for the graphic interface.

You may need to uninstall what you have at the 'System' pulldown under Administration > Synaptic Package manager.  Remove Samba.  The go 'Applications'>'Add/Remove' and install Samba there.  This is the graphical version and to me it seems MUCH easier to configure..

---

### Post by dragos_iliescu_2005 on 2008-12-28
1.Check if your system is configured to allow root login (System>Administration>Login Window); go to Security and check on the "Allow local system administrator login"
2.If you want to change the name of WOrkgroup to MSHome then try to modify it in the Samba config.


3.Try install gadmin-samba or use webmin to config samba

---

