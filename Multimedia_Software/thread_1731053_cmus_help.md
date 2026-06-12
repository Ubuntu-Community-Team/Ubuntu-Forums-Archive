---
title: "cmus help"
date: 2011-04-16
forum: Multimedia Software
---

### Post by meem1029 on 2011-04-16
So I just installed cmus to see what it is like since I've been enjoying cli stuff more recently.  Anyway, I have all my music in a separate partition since I dual-boot and want it accessible to both Ubuntu and Windows.  The problem I am having is that cmus does not seem to want to load my music files into my library.  The two albums I have on my linux partition work just fine, but none of them in shared do.  When I use the file navigator to go to the folders, it does not see any songs.  When I navigate to the same folder in the terminal it sees them just fine.  Does anyone have any idea as to what the cause might be?

---

### Post by VolatileMember on 2011-04-25
Hello meem1029,

can you download version 2.4.0 of cmus and compile it with debug support?

```
sudo apt-get build-dep cmus
wget http://downloads.sourceforge.net/cmus/cmus-v2.4.0.tar.bz2
tar -xf cmus-v2.4.0.tar.bz2
cd cmus-v2.4.0
./configure prefix=$HOME/cmus **DEBUG=2**
make install
```Then run cmus, reproduce the bug and post the output of ~/cmus-debug.txt :

```
~/cmus/bin/cmus
```

---

