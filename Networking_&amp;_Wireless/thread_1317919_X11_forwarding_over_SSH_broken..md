---
title: "X11 forwarding over SSH broken."
date: 2009-11-07
forum: Networking &amp; Wireless
---

### Post by Defrector on 2009-11-07
My X11-over-SSH broke and after hours of tinkering I haven't figured out why so I am asking for help. When ssh'ing with -XY, -X, or -Y enabled, $DISPLAY appears normal (see below), however applications trying to use X11 do not launch a window, and after a few minutes give up and say they cannot connect to the X11 server. Laptop can ssh into other machines and forward X11 fine.

The layout is:
> laptop => LAN => headless box

Both are running Ubuntu 9.10.

The SSH installed on the laptop and the headless is HPN SSH compiled and installed from [http://www.psc.edu/networking/projects/hpn-ssh/](http://www.psc.edu/networking/projects/hpn-ssh/) however it has worked properly for quite a while. I have been installing and removing a variety of software, particularly the virtualbox guest addons-x11. Removing these did not result in a change. The headless has been in a VM when the problem occurred. Problem persists when native. Smells like a config issue?

Info dump:
```
user@headless:~$ sudo apt-cache policy xauth
xauth:
  Installed: 1:1.0.3-2
  Candidate: 1:1.0.3-2
  Version table:
 *** 1:1.0.3-2 0
        500 http://us.archive.ubuntu.com karmic/main Packages
        100 /var/lib/dpkg/status
```

```
$ uname -a
Linux headless 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:05:01 UTC 2009 x86_64 GNU/Linux
```

```
user@user-laptop:~$ ssh user@headless -p 6699 -XY
user@headless's password:
Last login: Sat Nov  7 05:23:33 2009 from user-laptop
Linux headless 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:05:01 UTC 2009 x86_64

To access official Ubuntu documentation, please visit:
http://help.ubuntu.com/

user@headless:~$ xterm
[no response, no window launches]
^C
user@headless:~$ echo $DISPLAY
headless:10.0
```

...when sshd_config's X11UseLocalhost is set to 'yes', xterm returns a $DISPLAY not set and $DISPLAY is indeed not set.

:popcorn:

```
user@headless:~$ cat /usr/local/etc/sshd_config  
#       $OpenBSD: sshd_config,v 1.80 2008/07/02 02:24:18 djm Exp $

# This is the sshd server system-wide configuration file.  See
# sshd_config(5) for more information.                        

# This sshd was compiled with PATH=/usr/bin:/bin:/usr/sbin:/sbin:/usr/local/bin                                                             

# The strategy used for options in the default sshd_config shipped with                                                                     
# OpenSSH is to specify options with their default value where        
# possible, but leave them commented.  Uncommented options change a   
# default value.                                                      

Port 6699
#AddressFamily any
#ListenAddress 0.0.0.0
#ListenAddress ::     

# Disable legacy (protocol version 1) support in the server for new
# installations. In future the default will change to require explicit
# activation of protocol 1                                            
Protocol 2                                                            

# HostKey for protocol version 1
#HostKey /usr/local/etc/ssh_host_key
# HostKeys for protocol version 2   
#HostKey /usr/local/etc/ssh_host_rsa_key
#HostKey /usr/local/etc/ssh_host_dsa_key

# Lifetime and size of ephemeral version 1 server key
#KeyRegenerationInterval 1h                          
#ServerKeyBits 1024                                  

# Logging
# obsoletes QuietMode and FascistLogging
#SyslogFacility AUTH                    
#LogLevel INFO                          

# Authentication:

#LoginGraceTime 2m
#PermitRootLogin yes
#StrictModes yes    
#MaxAuthTries 6     
#MaxSessions 10     

#RSAAuthentication yes
#PubkeyAuthentication yes
#AuthorizedKeysFile     .ssh/authorized_keys

# For this to work you will also need host keys in /usr/local/etc/ssh_known_hosts                                                           
#RhostsRSAAuthentication no                                           
# similar for protocol version 2                                      
#HostbasedAuthentication no                                           
# Change to yes if you don't trust ~/.ssh/known_hosts for             
# RhostsRSAAuthentication and HostbasedAuthentication                 
#IgnoreUserKnownHosts no                                              
# Don't read the user's ~/.rhosts and ~/.shosts files                 
#IgnoreRhosts yes                                                     

# To disable tunneled clear text passwords, change to no here!
#PasswordAuthentication yes                                   
#PermitEmptyPasswords no                                      

# Change to no to disable s/key passwords
#ChallengeResponseAuthentication yes     

# Kerberos options
#KerberosAuthentication no
#KerberosOrLocalPasswd yes
#KerberosTicketCleanup yes
#KerberosGetAFSToken no   

# GSSAPI options
#GSSAPIAuthentication no
#GSSAPICleanupCredentials yes

# Set this to 'yes' to enable PAM authentication, account processing, 
# and session processing. If this is enabled, PAM authentication will 
# be allowed through the ChallengeResponseAuthentication and          
# PasswordAuthentication.  Depending on your PAM configuration,       
# PAM authentication via ChallengeResponseAuthentication may bypass   
# the setting of "PermitRootLogin without-password".                  
# If you just want the PAM account and session checks to run without  
# PAM authentication, then enable this but set PasswordAuthentication 
# and ChallengeResponseAuthentication to 'no'.                        
#UsePAM no                                                            

#AllowAgentForwarding yes
#AllowTcpForwarding yes  
#GatewayPorts no         
X11Forwarding yes        
#X11DisplayOffset 10     
X11UseLocalhost no       
#PrintMotd yes           
#PrintLastLog yes        
#TCPKeepAlive yes        
#UseLogin no
#UsePrivilegeSeparation yes
#PermitUserEnvironment no
#Compression delayed
#ClientAliveInterval 0
#ClientAliveCountMax 3
#UseDNS yes
#PidFile /var/run/sshd.pid
#MaxStartups 10
#PermitTunnel no
#ChrootDirectory none

# no default banner path
#Banner none

# override default of no subsystems
Subsystem       sftp    /usr/local/libexec/sftp-server

# the following are HPN related configuration options
# tcp receive buffer polling. disable in non autotuning kernels
#TcpRcvBufPoll yes

# allow the use of the none cipher
#NoneEnabled no

# disable hpn performance boosts.
#HPNDisabled no

# buffer size for hpn to non-hpn connections
#HPNBufferSize 2048

# Example of overriding settings on a per-user basis
#Match User anoncvs
#       X11Forwarding no
#       AllowTcpForwarding no
#       ForceCommand cvs server

AllowTcpForwarding yes
```

```
user@user-laptop:~$ ssh user@headless -p 6699 -XY -vvv
OpenSSH_5.2p1-hpn13v6, OpenSSL 0.9.8g 19 Oct 2007               
debug1: Reading configuration data /usr/local/etc/ssh_config    
debug2: ssh_connect: needpriv 0                                 
debug1: Connecting to headless [192.168.1.208] port 6699.      
debug1: Connection established.                                 
debug1: identity file /home/user/.ssh/identity type -1       
debug1: identity file /home/user/.ssh/id_rsa type -1         
debug1: identity file /home/user/.ssh/id_dsa type -1         
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.2p1-hpn13v6                                                          
debug1: match: OpenSSH_5.2p1-hpn13v6 pat OpenSSH*                     
debug1: Enabling compatibility mode for protocol 2.0                  
debug1: Local version string SSH-2.0-OpenSSH_5.2p1-hpn13v6            
debug2: fd 3 setting O_NONBLOCK                                       
debug1: SSH2_MSG_KEXINIT sent                                         
debug1: SSH2_MSG_KEXINIT received                                     
debug1: AUTH STATE IS 0                                               
debug2: kex_parse_kexinit: diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1                                                         
debug2: kex_parse_kexinit: ssh-rsa,ssh-dss                            
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se                          
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se                          
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
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se                          
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se                          
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96        
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96        
debug2: kex_parse_kexinit: none,zlib@openssh.com                      
debug2: kex_parse_kexinit: none,zlib@openssh.com                      
debug2: kex_parse_kexinit:                                            
debug2: kex_parse_kexinit:                                            
debug2: kex_parse_kexinit: first_kex_follows 0                        
debug2: kex_parse_kexinit: reserved 0                                 
debug2: mac_setup: found hmac-md5                                     
debug1: REQUESTED ENC.NAME is 'aes128-ctr'                            
debug1: kex: server->client aes128-ctr hmac-md5 none                  
debug2: mac_setup: found hmac-md5                                     
debug1: REQUESTED ENC.NAME is 'aes128-ctr'                            
debug1: kex: client->server aes128-ctr hmac-md5 none                  
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent              
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP                           
debug2: dh_gen_key: priv key bits set: 127/256                        
debug2: bits set: 514/1024                                            
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent                                 
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY                           
debug3: put_host_port: [192.168.1.208]:6699                           
debug3: put_host_port: [headless]:6699                               
debug3: check_host_in_hostfile: filename /home/user/.ssh/known_hosts                                                                     
debug3: check_host_in_hostfile: match line 1                          
debug3: check_host_in_hostfile: filename /home/user/.ssh/known_hosts                                                                     
debug3: check_host_in_hostfile: match line 1                          
debug1: Host '[headless]:6699' is known and matches the RSA host key.
debug1: Found key in /home/user/.ssh/known_hosts:1                 
debug2: bits set: 476/1024                                            
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
debug2: key: /home/user/.ssh/identity ((nil))                      
debug2: key: /home/user/.ssh/id_rsa ((nil))                        
debug2: key: /home/user/.ssh/id_dsa ((nil))                        
debug1: Authentications that can continue: publickey,password,keyboard-interactive                                                          
debug3: start over, passed a different list publickey,password,keyboard-interactive                                                         
debug3: preferred publickey,keyboard-interactive,password             
debug3: authmethod_lookup publickey                                   
debug3: remaining preferred: keyboard-interactive,password            
debug3: authmethod_is_enabled publickey                               
debug1: Next authentication method: publickey                         
debug1: Trying private key: /home/user/.ssh/identity               
debug3: no such identity: /home/user/.ssh/identity                 
debug1: Trying private key: /home/user/.ssh/id_rsa                 
debug3: no such identity: /home/user/.ssh/id_rsa                   
debug1: Trying private key: /home/user/.ssh/id_dsa                 
debug3: no such identity: /home/user/.ssh/id_dsa                   
debug2: we did not send a packet, disable method                      
debug3: authmethod_lookup keyboard-interactive                        
debug3: remaining preferred: password                                 
debug3: authmethod_is_enabled keyboard-interactive                    
debug1: Next authentication method: keyboard-interactive              
debug2: userauth_kbdint                                               
debug2: we sent a keyboard-interactive packet, wait for reply         
debug1: Authentications that can continue: publickey,password,keyboard-interactive                                                          
debug3: userauth_kbdint: disable: no info_req_seen                    
debug2: we did not send a packet, disable method                      
debug3: authmethod_lookup password                                    
debug3: remaining preferred:                                          
debug3: authmethod_is_enabled password                                
debug1: Next authentication method: password                          
user@headless's password:                                         
debug3: packet_send2: adding 64 (len 60 padlen 4 extra_pad 64)        
debug2: we sent a password packet, wait for reply                     
debug1: Authentication succeeded (password).
debug1: Final hpn_buffer_size = 131072
debug1: HPN Disabled: 0, HPN Buffer Size: 131072
debug1: channel 0: new [client-session]
debug1: Enabled Dynamic Window Scaling

debug3: ssh_session2_open: channel_new: 0
debug2: channel 0: send open
debug1: Requesting no-more-sessions@openssh.com
debug1: Entering interactive session.
debug2: callback start
debug2: x11_get_proto: /usr/bin/xauth  list :0 2>/dev/null
debug1: Requesting X11 forwarding with authentication spoofing.
debug2: channel 0: request x11-req confirm 0
debug2: client_session2_setup: id 0
debug2: channel 0: request pty-req confirm 1
debug2: channel 0: request shell confirm 1
debug2: fd 3 setting TCP_NODELAY
debug2: callback done
debug2: channel 0: open confirm rwindow 0 rmax 32768
debug2: tcpwinsz: 87380 for connection: 3
debug2: tcpwinsz: 87380 for connection: 3
debug2: channel_input_status_confirm: type 99 id 0
debug2: PTY allocation request accepted on channel 0
debug2: channel 0: rcvd adjust 87380
debug2: channel_input_status_confirm: type 99 id 0
debug2: shell request accepted on channel 0
debug2: tcpwinsz: 87380 for connection: 3
debug2: tcpwinsz: 87380 for connection: 3
Last login: Sat Nov  7 05:23:47 2009 from user-laptop
Linux headless 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:05:01 UTC 2009 x86_64

To access official Ubuntu documentation, please visit:
http://help.ubuntu.com/

debug2: tcpwinsz: 87380 for connection: 3
debug2: tcpwinsz: 87380 for connection: 3
user@headless:~$ debug2: tcpwinsz: 87380 for connection: 3
```

```
user@headless:~$ xauth list
user-laptop/unix:0  MIT-MAGIC-COOKIE-1  *CENSORED*
headless:10  MIT-MAGIC-COOKIE-1  *CENSORED*
```

Headless:
```
eth0      Link encap:Ethernet  HWaddr 00:24:1d:18:86:3e
          inet addr:192.168.1.208  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::224:1dff:fe18:863e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11215 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8638 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1630288 (1.6 MB)  TX bytes:954980 (954.9 KB)
          Interrupt:27 Base address:0xe000
```

The .ssh directories for both sides' accounts was cleared with no change other than invoking a reset of the fingerprints on login.

I attempted a reinstall of xauth on the headless machine with no improvement. Are there config files for xauth which I am not finding? Any ideas appreciated, thanx!
](*,)](*,)](*,)

---

### Post by Defrector on 2009-11-07
Any *legitimate* answers?:mad:

> **nick_back said:**
> snip

---

### Post by dox_drum on 2009-11-07
> **nick_back said:**
> snip

You shoul be kicked from the forum

---

### Post by Kokopelli on 2009-11-07
What is your X11 config on the headless machine and what (X11) packages do you have installed?

---

### Post by falconindy on 2009-11-07
```
#X11DisplayOffset 10
```
Uncomment that.

---

### Post by Defrector on 2009-11-07
Color this thread a deep dark shade of SOLVED.

The loopback device listed in ifconfig got snarled; SSH.X11 needs lo to work.

I suspect a latent/malfunctioning/partially-installed/zombified-from-the-dead-and-out-to-eat-my-brain hamachi VPN crashed(?) lo on bootup as there was a big recoverable segfault in the boot log where it tried to start.

Thanks for your replies.):P

---

