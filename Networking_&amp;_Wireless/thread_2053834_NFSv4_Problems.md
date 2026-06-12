---
title: "NFSv4 Problems"
date: 2012-09-06
forum: Networking &amp; Wireless
---

### Post by Shihan74 on 2012-09-06
I have simple little home file server, currently running fedora 10 and long in need of being upgraded. So i built a new server using ubuntu 12.04 and it was fine until i tried to get nfs working.

uids and usernames dont match in my home so with fed 10 the way things worked was if i were on my desktop as "testuser" (uid 1000) and fed10 has a "testuser" (uid 500). If i wrote a file to nfs the server would store it as uid 1000, client would see uid 1000 and so everything worked ok (even if the server had no notion of who uid 1000 was) - this still works with 12.04 clients too.

Setting up a test 12.04 server i ran into problems with this. In this setup i have a 12.04 client (boson) and server (silver), testuser on client is uid 1000, on server is uid 500. I create a directory "testdir" as "testuser" on the server, I mount everything in the nfsv4 way so i can get the idmap stuff working, and this is what happens:

Just fyi the domains match in both resolv.conf and idmap.conf

```

Client:

testuser@boson:/silver/testdir$ ls -al
total 8
drwxr-xr-x  2 testuser testuser 4096 2012-09-06 06:34 .
drwxr-xr-x 33 testuser     root 4096 2012-09-06 06:34 ..
testuser@boson:/silver/testdir$ ls -aln
total 8
drwxr-xr-x  2 1000 1000 4096 2012-09-06 06:34 .
drwxr-xr-x 33 1000    0 4096 2012-09-06 06:34 ..

Server:
[root@silver testdir]# ls -al
total 8
drwxr-xr-x  2 testuser testuser 4096 Sep  6 06:34 .
drwxr-xr-x 33 testuser     root 4096 Sep  6 06:34 ..
[root@silver testdir]# ls -aln
total 8
drwxr-xr-x  2 500 500 4096 Sep  6 06:34 .
drwxr-xr-x 33 500   0 4096 Sep  6 06:34 ..


```

Now that looks really awesome, the server sees uid of 500 where the client sees 1000. This is where the joy ends and things start going horribly wrong. I create a file on the client and the uid's get broken:

```

Client:

testuser@boson:/silver/testdir$ touch file
testuser@boson:/silver/testdir$ ls -al
total 8
drwxrwxrwx  2 testuser  testuser 4096 2012-09-06 06:39 .
drwxr-xr-x 33 testuser      root 4096 2012-09-06 06:34 ..
-rw-r--r--  1   nobody   nogroup 0 2012-09-06 06:39 file
testuser@boson:/silver/testdir$ ls -aln
total 8
drwxrwxrwx  2  1000  1000 4096 2012-09-06 06:39 .
drwxr-xr-x 33  1000     0 4096 2012-09-06 06:34 ..
-rw-r--r--  1 65534 65534    0 2012-09-06 06:39 file
testuser@boson:/silver/testdir$ 


Server:

[root@silver testdir]# ls -al
total 8
drwxrwxrwx  2 testuser testuser 4096 Sep  6 06:40 .
drwxr-xr-x 33 testuser     root 4096 Sep  6 06:34 ..
-rw-r--r--  1     1000     1000 0 Sep  6 06:40 file

```

The client creates the file with a uid of 1000 on the server side (clients uid for testuser) then the server ends up sending a nobody uid back to the client (some weird v3/v4 hybrid).

Attempting to shut all this down and go back to a nfs v3 realm (killing of idmap, gss, etc) produces an even worse condition:

```

Client:
testuser@boson:/silver/testdir$ touch file
testuser@boson:/silver/testdir$ ls -la
total 8
drwxrwxrwx  2 4294967294 4294967294 4096 2012-09-06 18:19 .
drwxr-xr-x 33 4294967294 4294967294 4096 2012-09-06 06:34 ..
-rw-r--r--  1 4294967294 4294967294    0 2012-09-06 18:19 file

Server:
[root@silver testdir]# ls -al
total 8
drwxrwxrwx  2 testuser testuser 4096 Sep  6 18:56 .
drwxr-xr-x 33 testuser     root 4096 Sep  6 06:34 ..
-rw-r--r--  1     1000     1000    0 Sep  6 18:53 file

```

Im more then happy to go back to the way things were with v3 where the server just stored and presented the file with whatever uid/gid the client told it to use but i do like the idea of username/groupnames matching if i could get it to work.

I've already bumped up the verbosity of the idmap daemon and i cant really see anything suggesting a problem as such, anyone got a suggestion on how i make a 12.04 server do nfs v3 correctly, or make 12.04 nfsv4 client/server talk correctly (with different uids)?

---

