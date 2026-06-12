---
title: "NFS - want to squash everyone but root"
date: 2010-06-15
forum: Networking &amp; Wireless
---

### Post by GH68 on 2010-06-15
I found an old (archived) post that asks exactly the same question as I have, how to combine all_squash and no_root_squash to have all non-root users squash to a specific group and user id but have root mapped to root:
[http://ubuntuforums.org/showthread.php?t=681218&highlight=nfs+squash+root]("http://ubuntuforums.org/showthread.php?t=681218&highlight=nfs+squash+root")

There is an explanation in that thread why it doesn't work, but this leaves my problem unresolved. I want to achieve the following: I have my back-up on an NFS server and I want root (through cron) to copy all the directories and files to this back-up share keeping all ownerships and permissions. This would be allowed by no_root_squash. I don't want anyone else to have write permissions even to their own back-up files, in order not to destroy their own back-up files, and thus my intention was to squash them to another user on the NFS server who obviously wouldn't have write permissions for these files. I'm greatful for any hints on how to achieve this, thanks!

---

