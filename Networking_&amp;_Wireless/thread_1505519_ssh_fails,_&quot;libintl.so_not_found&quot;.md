---
title: "ssh fails, &quot;libintl.so not found&quot;"
date: 2010-06-09
forum: Networking &amp; Wireless
---

### Post by tombrown on 2010-06-09
I have just installed Ubuntu 10.04 and run all the software updates.

When I use ssh the program is failing with the following error:

ssh [email]blah@blah.com[/email]
Password:

/libexec/ld-elf.so.1: Shared object "libintl.so.8" not found, required by "bash"
Connection to blah.com closed.

I'm guessing this is some sorting of linking failure.  Does anyone have a remedy?

Many thanks,

Tom

---

### Post by chrisstankevitz on 2011-09-26
Sorry, Ubuntu does not support libintl.

---

### Post by Kelketek on 2011-09-26
There's a nifty project that's called 'getlibs' that may solve your problem here. Since linked shared objects are actually a fairly common problem, someone made a little program specifically for the purpose of hunting them down and installing them.

The guy above me has more posts than me, so perhaps he's right, and you just need to compile in such a way that you don't need that library. But assuming he isn't, or you're lost for a method, here's something I would try:

```
wget http://frozenfox.freehostia.com/cappy/getlibs-all.deb
sudo dpkg -i getlibs-all.deb
sudo getlibs libintl.so
sudo ldconfig
```That should get and install the getlibs, find the desired shared object from the net and install it, then update your shared object configuration.

If it doesn't work, please reply with the output from getlibs when you ran the command, and the output of:

```
sudo ldconfig -v
```

The result after doing:

```
sudo updatedb
locate libintl.so
```

And the contents of the files in:

```
/etc/ld.so.conf.d
```

---

### Post by tombrown on 2011-09-27
Dear Kelktek and chrisstankevitz,

Thank you very much for taking the time to reply.  I think I resolved my problem but can't remember how.  I'm sorry, I should have closed the thread earlier.

Apologies,

Tom

---