### Post by LewisTM on 2012-09-06
I can replicate this behavior. Seems like even though the server does the UID translation of existing names for existing files, anything being written goes through a classical UID validation process. If the client UID is not present on the server, it gets assigned to user nobody. So the names are not much use. Frankly I have never heard of an NFS server that would rely solely on names, it needs some sort of external service to do the synchronization or mapping of UIDs.

Easiest for you would be to revert to nfs3 and add these parameters to your share in /etc/exports
```
all_squash,anonuid=500,anongid=500
```
That will force all connected users to access the share as if they were UID/GID 500

Cheers!

---

### Post by Shihan74 on 2012-09-07
> **LewisTM said:**
> I can replicate this behavior. Seems like even though the server does the UID translation of existing names for existing files, anything being written goes through a classical UID validation process. If the client UID is not present on the server, it gets assigned to user nobody. So the names are not much use. Frankly I have never heard of an NFS server that would rely solely on names, it needs some sort of external service to do the synchronization or mapping of UIDs.

Easiest for you would be to revert to nfs3 and add these parameters to your share in /etc/exports
```
all_squash,anonuid=500,anongid=500
```
That will force all connected users to access the share as if they were UID/GID 500

Cheers!

Sadly the name translation stuff is one of the things nfsv4 is about (its supposed to match username@domain between client and server and translate the ids in an appropriate way)... it was really designed with kerberos in mind (not a path im going to go down), but its supposed to work in a more general sense as well. Its weird that it only seems to work in one direction, its like the ubuntu 12 client writes as nfsv3, and reads as nfsv4 - very frustrating.

Unfortunately im not the only one connected to it all so squishing it all to one id doesnt really work for me.

Its a pity nfsv4 doesnt seem to be able to work as intended. At this point i think the only option i have is to build an old OS that only does nfsv3 as it wont squash any id's except root (by default). As far as i can tell theres just no way of forcing an nfsv4 server to operate the way an nfsv3 one would.

---

### Post by LewisTM on 2012-09-07
Do you have a reference about what you're saying? Pertaining to NFS4 being designed to do name translation, without LDAP or NIS or anyhting? To do that the server would need access to every client's username-UID pairs, something extremely insecure.

I think what is happening is simpler. When queried, the NFS4 server would provide a list of files with their owner usernames, NOT numerical UIDs. With only that info on hand, the local OS would (when asked with [FONT="Courier New"]ls -aln[/FONT] for instance) happily provide the corresponding local UIDs but those would be meaningless, it's what's on the server side that counts.

Why hide the true UIDs from the client? Security again. By withholding that information, NFS4 would make it harder for clients to spoof the UID and get free access. 

If you want the server to run in version 3 mode, you don't need to install an old OS. Just mount the share with type nfs (not nfs4) and add [FONT="Courier New"]vers=3[/FONT] to your mount options. Also the export line must be in legacy format.

---

### Post by Shihan74 on 2012-09-07
> **LewisTM said:**
> Do you have a reference about what you're saying? Pertaining to NFS4 being designed to do name translation, without LDAP or NIS or anyhting? To do that the server would need access to every client's username-UID pairs, something extremely insecure.


