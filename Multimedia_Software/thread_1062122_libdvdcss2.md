---
title: "libdvdcss2"
date: 2009-02-06
forum: Multimedia Software
---

### Post by jesuisbenjamin on 2009-02-06
hey there,

i tried to play a DVD on 8.10 and there is no reaction from VLC and Movie Player 'cannot open the location'.
Maybe installing libdvdcss2 would be a good idea, but:

```
sudo apt-get install libdvdcss2
```

returns: 

```
Package libdvdcss2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
```

Is there anyone with any idea?
Thanks :)

---

### Post by wolfen69 on 2009-02-06
```
sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list --output-document=/etc/apt/sources.list.d/medibuntu.list
```
then
```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

then install libdvdcss2.

this is of course, assuming you are using ubuntu 8.10

---

### Post by AKADAP on 2009-02-06
libdvdcss2 is probably not in any of the repositories you have linked to.
Do a google search. There are several good walkthroughs on how to get this installed.

---

### Post by wolfen69 on 2009-02-06
> **AKADAP said:**
> libdvdcss2 is probably not in any of the repositories you have linked to.
Do a google search. There are several good walkthroughs on how to get this installed.

i gave him the instructions to add the neccessary repos. ;)

---

