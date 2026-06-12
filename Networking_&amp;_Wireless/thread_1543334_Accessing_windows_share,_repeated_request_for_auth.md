---
title: "Accessing windows share, repeated request for authentication"
date: 2010-07-31
forum: Networking &amp; Wireless
---

### Post by sauparna on 2010-07-31
I am using Kubuntu 10.04, but I am posting here because the Kubuntu forums seems to be user agnostic. I just couldn't get past the verificaiton process. This should be a general networking problem that Ubuntu users can answer.

On my home network, I have a Windows machine whose shared folders I can access from one machine running Ubuntu 9.04. I've had to do no network configuration on Ubuntu, it just works out of the box. On Windows I do not have a password that I use to login. Ubuntu does not ask for it either.

But on Kubuntu, when I browse the network samba shares, I can see my Windows share, open it, navigate it, but every time I cd into another level in the share or click on a file (say a music file to play),  the authentication window pops up asking for a user name and password. What login information should I use here? I tried my Windows user name and a blank password, but that doesn't help.

What configuration step am I missing here?

---

### Post by Raymond2201 on 2010-07-31
It's usually not a good idea to have blank passwords for any of your systems, a quick fix would be to set your Windows machine to have the exact same credentials as your Ubuntu box, IE exact same username and password, that should just work.
I have never used blank passwords so not sure if there is a recent security measure in place with the latest Samba/Ubuntu

You could try mounting the shares using fstab so these shares are available every time you start up, a bit more convenient in the long run.

---

### Post by sauparna on 2010-08-03
Tried it. I set the windows password first, but smb access on Kubuntu shows an 'access denied' message at the bottom of the dolphin window. I changed the Windows username and password to match those of my Kubuntu system, but it didn't help. It's in fact erratic. At times it opens certian dirs, displays the contents and then the annoying authentication dialog box keeps popping up in spite of entering the login information.

So, there's more work to do now ...

---

### Post by Morbius1 on 2010-08-03
Did you create your windows shares to require authentication or are they simple shares?

From the Ubuntu box post the output of the following command:
```
smbtree
```

---

### Post by Raymond2201 on 2010-08-03
i suggest maybe mounting the shares at boot time on your Ubuntu install with fstab. I have no problems using this method.

You will need either the IP address or Hostname of the XP box & know the names of the shares.

there is a file /etc/fstab  which takes care of all automated mounting (hard drives, network shares CD/DVDROM etc...)

**Instructions for setting up network share.**

Create a file in your home directory that will hold your   windows username and password.

this file should be in this format:
```

username=yourusername
password=yourpassword

```
save this file as credentials in your home directory.

Create a new folder in your home directory, lets call it winShare
open /etc/fstab as root (sudo)
eg:
```

sudo kate /etc/fstab

```
at the end of this file add this line, replacing the bold sections with your information:
//**IP_OR_HOSTNAME_OF_XP**/**SHARENAME** /home/**YOURACCOUNTNAME**/winShare cifs credentials=/home/**YOURACCOUNTNAME**/credentials ,_netdev,uid=1000,iocharset=utf8,codepage=unicode,unicode  0  0

save the file:

open a terminal and type:
```

sudo mount -a
```

assuming all is well you should see the XP share mounted in your home folder in the winShare directory we created earlier.

Hope this helps.

---

### Post by sauparna on 2010-08-04
> **Morbius1 said:**
> Did you create your windows shares to require authentication or are they simple shares?

From the Ubuntu box post the output of the following command:
```
smbtree
```

Yes, simple shares. I have shared my windows drive D:, which physically is a HDD. 
My Comp -> Right click on drive D: -> Sharing ->
tick : share this on the network
tick : allow network users to change my files

Here's the smbtree output:

> 
JAAL[INDENT]         \\RAMGORUR       
[/INDENT][INDENT][INDENT]                 \\RAMGORUR\EPSON-C45                     EPSON Stylus C45 Series
                \\RAMGORUR\print$                                   Printer Drivers
                \\RAMGORUR\IPC$                                       Remote IPC
                \\RAMGORUR\kumbhokorno     
