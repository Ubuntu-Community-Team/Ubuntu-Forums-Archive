---
title: "trouble installing ipwraw-ng for intel proset wireless 3945"
date: 2009-03-26
forum: Networking &amp; Wireless
---

### Post by sk8sn0surf on 2009-03-26
Hey Im having touble installing ipwraw-ng. Ive been following **alimahmoudy's** instructions but I can't seem to get the file to make. This is what I've done so far.

```
sudo apt-get install build-essential (get core files)

sudo apt-get install libssl-dev (get supporting library)

wget http://dl.aircrack-ng.org/drivers/ip...022008.tar.bz2 (downloads driver)

tar -xjf ipwraw-ng* (extract the archive file)

cd ipwraw-ng (go to the extracted folder)

make

WARNING: $SHELL not set to bash.
If you experience build errors, try
'make SHELL=/bin/bash'.

make -C /lib/modules/2.6.27-7-generic/build M=/home/chris/Desktop/ipwraw-ng modules
make[1]: Entering directory `/lib/modules/2.6.27-7-generic/build'
make[1]: *** No rule to make target `modules'.  Stop.
make[1]: Leaving directory `/lib/modules/2.6.27-7-generic/build'
make: *** [modules] Error 2
root@chris-laptop:~/Desktop/ipwraw-ng# 

```

please help! I'm a complete linux noob at this point so Im sorry if its a simple fix.

---

