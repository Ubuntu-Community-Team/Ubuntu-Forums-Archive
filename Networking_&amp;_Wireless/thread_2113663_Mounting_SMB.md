---
title: "Mounting SMB"
date: 2013-02-08
forum: Networking &amp; Wireless
---

### Post by CivBase on 2013-02-08
I'm new to Ubuntu, but I prefer using VIM on a UNIX platform when coding in C.  My Ubuntu install (12.10, 64-bit) is in VMware and, since I have multiple computers, I save my code to a network location at my college so I can access it no matter which computer I'm using.  I've successfully connect to the server through the nautilus GUI, but I would very much like to access it from the terminal so I can quickly make changes and compile.

Google has provided me with a number of commands to mount to a directory, but none of them have succeeded.  'smbmount' is not recognized as a command and 'mount -t cifs' tells me "mount error(13): Permission denied".  When I try to access it through smbclient, it says "NT_STATUS_LOGON_FAILURE".

Am I missing something here or just doing something horribly wrong?  Thanks in advance!

---

### Post by papibe on 2013-02-08
Hi CivBase.

You may need to install a package to mount cifs partitions:
```
sudo apt-get install cifs-utils
```
Let us know how it goes.
Regards.

---

### Post by CivBase on 2013-02-12
Hey, sorry about taking so long to get back.  cifs-utils is already installed with the newest version.

---

### Post by papibe on 2013-02-13
When you mount a cifs partition you need use sudo. Then your local password is asked (the first time), then for a few minutes, no password will be asked.

Then, in order to mount a samba share in 'user' mode, you will need to provide a user and password. If no credentials file is used, the username is taken from your current user, and a password is asked. That password is actually the remote user's password (on the samba server).

Just making sure you have considered all this steps.

Let us know how it goes.
Regards.

---

### Post by CivBase on 2013-02-13
Yah, I considered all that but I still couldn't get it to work.

A friend of mine suggested I use sshfs and it worked like a charm, so I guess all is well now.  Thanks for the help!

---

### Post by papibe on 2013-02-13
The following situation:
```
$ smbclient //server/share
Enter user's password: 
session setup failed: NT_STATUS_LOGON_FAILURE

```
Usually happens when you use your local credentials to login into a remote server, which have a different password for the user.

Often that can be fixed by setting a password on the samba server using the command 'smbpasswd'.

Another alternative is to get the connection either using the full domain name of the user:
```
smbclient //server/share -U WORKGROUP\user
```
Or using the guest account:
```
smbclient //server/share -U guest
```
(password should be 'guest' or empty).

Let us know how it goes.
Regards.

---

