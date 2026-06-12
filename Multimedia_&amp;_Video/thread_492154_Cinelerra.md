---
title: "Cinelerra"
date: 2007-07-04
forum: Multimedia &amp; Video
---

### Post by SeattleUser on 2007-07-04
I see some people having success with this sw, but the package manager doesn't find it.  How would I install it?

After some googling I found this link.  Is it a reliable source?
[http://www.kiberpipa.org/~gandalf/ubuntu/README](http://www.kiberpipa.org/~gandalf/ubuntu/README)

---

### Post by moore.bryan on 2007-07-04
*you have to put in the cinelerra repo.  check [this page]("http://cvs.cinelerra.org/getting_cinelerra.php") for the one appropriate to your system.*

---

### Post by SeattleUser on 2007-07-04
Thanks for the info.  I'll give it a try.

---

### Post by moore.bryan on 2007-07-04
*no problem... if you run into any issues just post.  i've tried-out cinelerra and found it incredibly powerful, but not all that intuitive.*

---

### Post by sullenx on 2007-10-23
How about for Gutsy? No repository available?

---

### Post by FuturePilot on 2007-10-24
Doesn't look like there's a Gutsy repo yet. I hope they make one soon.

---

### Post by tubunu on 2007-10-28
Is it safe to use non Gutsy repository to install Cinelerra?

---

### Post by anv on 2007-11-04
Tried this: 
or AMD64 (and also Core Duo Intel64), by Valentina Messeri:
deb [http://giss.tv/~vale/ubuntu64](http://giss.tv/~vale/ubuntu64) ./

but:

cinelerra:
  Depends: liblame0 (>=3.97) but 3.96.1-2ubuntu1 is to be installed
 Depends: libquicktimehv but it is not going to be installed
 Depends: libquicktimehv but it is not going to be installed


how to proceed?

---

### Post by mimsmall on 2007-11-04
you can find a link rom this page for the Gutsy Gibbon package and there is a lint to the install instructions. They were no help to me, maybe they will work for you. I installed the package using Synaptic. When I clicked on the icon to open it I got a lot of disk activity but cinelerra did not open. I tried to open cinelerra in a terminal and got an error message that said "Illegal instruction (core dump)"   [http://cv.cinelerra.org/getting_cinelerra.php#ubuntu](http://cv.cinelerra.org/getting_cinelerra.php#ubuntu)

I used this program in Dapper, but have not been able to get the program to open in Feisty or Gutsy.

---

### Post by rsnow on 2007-11-05
Me too. I just completed the install from Synaptic and everything looked OK. I click on the icon in the Sound & Video menu and all I get is a quick flash in the upper left corner of the desktop.

---

### Post by ratm355 on 2007-11-10
It is working fine for me using the repository listed above. All I had to do was to download a later version of libfaac0 from debian-multimedia.org. Here is the link:

[http://www.debian-multimedia.org/dists/testing/main/binary-amd64/package/libfaac0.php](http://www.debian-multimedia.org/dists/testing/main/binary-amd64/package/libfaac0.php)

I added 
echo "0x7fffffff > /proc/sys/kernel/shmmax
to /etc/rc.local to stop that message from popping up when Cinelerra opens.

---

### Post by carusoswi on 2007-11-25
Is there anyone willing to post a step by step how to in order for me to get Cinelerra for my 7.04 system?

I don't know what to do with "deb [http://www.kiberpipa.org/~gandalf/ubuntu/feisty/cinelerra/pentium4/](http://www.kiberpipa.org/~gandalf/ubuntu/feisty/cinelerra/pentium4/) ./" for instance.

My machine is a Pentium 4/3.0/2gb ram, btw.

Any help would be appreciated.

My current editing is done in XP using Vegas 8 Pro, but I'd like to move to Ubuntu exclusively if possible.

Thanks.

Caruso

---

