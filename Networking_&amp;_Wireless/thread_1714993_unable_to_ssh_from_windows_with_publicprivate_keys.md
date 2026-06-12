---
title: "unable to ssh from windows with public/private keys"
date: 2011-03-26
forum: Networking &amp; Wireless
---

### Post by speedy18us on 2011-03-26
i'm using ubuntu server 10.10 and i have an ssh connection active on port 22. i connect from my laptop client with username and password, which is insecure. i've been using ubuntu server for about 3 years now, but i was unable (like ever) to create a private/public key connection to my server.
i followed so many tutorials, i don't remember. none of them are working. the last ones were: [http://www.wowtutorial.org/tutorial/22.html](http://www.wowtutorial.org/tutorial/22.html) and [http://linux-sxs.org/networking/openssh.putty.html](http://linux-sxs.org/networking/openssh.putty.html)
every time i'm trying to connect to ssh with putty, it says: 'putty server refused our key'.

today i've tried [http://linux-sxs.org/networking/openssh.putty.html](http://linux-sxs.org/networking/openssh.putty.html) made the following steps:
- generated keys with **sudo ssh-keygen -t rsa** and saved them to my ~/.ssh/ directory
- copied id_rsa.pub like this: **sudo cp id_rsa.pub authorized_keys**
- edited sshd_config:  **sudo nano /etc/ssh/sshd_config**
- the config is:
```
Port 22
Protocol 2
HostKey /etc/ssh/ssh_host_rsa_key
HostKey /etc/ssh/ssh_host_dsa_key
UsePrivilegeSeparation yes
KeyRegenerationInterval 3600
ServerKeyBits 768
SyslogFacility AUTH
LogLevel INFO
LoginGraceTime 120
PermitRootLogin no
StrictModes yes
RSAAuthentication yes
PubkeyAuthentication yes
AuthorizedKeysFile    ~/.ssh/authorized_keys
IgnoreRhosts yes
RhostsRSAAuthentication no
HostbasedAuthentication no
IgnoreUserKnownHosts yes
PermitEmptyPasswords no
ChallengeResponseAuthentication no
PasswordAuthentication yes
X11Forwarding yes
X11DisplayOffset 10
PrintMotd no
PrintLastLog yes
TCPKeepAlive yes
Banner /etc/issue.net
AcceptEnv LANG LC_*
Subsystem sftp /usr/lib/openssh/sftp-server
UsePAM yes
```- restarted ssh: **sudo /etc/init.d/ssh restart** or **sudo service ssh restart**
- copied ~/.ssh/id_rsa from Linux to Windows
- downloaded [http://tartarus.org/~simon/putty-snapshots/x86/puttygen.exe]("http://tartarus.org/%7Esimon/putty-snapshots/x86/puttygen.exe") (because it didn't worked at first [http://www.phwinfo.com/forum/comp-security-ssh/441246-interesting-changes-openssh-5-4p1-affected-putty.html](http://www.phwinfo.com/forum/comp-security-ssh/441246-interesting-changes-openssh-5-4p1-affected-putty.html))
- loaded id_rsa and converted to id_rsa.ppk
- started putty with the new key and received the error

what am i doing wrong ???

---

### Post by speedy18us on 2011-11-24
As unbelievable it may sounds, I was unable to connect to my linux box with public/private keys from my windows client for 3 years. I was having about 5 attempts. I switched to Debian and made almost the same steps and it's working like a charm. I was following this tutorial [http://www.ualberta.ca/CNS/RESEARCH/LinuxClusters/pka-putty.html](http://www.ualberta.ca/CNS/RESEARCH/LinuxClusters/pka-putty.html) and actually i'm surprised.

---

