---
title: "Upgrading from Listen 0.6.2 to 0.6.3"
date: 2010-01-23
forum: Multimedia Software
---

### Post by zookrider on 2010-01-23
Would somebody be so kind as to give me step by step instructions on upgrading from Listen-0.6.2 to 0.6.3

I downloaded the 0.6.3 file from [http://www.listen-project.org/downloads/]("http://www.listen-project.org/downloads/"), but it looks like I need to compile the upgrade from source and I'm not comfortable yet doing that without guidance. 

Thanks in advance.

---

### Post by user1397 on 2010-01-23
> **zookrider said:**
> Would somebody be so kind as to give me step by step instructions on upgrading from Listen-0.6.2 to 0.6.3

I downloaded the 0.6.3 file from [http://www.listen-project.org/downloads/](http://www.listen-project.org/downloads/), but it looks like I need to compile the upgrade from source and I'm not comfortable yet doing that without guidance. 

Thanks in advance.it is really rather simple.

ok first extract the tar file somewhere (let's say your desktop for this example)

then in a terminal type: ```
cd ~/Desktop/listen-0.6.3/
./configure
make
sudo make install
```each line after the other.

---

### Post by zookrider on 2010-01-23
> **ubuntuman001 said:**
> it is really rather simple.

ok first extract the tar file somewhere (let's say your desktop for this example)

then in a terminal type: ```
cd ~/Desktop/listen-0.6.3/
./configure
make
sudo make install
```each line after the other.

First, thank you for your help.

I extracted the tar file to my desktop no problem, but when i started entering code in the terminal I got the following:

> michael@michael-laptop:~$ cd ~/Desktop/listen-0.6.3/
michael@michael-laptop:~/Desktop/listen-0.6.3$ ./configure
bash: ./configure: No such file or directory

Did I miss something?

A quick ls -l check gives me this:

> michael@michael-laptop:~/Desktop/listen-0.6.3$ ls -l
total 72
-rw-r--r-- 1 michael michael  4676 2009-07-30 12:21 check.py
-rw-r--r-- 1 michael michael  1917 2009-07-30 12:21 copy
drwxr-xr-x 3 michael michael  4096 2009-07-30 12:21 data
-rw-r--r-- 1 michael michael 18011 2009-07-30 12:21 gpl.txt
-rwxr-xr-x 1 michael michael   754 2009-07-30 12:21 header.tmpl
-rw-r--r-- 1 michael michael   731 2009-07-30 12:21 INSTALL
-rw-r--r-- 1 michael michael  5959 2009-07-30 12:21 Makefile
drwxr-xr-x 2 michael michael  4096 2009-07-30 12:21 misc
drwxr-xr-x 2 michael michael  4096 2009-07-30 12:21 mmkeys
drwxr-xr-x 2 michael michael  4096 2009-07-30 12:21 po
-rw-r--r-- 1 michael michael  2008 2009-07-30 12:21 README
drwxr-xr-x 9 michael michael  4096 2009-07-30 12:21 src
-rw-r--r-- 1 michael michael     0 2009-07-30 12:21 TODO


---

### Post by Yellow Pasque on 2010-01-23
Read the INSTALL file. Also, run this beforehand to make sure you have all the dependencies:
```
sudo apt-get build-dep listen
```
Or see if you can find a pre-built .deb: [https://launchpad.net/ubuntu/+ppas?name_filter=listen](https://launchpad.net/ubuntu/+ppas?name_filter=listen)

---

### Post by zookrider on 2010-01-23
> **Temüjin said:**
> Read the INSTALL file. Also, run this beforehand to make sure you have all the dependencies:
```
sudo apt-get build-dep listen
```
Or see if you can find a pre-built .deb: [https://launchpad.net/ubuntu/+ppas?name_filter=listen](https://launchpad.net/ubuntu/+ppas?name_filter=listen)

Solved now, thanks.

INSTALL file was screwing me up. I got an error message when I tried to 
> make install
but once I realized I had to 
> sudo make install
it was all good.

---

