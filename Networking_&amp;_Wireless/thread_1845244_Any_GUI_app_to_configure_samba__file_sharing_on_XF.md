---
title: "Any GUI app to configure samba / file sharing on XFCE 4.8?"
date: 2011-09-16
forum: Networking &amp; Wireless
---

### Post by spsf on 2011-09-16
Hi 
I'm looking for an application to configure samba file/directory share under xfce 4.8, xubuntu 11.04.
Is there something just like gnome in ubuntu, where you just right click on a folder and select share using a simple GUI?

TIA

---

### Post by Morbius1 on 2011-09-16
One of the great disappointments is the disappearance of the following package:
```
thunar-shares-plugin
```It did for thunar what nautilus-share ( where you just right click on a folder and select share using a simple GUI ) did for Nautilus. It used to be there in previous versions but then it just disappeared.

You could install nautilus-share in XFCE which will bring with it just enough of Nautilus to make it work without installing all of Gnome.

Or you can install the following package:
```
system-config-samba
```It's a separate utility that creates classic samba shares but you can forget about any right click > share stuff. It also doesn't automatically modify permissions the way nautilus-share does and it can only be run after supplying sudo's password.

---

### Post by spsf on 2011-09-16
Morbius1 thank you
I have read about thunar-shares-plugin and also saw it in action with some old Mint XFCE version, was not able to install it by myself, I'm not very skilled at installing non .deb packages...
I have just installed system-config-samba in xubuntu 11.10 beta in VM, it did not work. 
I tried nautilus share, however it took over thunar, and I can't go back to it, lol...
I'll install in a spare HD just to try, I'll let you know later

Thank you for help!
Sergio

---

### Post by Morbius1 on 2011-09-16
>  I tried nautilus share, however it took over thunar, and I can't go back to it, lol...Not sure how that happened or if that's even possible. After it installs Nautilus you have to log out and login again fot the "Sharing Options" to appear and then double click /usr/share/applications/File Browser. 
> I have just installed system-config-samba in xubuntu 11.10 beta in VM, it did not work. What do you mean it did not work? You get error messages?

Try running it from the terminal:
```
gksu system-config-samba
```[COLOR=Blue]EDIT[/COLOR]: I have both of these implemented in Xubuntu 11.04 without any of your symptoms. Sorry for the bad advice.

---

### Post by spsf on 2011-09-17
It's NOT bad advice, I am the problem, I just have to say thank you again for trying to help me!
Actually system-config-samba launched and worked, but I could not see the shared folder from my other ubuntu machine...
I also installed GADMIN-SAMBA, which looks more complete app, however other box still not be able to see the shares on xubuntu.
I'll be back home only on tuesday and try it again.

---

### Post by Morbius1 on 2011-09-17
When you get back you might want to run the following commands which will provide you with information on how you are set up and give you error messages if it finds something that's wrong:
```
testparm -s
``````
smbtree
```BTW, and this is just my personal prejudices, but Gadmin-Samba will render your smb.conf into an incoherent mess that no one except a Systems Administrator with 10 years of experience will be able to debug.

---

### Post by CryNGRoad on 2011-12-02
I was looking for a solution to sharing in Thunar under xfce 4.8 as  well. What I have found to work fairly well is to just use a Thunar  custom action to create samba usershares with the net command.
Just create a custom action (Edit menu>Configure custom actions) to run the following command only on directories:
```
net usershare add %n %f "" Everyone:R guest_ok=y
```Note: The icon for the folder won't change, like it does for nautilus, but it does work.
 

 To unshare a folder, use this command from a terminal: 

 ```
net usershare delete *sharename*
``` where *sharename* is the name of the folder.

---

### Post by spsf on 2012-01-03
> **CryNGRoad said:**
> I was looking for a solution to sharing in Thunar under xfce 4.8 as  well. What I have found to work fairly well is to just use a Thunar  custom action to create samba usershares with the net command.
Just create a custom action (Edit menu>Configure custom actions) to run the following command only on directories:
```
net usershare add %n %f "" Everyone:R guest_ok=y
```Note: The icon for the folder won't change, like it does for nautilus, but it does work.
 

 To unshare a folder, use this command from a terminal: 

 ```
net usershare delete *sharename*
``` where *sharename* is the name of the folder.

Thanks! It works 100%!!

---

### Post by kholis on 2012-01-24
> **CryNGRoad said:**
> I was looking for a solution to sharing in Thunar under xfce 4.8 as  well. What I have found to work fairly well is to just use a Thunar  custom action to create samba usershares with the net command.
Just create a custom action (Edit menu>Configure custom actions) to run the following command only on directories:
```
net usershare add %n %f "" Everyone:R guest_ok=y
```Note: The icon for the folder won't change, like it does for nautilus, but it does work.
 

 To unshare a folder, use this command from a terminal: 

 ```
net usershare delete *sharename*
``` where *sharename* is the name of the folder.

It not works for me. Shared folder appear but cannot be opened. When I click it, it will display error message like:

[IMG]https://lh6.googleusercontent.com/-J97lsKomNrY/Tx6Gfgd98TI/AAAAAAAAAn4/uRE8fErsKiU/s800/thunar-share-error.png[/IMG]

Need help. Thanks

