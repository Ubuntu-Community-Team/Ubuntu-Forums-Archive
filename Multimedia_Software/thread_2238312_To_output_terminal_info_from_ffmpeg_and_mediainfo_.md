---
title: "To output terminal info from ffmpeg and mediainfo to a textfile easily"
date: 2014-08-07
forum: Multimedia Software
---

### Post by shantiq on 2014-08-07
**ffmpeg** 

log from terminal


```
{ echo time ffmpeg -i [rest of command]; time ffmpeg -i [rest of command]; } 2>&1 | tee ffmpeg.txt



```


**Mediainfo   **&#8203;all files in a folder


```
{ echo mediainfo *; mediainfo *; } 2>&1 | tee mediainfo.txt



```

NB: { echo cmd; cmd; } means the command is kept in the txt file ; without this it is not printed
also use tee -a to append if file already exists


PS and if anyone knows a shorter less cumbersome route please indicate :)  thanx

---

