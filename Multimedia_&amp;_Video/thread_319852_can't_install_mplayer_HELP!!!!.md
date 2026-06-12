---
title: "can't install mplayer HELP!!!!"
date: 2006-12-16
forum: Multimedia &amp; Video
---

### Post by robtherich8 on 2006-12-16
mplayer isn't on my system it seems so I tried to install it. This is what happened.

~$ sudo apt-get install mplayer
Password:
Reading package lists... Done
Building dependency tree... Done
Package mplayer is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package mplayer has no installation candidate

Hmmm, I'm a newbie to Linux (this week). Can anyone please help?

---

### Post by taurus on 2006-12-16
Make sure you have both universe and multiverse enable in /etc/apt/sources.list.  You can do that by editing /etc/apt/sources.list and remove the # in front of all the lines with universe and multiverse at the end (they start with "deb" at the beginning)...

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/apt/sources.list
```
Save it and run

```
sudo aptitude update
sudo aptitude install mplayer
```
Otherwise, use automatix2 to install mplayer and all the codecs since you also need the codecs before you can play anything on your machine.

---

### Post by robtherich8 on 2006-12-16
Hi, thanks for the reply. It turns about both Multiverse and Universe were enabled already. I looked for automatix2 and installed it according to the instructions here:

[http://www.getautomatix.com/wiki/index.php?title=Installation&Itemid=38#Installing_Automatix2_with_Apt](http://www.getautomatix.com/wiki/index.php?title=Installation&Itemid=38#Installing_Automatix2_with_Apt)

I followed the instructions for 6.06 which is the Ubuntu version I'm using.

It seems to install but when I run it it tells me this version is for 6.10 only! I'm considering trying a second, different Linux distro now ](*,)

---

### Post by taurus on 2006-12-16
Can you paste your /etc/apt/sources.list here?

```
cat /etc/apt/sources.list
```

---

### Post by robtherich8 on 2006-12-16
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main

---

### Post by robtherich8 on 2006-12-16
I also tried the non-automatix method you gave for installing mplayer. The second line gave this result:

$ sudo aptitude install mplayer

Reading package lists... Done
Building dependency tree... Done
Initialising package states... Done
Building tag database... Done
No candidate version found for mplayer
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done

Just to confirm (out of my ignorance I suppose), I tried mplayer again:

$ mplayer [http://localhost:1234](http://localhost:1234) (a number, not 1234 ;-)
bash: mplayer: command not found

---

### Post by taurus on 2006-12-16
Here's your problem!!!

```
deb http://www.getautomatix.com/apt edgy main
```
Remove that line and also the one below since the last two lines are exactly identical!!!

```
deb http://www.getautomatix.com/apt dapper main
```
Save it and run

```
sudo aptitude remove automatix2
sudo aptitude update
sudo aptitude install automatix2
```
Now, your automatix2 should be working...

---

### Post by robtherich8 on 2006-12-16
Thank you. That seems to have fixed the problem with Automatix. It's busily downloading a whole load of mplayer stuff! I wonder how those troublesome extra lines appeared (and I wonder if I'll ever understand their significance). Perhaps I put them in while trying to fix another problem earlier in the week. Clearly I should have just come to these forums. Thanks again :)

---

