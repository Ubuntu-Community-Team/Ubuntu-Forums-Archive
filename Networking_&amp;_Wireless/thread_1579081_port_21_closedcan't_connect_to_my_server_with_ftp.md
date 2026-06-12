---
title: "port 21 closed/can't connect to my server with ftp"
date: 2010-09-21
forum: Networking &amp; Wireless
---

### Post by Lakeside5 on 2010-09-21
Wow, don't know why I seem to have so much trouble with this ftp stuff.   I have so start all over a few times, reinstalling Lucid Lynx destop all over, and adding the needed files to make it a server.  I am just trying to do something simple for now- just having a localhost server environment to develop my joomla website, and later on host it from my server 'out there' (I already have a domain name and dynDNS service with nameservers etc. but don't want to do that yet, as I have in the past with my router forwarding port 80, and actually got hacked! so I don't want to do that again until I learn more about security) My problem right now is that I can't even get the localhost ftp to 'connect to the server'.  i know the host name (localhost) and username/password that I set when I set up Lucid Lynx, and I'm sure that is what I use for the ftp usernamepassword, host etc.  And I put port 21 for the port.  I see from 'Shields Up' that my port 21 is closed.  So I followed advice on a thread and entered a few commands in the terminal to ad iptables etc. But still, port 21 is closed and I can't install components  with the Joomla installer in admin's backend.  And I can't use fireftp to even change permissions in my local folders. What do i do next, open port 21 somehow?  I saw a terminal command about opening port 21 that was simple but I forget it.

---

### Post by pricetech on 2010-09-21
Shields Up is testing your WAN IP, assigned by your ISP, not your LAN IP, which is what you should be using for testing purposes if you don't want it exposed the the whole world just yet.

What FTP Server did you install ??

What FTP Client are you using ??

---

### Post by Lakeside5 on 2010-09-21
Ah, ftp server..then I missed a step I guess.Never seem to get this ftp stuff.  I am using firestarter for the client, but as for the server.  What do you  suggest?  I am using Ubuntu Luckd Lynx desktop (with LAMP added, for a localhost server). Is putty a ftp server?  I think I had that installed in the past.  Sorry to be so dense about ftp. Thanks for your help
update:
After googling some, I decided to install vsftpd.  I followed the tutorial here:  [http://www.wikihow.com/Set-up-an-FTP-Server-in-Ubuntu-Linux](http://www.wikihow.com/Set-up-an-FTP-Server-in-Ubuntu-Linux)
but am not sure if the last step (resart of server) worked as I got this message in my terminal after trying to restart:   sudo /etc/init.d/vsftpd restart
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service vsftpd restart   (WHAT is that 'service' where do I find it??)

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the restart(8) utility, e.g. restart vsftp
vsftpd start/running, process 2083

Anyway, I just keep trying,and would really like to just be able to develop my Joomla site, to use ftp to change file permissions, and be able to use ftp to install extensions.  I actually had this all working in the past so I don't know what I am doing wrong!
So confusing, on the vsftp tutorial it mentioned something about the files you want to transfer being placed in the root folder of the ftp server?  All my files (joomla installation) are in the server root:  /var/www, so I'm not sure what to do.

---

