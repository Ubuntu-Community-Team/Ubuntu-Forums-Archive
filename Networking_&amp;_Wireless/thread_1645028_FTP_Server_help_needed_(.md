---
title: "FTP Server help needed :("
date: 2010-12-14
forum: Networking &amp; Wireless
---

### Post by viperce on 2010-12-14
Hi All,

I am fairly new to linux & i was wondering what a decent FTP server would be to use,
Basically i want to setup a ftp server with virtual users.
What would be the easiest way to do this.

Also is it possible to give a user Administrator rights to all the ubuntu linux folders like /etc /usr /var ?

Thanks in advance :D

---

### Post by shredIt on 2010-12-14
Hi,

First of all I wouldn't recommend you to give access to system-configuration files over ftp.

I'm a big fan of pure-ftpd FTP-Server, because it's well documented and I haven't found no exploits for it in the last few months. ProFTPd's just got a hacked server last week or the week before the last week as far as I know from heise.

If you want to set up a server, not in a virtual machine i would recommend you first to understand the basics of a unix system, because from one day to another you will have a problem and then you probably will have no clue what to do except reinstalling the whole system.

Maybe you'll set up a test server using virtualbox or vmware-player and follow the 
perfect-server howto to learn the basics...

[http://www.google.at/url?q=http://www.howtoforge.com/perfect-server-debian-lenny-ispconfig3&sa=X&ei=GigHTenQIoG18QPFwNU3&ved=0CDAQrAIoATAB&usg=AFQjCNEatqHOp2eJr9_KQCPAftvIt-fsBQ](http://www.google.at/url?q=http://www.howtoforge.com/perfect-server-debian-lenny-ispconfig3&sa=X&ei=GigHTenQIoG18QPFwNU3&ved=0CDAQrAIoATAB&usg=AFQjCNEatqHOp2eJr9_KQCPAftvIt-fsBQ)

Make yourself comfortable with SSH, fail2ban and iptables!

Have fun ;-)

greetz

---

### Post by viperce on 2010-12-14
Thanks i will look into  pure-ftpd..

---

### Post by HermanAB on 2010-12-14
Howdy,

Vsftpd is also good.

Note however, that FTP is insecure, so you should not provide any system access via FTP, since it will get your machine hacked by some script kiddie in no time flat.

---

### Post by viperce on 2010-12-14
what would be a secure way of doing it then?

---

### Post by Cabalbl4 on 2010-12-14
> **viperce said:**
> what would be a secure way of doing it then?

At first, configure it not to use standard ftp port. For example 1280 instead of 21. This will give a good defense against many automated attacks. 

As for me, I am using proftpd for years with no problems for now.

You can see the guide here: [http://ubuntuforums.org/showthread.php?t=79588](http://ubuntuforums.org/showthread.php?t=79588)

If you wish to remote-administer the machine, you may try webmin. It can handle almost any remote operation.

---

### Post by CharlesA on 2010-12-14
> **viperce said:**
> what would be a secure way of doing it then?

Use SSH/SFTP if you need access to system files.

---

### Post by viperce on 2011-02-18
working now thanks charles

---

### Post by CharlesA on 2011-02-18
Glad you got it working. :)

Don't forget to mark the thread as solved.

---

