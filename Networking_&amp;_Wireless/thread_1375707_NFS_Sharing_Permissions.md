---
title: "NFS Sharing Permissions"
date: 2010-01-08
forum: Networking &amp; Wireless
---

### Post by tootlet on 2010-01-08
Greetings.
I have several computers behind a Smoothwall router so I'm not concerned with security of a directory I want to share via nfs with read/write permissions. The directory is called stuff and is in the root not my user home area. I did chown -a username originally so I could read and write to it as username. /etc/exports shares stuff as
/stuff 192.168.1.0/255.255.255.0(rw,async,no_root_squash)
 and hosts.deny and hosts.allow are set up fine. If I'm logged in as my username from any other computer, I have no problems reading and writing to this file as I want. But occasionally I need to access it as read and write as another user name. Doesn't work. I've chmod 777 stuff and chmod a+w stuff. Still can't though I can mount it using other user names.

What I want to do is share this with nfs and have every computer on my network have rw privileges to the directory and all subfolders and files. 

This is definitely user error. I'd be grateful for hints on what to look into. Thanks,
Tom

---

### Post by tootlet on 2010-01-09
Greetings,
I noticed a few people have checked this out but no suggestions. I finally got it to work. My problem was I wasn't using two parts of chmod correctly. (I did say this was most likely user error!) To change the permissions for all subfolders I had to use the reclusive -R. To get it changed so anyone could read, write and execute in the folder stuff I went to the root directory in the terminal and entered:
sudo chmod -R 777 stuff

All was well then and I could utilize the music or videos from my client machines. 

I also tried:
sudo chmod -R o=rwx, u=rwx, g=rwx stuff
which didn't work. Don't know what is messed up with this syntax as I copied it out of _Linux in a Nutshell_. Probably stupid user error again. (I hate that.) Anyway, maybe this will help someone else sometime. 

Cheers!

---

### Post by tootlet on 2010-01-09
Whoops,
Don't want to leave the impressioin that _Linux in a Nutshel_l isn't spot on. It's a great reference, but I don't always have the background needed to get the commands right. Like this time but I did get my problem figured out using this book. 
Tom

---

