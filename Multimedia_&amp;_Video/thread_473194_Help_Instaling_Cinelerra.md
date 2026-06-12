---
title: "Help Instaling Cinelerra"
date: 2007-06-13
forum: Multimedia &amp; Video
---

### Post by jazzman84116 on 2007-06-13
Can somebody plz help me install this  plz

---

### Post by AvalonSpirit on 2007-06-13
1. Make sure you have universe, multiverse and restricted repositories enabled
2. Add the following repository to your sources.list file, according to your CPU type:

- i686:
deb [http://www.kiberpipa.org/~gandalf/ubuntu/feisty/cinelerra/i686/](http://www.kiberpipa.org/~gandalf/ubuntu/feisty/cinelerra/i686/) ./
- athlonxp:
deb [http://www.kiberpipa.org/~gandalf/ubuntu/feisty/cinelerra/athlonxp/](http://www.kiberpipa.org/~gandalf/ubuntu/feisty/cinelerra/athlonxp/) ./
- pentium4:
deb [http://www.kiberpipa.org/~gandalf/ubuntu/feisty/cinelerra/pentium4/](http://www.kiberpipa.org/~gandalf/ubuntu/feisty/cinelerra/pentium4/) ./

3. apt-get update ; apt-get install cinelerra 

here is the readme about the packages: [http://www.kiberpipa.org/~gandalf/ubuntu/README](http://www.kiberpipa.org/~gandalf/ubuntu/README)

got this from the cinelerra.org page, and it worked for me.

hope it helps

---

