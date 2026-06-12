---
title: "can not move nfs mounted file to trash"
date: 2012-06-04
forum: Networking &amp; Wireless
---

### Post by sd@ksu on 2012-06-04
I have one nfs mounted filesystem from a remote computer on the local machine as below:
```
mount -t nfs -o nfsvers=3,_netdev,rw,suid,dev,intr,exec  $SERVERMOUNT $LOCALSERVERMOUNT &>/dev/null
```
where SERVERMOUNT is exported from the server and LOCALSERVERMOUNT is the mount point. The filesystem has been working fine. No problem with that.
Problem is if I want to delete a file from LOCALSERVERMOUNT by hitting delete (i.e., from nautilus). The file can not be moved to trash and has to be has to be deleted permanently. The following prompt will appear: 
[IMG]https://lh5.googleusercontent.com/-mIXvVELgk9c/T8z8rwAt5JI/AAAAAAAAC3c/-ULbmddjxL8/s800/Screenshot.png[/IMG]
.........
Can anyone tell me how to fix this. I want to be able to send files to trash upon deletion from the nfs mount? I think I need to provide the right option to the mount...but do not know which one. Please help.

---

### Post by sd@ksu on 2012-06-04
anyone listening...please...

---

### Post by Empire-Phoenix on 2012-06-04
Actually I never found any kind of netowrk mounted drive in any os, that moves deleted files to trash. AS far as I know they all purge them similary.

---

### Post by sd@ksu on 2012-06-04
there must exist a better solution..

---

### Post by capscrew on 2012-06-05
> **sd@ksu said:**
> there must exist a better solution..
I think there is a solution.  I'll bet the user does not have permission to access to the root of the partition that is mounted. Nautilus will try and make a Trash-nnnn folder (nnnn=UID of the user) there. If the user doesn't have access, then you get what you have.  See [**_[COLOR="Blue"]here[/COLOR]_**]("http://askubuntu.com/questions/69517/how-do-i-use-gnome-trash-for-files-in-different-partition") to implement the solution.  Document your work now  ;-)

Just a thought, I wonder if you have set up group membership for all users correctly that maybe the Nautilus Trash-nnnn would work for all users in the group?

---

### Post by sd@ksu on 2012-06-05
@ capscrew: All users belong to the same group users. and all users have 750 permission. But the filesystem is nfs..reading the link you provided..lets see if this can be done..

---

### Post by capscrew on 2012-06-05
> **sd@ksu said:**
> @ capscrew: All users belong to the same group users.
Does the group user have write rights to the root of the partition?

Edit: When you edit your response, my response might make no sense.  Please add a **Edit** to your additions.

---

### Post by sd@ksu on 2012-06-05
i understand what you are saying and I just tried on the actual machine...but I guess i have to do it on the server ! Will try more in a vmware ubuntu server later...else if u have a solution before me keep it posted..thanks anyways...

---

### Post by sd@ksu on 2012-06-05
no they do not have write right to the root partition..

---

### Post by capscrew on 2012-06-05
> **sd@ksu said:**
> i understand what you are saying and I just tried on the actual machine...but I guess i have to do it on the server ! Will try more in a vmware ubuntu server later...else if u have a solution before me keep it posted..thanks anyways...

The permissions may (or may not) need to be set at mount time.  It depends on what the remote partition formatting is.  This is a local host (where the mount point is) problem.  We're in some murky water here, so you will have to do your own work to test the thought.  It's also a possibility that you can't do this.  :-(

---

### Post by capscrew on 2012-06-05
> **sd@ksu said:**
> no they do not have write right to the root partition..

What are you calling the "root partititon"?  Do you mean / or the *root of the partition *in question?

I'm referring to the root of the mounted file system.

---

### Post by sd@ksu on 2012-06-06
> **capscrew said:**
> What are you calling the "root partititon"?  Do you mean / or the *root of the partition *in question?

I'm referring to the root of the mounted file system.

Yeah I meant the root of the mounted file system.

---

### Post by surfdoc on 2012-07-10
I'd like to re-ignite this discussion (seems to have died).

I have the same problem - in that my mounted nfs drive will not move to trash / rubbish bin. 

There do not seem to be any ownership problems as i was able to manually create a .Trash-1000 folder in the root. However the problem persists.

It would be great to resolve, as my nfs drive is a NAS drive which I wanted to mount seamlessly into ubuntu - and undelete would be useful as all the family are using it.

Cheers

---

### Post by surfdoc on 2012-07-16
Just to add, my NAS drive is a WD mybook live

---

