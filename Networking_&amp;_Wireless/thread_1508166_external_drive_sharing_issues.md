---
title: "external drive sharing issues"
date: 2010-06-12
forum: Networking &amp; Wireless
---

### Post by Cyborgoat on 2010-06-12
I am having issues with my 1TB ext. segate drive on my samba shares.  I can go to the Vista laptop and see the contents and open them, watch the movies, but am unable to write to or copy from this drive from the vista laptop. Actually I am unable to write to the main HDD as well so I am sure I have not setup something right.  I am running 10.04,  

thanks

---

### Post by Morbius1 on 2010-06-12
Please post the output of the following commands:

```
net usershare info
sudo net usershare info
testparm -s
```

---

### Post by Cyborgoat on 2010-06-14
michael@Cybor-Goat:~$ net usershare info
[interprize_]
path=/media/Interprize_
comment=
usershare_acl=Everyone:F,
guest_ok=n

[music]
path=/home/michael/Music
comment=
usershare_acl=Everyone:R,
guest_ok=y

[documents]
path=/home/michael/Documents
comment=
usershare_acl=Everyone:F,
guest_ok=y

[movies]
path=/home/michael/Movies
comment=
usershare_acl=Everyone:R,
guest_ok=y


info_fn: Error was Path is not a directory.
info_fn: file /var/lib/samba/usershares/interprize is not a well formed usershare file.
info_fn: Error was Path is not a directory.
michael@Cybor-Goat:~$ sudo net usershare info
[sudo] password for michael: 
michael@Cybor-Goat:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[michael]"
Processing section "[Interprize]"
Loaded services file OK.
Server role: ROLE_STANDALONE
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
    usershare owner only = No
    panic action = /usr/share/samba/panic-action %d

[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    browseable = No
    browsable = No

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers

[michael]
    path = /home/michael
    guest ok = Yes

[Interprize]
    path = /media/Interprize
    guest ok = Yes

---

### Post by Morbius1 on 2010-06-14
You are using two completely different methods to share folders using Samba: Nautilus-share and Classic-share. That's not recommend. 

You are also using both methods on the same target - that won't work:
Nautilus-share:
> [interprize_]
path=/media/Interprize
comment=
usershare_acl=Everyone:F,
guest_ok=nClassic-share:
> [Interprize]
    path = /media/Interprize
    guest ok = Yes     You'll note that in Nautilus-share you're not allowing guests to a writable share. In the Classic-share you're allowing guests to a read-only share. 

You also have shares within shares which really don't work:
> [michael]
    path = /home/michael
    guest ok = Yes*[COLOR=Blue]Allowing guests to a read-only parent folder.[/COLOR]*
> 
[documents]
path=/home/michael/Documents
comment=
usershare_acl=Everyone:F,
guest_ok=y*[COLOR=Blue]Allowing guests to a writable child share.[/COLOR]*

My recommendation is to remove the Classic-shares since the Nautilus-shares seem to be configured correctly. Just go into the Samba GUI utility you're using and remove  the /home/michael and /media/Interprize shares.

The external drive is another matter but let see how far we get after removing the classic-shares first.

---

### Post by Cyborgoat on 2010-06-14
Thanks, I will see what I can do.

---

### Post by Cyborgoat on 2010-06-14
Whats the difference between nautilus and clasic shares and how did I get both of them on my OS?

---

### Post by Morbius1 on 2010-06-15
Both methods are just different approaches to using Samba to share folders. Nautilus-shares is relative new but has been part of samba ( where it's called "usershares" ) for years.

Nautilus-share allows any user to share a directory he owns without becoming root. It's shares are defined in [COLOR=Blue]/var/lib/samba/usershares[/COLOR].

Classic-shares is the traditional method and is still the more configurable ( and more complex to use ) method. Classic-shares allows you to do things at a specific share level that Nautilus-share cannot. It's shares are defined in [COLOR=Blue]/etc/samba/smb.conf[/COLOR]

So it's basically a trade off between configurability vs ease of use. I would argue that for the average home user with simple shares , Nautilus-shares is all that's needed. But it depends on the users requirements.

---

### Post by Cyborgoat on 2010-06-23
sorry to keep bothering you, but do I simply rename the smb.conf file or what would be the best way to eliminate the classic shares.  one other question, what is a ssh share? and when would ssh be used?
Thanks

---

### Post by Cyborgoat on 2010-06-24
What I had in mind was I would like to create a firewall/file server for my home.  I have 2 tb's of hd to share and to be used to back up other items sent from others on the network.  Can I accomplish this on one unit or is it recommended the firewall be seperate from a server?  The external drive previously mentioned is "interprize".

So with all mentioned which is better nautilus or classic shares?

Would also like to log web sites others on the network has been on.

Is there any good literature or websites to help with learning networking with linux?  

Thanks

---

### Post by Morbius1 on 2010-06-24
To undo any of the shares you created simply reverse the steps you did to create them. As for your last post I have no experience is setting up that type of network, sorry.

---

