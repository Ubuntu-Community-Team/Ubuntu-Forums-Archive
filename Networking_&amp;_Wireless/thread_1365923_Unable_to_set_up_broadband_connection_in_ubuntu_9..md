---
title: "Unable to set up broadband connection in ubuntu 9.10"
date: 2009-12-27
forum: Networking &amp; Wireless
---

### Post by Tridibesh on 2009-12-27
At the present I am using Ubuntu 9.04. In it I can connect to the internet through my BSNL broadband( through Lan) connection and no problem occurs. But when I go to connect to the Internet in the same way as it in previous version in ubuntu 9.10, I become failure. It does not show any Auto Ethernet connection is established and it does not allow to connect to the DSL connection, which I created for my Broadband connection. This problem also occurs in Kubuntu 9.04 and 9.10. Is there any possibility of failing to detect the modem, because all the packages are got from out side of India, except the 9.04 and 8.10.

---

### Post by manojanand on 2009-12-28
I am also getting the same problem.In ubuntu 9.04 , internet was working fine but in 9.10 , it is not conecting. more over when i try to connect DSL connection , it first disconnects auto eth0 and then dails DSL comnnection. AT IPv4 seetings , i have selected auto IP.

---

### Post by manojanand on 2009-12-28
Check the following post and tell whether it works or not.
 
 
[http://ubuntuforums.org/showthread.php?t=1366212](http://ubuntuforums.org/showthread.php?t=1366212)

---

### Post by dineshs on 2009-12-30
If you are using BSNL broadband and has only one PC,better use PPPoE mode (save username and password in modem ie always ON mode) rather than using a PPPoE dialler ie Bridge mode.If you can tell what modem you are using I can tell you how to do this.Then edit the file /etc/resolv.conf to add the DNS server address.

---

### Post by bramma on 2009-12-31
Hi Friends!

After a big war, I found out a easy technique to configure broadband connection in Ubuntu 9.10.

The single package called "pppoeconf" do all the process..:P.
Just follow the steps...

1)Terminal->$pppoeconf
   Enter the password

2)New wizard will be opened.. It ll be very interactable one.. Just follow the instructions    given....

3)At the end after exiting from the wizard type

                        "pon dsl-provider" ----- to login

                        "poff" ----- to logout

Enjoy lot of doodles along with ubuntu:guitar:

---

