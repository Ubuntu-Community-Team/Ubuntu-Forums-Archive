---
title: "How do I unshare a folder with samba?"
date: 2009-02-24
forum: Networking &amp; Wireless
---

### Post by hurtstotalktoyou on 2009-02-24
So I shared a folder in samba, and it works great.  But now I'd like to un-share it.

How in the world do I do that?  It seems like it should be simple, but apparently it isn't.

I tried browsing the /etc/samba/smb.conf file, as suggested in other threads on this subject, but none of my shares are listed there.

Any help would be much appreciated.

EDIT:  Solved.  It turns out I needed to edit the /var/lib/samba/usershares directory.

---

### Post by howefield on 2009-02-24
How about using nautilus to navigate to the folder, right click on it and select sharing options. Set or unset as required.

---

### Post by hurtstotalktoyou on 2009-02-24
> **howefield said:**
> How about using nautilus to navigate to the folder, right click on it and select sharing options. Set or unset as required.

Thanks for the suggestion, but I have already tried it.  When I use nautilus, the box for sharing is unchecked, as if it were not shared (even though it is).  If I check the box, it gives me the option to create a share name for it (even though it is already shared and thus already has a share name).  I actually tried this, and it just creates a duplicate share.  Which means that now I have two shares I want to get rid of.

---

### Post by Iowan on 2009-02-24
Seems like Samba files are kept in a different place, now.  See if [this]("http://ubuntuforums.org/showpost.php?p=6462196&postcount=3") is still valid.

---

### Post by hurtstotalktoyou on 2009-02-24
> **Iowan said:**
> Seems like Samba files are kept in a different place, now.  See if [this]("http://ubuntuforums.org/showpost.php?p=6462196&postcount=3") is still valid.

That's it!

/var/lib/samba/usershares

Thanks!

---

### Post by michelkogan on 2009-10-09
thanks, this helped me too :guitar:

---

### Post by Major_Kong on 2010-01-07
Is there a 'ticket' for this nautilus bug ?

---

### Post by Iowan on 2010-01-07
I'm not sure it's a bug - I suspect it's intentional, but it IS a bit inconvenient sometimes.

---

### Post by linxmty on 2011-09-04
The sharing options are disabled (got greyed out) when you rename a previously shared folder, so apparently there is no way to unshare it unless you rename it exactly as it was... but if you 

1) Right click and select Properties
2) Click on Permissions
3) Uncheck the executable option and apply the permissions

*Orale ! *(this is an spanish exclamation),  the sharing mark magically disappears and the folder is no longer shared. :)

I found and test this trick a couple of times, and also "mas seguro mas marra'o" deleted some files under 

/var/lib/samba/usershares 

corresponding to other folders I didn't want to share any more.

---

### Post by Iowan on 2011-09-04
Closed.

From the [Code of Conduct]("http://ubuntuforums.org/index.php?page=policy"):
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

