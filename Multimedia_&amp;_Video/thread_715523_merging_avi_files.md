---
title: "merging avi files"
date: 2008-03-04
forum: Multimedia &amp; Video
---

### Post by Faud on 2008-03-04
Is it possible using Avidemux or Cinelerra to merge two avi files into one ? Is there an instruction guide anywhere ?
Thanks

---

### Post by moephan on 2008-03-05
This thread tells you how to do it with mencoder:
[http://ubuntuforums.org/showthread.php?t=85718](http://ubuntuforums.org/showthread.php?t=85718)

HTH

Cheers, Rick

---

### Post by michaelzap on 2008-03-05
Assuming the two files are the same format, etc, open the first file in Avidemux, then choose Append from the File menu and add the second file. Save with both audio and video set to Copy and you'll have a new merged file. That's it.

---

### Post by Faud on 2008-03-05
Thank you, it worked perfectly

---

### Post by FrankVdb on 2008-03-05
It's far simpler using the command line.

frank@laptop:~$ cat file1.avi file2.avi > newfile.avi

---

### Post by Faud on 2008-03-05
Yea I ended up using the command line and it was great. Never knew that I could do that

---

### Post by moephan on 2008-03-06
> **FrankVdb said:**
> It's far simpler using the command line.

frank@laptop:~$ cat file1.avi file2.avi > newfile.avi

Note that for avi files, that will join the files, but they won't play properly until you've re-indexed:
```

mencoder -forceidx -oac copy -ovc copy infile.avi -o outfile.avi

```

Cheers, Rick

---

