---
title: "[SSH] Host key verification failed."
date: 2011-01-30
forum: Networking &amp; Wireless
---

### Post by dijxtra on 2011-01-30
I just installed openssh-server, and all tutorials say it should work out of the box. But it doesn't, it dies with "Host key verification failed."

Here is the log:

```
nick@rilmir:~$ ssh -vv localhost                                       
OpenSSH_5.1p1 Debian-5ubuntu1, OpenSSL 0.9.8g 19 Oct 2007              
debug1: Reading configuration data /etc/ssh/ssh_config                 
debug1: Applying options for *                                         
debug2: ssh_connect: needpriv 0                                        
debug1: Connecting to localhost [::1] port 22.                         
debug1: Connection established.                                        
debug1: identity file /home/nick/.ssh/identity type -1                 
debug2: key_type_from_name: unknown key type '-----BEGIN'              
debug2: key_type_from_name: unknown key type 'Proc-Type:'              
debug2: key_type_from_name: unknown key type 'DEK-Info:'               
debug2: key_type_from_name: unknown key type '-----END'                
debug1: identity file /home/nick/.ssh/id_rsa type 1                    
debug1: Checking blacklist file /usr/share/ssh/blacklist.RSA-2048      
debug1: Checking blacklist file /etc/ssh/blacklist.RSA-2048            
debug1: identity file /home/nick/.ssh/id_dsa type -1                   
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.1p1 Debian-5ubuntu1
debug1: match: OpenSSH_5.1p1 Debian-5ubuntu1 pat OpenSSH*                                 
debug1: Enabling compatibility mode for protocol 2.0                                      
debug1: Local version string SSH-2.0-OpenSSH_5.1p1 Debian-5ubuntu1                        
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
debug2: kex_parse_kexinit: diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1                                 
debug2: kex_parse_kexinit: ssh-rsa,ssh-dss                                                   
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr  
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr  
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96                                                      
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: none,zlib@openssh.com
debug2: kex_parse_kexinit: none,zlib@openssh.com
debug2: kex_parse_kexinit:
debug2: kex_parse_kexinit:
debug2: kex_parse_kexinit: first_kex_follows 0
debug2: kex_parse_kexinit: reserved 0
debug2: mac_setup: found hmac-md5
debug1: kex: server->client aes128-cbc hmac-md5 none
debug2: mac_setup: found hmac-md5
debug1: kex: client->server aes128-cbc hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug2: dh_gen_key: priv key bits set: 137/256
debug2: bits set: 501/1024
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug2: no key of type 0 for host localhost
debug2: no key of type 2 for host localhost
The authenticity of host 'localhost (::1)' can't be established.
RSA key fingerprint is a7:31:55:d2:c4:b2:f1:3e:27:5d:5b:d9:82:45:ea:00.
Are you sure you want to continue connecting (yes/no)?
Host key verification failed.
nick@rilmir:~$

```

Also:
```

nick@rilmir:/etc/ssh$ ls -l
total 152
-rw-r--r-- 1 root root 125749 2009-01-28 22:01 moduli
-rw-r--r-- 1 root root   1595 2009-01-28 22:01 ssh_config
-rw-r--r-- 1 root root   1874 2011-01-30 20:49 sshd_config
-rw------- 1 root root    668 2011-01-30 20:49 ssh_host_dsa_key
-rw-r--r-- 1 root root    601 2011-01-30 20:49 ssh_host_dsa_key.pub
-rw------- 1 root root   1675 2011-01-30 20:49 ssh_host_rsa_key
-rw-r--r-- 1 root root    393 2011-01-30 20:49 ssh_host_rsa_key.pub
nick@rilmir:/etc/ssh$

```

So, key are there. Any idea what went wrong?

---

### Post by CharlesA on 2011-01-30
Post the output of this:

```
ls -l ~/.ssh/
```

---

### Post by dijxtra on 2011-01-30
> **CharlesA said:**
> Post the output of this:

```
ls -l ~/.ssh/
```

