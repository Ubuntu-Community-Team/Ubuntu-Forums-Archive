---
title: "/usr/bin/X11 problem"
date: 2010-09-05
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by pulpo69 on 2010-09-05
i did 3 times a fresh beta install (alternate cd 64bit), my display is strange, because it shows a part of the screen the rest is hidden behind the
frame of the monitor, but the resolution is correct.
/usr/bin/X11 says link to folder, but inside this is 1347 times another another folder saying link to folder.
very strange.

---

### Post by SevenMachines on 2010-09-05
/usr/bin/X11 is a symlink to /usr/bin (technically to . , the current working directory) apparently for compatibility reasons.

$ ls -l /usr/bin/X11
lrwxrwxrwx 1 root root 1 2010-06-25 17:53 /usr/bin/X11 -> .

then everythings fine.

Your X display problems are unrelated to this

---

### Post by pulpo69 on 2010-09-05
Thanks for your reply sevenmachines,
if i follow your advice:
ls -l /usr/bin/X11
i get:rwxrwxrwx 1 root root 1 2010-09-05 10:41 /usr/bin/X11 -> .
i do:lrwxrwxrwx 1 root root 1 2010-06-25 17:53 /usr/bin/X11 -> .
i get:lrwxrwxrwx 1 root root 1 2010-06-25 17:53 /usr/bin/X11 -> .
bash: .: Is a directory
i do otherwise:ls -l /usr/bin/X11
i get:lrwxrwxrwx 1 root root 1 2010-09-05 10:41 /usr/bin/X11 -> .

and the folder remains with over 1300 times the same inside.

---

### Post by SevenMachines on 2010-09-05
Is this some sort of script or something you're trying to run? the output of ls -l is fine though, '->' is a symlink, '.' is /usr/bin, /usr/bin/X11 is a symlink to the /usr/bin/ directory, exactly as it should be

---

### Post by pulpo69 on 2010-09-05
here is a screenshot

---

### Post by SevenMachines on 2010-09-05
I dont think thats such an elegant way for nautilus to handle the recursive symlink situation, possibly might be worth opening a bug on that

---

### Post by VMC on 2010-09-05
> **pulpo69 said:**
> Thanks for your reply sevenmachines,
if i follow your advice:
ls -l /usr/bin/X11
i get:rwxrwxrwx 1 root root 1 2010-09-05 10:41 /usr/bin/X11 -> .
i do:lrwxrwxrwx 1 root root 1 2010-06-25 17:53 /usr/bin/X11 -> .
i get:lrwxrwxrwx 1 root root 1 2010-06-25 17:53 /usr/bin/X11 -> .
bash: .: Is a directory
i do otherwise:ls -l /usr/bin/X11
i get:lrwxrwxrwx 1 root root 1 2010-09-05 10:41 /usr/bin/X11 -> .

and the folder remains with over 1300 times the same inside.

I know you stated this was a fresh install. I got the same output as SevenMachines:
```
$ ls -l /usr/bin/X11
lrwxrwxrwx 1 root root 1 2010-09-03 07:07 /usr/bin/X11 -> .

```

I noticed you also have two extra time date of 06/25. First I thought this was an upgrade.

---

### Post by SevenMachines on 2010-09-05
If its an issue, its one with the way nautilus displays the directory, the actual links fine. If you open /usr/bin/X11 in nautilus then this is the directory displayed, the actual contents is of course the symlinked directory of /usr/bin, which contains /usr/bin/X11. Now if you click the X11 symlink, the directory displayed is /usr/bin/X11/X11, the contents still /usr/bin, which is accurate if a little misleading. You can keep doing this ad-infinitum.
I dont know if the slightly confusing directory display could be considered a bug or not but it is just a presentation issue and not an actual problem. The problem OP is having with X display is unrelated.

---

### Post by pulpo69 on 2010-09-07
thanks vmc, thanks sevenmachines,
it was a fresh install with with formating the root-partition checked.
but there was one more strange thing, booting the first time after the fresh install, before gdm came up there was a one second the wallpaper
tat i had i my last installation.
changing now the wallpaper and rebooting, before gdn comes up i see for a moment the wallpaper i had before.

---

### Post by pulpo69 on 2010-09-18
i did another fresh install, some days ago. But &#65279;/usr/bin/X11 says link to folder, but inside this is 1300 times  another folder saying link to folder. Using this install in the meantime inside
 &#65279;/usr/bin/X11 are now 2000 another folder saying link to folder.
Nobody experienced the same?

---

### Post by cariboo on 2010-09-18
I've never seriously looked at it, but I did notice the same thing you did, several releases ago. It is causing you a problem? I would suggest creating a bug.

---

### Post by pulpo69 on 2010-09-19
bug reported.

---