[/INDENT][/INDENT]
JAAL is my Windows Workgroup.
RAMGORUR is the Windows box. 
 \\RAMGORUR\kumbhokorno is the Windows D: drive I mentioned in the beginning of this post.

@Raymond2201 : I haven't had time yet. I'll give that a shot too.

---

### Post by Morbius1 on 2010-08-04
The method you used to create the Windows share is the equivalent of a Linux Public share. It requires no username or password to access so this is getting confusing.

I assume that the smbtree output was from FRITZ or was that from the kubuntu box? If you did that from the kubuntu box do you get the same results?

What is the name of the kubuntu box?

---

### Post by sauparna on 2010-08-06
> **Morbius1 said:**
> The method you used to create the Windows share is the equivalent of a Linux Public share. It requires no username or password to access so this is getting confusing.

I assume that the smbtree output was from FRITZ or was that from the kubuntu box? If you did that from the kubuntu box do you get the same results?

What is the name of the kubuntu box?

Let me simplify it. I have removed FRITZ from the network, and hence modified the *smbtree* output in the previous post. Please take a look at it again. 

So now I have two machines on the network, the Kubuntu box and the Windows box. And I want to access the Windows box from Kubuntu. The *smbtree* output is from the Kubuntu box. The Kubuntu box is identified on the network by the name 'ubuntu' (the router's DHCP clients table says so).

---

### Post by sauparna on 2010-08-15
Well, I worked out a fix for the situation. This seems to work for my setup. 

**Setup**

[LIST]
[*]Local LAN, has the following machines:
[*]**A** : Headless Ubuntu 10.04 : Running samba daemon, shares dirs through samba (specified in /etc/samba/smb.conf)
[*]**B**: Windows XP : WINS enabled, TCP/IP over NetBios enabled. Has a username, but no password set. Logs in automatically
[*]**C** : Notebook, Kubuntu 10.04 : Straight out of the box, nothing extra installed.
[/LIST]

**Problem**
I am unable to browse the Windows box, **B**,  from **C** using Kubuntu's default network browser : *Dolphin -> Network -> Samba Shares -> <WIndows Workgroup>*. The machines are displayed but navigating **B** throws up an annoying authentication dialog box. I don't have read/write permissions either. I can browse **A**, though.

**Solution**

On **C**:

[LIST]
[*]*sudo apt-get install samba smbfs*
[*]*mkdir /media/shareA  /media/shareB*
[*]Added these two lines to /etc/fstab:
[LIST]
[*]*//B/shareB  /media/shareB   smbfs   rw,noauto       0       0*
[*]*//A/shareA /media/shareA   smbfs   credentials=/home/userX/.infoA,rw,uid=rup,noauto      0 0*
[/LIST]
 
[/LIST]


[LIST]
[*]**A**, the headless Ubuntu box needs authentication. So I created a file *.infoA* in */home/userX* containing these two lines:
[LIST]
[*]*username=blah*
[*]*password=blahblah*
[/LIST]
 
[/LIST]

[LIST]
[*]*sudo mount -a*
[*]or
[LIST]
[*]*sudo mount /media/shareA*
[*]*sudo mount /media/shareB*
[/LIST]
 
[/LIST]

Done. Now I can browse the shares.

**Note**

[LIST]
[*]I have fixed IP assigned to the two  machines **A** and **B**. If you use a router at home that doesn't resolve names, but assigns dynamic IPs to your local machines by DHCP then using computer names **A** and **B **doesn't work. You can use the IP address in stead but again, the IP is dynamically assigned and hence will keep changing. So hardwiring them into *fstab* is a bad idea.
[*]Replace userX with your user name in fstab  (or some other dir path).
[*]I added the *noauto* option to the lines in fstab so that they don't get mounted automatically. I  run *mount* every time I boot-up. For Kubuntu, automatic mounting through fstab doesn't work. You can add the mount command to */etc/rc.local*. That too doesn't work. The network connnection in Kubuntu is not available till the user authenticates himself after boot-up and desktop is displayed. I think rc.local runs before this step and hence does not find the network.
[/LIST]

That's it I think.

---

