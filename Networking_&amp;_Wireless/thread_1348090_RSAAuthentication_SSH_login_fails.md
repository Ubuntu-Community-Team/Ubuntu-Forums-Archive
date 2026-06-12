---
title: "RSAAuthentication SSH login fails"
date: 2009-12-06
forum: Networking &amp; Wireless
---

### Post by Bystroi on 2009-12-06
I got a Ubuntu 9.04 Desktop and would need to be able to open ssh connections to it from various computers without user interaction.
However, this particular box refuses rsa authentication attempts from anywhere, including itself (localhost.)
I have successfully set up number of passwordless ssh connections between number of other computers using Ubuntu and never had to do any tweaking.

In both client and server I first run:
```
ssh-keygen -b 4096 -t rsa
```Then in client:
```
ssh-copy-id <user>@<server>
ssh <user>@<server>
```and get
```
<user>@<server>'s password:
```... prompt. Usually at this point you do not have to use password anymore.

Even if I do
```
ssh-copy-id localhost
ssh localhost

```I still get the password prompt with this server?!!

The permissions for /home/<user> are 0755, /home/<user>/.ssh/ are 0700 and all files inside 0600.
Just to be sure, I tried setting StrictModes off in /usr/ssh/sshd_config but that didn't have any effect.

/usr/ssh/sshd_config is like this```

# Package generated configuration file
# See the sshd(8) manpage for details

# What ports, IPs and protocols we listen for
Port 22
# Use these options to restrict which interfaces/protocols sshd will bind to
#ListenAddress ::
#ListenAddress 0.0.0.0
Protocol 2
# HostKeys for protocol version 2
HostKey /etc/ssh/ssh_host_rsa_key
HostKey /etc/ssh/ssh_host_dsa_key
#Privilege Separation is turned on for security
UsePrivilegeSeparation yes

# Lifetime and size of ephemeral version 1 server key
KeyRegenerationInterval 3600
ServerKeyBits 768

# Logging
SyslogFacility AUTH
LogLevel INFO

# Authentication:
LoginGraceTime 120
PermitRootLogin yes
StrictModes yes

RSAAuthentication yes
PubkeyAuthentication yes
AuthorizedKeysFile    %h/.ssh/authorized_keys

# Don't read the user's ~/.rhosts and ~/.shosts files
IgnoreRhosts yes
# For this to work you will also need host keys in /etc/ssh_known_hosts
RhostsRSAAuthentication no
# similar for protocol version 2
HostbasedAuthentication no
# Uncomment if you don't trust ~/.ssh/known_hosts for RhostsRSAAuthentication
#IgnoreUserKnownHosts yes

# To enable empty passwords, change to yes (NOT RECOMMENDED)
PermitEmptyPasswords no

# Change to yes to enable challenge-response passwords (beware issues with
# some PAM modules and threads)
ChallengeResponseAuthentication no

# Change to no to disable tunnelled clear text passwords
#PasswordAuthentication yes

# Kerberos options
#KerberosAuthentication no
#KerberosGetAFSToken no
#KerberosOrLocalPasswd yes
#KerberosTicketCleanup yes

# GSSAPI options
#GSSAPIAuthentication no
#GSSAPICleanupCredentials yes

X11Forwarding yes
X11DisplayOffset 10
PrintMotd no
PrintLastLog yes
TCPKeepAlive yes
#UseLogin no

#MaxStartups 10:30:60
#Banner /etc/issue.net

# Allow client to pass locale environment variables
AcceptEnv LANG LC_*

Subsystem sftp /usr/lib/openssh/sftp-server
UsePAM yes

```The .ssh at the problem server looks otherwise ok with authorized_keys, id_rsa and id_rsa.pub.
md5sum shows client's id_rsa.pub and server's authorized_keys are identical files.
Even if you
```
cp id_rsa.pub authorized_keys
```at the server it will still ask you password when doing
```
ssh localhost
```I destroyed and recreated the keys, and rebooted both client and server several times. I also updated both for latest packages.