```
nick@rilmir:~$ ls -l ~/.ssh/
total 12
-rw------- 1 nick nick 1751 2010-10-04 20:47 id_rsa
-rw-r--r-- 1 nick nick  399 2010-10-04 20:47 id_rsa.pub
-rw-r--r-- 1 nick nick 3584 2010-10-04 20:50 known_hosts
nick@rilmir:~$

```

---

### Post by CharlesA on 2011-01-30
Remove the offending hostkey from known_hosts:

```
ssh-keygen -R localhost
```
```
ssh-keygen -R ::1
```

---

### Post by dijxtra on 2011-01-30
Nope, didn't help...

```
nick@rilmir:~$ ssh-keygen -R localhost
/home/nick/.ssh/known_hosts updated.
Original contents retained as /home/nick/.ssh/known_hosts.old
nick@rilmir:~$ ssh-keygen -R ::1
/home/nick/.ssh/known_hosts updated.
Original contents retained as /home/nick/.ssh/known_hosts.old
nick@rilmir:~$ ssh localhost
The authenticity of host 'localhost (::1)' can't be established.
RSA key fingerprint is a7:31:55:d2:c4:b2:f1:3e:27:5d:5b:d9:82:45:ea:00.
Are you sure you want to continue connecting (yes/no)?
Host key verification failed.
nick@rilmir:~$
```

---

### Post by CharlesA on 2011-01-30
rename known_hosts and then try to connect.

---

### Post by dijxtra on 2011-01-30
> **CharlesA said:**
> rename known_hosts and then try to connect.

```
nick@rilmir:~$ cd .ssh/
nick@rilmir:~/.ssh$ mv known_hosts known_hosts.old
nick@rilmir:~/.ssh$ ssh localhost
The authenticity of host 'localhost (::1)' can't be established.
RSA key fingerprint is a7:31:55:d2:c4:b2:f1:3e:27:5d:5b:d9:82:45:ea:00.
Are you sure you want to continue connecting (yes/no)?
Host key verification failed.
nick@rilmir:~/.ssh$ ls -l
total 12
-rw------- 1 nick nick 1751 2010-10-04 20:47 id_rsa
-rw-r--r-- 1 nick nick  399 2010-10-04 20:47 id_rsa.pub
-rw------- 1 nick nick 3584 2011-01-30 22:51 known_hosts.old
nick@rilmir:~/.ssh$ mv known_hosts.old known_hosts
```

---

### Post by CharlesA on 2011-01-31
Hrm. Are you able to connect to the hostname instead of using 'localhost' ?

Could try purging and reinstalling openssh-server.

---

### Post by dijxtra on 2011-01-31
> **CharlesA said:**
> Hrm. Are you able to connect to the hostname instead of using 'localhost' ?
Nope.

```
nick@rilmir:~$ ssh rilmir
The authenticity of host 'rilmir (127.0.1.1)' can't be established.
RSA key fingerprint is a7:31:55:d2:c4:b2:f1:3e:27:5d:5b:d9:82:45:ea:00.
Are you sure you want to continue connecting (yes/no)?                 
Host key verification failed.                                          
nick@rilmir:~$ ssh 127.0.0.1                                           
The authenticity of host '127.0.0.1 (127.0.0.1)' can't be established. 
RSA key fingerprint is a7:31:55:d2:c4:b2:f1:3e:27:5d:5b:d9:82:45:ea:00.
Are you sure you want to continue connecting (yes/no)?                 
Host key verification failed.
```                                          

> **CharlesA said:**
> Run this:

```
ssh -vvv localhost
```

