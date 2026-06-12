---
title: "Can connect via SSH over LAN, but not WAN"
date: 2009-06-04
forum: Networking &amp; Wireless
---

### Post by sauerpauer on 2009-06-04
Hello all!  Let me begin by saying just how great of a resource these forums have been for me.  Nearly every issue I've come across in my short (+/- 1 year) time using Linux has had an informative solution posted somewhere on these forums.  It's great!

I am having trouble connecting two boxes via SSH.  I can connect just fine over LAN, but I am running into problems when I try to connect from outside of my network.  

The box I am trying to connect to is a relatively vanilla Xubuntu installation with (as far as I can tell) a correctly configured ssh server (sshd), a fresh installation of firestarter (only one rule - the port that sshd is listening to is opened), and the box can both browse the internet and connect to other boxes on the LAN just fine.

As far as the WAN goes, I have a properly-updating hostname pointing to my dynamic IP (using dyndns), and my router is forwarding that same port to the internal IP address of the box.

I thought that was all that I needed to open SSH connections over the WAN, but I'm either missing something or I might just have something improperly configured.  As a starting point, when I try to open a ssh connection over the wan, here is the verbose output:
```
chris@mybox:~$ ssh -vvv -p 220 chris@myhostname.dyndns.com
OpenSSH_5.1p1 Debian-5ubuntu1, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to myhostname.dyndns.com [-snip-] port 220.
debug1: connect to address -snip- port 220: Connection refused
ssh: connect to host myhostname.dyndns.com port 220: Connection refused
```Any help you folks can offer will be greatly appreciated!

---

### Post by dmizer on 2009-06-04
Please post your /etc/ssh/sshd_conf file.

