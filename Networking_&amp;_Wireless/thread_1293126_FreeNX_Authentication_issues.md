---
title: "FreeNX Authentication issues"
date: 2009-10-16
forum: Networking &amp; Wireless
---

### Post by sircrayons on 2009-10-16
I have read everything I could find on the subject, and something's still not right.

I'm running Jaunty x86. I've got OpenSSH working just fine with public key authentication. I can log in from other Ubuntu machines and from Windows using PuTTY. For some reason, I can't get FreeNX to work. Here's what I get when I run nxsetup:
```
michael@fileserver:~$ sudo /usr/lib/nx/nxsetup --install
------> It is recommended that you use the NoMachine key for
        easier setup. If you answer "y", FreeNX creates a custom
        KeyPair and expects you to setup your clients manually.
        "N" is default and uses the NoMachine key for installation.

 Do you want to use your own custom KeyPair? [y/N] nSetting up /etc/nxserver ...done
Setting up /var/lib/nxserver/db ...done
Setting up /var/log/nxserver.log ...done
Adding user "nx" to group "utmp" ...done
Setting up known_hosts and authorized_keys2 ...done
Setting up permissions ...done
Setting up cups nxipp backend ...done

----> Testing your nxserver configuration ...
Warning: Invalid value "COMMAND_START_KDE=startkde"
         Users will not be able to request a KDE session.
Warning: Invalid value "COMMAND_START_CDE=xfce4-session"
         Users will not be able to request a CDE session.
Warning: Invalid cupsd version of "/usr/sbin/cupsd". Need version 1.2.
         Users will not be able to enable printing. Ignore if you use cups > 1.2

  Warnings occured during config check.
  To enable these features please correct the configuration file.

<---- done

----> Testing your nxserver connection ...
Permission denied (publickey).
Fatal error: Could not connect to NX Server.

Please check your ssh setup:

The following are _examples_ of what you might need to check.

        - Make sure "nx" is one of the AllowUsers in sshd_config.
    (or that the line is outcommented/not there)
        - Make sure "nx" is one of the AllowGroups in sshd_config.
    (or that the line is outcommented/not there)
        - Make sure your sshd allows public key authentication.
        - Make sure your sshd is really running on port 22.
        - Make sure your sshd_config AuthorizedKeysFile in sshd_config is set to authorized_keys2.
    (this should be a filename not a pathname+filename)
  - Make sure you allow ssh on localhost, this could come from some
    restriction of:
      -the tcp wrapper. Then add in /etc/hosts.allow: ALL:localhost
      -the iptables. add to it:
         $ iptables -A INPUT  -i lo -j ACCEPT
         $ iptables -A OUTPUT -o lo -j ACCEPT
```
Here's my sshd_config file:
```
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
PermitRootLogin no
StrictModes yes

RSAAuthentication yes
PubkeyAuthentication yes
AuthorizedKeysFile	%h/.ssh/authorized_keys
AuthorizedKeysFile %h/.ssh/authorized_keys2
AuthorizedKeysFile /var/lib/nxserver/home/.ssh/authorized_keys2

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
PasswordAuthentication no

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

AllowUsers michael nx
```
I've followed the instructions [here]("https://help.ubuntu.com/community/FreeNX") to no avail. Any help would be greatly appreciated.

---

### Post by Tha-Fox on 2009-10-29
I have almost the same situation. Here is what I've done so far.

1) I followed [this excellent guide]("https://help.ubuntu.com/community/FreeNX") while installing.

2) I got error saying ```
authentication failed for user my_username
```
auth.log had these lines: 
```
Oct 29 10:30:24 my_hostname sshd[20263]: pam_unix(sshd:session): session closed for user my_username
Oct 29 10:36:36 konenimi sshd[25275]: Accepted publickey for nx from client_ip port 52740 ssh2
Oct 29 10:36:36 my_hostname sshd[25275]: pam_unix(sshd:session): session opened for user nx by (uid=0)
Oct 29 10:36:43 my_hostname nxserver[25499]: (nx) Failed login for user=my_username from IP=client_ip
Oct 29 10:36:43 my_hostname sshd[25275]: pam_unix(sshd:session): session closed for user nx
```

3) I edited my sshd_config according to [this guide]("http://www.sharpee.com/wordpress/?p=108"). Now it accepts my public key but I still can't get in. 

4) I checked my /var/lib/nxserver/home/.ssh/authorized_keys2 and noticed that it ends with root@my_hostname. Is this wrong since root login is not permitted in sshd_config?

---

### Post by lorubenet on 2010-03-10
Hi there,

I've been fighting with FreeNx for hours finding the same problems as sircrayons. I could finally solve that. 

The problem was that I had installed lsh-server (I think kubuntu installs it by default). That means that the ssh server was not working, the lsh was working instead. Thus all changes made in the sshd_config file were plainly ignored. When restarting the ssh server one would get:

OpenBSD Secure Shell server not in use (/etc/ssh/sshd_not_to_be_run)

I could not find a way to keep this lsh and use freenx, and searching around the best advice I could find was to remove that lsh-server, so that's what I did.
After doing that I had to restart as the ssh server is then mixed up. Trying to ssh localhost does not work anymore (the password is not accepted). 
After that the thing works as explained in the ubuntu freenx help page. 

On a side note, I finally didn't do any change in the original sshd_config file. I simply use custom generated keys (pressing Y when doing the install). Then I copied the key to the machine where the client resides and voila, it worked nicely.

I hope this spares someone the few hours I was bumping my head against the wall. 
Ruben

---

