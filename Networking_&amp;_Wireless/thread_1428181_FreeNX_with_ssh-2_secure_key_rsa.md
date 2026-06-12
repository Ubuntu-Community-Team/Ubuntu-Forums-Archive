---
title: "FreeNX with ssh-2 secure key rsa"
date: 2010-03-12
forum: Networking &amp; Wireless
---

### Post by gottijr on 2010-03-12
-linux newbie-

  I just installed a home server 9.10 with xubuntu as gui

  I made a secure connection for ssh with ssh-2 rsa key.

  How can i connect through NX?

  My ssh2 rsa key requires NO pass phrase

  pls advice

---

### Post by 2hot6ft2 on 2010-03-12
You might want to go thru the How To in my sig. below.

I think what you missed was adding the line AllowUsers to /etc/ssh/sshd_config on the server.

> AllowUsers nx
AllowUsers (yourusername)
UsePAM yes (already there at bottom place AllowUsers above this)
you can also make it just one line like 
> AllowUsers nx (yourusername)

---

### Post by gottijr on 2010-03-12
> **2hot6ft2 said:**
> You might want to go thru the How To in my sig. below.

I think what you missed was adding the line AllowUsers to /etc/ssh/sshd_config on the server.


you can also make it just one line like

  thanks  i've done all those!

  but still i'm getting this error!

  and a head ache with it

---

### Post by 2hot6ft2 on 2010-03-12
> **gottijr said:**
> thanks  i've done all those!

  but still i'm getting this error!

  and a head ache with it
Did you go thru the how to?
Is FreeNX server installed on the server?
Is it running on the server?
Have you set the firewall on the server to allow the connection?
Did you generate the keys and put them in their proper places?
Did you make the edits to the /etc/ssh/ssh_config on the client?
Can you ssh into the server by terminal or nautilus?

It's all covered step by step in the how to.
It looks from the message like it's not running on the server, have you restarted it and shh?
Have you tried rebooting both machines?
If you enable password login will FreeNX connect?

---

### Post by gottijr on 2010-03-12
> **2hot6ft2 said:**
> Did you go thru the how to?
Is FreeNX server installed on the server?
Is it running on the server?
Have you set the firewall on the server to allow the connection?
Did you generate the keys and put them in their proper places?
Did you make the edits to the /etc/ssh/ssh_config on the client?
Can you ssh into the server by terminal or nautilus?

It's all covered step by step in the how to.
It looks from the message like it's not running on the server, have you restarted it and shh?
Have you tried rebooting both machines?
If you enable password login will FreeNX connect?

  yes i went through tutorials!

  i had to skip some steps as far as generating keys with puttygen on windows! for ssh i used rsa not dsa with no pass phrase!

  now when i NX has it's own key?

  how does it work?

  should i copy the authorized key from /home/user/.ssh to /var/lib/nx/home/.ssh?

  i get no message that nx is using my /home/user/.ssh/key (as it says on your tutorial)

 thanks

---

### Post by 2hot6ft2 on 2010-03-12
> **gottijr said:**
> i had to skip some steps as far as generating keys with puttygen on windows! for ssh i used rsa not dsa with no pass phrase!
There's nothing in there about "puttygen on windows" and replace dsa with rsa in the instructions.
> **gottijr said:**
> should i copy the authorized key from /home/user/.ssh to /var/lib/nx/home/.ssh?
> a key file called client.id_dsa.key will be created in: /var/lib/nxserver/home/custom_keys/

Now, we need to transfer the key to the client machine so that it can be imported in the FreeNX client application. First copy the key to your home directory on the server machine:

```
sudo cp /var/lib/nxserver/home/custom_keys/client.id_dsa.key ~/
```

Next, copy client.id_dsa.key to your client machine. Ideally you should copy the file securely, for example by running the following command from the client computer:

```
scp user@freenx-server:~/client.id_dsa.key ~/
```

which will securely copy the client.id_dsa.key file from the freenx-server computer to your home directory on the client.

> **gottijr said:**
> i get no message that nx is using my /home/user/.ssh/key (as it says on your tutorial)
I don't see that in there anywhere:confused:
Did you load the key in the FreeNX client Configuration?

---

### Post by gottijr on 2010-03-12
> **2hot6ft2 said:**
> There's nothing in there about "puttygen on windows" and replace dsa with rsa in the instructions.




I don't see that in there anywhere:confused:
Did you load the key in the FreeNX client Configuration?

  i did copy paste

  question is

  ssh has a key as well in home/user/.ssh
  nx has a key as well

  diff one

  how this works?

