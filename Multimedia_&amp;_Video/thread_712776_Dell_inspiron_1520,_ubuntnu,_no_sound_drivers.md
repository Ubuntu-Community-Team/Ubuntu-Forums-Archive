---
title: "Dell inspiron 1520, ubuntnu, no sound drivers"
date: 2008-03-02
forum: Multimedia &amp; Video
---

### Post by Bebrioks on 2008-03-02
Hi there, I have a problem.. Yesterday I bought new laptop, instantly instaled Linux ubuntu, but still have no sound :( I have codecs for sure, so there must be no drivers 4 sure. It was shown by my terminal..I should install ALSA drivers. Could anypne help me?
PS: I've seen posts with ALSA drivers, tried to solve this problem, but unfortunately nothin` happened.
Thank You for Your attention :) Hope to get a fast answer..:confused:

---

### Post by superprash2003 on 2008-03-03
try this ..[http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html](http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html)

---

### Post by linux23dragon on 2008-03-03
> **Bebrioks said:**
> Hi there, I have a problem.. Yesterday I bought new laptop, instantly instaled Linux ubuntu, but still have no sound :( I have codecs for sure, so there must be no drivers 4 sure. It was shown by my terminal..I should install ALSA drivers. Could anypne help me?
PS: I've seen posts with ALSA drivers, tried to solve this problem, but unfortunately nothin` happened.
Thank You for Your attention :) Hope to get a fast answer..:confused:


Hello Bebrioks

Open up a terminal and copy/paste this following command : -
```
sudo apt-get install linux-backports-modules-generic
```
Then reboot.

If you need any help to setup or use Ubuntu, then  remember that people (on this forum) have been using Ubuntu for many years.  These people have already have solutions for most issues (if not all of the issues) posted on the Ubuntu forums.  Here is some examples:-

HDA Soundcard fix :- [http://ubuntuforums.org/showthread.php?t=530374](http://ubuntuforums.org/showthread.php?t=530374)
Ubuntu-7.10 support:- [http://ubuntuforums.org/showthread.php?t=577469](http://ubuntuforums.org/showthread.php?t=577469)
Ubuntu-7.04 and 7.10 support:- [http://ubuntuforums.org/showthread.php?t=501195](http://ubuntuforums.org/showthread.php?t=501195)

---

### Post by Bebrioks on 2008-03-07
Thanks, that worked :)

---

### Post by MarcusCarabas on 2008-03-24
> **linux23dragon said:**
> Hello Bebrioks

Open up a terminal and copy/paste this following command : -
```
sudo apt-get install linux-backports-modules-generic
```
Then reboot.

If you need any help to setup or use Ubuntu, then  remember that people (on this forum) have been using Ubuntu for many years.  These people have already have solutions for most issues (if not all of the issues) posted on the Ubuntu forums.  Here is some examples:-

HDA Soundcard fix :- [http://ubuntuforums.org/showthread.php?t=530374](http://ubuntuforums.org/showthread.php?t=530374)
Ubuntu-7.10 support:- [http://ubuntuforums.org/showthread.php?t=577469](http://ubuntuforums.org/showthread.php?t=577469)
Ubuntu-7.04 and 7.10 support:- [http://ubuntuforums.org/showthread.php?t=501195](http://ubuntuforums.org/showthread.php?t=501195)

Thanks a bunch for sorting this out. I hadn't had much luck trying to get my soundcard and speakers going under Gutsy until I used the solution you posted. I have a question, however. I had been attempting the solution given on this site: [http://taufanlubis.wordpress.com/2007/11/26/fix-no-sound-for-ubuntu-in-toshiba-satellite-a205-s4707/](http://taufanlubis.wordpress.com/2007/11/26/fix-no-sound-for-ubuntu-in-toshiba-satellite-a205-s4707/)

The steps here basically involve downloading, making and installing the alsa driver, library and utilities that are available for download.  I went through the steps but when it came to inserting the utils into the kernel (At least that's what I thought I was doing) I hit a wall. That;s when I came across this post - followed the solution here and everything worked out fine. But, my question is - what about all those alsa driver, lib and util files? Can I simply delete them?

I'm sorry if this seems like a really ridiculous thing to ask - but I am very new to this and am not quite sure if  "linux-backports-modules-generic" needs to make use of any of the files mentioned above.

Once again, thanks for all the help :)
Marcus Carabas

---

### Post by gigo6000 on 2008-04-03
> **linux23dragon said:**
> Hello Bebrioks

Open up a terminal and copy/paste this following command : -
```
sudo apt-get install linux-backports-modules-generic
```
Then reboot.

If you need any help to setup or use Ubuntu, then  remember that people (on this forum) have been using Ubuntu for many years.  These people have already have solutions for most issues (if not all of the issues) posted on the Ubuntu forums.  Here is some examples:-

HDA Soundcard fix :- [http://ubuntuforums.org/showthread.php?t=530374](http://ubuntuforums.org/showthread.php?t=530374)
Ubuntu-7.10 support:- [http://ubuntuforums.org/showthread.php?t=577469](http://ubuntuforums.org/showthread.php?t=577469)
Ubuntu-7.04 and 7.10 support:- [http://ubuntuforums.org/showthread.php?t=501195](http://ubuntuforums.org/showthread.php?t=501195)

Thank you very much , I didn't think it would be that easy :) now everything works in my inspiron. Ubuntu rocks!

---

