---
title: "Very odd samba share read / write behaviour ?"
date: 2009-09-14
forum: Networking &amp; Wireless
---

### Post by uncle-c on 2009-09-14
Here is the important part of my smb.conf file.

```

[linux-share]

path = /home/share

 valid users = dog cat 
  write list = dog  
;  read list = cat
 read only = yes      
browseable = yes
; guest ok = yes              
; writable = yes
; available = yes


```

```

[unclec@localhost home]$ ls -al
total 24
drwxr-xr-x  5 root   root   4096 2009-09-11 15:38 .
drwxr-xr-x 21 root   root   4096 2009-09-14 08:45 ..

drwx------ 43 unclec unclec 4096 2009-09-14 12:16 unclec
drwxrwx---  2 root   animals  4096 2009-09-14 13:12 share
[unclec@localhost home]$ 


```
Both users dog and cat belong to the group animals.
As you would expect from the above smb.conf dog can read and write to the samba share whereas cat can only read. However, when I change the "write list" line to "write list = cat", cat has write access but so does dog. This is still the case even when I change the "read list " line to " read list = dog" . I can never get the samba share to be read + writeable by cat and read only by dog ?!! Any ideas as to where I may be going wrong ?

regards
uc

---

### Post by swerdna on 2009-09-14
[linux-share]
path = /home/share
read only = no
read list = dog

If you leave it at root:root ownership and chmod it to 777, then cat can write.

For greater security you could add this optional line: valid users = +animals

---

### Post by uncle-c on 2009-09-14
Thanks swerdna,
I do want to avoid giving the share 777 permissions. I've changed the smb.conf to this :

```

valid users = +animals
  
  read list = dog
 read only = no


```

and it seems to have done the trick. It looks as if permissions 770 on the linux-share directory overide the "read only" directive in the smb.conf file.
Thanks for pointing me in the right direction.Unfortunately the oddity still remains unanswered.

SCENARIO A:

(i) If read only = yes and write list = dog
then dog can write and cat cannot.

(ii) If read only = yes  and write list = cat
then dog can write and cat can write  (If the first part is anything to go by then dog should not be able to write ??!)

SCENARIO B:

(i) If read only = no and read list = dog
then dog cannot write and cat can write

(ii) If read only = no and read list = cat
then dog can write and cat cannot

I can understand the results of scenario B , but it is scenario A which confuses me.
To recap permissions on the share directory are 770.

---

### Post by swerdna on 2009-09-14
Scenario A, part (ii) should not occur on the basis of the info you gave. There is a difference between the underlying Linux settings for dog and cat (as evidenced by the different behaviour in Ai and Aii). But I can't imagine what it is. Check their properties carefully in System --> Admin --> Users and Groups, to see if they're identical.

Are they both enrolled in the Samba user database (probably "yes")?
What's in the [global] stanza (although I can't see what could be discriminatory between dog/cat in that)?

A real puzzle!

---

### Post by uncle-c on 2009-09-15
Morning,
Both dog and cat have "animals" as their secondary group, their primary groups being dog and cat respectively. Both have linux accounts on the client machine as well as Samba accounts on the server. Both have their own unique passwords to log into the samba share. The one difference is that even though both have accounts on the Samba server,  dog has a login shell account whereas cat does not have a login shell /account. I have created user cat on the Samba server purely for it to be allowed to have its own Samba password / account and for nothing else. Could this help ?

C

---

### Post by swerdna on 2009-09-15
I just ran "sudo useradd billy" to make a new user with really minimal rights, but that automakes a login shell, and then I added billy to the smbpasswd database. Then billy behaved like all my other remote users, able to access and write shares.

I can only suggest you delete the user and then re-add it using "sudo useradd", conventionally.

---

### Post by uncle-c on 2009-09-15
Alas I used the "useradd" command to add the new user as I do like to avoid the use of GUI as much as possible.
I think I may give it a rest.

---

### Post by swerdna on 2009-09-15
> **uncle-c said:**
> Alas I used the "useradd" command to add the new user as I do like to avoid the use of GUI as much as possible.
I think I may give it a rest.
That could be for the best :wink:

---

