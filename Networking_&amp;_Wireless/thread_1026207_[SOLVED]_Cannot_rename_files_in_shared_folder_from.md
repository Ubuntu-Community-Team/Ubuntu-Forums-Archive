---
title: "[SOLVED] Cannot rename files in shared folder from Vista"
date: 2008-12-30
forum: Networking &amp; Wireless
---

### Post by cab121 on 2008-12-30
hi, new user here.

i have a question regarding Samba (i think).

i have just setup an oldish Acer box running Intrepid to use as a LAMP server as i am making the switch from ASP.Net to PHP.
i am still working off my laptop running Vista and have added the new machine to the same workgroup without issue.

i can open the shared folder (www) on the Ubuntu machine from Vista and add, delete and edit files without issue, but i cannot rename them.

also, if i work from an app like Dreamweaver on Vista, i do not seem to be able to save the files i am editing, or rename them and get messages like...

"\\DEVBOX\www\MFC653C.tmp contains an invalid path"

i can however, delete files and folders from Dreamweaver.

does this sound like an issue with how i have set the shared folder up?

the www folder seems to be shared correctly and the permissions look OK and i am connected to the Ubuntu machine using the root account and password.

thanks in advance for any advice.

---

### Post by cab121 on 2008-12-30
there was nothing wrong with my shared folder, just a Vista issue.
i needed to Disable Offline Caching on the Vista machine which i found out about here: [http://www.scribd.com/doc/2093749/Vista-EnableDisable-offline-files](http://www.scribd.com/doc/2093749/Vista-EnableDisable-offline-files)

---

### Post by Iowan on 2008-12-31
I was about to ask if this one was solved when I saw it in the title of your second post. You can mark the _thread_ [SOLVED] using the option in Thread Tools

---

