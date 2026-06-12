---
title: "MYSQL doesn't start at bootup"
date: 2012-02-12
forum: Multimedia Software
---

### Post by duncang92 on 2012-02-12
I'm struggling trying to finish off my Mythtv install.

The problem I have is that the mysql daemon isn't running everytime I boot the machne up since there is no mysqld.sock file.

I have to manually run the following in a terminal window to create the mysqld.sock file and then kickoff the mysql daemon and the mythbackend each time I boot then all is good and Mythtv runs very nicely.

mkdir /var/run/mysqld
touch /var/run/mysqld/mysqld.sock
chown duncan /var/run/mysqld/mysqld.sock
chown -R duncan /var/run/mysqld/
mysqld

I can then kickoff mythbackend

I know I can stick all of this into a script to run at startup but I don't think that's the right way to do it.

Cheers for any help and pointers.

---

