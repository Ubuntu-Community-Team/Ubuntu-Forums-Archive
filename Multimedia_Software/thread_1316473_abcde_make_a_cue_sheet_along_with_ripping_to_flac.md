---
title: "abcde make a cue sheet along with ripping to flac"
date: 2009-11-06
forum: Multimedia Software
---

### Post by Captain_Falafel on 2009-11-06
I've got a CD collection I want to rip into flac, but also generate a cue sheet.

I can get the flac files fine running this:

```
abcde -o flac
```

but when I try:

```
abcde mkcue -o flac
```

I don't get a cue sheet.. what am I doing wrong?

---

### Post by andrew.46 on 2010-04-21
Hi Captain_Falafel,

Perhaps what you are after is:

```
abcde -o flac -a default,cue
```

Andrew

---

### Post by rommelsousa on 2010-06-24
I use this:

```
abcde -o flac -acddb,tag,playlist,cue,move,clean -N -x
```

---

