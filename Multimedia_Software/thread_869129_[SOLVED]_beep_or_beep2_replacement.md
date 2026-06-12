---
title: "[SOLVED] beep or beep2 replacement"
date: 2008-07-24
forum: Multimedia Software
---

### Post by victorbrca on 2008-07-24
Anyone knows of a utility similar to SmoothWall's beep2 that I can use to play numeric frequencies and wavelenght?

This is the type of file I'd like to play:

```
#!/usr/local/bin/beep
500 100
0 100
750 100
0 100
1000 100
```

Thanks,

Vic.

---

### Post by victorbrca on 2008-07-24
Found a package for OpenSuse [here]("http://rpm.pbone.net/index.php3/stat/4/idpl/5939587/com/beep2-1.2a-1.1.i386.rpm.html"), and here's a [link]("http://www.daedalus.co.uk/perl/beep.pl") on how to convert Nokia's RTTL to this file format. 

Any ideas?

---

### Post by victorbrca on 2008-07-25
If anyone ever comes around this here's the fix.

Download the rpm package from [here]("ftp://ftp.pbone.net/mirror/ftp5.gwdg.de/pub/opensuse/repositories/home:/netmask/Fedora_8/i386/beep2-1.2a-1.1.i386.rpm").

Install alien:

```
sudo apt-get install alien
```


Go to the folder were you downloaded the package and convert it to .deb and install it:

```
sudo alien -k beep2-1.2a-1.1.i386.rpm
sudo dpkg -i beep2_1.2a-1.1_i386.deb
```

Create a folder under, for example /home/user/etc/sound, then create a file. Open the file and paste the following code:

```
#! /usr/bin/beep2
# Name: Star Wars Theme 1
587 166
587 166
587 166
784 999
1174 999
1046 166
987 166
880 166
1568 999
1174 499
1046 166
987 166
880 166
1568 999
1174 499
1046 166
987 166
1046 166
880 666
0 333
587 166
587 166
587 166
784 999
1174 999
1046 166
987 166
880 166
1568 999
1174 499
1046 166
987 166
880 166
1568 999
1174 499
1046 166
987 166
1046 166
880 666

```


Make the file executable:

```
chmod a+x [filename]
```


Run the file from a terminal window:

```
./[filename]
```


Vic.

---

