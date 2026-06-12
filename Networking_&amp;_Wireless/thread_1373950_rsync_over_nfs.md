---
title: "rsync over nfs"
date: 2010-01-06
forum: Networking &amp; Wireless
---

### Post by Romualdou on 2010-01-06
Hi,

I wrote a rsync script to backup my laptop data on my desktop. The script tries to mount a directory from the desktop, checks that is is properly mounted and starts rsync to backup my laptop home directory on the desktop.

This worked fine when I tested it on small amount of data. But as soon as I run it to backup a bigger directory, rsync will hang after around 60Mb of data uploaded. 

dmesg reports nfs timeout on the laptop. From that point onwards, the network does not work anymore. A new nfs timeout comes in dmesg every 20 seconds. No ping, no web surfing. I can still disconnect and reconnect using network manager, this will report proper connection, but in reality no connection works.

I eventually had a full system hang when rebooting...

I googled and found few similar cases, people telling this could be related to some specific network cards not managing "big ammount of data", but no clear solution found so far.

I changed mount option for the NFS directory to "soft" and icreased timeo from 14 to 24. No idea if that could be the right idea, but in all cases it didn't work so far...

Any suggestions ?

---

### Post by Romualdou on 2010-01-11
In the mean time, I changed rsize parameter down to 1024. It seems to increase the data quantity that can be transferred before hanging from 60Mb to around 300MB ?

Any clue ?

---

### Post by Lars Noodén on 2010-01-11
No guess yet.  Has running sync in verbose mode (**--verbose**)offered any clues as to what it is doing when it hangs?  How about watching the transfer rates and then limiting rsync to a lower transfer rate (**--bwlimit**) ?

If you have access to the nfs server, you could try running that in verbose mode in the shell and not letting it detach to daemon so as to be able to see the messages.

---

### Post by Romualdou on 2010-01-15
Last running rsync was enough to finish my 1Go backup. So as I'm now just updating the backup with the data added / modified, I don't have volume issues anymore.  The root problem is not solved yet but I have no time to spend on this for the moment. 

If I have to backup more big data this way so that it becomes a problem again I will try your suggestions. 

Thanks for the support anyway.

---

