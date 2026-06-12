---
title: "SSH key authentication issues"
date: 2011-01-08
forum: Networking &amp; Wireless
---

### Post by chak2005 on 2011-01-08
Good afternoon everyone,

Find myself in a bit of a bind, I am trying to set up a remote SSH server on my ubuntu server running at a remote location.  Should be easy, but *[I]Murphy's law*[/I] loves me which is why I've finally caved and am now asking for help. 

**Background**

I want to SSH from my windows client to my ubuntu server using key authentication. I have set up Openssh on my ubuntu server and configured it, I have putty on my windows client. I am able to log into my ubuntu machine over SSH with a username/password however key authentication fails with Putty spitting out a **"Server refused our key"** (hold on now before you hit the reply button!)

At first I generated the keys on my windows client using puttygen and then moved my public key over to my ubuntu machine with WinSCP reformatted the key so it matched up with OpenSSH's standards and plopped the sucker in my ~/.ssh/authorized_keys file.

When that didn't work I tried visa versa, and generated the keys on my ubuntu server, and pulled over the private key to my windows client and loaded it up through puttygen, puttygen correctly reformatted the key, tried again and still nothing. Public key again was put in its appropriate place.

I also caught on to the fact that this ubuntu server's home folder was encrypted at install and SSH's PKI authentication doesnt take to kindly to that. So for the third try, I moved my authorized_key file over to my /etc/ folder and changed the sshd_config file accordingly. My thinking was I should be able to log in just not have my home folder mounted. Well still no luck even after moving my file I received the same error in putty and prompted me for a username/password.

The last thing I could think of was double checking permissions, my authorized_keys folder was set to -rw------- 1 root root. Maybe its default directory needs updating? Or some other permission tweaks? Can any SSH experts offer any advice? I am not sure what else to do. =/ below is my sshd_config file and auth.log in case there maybe something missing in there or something I overlooked. I am not sure if the fault is with the keys/putty/OpenSSH/ or ecryptfs...

```

Port 7777
ListenAddress 0.0.0.0
Protocol 2
HostKey /etc/ssh/ssh_host_rsa_key
HostKey /etc/ssh/ssh_host_dsa_key
UsePrivilegeSeparation yes


KeyRegenerationInterval 3600
ServerKeyBits 768

SyslogFacility AUTH
LogLevel VERBOSE

# Authentication:
LoginGraceTime 120
PermitRootLogin no
StrictModes no
AllowUsers User1

RSAAuthentication yes
PubkeyAuthentication yes
#AuthorizedKeysFile     /etc/authorized_keys

# Don't read the user's ~/.rhosts and ~/.shosts files
IgnoreRhosts yes
# For this to work you will also need host keys in /etc/ssh_known_hosts
RhostsRSAAuthentication no
# similar for protocol version 2
HostbasedAuthentication no

PermitEmptyPasswords no
ChallengeResponseAuthentication no

PasswordAuthentication yes (can't make this no until my keys work =/)

X11Forwarding no
X11DisplayOffset 10
PrintMotd no
PrintLastLog yes
TCPKeepAlive no
ClientAliveInterval 60
ClientAliveCountMax 3
#UseLogin no
MaxAuthTries 2
```Also here is the result from my auth.logs

```

Jan  8 13:46:35 sshd[3182]: Connection from XX.XXX.XXX.XXX port XXXX
Jan  8 13:46:40 sshd[3182]: Failed none for user from XX.XXX.XXX.XXX port XXXX ssh2
Jan  8 13:46:40 sshd[3182]: Failed publickey for user from XX.XXX.XXX.XXX port XXXX ssh2
Jan  8 13:46:45 sshd[3182]: pam_sm_authenticate: Called
Jan  8 13:46:45 sshd[3182]: pam_sm_authenticate: username = [My login creds]
Jan  8 13:46:45 sshd[3184]: Passphrase file wrapped
Jan  8 13:46:48 sshd[3184]: Error attempting to add filename encryption key to user session keyring; rc = [1]
Jan  8 13:46:48 sshd[3182]: Accepted password for user from XX.XXX.XXX.XXX port XXXX ssh2
Jan  8 13:46:48 sshd[3182]: pam_unix(sshd:session): session opened for user by (uid=0)
```

---

### Post by chak2005 on 2011-01-08
Figured I'd post and let everyone know, the issue was with my home folder. I simply decrypted the home folder permanently and everything is now working. 

Cheers.:popcorn:

---

### Post by kevdog on 2011-01-08
What was it encrypted with??

---

### Post by chak2005 on 2011-01-09
ecryptfs. I did the whole encrypt home folder upon server install. Mistake with my SSH server.:(

---

### Post by rancor on 2011-01-11
I don't agree that it was a wrong to encrypt the file system, you just have the authorized_keys on the encrypted file system that was the problem since it can't be decrypted until you have authenticated and the login with ssh tries to access the file before you have been authenticated. 

**This is how to fix the problem**

Move authorized_keys to /etc/ssh-public-keys/<username>/

Edit /etc/ssh/sshd_config and change AuthorizedKeysFile to

> AuthorizedKeysFile      /etc/ssh-public-keys/%u/authorized_keys

Restart sshd

sudo service ssh restart

// rancor

---

### Post by giljorak on 2011-01-15
> **rancor said:**
> I don't agree that it was a wrong to encrypt the file system, you just have the authorized_keys on the encrypted file system that was the problem since it can't be decrypted until you have authenticated and the login with ssh tries to access the file before you have been authenticated. 

**This is how to fix the problem**

Move authorized_keys to /etc/ssh-public-keys/<username>/

Edit /etc/ssh/sshd_config and change AuthorizedKeysFile to



Restart sshd

sudo service ssh restart

// rancor

Thank you!!!
 I just started using authentication keys and ran into this issue when logging in to my main account. All the other accounts were working just fine.

---

