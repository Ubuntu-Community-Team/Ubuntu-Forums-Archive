---
title: "trying to connect MythTV to WD My Cloud with Mythbuntu"
date: 2016-09-02
forum: Mythbuntu
---

### Post by mlapoint on 2016-09-02
Ok, I used to be an ETL programmer, but that was over 10 years ago.  I have only had a little experience with Linux and have decided to try getting into it.

Computer:  Mythbuntu 14.04.12
NAS: WD My Cloud 4 TB

I want to use the My Cloud NAS for my data storage.  I am primarily storing recorded TV and movies.  I have set up the nfs daemon and it works, and I am trying to set up MythTV to connect through nfs to write the recorded television to the My Cloud.  

I need to put in a directory in the exports file that is as follows:
/nfs/shares/Public/Shared Videos/TV/DVR

The problem is the space in between "Shared" and "Videos".  I have tried putting it in like above, I have tried the following:
/nfs/Public/Shared%20Videos/TV/DVR
/nfs/shares/Public/\Shared Videos\/TV/DVR
"/nfs/shares/Public/Shared Videos/TV/DVR"
/nfs/Public/Shared\040Videos/TV/DVR

None of these seems to work.

Can someone please help me?  I am aware that this has been asked before, but I do not know what the answer is and I am not sure if this is the proper forum to put it in either.

Thank You,

Mike

---

### Post by deadflowr on 2016-09-02
I don't see /Share\ Videos/ in the list.

---

### Post by mlapoint on 2016-09-05
I tried adding this to the exports file:
```
/nfs/Public/Shared\ Videos/TV/DVR *(rw,no_all_squash,sync,no_subtree_check,insecure,crossmnt,anonuid=65534,anongid=1000)
```

and received the following error when I tried to restart the My Cloud:
```
exportfs: Invalid IP address Videos/TV/DVR
exportfs: Invalid IP address Videos/TV/DVR
exportfs: Failed to stat /nfs/Public/Shared\: No such file or directory
```

Thank You for the time to help Deadflowr.

Mike

FYI, this is my entire exports file:

```
#/var/lib/mythtv/recordings    *(ro,async,no_root_squash,no_subtree_check)
#/var/lib/mythtv/videos    *(ro,async,no_root_squash,no_subtree_check)
#/var/lib/mythtv/music    *(ro,async,no_root_squash,no_subtree_check)
#/var/lib/mythtv/pictures    *(ro,async,no_root_squash,no_subtree_check)
# Use nobody user (uid 65534) for nfs guest.  This is restricted from private
# shares by ACLs.
#
/nfs/Public *(rw,all_squash,sync,no_subtree_check,insecure,crossmnt,anonuid=65534,anongid=1000)
/nfs/Public/Shared\ Videos/TV/DVR *(rw,no_all_squash,sync,no_subtree_check,insecure,crossmnt,anonuid=65534,anongid=1000)
/nfs/ubu *(rw,no_all_squash,sync,no_subtree_check,insecure,crossmnt,anonuid=65534,anongid=1000)
```

Also, when I run "showhosts -e localhost" on the My Cloud, I get the following:

```
/nfs/ubu            *
/nfs/Public/Shared\ *
/nfs/Public         *
```

---

### Post by mlapoint on 2016-09-06
Oops, I meant:  showmount -e localhost

---

### Post by deadflowr on 2016-09-06
I decided to move this thread to the **Mythbuntu** sub-forum.
Where others who would have better understanding will find it.

---

### Post by uteck on 2016-09-12
It seems the problem is that the WD My Cloud is not parsing the path correctly.  Can you rename 'Shared Videos' to something without the space?
Or try putting in double quotes:
"nfs/Public/Shared Videos/TV/DVR" *(rw,no_all_squash,sync,no_subtree_check,insecure,crossmnt,anonuid=65534,anongid=1000)
But I am not sure how the exports file like that.

---

