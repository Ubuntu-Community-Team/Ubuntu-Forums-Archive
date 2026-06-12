---
title: "Dual WAN router: SSH, loadbalancing &amp; failover"
date: 2011-11-02
forum: Networking &amp; Wireless
---

### Post by nlz on 2011-11-02
Because I suffer from a very poor connection I've got two internet lines from two ISP's. To use the two lines at the same time I've purchased a dual WAN router (Draytek Vigor 2920n). For browsing it is working fine, but I need to upload and download relative large files (audio content of about 50 MB each) on a daily basis. For this I'm using FTP and SSH because it allows  me to continue where I left if the connection fails.

If connection 1 fails, I've got a failover to connection 2, but this messes up my FTP/SSH session, so I have to login again manually and keep track of the process. Has anyone got a good idea to solve and automate this problem?

Two possible solutions I'm thinking about (even though I don't know exactly how to do it):

1.
a. 
Get SSH certificate on my keyring for the distant server and copy in ~/.ssh (so no need for typing in a password)
b. 
Create a bash script (or maybe rsync can do this) which checks if (1) there is a connection which is uploading a file from folder X to distant server and (2) verifies if the file is not on the server already. 
c. 
If there is no connection, and the file is not present in the distant folder: start copying file to the folder on the distant server 

2.
Create a SSH session between three IP's: my two local IP adresses and the one of the distant server. Problem is that I don't know if I can download 1 file over two connections (like RAID)

---

### Post by nlz on 2011-11-02
If I would go for solution 1, it might look like this:

An executable script send.txt:

```
rsync -e ssh -varuzP [LOCAL FOLDER]  [USER]@[REMOTE SERVER]:[REMOTE FOLDER]
```

And a cronjob running that file every minute.

Problems with this solution:

1. Cron is starting a new process every minute, how can cron check if there is already a process running?

2. I'll probably only be using the bandwith of one connection, whereas I would like to use the bandwith of the two connections.

---

### Post by papibe on 2011-11-02
I'm a little confused by your unusual setup. But here are my thoughts.

IMHO, the best way I know to transfer files over an instable connection is a combination of:
[LIST]
[*]SSH keys to get paswordless connections.
[*]rsync with the --partial option.
[*]A bash script that assumes the connection will drop.
[*]More appropriate TCP options for the ssh connection.
[/LIST]
Take a look at my post (#2) here in this [thread]("http://ubuntuforums.org/showthread.php?t=1861143").

I hope that would give you more ideas,
Regards.

---

### Post by nlz on 2011-11-02
To ensure that the process is not running twice, I could let the cronjob execute the following script:

#!/bin/bash

ps -ef | grep -v grep | grep "rsync" \
> dev/null
if [ $? -ne 0 ]; then
'send.txt'
fi

# End of Script

---

### Post by nlz on 2011-11-02
Thanks papibe!

So the setup I'm looking at now is the following:

1. Exchange SSH keys
2. An executable script 'send.txt':

```
rsync -azivP -e "ssh -o TCPKeepAlive=no -o ServerAliveInterval=40" [LOCAL FOLDER]  [USER]@[REMOTE SERVER]:[REMOTE FOLDER]

```

and everytime I need to send the files I just execute 'send.txt'.

I'll give it a try and report back later on.

> **papibe said:**
> I'm a little confused by your unusual setup. But here are my thoughts.

IMHO, the best way I know to transfer files over an instable connection is a combination of:
[LIST]
[*]SSH keys to get paswordless connections.
[*]rsync with the --partial option.
[*]A bash script that assumes the connection will drop.
[*]More appropriate TCP options for the ssh connection.
[/LIST]
Take a look at my post (#2) here in this [thread]("http://ubuntuforums.org/showthread.php?t=1861143").

I hope that would give you more ideas,
Regards.

---

### Post by papibe on 2011-11-02
I would assume the worst (drop connection) and use and skeleton script like the one I mention in the linked thread:
```
rsync ...
until [ $? = 0 ]
do
    sleep 90
    rsync ...
done
```
Regards.

---

### Post by nlz on 2011-11-03
You're right papibe.
I've made it:


```
#!/bin/bash

rsync -azivP -e "ssh -o TCPKeepAlive=no -o ServerAliveInterval=40" [LOCAL FOLDER]  [USER]@[REMOTE SERVER]:[REMOTE FOLDER]
until [ $? = 0 ]
do
    sleep 60
    rsync -azivP -e "ssh -o TCPKeepAlive=no -o ServerAliveInterval=40" [LOCAL FOLDER]  [USER]@[REMOTE SERVER]:[REMOTE FOLDER]
done
```

And it's working properly! Thanks!

---

