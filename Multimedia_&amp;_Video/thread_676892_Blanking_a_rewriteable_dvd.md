---
title: "Blanking a rewriteable dvd"
date: 2008-01-24
forum: Multimedia &amp; Video
---

### Post by da Wookiee on 2008-01-24
I need help with rewritable dvds.  I'm able to write to them with either k3b or Gnomebaker, but once written to, I can't manage to blank or rewrite them.  The format command just gives an error, and I can't just move the files to trash.  I'm sure I'm missing something simple, but I'd like to know what it is.  

I'm able to blank the same dvds in windows using NTI cd and dvd maker that came with my acer machine.

---

### Post by topic58 on 2008-01-24
dvd+rw-format -blank[=full] /dev/dvd

---

### Post by da Wookiee on 2008-01-25
Tried that, here's what I put in and what i got.


```
mindseye@Alphaone:~$ dvd+rw-format -blank[=full] /dev/dvd
* BD/DVD±RW/-RAM format utility by <appro@fy.chalmers.se>, version 7.0.
* 4.7GB DVD+RW media detected.
- illegal command-line option for this media.
- you have the option to re-run dvd+rw-format with:
  -lead-out  to elicit lead-out relocation for better
             DVD-ROM compatibility, data is not affected;
  -force     to enforce new format (not recommended)
             and wipe the data.

```

Am I still missing something?  Also shouldn't there be a gui way of doing this?  I'm not scared of the command line, but I want to work in the gui as much as I can.

---

### Post by disturbed1 on 2008-01-25
This is the command that works for me

dvd+rw-format -force /dev/sr0

^^ notice the sr0, you may want to check what your actual device is. /dev/dvd never worked for me it might for you ;)

---

