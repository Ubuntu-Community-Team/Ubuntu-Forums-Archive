---
title: "Mythexport will not install?"
date: 2014-08-15
forum: Mythbuntu
---

### Post by schnabea on 2014-08-15
Hello all,

I am running 14.04.1 with mythtv 0.27 and every time I try to enable mythexport I get an installation error. The basic message is "mkdir: missing operand
 Try `mkdir --help' for more information." As seen in this [bug report]("https://bugs.launchpad.net/ubuntu/+source/mythexport/+bug/1079972")

Has anyone found a solution for this? All the googling I've done has shown multiple reports of this issue, but I haven't found a solution yet...

---

### Post by t8-launchpad on 2015-07-09
Can't help with a solution, but also have the same problem on 2 clean installs of Mythbuntu 14.04.1

---

### Post by blm-ubunet on 2015-07-10
The second search result leads to this thread:
[http://ubuntuforums.org/showthread.php?t=2274131&highlight=mythexport](http://ubuntuforums.org/showthread.php?t=2274131&highlight=mythexport)
The OP of that thread never reported back if it worked..

If the bug is the same as the above link then the bug seems to be a simple typo.
The mythtv working folder in /home/ is .mythtv & an extra dot has been inserted here & has messed up the folder path.

Does that linked post solve the install problem ?

---

### Post by 5imon on 2016-03-27
I am also struggling to overcome this bug on clean installs of mythbuntu 0.27. The link provided above didn't solve my problem. Has anybody got this working yet? Thanks in advance for any suggestions.

---

### Post by blm-ubunet on 2016-03-27
Did you create (if missing) the 2 folders & then run
```
sudo dpkg-reconfigure mythexport
```
?

---

### Post by 5imon on 2016-03-27
Thanks blm-ubunet for your reply. I did create the folders, the /home/mythtv/.mythtv folder already existed. Then issuing the command:

sudo dpkg-reconfigure mythexport

returned the following

dpkg-query: package 'mythexport' is not installed and no information is available
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: mythexport is not installed

then

sudo apt-get and sudo apt-get install then took me no further in solving the install problem

---

### Post by 5imon on 2016-03-27
the above should have stated sudo apt-get update and sudo apt-get install mythexport

---

### Post by blm-ubunet on 2016-03-27
Download the .deb package & edit one of the scripts..

The problem is reported to be "mythexport/dir in debconf's config.dat is empty"
```
mythexport.postinst:
...
case "$1" in
    configure)
    . /usr/share/debconf/confmodule

    db_get mythexport/dir
    dir="$RET"
--    if [ -n $dir ]; then
++   if [ "x$dir" != "x" ]; then
       mkdir -p $dir

        chown mythtv:mythtv $dir || true
```
Then install your modified .deb with "gdebi".

---

### Post by 5imon on 2016-03-28
Thanks again for your continued support. Your help is very much appreciated.

I've seen what you've now suggested elsewhere but still don't know how to start implementing this fix. Could you possibly provide me with a few explicit steps to follow? i.e the command to download the particular .deb package and also the name of the file to edit etc?

---

### Post by 5imon on 2016-04-19
For those following this thread, and also suffering the same MythExport bug, I have attempted the above hinted solution without any real joy whatsoever. Btw this bug work around was also listed at


[https://bugs.launchpad.net/ubuntu/+source/mythexport/+bug/1079972](https://bugs.launchpad.net/ubuntu/+source/mythexport/+bug/1079972)


I copied and then extracted the *.deb file, from /var/cache/apt/archives/mythexport_2.2.4-0ubuntu2_amd64.deb, using the approach listed here:


[http://news.softpedia.com/news/How-to-Repack-Deb-Files-on-Debian-and-Ubuntu-404930.shtml](http://news.softpedia.com/news/How-to-Repack-Deb-Files-on-Debian-and-Ubuntu-404930.shtml)


Once extracted I carefully modified the file in "postinst" by replacing the single line:


if [ -n $dir ]; then


with


if [ "x$dir" != "x" ]; then




Once the package was re-built I could then install this package file using gdebi. However, although it can now install it solved nothing as MythExport remains completely broken. Every time the Mythtbuntu control centre is opened a message box will appear complaining about the MythExport addon; it states that it will disable it. Very frustrating. MythExport cannot then be enabled in the mythtbuntu control centre.




I have tried re-installing Mythbuntu 0.27 from scratch and the bug remains.
I've even tried installing Mythbuntu 0.28 and the bug is still present.
I've tried installing MythTV on Ubuntu 15.4 and the bug remains.


It seems with all the MythTV updates that come in that MythExport has been well and truly forgotten about.

Am I doing something wrong? Has anyone managed to get MythExport installed and working? Maybe the solution is to ditch Mythbuntu altogether and compile MythTV from scratch?

---

### Post by blm-ubunet on 2016-04-28
Getting the package to install is just one part of the problem.
And no way it's going to work in 16.04.

mythexport is not part of mythtv nor part of mythbuntu..
mythexport package is hosted on ubuntu launchpad.
[https://launchpad.net/mythexport](https://launchpad.net/mythexport)
Installing mythtv from source makes no difference.

If mythexport was re-homed into mythbuntu then maybe it could get some TLC.

Note that mythbuntu-0.28/*buntu 16.04 will break mythexport even further due to changes in mysql, php & python versions (& probably ffmpeg libav* changes).

---

