---
title: "ndiswrapper troubles"
date: 2006-02-04
forum: Networking &amp; Wireless
---

### Post by evilmrt on 2006-02-04
Hey folks, I've got a huge headache from trying to get my Belkin F5D7001 wifi card working in Ubuntu. I'm posting this in windows :P

After installing ndiswrapper from source per instructions here: [http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation)...

I'm running into a couple problems. After modprobing ndiswrapper (everything before that step went fine), the console just hangs. Dmesg gives me this:

[4294691.271000] ndiswrapper version 1.8 loaded (preempt=no,smp=no)
[4294691.315000] ndiswrapper (wrapper_init:173): loadndiswrapper failed (1792); check system log for messages from 'loadndisdriver'
[4294691.320000] ndiswrapper (wrapper_init:180): ndiswrapper: initialization failed

Whats going on?

---

### Post by Lambert on 2006-02-04
Post output of 

```
cat /proc/version
```
and
```
modinfo ndiswrapper
```

Breezy also has a module pre-installed, did you remove that before compiling and installing?

---

### Post by evilmrt on 2006-02-07
well, I can't even load ubuntu, because it hangs during the boot process when loading ndiswrapper :( 

now what? I'm about to ditch ubuntu, unless I can use internet

also, I don't remember removing any module, but I didn't use a fresh Breezy anyway. Its upgraded from Hoary. Which was upgraded from warty ;)

---

### Post by Lambert on 2006-02-07
You will need to boot using a livecd, then mount your ubuntu partition and edit the /etc/module file and remove the line 'ndiswrapper' then you should be able to boot.

---

