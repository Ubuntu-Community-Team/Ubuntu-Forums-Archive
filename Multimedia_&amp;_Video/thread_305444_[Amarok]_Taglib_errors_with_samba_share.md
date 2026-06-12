---
title: "[Amarok] Taglib errors with samba share"
date: 2006-11-23
forum: Multimedia &amp; Video
---

### Post by ThArGos on 2006-11-23
Hi,

I know that this problem has been discussed from some time now but I can't manage Amarok to build its collection fine.

I'm using Amarok 1.4.4 on a kubuntu edgy that I've recently installed.

I haven't got any .rm files in my directories.

My music is shared on a debian server with samba.

So like everybody, the problem is that Amarok sends me an error message during the build of my collection telling that there are too many errors and that I should reinstall TagLib.

Well I tried that without any success.

Reading forums I found that link :
[http://amarok.kde.org/amarokwiki/index.php?title=Samba&redirect=no](http://amarok.kde.org/amarokwiki/index.php?title=Samba&redirect=no)

which seems to give the solution to my problem.

so I mounted the share in order to have writable access (because I want to be able to change my mp3 tags via amarok).

Well I still have the same errors. So I figure it's because I'm quite a newbie and that I don't masterise at mount+samba.

This is what I have done:
On the server :
I have a user named *musicrec*. This user has read/write access to the music directory and is the owner too.

> [tigrou:musicrec]~/musique$ ll
drwxr-xr-x  11 musicrec      500  4096 2006-08-08 15:19 00 - Divers
drwxr-xr-x   8 musicrec      500  4096 2006-08-08 15:21 80ies
drwxr-xr-x  13 musicrec      500  4096 2006-08-08 15:25 ambient
.
.
.

On the client :
I have a user named *thargos*. According to what I have read on the amarok wiki page, I must have the same rights as *musicrec*.
So I mounted my directory this way:

> sudo mount -t smbfs -o username=musicrec,fmask=644,dmask=755,iocharset=utf8,uid=thargos,gid=thargos //192.168.0.1/musicrec /mnt/musique


(I tried iocharset=iso8859-1 too)

Well I finally have read/write access to the directory and am the owner too:

> thargos@thargos-desktop:~/musique$ ll
drwxr-xr-x 1 thargos thargos 4096 2006-08-08 16:19 00 - Divers
drwxr-xr-x 1 thargos thargos 4096 2006-08-08 16:21 80ies
drwxr-xr-x 1 thargos thargos 4096 2006-08-08 16:25 ambient
.
.
.

But it seems I have made something wrong because I still have the sames errors :(

Can anybody help me on this? Am I mounting or sharing everything right?

I heard something about *character set = ISO8859-1* to add into smb.conf. I may try this tonight but I am quite sceptic about that.

Well thank you in advance for any help you could bring to me.

P.S.: before using kubuntu, I was using mandriva one with an older version of amarok and everything was running fine.

---

### Post by ThArGos on 2006-11-24
Well I added *character set = ISO8859-1* yesterday to smb.conf on the server but I didn't notice any changes :(

Any idea?

---

### Post by koshari on 2006-11-29
try using cifs in the fstab line instread of smb, this worked for me, heres my line, 

```
//192.168.0.8/bigmutha /mnt/shared cifs auto,user,username=<placeYourUserNameHere>,workgroup=workgroup,password=<placeYourPWhere>,uid=500,gid=500,file_mode=0777,dir_mode=0777,rw 0 0
```

btw i had to make the share have write access or the scanner barfed.

let me know how you went,

---

