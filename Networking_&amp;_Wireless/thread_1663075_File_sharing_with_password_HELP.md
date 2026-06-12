---
title: "File sharing with password HELP"
date: 2011-01-09
forum: Networking &amp; Wireless
---

### Post by eddie3000 on 2011-01-09
OK! Hello everyone. :D This is my problem.

I am a complete dummy. I have read tutorials for months now how to setup samba, and I simply don't get it.
I have a PC with ubuntu, lets call it PC A, and another two with Vista and ubuntu, PCs B and C. 
Each have their own name and password to login.
I guess I need to have them all in the same workgroup, just like in windows.
How do I create a samba user and password on A to allow B and C to access and modify files in a shared folder on A? How do I configure samba? I also want to have to enter a password to access the shared folder. 
I have managed to get it going sometimes, but one PC I get asked for a user and password I do not have to access anotherone, on another PC I have free access and permissions to the same PC that asked for a password on the other,..., sometimes it simply won't work.:P
I've been trying for ages, and I'm starting to feel an absolute idiot! :confused:
I am using ubuntu 10.04 and windows XP and Vista.
Any tutorials for dummies like myself that go through a step by step guide from scratch? Could anybody here guide step by step to do this? This must be dead simple, but I simply haven't been capable yet of doing so myself.
Thank you.:)

---

### Post by wjp.reg on 2011-01-09
You might get the help you need from this page: [http://www.techotopia.com/index.php/Sharing_Ubuntu_Linux_Folders_with_Remote_Windows_Systems]("http://www.techotopia.com/index.php/Sharing_Ubuntu_Linux_Folders_with_Remote_Windows_Systems")
Good Luck!

---

### Post by Morbius1 on 2011-01-09
> How do I create a samba user and password on A to allow B and C to access and modify files in a shared folder on A?Creating a samba user is a two step process:

You have to create a local user on PC-A. For example for the user on PC-B - "userb":
```
sudo useradd -s /bin/true userb
```[COLOR=Blue]*This will create a linux user on PC-A that has no local PC-A logon capability and no server home directory.*[/COLOR]

Then you need to create the samba password for that user:
```
sudo smbpasswd -a userb
```[COLOR=Blue]*This will add AND enable a samba password for userb*[/COLOR]
> How do I configure samba? 
I have managed to get it going sometimes ....It seems you've tried to configure Samba already but there are two different methods that can be used to create samba shares and you didn't tell us what method you are using. If you post the output of the following commands it will tell us what method you are using and how you are using it:
```
testparm -s
``````
net usershare info --long
```

---

