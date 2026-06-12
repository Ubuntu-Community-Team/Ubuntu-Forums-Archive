---
title: "smbclient fails while mount -t cifs works"
date: 2012-11-18
forum: Networking &amp; Wireless
---

### Post by ffonz on 2012-11-18
I have a Plextor NAS PX-EH. Since a few months (I don't know exactly when) I cannot contact Samba shares which need credentials any more. The Share without credentials don't give a problem. But I could still mount the shares.

I pinpointed the problem to smbclient & mount.

When I do 
```
sudo mount -t cifs -o username=alfons,password=secret //192.168.0.104/alfons ./log.tmp/
```everything is OK. I can see the content of the share.
But when I do
```
alfons@alfons-laptop:~$ smbclient //192.168.0.104/alfons --user=alfons
Enter alfons's password: 
session setup failed: NT_STATUS_LOGON_FAILURE
```I get an error.
When I set an empty password on the account on my NAS, I get the following result
```
alfons@alfons-laptop:~$ smbclient //192.168.0.104/alfons --user=alfons
Enter alfons's password: 
Anonymous login successful
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 2.2.11-ja-1.0]
tree connect failed: NT_STATUS_WRONG_PASSWORD

```This result seems odd to me.

I think there might be something wrong on the NAS side since I cannot login from several OS-es: Ubuntu, Windows 7 and a Windows XP virtual machine. But what?

The NAS is not easy to get in to. I cannot open a telnet session, or so. Only a Web interface, ftp and samba. I can set the factory defaults back, but then the hdd will be formatted and all data will be lost!

Does anyone have a clue?

Regards,

Alfons

---

### Post by ffonz on 2012-11-27
I discovered that the problem has to lie on the (Ubuntu) client side and not on the NAS. The problems I have with windows machines as well are separate from this, I think.

I used an Ubuntu bootable USB stick, and with that environment I had no troubles using smbclient to connect to my NAS.

But on my laptop with Ubuntu 12.04, smbclient fails. I think something got corrupted in the settings on my laptop.

Does anyone have a clue what might be wrong on the client side?

---

### Post by dannyboy79 on 2012-11-27
maybe the smbpasswd got changed on your client side?

---

### Post by ffonz on 2012-11-27
Hmmmm, sounds interesting. Could you explain a little more what I should look for?

---

### Post by dannyboy79 on 2012-11-28
kind of a shot in the dark, but issuing the following command may or may not work?

```
smbpasswd username
```
then it'll ask you for the users smbpasswd you want to use twice.

Also, try to use the -W switch along with your workgroup name and see if that works.

---

### Post by ffonz on 2012-11-29
I believe smbpasswd is not the right solution. I want to access a share that has a username that does not exist on my local machine. And smbpasswd demands that the user already exists on the local system. In my situation this is not the case (anymore).

The user on my local system is called 'alfons' and the owner of the samba share is called 'fotocopier'. And I know, in my previous examples I should have used the username 'fotocopier'. But even so it doesn't solve my problem.

---

