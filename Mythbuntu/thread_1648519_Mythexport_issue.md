---
title: "Mythexport issue"
date: 2010-12-18
forum: Mythbuntu
---

### Post by GuiGuy on 2010-12-18
I'm once again trying to get mythexport working. It is frustrating:

The only error the log is throwing is this:

> Can't locate .pm in @INC (@INC contains: /usr/share/mythexport/configs /usr/share/mythexport /etc/perl /usr/local/lib/perl/5.10.1 /usr/local/share/perl/5.10.1 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl .) at /usr/bin/mythexport-daemon line 428.


can anyone enlighten me as to what this means?

---

### Post by cipherboy_loc on 2010-12-18
> **GuiGuy said:**
> I'm once again trying to get mythexport working. It is frustrating:

The only error the log is throwing is this:



can anyone enlighten me as to what this means?
Note: I do not use Myth-TV. Just warning you, but read ahead.

The only thing I can think of is that you have a goofed-upped mythexport/mythtv install. It is trying to include (#include <library>, except in Perl so it is use <module>) a library, except instead of putting a name (Digest::MD5 for example), it just puts a simi-colon (thus ending the line. What is the output of the following command:

```
cat $(which mythexport) | grep -i 'use '
```


In other words, it is saying that it cannot find a module with no name, hence it does not exist. You have two options: edit the mythexport script and remove the use line, or you could re-install mythexport.


Note, I say again: I do not have, nor do I use, nor do I claim to know anything about mythexport or mythtv. This is purely from building Perl apps (for private use),
Cipherboy

---

### Post by ZedThou on 2010-12-20
> **GuiGuy said:**
> I'm once again trying to get mythexport working. It is frustrating:

The only error the log is throwing is this:



can anyone enlighten me as to what this means?

There's something wrong with your mythexport installation. mythexport loads config modules from /usr/share/mythexport/config, e.g., I have three choices

```

$ ls /usr/share/mythexport/configs/
N900LowBitrate.pm  PortableH264HighRes.pm  PortableH264LowRes.pm

```

Then when I export with "On the Go Lightweight" I choose one of these profiles from the drop-down menu. For some reason, your mythexport is trying to open a profile whose name is an empty string.

---

### Post by tsh on 2012-10-17
I'm plagued with these mythexport errors. For some reason, the database entries which it uses don't get configured properly and whenever i upgrade, I loose the hacks I do at the last minute before flying somewhere.

Quick fix is to hard-code the format file name into the script, I think.

---

### Post by nickrout on 2012-10-17
> **tsh said:**
> I'm plagued with these mythexport errors. For some reason, the database entries which it uses don't get configured properly and whenever i upgrade, I loose the hacks I do at the last minute before flying somewhere.

Quick fix is to hard-code the format file name into the script, I think.this thread is over a year old, please start a new one.

---

### Post by overdrank on 2012-10-17
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

