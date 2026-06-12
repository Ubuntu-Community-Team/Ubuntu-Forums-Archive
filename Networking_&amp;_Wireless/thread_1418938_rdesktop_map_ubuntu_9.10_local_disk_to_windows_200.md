---
title: "rdesktop map ubuntu 9.10 local disk to windows 2008 server"
date: 2010-03-01
forum: Networking &amp; Wireless
---

### Post by paua_fritter on 2010-03-01
I'm a newbie and would appreciate some help:

Using the following command, I can access a windows 2008 server:

rdesktop -u myusername -d mydomain -p - -fP -r sound:local -r disk:myhome=/home/myhome serveraddress

connection works fine, and to start with I can see my local disk "\\tsclient\myhome" and navigate around + open files.

If I try to delete a file or rename a folder, I get an Error 0x8007048F:The device is not connected.

After this, I can no longer access the local disk. It says: 

"\\tsclient\myhome is not accessible. You might not have permission to use this network resource. Contact the administrator of this server to find out if you have access permissions.
Attempt to access invalid address."

As I understand it, I should be contacting myself about permissions... Can anyone tell me what I need to do on my local ubuntu machine to fix this?

---

### Post by paua_fritter on 2010-03-02
.

---

### Post by DAKnn on 2010-03-13
> **paua_fritter said:**
> .
I have some PROBLEM too!

---

### Post by abohsin on 2010-03-13
Have you tried changing permissions on the directory you are sharing during rdesktop to 777 to test if the problem really is permissions. Try this from a terminal:
chmod -fR 777 <your_directory>

Although I doubt it is a permissions problem.

---

### Post by paua_fritter on 2010-03-15
Don't want to change permissions of all files and directories. I used chmod to change the permissions of "myhome" and then created an empty text file in "myhome" using

touch myfile.txt
sudo chmod 777 myfile.txt

I then logged on to the windows 2008 server. I can open this text file, type something, save it, even save it as another file. But I cannot delete it...

---

### Post by vukoxx on 2010-05-21
it's one of many more bugs in rdesktop.
in [http://www.opensource-archive.org/archive/index.php/t-170648.html](http://www.opensource-archive.org/archive/index.php/t-170648.html)
someone says [http://sourceforge.net/tracker/index.php?func=detail&aid=2812158&group_id=24366&atid=381349](http://sourceforge.net/tracker/index.php?func=detail&aid=2812158&group_id=24366&atid=381349) would be the corresponding patch...
but infact you can find a few different patches on sourceforge regarding this issue :(

---

### Post by Jack-87 on 2010-08-04
any solution or work around yet... I am having the same issue :(

---

### Post by profeta81 on 2011-11-18
hello hello!

had the same problem on Ubuntu 10.10 connecting to a Windows 7 machine.

Just to report my brute force solution to the problem:

1 - uninstall the ubuntu package

# sudo apt-get --purge remove rdesktop

2 - download latest rdestop (currently 1.7.0) from [www.rdesktop.org](www.rdesktop.org) website (1.7 includes patch mentioned in previous post)

3 - untar, configure, compile, and install with usual commands:

# untar rdesktop-1.7.0.tar.gz
# cd rdesktop-1.7.0
# ./configure
# make
# sudo make install

p.s. for tscclient users: uninstalling ubuntu rdesktop package will remove tscclient as well so afterwards you will either have to download and install tscclient yourselves ([http://sourceforge.net/projects/tsclient/](http://sourceforge.net/projects/tsclient/))  or simply use command line to start rdesktop...

hope this helps!
cheers!

---

### Post by ahouchens on 2011-11-29
Tried profeta81's steps without any success.

I have Ubuntu 11 and I am experiencing this issue on Windows Vista Ultimate for the remote machine.

I see other people are recommending two other possible solutions:

1. INstalling Ext2Fsd on the remote windows vista ultimate machine.
2. Configuring Samba on Ubuntu.

Will either of these solutions work? I suppose I'm trying to avoid dead end journeys.

---

### Post by prcyans on 2012-01-23
same problem
ubuntu 10.04LTS rdesktop to windows7-64bit
same problem

using profeta81 methods
i.e.,
use latest rdesktop
(websit did quote solving problems with 64 bit)
verified
problem solved

thanks

---

