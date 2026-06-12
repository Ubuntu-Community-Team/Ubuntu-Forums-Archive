---
title: "Belkin Wireless G USB adapter F5D7050 v. 4000     help"
date: 2006-06-15
forum: Networking &amp; Wireless
---

### Post by dracule on 2006-06-15
I got ndiswrapper, and installed the driver found on my cd (BLKWGU.inf with BLKWGU XP.sys files). it says hardware is present in ndisgtk, but i still cant configure it in network settings. I tried doing it with different .sys files but still none of them work. I love ubuntu but this is about the only thing holding me back right now.

---

### Post by dracule on 2006-06-15
update:

i downloaded the linux driver source for my chipset. but i have no idea how to compile it.

---

### Post by noname101 on 2006-06-15
To compile it you'll need to do this:
Replace version with what ever uname -r displays.
```

sudo apt-get install build-essential
sudo apt-get install linux-source-version
cd /usr/src
sudo tar xvjf linux-source-version.tar.bz2
sudo ln -s /usr/src/linux-source-version /usr/src/linux
sudo ln -s /usr/src/linux /lib/modules/version/build
cd linux
sudo make oldconfig
sudo make include/linux/version.h
sudo make modules
cd ../
```
Then extract the file you downloaded to your home folder.
Just double click the file and click extract.
Then do this:
```
make && make install
```

---

### Post by dracule on 2006-06-15
im on my other computer...

is it supposed to take 3+ hours after sudo make modules? i thought it would take like 15 minutes but it is still going.

---

### Post by noname101 on 2006-06-15
Well it depends on how fast your computer is. It'll take a while anyways. You could try compiling it without doing that command.

---

