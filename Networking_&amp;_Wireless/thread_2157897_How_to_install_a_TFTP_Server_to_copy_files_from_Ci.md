---
title: "How to install a TFTP Server to copy files from Cisco Switch/Router"
date: 2013-06-27
forum: Networking &amp; Wireless
---

### Post by lp.descamps on 2013-06-27
Hi,

I've been trying to get a tftp server up and running on lubuntu but can't seem to get it working.

tried tftpd-hpa and followed the how-to's around but no luck just get a time-out. I did tried locally aswell ... no luck.

anyone would have ideas?

thanks

---

### Post by guyr34 on 2013-06-27
Install atftpd

---

### Post by Lars Noodén on 2013-06-27
TFTP is different from FTP.  You need an actual TFTP client to connect to a TFTP server.  The repositories have HPA's tftp client listed as the package 'tftp-hpa'

When you do try to connect using the tftp client, you are quite limited in what you can do.  Enter a question mark (?) to see the list of tftp commands available.  

Can you explain a little what you are trying to do and how TFTP fits into this?  It's not exactly a commonly used protocol.

---

### Post by hartz on 2013-06-27
> **lp.descamps said:**
> Hi,

I've been trying to get a tftp server up and running on lubuntu but can't seem to get it working.

tried tftpd-hpa and followed the how-to's around but no luck just get a time-out. I did tried locally aswell ... no luck.

anyone would have ideas?

thanks

What is your problem symptoms (Time-out?  Connection refused?  Error message)

What is the service status?
Enter the command
status tftpd-hpa
If it is not running, start it with
start tftpd-hpa

What did you put in the config file (/etc/default/tftpd-hpa)

Does it exist and what is the permissions on the TFTP directory specified in the config file (eg /var/lib/tftpboot)

Did you eliminate having a networking problem (Eg IP addresses, routing, etc)

---

### Post by lp.descamps on 2013-06-28
> **guyr34 said:**
> Install atftpd

Hi Guyr34,

thanks for your reply. I installed it now I get permission is denied
cheers

---

### Post by lp.descamps on 2013-06-28
Hi Lars,
Cisco uses TFTP protocol for maintenance like copy new OS or config file etc . i use tftp on cisco a lot with tftpd32 in windows but i got a lubuntu laptop which i would like to use aswell.
hope that make sense

thanks

---

### Post by lp.descamps on 2013-06-28
Hi Lars,
Cisco uses TFTP protocol for maintenance like copy new OS or config file etc . i use tftp on cisco a lot with tftpd32 in windows but i got a lubuntu laptop which i would like to use aswell.
hope that make sense

thanks

---

### Post by lp.descamps on 2013-06-28
Hi Hartz,

since I installed atftpd as suggested earlier in this thread. I get permission denied. is atftpd a dependencies of tftpd-hpa or another app? I think it s a different one. which one should go with?
the service was stopped. but it was running before so i guess it stopped because i installed atftpd. i start the service and still getting perm denied...

the config is 
# /etc/default/tftpd-hpa

RUN_DAEMON="no"
TFTP_USERNAME="tftp"
TFTP_DIRECTORY="/tftp"
TFTP_ADDRESS="0.0.0.0:69"
TFTP_OPTIONS="-secure -create -v"

the folder /tftp perm is 

ls -la /tftp/
total 8
drwxrwxrwx  2 root  root  4096 Jun 27 08:51 .
drwxr-xr-x 24 root  root  4096 Jun 27 08:39 ..
-rw-rw-r--  1 lpdne lpdne    0 Jun 26 16:20 c2900-confg
-rw-rw-r--  1 lpdne lpdne    0 Jun 27 08:31 c3550-confg
-rw-rw-r--  1 lpdne lpdne    0 Jun 27 08:51 New
the 3 files in there were created locally.

i dont think it s a network issue as i get a perm denied I can now copy a file from /tftp to cisco switch

so definitely an issue with perm...
thanks

---

### Post by lp.descamps on 2013-06-28
i does work now . i had del the test files in /tftp
but wonder what's the correct process of installing a tftp server on lubuntu :-)

thanks Guyr

---

### Post by Lars Noodén on 2013-06-28
> **lp.descamps said:**
> but wonder what's the correct process of installing a tftp server on lubuntu :-)

This ought to do it:

```

sudo apt-get update
sudo apt-get install tftpd-hpa

```

Then your files go in /var/lib/tftpboot

If you also need the TFTP client then you can add the package 'tftp-hpa'

---

### Post by hartz on 2013-06-28
> **lp.descamps said:**
> Hi Hartz,

since I installed atftpd as suggested earlier in this thread. I get permission denied. is atftpd a dependencies of tftpd-hpa or another app? I think it s a different one. which one should go with?

Just select one because if you have both they can clash when they try to start up on the same port, one will start first, the otehr will fail because the port (:69) is already in use.  If you have two with different configuration and you don't know which one is running then you will not know what settings apply, etc.

> **lp.descamps said:**
> 
the service was stopped. but it was running before so i guess it stopped because i installed atftpd. i start the service and still getting perm denied...


A stopped service NORMALLY gives you a connection refused, not a connection time-out.  Except that tftp is sometimes a different beast.

> **lp.descamps said:**
> 
the config is 
# /etc/default/tftpd-hpa

RUN_DAEMON="no"
TFTP_USERNAME="tftp"
TFTP_DIRECTORY="/tftp"
TFTP_ADDRESS="0.0.0.0:69"
TFTP_OPTIONS="-secure -create -v"


I don't know if this is a copy-paste error or what, but the TFTP client will not accept files created unless you specify --create (With a double-dash)

The secure option should have a double-dash as well.  In that case /tftp is seen as / by the client connecting.  This means the client should just put the file, not specify a target directory.  

> **lp.descamps said:**
> 
the folder /tftp perm is 

ls -la /tftp/
total 8
drwxrwxrwx  2 root  root  4096 Jun 27 08:51 .
drwxr-xr-x 24 root  root  4096 Jun 27 08:39 ..
-rw-rw-r--  1 lpdne lpdne    0 Jun 26 16:20 c2900-confg
-rw-rw-r--  1 lpdne lpdne    0 Jun 27 08:31 c3550-confg
-rw-rw-r--  1 lpdne lpdne    0 Jun 27 08:51 New
the 3 files in there were created locally.


Yes, those existing files are not writeable by the client.

> **lp.descamps said:**
> 
i dont think it s a network issue as i get a perm denied I can now copy a file from /tftp to cisco switch

so definitely an issue with perm...
thanks

---

