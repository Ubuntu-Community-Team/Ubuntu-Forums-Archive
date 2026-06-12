---
title: "Please help: half working NFS / weird permissions issue"
date: 2010-06-17
forum: Networking &amp; Wireless
---

### Post by Raimund Eimann on 2010-06-17
Hi,

I've been using NFS on SuSE/openSuSE Linux for 10 years now and know that
UID/GID must match the server to have the same permissions on the NFS
client box.

I've exported ~10 directories on the server. When the client box still ran
openSuSE 11.2, everything was ok.

Recently, I installed the client with Ubuntu 10.04 64 bit, and now NFS is
partly broken, without making any changes to the server:

* I'm running openLDAP to distribute user information, so UIDs and GIDs
are identical on both the client and the server.

* for certain groups, I get permission problems, for others everything is
fine:

  - I have a openLDAP-provided group bbusers which all users belong to.
Home dir perms are <username>:bbusers with either 750 of even 700
permissions on most subdirectoies. No problems here.

  - I have other groups provided by openLDAP called bbpcit_p and
bbpict_r and some directories that use these groups on an NFS export
mounted on the client:

[FONT=Courier New]    raimund@nfsclient:/nfs/p$ l -d Garten Scans
    drwxr-x--- 3 root bbpict_p 36864 2009-09-13 18:46 Garten/
    drwxr-x--- 9 root bbpict_r  4096 2008-12-04 21:36 Scans/
[/FONT]
    Numeric UIDs/GIDs here:

[FONT=Courier New]    raimund@jupiter:/nfs/p$ l -dn Garten Scans
    drwxr-x--- 3 0 1017 36864 2009-09-13 18:46 Garten/
    drwxr-x--- 9 0 1007  4096 2008-12-04 21:36 Scans/
[/FONT]
    I can "cd Scans" without problems, but I can't "cd Garten", I get
"permission denied" If I try the latter. I am a member of both groups:

[FONT=Courier New]    raimund@jupiter:/nfs/p$ id | tr "," "\n" |grep bbpict_
    1007(bbpict_r)
    1017(bbpict_p)
[/FONT]
* I am sure this is an NFS problem, because when I create directories
with the same permissions/groups an a local filesystem, everything works
just fine. When I SSH into the server I can enter the directories just fine
as well.

* If I do a "sg bbict_p", my default group changes from bbusers
(GID=1000) to bbpict_p. After this procedure I can "cd Garten".

* Could it be that the NFS-client somehow ignores higher GIDs? Groups
with GIDs>=1012 seem to suffer from this problem more often, but I haven't
tested them all. Which config file might contain restrictions like this?

I am pretty much out of ideas on this problem. I would *greatly*
appreciate hints on how to solve it. Please, NFS-experts, enlighten me!

Cheers,
Raimund

---

### Post by Raimund Eimann on 2010-06-18
Ok, I found it myself:

rpc.mountd was running without -g on the server (= "--manage-gids"). Added -g, now everything woks just fine.

I have no idea why things work fine with am openSuSE client. I think it's safe to say that the openSuSE clients do not require the '-g' Flag on the server to perform as wanted.

I hope other people that move away from openSuSE and run into the same problem will read this and therefore not have to search as much as I did.

Cheers,
Raimund

---