Also, it may help to refer to this document: [https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)
and
[https://help.ubuntu.com/community/SSH](https://help.ubuntu.com/community/SSH)

---

### Post by sauerpauer on 2009-06-04
Thanks for the quick response!  Oh, I am running 9.04.  Are there any ports I shouldn't use for the server?  The documentation you cited actually helped me set most of this stuff up! :D

Edit:  Actually, if anybody is familiar with it, I'd like to keep this as secure as possible.  Once I get it working, that's what I'll be focused on.  Is there anything else I can add to the config file to make it more secure?

Edit2:  Just to make sure I'm using the right syntax, I'm using ```
ssh -p (port number) chris@myhostname.dyndns.com
```
"chris" is the user name on both the host and client box, "myhostname.dyndns.com" is the DNS host for my WAN IP address, and "server" will be the server's hostname.

Ex (this is what actually works on the LAN): ```
ssh -p 220 chris@server
```

sshd_config: 
```
# for consistency and privacy... I'm actually using a different port
Port 226
Protocol 2
# ** I need to figure out how to use keys; I'd like to use keys exclusively for the
# security aspect once I get it working just using a password
HostKey /etc/ssh/ssh_host_rsa_key
HostKey /etc/ssh/ssh_host_dsa_key
UsePrivilegeSeparation yes
KeyRegenerationInterval 3600
ServerKeyBits 768

SyslogFacility AUTH
LogLevel INFO
LoginGraceTime 20
PermitRootLogin no
StrictModes yes

RSAAuthentication yes
PubkeyAuthentication yes
#AuthorizedKeysFile    %h/.ssh/authorized_keys

# Don't read the user's ~/.rhosts and ~/.shosts files
IgnoreRhosts yes
# For this to work you will also need host keys in /etc/ssh_known_hosts
RhostsRSAAuthentication no
# similar for protocol version 2
HostbasedAuthentication no
# Uncomment if you don't trust ~/.ssh/known_hosts for RhostsRSAAuthentication
#IgnoreUserKnownHosts yes

PermitEmptyPasswords no

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

X11Forwarding no
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

```

---

### Post by dmizer on 2009-06-05
Many of the ports below 1024 are reserved for specific applications. For example, port 220 is used for IMAP. While it's not specifically a problem to use port 220, it could cause problems later on if you decide to add a service which needs the port you're using for ssh. I generally use large, but memorable numbers like 32768 (memory addresses) for my ssh ports.

Double check your port numbers and port forwarding to make sure you have the correct numbers entered.

The only other thing I can think of is a possible local firewall like UFW or IPtables. Please post the output of:
```
sudo iptables -L
```

PS. If you have RSA or DSA keys set up and working for your server, I suggest disabling both pam and PasswordAuthentication. If you do not have RSA or DSA keys set up, then I wouldn't advise opening your SSH server to the WAN, as all that keeps your machine from getting owned is a password.

---

### Post by sauerpauer on 2009-06-05
So, I actually posted the sshd_config of my client machine :oops:.  Here's the actual sshd_config:
```
Port 220
Protocol 2
HostKey /etc/ssh/ssh_host_rsa_key
HostKey /etc/ssh/ssh_host_dsa_key
UsePrivilegeSeparation yes
KeyRegenerationInterval 3600
ServerKeyBits 768
SyslogFacility AUTH
LogLevel INFO
LoginGraceTime 20
PermitRootLogin no
StrictModes yes

RSAAuthentication yes
PubkeyAuthentication yes
ChallengeResponseAuthentication no
X11Forwarding no

```iptables -L gives:
```
Chain INPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5 
DROP       all  --  anywhere             255.255.255.255     
DROP       all  --  anywhere             192.168.0.255       
DROP       all  --  BASE-ADDRESS.MCAST.NET/8  anywhere            
DROP       all  --  anywhere             BASE-ADDRESS.MCAST.NET/8 
DROP       all  --  255.255.255.255      anywhere            
DROP       all  --  anywhere             0.0.0.0             
DROP       all  --  anywhere             anywhere            state INVALID 
LSI        all  -f  anywhere             anywhere            limit: avg 10/min burst 5 
INBOUND    all  --  anywhere             anywhere            
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Input' 

Chain FORWARD (policy DROP)
target     prot opt source               destination         
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5 
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Forward' 

Chain OUTPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
DROP       all  --  BASE-ADDRESS.MCAST.NET/8  anywhere            
DROP       all  --  anywhere             BASE-ADDRESS.MCAST.NET/8 
DROP       all  --  255.255.255.255      anywhere            
DROP       all  --  anywhere             0.0.0.0             
DROP       all  --  anywhere             anywhere            state INVALID 
OUTBOUND   all  --  anywhere             anywhere            
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Output' 

Chain INBOUND (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:229 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:229 
LSI        all  --  anywhere             anywhere       
Chain LOG_FILTER (5 references)
target     prot opt source               destination         

Chain LSI (2 references)
target     prot opt source               destination         
LOG_FILTER  all  --  anywhere             anywhere            
LOG        tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN 
LOG        tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST 
LOG        icmp --  anywhere             anywhere            icmp echo-request limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
DROP       icmp --  anywhere             anywhere            icmp echo-request 
LOG        all  --  anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Inbound ' 
DROP       all  --  anywhere             anywhere            

Chain LSO (0 references)
target     prot opt source               destination         
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Outbound ' 
REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable 

Chain OUTBOUND (1 references)
target     prot opt source               destination         
ACCEPT     icmp --  anywhere             anywhere            
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     all  --  anywhere             anywhere    
        chris@psubuntu:~$ Chain INPUT (policy DROP)
bash: syntax error near unexpected token `('
chris@psubuntu:~$ target     prot opt source               destination         
bash: target: command not found
chris@psubuntu:~$ ACCEPT     all  --  anywhere             anywhere            
bash: ACCEPT: command not found
chris@psubuntu:~$ ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5 
bash: ACCEPT: command not found
chris@psubuntu:~$ DROP       all  --  anywhere             255.255.255.255     
bash: DROP: command not found
chris@psubuntu:~$ DROP       all  --  anywhere             192.168.0.255       
bash: DROP: command not found
chris@psubuntu:~$ DROP       all  --  BASE-ADDRESS.MCAST.NET/8  anywhere            
bash: DROP: command not found
chris@psubuntu:~$ DROP       all  --  anywhere             BASE-ADDRESS.MCAST.NET/8 
bash: DROP: command not found
chris@psubuntu:~$ DROP       all  --  255.255.255.255      anywhere            
bash: DROP: command not found
chris@psubuntu:~$ DROP       all  --  anywhere             0.0.0.0             
bash: DROP: command not found
chris@psubuntu:~$ DROP       all  --  anywhere             anywhere            state INVALID 
bash: DROP: command not found
chris@psubuntu:~$ LSI        all  -f  anywhere             anywhere            limit: avg 10/min burst 5 
bash: LSI: command not found
chris@psubuntu:~$ INBOUND    all  --  anywhere             anywhere            
bash: INBOUND: command not found
chris@psubuntu:~$ LOG_FILTER  all  --  anywhere             anywhere            bash: LOG_FILTER: command not found
chris@psubuntu:~$ LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Input' 
> 
> Chain FORWARD (policy DROP)
> target     prot opt source               destination         
> ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5 
> LOG_FILTER  all  --  anywhere             anywhere            
> LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Forward' 
> 
> Chain OUTPUT (policy DROP)
> target     prot opt source               destination         
> ACCEPT     all  --  anywhere             anywhere            
> DROP       all  --  BASE-ADDRESS.MCAST.NET/8  anywhere            
> DROP       all  --  anywhere             BASE-ADDRESS.MCAST.NET/8 
> DROP       all  --  255.255.255.255      anywhere            
> DROP       all  --  anywhere             0.0.0.0             
> DROP       all  --  anywhere             anywhere            state INVALID 
> OUTBOUND   all  --  anywhere             anywhere            
> LOG_FILTER  all  --  anywhere             anywhere            
> LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Output' 
bash: command substitution: line 1: unexpected EOF while looking for matching `''
bash: command substitution: line 8: syntax error: unexpected end of file
bash: LOG: command not found
chris@psubuntu:~$ 
chris@psubuntu:~$ Chain INBOUND (1 references)
bash: syntax error near unexpected token `('
chris@psubuntu:~$ target     prot opt source               destination         
bash: target: command not found
chris@psubuntu:~$ ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
bash: ACCEPT: command not found
chris@psubuntu:~$ ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
bash: ACCEPT: command not found
chris@psubuntu:~$ ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:229 
bash: ACCEPT: command not found
chris@psubuntu:~$ ACCEPT     udp  --  anywhere             anywhere            udp dpt:229 
bash: ACCEPT: command not found
chris@psubuntu:~$ LSI        all  --  anywhere             anywhere       Chain LOG_FILTER (5 references)
bash: syntax error near unexpected token `('
chris@psubuntu:~$ target     prot opt source               destination         
Chain LOG_FILTER (5 references)
target     prot opt source               destination         

Chain LSI (2 references)
target     prot opt source               destination         
LOG_FILTER  all  --  anywhere             anywhere            
LOG        tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN 
LOG        tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST 
LOG        icmp --  anywhere             anywhere            icmp echo-request limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
DROP       icmp --  anywhere             anywhere            icmp echo-request 
LOG        all  --  anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Inbound ' 
DROP       all  --  anywhere             anywhere            

Chain LSO (0 references)
target     prot opt source               destination         
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Outbound ' 
REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable 

Chain OUTBOUND (1 references)
target     prot opt source               destination         
ACCEPT     icmp --  anywhere             anywhere            
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     all  --  anywhere             anywhere            bash: target: command not found
chris@psubuntu:~$ 
chris@psubuntu:~$ Chain LSI (2 references)
bash: syntax error near unexpected token `('
chris@psubuntu:~$ target     prot opt source               destination         
bash: target: command not found
chris@psubuntu:~$ LOG_FILTER  all  --  anywhere             anywhere            bash: LOG_FILTER: command not found
chris@psubuntu:~$ LOG        tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
> DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN 
> LOG        tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
> DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST 
> LOG        icmp --  anywhere             anywhere            icmp echo-request limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
bash: command substitution: line 1: unexpected EOF while looking for matching `''
bash: command substitution: line 4: syntax error: unexpected end of file
bash: LOG: command not found
chris@psubuntu:~$ DROP       icmp --  anywhere             anywhere            icmp echo-request 
bash: DROP: command not found
chris@psubuntu:~$ LOG        all  --  anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Inbound ' 
> DROP       all  --  anywhere             anywhere            
> 
> Chain LSO (0 references)
> target     prot opt source               destination         
> LOG_FILTER  all  --  anywhere             anywhere            
> LOG        all  --  anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Outbound ' 
> REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable 
> 
> Chain OUTBOUND (1 references)
> target     prot opt source               destination         
> ACCEPT     icmp --  anywhere             anywhere            
> ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
> ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
> ACCEPT     all  --  anywhere             anywhere            Chain LOG_FILTER (5 references)
> target     prot opt source               destination         
> 
> Chain LSI (2 references)
> target     prot opt source               destination         
> LOG_FILTER  all  --  anywhere             anywhere            
> LOG        tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
bash: command substitution: line 1: unexpected EOF while looking for matching `''
bash: command substitution: line 8: syntax error: unexpected end of file
bash: LOG: command not found
chris@psubuntu:~$ DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN 
bash: DROP: command not found
chris@psubuntu:~$ LOG        tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
> DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST 
> LOG        icmp --  anywhere             anywhere            icmp echo-request limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
> DROP       icmp --  anywhere             anywhere            icmp echo-request 
> LOG        all  --  anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Inbound ' 
bash: command substitution: line 1: unexpected EOF while looking for matching `''
bash: command substitution: line 4: syntax error: unexpected end of file
bash: LOG: command not found
chris@psubuntu:~$ DROP       all  --  anywhere             anywhere            
bash: DROP: command not found
chris@psubuntu:~$ 
chris@psubuntu:~$ Chain LSO (0 references)
bash: syntax error near unexpected token `('
chris@psubuntu:~$ target     prot opt source               destination         
bash: target: command not found
chris@psubuntu:~$ LOG_FILTER  all  --  anywhere             anywhere            bash: LOG_FILTER: command not found
chris@psubuntu:~$ LOG        all  --  anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Outbound ' 
> REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable 
> 
> Chain OUTBOUND (1 references)
> target     prot opt source               destination         
> ACCEPT     icmp --  anywhere             anywhere            
> ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
> ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
> ACCEPT     all  --  anywhere             anywhere            



```hmm... is this the right output?  Seems pretty excessive...
I haven't looked through the entire output though, maybe I messed it up somehow?

Thanks for the security advice though!

---

### Post by dmizer on 2009-06-05
Well, that could be causing problems. Is there something in particular you need a firewall for (internet connection sharing for example). Did you install firestarter (if so, uninstall it). Otherwise, you can disable it with this command:
```
sudo ufw disable
```
Double check your iptables rules after you've done that. They should look like this:
```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
```

PS. To copy and paste from terminal, just highlight the text (no need to click), and middle click to the area you'd like to paste into.

---

### Post by sauerpauer on 2009-06-05
The ssh server is accepting connections over the WAN now, for whatever reason.  I'd still like to know why I had problems earlier though.  I think I had some port forwarding on my gateway messed up... I'll look into it when I get a chance.

Why is firestarter a problem?  It seems like the only problem I've seen people have with it is that it doesn't actually disable the firewall when you tell it to.  I would like to learn how to configure iptables manually, but since the ssh server is occasionally on public wifi, I needed to make sure I had everything set up correctly.  I won't mind uninstalling it if I can find some good resources to learn how to manually configure iptables.

I won't disable the firewall on my server now that I have it up and running, but it looks like your post had an example of an iptables config with no firewall.  What should iptables look like when the firewall is up and properly configured?

I'm looking into why my iptables seemed so messed up (I had to copy and paste several times because it kept listing more information, even though some of it looked like duplicates), I'll post here if i get some more discernable results.  Thanks for all your help!  I really appreciate it!

Edit:
iptables -L on the server machine now gives this, without the duplication/hanging problems I had earlier:
```
Chain INPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5 
DROP       all  --  anywhere             255.255.255.255     
DROP       all  --  anywhere             192.168.0.255       
DROP       all  --  BASE-ADDRESS.MCAST.NET/8  anywhere            
DROP       all  --  anywhere             BASE-ADDRESS.MCAST.NET/8 
DROP       all  --  255.255.255.255      anywhere            
DROP       all  --  anywhere             0.0.0.0             
DROP       all  --  anywhere             anywhere            state INVALID 
LSI        all  -f  anywhere             anywhere            limit: avg 10/min burst 5 
INBOUND    all  --  anywhere             anywhere            
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Input' 

Chain FORWARD (policy DROP)
target     prot opt source               destination         
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5 
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Forward' 

Chain OUTPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
DROP       all  --  BASE-ADDRESS.MCAST.NET/8  anywhere            
DROP       all  --  anywhere             BASE-ADDRESS.MCAST.NET/8 
DROP       all  --  255.255.255.255      anywhere            
DROP       all  --  anywhere             0.0.0.0             
DROP       all  --  anywhere             anywhere            state INVALID 
OUTBOUND   all  --  anywhere             anywhere            
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Output' 

Chain INBOUND (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:229 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:229 
LSI        all  --  anywhere             anywhere            

Chain LOG_FILTER (5 references)
target     prot opt source               destination         

Chain LSI (2 references)
target     prot opt source               destination         
LOG_FILTER  all  --  anywhere             anywhere            
LOG        tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN 
LOG        tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST 
LOG        icmp --  anywhere             anywhere            icmp echo-request limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
DROP       icmp --  anywhere             anywhere            icmp echo-request 
LOG        all  --  anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Inbound ' 
DROP       all  --  anywhere             anywhere            

Chain LSO (0 references)
target     prot opt source               destination         
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Outbound ' 
REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable 

Chain OUTBOUND (1 references)
target     prot opt source               destination         
ACCEPT     icmp --  anywhere             anywhere            
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     all  --  anywhere             anywhere            
```

---

### Post by dmizer on 2009-06-05
Rather than manually configuring IPtables, you should consider the default firewall configurator called UFW: [https://help.ubuntu.com/community/Uncomplicated_Firewall_ufw](https://help.ubuntu.com/community/Uncomplicated_Firewall_ufw)

It comes with a gui you can install called gufw.
```
sudo apt-get install gufw
```
Way better resource than Firestarter in my opinion. Any time I've used Firestarter, it's caused more problems than it's solved.

> I'm looking into why my iptables seemed so messed up (I had to copy and paste several times because it kept listing more information, even though some of it looked like duplicates), I'll post here if i get some more discernable results. Thanks for all your help! I really appreciate it!
In terminal, a left click is paste (I believe). So if you selected the text (remember, select=copy) and right clicked to look for an action menu, it would have just pasted the text you selected. Takes some getting used to, but once you learn how that select-to-copy works, it's a real time saver.

Hence my PS in post 6 ;)

---

### Post by sauerpauer on 2009-06-05
I will give UFW a shot before I start learning what's what with IPtables.  
> **dmizer said:**
> So if you selected the text (remember, select=copy) and right clicked to look for an action menu, it would have just pasted the text you selected.
I see that now....  #-o
Thanks for all your help!  I'll mark this thread as resolved (turns out I had some port forwarding problems after all).

---

