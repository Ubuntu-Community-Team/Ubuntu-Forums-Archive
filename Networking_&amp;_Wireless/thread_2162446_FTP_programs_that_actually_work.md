---
title: "FTP programs that actually work???"
date: 2013-07-14
forum: Networking &amp; Wireless
---

### Post by vailixi on 2013-07-14
I've set up FTP before before. I can't remember it being this much work. I tried VSFTPD which doesn't work right out of box. I kept getting a 550 error and a 550 error. I've changed the stuff about 10 different times.

Anybody got an example .conf file that actually works?

If you've installed an FTP server recently please post your command line history and anything else relevant.

Better yet what are some FTP servers that actually work right out of the box without editing more files?

---

### Post by Lars Noodén on 2013-07-14
If you want to transfer files *securely* then you want SFTP.  It works out of the box and is part of the package openssh-server.  You can connect to it using your file manager (e.g. Nautilus) or a dedicated client (e.g. FileZilla)

If you really known what FTP is and want it anyway, the two main servers vsftp and proftp will require a little fiddling, there is no way around that.  

[http://www.openlogic.com/wazi/bid/188103/Stop-Using-FTP-How-to-Transfer-Files-Securely](http://www.openlogic.com/wazi/bid/188103/Stop-Using-FTP-How-to-Transfer-Files-Securely)
[http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp](http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp)

---

### Post by vailixi on 2013-07-14
Uninstalled vsftpd and reinstalled openssh-server

Getting this error. now.

Status:    Connecting to 192.168.0.15:21...
Status:    Connection attempt failed with "ECONNREFUSED - Connection refused by server".
Error:    Could not connect to server

Are there some other permissions somewhere on my system I need to set to allow FTP access?

---

### Post by 2Stoned on 2013-07-14
> **vailixi said:**
> Getting this error. now.

Status:    Connecting to 192.168.0.15:21...
Status:    Connection attempt failed with "ECONNREFUSED - Connection refused by server".
Error:    Could not connect to server


I think this is a firewall issue.

---

### Post by Lars Noodén on 2013-07-15
The error shows that you are trying to connect using FTP.  If you are using openssh-server then you have SFTP and need to use that instead.  If you are using the shell, you can type this:

```

sftp 192.168.0.15

```

Fill in whatever is the right IP address for your SFTP server.  If you want a graphical tool you can use FileZilla.  Or you can run your file manager (such as Nautilus) and press *ctrl-L* to connect to a remote server.  In the address box enter the following URI

```

sftp://user@192.168.0.15/

```

Substitute 'user' for your user name on the remote system and use the right IP address.

---

