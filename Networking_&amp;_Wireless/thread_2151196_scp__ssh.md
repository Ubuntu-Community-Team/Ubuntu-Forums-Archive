---
title: "scp / ssh"
date: 2013-06-03
forum: Networking &amp; Wireless
---

### Post by Stephan H on 2013-06-03
Hello Forum,

I tried to copy a few files to another local machine in the network using **cp** and **rsync**.
However, I can't connect. I'm assuming a syntax error.
All examples here [https://help.ubuntu.com/community/SSH/TransferFiles](https://help.ubuntu.com/community/SSH/TransferFiles) don't show where the port number can be inserted. 
So I went ```
scp /folder1/folder2/folder2/file.txt user@192.168.1.123 -p123:/user/folder1/folder2/folder3
``` according to how one connects via ssh but it won't work.
Getting error > ssh: Could not resolve hostname

Where does the port number go?
Had similar problems with **rsync**

Stephan

---

### Post by steeldriver on 2013-06-03
try

```
scp -P123 path/to/file user@192.168.1.123:/path/to/destination
```

NB it's an upper case -P for the port unlike in ssh

---

### Post by Stephan H on 2013-06-04
Thanks.

SCP works!
Now need to get rsync sorted.

enter: 

 ```
rsync ssh --port=123 /path/from/source/file.txt user@192.168.1.123:~/path/to/destination/
```

Getting:

```
ssh: connect to host 192.168.0.69 port 22: Connection refused
rsync: connection unexpectedly closed (0 bytes received so far) [sender]
rsync error: unexplained error (code 255) at io.c(605) [sender=3.0.9]
```

Not sure if this is the same problem though...

Stephan

---

### Post by papibe on 2013-06-04
Hi Stephan H.

You need to use the -e option to tell rsync what ssh options to use. For example:
```
rsync **[COLOR="#FF0000"]-e "ssh -p123"[/COLOR]** /path/from/source/file.txt user@192.168.1.123:~/path/to/destination/
```
Let us know how it goes.
Regards.

---

### Post by Stephan H on 2013-06-10
Yep, that's it! it works.

My code is now ```
rsync -avzb -c -e "ssh -p123" /path/from/source/ user@192.168.1.123:~/path/to/destination
``` to backup the complete "source" folder with all subfolders.


Thanks for all help.

Stephan

PS: It apparently does not make a difference whether there is a / or not behind folder "destination".

---

