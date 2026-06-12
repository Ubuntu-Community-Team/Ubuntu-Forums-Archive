---
title: "Sharing preferences reset when computer is restarted"
date: 2012-12-16
forum: Networking &amp; Wireless
---

### Post by triglyph on 2012-12-16
I have set up an Ubuntu 12.04 computer to serve as a file server for both Mac and Windows machines. It works great but file sharing has to be reset every time I restart the computer (this is not a file server that will be left on at all times).

The #1 problem is that when I set Folder Sharing privileges in Properties, those preferences disappear when I restart and I have to enter them all over again. I have them set up as NTFS so they are accessible from the Mac (which is Lion).

When all the permissions are set, networking works fine, but I need to learn how to make these selections permanent.

Also, it seems that sometimes, the Mac can't see the server drives until they are open. Is this normal?

Any suggestions?

---

### Post by Morbius1 on 2012-12-16
> The #1 problem is that when I set Folder Sharing privileges in  Properties, those preferences disappear when I restart and I have to  enter them all over again.I'm guessing this is a Samba question. The next time you restart run the following command to see if it really has to be shared again:
```
net usershare info --long
```Once you set this up it shouldn&#8217;t just disappear. There was a bug some years ago where the sharing properties diaglog showed it to be not shared but was in fact shared. The net usershare .. command will tell you the facts.
> I have them set up as NTFS so they are accessible from the Mac (which is Lion).I don't know what that means. Samba hides the file format from the remote user so it doesn't matter what filesystem is being used.
> Also, it seems that sometimes, the Mac can't see the server drives until they are open. Is this normal?That question has me stumped. What do you mean by open? You have to have these partitions mounted for them to be shared. If they are not mounted then you can't access them locally either. So if the question is do they need to be mounted first the answer is yes and that's normal.

---

