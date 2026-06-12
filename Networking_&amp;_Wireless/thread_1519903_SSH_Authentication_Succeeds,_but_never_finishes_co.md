---
title: "SSH Authentication Succeeds, but never finishes connecting"
date: 2010-06-28
forum: Networking &amp; Wireless
---

### Post by andey on 2010-06-28
> andey@andey-labtop:~$ ssh -v 192.168.202.102
OpenSSH_5.3p1 Debian-3ubuntu4, OpenSSL 0.9.8k 25 Mar 2009
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to 192.168.202.102 [192.168.202.102] port 22.
debug1: Connection established.
debug1: identity file /home/andey/.ssh/identity type -1
debug1: identity file /home/andey/.ssh/id_rsa type -1
debug1: identity file /home/andey/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.1p1 Debian-6ubuntu2
debug1: match: OpenSSH_5.1p1 Debian-6ubuntu2 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.3p1 Debian-3ubuntu4
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-ctr hmac-md5 none
debug1: kex: client->server aes128-ctr hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Host '192.168.202.102' is known and matches the RSA host key.
debug1: Found key in /home/andey/.ssh/known_hosts:1
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: publickey
debug1: Trying private key: /home/andey/.ssh/identity
debug1: Trying private key: /home/andey/.ssh/id_rsa
debug1: Trying private key: /home/andey/.ssh/id_dsa
debug1: Next authentication method: password
andey@192.168.202.102's password: 
debug1: Authentication succeeded (password).
debug1: channel 0: new [client-session]
debug1: Requesting [EMAIL="no-more-sessions@openssh.com"]no-more-sessions@openssh.com[/EMAIL]
debug1: Entering interactive session.
debug1: Sending environment.                                                                                                                                                        
debug1: Sending env LANG = en_US.UTF-8                                                                                                                                              
Write failed: Broken pipe  i can connect to other servers just not this one.
i reinstalled openssh-server all over again, and reconfigured it
i even tried running it on different port, 
the firewall is off, 
and i can FTP to it
any ideas?

---

### Post by andey on 2010-07-10
bump, no one has the slightest idea? :(

---

### Post by Joey The Saint on 2010-08-15
Lots of ideas, unfortunately none of them that seem to have worked out for me.  You can probably guess from that I'm seeing exactly the same thing.  It really doesn't seem to be related to SSH, though, I don't think.  I mean, SSH is really the most obvious situation where it happens, but I'm also observing behaviour in some of the other applications I'm running off the machine where I see the behaviour you describe that seems incorrect.  It almost seems like a general networking configuration problem to me.  I'd been looking at TCP settings at first but I can't find a tweakable that makes any significant impact.  If I find anything I'll be sure to come back around and let you know how I solved my problem.

Oh, and FWIW, it does seem like there are others with the same problems.  [http://ubuntuforums.org/showthread.php?t=1479184](http://ubuntuforums.org/showthread.php?t=1479184) for one.

---

### Post by jamonkko on 2011-10-07
I had exactly the same problem. Turned out that it was not ssh problem, but a wlan router one. 
ssh worked well from other locations, but not from certain wlan. It was also possible to access other servers with ssh from that wlan and also directly from the asdl modem (bypassing wlan router).

Then I changed the wlan router from Apple Airport Extreme (5th gen) to Asus and it started working. 

So there was some problem with combination of Airport Extreme and A-Link asdl modem. Weird thing is that one other Airport Extreme worked fine in other building. SSH was connecting fine. But that same unit did not work when used in the problematic building with A-Link asdl box. There was also a problem accessing https service hosted by the same virtual image that hosted the broken ssh connections. But with some other Airport Extreme the https worked and ssh did not work.

And all the time both that https and ssh worked just fine from other locations. And it was possible to access lot of other servers with ssh and https, not just that one virtual image. 

So, I bet that your problem is a hardware one. Try changing your wlan router. I blame the Airport :(

---

