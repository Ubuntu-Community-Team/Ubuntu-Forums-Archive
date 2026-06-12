---
title: "how do I ftp files from one ubuntu server to another retaining permissions?"
date: 2010-02-21
forum: Networking &amp; Wireless
---

### Post by gareth40 on 2010-02-21
got two ubutnu servers running side by side, I need to transfer several dir's of files, incl sub dirs to the other server via ftp and retaining the file permissions and dir structure.  both servers have ftp access, im assuming theres an ftp command I use on the destination server to connect to the source server and retrieve the files?  all the files reside in the one dir and need to be copied to the same dir on the destination server.

---

### Post by puppywhacker on 2010-02-21
ftp doesn't support access rights or ownership of files. What you can do is make a tar out of the directory you want to transfer and untar it at the destination, this will preserve ownership if the owner has the same uid on both machines number.

The user-id is mapped to the username in the /etc/passwd file. So here the user puppy has the id 1000 in the group id 1000 (users)
```

sudo grep puppy /etc/passwd
puppy:x:1000:1000:jan,,,:/home/puppy:/bin/bash
```

---