```
nick@rilmir:~$ ssh -vvv localhost                                      
OpenSSH_5.1p1 Debian-5ubuntu1, OpenSSL 0.9.8g 19 Oct 2007              
debug1: Reading configuration data /etc/ssh/ssh_config                 
debug1: Applying options for *                                         
debug2: ssh_connect: needpriv 0                                        
debug1: Connecting to localhost [::1] port 22.                         
debug1: Connection established.                                        
debug1: identity file /home/nick/.ssh/identity type -1                 
debug3: Not a RSA1 key file /home/nick/.ssh/id_rsa.                    
debug2: key_type_from_name: unknown key type '-----BEGIN'              
debug3: key_read: missing keytype                                      
debug2: key_type_from_name: unknown key type 'Proc-Type:'              
debug3: key_read: missing keytype                                      
debug2: key_type_from_name: unknown key type 'DEK-Info:'               
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
debug2: key_type_from_name: unknown key type '-----END'                
debug3: key_read: missing keytype                                      
debug1: identity file /home/nick/.ssh/id_rsa type 1                    
debug1: Checking blacklist file /usr/share/ssh/blacklist.RSA-2048      
debug1: Checking blacklist file /etc/ssh/blacklist.RSA-2048            
debug1: identity file /home/nick/.ssh/id_dsa type -1                   
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.1p1 Debian-5ubuntu1
debug1: match: OpenSSH_5.1p1 Debian-5ubuntu1 pat OpenSSH*                                 
debug1: Enabling compatibility mode for protocol 2.0                                      
debug1: Local version string SSH-2.0-OpenSSH_5.1p1 Debian-5ubuntu1                        
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
debug2: kex_parse_kexinit: diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1                                 
debug2: kex_parse_kexinit: ssh-rsa,ssh-dss                                                   
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr  
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr  
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96                                                      
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96                                                      
debug2: kex_parse_kexinit: none,zlib@openssh.com                                             
debug2: kex_parse_kexinit: none,zlib@openssh.com                                             
debug2: kex_parse_kexinit:                                                                   
debug2: kex_parse_kexinit:                                                                   
debug2: kex_parse_kexinit: first_kex_follows 0                                               
debug2: kex_parse_kexinit: reserved 0                                                        
debug2: mac_setup: found hmac-md5                                                            
debug1: kex: server->client aes128-cbc hmac-md5 none
debug2: mac_setup: found hmac-md5
debug1: kex: client->server aes128-cbc hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug2: dh_gen_key: priv key bits set: 130/256
debug2: bits set: 508/1024
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug3: check_host_in_hostfile: filename /home/nick/.ssh/known_hosts
debug3: check_host_in_hostfile: filename /etc/ssh/ssh_known_hosts
debug3: check_host_in_hostfile: filename /home/nick/.ssh/known_hosts
debug3: check_host_in_hostfile: filename /etc/ssh/ssh_known_hosts
debug2: no key of type 0 for host localhost
debug3: check_host_in_hostfile: filename /home/nick/.ssh/known_hosts2
debug3: check_host_in_hostfile: filename /etc/ssh/ssh_known_hosts2
debug3: check_host_in_hostfile: filename /home/nick/.ssh/known_hosts
debug3: check_host_in_hostfile: filename /etc/ssh/ssh_known_hosts
debug2: no key of type 2 for host localhost
The authenticity of host 'localhost (::1)' can't be established.
RSA key fingerprint is a7:31:55:d2:c4:b2:f1:3e:27:5d:5b:d9:82:45:ea:00.
Are you sure you want to continue connecting (yes/no)?
Host key verification failed.
nick@rilmir:~$

```

BTW, thanks a bunch for the effort. I just can't figure it out...

---

### Post by CharlesA on 2011-01-31
Try purging and reinstalling openssh-server, see how that goes.

---

