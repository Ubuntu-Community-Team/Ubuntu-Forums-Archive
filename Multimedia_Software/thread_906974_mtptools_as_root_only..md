---
title: "mtptools as root only."
date: 2008-09-01
forum: Multimedia Software
---

### Post by dmizer on 2008-09-01
I have a very new Japanese phone (P905i). This phone has a decent (though restrictive) music player, as well as the ability to play qvga movies in wmv format.

Currently I am able to upload music and movies to the phone by CLI with the following command:
```
sudo mtp-connect --sendfile filename.wma,Music
```
where "Music" is an existing folder on the phone. (unfortunately the phone only supports wma, rather than mp3)

Obviously this is quite tedious because mtp-connect doesn't seem to support wild cards which means that I have to manually upload every single file. So, I'd like something significantly more user friendly. I think part of the problem is that mtptools only detects my phone if I run it with root permissions.

So, my question is three fold:
1) How do I get Amarok (or Rhythmbox, or any sync software) to connect to my phone without opening it as root? I assume I'll have to add myself to some group, but I don't know what it is.
2) How do I configure Amarok (or Rhythmbox, or any sync software) to talk to my phone?
3) Is it possible to configure Amarok (or Rhythmbox, or any sync software) to convert to the necessary format on the fly while the file is uploaded, so I don't have to keep two instances of all my music/movies?

---

### Post by lswb on 2008-09-01
I'm not familiar with mtp-connect, but if it can only handle one filename at a time, try

for file in *.wma ; do mtp-connect $file,Music ; done

probably best to put it in a script and then run it with sudo.

---

### Post by dmizer on 2008-09-01
> **lswb said:**
> I'm not familiar with mtp-connect, but if it can only handle one filename at a time, try

for file in *.wma ; do mtp-connect $file,Music ; done

probably best to put it in a script and then run it with sudo.

Thank you, that's very nearly what I need. I need to escape the spaces in file names. How can that be included in the script?

---

### Post by lswb on 2008-09-01
The safest form for including any spaces or other special characters is like this:

for file in *.wma ; do mtp-connect "${file}",Music ; done

---

### Post by dmizer on 2008-09-02
Unfortunately, this was not successful either. Still reading the spaces as options even if I perform:
```
sudo mtp-connect "file with space.wma",usic
```

The only way I can successfully escape spaces is with this command:
```
sudo mtp-connect file\ with\ space.wma,Music
```

---

### Post by lswb on 2008-09-02
You can pipe the filename through sed, it would be something like this if you want a one-liner:

for file in *.wma ; do mtp-connect $(echo $file|sed 's/\ /\\\ /g'),Music ; done

I can't test this with mtp-connect since it's not installed on my system, but the sed part does substitute "\ " for a plain " " in a file name. Good luck!

---

### Post by dmizer on 2008-09-03
> **lswb said:**
> The safest form for including any spaces or other special characters is like this:

for file in *.wma ; do mtp-connect "${file}",Music ; done

This worked. The previous error was my fault. I forgot a critical element in the original command (I was at work with no references at the time). Here is what ultimately succeeded:
```
for file in *.wma ; do mtp-connect [COLOR="Red"]--sendfile[/COLOR] "${file}",Music ; done
```

#-o

---

