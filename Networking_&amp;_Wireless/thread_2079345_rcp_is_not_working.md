---
title: "rcp is not working"
date: 2012-11-01
forum: Networking &amp; Wireless
---

### Post by 233x on 2012-11-01
Hello forum,
rcp doesn't work on my Lubuntu machine, because I receive an "connection refused" error when I try to connect. I can ping both hosts each other, so I assume that some necessary service is not running. I know that rcp is deprecated, but I need to use it.

---

### Post by spjackson on 2012-11-01
If at all possible you should use scp or rsync. However, if there is some genuine reason why it muct be rcp, then I think you need to install the rsh-server package on the target machine.

---

### Post by 233x on 2012-11-02
Thanks. rsh-server is already installed, but still the connection is refused. Could you please give me some procedures for systematic troubleshooting? The .rhosts file has the value "++". However, telnet is also unable to connect.

---

### Post by Lars Noodén on 2012-11-02
rcp is very insecure.  It would be a bad idea to start using it now that secure options are available.  Most systems have long since replaced rsh, rcp and ftp with ssh, scp and sftp.  Can you try scp instead?

---

### Post by codemaniac on 2012-11-02
> **Lars Noodén said:**
> rcp is very insecure.  It would be a bad idea to start using it now that secure options are available.  Most systems have long since replaced rsh, rcp and ftp with ssh, scp and sftp.  Can you try scp instead?

+1 what Lars said , 

++ the below archived document that highlights known flaws of a r* utility e.g. rlogin.

[www.cert.org/archive/pdf/98tr017.pdf](www.cert.org/archive/pdf/98tr017.pdf)

---

### Post by 233x on 2012-11-02
In this case, security doesn't matter, becaus it's only a LAN test project.

---

### Post by spjackson on 2012-11-02
> **233x said:**
> Thanks. rsh-server is already installed, but still the connection is refused. Could you please give me some procedures for systematic troubleshooting? The .rhosts file has the value "++". However, telnet is also unable to connect.
Can you tell from the error message that it's using port 514? In the absence of an intervening firewall I think that "connection refused" implies that there's nothing listening on the port.

You could try looking for log messages in /var/log on the target machine. I'm afraid that I don't really know anything about the rsh-server package, so I don't know what configuration or start up procedure to check.

---

### Post by 233x on 2012-11-03
I don't know if it's using port 514. Anyway, here is some other data that might be relevant:

Firewall setting on the destination machine:

Chain INPUT    (policy ACCEPT)
target             propt opt source       destination

Chain FORWARD   (policy ACCEPT)
target             propt opt source       destination

Chain OUTPUT   (policy ACCEPT)
target             propt opt source       destination


ssh seems to work without problems:

user1@ubuntu1:~$ ssh -vv
OpenSSH_6.0p1 Debian-3ubuntu1, OpenSSL 1.0.1c 10 May 2012
usage: ssh [-1246AaCfgKkMNnqsTtVvXxYy] [-b bind_address] [-c cipher_spec]
           [-D [bind_address:]port] [-e escape_char] [-F configfile]
           [-I pkcs11] [-i identity_file]
           [-L [bind_address:]port:host:hostport]
           [-l login_name] [-m mac_spec] [-O ctl_cmd] [-o option] [-p port]
           [-R [bind_address:]port:host:hostport] [-S ctl_path]
           [-W host:port] [-w local_tun[:remote_tun]]
           [user@]hostname [command]


Entries in var/log/auth.log:

Nov 3 11:46:23 ubuntu1 sshd[1655]: Accepted password for user1 from
          192.168.0.100 port 49318 ssh2 
Nov 3 11:46:23 ubuntu1 sshd[1655]: pam_unix(sshd:session): session
opened for user1 by (uid=0)

Nov 3 12:27:04 ubuntu1 sshd[1897]: refused connect from ....


Telnet:

Mac:~ R_$ telnet 192.168.0.101 22
Trying 192.168.0.101...
Connected to 192.168.0.101.
Escape character is '^]'.
SSH-2.0-OpenSSH_6.0p1 Debian-3ubuntu1

---

### Post by The Cog on 2012-11-03
Let's check that something is actually listening for those incoming connections. Can you post the result of this command on the server:
```
sudo netstat -lntp
```

---

