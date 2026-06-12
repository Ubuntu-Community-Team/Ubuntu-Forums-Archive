---
title: "NFS share permissions problem"
date: 2009-12-16
forum: Networking &amp; Wireless
---

### Post by My Name on 2009-12-16
i seem to have a problem with the permissions on my shared folder.
here is my exports file.
```
/storage    192.168.0.3 (rw,no_root_squash,async)
```

Obviously the folder I want to share is /storage and the ip i want to share to is 192.168.0.3
I can mount the share and view everything in it but I cannot alter/create/delete any files

It should be pretty straight forward as it has been in the past but I'm stumped.

Any ideas?

---

### Post by uniden9 on 2009-12-16
Well the easiest method is to just hardset the user.  For nfs security to work correctly, the user id on host and server have to match. This is almost never the case, as adduser and others normally just auto assign the numeric user id. Bob could have id of 177 on server and 200 on client. Anyways, depending on your security needs, you can have nfs squash all the user matching and hard set the user on the server side.  Most your issues will be server side specific. 

Here is an example of my nfs export.
/_fileserver/fstore1_a       192.168.200.1/255.255.255.255(rw,async,no_subtree_check,insecure,all_squash,anonuid=1002,anongid=1004)

I'm not concerned with security, as this is just a large media pc nfs.  anonuid and anongid set the numeric user group and user id that exist on the server for all connected clients. all_squash means to completely ignore the clients uid and guid and use my anonuid and anongid all the time. If i create a file as anyone on the client, on the server, where the nfs share exists, its set to user id=1002 and group id 1004.  The insecure option has nothing to do with the security override, it just lets me bind nfs to port above 1024. The other options are standard nfs.

I imagine the next question would be, what are my numeric user id and group id.  On the server,
sudo id username

example
sudo id syslog
uid=121(syslog) gid=131(syslog) groups=131(syslog)

Also you have to make sure your user id and group on the server have access to your export folder.  
sudo chown user:group /_fileserver/fstore1_a 

Once you have the server configured, all that is left, is to re export your file system.  

sudo export -a

Hope this helps.

---

### Post by My Name on 2009-12-17
Thanks for the reply.
i'm not too concerned about security, the folder contains movies and music.
I'll give this a pop tonight. maybe I will try with each option one by one and see where that gets me.

thanks again

---

### Post by My Name on 2009-12-17
Actually after reading it a few times I think I understand it better now.
The idea i guess is for anything accessing the nfs will be given a specific user ID and group ID.
And the chown is to make sure the IDs that have been assigned have full read/write access to the files.

Woop woop woop

everyday is a school day...

---

### Post by My Name on 2009-12-17
```
/storage 192.168.0.3(rw,async,no_subtree_check,insecure ,all_squash,anonuid=101,anongid=102)
```
this is my new exports file and i'm getting a syntax error bad option list
sudo id syslog gives
```
uid=101(syslog) gid=102(syslog) groups=102(syslog)
```

am i missing something?

---

### Post by My Name on 2009-12-17
OK i've found the problem, there was a space after insecure

thanks for the help, it worked perfectly

---

### Post by Curtis.Everingham on 2010-03-11
I was having a weird issue where i could transfer small files no problem over NFS, but trying to transfer large directories/files resulted in permissions errors (they were the same files with the same permissions, just transferred in parts or transferred as a whole).

I'm posting this for anyone finding this thread trying to solve a similar problem. 

the solution, suggested above, of adding
> all_squash,anonuid=101,anongid=102
to your exports file (replacing 101 and 102 with whatever your server ID's are) worked for me.

Thanks Uniden

---

### Post by Curtis.Everingham on 2010-03-21
Hmm.... looks like i spoke a little too soon.

I'm now getting permissions errors writing TO the nfs share even with the anonid and anongid set. instead of only large files, now they are apparently random files (all set to mode 777, along with the nfs directory im copying to)

are there permissions settings besides chown, chmod, and the anonid and anongid lines in the exports file?

---

