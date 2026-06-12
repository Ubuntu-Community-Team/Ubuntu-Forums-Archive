---
title: "Tunnel device open failed"
date: 2010-01-18
forum: Networking &amp; Wireless
---

### Post by CDFM on 2010-01-18
I run Ubuntu 9.10 locally connecting to CentOS5 on a remote server.

When I run the following command in the Terminal;

ssh -v -L 10005:localhost:10000 root@remote_ip_address -F ~/.ssh_config -i ~/.ssh/private_key_file_name

after 'Authentication succeeded (publickey)' I get the following for channel 1;

sys_tun_open: failed to open tunnel control interface: Permission denied

however, it does open an interactive client-session on channel 2 and my browser will then connect (via URL localhost:10005) to Webmin on the remote server which is the object of the exercise.

However, because sys_tun_open failed, I am concerned that the transactions may not be encrypted as I understand they would be in proper tunnelling - I am very new to this :) so all information is welcome.

---

### Post by Lars Noodén on 2010-01-18
( Try not to log in as root if you can possibly avoid it.  If there is a special task you need, there are ways to set up sudo to handle it.  )

Check your server configuration to make sure that tunneling is allowed.  /etc/ssh/sshd_config should have **AllowTcpForwarding *yes*** either for the whole server or just for the **Match** directive that affects the group of the user logging in.

---

### Post by CDFM on 2010-01-18
Uncommenting 'AllowTcpForwarding  yes' and restarting ssh did the trick, thank you very much.

Also I am running;
sudo ssh -v -L 10005:localhost:10000 root@remote_ip_address -F ~/.ssh_config -i ~/.ssh/private_key_file_name
 
Was that what you meant?

One small glitch - exit no longer breaks the connection.
Now I have to log out of my localhost to break it.
Should I be typing something else instead of exit?

---

### Post by Lars Noodén on 2010-01-18
> **CDFM said:**
> Uncommenting 'AllowTcpForwarding  yes' and restarting ssh did the trick, thank you very much.

Also I am running;
sudo ssh -v -L 10005:localhost:10000 **root**@remote_ip_address -F ~/.ssh_config -i ~/.ssh/private_key_file_name
 
Was that what you meant?

One small glitch - exit no longer breaks the connection.
Now I have to log out of my localhost to break it.
Should I be typing something else instead of exit?


I've marked in bold the part to try to fix.  Ideally you want to log in as a regular user, then use sudo to run whatever script or program.  Sudo can be adjusted to allow just one specific action with one specific set of arguments.  That minimizes the risk if the key or the account are compromised.  

As to why exit does not work, that's something else.  What shell is running on the remote account.  What's special in ~/.ssh_config for the host "remote_ip_address" ?

---

### Post by CDFM on 2010-01-19
OK Lars, I think I has better go and learn about sudo before continuing that part of this post.

What shell is running on the remote account? Bash, as far as I'm aware - I can't see any sign of anything else.

The ssh_config file that I use on my Ubuntu localhost is as follows;
Host *
#   ForwardAgent no
#   ForwardX11 no
   ForwardX11Trusted yes
   RhostsRSAAuthentication yes
   RSAAuthentication yes
#   PasswordAuthentication yes
#   HostbasedAuthentication no
   GSSAPIAuthentication no
#   GSSAPIDelegateCredentials no
#   GSSAPIKeyExchange no
#   GSSAPITrustDNS no
#   BatchMode no
#   CheckHostIP yes
#   AddressFamily any
#   ConnectTimeout 0
   StrictHostKeyChecking ask
#   IdentityFile ~/.ssh/identity
#   IdentityFile ~/.ssh/id_rsa
#   IdentityFile ~/.ssh/id_dsa
   Port 9022
   Protocol 2,1
#   Cipher 3des
#   Ciphers aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour,aes192-cbc,aes256-cbc
#   MACs hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160
#   EscapeChar ~
   Tunnel yes
   TunnelDevice any:any
#   PermitLocalCommand no
    SendEnv LANG LC_*
    HashKnownHosts yes
    GSSAPIAuthentication yes
    GSSAPIDelegateCredentials no

As to what might be special, I'm afraid I don't know enough to be sure

---

