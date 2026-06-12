---
title: "chmod Kdenlive Installation Errors"
date: 2018-08-16
forum: Multimedia Software
---

### Post by martinssm on 2018-08-16
I just wanted to install Kdenlive using it's AppImage file, so I copied the name of the file and used it in a command : chmod a+x kdenlive-18.04.1-x86_64.AppImage This came up : chmod: cannot access 'kdenlive-18.04.1-x86_64.AppImage': No such file or directory

---

### Post by deadflowr on 2018-08-16
Where is the file?
You either need to be in the direct directory it's in, or run the chmod command with the full file path
so either of these
```
cd /the/directory/where/the/file/is
chmod a+x kdenlive-18.04.1-x86_64.AppImage 
or
chmod a+x /the/directory/where/the/file/is/kdenlive-18.04.1-x86_64.AppImage 
```
Replace /the/directory/where/the/file/is with the actual directory it's in, most probably Downloads.
(since Downloads is the default download folder.)

---

### Post by steeldriver on 2018-08-16
Most likely, you issued the command from a different directory than the one containing the file

Less likely, the name is not exactly as you copied it (for example, has hidden characters such as trailing whitespace)

---

