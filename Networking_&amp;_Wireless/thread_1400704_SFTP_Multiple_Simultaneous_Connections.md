---
title: "SFTP Multiple Simultaneous Connections"
date: 2010-02-07
forum: Networking &amp; Wireless
---

### Post by Eagleon on 2010-02-07
Hi Guys,

I really hope someone could help me with this problem. I've been stuck on this for a month!! 

I am using the sftp command to upload files using a bash script. I use a command such as this:

```
sftp -C -B $BUFFER -R $REQUESTS -oPort=$PORT $USER@$HOST:$PATH <<EOF 
mput $1
EOF
```

Simple enough right? The problem is that it is extremely slow to do it this way... as many of you would know if you have shared server somewhere. I would use scp if remote server supported it, but it doesn't.

Anyway, If any of you have ever used FileZilla, in the Settings, if you go to "Transfers" there is a place where you can set the number of "maximum simultaneous transfers". This feature works wonders with SFTP (and FTP too). It really speeds things up. How do I accomplish this same thing with the sftp command... because I don't want to use a GUI. I don't even mind using FileZilla through the command line if possible... but it does not seem to be possible. 

Please help, I've been stuck on this for a month!!! I've searched everywhere and tried a lot of things with no avail...

---

### Post by apmcd47 on 2010-02-07
LFTP is a scriptable ftp client which supports ftp, http and sftp protocols. I think it can do what you are after. It's in the Ubuntu repositories. See [this link]("http://lftp.yar.ru/") for more info.

Yes, I'm a fan of lftp and will plug it whenever possible:guitar:

Andrew

---

### Post by Eagleon on 2010-02-07
Thank you so much Andrew!! I am reading the man page and already excited about this. Cool!! 

Also, for future reference for others who have this issue... from what I read in the man page, this is probably the way to do it:

 ```
mirror:parallel-transfer-count
```

Where you can specify the number of parallel transfers. Have not tested it yet. Am I on the right track Andrew?

Thanks so much again!!

EDIT: Actually, thats to mirror, not for uploading (doh! -- my bad). Any idea how I can specify the number of transfers allowed? can't seem to find an obvious answer on the man page. Or does it handle this automatically and use the max possible?

---

### Post by apmcd47 on 2010-02-07
I was thinking ```
cmd:parallel
``` but I have never needed this feature.

Good luck, I'm glad you think this is the right tool.

Andrew

---

### Post by Eagleon on 2010-02-07
Thanks again Andrew! Yep, I see what you mean ...

I will play around with this and update this thread with what I find out. :)

---

### Post by Eagleon on 2010-02-07
Well, I just finished running some tests. It works brilliantly. I did not try the 

```
cmd:parallel 
``` 

after all, since from what it seems... I have to set that option in the settings. Unless I misunderstood the man page. I am not sure how to pass that to LFTP. Since this stuff is going into a bash script that I want to distribute, writing stuff in the lftprc file, or lftp.conf would not be an option. So instead, I tried this:

```
mirror --parallel=10 -R
``` 

It does a reverse mirror of all files in my folder (which is what I want) ... I am watching the upload progress, and doing an ls on the remote machine shows that 10 files are being written simultaneously. PERFECT!!!

Thanks Andrew!! You are a life saver!!

One last question though. If I wanted to pass the cmd : parallel without touching the config/settings files, how could I do it? is it possible? Thanks!

---

### Post by apmcd47 on 2010-02-15
> **Eagleon said:**
> 
One last question though. If I wanted to pass the cmd : parallel without touching the config/settings files, how could I do it? is it possible? Thanks!
Sorry, I haven't been checking this for a while.

I think prefixing your lftp command with ```
set cmd:parallel; 
``` should do it. for example:

[PHP]PREFIX_CMD="set cmd:fail-exit yes; set:parallel;"
CMD="(actual lftp command)"
lftp -u user -e "$PREFIX_CMD $CMD quit" sftp://remote.system[/PHP]

Andrew

---