---

### Post by 2hot6ft2 on 2010-03-12
The ssh key allows you to connect to the ssh server like in a terminal or nautilus.
The FreeNX key allows the FreeNX client to connect to the FreeNX (nx) server.

So without a freenx key you can still ssh to the ssh server.
2 servers 2 keys
2 clients 2 keys
So 4 keys total

There is no "puttygen", "windows", "nx is using" or "/home/user/.ssh" anywhere in the how to. Try the search function and you'll see. So I don't know where you got them.

---

### Post by gottijr on 2010-03-12
Ok thanks for your time and patients

  I created a ssh-2 rsa secure key

  i'm able to connect through putty with no pass phrase

  connection is from - to (Windows laptop - local server ubuntu 9.10 with xubuntu gui)

  on freenx creat new custom key

  i copy client key and upload to putty (in windows)

  from /var/lib/nxserver/home/.ssh/client ... 

  i get the same error

  made changes in node.conf
  ```

  ENABLE_PASSDB_AUTHENTICATION="1"

# This adds SSH to the possible authentication methods. For it to work sshd
# must be set up at localhost accepting password authentication.
ENABLE_SSH_AUTHENTICATION="0"
  
  
```

  and here is my sshd_config

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
AuthorizedKeysFile      %h/.ssh/authorized_keys

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
#UseLogin no

#MaxStartups 10:30:60
#Banner /etc/issue.net

# Allow client to pass locale environment variables
AcceptEnv LANG LC_*

Subsystem sftp /usr/lib/openssh/sftp-server
AllowUsers nx
AllowUsers obama
UsePAM yes
  
```

also on "/etc/init.d/freenx restart" i get:

 ```

NX> 100 NXSERVER - Version 3.2.0-74-SVN OS (GPL, using backend: 3.3.0)
NX> 500 Error: No running sessions found.
NX> 999 Bye
NX> 100 NXSERVER - Version 3.2.0-74-SVN OS (GPL, using backend: 3.3.0)
NX> 500 ERROR: Service already running
NX> 999 Bye

```

  ON YOUR TUTORIAL I SEE:
```

 NX server will reply with:

Quote:
NX> 100 NXSERVER - Version 3.2.0-74-SVN OS (GPL, using backend: 3.3.0)
NX> 1000 NXNODE - Version 3.2.0-74-SVN OS (GPL, using backend: 3.3.0)
NX> 716 Public key added to: /home/yourusername/.ssh/authorized_keys2
NX> 1001 Bye.
NX> 999 Bye

 
```

  i never got the NX> 716 code

  p.s.: pls advice i really want to figure this one out.

---

### Post by 2hot6ft2 on 2010-03-12
> **gottijr said:**
> Ok thanks for your time and patients
You're welcome

> **gottijr said:**
> I created a ssh-2 rsa secure key
Ok, as it should be

> **gottijr said:**
> i'm able to connect through putty with no pass phrase
I did nothing with PuTTy, that's why it is NOT in the how to. You must be confusing it with another how to. But at least you can connect to the server so that's a good sign.

> **gottijr said:**
> connection is from - to (Windows laptop - local server ubuntu 9.10 with xubuntu gui)
Ok, the how to is about ubuntu to ubuntu so windows is not discussed at all in the how to. I believe this was mentioned just the other day and the user had to edit the hosts file on the windows machine. It's been so long since I've messed with the windows host file that's about all I can tell you there.

I don't even know where to put the key files in windows.

> **gottijr said:**
> on freenx creat new custom key
Right

> **gottijr said:**
> i copy client key and upload to putty (in windows)

  from /var/lib/nxserver/home/.ssh/client ... 

  i get the same error
PuTTy? I thought you were trying to get FreeNX to connect not PuTTy.:confused:

> **gottijr said:**
> made changes in node.conf
  ```

  ENABLE_PASSDB_AUTHENTICATION="1"

# This adds SSH to the possible authentication methods. For it to work sshd
# must be set up at localhost accepting password authentication.
ENABLE_SSH_AUTHENTICATION="0"
  
  
```

  and here is my sshd_config

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
AuthorizedKeysFile      %h/.ssh/authorized_keys

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
#UseLogin no

#MaxStartups 10:30:60
#Banner /etc/issue.net

# Allow client to pass locale environment variables
AcceptEnv LANG LC_*

Subsystem sftp /usr/lib/openssh/sftp-server
AllowUsers nx
AllowUsers obama
UsePAM yes
  
```
node.conf looks good