Sure, [https://help.ubuntu.com/community/NFSv4Howto](https://help.ubuntu.com/community/NFSv4Howto) though this is what rpc.idmapd is for (rtm for the rest). So long as the domainnames match if idmapd can match usernames between client and server, it *should* translate them in an appropriate way... see the first post where a uid of 500 on the server is translated to a uid of 1000 on the client? its doing that via the username. Is it insecure? well, no less secure the nfsv3 where the server trusts the client to tell it the uid and will only ever squish root uid/gid. It is something that can tie heavily into kerberos, but not supposed to be exclusively to that (again, see the example above where it translates 500<->1000) 

> **LewisTM said:**
> 
I think what is happening is simpler. When queried, the NFS4 server would provide a list of files with their owner usernames, NOT numerical UIDs. With only that info on hand, the local OS would (when asked with [FONT="Courier New"]ls -aln[/FONT] for instance) happily provide the corresponding local UIDs but those would be meaningless, it's what's on the server side that counts.


Local uids on the client maybe meaningless to the server, but certainly not to the client. But even that being so, the server stored the file i created on the client with the local uid of the client (i.e. not the anonymous)


> **LewisTM said:**
> 
Why hide the true UIDs from the client? Security again. By withholding that information, NFS4 would make it harder for clients to spoof the UID and get free access.


not at all, remote uid's are easily found out just by looking at the logs between client and server... OR if you connect to the server with a client that knows nothing about nfsv4 and rcp.idmapd, server will send the uid's it knows (even though its an nfsv4 server)... 

> **LewisTM said:**
> 
If you want the server to run in version 3 mode, you don't need to install an old OS. Just mount the share with type nfs (not nfs4) and add [FONT="Courier New"]vers=3[/FONT] to your mount options. Also the export line must be in legacy format.


Ahhh that does indeed work, i was missing the vers=3 component of that, thanks.

---

### Post by Shihan74 on 2012-09-14
I've moved this thread back to unsolved because i stumbled onto another strange facet of this problem. Im beginning to believe this is all a bug in the linux version of nfsv4, but if i move (as root on the client, boson) a file that testuser has created into a share on the server, the following occurs:

Client:
```

root@boson:/silver/testdir# mv ~testuser/file .
root@boson:/silver/testdir# ls -al
total 8
drwxr-xr-x 2 testuser testuser 4096 Sep 14 21:42 .
drwxr-xr-x 3 root     root     4096 Sep 14 20:11 ..
-rw-rw-r-- 1 testuser testuser    0 Sep 14 21:41 file
root@boson:/silver/testdir# ls -aln
total 8
drwxr-xr-x 2 1000 1000 4096 Sep 14 21:42 .
drwxr-xr-x 3    0    0 4096 Sep 14 20:11 ..
-rw-rw-r-- 1 1000 1000    0 Sep 14 21:41 file

```

Server:
```

[root@silver testdir]# ls -la
total 8
drwxr-xr-x 2 testuser testuser 4096 Sep 14 21:42 .
drwxr-xr-x 3 root     root     4096 Sep 14 20:11 ..
-rw-rw-r-- 1 testuser testuser    0 Sep 14 21:41 file
[root@silver testdir]# ls -aln
total 8
drwxr-xr-x 2 500 500 4096 Sep 14 21:42 .
drwxr-xr-x 3   0   0 4096 Sep 14 20:11 ..
-rw-rw-r-- 1 500 500    0 Sep 14 21:41 file

```

So, the uid was translated on write, but only when the user is root on the client. Same thing occurs with fedora and centos so i assume this is actually a bug further upstream in the linux nfs implementation.

Also, part of the reason i thought this should work originally was that is how it works with solaris, and when it didnt work with linux i figured "implementation difference", but the above suggests either a bug or a permission problem that I cant seem to nail down.

I get the feeling that what is going on here in the linux world is that when a user tries to write a file to an nfs4 partition as username "testuser", the server sends back something saying "write it as uid 500"... uid 0 (root) is capable of doing such, but uid 1000 is not...

Anyone got any suggestions?

---

### Post by luvshines on 2012-09-18
The problem which you have stated has been nicely described in the following URL
[http://dfusion.com.au/wiki/tiki-index.php?page=Why+NFSv4+UID+mapping+breaks+with+AUTH_UNIX](http://dfusion.com.au/wiki/tiki-index.php?page=Why+NFSv4+UID+mapping+breaks+with+AUTH_UNIX) 

We have been struggling with a similar situation for the past one year. The only solution is to use NFSv3 for now unless both the server and client can refer to the same ID and user/group name mapping source

Are you having trouble with NFSv3 too ?
How are you mounting the nfs share ? Are you sure that you are doing a V3 mount ?

It would be best to switch off NFSv4 if you don't want to use it
[http://andy.delcambre.com/2007/06/25/disabling-nfsv4-on-ubuntu.html](http://andy.delcambre.com/2007/06/25/disabling-nfsv4-on-ubuntu.html)

---

### Post by Shihan74 on 2012-09-20
> **luvshines said:**
> The problem which you have stated has been nicely described in the following URL
[http://dfusion.com.au/wiki/tiki-index.php?page=Why+NFSv4+UID+mapping+breaks+with+AUTH_UNIX](http://dfusion.com.au/wiki/tiki-index.php?page=Why+NFSv4+UID+mapping+breaks+with+AUTH_UNIX) 

We have been struggling with a similar situation for the past one year. The only solution is to use NFSv3 for now unless both the server and client can refer to the same ID and user/group name mapping source

Are you having trouble with NFSv3 too ?
How are you mounting the nfs share ? Are you sure that you are doing a V3 mount ?

It would be best to switch off NFSv4 if you don't want to use it
[http://andy.delcambre.com/2007/06/25/disabling-nfsv4-on-ubuntu.html](http://andy.delcambre.com/2007/06/25/disabling-nfsv4-on-ubuntu.html)

I dropped to NFSv3 after giving up on 4. NFSv3 is fine, but especially in the ubuntu case its a little limiting. Aside from ubuntu itself creating most of its users on the fly, its difficult to keep uid/gid's tracking one another across multiple machines (even when they are the same OS).

I did stumble onto the datafusion site, but i got the feeling the information was a little dated because i dont believe it explains why uid/gid mapping does work when the uid trying to write a file as "testuser" (above) is root

---

