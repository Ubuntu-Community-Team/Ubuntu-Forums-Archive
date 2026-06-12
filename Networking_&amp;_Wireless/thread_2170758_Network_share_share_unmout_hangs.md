---
title: "Network share share unmout hangs"
date: 2013-08-27
forum: Networking &amp; Wireless
---

### Post by Ghoetic on 2013-08-27
Hello all users!

So i've got a couple of questions, that i would be thankful if answered.

Basicly i have set up an ubuntu file sharing network at my work.

We use 3 laptops and a stationary. all 4 computers use 12.04 LTS.
We connect with the laptop wirelessly and the stationary is "hard" wired.
A brief explenation of where i am, i have setup the the server to use samba for sharing, and use the remote desktop viewer to reach it if its needed.

There are a total of 4 maps on the server, 3 maps wich are individual to each laptop to backup the contents of one directory on each laptop. we can call them backup lt1 to 3.
and one directory called "sync" wich will sync every computer with all the contents of each laptop. 

We use Luckybackup to arrange this. thats short version of it.

It is basicly working, just need to iron out some kinks.

Problems encountered:

fstab issue's on laptops

the first round of fstab looked something like this: 

//x.x.x.x/backup(1) //home/user/Public/backup(1) cifs defaults,user=xxx,password=xxx,uid=1000,umask=000,rw 0 0.

worked = okayish. by that i mean if i wasnt connected to the network after some random time it would have a nasty crash to a black screen with a log of some kind of mount.cifs related timeout error or something "lavander". or if i was connected and then lost and regained it would lock the folders, meaning i could enter the directorys but not do anything, no changing or writing files.
but if i stayed withing range it worked kinda flawlessly.


obviously i didnt want do settle for this, so i googled, and in the end i made script for /etc/network/if-up(down).d/wireless-up(down)
and added to fstab "nobootwait,nbauto"

wireless-up basicly looks like this.

#!/bin/sh

sudo mount //x.x.x.x/backup(1)  /home/user/Public/backup(1)
sudo mount //x.x.x.x/sync  /home/user/Public/sync

and wireless-down was basicly the same but with sudo umount <mounted directory>.

So this seems to work flawlessly on mounting, which i find wierd because i didnt give any options "-o" for user and password, so does this read from fstab?

but if i lose my connection, the "drives" still stay on visible, but when it try to enter it basicly hangs the directory, and if i close it and try to open the previous directory like /home, it dosent load up, until after a long while and if i get reconnected it loads the directory quite fast.

this wasnt the case before, does it have to do with the if-down.d script or something else?

and my finishing questions:

Is there any easier way of entirely share files for this purpous?

and is there a safe way for fstab to mount or retry when available without giving me the nasty errors?

and this might not belong in networking but, regular luckybackup (not super user) worked fine the first few times i started it and made crons, but when i start it now i neither see my scheduled jobs and i cant make new, only if enter super user mode, but even then i cant see the old jobs that i scheduled, they arent even there. :S

last notice: i've in total only worked with linux ubuntu since the task was handed to me, which is maby around 4 days, all of my work is mostly learned from the internet.

Thanks in advance!

---

