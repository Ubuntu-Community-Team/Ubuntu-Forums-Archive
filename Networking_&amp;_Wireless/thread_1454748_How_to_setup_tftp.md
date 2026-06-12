---
title: "How to setup tftp"
date: 2010-04-15
forum: Networking &amp; Wireless
---

### Post by shikhar_sharma on 2010-04-15
Hi guyz,
I am using ubuntu 9.10.i want to setup a tftp server on my machine so that my cisco router can take the configuration files from it.I installed tftp on my machine by following the article [http://www.davidsudjiman.info/2006/03/27/installing-and-setting-tftpd-in-ubuntu/](http://www.davidsudjiman.info/2006/03/27/installing-and-setting-tftpd-in-ubuntu/)
but i couldnt understand the 2nd step.wat i did was i created a file tftp in /etc/xinet.d with the script mentioned in step 2.is that wat i am supposed to do????also when i try to start the server by 
$ sudo /etc/init.d/xinetd start
then it says fail but when i type
$ sudo /etc/init.d/xinetd restart
it says pass

And the biggest problem is i dont know what is the name of this tftp server.
In cisco router u need to give the name of the tftp server or its ip address
and i dont know what that is.i tried giving the ip address of my system 
but it cant connect to it.HELP

---

