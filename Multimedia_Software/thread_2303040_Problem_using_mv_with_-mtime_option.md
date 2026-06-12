---
title: "Problem using mv with -mtime option"
date: 2015-11-15
forum: Multimedia Software
---

### Post by GwibberFooey on 2015-11-15
I am trying to make a command that moves all files in /sourceFolder that were modified more than 2 days ago to the directory /destinationFolder  . 
When I run the command :
find /sourceFolder -mtime +2 -exec mv "{}" /destinationFolder
then I see the error message:
find: missing argument to `-exec'

---

### Post by TheFu on 2015-11-15
Try
```
find /sourceFolder -mtime +2 -exec mv {} /destinationFolder  \;
```

Yes, the ';' must be escaped.

---

### Post by GwibberFooey on 2015-11-15
Problem solved!

---

