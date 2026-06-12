---
title: "any2dvd"
date: 2007-07-20
forum: Multimedia &amp; Video
---

### Post by TaintedTux on 2007-07-20
I found this program called any2dvd for Linux. It is to convert avi files and such into DVD type video to burned onto a dvd and played on a dvd player. Has anyone used this because here is my problem. 

Intall:

## Installation instructions ##

* Copy the files 'any2vob' & 'any2dvd' into your $PATH somewhere.

	Example:
	'/usr/bin' or '/usr/local/bin'

* Copy the files 'any2vob.1' & 'any2dvd.1' into your $MANPATH somewhere.

	Example:
	'/usr/share/man' or /usr/local/share/man'


* After installation, type `any2dvd -h` or `man any2dvd` for a help page.

* any2vob - Encodes the movies
* any2dvd - Calls on any2vob to encode the movies, then creates the DVD menus & burns to DVD

* Any2vob can be used as a standalone tool seperate from any2dvd, for creation of .VOB files only, type `any2vob -h` or `man any2vob` for a help page.

I have done all of this. 
any2dvd-h gives me 
nate@Tainted:~$ any2dvd-h
bash: any2dvd-h: command not found

any2dvd -h gives me
/usr/local/bin/any2dvd: 295: Syntax error: Bad substitution

I have tried copying the files to both /usr/bin and /usr/local/bin and I get the same resulsts either way. 
If anyone has used this program and offer any help I'd appreciate it. 

Or if you know another way to convert avi files to dvd video thats fairly easy that would be fine to. 
Thanks

---

### Post by yabbadabbadont on 2007-07-20
For an actively supported alternative to that script, how about using tovid.  :D

[http://tovid.wikia.com/wiki/Main_Page](http://tovid.wikia.com/wiki/Main_Page)

Forum howto thread: [http://ubuntuforums.org/showthread.php?t=183936](http://ubuntuforums.org/showthread.php?t=183936)

It does the same thing that any2dvd does and a lot more.

---

### Post by thirtankara on 2008-03-27
There's a bashism in the script.
Just change /bin/sh for /bin/bash in the first line.
For more information, visit:
[http://sourceforge.net/tracker/index.php?func=detail&aid=1898510&group_id=143060&atid=754969](http://sourceforge.net/tracker/index.php?func=detail&aid=1898510&group_id=143060&atid=754969)
Regards

---

