---
title: "Download all the files in an http:// folder"
date: 2009-09-17
forum: Networking &amp; Wireless
---

### Post by RealG187 on 2009-09-17
Yahoo! is shutting down Geocities and I need to download all the files in my webfolder there, is there a program that will download all the files there automatically?

[http://forums.fedoraforum.org/showthread.php?p=1266194#post1266194](http://forums.fedoraforum.org/showthread.php?p=1266194#post1266194)

---

### Post by yabbadabbadont on 2009-09-18
wget -m http://<your url here>

Edit: "man wget" for details on how to specify username and password.

---

### Post by RealG187 on 2009-09-18
I typed the command and got a few of the files, but not all of them...

---

### Post by Finalfantasykid on 2009-09-18
I don't think you will be able to accomplish what you want using an http:// address.  You will most likely need a ftp address.

Then you would use...

```
wget -r ftp://user@yourDomain.net --password=yourPassword
```

---

### Post by RealG187 on 2009-09-18
I don't have FTP acess, Yahoo! is being money hungry and only allowing FTP access to people who paid, the thing is I bought my hosting before they decided to shut down Geocities so they don't care about old customers, only new ones.

---

### Post by Finalfantasykid on 2009-09-18
Ok so I tried a couple of things, and it seems you can do what you want using wget, and an http address, however there cannot be an index file inside of the directory, otherwise that is all it will download.  So maybe first download all of your index.html/.htm/.whatever files and then delete them.  Then you should be able to do the "wget -r http://www.yourDomain.net" command.

---

