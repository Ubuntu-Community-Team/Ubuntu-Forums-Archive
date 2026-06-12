---
title: "Soundcard problem: Via VT1720 Envy24"
date: 2006-05-30
forum: Multimedia &amp; Video
---

### Post by tibrisch on 2006-05-30
Hello!
Im having problems with my embeded Via VT1720 Envy24 soundcard. Do i have to fix this problem as described in a topic at the 5.04 Hoary section. Im a newbe to linux and altering sourcecode and compiling modules scares me ;)

Thanks
/Tibrisch

---

### Post by llamakc on 2006-05-30
Which kernel are you using:

```
uname -r
```

I'm using 2.6.15-22-k7 because 2.6.15-23-* completely borked sound for me too.

---

### Post by tibrisch on 2006-06-08
[QUOTE=llamakc]Which kernel are you using:

```
uname -r
```

I'm using 2.6.15-22-k7 because 2.6.15-23-* completely borked sound for me too.[/QUOTE]


Hi, im using 2.6.15-23-386... but if i remember correctly it didnt work with 22 either.

Could this have something to do with my problem perhaps?
What does error -5 mean?
```

dmesg | grep ICE
[4294692.813000] ICE1724: probe of 0000:03:02.0 failed with error -5

```

---

