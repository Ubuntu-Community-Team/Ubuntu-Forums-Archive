---
title: "samba and [homes]"
date: 2010-10-19
forum: Networking &amp; Wireless
---

### Post by aden on 2010-10-19
Hello. I have recently installed samba and started to configure it. Ive managed to make public folder pretty easily but i wish to have private folder for every user as well. 
So i added to smb.conf


```

[homes]
comment = katalog
writable = yes

```
Loging on another ubuntu and trying to acces home directory through

smb://ip/user_name i am receiving error:

error: failed to mount windows share
Please select another viewer and try again

users are added to smb.

Any clue whats wrong with it?

---

### Post by mstjohn1974 on 2010-10-19
what is the path of [homes]?

---

### Post by luvshines on 2010-10-19
What does it say from terminal:
```
smbclient //<ip>/<user-name> -U<user-name>%<user-passwd>
```

---

### Post by aden on 2010-10-19
mstjohn1974:
kinda unknown ;p i havent found requirements to use one. but i had previously added to [homes] path = x/x/x and i doesnt worked also (x's were the folder names ofc)

luvshines
```

Domain=[DOM] OS=[Unix] Server=[Samba 3.5.4]
tree connect failed: NT_STATUS_BAD_NETWORK_NAME

```

---

### Post by beegary on 2010-10-19
Have you added the user to the Samba users list?
From [https://help.ubuntu.com/6.06/ubuntu/serverguide/C/configuring-samba.html](https://help.ubuntu.com/6.06/ubuntu/serverguide/C/configuring-samba.html)

> **User Accounts**

                                                                                                 User Accounts define persons with some level of  authorization to use certain computer and network resources.  Typically,  in a network               environment, a user account is provided to each person  allowed to access a computer or network, where policies and permissions  then               define what explicit rights that user account has access  to.  To define SAMBA network users for your Ubuntu system, you may use  the               **smbpasswd** command.  For example to add a SAMBA user to your Ubuntu system with the user name               jseinfeld, you would enter this command at the prompt:              
                    
                   **smbpasswd -a jseinfeld**                                      
                                  The **smbpasswd** application will then prompt you to enter a password for the user:               


---

### Post by Morbius1 on 2010-10-19
luvshines, I don't know what you think but the last time I've seen that error it was because the full path to the target folder didn't have the correct permissions.

/home must have a 0755 or at least a 0711
and /home/$USER must have the same as above.

If you did a:
```
ls -al /home
```it would tell you if your permissions are correct

---

### Post by aden on 2010-10-19
beegary:
Yes they are added. Been using public folder with guest = no so user had to log in to enter directory and it worked just fine

Morbius1
I was thinking about permissions earlier so just in case i have set it all to 777 even and its still the same

edit: its alive! ok.. i was kinda stupid. All at all it seems like i had to make directory for each user as well, like they login name. Got used to Active Directory and though it will make it by itself upon logging or something. 
However ive got another question. Everything is ok if i log in through console or by using smb://<ip>/<user_name> but.. through places -> network etc etc doesnt work. Public directory works with no problem. So if i get there throught smb://........ folder gets automatically mounted to the desktop, but why cant it work regular way throught network or something?

---

### Post by luvshines on 2010-10-19
**Deleted** (by the time my post was submitted it was already working :) [hate my sluggish internet connection] )

---

### Post by aden on 2010-10-19
Whole smb.conf:
```

Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[share]"
Processing section "[homes]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
    workgroup = DOM
    netbios name = SERWEREK
    server string = domowy serwer plikow

[share]
    comment = share
    path = /home/aden/share
    read only = No
    create mask = 0777
    directory mask = 0777
    guest ok = Yes

[homes]
    comment = katalog
    path = /home/aden/homes/%S
    read only = No

```

some of the names like server string are not in english, not important tho.
edit: looks like it doesnt showed
```

security = user

```
which is in the [global] section of smb.conf

---

### Post by Morbius1 on 2010-10-19
> However ive got another question. Everything is ok if i log in through  console or by using smb://<ip>/<user_name> but.. through  places -> network etc etc doesnt work. Public directory works with no  problem. So if i get there throught smb://........ folder gets  automatically mounted to the desktop, but why cant it work regular way  throught network or something?Are you talking about the [homes] share?

I do not believe it's browseable through Places > Network like a normal share because it's created "on the fly" the moment the remote user asks for it. It uses the [homes] share definition as a template and creates a share for that user at that moment. If you want them to show up under places > network you need to actually create separate shares for each of them and use a "valid user =" option to restrict it's use to that user.

Anyway that's how I remember it working :wink:

---

### Post by aden on 2010-10-19
I see. Well thanks for help everyone. After all it works ;]

---

