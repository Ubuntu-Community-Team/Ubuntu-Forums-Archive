---
title: "SSH: Connection closed by remote host"
date: 2009-10-22
forum: Networking &amp; Wireless
---

### Post by merlot on 2009-10-22
Hello,

I am currently using ubuntu 8.04, and running ssh server on my machine. I wanted to leave my computer on at home, and try to reach it from work. However, whenever I try to connect to my computer by 

ssh -l XXXX 123.123.123.123   (the numbers are just an example)

I get an error: Connection closed by remote host.

Here is what my ssh log file looks like after executing the command above,

Oct 22 23:54:51 phonon sshd[5914]: Received signal 15; terminating.
Oct 22 23:54:51 phonon sshd[17433]: socket: Address family not supported by protocol
Oct 22 23:54:51 phonon sshd[17433]: Server listening on 0.0.0.0 port 22.
Oct 22 20:16:31 phonon sshd[5914]: socket: Address family not supported by protocol

I searched this error on the net, but the information I found didn't help to solve my problem. I really appreciate if you could give me an idea to fix this. 

By the way, my /etc/hosts file is 
127.0.0.1 localhost
127.0.1.1 phonon

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts



Thank you very much.

---

### Post by duanedesign on 2009-10-22
"Address family not supported by protocol"
Makes me wonder if it is a IPv6/4 problem. Are you using IPv6 anywhere?

Maybe disabling SSH IPv6 support by adding "AddressFamily  inet" to /etc/ssh/sshd_config, and restarting the openssh daemon 'sudo /etc/init.d/sshd restart'

---

### Post by merlot on 2009-10-23
I tried that but it didn't help. I still have the same problem:(

---

### Post by dmizer on 2009-10-23
Try this instead: ssh -l XXXX [COLOR="Red"]your-ubuntu-username@[/COLOR]123.123.123.123

---

### Post by merlot on 2009-10-23
That didn't help it either.

---

### Post by dmizer on 2009-10-23
Did you forward port 22 through your router to your home machine?

---

### Post by merlot on 2009-10-23
I don't know. Could you explain how I can check it? and if it is not forwarded, how can forward it?

---

### Post by dmizer on 2009-10-23
> **merlot said:**
> I don't know. Could you explain how I can check it? and if it is not forwarded, how can forward it?

[http://portforward.com/](http://portforward.com/)

Before you do, make sure your ssh is properly secured ([login password is not enough](http://ubuntuforums.org/showthread.php?t=1255366)). [https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)

---

