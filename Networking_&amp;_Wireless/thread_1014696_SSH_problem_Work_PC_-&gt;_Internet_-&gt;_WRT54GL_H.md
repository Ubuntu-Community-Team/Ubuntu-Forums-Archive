---
title: "SSH problem: Work PC -&gt; Internet -&gt; WRT54GL Home Router -&gt;Ubuntu 8.10 laptop"
date: 2008-12-18
forum: Networking &amp; Wireless
---

### Post by gegtot on 2008-12-18
Hi all!

I want to access my Ubuntu laptop from my work pc through my WRT54GL home router.

The router is setup to forward port 22 requests to the ubuntu laptop.

Within the home LAN behind the router all works fine, but accessing from work does not work.

Judging by the symptom, the connection request works, but the connection as such is refused. 

Can anyone give me a pointer on what to do next?

**How to reproduce**
1. Open Putty on the work pc
2. Start an ssh session pointing to the IP of the home router on port 22.
3. Click "yes" in the Putty Security Alert dialogue (see screen shot)
4. Supply the user name at the login prompt and hit enter.

**Expected result**
**>** The password prompt should appear.

**Actual result**
**>** A dialogue "Putty fatal error appears", saying "Server unexpectedly closed network connection".

---

### Post by jnorthr on 2008-12-18
first thoughts:
this may be a permissions issue more than a network issue
you may need to look into your /var/log/syslog on your ubuntu machine to see if there are any messages about the time you try to log on. If a connection has reached your ubuntu box i would expect at least some success or failure message to be logged there.

your router may have a log feature as well that might show attempts to gain access. if it does not show up there, it may not be reaching your router as you think.

sorry i'm just guessing on all this ;)

---

### Post by Pvt_Ryan on 2008-12-18
Have you remembered to forward port 22 from your router to your laptop?

---

### Post by The Cog on 2008-12-18
It may be that your company firewall isn't allowing SSH out to the internet. Do you know of anywhere else you can try to connect from, to try and prove that your home end works?

---

### Post by gegtot on 2008-12-19
Hi guys,

Sorry for the late reply. I got hold up by another problem. See [http://ubuntuforums.org/showthread.php?t=1015959](http://ubuntuforums.org/showthread.php?t=1015959).

**Pvt_Ryan:** Yes, I have forwarded port 22 correctly.

**jnorthr:** no log entries are made, neither in the router nor in /var/log/syslog 

**The Cog:** 

**ssh localhost** from the localhost to  works fine. 
**ssh routerIP** from the localhost does not work. No firewall at work involved here.

(localhost = ubuntu laptop)

However, when I do **ssh routerIP** from my ubuntu laptop just after doing **rm /home/userX/.ssh/known_hosts** I get the following:
```

@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that the RSA host key has just been changed.
The fingerprint for the RSA key sent by the remote host is
5e:a2:8a:6c:c4:a8:57:52:2c:7c:bd:80:2f:26:3a:b0.
Please contact your system administrator.
Add correct host key in /home/userX/.ssh/known_hosts to get rid of this message.
Offending key in /home/userX/.ssh/known_hosts:1
RSA host key for routerIP has changed and you have requested strict checking.
Host key verification failed.
```

When I do **ssh routerIP** again I get a shorter version: ```
Connection closed by routerIP
```

This may also be of interest. When I generate a key and then try to log in, the following happens:

```
UserX@viao:~$ ssh-keygen
Generating public/private rsa key pair.
Enter file in which to save the key (/home/UserX/.ssh/id_rsa): test
Enter passphrase (empty for no passphrase): 
Enter same passphrase again: 
Your identification has been saved in test.
Your public key has been saved in test.pub.
The key fingerprint is:
c2:a4:43:80:b2:be:cd:09:35:f0:35:59:4a:69:4b:25 UserX@viao
The key's randomart image is:
+--[ RSA 2048]----+
| ..  E=o         |
|o. ..Bo          |
|..o =.+          |
|.  = =           |
|. . + o S        |
| o   . .         |
|  = .            |
| . +             |
|                 |
+-----------------+
UserX@viao:~$ ssh  RouterIP
The authenticity of host 'RouterIP (RouterIP)' can't be established.
RSA key fingerprint is df:e4:02:7e:7f:8a:c0:70:06:77:45:da:e9:65:93:f2.
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added 'RouterIP' (RSA) to the list of known hosts.
Connection closed by RouterIP
```

---

### Post by Yardarm on 2008-12-19
When you run 'ssh routerIP', are you using the NAT translated internal address, such as 192.168.0.1, or your ISP provided IP address?  It almost seems like you're trying to login to the router itself.

---

### Post by gegtot on 2008-12-19
The RouterIP is the ISP provided IP address, the IP address that I would use to create the connection from work like this:
**WorkIP -> RouterIP -> LaptopIP**        
Where the router forwards the ssh connection to my laptop.

---