Ssh outputs some strange messages though...

```
OpenSSH_5.1p1 Debian-3ubuntu1, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to localhost [127.0.0.1] port 22.
debug1: Connection established.
debug1: identity file /home/<user>/.ssh/identity type -1
debug3: Not a RSA1 key file /home/<user>/.ssh/id_rsa.
debug2: key_type_from_name: unknown key type '-----BEGIN'
debug3: key_read: missing keytype
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug2: key_type_from_name: unknown key type '-----END'
debug3: key_read: missing keytype
debug1: identity file /home/<user>/.ssh/id_rsa type 1
debug1: Checking blacklist file /usr/share/ssh/blacklist.RSA-4096
debug1: Checking blacklist file /etc/ssh/blacklist.RSA-4096
debug1: identity file /home/<user>/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version lshd-2.0.4 lsh - a GNU ssh
debug1: no match: lshd-2.0.4 lsh - a GNU ssh
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.1p1 Debian-3ubuntu1
debug2: fd 3 setting O_NONBLOCK
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug2: kex_parse_kexinit: diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ssh-rsa,ssh-dss
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib
debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: first_kex_follows 0 
debug2: kex_parse_kexinit: reserved 0 
debug2: kex_parse_kexinit: diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ssh-rsa,spki-sign-rsa
debug2: kex_parse_kexinit: aes256-cbc,3des-cbc,blowfish-cbc,arcfour
debug2: kex_parse_kexinit: aes256-cbc,3des-cbc,blowfish-cbc,arcfour
debug2: kex_parse_kexinit: hmac-sha1,hmac-md5
debug2: kex_parse_kexinit: hmac-sha1,hmac-md5
debug2: kex_parse_kexinit: none,zlib
debug2: kex_parse_kexinit: none,zlib
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: first_kex_follows 0 
debug2: kex_parse_kexinit: reserved 0 
debug2: mac_setup: found hmac-md5
debug1: kex: server->client 3des-cbc hmac-md5 none
debug2: mac_setup: found hmac-md5
debug1: kex: client->server 3des-cbc hmac-md5 none
debug2: dh_gen_key: priv key bits set: 196/384
debug2: bits set: 1030/2048
debug1: sending SSH2_MSG_KEXDH_INIT
debug1: expecting SSH2_MSG_KEXDH_REPLY
debug3: check_host_in_hostfile: filename /home/<user>/.ssh/known_hosts
debug3: check_host_in_hostfile: match line 1
debug1: Host 'localhost' is known and matches the RSA host key.
debug1: Found key in /home/<user>/.ssh/known_hosts:1
debug2: bits set: 1026/2048
debug1: ssh_rsa_verify: signature correct
debug2: kex_derive_keys
debug2: set_newkeys: mode 1
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug2: set_newkeys: mode 0
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug2: service_accept: ssh-userauth
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug2: key: /home/<user>/.ssh/identity ((nil))
debug2: key: /home/<user>/.ssh/id_rsa (0xb97d49d8)
debug2: key: /home/<user>/.ssh/id_dsa ((nil))
debug1: Authentications that can continue: password,publickey
debug3: start over, passed a different list password,publickey
debug3: preferred gssapi-keyex,gssapi-with-mic,gssapi,publickey,keyboard-interactive,password
debug3: authmethod_lookup publickey
debug3: remaining preferred: keyboard-interactive,password
debug3: authmethod_is_enabled publickey
debug1: Next authentication method: publickey
debug1: Trying private key: /home/<user>/.ssh/identity
debug3: no such identity: /home/<user>/.ssh/identity
debug1: Offering public key: /home/<user>/.ssh/id_rsa
debug3: send_pubkey_test
debug2: we sent a publickey packet, wait for reply
debug1: Authentications that can continue: password,publickey
debug1: Trying private key: /home/<user>/.ssh/id_dsa
debug3: no such identity: /home/<user>/.ssh/id_dsa
debug2: we did not send a packet, disable method
debug3: authmethod_lookup password
debug3: remaining preferred: ,password
debug3: authmethod_is_enabled password
debug1: Next authentication method: password
```I'm out of things to try. Please, any thoughts?