In sshd_config. I have 1 line you don't right above X11Forwarding yes I have
AllowTcpForwarding yes
Other than that they look the same.
I don't think that will matter.

> **gottijr said:**
> also on "/etc/init.d/freenx restart" i get:

 ```

NX> 100 NXSERVER - Version 3.2.0-74-SVN OS (GPL, using backend: 3.3.0)
NX> 500 Error: No running sessions found.
NX> 999 Bye
NX> 100 NXSERVER - Version 3.2.0-74-SVN OS (GPL, using backend: 3.3.0)
NX> 500 ERROR: Service already running
NX> 999 Bye

```
Same here but I use
```
sudo /etc/init.d/freenx-server restart
```
Since it is the server being restarted.

> **gottijr said:**
> ON YOUR TUTORIAL I SEE:
```

 NX server will reply with:

Quote:
NX> 100 NXSERVER - Version 3.2.0-74-SVN OS (GPL, using backend: 3.3.0)
NX> 1000 NXNODE - Version 3.2.0-74-SVN OS (GPL, using backend: 3.3.0)
NX> 716 Public key added to: /home/yourusername/.ssh/authorized_keys2
NX> 1001 Bye.
NX> 999 Bye

 
```

  i never got the NX> 716 code

  p.s.: pls advice i really want to figure this one out.
When you ran this command **on the Server in a terminal**
```
sudo nxserver --adduser (yourusername)
```
Replacing (yourusername) with the user name you log into the server normally you didn't receive the 716.
That's strange. Check in /home/yourusername/.ssh/ and see if the authorized_keys2 file is there.

You can browse to it in nautilus by opening your home folder then clicking on View and checking the "Show Hidden Files" box then you will be able to see and open the .ssh folder.

If it's not there then run it again (on the server not the client) as well as the command that follows it in the how to which is

> and add a password

```
sudo nxserver --passwd (yourusername)
```
[QUOTE]NX> 100 NXSERVER - Version 3.2.0-74-SVN OS (GPL, using backend: 3.3.0)
New password: **(enter your NEW password here and hit Enter (It wont be displayed)see below)**
Password changed.
NX> 999 Bye

