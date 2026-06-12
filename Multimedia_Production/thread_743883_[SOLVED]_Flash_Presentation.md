---
title: "[SOLVED] Flash Presentation"
date: 2008-04-03
forum: Multimedia Production
---

### Post by expatCM on 2008-04-03
My son just asked me to install some software so that he can design and edit and flash presentation which is a core module next term.

Any suggestions what I should install since looking round Synaptic does not seem to give any clue ...

---

### Post by Cresho on 2008-04-03
hmm...Free?  As far as I can tell, NONE!  BUT....there is a work around.

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=6415](http://appdb.winehq.org/objectManager.php?sClass=version&iId=6415)

if interested, install wine from add remove.  Download the demo and try it.  it is an exe but you can right click and run with wine if double clicking doesn't work.

I remember swish selling the products way cheaper like 20 bucks.  Frankly I think 100 plus is a bit too much.  Just a little warning, if you decide to buy, they require activation process which might not work at all to activate the product.

---

### Post by gsmanners on 2008-04-03
If you don't mind alpha quality, there's also this: [http://www.salasaga.org/](http://www.salasaga.org/)

---

### Post by hmgp on 2008-04-03
Hi there! I made a small and simple ( I think it's simple :) ) how-to to get Salasaga on Ubuntu. You can see it [here]("http://opensourceportugal.blogspot.com/2008/04/salasaga-on-ubuntu-710.html") or [here]("http://www.salasaga.org/wiki/index.php/HowToInstallOnUbuntu").

I hope it helps.

---

### Post by expatCM on 2008-04-05
Very nice to receive a wide range of responses.  I have alternatives to work with here ...  thank you so much for your help :)

---

### Post by AMTravesser on 2008-04-06
Hello, hmgp,

I followed your little tutorial.  Got the dependencies installed, then tried to compile the ming library.  I get this:

```

[email]allasso@Praise:~/debs/ming-0.4.0.beta[/email]5$ sh autogen.sh
Running aclocal -I macros
Running libtoolize --automake
Running autoheader -f
Running automake
configure.in: 207: automake requires `AM_PROG_LEX', not `AC_PROG_LEX'
automake: configure.in: required file `config/mkinstalldirs' not found
Makefile.am:13: additionnal_dist_subdirs defined both conditionally and unconditionally
Makefile.am:11: option `dist-bzip2' not recognized
Makefile.am:11: require version 1.4d, but have 1.4-p6
test/Movie/add/Makefile.am:13: variable `NULL' not defined
test/Movie/add/Makefile.am:18: variable `NULL' not defined
test/Movie/add/Makefile.am:13: variable `NULL' not defined
test/Movie/add/Makefile.am:18: variable `NULL' not defined
test/Movie/add/Makefile.am:25: variable `NULL' not defined
automake: test/actionscript/Makefile.am: not supported: source file `../run_test.c' is in subdirectory
automake: test/actionscript/Makefile.am: not supported: source file `../../util/makeswf_utils.c' is in subdirectory
util/Makefile.am:14: pngprograms multiply defined in condition
util/Makefile.am:28: warning: automake does not support conditional definition of pngprograms in bin_PROGRAMS
util/Makefile.am:28: warning: automake does not support conditional definition of pngprograms in bin_PROGRAMS
util/Makefile.am:28: warning: automake does not support conditional definition of pngprograms in bin_PROGRAMS
util/Makefile.am:28: warning: automake does not support conditional definition of pngprograms in bin_PROGRAMS
util/Makefile.am: listmp3_OBJECTS should not be defined

  Something went wrong, bailing out!

```

any suggestions?

Thanks.

---

### Post by hmgp on 2008-04-07
Hello. I don't know what could be. I will investigate and if I find anything I will post it here. You can go to the Salasaga forum and try there also.

Thank you.

---

### Post by AMTravesser on 2008-04-07
okay, thank you.

Allasso

---

