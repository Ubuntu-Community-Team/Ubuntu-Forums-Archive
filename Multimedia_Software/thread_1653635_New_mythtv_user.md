---
title: "New mythtv user"
date: 2010-12-27
forum: Multimedia Software
---

### Post by sami8519 on 2010-12-27
Hi,

I have just installed mythbuntu based on ubuntu 10.10 and I am wondering where I have to put the remote control configuration file, lircrc.conf, I mean what is the path of this file?

Thanks and Best Regards
Sami

---

### Post by sami8519 on 2010-12-27
no body knows:(

---

### Post by VonSpyder on 2010-12-27
I would be interested to know this as well...assuming i ever get linux support for my tv tuner.

---

### Post by sami8519 on 2010-12-27
Still waiting!!

---

### Post by MartyBuntu on 2010-12-27
You've read the MythTV documentation on lirc?

---

### Post by sami8519 on 2010-12-27
I did. It is said to be
cp lircrc.example ~/.lircrc

what I wanted to know is where the /.lircrc folder is on mythbuntu 10.10?

Regards
Sami

---

### Post by BicyclerBoy on 2010-12-28
The tilde (~) is a linux abbreviation for home folder for the current user.
The slash (/)  is root of filesystem.

So ~/.lircrc     == /home/myth/.lircrc
assuming user-name is "myth".

I have not used mythbuntu but..
Beware that your mythbuntu/mythtv may run as another user.
On my system *buntu mythtv runs as "mythtv", the main user is another user.

Check how many folders are in the /home folder.

I thought mythbuntu had a lirc configuration tool that did every thing including sliced bread/toast & coffee (ubuntu of course) ?

---

### Post by AKADAP on 2010-12-29
> **sami8519 said:**
> I did. It is said to be
cp lircrc.example ~/.lircrc

what I wanted to know is where the /.lircrc folder is on mythbuntu 10.10?

Regards
Sami

Since you did not know what '~' means, I will assume you are a complete newbie, and also have no idea what the '.' at the beginning of the file name does.

A period at the beginning of a filename makes the file a hidden file. Meaning that if you do 'ls' to list the files in a directory, files that begin with a period will not show up. you must do 'ls -a' to list all the files in a directory, including the hidden files.

---