(you can paste in a good long premade password which is what you will put into the freenx client so make it a good one you'll only need to put it into the FreeNX client for each profile once if you tick the save password in the configuration for (Home and Away)
I'm not sure how long it can be but it can handle at least 30 characters see:
[http://help.ubuntu.com/community/StrongPasswords]("http://help.ubuntu.com/community/StrongPasswords")

Don't forget to restart the sshd daemon after making that change using:
```
sudo /etc/init.d/ssh restart
```

I am not sure if it is really necessary but I guess it can do no harm to restart to freenx server.
```
sudo /etc/init.d/freenx-server restart
```[/QUOTE]
Remember your supposed to import the key into the FreeNX Client on the client NOT PuTTY.

And check the hosts file in windows, just search for hosts to find it I think it was in C:\ but it's been so long I wont swear to it.

Time to eat so I'll check back in a while.

---

### Post by gottijr on 2010-03-12
> **2hot6ft2 said:**
> 
I did nothing with PuTTy, that's why it is NOT in the how to. You must be confusing it with another how to. But at least you can connect to the server so that's a good sign.


  i know but i had to apply your tutorial to my own needs.

> 
PuTTy? I thought you were trying to get FreeNX to connect not PuTTy.:confused:


  I meant freenx ... my mistake



> 
AllowTcpForwarding yes
Other than that they look the same.
I don't think that will matter.

 
i fixed that


> 
When you ran this command **on the Server in a terminal**
```
sudo nxserver --adduser (yourusername)
```
Replacing (yourusername) with the user name you log into the server normally you didn't receive the 716.
That's strange. Check in /home/yourusername/.ssh/ and see if the authorized_keys2 file is there.

You can browse to it in nautilus by opening your home folder then clicking on View and checking the "Show Hidden Files" box then you will be able to see and open the .ssh folder.

If it's not there then run it again (on the server not the client) as well as the command that follows it in the how to which is


Remember your supposed to import the key into the FreeNX Client on the client NOT PuTTY.

And check the hosts file in windows, just search for hosts to find it I think it was in C:\ but it's been so long I wont swear to it.

Time to eat so I'll check back in a while.


i fixed that so there's no more of that error. But still same error from connection

  i don't get it...

  i just can't figure out.

---

### Post by gottijr on 2010-03-12
this is the error from "details"

```

NX> 203 NXSSH running with pid: 3012
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
NX> 200 Connected to address: *.*.*.* on port: 22
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
HELLO NXSERVER - Version 3.2.0-74-SVN OS (GPL, using backend: 3.3.0)
NX> 105 hello NXCLIENT - Version 3.2.0
NX> 134 Accepted protocol: 3.2.0
NX> 105 SET SHELL_MODE SHELL
NX> 105 SET AUTH_MODE PASSWORD
NX> 105 login
NX> 101 User: obama
NX> 102 Password: 
NX> 103 Welcome to: obama.hsd1.wa.comcast.net user: obama
NX> 105 listsession --user="obama" --status="suspended,running" --geometry="1920x1200x32+render" --type="unix-cde"
NX> 127 Sessions list of user 'obama' for reconnect:

Display Type             Session ID                       Options  Depth Screen         Status      Session Name
------- ---------------- -------------------------------- -------- ----- -------------- ----------- ------------------------------


NX> 148 Server capacity: not reached for user: gottijr
NX> 105 startsession  --link="adsl" --backingstore="1" --encryption="1" --cache="16M" --images="64M" --shmem="1" --shpix="1" --strict="0" --composite="1" --samba="1" --media="0" --session="Ubuntu%20Virtual" --type="unix-cde" --geometry="1914x1144" --client="winnt" --keyboard="pc102/en_US" --screeninfo="1914x1144x32+render" 

/usr/bin/nxserver: line 448: /var/lib/nxserver/db/running/sessionId{B3F2BF69F27B67946416D871CACDE115}: Permission denied
cat: /var/lib/nxserver/db/running/sessionId{B3F2BF69F27B67946416D871CACDE115}: No such file or directory
Permission denied (publickey,password).
NX> 280 Exiting on signal: 15


```

  I'm sure this you'll help someone that knows more than me

---

### Post by gottijr on 2010-03-12
I also stopped the ssh service

  Than i make changed to node.conf to default

  get freenx server to no machine key

   freenx client key to default

  and i get connection denied...

  makes no sense anymore


  i was using freenx before

 than i changed to ssh secure key

  now is not working anymore (freenx)

---

### Post by 2hot6ft2 on 2010-03-12
The bottom of that seems to give a clue.
"**Permission denied (publickey,password)**"

Like I said I don't know about using it on windows so unless someone here drops in with some words of wisdom on the FreeNX Client configuration on windows I'll have to refer you to the nomachine websites Configuration help page here:
[http://www.nomachine.com/configuration.php](http://www.nomachine.com/configuration.php)

The top one on the list has options for how you want to view the configuration setup. All I can suggest at this point is to go thru the windows client part and see if you can figure out the problem.

The server on ubuntu seems to be good to go but the client on windows is being denied for some reason which may just be as simple as where the key files are located. I just don't know.

I do see this on the Client Installation Instructions page here:
[http://www.nomachine.com/documents/client/install.php](http://www.nomachine.com/documents/client/install.php)
>  The supported platforms are:

Windows

    * 2000/2003/XP/Vista
And I don't recall you mentioning which version of windows you're using.
I hope you get it straightened out since it's a great setup once you get it running.

---

### Post by gottijr on 2010-03-12
NEED TO UPDATE - THINGS CHANGED AFTER REBOOT

  so after:

   1. stop ssh
   2. change node.conf to default
   3. set freenx server to no machine key
   4. freenx client - key to default
   5. REBOOT - server

  i got access back.

  so i'm trying to figure out how this should work now.

---

### Post by gottijr on 2010-03-12
UPDATE

  1. change freenx server to custom new key
  2. change the key in freenx client
  3. working good

  all this with "node.conf" default!!!

  the only change that we still have is in "sshd_config"

   adduser nx username

  i guess this is it !

  All this i guess because my ssh authentification is again JUST WITH PASSKEY WITHOUT PASS PHRASE.

  i will keep updates on that.

  if someone knows more about this pls advice!

 P.S. thanks alot 2hot6ft2 for all your time.

---

### Post by 2hot6ft2 on 2010-03-12
> **gottijr said:**
> NEED TO UPDATE - THINGS CHANGED AFTER REBOOT

  so after:

   1. stop ssh
   2. change node.conf to default
   3. set freenx server to no machine key
   4. freenx client - key to default
   5. REBOOT - server

  i got access back.

  so i'm trying to figure out how this should work now.
Well if it works with the default freenx key then it's not that bad. As long as you can still disable password autentication in ssh and still connect you're pretty secure since even if someone were to get past the default freenx key they would still have to deal with the ssh key.

---

### Post by 2hot6ft2 on 2010-03-12
> **gottijr said:**
> UPDATE

  1. change freenx server to custom new key
  2. change the key in freenx client
  3. working good

  all this with "node.conf" default!!!

  the only change that we still have is in "sshd_config"

   adduser nx username

  i guess this is it !

  All this i guess because my ssh authentification is again JUST WITH PASSKEY WITHOUT PASS PHRASE.

  i will keep updates on that.

  if someone knows more about this pls advice!

 P.S. thanks alot 2hot6ft2 for all your time.
Does that mean it's working like it should now?
And welcome.

EDIT: Once you can login with the pass "key" you should be able to change:
# Change to no to disable tunnelled clear text passwords
PasswordAuthentication yes

to no in sshd_config

---

### Post by gottijr on 2010-03-12
> **2hot6ft2 said:**
> Well if it works with the default freenx key then it's not that bad. As long as you can still disable password autentication in ssh and still connect you're pretty secure since even if someone were to get past the default freenx key they would still have to deal with the ssh key.

  Looks like it works also with new custom key
  
  So far i guess it was just from the changes in node.conf

  i will test more and update

  P.S. again my ssh-2 key requires no password. is automatic login with private key.

---

### Post by 2hot6ft2 on 2010-03-12
> **gottijr said:**
> Looks like it works also with new custom key
  
  So far i guess it was just from the changes in node.conf

  i will test more and update

  P.S. again my ssh-2 key requires no password. is automatic login with private key.
Glad to hear it. Enjoy.

---

### Post by gottijr on 2010-03-12
This is crazy

  actually it looks like you need to modify node.config

  but i get this error

  anyone have any ideea?

  thanks

---

### Post by gottijr on 2010-03-12
UPDATE

  It's starting to make more sens!

  i made this thread a big mess with all my postings... 

  too much stress one day lost with figuring out this freenx and ssh priv key connection

  good results so far:

  if i set everything as the tutorial posted previously i get that screen when i try to open the terminal! (now this is the new problem)

  if i leave sshd_config 

  with PasswordAuthentication yes

  everything is fine ... i get a normal terminat user@ip:

 But i don't have the secure ssh with private key.

  anyone can advice?

---

### Post by jervill on 2010-11-13
> **gottijr said:**
> this is the error from "details"

```

NX> 203 NXSSH running with pid: 3012
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
NX> 200 Connected to address: *.*.*.* on port: 22
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
HELLO NXSERVER - Version 3.2.0-74-SVN OS (GPL, using backend: 3.3.0)
NX> 105 hello NXCLIENT - Version 3.2.0
NX> 134 Accepted protocol: 3.2.0
NX> 105 SET SHELL_MODE SHELL
NX> 105 SET AUTH_MODE PASSWORD
NX> 105 login
NX> 101 User: obama
NX> 102 Password: 
NX> 103 Welcome to: obama.hsd1.wa.comcast.net user: obama
NX> 105 listsession --user="obama" --status="suspended,running" --geometry="1920x1200x32+render" --type="unix-cde"
NX> 127 Sessions list of user 'obama' for reconnect:

Display Type             Session ID                       Options  Depth Screen         Status      Session Name
------- ---------------- -------------------------------- -------- ----- -------------- ----------- ------------------------------


NX> 148 Server capacity: not reached for user: gottijr
NX> 105 startsession  --link="adsl" --backingstore="1" --encryption="1" --cache="16M" --images="64M" --shmem="1" --shpix="1" --strict="0" --composite="1" --samba="1" --media="0" --session="Ubuntu%20Virtual" --type="unix-cde" --geometry="1914x1144" --client="winnt" --keyboard="pc102/en_US" --screeninfo="1914x1144x32+render" 

/usr/bin/nxserver: line 448: /var/lib/nxserver/db/running/sessionId{B3F2BF69F27B67946416D871CACDE115}: Permission denied
cat: /var/lib/nxserver/db/running/sessionId{B3F2BF69F27B67946416D871CACDE115}: No such file or directory
Permission denied (publickey,password).
NX> 280 Exiting on signal: 15


```

  I'm sure this you'll help someone that knows more than me

I know this is an old topic, but I thought I'd post my solution here for anyone else that was running into this problem too.

I was encountering this error when I had SSH setup to only use Public/Private Key encryption (PasswordAuthentication set to no) and was using the default freeNX keys. The answer (which seems pretty obvious now) is to add the default freeNX key to the /home/<username>/.ssh/authorized_keys file. The freeNX key can be found in /etc/nxserver/users.id_dsa.pub

---

