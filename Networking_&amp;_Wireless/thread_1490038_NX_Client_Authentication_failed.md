---
title: "NX Client Authentication failed"
date: 2010-05-21
forum: Networking &amp; Wireless
---

### Post by kevin_@ on 2010-05-21
Hi,
 
I have been used NX client on windows 7 connected to ubuntu with NX client/node/server with no issues. The matter started when I have formatted Ubuntu and reinstalled NX, from that NX connects but shows a key error as follows:
 
NX> 203 NXSSH running with pid: 4328
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
NX> 200 Connected to address: 192.168.0.xxx on port: 22
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
NX> 204 Authentication failed.
 
I have been doing all the procedures I could thought and others I have found at forums as:
 
- included NX and 'my user' at sshd_config
- included authorized_key2 at sshd_config 
- copyed the keys from /usr/NX/share/keys and used them at windows client
- generated new key using nxserver -keygen and also used at windows client
- changed the /.ssh ownership to 'my user' and NX giving them all privileges
- reinstalled nx client/node/server at ubuntu
- uninstalled client/node/server, deleted NX directory at ubuntu and reinstalled all
- stoped and restarted the server service
 
the only way i have managed to get back the connection was to reinstall the packs below but i can not answer why it runned. those packs were choosed just as a clue because I thought there is a SSh config issue. so once i reinstall them the connection runs fine BUT until the rebooting of PC! once PC it is restarted the only way to get new connection is to reinstall those packs again.
 
ishutils
ishclient
ishserver
putty-tools
openssh-client
openssh-server
putty
ssh-askpass-gnome
x11-session-utils
hotssh
 
it seems there is a SSH config issue but i was not been able to find what.
all advices will be very welcome.
 
Cheers
 
 
 
 
my sshd_config copy:
 
########################################
 
# Package generated configuration file
# See the sshd( manpage for details
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
AllowUsers nx meuuser
StrictModes no
RSAAuthentication yes
PubkeyAuthentication yes
AuthorizedKeysFile %h/.ssh/authorized_keys
AuthorizedKeysFile %h/.ssh/authorized_keys2
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
ChallengeResponseAuthentication yes
# Change to no to disable tunnelled clear text passwords
#PasswordAuthentication yes
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
#############

---

### Post by chon on 2010-05-22
Hi Kevin.

I have been having a very similar issue and have been working on it for a couple of days and can't seem to resolve it either.  Have done exactly what you've done as well.

Likely won't solve your problem but I noted in your sshd_config file that you have:
AuthorizedKeysFile %h/.ssh/authorized_keys
AuthorizedKeysFile %h/.ssh/authorized_keys2

Depending on which file you're using you probably want to comment out the one you don't want to use.  It looks like it is currently defaulting to authorized_keys2.

When I run /usr/NX/bin/nxserver --status it gives me the following:
NX> 900 Connecting to server ...
NX> 204 Authentication to NX server failed.
NX> 110 NX Server is stopped.
NX> 999 Bye.

However, when I run /usr/NX/bin/nxserver --usercheck chon it seems to be okay.
NX> 900 Verifying public key authentication for NX user: chon.
NX> 900 Public key authentication succeeded.
NX> 999 Bye.

Which version of ubuntu are you using?  I'm using 10.4.  Worked fine for me under 8.10, 9.04, 9.10 but can't seem to get it working on 10.4

I share in your frustration.....

---

### Post by kevin_@ on 2010-05-22
Hi Chon,
 
Thanks for your replying and observation about 'authorized_keys'. I have commented that line, restarted the service and tryed to connect but no success...
 
I am using Ubuntu 9.1 and NX has been running fine at 9.1 before I have formatted the machine.
 
Does anybody has any suggestion for us??!! 
 
Cheers

---

### Post by kevin_@ on 2010-05-22
Hi Again
 
I just have tryed /usr/NX/bin/nxserver --status and got the same:
 
