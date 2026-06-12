---
title: "I cannot start the GUI / Getting dead.letter message"
date: 2010-06-17
forum: Networking &amp; Wireless
---

### Post by Diana Rogger on 2010-06-17
Hi Support,

I was connected to my intranet website using webmin.
I was getting a message that the hostname cannot be resolved.
I went into the /etc/hosts file and change the following:

127.0.0.1       localhost intranet.lab.net
192.168.50.100  intranet.lab.net

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

after changing this lin: 127.0.0.1       localhost intranet.lab.net
I cannot access the website using webmin.
I can logon localy but when I want to edit the /etc/hosts file using:

sudo vi /etc/hosts the file is open as readonly
I cannot edit nothing with the root account. 

When I do: sudo vi /etc/hosts

I am getting this message:

sudo: unable to resolve host HOASTNAME= "localhost"
[sudo] password for diana: /home/diana/dead.letter... Saved message in /home/diana/dead.letter

Is there a solution to get write access to change the hosts file?

Thank you in advanced

---

### Post by Diana Rogger on 2010-06-21
Hi,

I found a solution.
I downloaded the live CD and so I could edit the hosts file to change the lines below:

127.0.0.1 localhost intranet.lab.net
192.168.50.100 intranet.lab.net

is now

127.0.0.1 localhost 
192.168.50.100 intranet.lab.net

I can now use webmin to manage the website.
I can also ping the server now but I still have 1 problem:

I CANNOT START THE GUI

1. DO SOMEONE ON THIS FORUM KNOW HOW TO START THE GUI 
2. WHAT CAN I DO SO THAT THE SERVER CAN RESOLVE THE NAME OF THE SERVER? 

Thank you in advanced,

Diana

---

