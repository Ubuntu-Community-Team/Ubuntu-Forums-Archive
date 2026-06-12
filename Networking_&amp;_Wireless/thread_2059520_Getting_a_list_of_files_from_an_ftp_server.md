---
title: "Getting a list of files from an ftp server"
date: 2012-09-18
forum: Networking &amp; Wireless
---

### Post by texpat on 2012-09-18
Hi all,

This is what I did:

```
ftp> **ls > filelist.txt**
ftp> output to local-file: filelist.txt? **y**
200 PORT command successful
150 Opening ASCII mode data connection for file list
450 >: No such file or directory
ftp> 
```
(emphasis mine to highlight user input)

This creates a local file filelist.txt but its empty.

Thanks for reading. I'd appreciate any help with this.

---

### Post by SlugSlug on 2012-09-18
does ```
ls 
```display the list as expected?

---

### Post by SlugSlug on 2012-09-18
```
 ls . filelist.txt
```

---

### Post by texpat on 2012-09-18
> **SlugSlug said:**
> ```
 ls . filelist.txt
```

That did it. Thanks!

---

### Post by wilnotdie on 2012-09-26
That works good. How would I go about getting a list of only the file names?

I tried

```
ls -m1 . /list.txt
```

but doesn't work.  Just says 

usage: ls remote-directory local-file

by itself it gives me the correct output.

---

