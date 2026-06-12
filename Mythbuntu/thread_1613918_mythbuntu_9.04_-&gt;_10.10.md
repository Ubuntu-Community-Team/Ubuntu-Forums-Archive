---
title: "mythbuntu 9.04 -&gt; 10.10"
date: 2010-11-05
forum: Mythbuntu
---

### Post by drjenk on 2010-11-05
Hi,
I'm planning on upgrading to 10.10 soon.  I have read it is preferable to do a clean install due to it being preferable to use ext3?  (or ext4?)

So I'm going to follow the procedure to backup my database while performing a clean install, provided here:
[http://www.mythbuntu.org/upgrading](http://www.mythbuntu.org/upgrading)

But am I correct that, if I want to also preserve my recordings, I need to copy all the .nuv files off somewhere prior to this procedure, then copy them back to the recordings directory afterward?  It seems like if I am backing up my database, which has data about the recordings, I'd also need to preserve the actual recordings at some point, unless I'm missing something.

Thanks

---

### Post by scottishnarn on 2010-11-05
Yes, you do. 

Most people (or at least I do and it's recommended in the MythTV documentation somewhere) have a separate partition with the recordings on it. In this case you just need to mount the partition to the same place.

---

### Post by drjenk on 2010-11-06
Ya I do have them in a different partition from the OS, I just went with the defaults when installing 9.04.  I assume when I install 10.10 it will make the same partition for the recordings in the same place on the same drive, at least hopefully it will.   Thanks for the input.

David J.

---

### Post by fatmonk on 2010-11-09
Hi David,

Have you taken the plunge yet?

I'd be interested to know how you get on as I'm about to do an 810 to 10.10 upgrade.

I've actually started a thread to compile answers about upgrading from 8.10 to 10.10 so that there is a 'one-stop' thread for anyone considering the same..

-FM

---