### Post by dijxtra on 2011-01-31
> **CharlesA said:**
> Try purging and reinstalling openssh-server, see how that goes.
I went to synaptic, marked openssh-server for "complete removal" and then hit apply (sorry, I can't remember this intant how you do that in shell).

And then I did this:

```
nick@rilmir:~$ sudo apt-get install openssh-server
[sudo] password for nick:                         
Reading package lists... Done                     
Building dependency tree                          
Reading state information... Done                 
Suggested packages:                               
  rssh molly-guard                                
The following NEW packages will be installed:     
  openssh-server                                  
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/285kB of archives.                             
After this operation, 782kB of additional disk space will be used.
Preconfiguring packages ...                                       
Selecting previously deselected package openssh-server.           
(Reading database ... 190091 files and directories currently installed.)
Unpacking openssh-server (from .../openssh-server_1%3a5.1p1-5ubuntu1_i386.deb) ...
Processing triggers for ufw ...
Processing triggers for man-db ...
Setting up openssh-server (1:5.1p1-5ubuntu1) ...
Creating SSH2 RSA key; this may take some time ...
Creating SSH2 DSA key; this may take some time ...
 * Restarting OpenBSD Secure Shell server sshd                                        [ OK ]

nick@rilmir:~$ ssh localhost
The authenticity of host 'localhost (::1)' can't be established.
RSA key fingerprint is 06:f9:cc:02:6a:45:55:ae:79:f2:d2:ea:90:ec:8e:52.
Are you sure you want to continue connecting (yes/no)?
Host key verification failed.
nick@rilmir:~$ ssh rilmir
The authenticity of host 'rilmir (127.0.1.1)' can't be established.
RSA key fingerprint is 06:f9:cc:02:6a:45:55:ae:79:f2:d2:ea:90:ec:8e:52.
Are you sure you want to continue connecting (yes/no)?
Host key verification failed.
nick@rilmir:~$ ssh 127.0.0.1
The authenticity of host '127.0.0.1 (127.0.0.1)' can't be established.
RSA key fingerprint is 06:f9:cc:02:6a:45:55:ae:79:f2:d2:ea:90:ec:8e:52.
Are you sure you want to continue connecting (yes/no)?
Host key verification failed.
nick@rilmir:~$

```

This makes me really sad :-(((( I'm desperate now. My kingdom for a ssh deamon :-(

---

### Post by CharlesA on 2011-01-31
Try this:

```
sudo apt-get purge openssh-server
```
```
ls -l /etc/ssh
```

EDIT: See [here](http://www.unix.com/unix-dummies-questions-answers/145221-host-key-verification-failed-openssh.html). Not exactly the same problem, but maybe it'll give you a place to start.

---

### Post by dijxtra on 2011-02-01
> **CharlesA said:**
> Try this:

```
sudo apt-get purge openssh-server
```
```
ls -l /etc/ssh
```

```
nick@rilmir:~$ sudo apt-get purge openssh-server
[sudo] password for nick:                       
Reading package lists... Done                   
Building dependency tree                        
Reading state information... Done               
The following packages will be REMOVED:         
  openssh-server*                               
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 782kB disk space will be freed.         
Do you want to continue [Y/n]?                                
(Reading database ... 190105 files and directories currently installed.)
Removing openssh-server ...                                             
 * Stopping OpenBSD Secure Shell server sshd                                          [ OK ] 
Purging configuration files for openssh-server ...                                           
Processing triggers for man-db ...                                                           
Processing triggers for ufw ...                                                              
nick@rilmir:~$ ls -l /etc/ssh                                                                
total 132                                                                                    
-rw-r--r-- 1 root root 125749 2009-01-28 22:01 moduli                                        
-rw-r--r-- 1 root root   1595 2009-01-28 22:01 ssh_config                                    
nick@rilmir:~$ sudo apt-get install openssh-server
Reading package lists... Done                     
Building dependency tree                          
Reading state information... Done                 
Suggested packages:
  rssh molly-guard
The following NEW packages will be installed:
  openssh-server
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/285kB of archives.
After this operation, 782kB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package openssh-server.
(Reading database ... 190091 files and directories currently installed.)
Unpacking openssh-server (from .../openssh-server_1%3a5.1p1-5ubuntu1_i386.deb) ...
Processing triggers for ufw ...
Processing triggers for man-db ...
Setting up openssh-server (1:5.1p1-5ubuntu1) ...
Creating SSH2 RSA key; this may take some time ...
Creating SSH2 DSA key; this may take some time ...
 * Restarting OpenBSD Secure Shell server sshd                                        [ OK ]

nick@rilmir:~$ ssh localhost
The authenticity of host 'localhost (::1)' can't be established.
RSA key fingerprint is 45:0c:c4:58:bc:ee:b7:f3:d4:2e:16:0e:92:2b:0f:31.
Are you sure you want to continue connecting (yes/no)?
Host key verification failed.
nick@rilmir:~$
```

> **CharlesA said:**
> EDIT: See [here](http://www.unix.com/unix-dummies-questions-answers/145221-host-key-verification-failed-openssh.html). Not exactly the same problem, but maybe it'll give you a place to start.

This seems highly unlikely since I'm trying to ssh form the same machine, but I'll look into it.

---

### Post by CharlesA on 2011-02-01
Are you able to ssh from another machine?

You could try creating a new user and seeing if you can ssh in as that user.

---

### Post by dijxtra on 2011-02-10
> **CharlesA said:**
> Are you able to ssh from another machine?
Nope, I'm not.
> **CharlesA said:**
> You could try creating a new user and seeing if you can ssh in as that user.
I have another user on my machine. I tried ssh localhost as that user, with same results...

---

### Post by CharlesA on 2011-02-10
Is it giving you the same error from the other machine?

If that's the case, then something is definitely messed up with sshd.

---

### Post by dijxtra on 2011-02-11
> **CharlesA said:**
> Is it giving you the same error from the other machine?
Yup, the same error.
> **CharlesA said:**
> If that's the case, then something is definitely messed up with sshd.
So, what do I do? :-D

---

### Post by MihailK on 2011-02-11
Hi!
Might sound dumb, but try typing 'yes' on this line:

```

Are you sure you want to continue connecting (yes/no)? yes
 
```

I think the default is 'no'.
This is my output:

```

ssh oracle@192.168.16.12
The authenticity of host '192.168.16.12 (192.168.16.12)' can't be established.
RSA key fingerprint is f9:db:70:1a:3a:67:1a:cc:0a:5a:89:f2:48:47:ec:0a.
Are you sure you want to continue connecting (yes/no)? **[COLOR=Red]yes[/COLOR]**
Warning: Permanently added '192.168.16.12' (RSA) to the list of known hosts.

oracle@192.168.16.12's password: 
Last login: Fri Feb  4 10:50:47 2011 from class07

```

Good luck! :)

---

### Post by CharlesA on 2011-02-11
Wow.. I had totally missed that. Thought the OP was putting 'yes' to the message.

---

### Post by carsonrose on 2011-02-11
have  you tried deleting the /home/<username>/.ssh/known_hosts file?

I know there will be 100 people jump on me for telling you to try that, but I get this problem alot when I change IP addresses or networks... same thing really.

See if you can delete the file and let the ssh recreate it.........

:popcorn:

---

### Post by CharlesA on 2011-02-11
> **carsonrose said:**
> have  you tried deleting the /home/<username>/.ssh/known_hosts file?

I know there will be 100 people jump on me for telling you to try that, but I get this problem alot when I change IP addresses or networks... same thing really.

See if you can delete the file and let the ssh recreate it.........

:popcorn:
Did that earlier. ;)

---

### Post by dijxtra on 2011-02-14
> **MihailK said:**
> Hi!
Might sound dumb, but try typing 'yes' on this line:

```

Are you sure you want to continue connecting (yes/no)? yes
 
```
I gave up on ever again using SSH on my machine, then I sshed to my work machine and typed "yes" on that question and said to myself: "wait a minute, I didn't type "yes" when trying to connecto to localhost, now did I?"

So I came here to say that everything works now that I've started typing "yes", and what do I see? :-D

Anyway, everybody, especially CharlesA, thank you for trying, and also thank you for finding a solution. Although it is a "dumb" solution and although I also found it myself, it gives me great hope in human race that people like CharlesA are prepared to stick to another persons problem until it is fixed. Thanky you! :-)

---

### Post by andoni on 2011-12-27
> **carsonrose said:**
> have  you tried deleting the /home/<username>/.ssh/known_hosts file?

I know there will be 100 people jump on me for telling you to try that, but I get this problem alot when I change IP addresses or networks... same thing really.

See if you can delete the file and let the ssh recreate it.........

:popcorn:
Sorry for bumping an old thread, but that worked! Thanks a lot :) .

---

