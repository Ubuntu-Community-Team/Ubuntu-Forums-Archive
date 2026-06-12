---
title: "libmp3lame"
date: 2010-09-23
forum: Multimedia Software
---

### Post by nandan.amar on 2010-09-23
I am compiling libmp3lame from svn and I got following error

**_ No rule to make target `basic.html', needed by `all-am'.  Stop._**

which package am I missing.....??

---

### Post by andrew.46 on 2010-09-23
Hi nandan,

> **nandan.amar said:**
> I am compiling libmp3lame from svn 

Can I ask which svn repository you are using? I ask especially as I believe the lame developers are still using cvs...

Andrew

---

### Post by nandan.amar on 2010-09-23
Dear Andrew
you are correct .
I am using source from CVS.
I don't think that is the reason for error.

---

### Post by andrew.46 on 2010-09-23
Hi nandan,

You are pretty keen as the latest release version came out in March this year :). Is there a reason you need the bleeding edge version?

Andrew

---

### Post by nandan.amar on 2010-09-23
I am compiling ffmpeg from svn and for that libmp3lame is needed .
I took it from CVS.
One earlier version I also tried from .tar file. 
this time I am sure about repository.
So during the chain of compilation I got error like

[COLOR="DarkOrange"] No rule to make target `basic.html', needed by `all-am'. Stop.
[/COLOR]
what is reason for such error...?

---

### Post by andrew.46 on 2010-09-23
Hi nandan,

> **nandan.amar said:**
> I am compiling ffmpeg from svn and for that libmp3lame is needed

Indeed, and the repository libmp3lame is now too old. Have a look at this post if you are using Lucid:

Install FFmpeg and x264 on Ubuntu Lucid Lynx 10.04
[http://ubuntuforums.org/showpost.php?p=9868359&postcount=1289](http://ubuntuforums.org/showpost.php?p=9868359&postcount=1289)

and you will see build instructions for lame 3.98.4 which is probably what you are after rather than the cvs version. 

Andrew

---

### Post by nandan.amar on 2010-09-23
Dear Andrew
many thanks
I got work done and disabled libmp3lame.
But still I would like to know about error during compilation.
I am sure I am not having some components installed on my system.
can u help in that regard...

---

### Post by andrew.46 on 2010-09-23
Hi nandan,

If you followed FakeOutdoorsman's suggestion you should have a working copy of FFmpeg *with* libmp3lame, you did not compile lame as he suggested in Step 5?

As to your error, can you give the terminal commands you used to download the cvs lame, the ./configure results and the terminal output from make? This should give an idea of what is going on...

Andrew

---

### Post by nandan.amar on 2010-09-23
thanks
I followed the link and compiled without disabling libmp3lame
:)

I followed instructions from [here]("http://sourceforge.net/scm/?type=cvs&group_id=290") as

cvs -d: pserver: [email]anonymous@lame.cvs.sourceforge.net[/email]:/cvsroot/lame login

cvs -z3 -d: pserver:anonymous@lame.cvs.sourceforge.net:/cvsroot/lame co -P modulename

and then configure [here]("http://pastebin.com/NnPZrz6W") is log , 

amd got error during make
[here]("http://pastebin.com/hansmAGT") is log.

---

### Post by mc4man on 2010-09-23
> But still I would like to know about error during compilation.
The lame/doc/html/makefile.am and makefile.in are at odds with each other and both are incorrect as to the included .html files (the .in is the worst, the .am is just missing one which is not that big a deal

So you'd need to make them the same and should reflect the actual files,
something like this would probably do (in both the .am and .in before the configure

```
pkghtml_DATA = \
    about.html \
	abr.html \
	cbr.html \
	contact.html \
	contributors.html \
	detailed.html \
	history.html \
	index.html \
	introduction.html \
	links.html \
	list.html \
	ms_stereo.html \
	usage.html \
	vbr.html
```

---