### Post by Lars Noodén on 2012-11-03
> **233x said:**
> 
ssh seems to work without problems:


Why rcp?  If you have ssh, then you also have scp.  scp is designed around how rcp worked so if you have a script using rcp you should be able to use scp as a drop-in replacement.

---

### Post by 233x on 2012-11-04
@The Cog: 
I'm using Lubuntu as guest on VirtualHost, but copying data between guest and host doesn't work, although I have checked the "bidirectional" option. Then I tried to install the guest additions, but it also failed. I could install them neither from the menu, nor from the console  (sudo apt-get install virtualbox-guest-additions). That's why I had to attach an image showing the console output.

The browser within Lubuntu (the guest OS) doesn't work also, but when I ping google.com ping shows that the host is reachable.

---

### Post by The Cog on 2012-11-05
That picture shows that only cups (print server) and sshd server are listening. I don't see port 514 listening and I don't see rcpd or anything like it holding an open port. So your rcp server is not running.

The ssh connection should not be refused - sshd is listening for connections as properly. However, whether you can connect to it depends on how the networking is set up. If configured for NAT then you will not be able to connect to the Lubuntu from outside. Also, I have seen problems where the guest cannot connect to the host although it can connect to other machines on the network. 

If ssh is giveng connection refused, than I think you need to look for networking problems because the guest itself is listening properly.

---

### Post by 233x on 2012-11-05
Thanks. Lubuntu runs on VirtualBox with the "Bridged Adapter" option. I also followed those steps to enable r-services, but it didn't work:
[http://people.redhat.com/kzak/docs/rsh-rlogin-howto.html](http://people.redhat.com/kzak/docs/rsh-rlogin-howto.html)

Whenever i call the rcp command, I am getting an "Authentication failure", which normally indicates wrong values in .rhosts, hosts.deny or hosts.allow, but maybe there are still other places to look.

My local network has these addresses:
192.168.0.1    - router
192.168.0.100 - host
192.168.0.101 - Lubuntu guest 


I have added some more screenshots that show my settings in detail.

---

### Post by spjackson on 2012-11-06
> **233x said:**
> 
Whenever i call the rcp command, I am getting an "Authentication failure", which normally indicates wrong values in .rhosts, hosts.deny or hosts.allow, but maybe there are still other places to look.

Well that's definite progress. When you get "Authentication failure" does anything get logged in /var/log on the target machine?

---

### Post by 233x on 2012-11-06
Yes, it does. However, the error message changed from "Authentication failure" to "Permission denied", which sounds more concrete than the first one.

Here are the last lines from /var/log/auth.log:
[COLOR=Blue]Nov  6 11:48:46 ubuntu1 rshd[1752]: pam_rhosts(rsh:auth): denied access to [EMAIL="user@iMac.local"]user@iMac.local[/EMAIL] as user1
Nov  6 11:48:46 ubuntu1 rshd[1752]: rsh denied to [EMAIL="user@iMac.local"]user@iMac.local[/EMAIL] as user1: Permission denied.[/COLOR]

"iMac" is the host computer on which Lubuntu ("ubuntu1") runs in VirtualBox as a guest. "iMac" has address 192.168.0.100, "ubuntu1" has address 192.168.0.101.

I want to achieve this:
The small LAN has a central folder on ubuntu1 to which any user on any machine can copy files. 
The  "Permission denied" error indicates that maybe some entries in the  .rhosts, hosts, hosts.allow, hosts.deny or hosts.equiv or the privileges  of the folder to which the file is written are not correct. Did I  forget something here?

Here are the contents of those files:

r.hosts:
++

hosts.deny: empty

hosts.allow:
ALL: ALL

hosts:
127.0.0.1    localhost
127.0.1.1    ubuntu1
192.168.0.100   iMac
# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

hosts.equiv:
192.168.0.100

The folder on the destination machine, to which the file is written, is located at var/tmp/incoming. This directory has been set to 777 for simplicity.

Update: rcp is now working, but rsh doesn't work and I get the error message "select: protocol failure in circuit setup". The reason might be the firewall blocking the connection attempt. Are there any more possible reasons for that? I am using xinetd and followed those instructions: [http://people.redhat.com/kzak/docs/rsh-rlogin-howto.html](http://people.redhat.com/kzak/docs/rsh-rlogin-howto.html)

---

