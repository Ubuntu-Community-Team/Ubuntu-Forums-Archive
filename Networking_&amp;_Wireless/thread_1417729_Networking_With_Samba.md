---
title: "Networking With Samba?"
date: 2010-02-27
forum: Networking &amp; Wireless
---

### Post by joek71 on 2010-02-27
Hi guys 

I installed GADMIN for Samba i configured all, gave username and password.
but when i try to log in with vista giving the same username and password it wont let log in, and help be great .

thanks.

---

### Post by Morbius1 on 2010-02-27
I don't even know what gadmin is - is it some kind of graphical samba configurator?

Anyway, please post the output of the following command so we can all see how you've set up your shares and configured samba.

Open **Terminal**
Type **testparm -s**

Just in case you also tried the Nautilus-share method of sharing files please post the output of this command as well please:

[B]net usershare info

[/B]It sounds like you didn't set up a password for the remote user ( smbpasswd ) but it's not clear from your description.

---

### Post by joek71 on 2010-02-27
yes it is a graphical interface to Samba
I ran what yo usaid and got this:

joe@joe:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
Processing section "[homes]"
WARNING: The "share modes" option is deprecated
Processing section "[netlogon]"
WARNING: The "share modes" option is deprecated
Processing section "[profiles]"
Processing section "[printers]"
WARNING: The "share modes" option is deprecated
Processing section "[pdf-documents]"
Processing section "[pdf-printer]"
Loaded services file OK.
WARNING: You have some share names that are longer than 12 characters.
These may not be accessible to some older clients.
(Eg. Windows9x, WindowsMe, and smbclient prior to Samba 3.0.)
Server role: ROLE_STANDALONE
[global]
    server string = Samba file and print server
    interfaces = 127.0.0.1/8, 192.168.0.0/24
    bind interfaces only = Yes
    update encrypted = Yes
    client schannel = No
    server schannel = No
    allow trusted domains = No
    obey pam restrictions = Yes
    guest account = smbguest
    passwd program = /usr/bin/passwd '%u'
    passwd chat = *New*password* %n\n *ReType*new*password* %n\n *passwd*changed*\n
    passwd chat timeout = 120
    username map = /etc/samba/smbusers
    password level = 6
    username level = 6
    unix password sync = Yes
    log file = /var/log/samba/samba.log
    max log size = 1000
    name resolve order = wins lmhosts bcast
    client signing = No
    client use spnego = No
    socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
    printcap name = cups
    machine password timeout = 120
    add user script = /usr/sbin/useradd -d /dev/null -c 'Samba User Account' -s /dev/null '%u'
    delete user script = /usr/sbin/userdel '%u'
    add group script = /usr/sbin/groupadd '%g'
    delete group script = /usr/sbin/groupdel '%g'

---

### Post by Morbius1 on 2010-02-27
OMG, I may have to get my Samba textbook out to decipher some of those parameters.

There is one thing that is noticeable however. You have no shares defined.

Are we missing some of the output?

---

### Post by capscrew on 2010-02-27
> **Morbius1 said:**
> OMG, I may have to get my Samba textbook out to decipher some of those parameters.



:D  I've taken to looking [**_[COLOR="Navy"]here[/COLOR]_**]("http://www.samba.org/samba/docs/man/manpages-3/smb.conf.5.html") for that information.  

SA-admin, Webmin and gadmin all use scripts (perl or python) to configure Samba.  They do use obscure smb.conf settings.

Edit: As well as E-box!

---

### Post by Morbius1 on 2010-02-27
capscrew, 

Yes I've just started go through some of them from that same page. I hate these gui utilities that are supposed to make things simpler for the user ;) smb.conf, fstab, etc.....

joek71,

I've got to ask you what it is you're trying to achieve and in what kind of environment are you trying to achieve it.

Is this just a home network and you're trying to share some folders and you want to have the remote user supply a username and password? OR is this something more complicated?
[COLOR=Blue]
EDIT: [/COLOR]I've got to quite for the day. I would like to leave you with a piece of information in the event you may need it. There is a copy of the original version of smb.conf that came with your initial install at /usr/share/samba/smb.conf in case gadmin does not create a backup copy of the original for times like this.

---

### Post by joek71 on 2010-02-28
This is what i need to achieve, I have an external hard drive that is connect to my pc that has ubuntu on it and my wife has files on it she uses her laptop with Vista Home, before when i had windows she could have connected to this drive and move files in and out, this is what i am trying to achieve.

thanks

---

### Post by dmizer on 2010-02-28
> **joek71 said:**
> This is what i need to achieve, I have an external hard drive that is connect to my pc that has ubuntu on it and my wife has files on it she uses her laptop with Vista Home, before when i had windows she could have connected to this drive and move files in and out, this is what i am trying to achieve.

thanks

I believe you will need to create a hard mount point in /etc/fstab for your external USB drive before you can share it with Samba.

---

### Post by Morbius1 on 2010-02-28
Your needs are simple and that calls for using "Simple Sharing". If it where me this is what I would do:

First: Make sure that on your system the following file actually exists:
**/usr/share/samba/smb.conf**
If it does then follow these steps:

Open **Terminal** 
Type **sudo cp /etc/samba/smb.conf /etc/samba/smb.confORIG** 
[COLOR=Blue]*This will create a copy of the current smb.conf and call it smb.confORIG *[/COLOR]
Type **sudo cp -a /usr/share/samba/smb.conf /etc/samba/ **
[COLOR=Blue]*This is a copy of the original smb.conf in /usr/share/samba. This will copy it to /etc/samba.*[/COLOR]
Type **gksu gedit /etc/samba/smb.conf**
Add the following line to the [COLOR=Blue][global][/COLOR] section of smb.conf:
```
force user = joek71
```[COLOR=Blue]*Change joek71 to your local ubuntu login user name.*[/COLOR] 
Save the file, exit gedit, and back in the Terminal type: **sudo service samba restart**

Now go to Nautilus, right click on the mount point of the external HDD - for example: /media/Seagate. Select **Sharing Options** > Put a check on all three boxes > Select [B]Create Share

[/B]Now see if Windows can access the Ubuntu share.

If you run into difficulties then post the output of the "samba 2-step" again:

**testparm -s**
**net usershare info**

---

### Post by joek71 on 2010-02-28
First I would like to Thank all you guys here for helping me out.

Now i did the steps but when i go to my wifes laptop i see Samba and i also see my desktop and when i click on samba it asks for my username / password.
And when i press on the other icon name of my desktop in her laptop it say cant enter WinsLogon on.  So i dont know what to do next, either way it wont let me access my desktop threw her laptop on my local network.  She is running Vista Home Edition.
Still reading and researching on how to get this done.

Thanks again for all your help

---

### Post by joek71 on 2010-02-28
Guys it works, THANKS YOU SO MUCH FOR ALL YOUR HELP :P:P:P:P

You guys here are the motts, thank you.!!!!!!!!!!!!!!!!!!!!!!!!!!!!!:D:D:D:D

---