Note: I'm using Xubuntu 11.10

---

### Post by Morbius1 on 2012-01-24
What are the Linux permissions of the "shared" share?
```
ls -al /path/to/"shared"/folder
```

---

### Post by grege on 2012-01-24
Rather than installing Nautilus and Nautilus-Share you can install Dolphin and kdenetwork-filesharing and use it to setup shares. It will not take over the desktop like Nautilus, but it will drag in a lot of KDE. But then once it has done it's job you can remove it (maybe). Make sure Samba is installed first.

Dolphin is not as simple as right click share, you select configure file sharing and add the folders to the list.

---

### Post by Morbius1 on 2012-01-24
Actually, CryNGRoad had a very clever solution to this issue:
> Just create a custom action (Edit menu>Configure custom actions) to run the following command only on directories:
```
net usershare add %n %f "" Everyone:R guest_ok=y
```I would suggest just one more addition to that command in order to completely duplicate the actions taken by nautilus-share on Gnome for a guest accessible share:
```
 net usershare add %n %f "" Everyone:F guest_ok=y && chmod 777 %f
```
This way there is no need for Nautilus, Dolphin, or any other aquatic animal.

---

### Post by kholis on 2012-01-24
> **Morbius1 said:**
> What are the Linux permissions of the "shared" share?
```
ls -al /path/to/"shared"/folder
```

```

kholis@kalau:~$ ls -al /home/kholis/shared/
total 36
drwxrwxrwx   2 kholis kholis  4096 2012-01-24 21:24 .
drwxrwx--- 130 kholis kholis 32768 2012-01-24 18:04 ..
-rw-rw-r--   1 kholis kholis     0 2012-01-24 16:58 test.txt

```


> **Morbius1 said:**
> Actually, CryNGRoad had a very clever solution to this issue:
I would suggest just one more addition to that command in order to completely duplicate the actions taken by nautilus-share on Gnome for a guest accessible share:
```
 net usershare add %n %f "" Everyone:F guest_ok=y && chmod 777 %f
```
This way there is no need for Nautilus, Dolphin, or any other aquatic animal.

I've tried it. Produce same issue.
```

kholis@kalau:~$ net usershare info
[shared]
path=/home/kholis/shared
comment=
usershare_acl=Everyone:F,
guest_ok=y

``` 

I've tried this too, but produce same error. [http://forums.linuxmint.com/viewtopic.php?f=197&t=88255](http://forums.linuxmint.com/viewtopic.php?f=197&t=88255)

Maybe any other configuration in /etc/samba/smb.conf or something?

Thanks

---

### Post by Morbius1 on 2012-01-24
Your problem is here:
> drwxrwx--- 130 kholis kholis 32768 2012-01-24 18:04 ..Those last three "---" indicates the permissions allowed to "other" in linux and "guest" in Samba. The remote Samba guest has no permissions to open up your home directory to access the shared folder within it.

You have 2 options:

[1] chmod the home directory to allow guests to at least access the subfolders:
```
 chmod 0775 /home/kholis
```[2] Keep permissions on the home folder as it is and change your smb.conf to convert the remote guest to you:

Edit /etc/samba/smb.conf and add the following line to the [global] section - right under the workgroup line:
```
force user = kholis
```Then save the file and restart samba:
```
sudo service smbd restart
```

---

### Post by kholis on 2012-01-25
> **Morbius1 said:**
> Your problem is here:
Those last three "---" indicates the permissions allowed to "other" in linux and "guest" in Samba. The remote Samba guest has no permissions to open up your home directory to access the shared folder within it.

You have 2 options:

[1] chmod the home directory to allow guests to at least access the subfolders:
```
 chmod 0775 /home/kholis
```[2] Keep permissions on the home folder as it is and change your smb.conf to convert the remote guest to you:

Edit /etc/samba/smb.conf and add the following line to the [global] section - right under the workgroup line:
```
force user = kholis
```Then save the file and restart samba:
```
sudo service smbd restart
```

It's work now. Thanks Morbius for excellent explanation.

---

### Post by kruget on 2012-10-01
> **Morbius1 said:**
> Actually, CryNGRoad had a very clever solution to this issue:
I would suggest just one more addition to that command in order to completely duplicate the actions taken by nautilus-share on Gnome for a guest accessible share:
```
 net usershare add %n %f "" Everyone:F guest_ok=y && chmod 777 %f
```This way there is no need for Nautilus, Dolphin, or any other aquatic animal.

I tried those but still failed to see the shared folder in the network.

What is the prerequisite? Should i installed samba or something else first? 
I got fresh xubuntu 12.04.
- - - - -
edit: please ignore my post, i installed samba and the tips works. Sorry :)

---

### Post by Sketchworks on 2013-05-20
ok lost i installed samba and whatnot and have 3 other pc's with the same xubuntu 13.x install... i wanna use the main pc to store all the movies and whatnot and be able to access them from any of the pc's on the network any ideas?

---

### Post by seafury on 2013-10-01
Hi not sure you managed to sort it out.

Have you added your user name to smb?

In terminal add the following $sudo smbpasswd -a yourUsername  

It will ask for the sudo password and then your password for smb twice to check for typos.

Hope it helps.

Regards

---

