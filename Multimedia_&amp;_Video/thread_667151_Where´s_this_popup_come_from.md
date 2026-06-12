---
title: "Where´s this popup come from?"
date: 2008-01-14
forum: Multimedia &amp; Video
---

### Post by viniciusandre on 2008-01-14
It happens every time I login, after the username and password screen:

[[IMG]http://img61.imageshack.us/img61/4264/telabr7.th.jpg[/IMG]](http://img61.imageshack.us/img61/4264/telabr7.jpg)

For who can´t read portuguese:
**¨The language pt_br does not exists, using the system default.¨**

Thank you!

---

### Post by santaslittlehelper on 2008-01-14
Hi

I am not sure how come but there seem to be something a miss with you're locals.

Maybe you can fix it with,
System > Administration > Language Support
then choose Portuguese to download if it is not already so.

If that don't fix it you can try posting the output of the following commands.

```
cat /etc/environment
locale
locale -a
```

---

### Post by viniciusandre on 2008-01-14
Hello!

Thanks for the help.
My config for System > Administration > Language Support is already setted to PT_BR.

Here's the outputs:

```
vinicius@vinicius:~$ cat /etc/environment 
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
LANG="pt_BR.UTF-8"
LANGUAGE="pt_BR:pt:pt_PT"
```

```
vinicius@vinicius:~$ locale
LANG=pt_BR.UTF-8
LANGUAGE=pt_BR:pt:en
LC_CTYPE="pt_BR.UTF-8"
LC_NUMERIC="pt_BR.UTF-8"
LC_TIME="pt_BR.UTF-8"
LC_COLLATE="pt_BR.UTF-8"
LC_MONETARY="pt_BR.UTF-8"
LC_MESSAGES="pt_BR.UTF-8"
LC_PAPER="pt_BR.UTF-8"
LC_NAME="pt_BR.UTF-8"
LC_ADDRESS="pt_BR.UTF-8"
LC_TELEPHONE="pt_BR.UTF-8"
LC_MEASUREMENT="pt_BR.UTF-8"
LC_IDENTIFICATION="pt_BR.UTF-8"
LC_ALL=
```

```
vinicius@vinicius:~$ locale -a
C
en_AU.utf8
en_BW.utf8
en_CA.utf8
en_DK.utf8
en_GB.utf8
en_HK.utf8
en_IE.utf8
en_IN
en_NZ.utf8
en_PH.utf8
en_SG.utf8
en_US.utf8
en_ZA.utf8
en_ZW.utf8
POSIX
pt_BR.utf8
pt_PT.utf8
```

Thank You!

---

### Post by santaslittlehelper on 2008-01-15
Hi

Sorry, I am all but guesses on this one, if you don't get a response soon then maybe try another part of the forum as I don't think this has much to do with multimedia.
Maybe a better chance that someone who knows will see you're post. 

Hope you solve it.

---

