---
title: "a wget command problem"
date: 2010-01-11
forum: Networking &amp; Wireless
---

### Post by replikanxxl on 2010-01-11
i wanted to download a whole folder at an address . its like one of those pages there are folders and files and there are folders and files in those folders and there are files and folders in those folders..... . Wget gets these automated like a Google spider so i read an article and used the command and arguments there . and it was working . 

```
wget -H -r --level=1 -k -p  URL
```

But theres a problem. every folder(or page) also has a link to parent folder(or page). so this command is downloading all the files not just under the folder i want, but also all the files of folders those are above this folder on hierarchy. So in the end it was downloading all on that server. How can we prevent such thing ? is there a way to input the link that should be avoided, as an argument ?:popcorn:

---

### Post by garryknight on 2010-01-11
> **replikanxxl said:**
> But theres a problem. every folder(or page) also has a link to parent folder(or page). so this command is downloading all the files not just under the folder i want, but also all the files of folders those are above this folder on hierarchy.

'man wget' shows that the --no-parent argument can be used here:

"Do not ever ascend to the parent directory when retrieving recursively.  This is a useful option, since it guarantees that only the files below a certain hierarchy will be downloaded."

---

### Post by replikanxxl on 2010-01-11
thank you. I'm so sure this is the answer. I better get familiar with reading manuals

---

