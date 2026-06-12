---
title: "Please help with Secure Copy"
date: 2013-07-12
forum: Networking &amp; Wireless
---

### Post by Jaraxle on 2013-07-12
I'm trying to copy a file using secure copy and I can't find a way to make it work.

I used SSH to connect to remote host and tried to push file to local client and also tried to pull file from local client. Neither way is working. I either get unable to resolve host message, cannot stat file, or connection time out. The name of the file is config.sys and I am using the following format:

scp config.sys [email]jaraxle@localhost:/home/jaraxle/config.sys[/email]

I have also tried to copy file into root directory:

scp config.sys root@localhost:~/

Neither way is working. This is my first time using scp but the instructions seem clear and I don't see what I'm doing wrong.

---

### Post by steeldriver on 2013-07-12
Is the config.sys file in the directory that you're executing the scp command from? If not, you need to give the path to the file as well as a path to the destination (which must be writeable) i.e. from a shell the local machine (NOT ssh'd into the remote machine - scp does that part for you)

```
scp /path/to/config.sys jaraxle@192.168.1.16:/home/jaraxle/config.sys
```

where in this case 192.168.1.16 is the IP of the destination machine - you can use a hostname provided it is resolvable

---

### Post by Jaraxle on 2013-07-12
Forgot to mention that config.sys is in the directory I'm executing scp command from. However, I was trying to push from remote server to client. Using your advice, I'm now executing command from local machine. The file is in the root directory of remote server so I am trying using the following format:

scp ~/config.sys jaraxle@192.168.1.16:/home/jaraxle/config.sys

Host name is not resovable so I am using ip (had tried both before) but getting connection refused on port 22.

I can ping remote host and also ssh into host. Could part of the problem now be the fact that I disable password login on remote host (using authentication keys with same user name as login)? Also disabled root login on server but user account has sudo privileges.

It's really frustrating because I am so close and I know it's something that I'm overlooking. I just installed sshfs command on server and am trying to learn that command to see if that method will work.

---

### Post by CharlesA on 2013-07-12
Why not just use rsync? It supports keys and can be set to function like scp.

---

### Post by steeldriver on 2013-07-12
If you are trying to copy the file FROM the root dir of the remote machine TO the current directory on your local machine, that would be

```
scp jaraxle@192.168.1.16:/config.sys ./
```

---

### Post by Jaraxle on 2013-07-12
That did it. Thanks a lot, steeldriver!

The ending ./ was different than the examples I was using and what I was trying was wrong. I also didn't realize that scp would log in for you (duh!) and to run it *from* the directory where you wanted to place the file. I think that was the main thing I was doing wrong.

Definately showed me that I need to read more about scp and rysnc before I start trying to do too much but I wanted to finish this job and was thrilled when I saw the file copy over! Thanks again to everyone who responded.

---