---

### Post by Bystroi on 2009-12-07
I found this [http://ubuntuforums.org/showthread.php?t=1214231](http://ubuntuforums.org/showthread.php?t=1214231) which I haven't tried out.

So I created a new directory /etc/.ssh/<user>/ and copied the authorized_keys over to that directory.

Then I set the permissions so that /etc/ and /etc/.ssh are root:root and 0755 and /etc/.ssh/<user>/ is <user>:<user> 0700.

Finally I changed /etc/ssh/sshd_config so that
```

...
StrictModes no
...
AuthorizedKeysFile    /etc/.ssh/%u/authorized_keys
...
```I rebooted (just to be sure) and...   it does not work. Still asking persistently for the damn password. ](*,)

What is going on here?!!

---

### Post by Bystroi on 2009-12-07
And one more odd thing I just noticed. There are not any entries related to ssh login/logout events in syslog or auth.log or in any other log in that directory. 
If I tail -f those and login - nothing shows up.

---

### Post by Muttley99 on 2009-12-08
I'm having the exact same problem! I've just had some good debug after 

ssh -vvv ipaddressofserver 

Looks like the key is in the wrong format - will get back and let you know!


My problem seems to be an encrypted /home directory!!

---

### Post by Bystroi on 2009-12-11
> **Muttley99 said:**
> I'm having the exact same problem! I've just had some good debug after 

ssh -vvv ipaddressofserver 

Looks like the key is in the wrong format - will get back and let you know!


My problem seems to be an encrypted /home directory!!

Did you manage to fix it with [http://ubuntuforums.org/showthread.php?t=1214231](http://ubuntuforums.org/showthread.php?t=1214231) ?

So the error messages with the key are not significant? I'm still stuck with this.

---

### Post by Muttley99 on 2009-12-11
Do you have an encrypted /home directory? if so, this is very likely your problem. I there is a quick and easy solution without making a new /home directory.
I have posted on the Ubuntu server forum the solution; The solution was found by someone else, I followed the instructions below and it has solved the problem 

[HTML]Here is an exact cut-and-paste. I left out a few details in the last
one, as it was merely pseudo code.

 $ /sbin/umount.ecryptfs_private
 $ cd $HOME
 $ chmod 700 .
 $ mkdir -m 700 .ssh
 $ chmod 500 .
 $ echo $YOUR_REAL_PUBLIC_KEY > .ssh/authorized_keys
 $ /sbin/mount.ecryptfs_private

Note that you should not have *any* other programs running between
those umount and mount commands, as all of your home directory will be
unreadable by those programs. If you're on a graphical desktop, log
out of all sessions and either ssh in, or login on the tty terminal.

I just tested the above commands and they work perfectly.

:-Dustin[/HTML]

BTW. I've spent many hour trying to solve this over the last week and tried a whole list of stuff so if it doesn't solve your problem let me know here and I may be able to help with some things you may not have tried!

---

### Post by Bystroi on 2009-12-14
Unfortunately /sbin/umount.ecryptfs_private does not exist.

I do not think that the problem is in home dir encryption as I have already moved the authorized_keys to it's own dir at /etc/.ssh/<user>/ , set permissions and changed the AuthorizedKeysFile at sshd_config accordingly.

---

### Post by jobix on 2009-12-14
Can you try this? 
Put "sshd: ALL" into your /etc/hosts.allow file and restart the sshd process.

---

### Post by Bystroi on 2009-12-14
I finally solved it. It was very stupid mistake in the end: The lsh-server was running and blocking openssh from starting up.

So I removed lsh-server from init.d, deleted the /etc/ssh/ssh_not_to_be_run and rebooted and it finally works. :P

---

