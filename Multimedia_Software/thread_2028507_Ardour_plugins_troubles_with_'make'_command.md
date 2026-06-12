---
title: "Ardour plugins: troubles with 'make' command"
date: 2012-07-18
forum: Multimedia Software
---

### Post by magneto538 on 2012-07-18
Hey guys,

I am new here and I'm having some fun on Ubuntu by just a few days. I'm trying to install some good LDSPA plugins for Ardour (these ones seem to be good: [http://plugin.org.uk/](http://plugin.org.uk/)). The download file is a tarball, so I extracted it and used /.configure. Nothing bad here, everything seems to be working. But when I try to use the 'make' command, I get this message:

```
make: *** No targets specified and no makefile found.  Stop.
```

 I followed every README and INSTALL file contained in the archive I downloaded, I tried to change permissions using 'chmod +x', I have downloaded 'make' and 'build-essential', but nothing works on that package. I've had many troubles with other tarballs, but eventually I was able to install them: but nothing seems to be working on this. I've already searched for other guides to solve my problem, but I found nothing interesting.

Any suggestion? What should I do? (and, could you suggest me some good plugins for Ardour? :cool: )

Thanks.
D

---

### Post by magneto538 on 2012-07-21
Up? Anyone here who knows how to solve my problem?

---

### Post by steeldriver on 2012-07-21
either the tarball didn't extract properly (the makefile really is missing) or you are not in the directory containing the makefile - did you maybe miss a step where it says 'cd  to the src directory' or somesuch? have you looked through the extracted tree to see if you can locate the makefile?

---

### Post by ranger1021994 on 2012-07-21
Well makefile maybe absent.
You need makefile.in and makefile.am to generate proper makefile

---

### Post by mc4man on 2012-07-21
At the prompt of extracted source - 
```
touch config.rpath && ./autogen.sh
```
The run make, ect.

---

