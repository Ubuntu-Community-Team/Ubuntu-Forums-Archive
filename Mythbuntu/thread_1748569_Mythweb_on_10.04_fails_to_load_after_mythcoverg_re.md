---
title: "Mythweb on 10.04 fails to load after mythcoverg rebuild"
date: 2011-05-03
forum: Mythbuntu
---

### Post by sudanmas on 2011-05-03
I had to dump mythconverg and recreate the database from scratch.  Mythweb was working before the drop, but now won't load.

I confirmed Apache is running fine - 192.168.123.105 displays apache's default page.

When I go to 192.168.123.105/mythweb I get the mythweb login dialogue box.  I key the correct username and password and get only a blank white screen.

Where should I look next to try to narrow down the problem?

---

### Post by nickrout on 2011-05-03
your apache logs?

---

### Post by sudanmas on 2011-05-06
I should have known that ;-)  Everything in ubuntu has a log of some sort.

Here's the last error message in the log file:

**[Fri May 06 17:43:35 2011] [error] [client 192.168.123.108] PHP Warning:  require(modules/_shared/tmpl/tmpl/header.php): failed to open stream: No such file or directory in /usr/share/mythtv/mythweb/modules/_shared/tmpl/_errors/fatal.php on line 23**

Line 23 in the fatal.php points to:

**require 'modules/_shared/tmpl/'.tmpl.'/header.php**

I'm not sure what '.tmpl.' is pointing to so I'm having trouble locating **header.php**

The other odd thing is that the error message reference 192.168.123.108

I'm currently using 192.168.123.105 according to **ifconfig**

---

### Post by nickrout on 2011-05-07
are you accessing mythweb from the same computer? Does 108 refer to the server or the client, or are they the same?

---

### Post by sudanmas on 2011-05-07
192.168.123.108 currently is assigned to the laptop I'm using

---

