---
title: "GRsync Error! Host key verification failed..."
date: 2011-01-06
forum: Networking &amp; Wireless
---

### Post by Rytron on 2011-01-06
Hi.

I can connect to Linux Mint 10 Laptop from Ubuntu 10.10 Desktop via Nautilus, File, Connect to Server and SSH. Both machines can ping each other. But I cannot use grsync between Desktop to Laptop. It wont accept the password for laptop (even though I am typing it in correctly). I disabled all firewalls for this task.

I first get this message (I put in xx for security reasons):
```
The authenticity of host '192.168.1.11 (192.168.1.11)' can't be established.
RSA key fingerprint is 57:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:2f.
Are you sure you want to continue connecting (yes/no)? 
```

I type in yes
Then I get this error when I run grsync:

```
*** Launching RSYNC command (simulation mode):
rsync -r -n -t -v --progress --delete -l --exclude-from=/home/rytron/Documents/I.T_General/I.T_GL/Networking/Synchronisation/GRsync/GRsync(Desktop-Laptop)Exclude-List.txt /home/rytron/ 192.168.1.11:/home/rytron/

Host key verification failed.

rsync: connection unexpectedly closed (0 bytes received so far) [sender]
rsync error: unexplained error (code 255) at io.c(601) [sender=3.0.7]
Rsync process exit status: 255
```

I have deleted the .ssh folder on my desktop but that did not solve this. There is no .ssh folder on my laptop home directory.

:confused:

---

### Post by Rytron on 2011-01-12
There must be some bug with Grsynsc. I tried rsync in the terminal and there was no problem.

```
rsync -aP --del --exclude-from=/home/rytron/Exclude-List.txt ~ 192.168.1.11:/home/
```

---

### Post by Rytron on 2011-01-18
How can I make an alias from this:
```
rsync -aP --del --exclude-from=/home/rytron/GRsync\(Desktop-Laptop\)Exclude-List.txt ~ 192.168.1.11:/home/
```

I am unsure as to where to put the ' and " etc.

```
alias dplp='rsync -aP --del --exclude-from=/home/rytron/GRsync\(Desktop-Laptop\)Exclude-List.txt ~ 192.168.1.11:/home/'
```

How can I exclude deep directories with Rsync? I can put a file/folder such as in Exclude-List.txt
Ubuntu One
eduke32.log

How can I get rsync to recognise [COLOR="Indigo"]/home/rytron/Documents/Wallpaper/[/COLOR] in Exclude-List.txt?

---

