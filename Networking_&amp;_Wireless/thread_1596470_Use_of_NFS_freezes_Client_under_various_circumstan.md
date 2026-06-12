---
title: "Use of NFS freezes Client under various circumstances"
date: 2010-10-14
forum: Networking &amp; Wireless
---

### Post by b00nish on 2010-10-14
Hey there

I'm using a Kubuntu 10.10 Client Machine which mounts NFS shares form a Kubuntu 10.04 Server.
The server seems to work smoothly but the client causes huge problems since I upgraded to 10.10 (before I used 8.04 which worked withouth problems).

My problems are, that in various situations the use of the NFS shares causes the Client to freeze completely!

Examples:
Unzipping a big file from the NFS server to the NFS server via the client -> always immediate freeze (after some seconds)
Transfering big files from one NFS folder to another -> mostly immediate freeze (after some seconds)
Viewing a movie which is on the NFS server -> sometimes freeze after variably amounts of time
Letting the Strigi-Indexer index files on the NFS shares -> mostly freeze after a short while

It seems that everything that puts some load (high data transfer) on NFS immediatly locks up the whole client.

Can anyone help?

---

### Post by annoyingrob on 2010-10-14
What sort of options are you passing when connecting to the NFS share? Things like noatime, and I think ioctl are highly recommended to prevent nfs from bogging down. 

On an unrelated note, I have had performance issues like you describe when my server was running bandwidthd on the interface.

---

### Post by b00nish on 2010-10-14
Hi

I'm mounting via fstab as follows:

"rw,users,hard,intr,sync"

(I'm exporting at the server with: "(rw,sync)")

Initially I worked just with 'rw,users (fstab) and 'rw,async'(exports) which worked perfectly on 8.04. When I saw the problems with 10.10 I changed to 'sync' because I heard that would be more safe and added the other options - but it didn't help.

I'll try 'noatime' now and let you know if it works afterwards. What is 'ioctl'? Never heard of this mount option.

However I'm not very confident that changing mount options will help because it's a problem that came with 10.10 and did not occur with the same simple mount options in 8.04.

(Side note: Client and Server are connected via Gigabit Ethernet)

**EDIT:** I tried 'noatime' and almost tought that it worked... some action which usually lead to an instant freeze after some seconds took now a bit longer... but it finally freezed anyway, it just took a bit longer. Maybe a coincidence.

**EDIT 2: ** It also would be helpful if youc could tell me, how to gather more informations on the problem e.g. by enable nfs client logging or such things....

---

### Post by b00nish on 2010-10-14
More detailed infos form /proc/mount:

192.168.1.101:/media/data4 /media/data4 nfs rw,sync,nosuid,nodev,noexec,noatime,nodiratime,vers=3,rsize=262144,wsize=262144,namlen=255,hard,proto=tcp,timeo=600,retrans=2,sec=sys,mountaddr=192.168.1.101,mountvers=3,mountport=51311,mountproto=udp,addr=192.168.1.101 0 0

and those are the old ones from 8.04 which worked (I still have toe old system on dualboot):

192.168.1.101:/media/data4 /media/data4 nfs rw,nosuid,nodev,noexec,vers=3,rsize=262144,wsize=262144,hard,nointr,proto=tcp,timeo=600,retrans=2,sec=sys,addr=192.168.1.101 0 0

Someone sees a relevant difference?

(I already tried set 10.10 to mountproto=tcp since this was a difference i noticed.. didn't help tough)

**EDIT:** During a recent freeze I looked at the system monitoring and noticed that a process called "kondemand/1" caused high cpu usage in the very moment before the crash. I never noticed this process before even it's always there but usually doesn't consume much ressources. Could this be relevant? On the ther hand I read about the function of this process and it doesn't seem to have anything to do with NFS ;)

---

### Post by b00nish on 2010-10-15
*bump*

Any informations how to obtain logs or something would be useful. Thanks!

---

### Post by luvshines on 2010-10-15
They are having some similar discussions here:
[http://ubuntuforums.org/showthread.php?t=1577973](http://ubuntuforums.org/showthread.php?t=1577973)

---

