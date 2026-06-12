---
title: "SSH home network"
date: 2009-04-27
forum: Networking &amp; Wireless
---

### Post by NJC on 2009-04-27
Trying to ssh via a home network (wired router). I've generated the public key without password on client and copied to server into /.ssh/authorized_keys. Changed sshd_config to "Passwordauthentication no" and then ssh restart. chmod on Server and Client

```
$ $ chmod go-w ~/
$ chmod 700 ~/.ssh
$ chmod go-rwx ~/.ssh/*
```Output ssh -v <server ip>:
> debug1: Authentications that can continue: publickey
debug1: Next authentication method: publickey
debug1: Offering public key: /home/#####/.ssh/id_rsa
debug1: Authentications that can continue: publickey
debug1: Trying private key: /home/#####/.ssh/identity
debug1: Trying private key: /home/#####/.ssh/id_dsa
debug1: No more authentication methods to try.
Permission denied (publickey).
What am I doing wrong?  ](*,) I've perused these and a 1/2 dozen more links trying to find the answer.

[https://help.ubuntu.com/community/AdvancedOpenSSH](https://help.ubuntu.com/community/AdvancedOpenSSH)
[https://help.ubuntu.com/community/SSHHowto#Logging%20in%20from%20other%20computers]("https://help.ubuntu.com/community/SSHHowto#Logging%20in%20from%20other%20computers")
[http://sial.org/howto/openssh/publickey-auth/](http://sial.org/howto/openssh/publickey-auth/)

---

### Post by Iowan on 2009-04-27
> **NJC said:**
> I've generated the public key without password on client and copied to server into /.ssh/authorized_keys.Is that the right directory - or does it need to go under */home/username/.ssh*?

---

### Post by NJC on 2009-04-27
> Assuming that all of the servers use OpenSSH instead of a different SSH implementation, the public key data must be appended into the ~/.ssh/authorized_keys file on the servers.[http://sial.org/howto/openssh/publickey-auth/](http://sial.org/howto/openssh/publickey-auth/)

I think I've done that part correctly, but am still missing something important. :confused:

---

### Post by Iowan on 2009-04-27
You realize that "~/.ssh/authorized_keys" is not the same as "/.ssh/authorized_keys"? The tilde (~) refers to the user's home directory - probably meaning "/home/username/.ssh/authorized_keys". Try moving/copying it there to see if it makes a difference.

---

### Post by NJC on 2009-04-27
I didn't notice the difference between the 2 directories (:oops:) but I did check and it is correctly in /home/username/.ssh/authorized_keys

UPDATE: I completely uninstalled openssh client and server, deleted ~/.ssh contents, reinstalled and ran again. Tried a simple ssh connection and ran into known_hosts problem. Deleted contents of known_hosts on Client and FINALLY was able to login. Essentially not having a clue how to ssh, I was trying to use a public key even before I had made a connection.  #-o

Now I'll try to generate a public key and copy to Server for Attempt #12 to make this work. :mrgreen:

---

### Post by NJC on 2009-04-29
Not sure of status, but there might be an associated bug:

[https://bugs.launchpad.net/ubuntu/+source/gnome-keyring/+bug/328127](https://bugs.launchpad.net/ubuntu/+source/gnome-keyring/+bug/328127)

EDIT: I was able to setup keys using instructions here. 

[http://suso.org/docs/shell/ssh.sdf](http://suso.org/docs/shell/ssh.sdf)

---

### Post by NJC on 2009-05-12
Should I be setting up static IP's through router or Ubuntu? My keys don't match because my IP's keep changing on Client and Server.

---

### Post by amenszer on 2009-05-12
Is this is for the ability to ssh without a password prompt?

If so, here is how to do it:

---- 1----
As the user you are going to be running rsync as, and on the machine you will be running rsync on, type: ssh-keygen -t rsa

Follow the prompts and use the defaults for the filenames it gives you. Don't enter in a passphrase, otherwise you will still be prompted for a password when trying to connect.

You should then have two new files in ~/.ssh, id_rsa and id_rsa.pub.

---- 2 ----

Open ~/.ssh/id_rsa.pub and copy the line in it to the ~/.ssh/authorized_keys file on the host you will be connecting to as the user you will be logging in as.

---- 3 ----

Now try it out. Try ssh'ing from the host you created the id_rsa* files on to the one you added a line to the authorized_keys file. You won't be prompted for a password any more.





As far as the dynamic IP problem, you could always register an account with dyndns.org, though I don't think they have an auto-update client for linux. I don't think that will affect your ssh keys...but I'm not 100% sure on that.

Hope this helps.

---

### Post by Jive Turkey on 2009-05-12
> **amenszer said:**
> Is this is for the ability to ssh without a password prompt?

If so, here is how to do it:

---- 1----
As the user you are going to be running rsync as, and on the machine you will be running rsync on, type: ssh-keygen -t rsa

Follow the prompts and use the defaults for the filenames it gives you. Don't enter in a passphrase, otherwise you will still be prompted for a password when trying to connect.

You should then have two new files in ~/.ssh, id_rsa and id_rsa.pub.

---- 2 ----

Open ~/.ssh/id_rsa.pub and copy the line in it to the ~/.ssh/authorized_keys file on the host you will be connecting to as the user you will be logging in as.

---- 3 ----

Now try it out. Try ssh'ing from the host you created the id_rsa* files on to the one you added a line to the authorized_keys file. You won't be prompted for a password any more.





As far as the dynamic IP problem, you could always register an account with dyndns.org, though I don't think they have an auto-update client for linux. I don't think that will affect your ssh keys...but I'm not 100% sure on that.

Hope this helps.
**EDIT:** I've been having the same problem

2 things to add:

1) There is a dyndns updater for linux that will keep a url pointed at your router.  Synaptic finds six of them in the repositories I have activated.
This will only help if you intend to connect from outside the router, and you will still need port forwarding from the router to your ssh server.  

2) If your computers behind the router are always getting different ip addresses from the DHCP server on the router, that will pose big problems for you.  I use address reservation through the clients' MAC addresses being matched to specified ip addresses.  That feature may not be available for your router. If not you will probably need to set up static IPs.  Alternatively, you can configure your server to act as a DHCP server with address reservation, that is a whole can of worms I would avoid.  The advantage to leaving DHCP enabled is that visitors and new computers can access your network without you having to help reconfigure things on their computer and then change them back after.


**EDIT:** I've been having the same problem as the OP so I tried your advice.
Now instead of asking for password it says:" Connection closed by xxx.xxx.xxx.xxx"

---

### Post by Famke on 2009-05-12
Thanks for the info, I appreciate it.

---

### Post by Jive Turkey on 2009-05-12
I discovered that the source of the authentication failure for me was that in copying the key to the host, the two methods I used put extra whitespace into the authorized_keys file.  

The two methods causing problems I used were 
A - copy the key from gedit on the client to the host via ssh & nano on the server
B - having copied id_rsa.pub to the host
```
cat id_rsa.pub >> ~/.ssh/authorized_keys
``` 

I remedied the problem by opening the authorized_keys in gedit, sitting at the host of course, and changing its contents from this:
```
ssh-rsa 
;lahfsd;oan;jnrg;gkldfgiriewp...==
user@client

```
to have it all on one line like this:
```
ssh-rsa ;lahfsd;oan;jnrg;gkldfgiriewp...== user@client
```

my host is CentOS on the server side though.
maybe that will help anyway.

---

### Post by BrianK on 2009-05-12
To be perfectly correct, the stuff in your ~/.ssh dir should not have their execute bit turned on, so they should be 600, not 700.

ssh'ing to a dynamic ip should be no issue whatsoever.  You'll just have a ton of extra garbage in your ~/.ssh/known_hosts file.  Even the fact that you come from a different IP this time than you did last time makes no difference.  You may run into trouble if you're ssh'ing with "-o 'BatchMode yes'" - I'm not sure if you then get the opportunity to confirm that you're sshing to a trusted host (thus copying the host info into the known_hosts file)

double check that your perms on the ~/.ssh directory are 700
double check that the authorized_keys & id_dsa files inside ~/.ssh are 600

This must be true on BOTH MACHINES.  File permissions are very important to ssh & almost always the cause of problems when setting up public key auth.

edited to add:

This is a working conf:
```
akane:~>\ls -ld ~/.ssh/ && \ls -l ~/.ssh/
drwx------ 2 briank cg 95 2009-05-12 16:33 /my_company/users/briank/.ssh/
-rw------- 1 briank cg    602 2008-10-03 19:51 authorized_keys
-rw------- 1 briank cg    672 2008-10-03 19:46 id_dsa
-rw-r--r-- 1 briank cg    602 2008-10-03 19:46 id_dsa.pub
-rw-r--r-- 1 briank cg 205254 2009-05-12 16:33 known_hosts

```

edited again to add:

This is how I do my public key setups:
```
# do this once to generate your keys:
ssh-keygen -t dsa

# distribute keys like so:
cat ~/.ssh/id_dsa.pub | ssh user@server "cat - >> ~/.ssh/authorized_keys && chmod 600 ~/.ssh/authorized_keys"
```

---

### Post by amenszer on 2009-05-13
edit: nm

---

### Post by NJC on 2009-09-22
Update:

Client = Desktop PC Intel E5200 3.08Ghz 
Server = Old Dell PIII

I recently revisited this project and wiped out Ubuntu 9.04 on the Dell and install Ubuntu 9.04 Server edition with SSH and Samba. It was a VERY fast install. I configured the Dell box with a Static IP, router forwarded to port 22 and adduser to add a family member. Family member installed Filezilla and was successfully able to copy a few files after I gave him my public IP. \\:D/

After HOURS and HOURS of fiddling, wailing and gnashing of teeth with public keys and known host files on Ubuntu 9.04 desktop edition, installing the Server edition of Ubuntu was easy. I can't remotely start (unless I config the BIOS) but sudo poweroff shuts it off. But configuring Static IP is a must, otherwise it will funk up the SSH login.

---

### Post by NJC on 2009-10-23
I now want to run a rsync cron job via ssh but need password-free entry. Here are the [steps]("http://suso.org/docs/shell/ssh.sdf"):

```
ssh-keygen -t dsa
``````
scp ~/.ssh/id_dsa.pub username@server:.ssh/authorized_keys
```At which I am denied access to authorized_keys. Hmmm. 

```
chmod 700 ~/.ssh
chmod 600 ~/.ssh/authorized_keys

```After following instructions to remove the following error, I am still getting this (sample)> @@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
[LEFT]   @    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
  @@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
  IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
  Someone could be eavesdropping on you right now (man-in-the-middle attack)!
  It is also possible that the RSA host key has just been changed.
  The fingerprint for the RSA key sent by the remote host is
  23:00:20:83:de:02:95:f1:e3:34:be:57:3f:cf:2c:e7.
  Please contact your system administrator.
  Add correct host key in /home/xahria/.ssh/known_hosts to get rid of this message.
  Offending key in /home/xahria/.ssh/known_hosts:8
  RSA host key for localhost has changed and you have requested strict checking.
  Host key verification failed.
[/LEFT]
[LEFT]
](*,)

I have deleted known_hosts file but same error occurs. I have re-installed the Server so that could be the root of problem but how to reset it all? This is strictly LAN SSH.
[/LEFT]

---

### Post by NJC on 2010-11-11
Hi all - an update. FINALLY I can access my Ubuntu Server via passwordless SSH. The bad news is that I have no idea what changed; good news is it's fixed. Yay. 
> ssh user@192.168.1.101
Linux ubuntu-server 2.6.32-24-generic-pae #43-Ubuntu SMP Thu Sep 16 15:30:27 UTC 2010 i686 GNU/Linux
Ubuntu 10.04.1 LTS

Welcome to Ubuntu!
 
```
System information as of Thu Nov 11 16:33:00 PST 2010

  System load:  0.83                Processes:           90
  Usage of /:   15.5% of 915.24GB   Users logged in:     0
  Memory usage: 2%                  IP address for lo:   127.0.0.1
  Swap usage:   0%                  IP address for eth0: 192.168.1.101
  Temperature:  77 C
```
I upgraded my Desktop to 10.10, and reinstalled Ubuntu 10.04LTS Server to a 1TB Western Digital drive. I followed all of the same steps to create keys, copy them to Server - blah blah blah - and now it magically works. I am using a Rsync script to backup my files, but don't have the scripting/cron part working.

---

### Post by NJC on 2010-11-17
I hope this can help others. Just as magically as SSH starting working sans password, it also magically recently disappeared. 

 Some more fraggin about with key generation, deleting known_hosts, ad nauseam ... finally found the problem to be **Server** directory permissions. But it's unknown why these permissions changed.
```
chmod go-w ~/
chmod 700 ~/.ssh
chmod 600 ~/.ssh/authorized_keys
```[https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)

Which changed the following:

**drwxrwxrwx** 23 user user   4096 2010-11-16 23:26 .

to 

**drwxr-xr-x** 23 user user   4096 2010-11-16 23:26 .

---

