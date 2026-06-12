---
title: "gcc fails with amixer error?"
date: 2009-02-03
forum: Multimedia Software
---

### Post by GadiCohen on 2009-02-03
Newish install, tried to compile something for the first time yesterday.  Both gcc and g++ fail with the following error; no executable is produced.

```

dragon@dragon:~$ gcc -o hello hello.c
amixer: Cannot find the given element from control hw:0

amixer: Cannot find the given element from control hw:0

amixer: Cannot find the given element from control hw:0

dragon@dragon:~$ 

```

My audio is all working great, including mixer controls.  I have the default alsa device pointing to pulseaudio.  Any suggestions?  Thanks.

---

### Post by GadiCohen on 2009-04-02
I haven't managed to solve this yet.

I did notice though that I can compile as root (and I'm assuming anyone other than my default user) - I still have no clue what to look for though, no obvious environment variables, not sure what else I can check?

Any help would be really appreciated :)

---

### Post by GadiCohen on 2009-06-30
Ok wow, finally solved this... don't expect this will help anyone, but for the record.

I had a ~/bin/as which calls amixer.  ~/bin was in my path before /usr/bin where the real 'as' lives.  as is called by gcc.  Mystery solved.

---

