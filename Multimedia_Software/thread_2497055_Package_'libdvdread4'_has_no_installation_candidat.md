---
title: "Package 'libdvdread4' has no installation candidate"
date: 2024-04-21
forum: Multimedia Software
---

### Post by crucio200 on 2024-04-21
Hi, i'm trying to play some encrypted DvD but i can't since some of them are probably encrypted. Itried following the guide: [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats) So I tried to do: 
sudo apt-get install lubuntu-restricted-extras
 
then: 
sudo /usr/share/doc/libdvdread4/install-css.sh 

When i use this command this happens:

fracru@FraCru:~$ sudo /usr/share/doc/libdvdread4/install-css.sh
[sudo] password for fracru: 
sudo: /usr/share/doc/libdvdread4/install-css.sh: command not found

Then i searched online and tried: sudo apt-get install libdvdread4 && sudo /usr/share/doc/libdvdread4/install-css.sh

but i have anyway problems:
fracru@FraCru:~$ sudo apt-get install libdvdread4 && sudo /usr/share/doc/libdvdread4/install-css.sh
[sudo] password for fracru: 
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Package libdvdread4 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'libdvdread4' has no installation candidate

What should i do? Thanks a lot this is my first time using linux

---

### Post by Holger_Gehrke on 2024-04-21
The way to do this has changed a few times and the instructions in the wiki seem to be stuck at some point in time far in the past. Follow the link to [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs) on the page you linked and then do what it tells you to do for Ubuntu version 15.10 or newer.
```

sudo apt install libdvd-pkg

```

This should download, compile, package, and install the libraries needed for DVD decoding. If it doesn't do all of that, you might have to run
```

sudo dpkg-reconfigure libdvd-pkg

```

Holger

---

### Post by crucio200 on 2024-04-21
I followed both the commands but the pc still can't read some dvds. I dont know why: it recognize the title but when i try to press play, i read in the top the name of the dvd for just a sec and then it tourns again normal.

Edit: i followed the exactly same instruction on a different pc with the same lubuntu and it works...

---

