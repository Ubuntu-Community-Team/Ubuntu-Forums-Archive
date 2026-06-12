---
title: "ALSA Upgrade gone bad."
date: 2010-04-25
forum: Multimedia Software
---

### Post by sL8 on 2010-04-25
I googled an ALSA upgrade on google, followed it and everything.
Now I get
```

tyler@tyler-desktop:~$ aplay -l
aplay: device_list:207: no soundcards found...
```
Gehh..

It all started with really low volume from my MobilePre.
Could anyone help?

---

### Post by lidex on 2010-04-25
Reboot and post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#*
```
Terminal="Applications->Accessories->Terminal"
Please post text output using code tags. Also helpful is the make/model of your PC/Laptop.

---

### Post by sL8 on 2010-04-25
```

tyler@tyler-desktop:~$ uname -a
Linux tyler-desktop 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:09:38 UTC 2010 x86_64 GNU/Linux

``````

tyler@tyler-desktop:~$ aplay -l
aplay: device_list:207: no soundcards found...
``````

tyler@tyler-desktop:~$ cat /proc/asound/version
cat: /proc/asound/version: No such file or directory
``````

tyler@tyler-desktop:~$ head -n 1 /proc/asound/card*/codec#*
head: cannot open `/proc/asound/card*/codec#*' for reading: No such file or directory
```It's a custom built computer, I can probably fetch the specs, if needed?

---

### Post by lidex on 2010-04-26
So, lucid x64 install then. Your alsa update was botched. Try the alsa-upgrade-script link in my sig.

---

### Post by sL8 on 2010-04-26
Alright, doing it right now, will report back with the results, as an edit.
-edit-
It's download a lot of stuff, 30 minutes left o.o.
Fonts and stuff?
```

Get:61 http://us.archive.ubuntu.com/ubuntu/ lucid/main python-dev 2.6.5-0ubuntu1 [970B]
Get:62 http://us.archive.ubuntu.com/ubuntu/ lucid/main texlive-font-utils 2009-7ubuntu3 [1,788kB]
Get:63 http://us.archive.ubuntu.com/ubuntu/ lucid/main texlive-fonts-recommended-doc 2009-7 [2,411kB]
Get:64 http://us.archive.ubuntu.com/ubuntu/ lucid/main texlive-latex-base-doc 2009-7 [40.7MB]

```-edit-
Oh, dependencies. Nevermind, haha.

-edit-
Done! Got sound back, thank you.
And figured out the quietness too!

---

### Post by lidex on 2010-04-26
Great. Please mark the thread as solved using 'Thread Tools' up top.

---

