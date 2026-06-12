---
title: "SSH Issue - 12.04 - Permissions Problem"
date: 2012-08-14
forum: Networking &amp; Wireless
---

### Post by Lanh on 2012-08-14
Hi,

Today I upgraded from 10.04 via the distribution upgrade mechanism through all the steps up to 12.04 and now SSH and SFTP no longer work.

I use my laptop mainly as a file server for my Android devices, and had been merrily using both ConnectBot and X-Plore to connect from my tablet and phone to my laptop, both on the internal network and the external network, (via the internet).

Now, neither program will connect to the laptop at all, connectbot gives an error saying that it has timed out, (xplore gives no error message).

I have tried reinstalling, I have tried following numerous help tutorials which have been posted in this and other forums, and so far nothing has helped turning me from someone who is extremely happy with Ubuntu to someone who is now so frustrated by it that he is considering throwing the laptop out of the window and simply sticking with android in the future.

The error appears to be a permissions thing, as when I run ssh in debug mode it says that it can't load acceptable keys and a few other things including binding the service to port 22 which is obviously a problem. (Sorry I can't paste from terminal, I'm using my tablet while my laptop works out whether or not it's actually going to restart ssh and apparently it needs all it's resources to do that).

If someone could walk me through what I have to do, baby step by baby step to have it working exactly as I did in 10.04, (when it just worked), or could at least point me in the direction of what might have changed to mess up a working configuration between 10.04 and 12.04 so that I have some idea of what I'm actually searching for, I'd be massively appreciative.

---

### Post by Lanh on 2012-08-14
Okay, I've done a hard reboot, this is the debug error
```
debug1: sshd version OpenSSH_5.9p1 Debian-5ubuntu1
debug1: could not open key file '/etc/ssh/ssh_host_rsa_key': Permission denied
Could not load host key: /etc/ssh/ssh_host_rsa_key
debug1: could not open key file '/etc/ssh/ssh_host_dsa_key': Permission denied
Could not load host key: /etc/ssh/ssh_host_dsa_key
debug1: setgroups() failed: Operation not permitted
debug1: rexec_argv[0]='/usr/sbin/sshd'
debug1: rexec_argv[1]='-d'
Set /proc/self/oom_score_adj from 0 to -1000
debug1: Bind to port 22 on 0.0.0.0.
Bind to port 22 on 0.0.0.0 failed: Permission denied.
debug1: Bind to port 22 on ::.
Bind to port 22 on :: failed: Permission denied.
Cannot bind any address.

```

---

### Post by Lanh on 2012-08-14
New related, (probably?),  issue discovered....

I can no longer login via SSH to my remote server using the laptop either, (it continues to work without issue on the tablet and the phone), using command line in the terminal. 

Forgive my frustration, but I'm really beginning to wish that instead of acting upon the pop-ups telling me that I should upgrade, that I'd just found a way to disable them, because as things stand, the main two purposes that I use Ubuntu for, have been decimated by the upgrade and I'm sitting here with a machine which is now effectively useless (other than storing files that I can no longer get at). At least 10.04 worked ya know. 

Again, please forgive my frustration, but this is exactly the kind of thing that I stopped using Windows for.

---

### Post by hawkmage on 2012-08-14
Where are the error you posted from?  Was it from the auth.log file?  Or was an from truing to run ssh from the command line?

---

### Post by Lanh on 2012-08-14
Trying to run SSH from the command line with the -d tag.

---

### Post by hawkmage on 2012-08-14
Did you run ssh or sshd?

The errors you listed look like errors from trying to run the sshd executable as a regular user.  

The command "ssh" is for connecting to annother system where as sshd is the executable for the ssh darmon.  If you are trying to start the ssh daemon run "sudo service ssh start"

---

### Post by Lanh on 2012-08-15
I had been attempting to start it in that manner.

Further testing indicated that when trying to start it the /etc/init.d/ method that sshd was in fact missing, (thanks software centre), so I wiped it out and then reinstalled via aptitude, which I managed to get the server up and running using.```
sudo service ssh restart
ssh stop/waiting
ssh start/running, process 23955

```

However, I'm still experiencing errors when attempting to connect to the laptop via either ssh or sftp, with both methods, (using ConnectBot and AndFTP), simply timing out when previously, (using 10.04), the connection was pretty much instantaneous.

Do I have any errors in my config file, (sshd_config), that I am missing? I wouldn't think that was altered by the update from 10.04 through 12.04, but I can't think of anything else.

```
# Package generated configuration file
# See the sshd_config(5) manpage for details

# What ports, IPs and protocols we listen for
Port 22
# Use these options to restrict which interfaces/protocols sshd will bind to
ListenAddress ::
ListenAddress 0.0.0.0
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
#AuthorizedKeysFile	%h/.ssh/authorized_keys

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
PasswordAuthentication yes

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
UseLogin no

#MaxStartups 10:30:60
#Banner /etc/issue.net

# Allow client to pass locale environment variables
AcceptEnv LANG LC_*

Subsystem sftp /usr/lib/openssh/sftp-server

# Set this to 'yes' to enable PAM authentication, account processing,
# and session processing. If this is enabled, PAM authentication will
# be allowed through the ChallengeResponseAuthentication and
# PasswordAuthentication.  Depending on your PAM configuration,
# PAM authentication via ChallengeResponseAuthentication may bypass
# the setting of "PermitRootLogin without-password".
# If you just want the PAM account and session checks to run without
# PAM authentication, then enable this but set PasswordAuthentication
# and ChallengeResponseAuthentication to 'no'.
UsePAM yes
```

---

### Post by hawkmage on 2012-08-15
Normily you only need to use the ListenAddress if you want to limit sshd to a specific address, if you want it to respond on all interfaces all you need is the line "Port 22".

What do you get when running this:
```
sudo lsof -p `pgrep sshd -P 1` -n -P | grep 'IPv[46]'
```

ALso what about running this command on the server:
```
ssh localhost
```

---

