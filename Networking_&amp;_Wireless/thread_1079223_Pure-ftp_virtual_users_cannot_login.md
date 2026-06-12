---
title: "Pure-ftp virtual users cannot login"
date: 2009-02-24
forum: Networking &amp; Wireless
---

### Post by oliver369 on 2009-02-24
Hi there,

I am trying to set up an FTP server which only offers access to virtual users.

The set-up I have is very straight forward:
[LIST]
[*]Installed Ubuntu 8.10
[*]Installed PureAdmin from the Add/Remove Applications
[*]Added a virtual user by the name of 'testftp' from the Pure Admin
[/LIST]

If I try to log in to the FTP server with the virtual user 'testftp' I get 530 Login authentication failed.

If I try to login with my system account it logs in correctly and I see my home directory.

What I need to be able to define is that Pure FTP only uses virtual users and not system accounts.

How can configure this?

---

### Post by Eeqmcsq on 2009-05-31
I can answer half your problem. I tested this using the GUI app "pureadmin" in Xubuntu 9.04. Where I use mousepad for the text editor, you can use gedit in Ubuntu.

You will need to create this soft link to tell pure-ftp to include virtual user authentication:

```
sudo ln -s /etc/pure-ftpd/conf/PureDB /etc/pure-ftpd/auth/50pure
```

Now, restart the ftp server and try your virtual user. The next problem you might run into will be this error: "530 Sorry, but I can't trust you". This error is caused by your virtual user's userID and groupID being too low. The minimum allowed ID number is defined in /etc/pure-ftpd/conf/MinUID, which you can read in any text editor. The default is 1000.

You can either change the virtual user's userID and groupID to a user and/or group that's higher than 1000, or you can lower the limit. To lower the limit, you can edit the text file and change the number:

```
sudo mousepad /etc/pure-ftpd/conf/MinUID
```

Now, restart the ftp server and your virtual users should now be able to log in.

As for disabling logging in with the system accounts, I couldn't figure out that answer.

---

### Post by Sapnix on 2009-07-05
thx worked on 8.04 didn't on 9.04

---

### Post by deebocean on 2009-09-28
after "as Eeqmcsq said" ```
sudo ln -s /etc/pure-ftpd/conf/PureDB /etc/pure-ftpd/auth/50pure
```
you may try "to change "1000" to a lower number:
```
sudo gedit /etc/pure-ftpd/conf/MinUID
```
or to choose a linux user from pureadmin
```
Applications --> System Tool --> PureAdmin --> PureFtpd --> Manage Users --> "choose one of created virtual users" --> Edit user --> from the right column choose user and group of a user with ID min (1000).

```
you may want to create a new user for this purpose before configuring the PureAdmin.
```
sudo adduser ftpuser1
```
that worked for me.

---

### Post by glacoon on 2009-11-10
Hello,

I had the same *530 error* on my side with pure-ftp and pureadmin installation (on Kubuntu Karmic).

I changed three things to make it work:

1/ I used PureAdmin to create the virtual users, and by default the paths to the config files where different from the ones created by pure-pw command ([FONT=Courier New]/etc/pureftpd.pdb[/FONT] and [FONT=Courier New]/etc/pureftpd.passwd[/FONT] instead of [FONT=Courier New]/etc/pure-ftpd/pureftpd.pdb[/FONT] and [FONT=Courier New]/etc/pure-ftpd/pureftpd.passwd[/FONT]) => To change this, I used the option to search automatically for these files in the 3rd settings tab of PureAdmin)

2/ The [FONT=Courier New]/etc/pure-ftpd/conf[/FONT] folder was empty after my installation, I had to create the file about virtual users: I created the [FONT=Courier New]/etc/pure-ftpd/conf/PureDB[/FONT] file containing the single line *[FONT=Courier New]/etc/pure-ftpd/pureftpd.pdb[/FONT]*

3/ Finally, as said above:
```
sudo ln -s /etc/pure-ftpd/conf/PureDB /etc/pure-ftpd/auth/50pure
```

---

### Post by Hugo de la cruz on 2010-11-09
ok it work i follow the howto from this link [http://ubuntuforums.org/archive/index.php/t-91052.html](http://ubuntuforums.org/archive/index.php/t-91052.html)

and add the code

sudo ln -s /etc/pure-ftpd/conf/PureDB /etc/pure-ftpd/auth/50pure 

and it work on ubuntu 10.10 niceeeee

:guitar:

---

