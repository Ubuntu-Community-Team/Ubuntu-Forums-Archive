---
title: "Dual Head Won't Work =("
date: 2006-07-17
forum: Multimedia &amp; Video
---

### Post by kaje on 2006-07-17
Trying to get the "Big Desktop" setup.

Two CRTs: 22" - 17"


- Have the proprietary ATI drivers installed.

- Ran the following command:

```
aticonfig --initial=dual-head --screen-layout=right --dtop=horizontal --overlay-on=1
```

Currently, my secondary monitor works, but it's the same thing displayed on my primary (only it looks like it's zoomed in due to the resolution being higher than the secondary supports).

I've looked at all the ATI dual head related posts for Dapper Drake on the forums here and none of them seem to refer to my problem or fix it. I'll post my xorg.conf if it's needed.

This problem is keeping me from wanting to even boot into Ubuntu anymore because it's been nothing but a headache.

Would appreciate anyone that's able to help me get this setup.

---

### Post by kaje on 2006-07-18
I've also tried the following command;

```
aticonfig --initial=dual-head --dtop=horizontal --screen-layout=right --iagp=off -v

```

To which I get the error:

```
aticonfig: unrecognized option `--iagp=off'
aticonfig: parsing the command-line failed.

```

Google doesn't bring up any results for this error, either.  :-k

---

### Post by kaje on 2006-07-18
bump

---

### Post by cet' on 2007-12-20
I have a optplex 745 with dual monitors running 7.10 gutsy gibbon

i manged to get dual monitors working using fglrx and the drivers that ubuntu automatically advised to use although they are the proprietary drivers

then give the command

sudo aticonfig --initial=dual-head --screen-layout=left

ctrl alt backspace to restart x and you will now have dual screens

---

