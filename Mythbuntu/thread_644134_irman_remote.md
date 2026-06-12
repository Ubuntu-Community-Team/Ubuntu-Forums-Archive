---
title: "irman remote"
date: 2007-12-18
forum: Mythbuntu
---

### Post by ishkabob on 2007-12-18
Hi all,

I'm trying to use a serial remote that uses (I think) the Irman drivers.  I have the receiver plugged into the first serial port and when I run

```
 cat /dev/ttyS0 
``` or
```
 cat /dev/ttyS1 
```

nothing happens when I started pressing buttons on the remote.  I should see something on the terminal I think.  Anyone have any ideas?

- Kevin

---

### Post by OffAxis on 2007-12-18
irman support is busted in version .8.2

```
lircd -v
```
will tell you what version you're using.

follow these instructions to get .8.3 installed and working.
[http://lirc.org/cvs.html]("http://lirc.org/cvs.html")

---

### Post by ishkabob on 2007-12-18
Yeah I saw that, but I shouldn't need Lirc just to get some nonsense output from the serial device right?  I might be wrong; thanks for the reply!

---

### Post by OffAxis on 2007-12-19
instead of doing the cvs build, it's even easier to grab the pre-release package.

```
sudo wget http://launchpadlibrarian.net/10229062/lirc_0.8.3%7Epre1-0ubuntu1_i386.deb 
```
and then just install it

```
sudo dpkg -i lirc_0.8.3~pre1-0ubuntu1_i386.deb
```

---

