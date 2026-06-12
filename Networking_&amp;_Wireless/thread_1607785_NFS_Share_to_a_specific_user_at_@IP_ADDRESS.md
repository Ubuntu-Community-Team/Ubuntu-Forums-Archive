---
title: "NFS Share to a specific user at @IP_ADDRESS"
date: 2010-10-28
forum: Networking &amp; Wireless
---

### Post by csharpplus on 2010-10-28
I am a newbie, so thanks in advance for any help.

I would like to have one user only (named **allowed_user**) from machine that has a static IP of **IP1**, to be able to _**write to a folder**_ named **target_folder** on a machine that has a static IP of **IP2**  (meaning, this user is allowed to create new files in this target folder), YET, I'd like to also _prevent from this user_ (**allowed_user**) to delete files in **target_folder**. meaning, the user is allowed to create any files but not delete existing ones.

Is there a way to achieve this?

---

### Post by SeijiSensei on 2010-10-28
Use the "sticky bit":

[http://linuxdevcenter.com/pub/a/linux/lpt/22_06.html](http://linuxdevcenter.com/pub/a/linux/lpt/22_06.html)

```
chmod 1777 /path/to/directory
```

sets the sticky bit on a world-writable directory.

---

### Post by csharpplus on 2010-10-28
_[]("http://ubuntuforums.org/member.php?u=698195")_SeijiSensei,

Thanks for your help.

Will this prevent from 'allowed_user' to also delete files that he had created earlier?

---

### Post by SeijiSensei on 2010-10-28
I don't know.  I know it prevents susie from deleting bill's files.  I don't think I'm prohibited from deleting files I create in /tmp, though, and that uses the sticky bit.  You can mark a file "immutable" on an ext filesystem by using "sudo chattr +i /path/to/file" but you have to be root to do that. ("man chattr" for details.)

If you're worried about keeping an audit trail, you could always set up rsync to make a snapshot of /tmp every minute or two.

---

### Post by csharpplus on 2010-10-28
Great, thanks!

---

