---
title: "Please! Need help with openSSH configuration"
date: 2010-01-31
forum: Networking &amp; Wireless
---

### Post by Lemiwinks on 2010-01-31
I have been struggling with this for a while now and have not made any progress. Read through anything I could find but nothing helps. And as an added insult, being an ubuntu rookie, everything is to low level for me(ei. I dont know what their takling about :oops:)

So this is where I am at now:
[LIST]
[*]I installed openSSH
[*]Backed up my sshd_conf file
[*]Disabled password authentication
[*]Enabled key authentication
[*]Changed log level to VERBOSE
[*]Added AllowUsers michael
[*]Saved and restarted openSSH
[*]Checked if it was running (ps -A | grep sshd) and it was
[*]Checked if it was listening for incomming connections(sudo netstat --inet -lpn | grep sshd)
[*]This is where I am stuck right now. It said: *ssh: connect to host localhost port 22: Connection refused*
[/LIST]

I folled the following how to's: [https://help.ubuntu.com/9.04/serverguide/C/openssh-server.html]("https://help.ubuntu.com/9.04/serverguide/C/openssh-server.html")   [https://help.ubuntu.com/community/SSH/OpenSSH/Configuring]("https://help.ubuntu.com/community/SSH/OpenSSH/Configuring")

So what did I miss? Any help would be appreciated!

---

### Post by puppywhacker on 2010-01-31
Firewalls will do that to you.

"connection refused" indicates that the TCP could not establish connections, since you say you checked if ssh was listening to port 22 already it must be a network problem

Check if you can ssh into your ssh server from the local system first.

Then also use "ssh -v" to get the verbose information from your ssh client

---

### Post by wojox on 2010-01-31
> 
# Disabled password authentication
# Enabled key authentication


Did you add your key?

---

### Post by Lemiwinks on 2010-01-31
@puppywhacker: thanks for the swift response. I did the (sudo netstat --inet -lpn | grep sshd) from the local machine(our new home server. BTW the rest of the PC on our home network are windows PC's)

I have not enabled any port forwarding on the router.Although I doubt that it should pose a problem because I am attemping to connect from the server to the server, but could that be it?

---

### Post by Lemiwinks on 2010-01-31
> **wojox said:**
> Did you add your key?

hmm... #-o doh! No I did not... 

Ok, so a quick Q about that. How do I choose a username for the key? Since the RSA key synopsis is: <ssh-rsa or ssh-dsa> <really long string of nonsense> <username>@<host>

I dont really get the <username>@<host> part. How is the <username> part determined or chosen and how is the <host> part determined or chosen?

Thanks for the help. Feels I'm not stuck in a rut anymore

---

### Post by Brandon Williams on 2010-01-31
The username@host part doesn't really matter. It will be your username on the local machine (where the key is created) and hostname on the local machine. It does not limit your ability to move the key around or use it from other machines/user accounts.

---

### Post by Lemiwinks on 2010-01-31
> **Brandon Williams said:**
> The username@host part doesn't really matter. It will be your username on the local machine (where the key is created) and hostname on the local machine. It does not limit your ability to move the key around or use it from other machines/user accounts.

Oh, ok. So the username that is generated will not be needed to log in from another PC?

So I generated an RSA key and tried *sudo netstat --inet -lpn | grep sshd* again from the local machine, but I still get denied... Any other suggestions? Should I post my sshd_conf file?

---

### Post by wojox on 2010-01-31
You transfer the ssh key by 

```
ssh-copy-id <username>@<host>
```

but you got to ahead and disabled password authentication, so it may not work. Never tried. 

[OpenSSH Keys]("https://help.ubuntu.com/community/SSH/OpenSSH/Keys#Public%20and%20Private%20Keys")

---

### Post by Lemiwinks on 2010-01-31
Ok, now I am totally confused...

I followed the above mentioned how to's and that seemed to mislead me. Would it be possible for someone to give me a step by step procedure that I can follow to setup my SSH server? It can be vague, I don't mind. I can search for the details myself.

PS ssh-copy-id <username>@<host> did not work(ssh: connect to host linserv port 22: Connection refused)

Thanks for all the help and guidance everyone!

---

### Post by puppywhacker on 2010-01-31
I think this is the cleanest howto for public key ssh

[https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)

---

