---
title: "mythexport 1.0.4 and multiple backends"
date: 2009-05-10
forum: Mythbuntu
---

### Post by 4dognight on 2009-05-10
I'm running mythbuntu/Hardy on 3 BE/FE.
When mythexport runs , it always runs on the MBE, even though the recording is on one of the slaves. It works if the recording is on the MBE, but fails to find the file obviously, when its on one of the slaves. I have the config set, to run on the original host that made the recording. 

Is this supposed to only run on the MBE? 
I have installed mythexport on all of the servers.

Any ideas?

---

### Post by 4dognight on 2009-05-10
Anyone?

I think the problem might be that I have 3 recording directories. One for each  server. Myth will try to balance recordings across the 3 . So even though it might record on server 'B', it might store the rcording on server 'A'.

I would think it shouldnt matter as it can get the server its stored on, from the DB?

Im just speculating here, hoping someone who knows mythexport, might jump in and inform me. :-)

---

### Post by 4dognight on 2009-05-10
OK, I did some diggin into the mythexport code, and determined that,

It doesnt check for the server on which the recording resides.
I can only assume then that mythexport is supposed to be run on the server that contains the recording. Which means the problem lies in Myth not running mythexport on the correct server.

Or, if mythexport is supposed to only run on the master BE, then mythexport needs to check for which server the recording resides  on.

Still need someone to chime in, who is intimate with the workings of mythexport.

BTW, here is my setting from the config which I believe is the one which could control where mythexport should run.

echo 'SELECT * FROM settings s where value = "JobsRunOnRecordHost"'|mysql -umythtv -pmythtv mythconverg 
value	data	hostname
JobsRunOnRecordHost	1	NULL

---

### Post by 4dognight on 2009-05-11
bump

---

### Post by rhpot1991 on 2009-05-12
It will look for the recordings in your storage directories, the issue then comes up if that recording isn't viewable on the current backend running the job.  The easiest thing to do would be to setup NFS shares so each backend can see all the recordings, I like to make them match up so the directory structure is the same on each backend, but as long as they are in a storage directory you should be fine.

---

### Post by 4dognight on 2009-05-12
Let see if I got this right.

I have 3 servers with a /var/lib/mythtv/recordings defined locally now.
So, I am to NFS mount each other 2 servers directory on my MBE  server. Then put all 3 in the storage group.

Say I have servers A,B,C ( A is the MBE)

A will have it's local dir, plus Bs and Cs dir remotely mounted.
Then put each dir into the storage group on A.

 Server A will then record using the 3 dirs.
Not that it should matter. I guess if A then records to one of B's or C's dir, it will be going across the network.

This might fool mythweb's backend status, in thinking it has more disk than actually exists.

I will give this a try. 

Am I correct in assuming then that mythexport will always run on the Master backend?

---

### Post by 4dognight on 2009-05-14
OK, I got this working now.
I ended up mounting each of the other servers drives on all 3 servers.
And then putting them in the storage group on each server.
Mythweb status seemed to figure it out and get the correct free space available, even though each drive is effectively mounted 3 times.

I also noticed mythexport will run on any of the three servers. It seems to get run on the least busy server at the moment.

---

### Post by rhpot1991 on 2009-05-14
> **4dognight said:**
> 
I also noticed mythexport will run on any of the three servers. It seems to get run on the least busy server at the moment.

That is a user job setting, you can access all of these in mythtv-setup.  You can tell it how many jobs a specific backend can run, then whichever backend has a free slot will run the job.

---

