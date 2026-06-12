---
title: "SSH: Permission denied (publickey,password)"
date: 2011-10-14
forum: Networking &amp; Wireless
---

### Post by DevinJCan on 2011-10-14
Hello and thanks for checking out my thread.

I am having an issue authenticating a remote host via SSH to which I am connected via cross-over cable. The remote host I am attempting to access is in my apartment and is running Ubuntu 10.04 Lucid. I have ran the sudo apt-get install ssh and can ping the PC. Also, I am running Ubuntu 11.04 on my main PC.

I need to check into the implications of public key authentication vs straight pass-phrase authentication. I am not going to be connecting over a wan and I may want to in the future.

so, what do I do to control the PC from the other end of my apartment?



/etc/ssh/ssh_config
> 
# This is the ssh client system-wide configuration file.  See
# ssh_config(5) for more information.  This file provides defaults for
# users, and the values can be changed in per-user configuration files
# or on the command line.

# Configuration data is parsed as follows:
#  1. command line options
#  2. user-specific file
#  3. system-wide file
# Any configuration value is only changed the first time it is set.
# Thus, host-specific definitions should be at the beginning of the
# configuration file, and defaults at the end.

# Site-wide defaults for some commonly used options.  For a comprehensive
# list of available options, their meanings and defaults, please see the
# ssh_config(5) man page.

Host *
#   ForwardAgent no
#   ForwardX11 no
#   ForwardX11Trusted yes
#   RhostsRSAAuthentication no
#   RSAAuthentication yes
#   PasswordAuthentication yes
#   HostbasedAuthentication no
#   GSSAPIAuthentication no
#   GSSAPIDelegateCredentials no
#   GSSAPIKeyExchange no
#   GSSAPITrustDNS no
#   BatchMode no
#   CheckHostIP yes
#   AddressFamily any
#   ConnectTimeout 0
#   StrictHostKeyChecking ask
#   IdentityFile ~/.ssh/identity
#   IdentityFile ~/.ssh/id_rsa
#   IdentityFile ~/.ssh/id_dsa
#   Port 22
#   Protocol 2,1
#   Cipher 3des
#   Ciphers aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc
#   MACs hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160
#   EscapeChar ~
#   Tunnel no
#   TunnelDevice any:any
#   PermitLocalCommand no
#   VisualHostKey no
#   ProxyCommand ssh -q -W %h:%p gateway.example.com
    SendEnv LANG LC_*
    HashKnownHosts yes
    GSSAPIAuthentication yes
    GSSAPIDelegateCredentials no

Any ideas/solutions will be greatly appreciated. I am a full time student studying IT-Sec. I am a newbie and looking for guidance. Thank you.

---

### Post by gdonwallace on 2011-10-14
I have never tried to use SSH on two machines that are physically connected to each other.  I guess the first question would be is SSH installed and running on both machines.  

I know that there is a way to have SSH generate the key to use for the connection, I am at work right now and don't have access to that information.  Google ssh, there is a location that has a lot of really good information available on how to setup and use SSH.

Hope that helps.

---

### Post by smurphy_it on 2011-10-14
First you need to verify that SSH daemon is waiting for connections.  You can do that from the machine itself, or you can simply use telnet if you wish.

On physical machine:
```
netstat -ant |grep LISTEN
```

From remote machine:
```
telnet HOSTNAME 22
```

Pass-phrase vs. Key authentication.  If the machine is to be "accessible" from the internet, you'll want to use key'd authentication with a passphrase.  Password only would be subject to brute force password attacks.

To generate the ssh key(s), you can use rsa or dsa.

```
ssh-keygen -t rsa
```
or
```
ssh-keygen -t dsa
```

---

### Post by collisionystm on 2011-10-14
you can use public key if you do not want to put in a password everytime.

On your server 

```
sudo apt-get install ssh
```

On your personal computer

```
ssh-keygen
```

Enter through all the prompts... no password.

```
cd /home/username/.ssh
```

```
vi id_rsa.pub
```

Copy all the text in here

type ```
:q!
``` to exit

ssh to your server

```
cd .ssh
```

```
nano authorized_keys
```

paste contents

CTRL+X then Y to save

exit out of the ssh

ssh to your server again... should not ask for password anymore.

---

### Post by DevinJCan on 2011-10-14
Ah, Thank you collisionystm. That was what I was looking to do!

---

### Post by collisionystm on 2011-10-14
> **DevinJCan said:**
> Ah, Thank you collisionystm. That was what I was looking to do!

No problem.. done it a million times. Glad to help.

---

