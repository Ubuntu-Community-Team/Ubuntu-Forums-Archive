---
title: "Atheros AR9285 on Jaunty 9.04"
date: 2009-07-01
forum: Networking &amp; Wireless
---

### Post by junxuan on 2009-07-01
I've recently installed jaunty on my new HP dv2-1014 AU. After reading through the forums i found solutions such as installing the backports and wicd manager. How it has not solved my problem. My wireless just doesnt work, can anybody help me? Thx

---

### Post by junxuan on 2009-07-02
bump.

---

### Post by eode on 2009-08-06
I don't know entirely yet, but a part of it is installing linux-backports-modules-jaunty.  That gets my card recognized, although it doesn't seem to see any networks..

..uh, that is, until I click the 'wireless' button on my laptop.. ..hehe.. ..yeah.  ..so, just install linux-backports-modules-jaunty.

:-)

You may need to select your specific kernel (I.e., linux-backports-modules-jaunty-generic), but I think the general "-jaunty" package should be fine.

:-)

---

### Post by MadHatter21 on 2009-08-06
Download and install compatible wireless if that does not work. 

[http://linuxwireless.org/en/users/Download/stable/](http://linuxwireless.org/en/users/Download/stable/)

then Unzip the directory then go into the terminal.

Then get into the directory of the unzipped file and run the following commands.

```

make
sudo make install
sudo make unload

```

after instalation go to etc directory and edit the modules file.

```

cd /etc
sudo pico modules

```

then add your driver. For myself I have a atheros ar5b95 so I use ath9k. So I would add,

```

ath9k

```

then save and exit. Restart your computer and you should be set. Let ne know how it works.

---

