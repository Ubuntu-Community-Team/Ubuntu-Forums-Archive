---
title: "Mencoder in Utopic"
date: 2015-03-22
forum: Multimedia Software
---

### Post by Kieran. on 2015-03-22
Under which utopic respository is mencoder located? After an upgrade I can no longer install this via apt?

---

### Post by bapoumba on 2015-03-22
Probably these :
[https://bugs.launchpad.net/ubuntu/+source/mplayer2/+bug/1363877](https://bugs.launchpad.net/ubuntu/+source/mplayer2/+bug/1363877)
[https://bugs.launchpad.net/ubuntu/+source/mplayer2/+bug/1426720](https://bugs.launchpad.net/ubuntu/+source/mplayer2/+bug/1426720)

---

### Post by Kieran. on 2015-03-22
Ah yes, didn't see those in a search. Have subscribed to the bugs. Many thanks.

---

### Post by mc4man on 2015-03-22
Those bug reports assume that mencoder came from mplayer2 source which is wrong, it was/is from mplayer source.
mplayer was dropped from Debian/Ubuntu a while back for various reasons so no mplayer = no mencoder

---

### Post by SeijiSensei on 2015-03-22
Mencoder is largely deprecated in favor of more modern converters like ffmpeg or its clone avconv.  The mplayer2 developers chose not to support mencoder as a result.  However the developer of smplayer appears to be distributing a version of mplayer with mencoder as well from his PPA: [https://launchpad.net/~rvm/+archive/ubuntu/mplayer](https://launchpad.net/~rvm/+archive/ubuntu/mplayer).

---

### Post by Kieran. on 2015-03-22
Thanks for all the info. I've just tried avconv and it's more than capable of doing what I'm looking for. Have to get used to all the different options but that's progress for you!

---

### Post by andrew.46 on 2015-03-22
This guide may require some massaging to run under Utopic but certainly produces MEncoder under Trusty:

Build the svn MPlayer under the latest Ubuntu release
[http://www.andrews-corner.org/ubuntu/mplayer.html](http://www.andrews-corner.org/ubuntu/mplayer.html)

---