root@xxxxxx:~# /usr/NX/bin/nxserver --status
NX> 900 Connecting to server ...
NX> 204 Authentication to NX server failed.
NX> 110 NX Server is stopped.
NX> 999 Bye.
 
but then tryed /usr/NX/bin/nxserver --usercheck and it is not recognized by the system and so I clue the service is not up.
 
but when I start the service it says that service is ALREADY running.
 
root@xxxxxx:~# /usr/NX/bin/nxserver --start
NX> 500 Service already running.
NX> 999 Bye.
 
and for the last try again /usr/NX/bin/nxserver --usercheck but is not recognized, still the same as before.
 
strange but it seems we have a problem of permissions as a root cause of server service down...
 
i will try to grant full permission to NX dir and see waht hapens, would be great if You could try the same Chon.
 
Cheers

---

### Post by mhowell67 on 2011-01-13
I'm seeing NX> 500 ERROR: Public key authentication failed when doing usercheck for my account. Any suggestions on how I fix this?

---

### Post by chon on 2011-04-17
Hi all.

After several attempts at trying to get NX up-and-running I was finally able to do it.  To help others like me who struggled to do this I wrote up a "NoMachine NX Installation Guide v1.0" document in an attempt to help others.  Please feel free to edit this document to improve on it.

If you have any questions please let me know and I'll do what I can to help.  Also, please let me know if this was helpful to you.

Chon

---

### Post by AlexWerz on 2011-05-13
chon, you saved my day. I would like to  translate the installation into german and put it on my homepage (if you don't mind).

Take care,
Alex

---

### Post by chon on 2011-05-13
Hi Alex. 

I'm glad it helped.  Please feel free to translate it and improve on it as you see fit.

chon

---

### Post by mattniiro on 2011-12-07
Thank you so much for the wonderful write up.  It helped me get thru all of my issues.

Have a great day.

---

### Post by Diego318 on 2012-01-11
HOLY CRAP, IT WORKS.

DO EVERYTHING IN CHON'S GUIDE


:popcorn: :popcorn: :popcorn:

---

### Post by drewncrew on 2012-03-21
Thanks!!!  After hours of attempting to install NX, I came across your document and NX is working now.  Also, I am running this on MINT.



> **chon said:**
> Hi all.

After several attempts at trying to get NX up-and-running I was finally able to do it.  To help others like me who struggled to do this I wrote up a "NoMachine NX Installation Guide v1.0" document in an attempt to help others.  Please feel free to edit this document to improve on it.

If you have any questions please let me know and I'll do what I can to help.  Also, please let me know if this was helpful to you.

Chon

---

### Post by ja_fileiv2 on 2012-07-18
My dear friend... I was excited about this document as everyone used it and it works but unfortunately that doesn't work for me...

Im still getting the "The NX Service is not available  or the NX access was disable on your local host"

NX> 203 NXSSH running with pid: 3668
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
NX> 200 Connected to address: 127.0.0.1 on port: 443
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
NX> 204 Authentication failed.


Could someone please help me??

Thanks a lot fellows!

---

### Post by oznrngr on 2012-10-20
The solution posted on the site worked for me:

[http://www.linuxquestions.org/questions/linux-software-2/nx-server-access-problem-930551/](http://www.linuxquestions.org/questions/linux-software-2/nx-server-access-problem-930551/)

cd /usr/NX/home/nx/.ssh
ln -s authorized_keys2 authorized_keys

I'm running opensuse 12.2 with NX Server 3.5.0-11

---

### Post by mpjoe2000 on 2012-10-30
NXSFE has a limit of 2 sessions per server. Why don't you use FreeNX, which doesn't have this limit.

easy installation guide, but read carefully!!

Ubuntu installation:
[https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX)

Debian installation:
[http://wiki.debian.org/freenx](http://wiki.debian.org/freenx)

---

### Post by bphhsh on 2012-11-12
Excellent with the guide, but to solve the same problem I just did: ( with explanation from the man file below).
 
As root: try the following
 
nxserver --keygen

--keygen
  Generate a new pair of SSH keys. After running this procedure, the
  NX clients will use  the key: /usr/NX/share/keys/default.id_dsa.key
  to connect to this NX server.

nxserver --keyrestore

--keyrestore 
  Restore the SSH key-pair provided with the server package. Current 
  public key will be moved to default.id_dsa.pub.backup file, private
  key will be moved to /usr/NX/share/keys/default.id_dsa.key.backup
  file.

nxserver --usercheck myusername

--usercheck USERNAME
  Check the status of the specified user and add the public key for SSH 
  authentication to the user's authorized keys file.
  
  
  When I did this authentication worked again

---

### Post by cu_ on 2012-11-23
After spending almost a day on this, I gave up and went back to Nomachine nx 3.5 (this problem occurred exact the same way as OP described for preview 4).  Hope NoMachine gets a chance to iron out any incompatibilities with 12.10 before the preview period for 4 ends.

---

### Post by cr0cK on 2013-01-05
I'm a Arch user and I just wasted 2 hours to try to understand all this stuff. But, as I expected, the solution is quite simple and is given on this page: [http://www.nomachine.com/ar/view.php?ar_id=AR10B00046](http://www.nomachine.com/ar/view.php?ar_id=AR10B00046)

And, make sure than:
- you have your public key (on the server) in /usr/NX/home/nx/.ssh/authorized_keys
- you can connect to your server with: ssh nx@server (use -v to have some debug output if you can't connect to try to understand why)

If you can, you should be able to connect with the NX client.

Good luck.

---

### Post by cr0cK on 2013-01-05
Well, after 30 min again to refix authentification, I removed this of the NX public key (/usr/NX/home/nx/.ssh/authorized_keys) to make the stuff working.

no-port-forwarding,no-agent-forwarding,command="/usr/NX/bin/nxnode

---

### Post by mpincay on 2013-03-04
Great work!!!!

Thank you very much!

---

### Post by Luckyfriend22 on 2013-06-03
Guys, after doing everything in this document, I got the farthest yet. But, using a Windows client to connect to NX server 3.5 running on CentOS 6.4 (I know, not Ubuntu, but this post was the only one that could get me remotely close to solving my problem after 4 days, hence the reply), I still get error messages. It still won't work.  I need this to work from Windows 7 machines specifically, and need the GUI in linux to do some specific stuff, so any help specific to NX will be much appreciated.  First, here is the error in client side:

NX> 203 NXSSH running with pid: 3664
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
NX> 200 Connected to address: 192.168.137.70 on port: 22
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
HELLO NXSERVER - Version 3.5.0-11 - LFE
NX> 105 Hello NXCLIENT - Version 3.5.0
NX> 134 Accepted protocol: 3.5.0
NX> 105 Set shell_mode: shell
NX> 105 Set auth_mode: password
NX> 105 Login 
NX> 101 User: Hans
NX> 102 Password: ******
NX> 103 Welcome to: centosoefen user: Hans
NX> 105 Listsession --user="Hans" --status="suspended\054running" --geometry="1920x1080x32+render" --type="unix-gnome" 
NX> 127 Available sessions: 

Display Type             Session ID                       Options  Depth Screen         Status      Session Name
------- ---------------- -------------------------------- -------- ----- -------------- ----------- ------------------------------

NX> 148 Server capacity: not reached for user: Hans
NX> 105 Start session with: --link="wan" --backingstore="1" --encryption="1" --cache="16M" --images="64M" --shmem="1" --shpix="1" --strict="0" --composite="1" --media="0" --session="CentOSHome" --type="unix-gnome" --geometry="1914x1022" --client="winnt" --keyboard="pc102\057en_US" --screeninfo="1914x1022x32+render" 
NX> 595 ERROR: A fatal error occurred in NX Server.
NX> 595 ERROR: The exception id is: B76E8FB5. To get detailed information about
NX> 595 ERROR: the error search for the string B76E8FB5 in the system log
NX> 595 ERROR: file (usually '/var/log/messages').
NX> 500 ERROR: Last operation failed.
NX> 280 Exiting on signal: 15


Checking /var/log/messages I got the following:


[root@centosoefen ~]# cat /var/log/messages | grep B76E8FB5
Jun   3 21:53:57 centosoefen NXSERVER-3.5.0-11[6639]: ERROR: (exception id  B76E8FB5) Failed to add the host to the list of known hosts  (/usr/NX/home/nx/.ssh/known_hosts).#015
Jun  3 21:53:57 centosoefen  NXSERVER-3.5.0-11[6639]: ERROR: (exception id B76E8FB5) NX> 596  ERROR: NXNODE Ver. 3.5.0-9  (Error id e7F7188)
Jun  3 21:53:57  centosoefen NXSERVER-3.5.0-11[6639]: ERROR: (exception id B76E8FB5)  NX> 596 ERROR: create session: run commands
Jun  3 21:53:57  centosoefen NXSERVER-3.5.0-11[6639]: ERROR: (exception id B76E8FB5)  NX> 596 ERROR: execution of last command failed
Jun  3 21:53:57  centosoefen NXSERVER-3.5.0-11[6639]: ERROR: (exception id B76E8FB5)  NX> 596 last command: /usr/bin/xauth -v -f  /home/Hans/.nx/C-centosoefen-1001-09F550CF05BE1F30EACAEC2DC9141C7C/authority  source  /home/Hans/.nx/C-centosoefen-1001-09F550CF05BE1F30EACAEC2DC9141C7C/scripts/authority
Jun  3 21:53:57 centosoefen NXSERVER-3.5.0-11[6639]: ERROR: (exception id B76E8FB5) NX> 596 exit value: 1
Jun   3 21:53:57 centosoefen NXSERVER-3.5.0-11[6639]: ERROR: (exception id  B76E8FB5) NX> 596 stdout: Using authority file  /home/Hans/.nx/C-centosoefen-1001-09F550CF05BE1F30EACAEC2DC9141C7C/authority
Jun   3 21:53:57 centosoefen NXSERVER-3.5.0-11[6639]: ERROR: (exception id  B76E8FB5) NX> 596 Writing authority file  /home/Hans/.nx/C-centosoefen-1001-09F550CF05BE1F30EACAEC2DC9141C7C/authority
Jun   3 21:53:57 centosoefen NXSERVER-3.5.0-11[6639]: ERROR: (exception id  B76E8FB5) NX> 596 stderr: /usr/bin/xauth:  creating new authority  file  /home/Hans/.nx/C-centosoefen-1001-09F550CF05BE1F30EACAEC2DC9141C7C/authority
Jun   3 21:53:57 centosoefen NXSERVER-3.5.0-11[6639]: ERROR: (exception id  B76E8FB5) NX> 596 /usr/bin/xauth:  /home/Hans/.nx/C-centosoefen-1001-09F550CF05BE1F30EACAEC2DC9141C7C/scripts/authority:3:   bad display name "centosoefen:1001" in "add" command
Jun  3  21:53:57 centosoefen NXSERVER-3.5.0-11[6639]: ERROR: (exception id  B76E8FB5) NX> 596 init: stdin arguments:  user=Hans,userip=192%2e168%2e137%2e1,uniqueid=09F550CF05BE1F30EACAEC2DC9141C7C,display=1001,node_number=0,server_name=centosoefen,license=%28None%29,subscriptionid=None,productid=LFE,reconnect=1,balance_host=192%2e168%2e137%2e70,encryption_mode=3,connection=local,images=64M,cache=16M,client=winnt,media=0,backingstore=1,encryption=1,strict=0,clipboard=both,shpix=1,rootless=0,composite=1,session=CentOSHome,shmem=1,type=unix%2dgnome,virtualdesktop=1,screeninfo=1914x1022x32%2brender,keyboard=pc102%2fen_US,geometry=1914x1022,link=wan
Jun   3 21:53:57 centosoefen NXSERVER-3.5.0-11[6639]: ERROR: (exception id  B76E8FB5) NXNodeExec::exec('startsession',  'user=Hans&userip=192%2e168%2e137%2e1&uniqueid=09F550CF05BE1F30EA...',  'localhost', 22) called at handlers/nxserver.pl line 3582
Jun  3  21:53:57 centosoefen NXSERVER-3.5.0-11[6639]: ERROR: (exception id  B76E8FB5) NXShell::handler_session_start('--link="wan"  --backingstore="1" --encryption="1" --cache="16M" -...') called at  NXShell.pm line 373
Jun  3 21:53:57 centosoefen  NXSERVER-3.5.0-11[6639]: ERROR: (exception id B76E8FB5)  NXShell::handle_command('startsession', '--link="wan" --backingstore="1"  --encryption="1" --cache="16M" -...') called at NXShell.pm line 145
Jun   3 21:53:57 centosoefen NXSERVER-3.5.0-11[6639]: ERROR: (exception id  B76E8FB5) NXShell::run() called at nxserver.pl line 4497
Jun  3 21:53:57 centosoefen NXSERVER-3.5.0-11[6639]: ERROR: (exception id B76E8FB5) eval {...} called at nxserver.pl line 4456


Please bare in mind that I am a total newbie to Linux, and a very stubborn Windows user :-)

Any help guys?

---

### Post by Luckyfriend22 on 2013-06-03
Just a note: since I posted my previous reply, I decided to go with Ubuntu for what I want to do. It is more easily integrated with Windows, so the wife will not have any difficulty managing without my presence.

But still, any help on those errors will be ever so welcome!

Thanx!

---

### Post by jerome3 on 2013-08-11
Hi Chon

thank you so much for this helpfull and complete guide, it is clearer than the manual on nomachine website :KS

I an debian user and I would like to complete it and translate it in french if you are ok ?

One question that I still have not understood, do you think it's possible to connect only using ssh keys (without any password), maybe by doing another configuration in the server.cfg file? 
but which option activate?

see you soon

---

### Post by chon2 on 2013-08-21
Hi jerome3

If you look at this url:
[http://www.nomachine.com/documentation/admin-guide.php](http://www.nomachine.com/documentation/admin-guide.php)

Under point #4 it says the following:

NX is configured by default to allow access for any system user, as long as the user provides valid credentials for the SSH login. **Please note that SSH authentication without password is not supported.** NX offers an alternative authentication method, allowing the administrator to specify which user can access the system through NX. This works by implementing a separation between the system password and the NX password, so that, for example, it is possible to forbid remote access to the system by any other means except NX and use the NX tools to implement effective accounting of the system resources used by the user.

So it appears you can't do what you're intending with SSH authentication.

Chon

---

### Post by chon2 on 2013-08-21
@Luckyfriend22:

I don't use CentOS so I can't check this; however, it appears you have a permission problem.  To see if this is the case you can try the following:

$ sudo chmod 0700 /usr/NX/home/nx/.ssh/known_hosts

Now try and login and fingers crossed you'll have success.

Chon

---

### Post by bruno5 on 2013-10-06
Chon,

I have been trying to do that for one week, until I saw your document. Thank you so much!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

Btw, your instructions apply to red hat too.

---

### Post by yh_wu on 2014-06-03
Just delete the /usr/NX folder and uninstall and reinstall. You may also need to delete the user nx in /etc/passwd .

Every time a newer/older version of nomachine is installed, you may need to clean up old/new stuff.

---

