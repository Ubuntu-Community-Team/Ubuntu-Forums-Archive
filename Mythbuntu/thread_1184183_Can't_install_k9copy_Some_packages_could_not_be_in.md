---
title: "Can't install k9copy: Some packages could not be installed"
date: 2009-06-10
forum: Mythbuntu
---

### Post by laffinet on 2009-06-10
I hope I'm not in breach of any forum rules (if so, I do apologise). I've posted this problem some days ago in the Absolute Beginners forum but didn't get any responses. Since it's related to my Myth machine I thought I'll try here and post again. So here it goes:

Hi !

I'm running Mythbuntu 9.04 from a fresh install and tried to install k9copy, however when I run

```
sudo apt-get install k9copy
``` 

I get the following errors

```
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  k9copy: Depends: kdebase-runtime (>= 4:4.1.96) but it is not going to be installed
          Depends: kdelibs5 (>= 4:4.1.96) but it is not going to be installed
          Depends: libqt4-svg (>= 4.5.0~+rc1) but it is not going to be installed
E: Broken packages
```

I've got this line in the sources.list file:

```
deb http://au.archive.ubuntu.com/ubuntu/ jaunty main universe restricted multiverse
```

Any idea what could cause this and what I can do to resolve this ?

When trying to install the package independently (sudo apt-get install kde-base runtime) I get the same error:

```
The following packages have unmet dependencies:
  kdebase-runtime: Depends: kdelibs5 (>= 4:4.2.1) but it is not going to be installed
                   Depends: libqt4-svg (>= 4.5.0~+rc1) but it is not going to be installed
                   Depends: kdebase-runtime-bin-kde4 (= 4:4.2.2-0ubuntu1) but it is not going to be installed
E: Broken packages
```

I did update before trying to install (sudao apt-get update)

---

### Post by laffinet on 2009-06-14
Anyone ?

---

### Post by desktopj on 2009-06-15
Sounds like a broken installation or db. Something may have become scrambled. 

From the [Apt-get Howto]("http://www.debian.org/doc/manuals/apt-howto/index.en.html#contents")
----------------
If an installation breaks in the middle of the process and you find that it's no longer possible to install or remove packages, try running these two commands:

     # apt-get -f install
     # dpkg --configure -a

And then try again. It may be necessary to run the second of the above commands more than once. This is an important lesson for those adventurers who use `unstable'.
-----------------

Also 'apt-get clean' can clear out your local archive cache and force new file downloads.

Good luck
Jeff

---

### Post by utar on 2009-06-15
Have you tried installing using the gui package manager.  In my experience this can give slightly more useful error messages.

I'm guessing the problem revolves round k9copy needing KDE to run whereas mythbuntu comes with xfce as the window manager.  If you install the kde meta-package this will install all the kde files and this may well fix the dependency issues.  However I'm not sure if installing kde will break anything.  So be **very careful** if you decide to do this.


Utar

---

### Post by laffinet on 2009-06-16
> **desktopj said:**
> Sounds like a broken installation or db. Something may have become scrambled. 

From the [Apt-get Howto]("http://www.debian.org/doc/manuals/apt-howto/index.en.html#contents")
----------------
If an installation breaks in the middle of the process and you find that it's no longer possible to install or remove packages, try running these two commands:

     # apt-get -f install
     # dpkg --configure -a

And then try again. It may be necessary to run the second of the above commands more than once. This is an important lesson for those adventurers who use `unstable'.
-----------------

Also 'apt-get clean' can clear out your local archive cache and force new file downloads.

Good luck
Jeff

Unfortunately, this didn't work. Still the same problem. 
I had no problem installing k9copy when I ran 8.10.
I'm reluctant to try the second solution suggested (installing kde), since I don't want to break anything and I can't see how this is the issue. Any dependencies should be sorted by apt-get.

Any other ideas ?

---

### Post by desktopj on 2009-06-16
I did a 'sudo apt-get install k9copy' from my xfce desktop (9.04 mythbuntu w/weekly mythtv updates). I got the following packages listed for install.
-----------------
The following extra packages will be installed:
  libboost-regex1.34.1 libicu38 mencoder mkvtoolnix twolame vamps
Suggested packages:
  mplayer-doc mkvtoolnix-gui
The following NEW packages will be installed:
  k9copy libboost-regex1.34.1 libicu38 mencoder mkvtoolnix twolame vamps
-------------------

Install ran error free -- except that it created a .kde directory that was owned by root (easily fixed) and doesn't show up on the menu (just ran from terminal). Starts up and looks ok to me.

So, I still feel that it's the package database.

---

### Post by laffinet on 2009-06-16
Thansk for your help and trying that.

Should I see any output when running 
apt-get -f install and
dpkg --configure -a ?

Because I didn't, command ran (I guess) and returned me to the prompt, no output, nothing.
I haven't had any problems installing other software. 
How would I be able to I fix the database ?

---

### Post by robert shearer on 2009-06-16
often there is no output when a command completes successfully.
Did you run..

```
sudo apt-get -f install
```
```
sudo dpkg --configure -a
```.

Have you tried then reloading and trying to install k9copy?

---

### Post by laffinet on 2009-06-16
Yes, did both (the second one quite a few times, as suggested by desktopj). Nothing changed, still the same problem.
Trying to instal k9copy results in the sam error messages as before.

---

### Post by robert shearer on 2009-06-16
From here...[https://help.ubuntu.com/community/K9Copy](https://help.ubuntu.com/community/K9Copy)

> Note that k9copy will work on KDE or gnome. 

and I see you are running xfce. (mythbuntu default)

You might try asking on the Mythbuntu forum..
[http://ubuntuforums.org/forumdisplay.php?f=301](http://ubuntuforums.org/forumdisplay.php?f=301)

EDIT OOps, misread subforum, you're already there.

---

### Post by laffinet on 2009-06-16
I understand that k9copy is a kde application. 
I should still be able to install it on a xfce machine and have done so successfully in the past (8.10). Note that desktopj has done this successfully, too.

---

### Post by desktopj on 2009-06-16
Just curious, when .kde directory was created in my home directory, it was assigned ownership of root.root instead of to me (odd). I had to reassign ownership.

What is the ownership/permissions of .kde in your home dir?

---

### Post by laffinet on 2009-06-17
There is no .kde directory in my /home

---

### Post by laffinet on 2009-06-20
Anyone ? Any other ideas ?

---

### Post by desktopj on 2009-06-22
Hi,

How about changing the server from 'deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) etc...


to 'deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) etc...

in sources.list? Maybe forcing apt-get to reload from a different url might clear things up. If it doesn't, retry all the previous
# apt-get -f install
# dpkg --configure -a 
along with apt-get update, clean and check

Let us know if that works.

As a side note: I remember once with RH4 I got stuck in a similar rpm hell, and after working on it for weeks, I just finally bit the bullet and reinstalled.

---

### Post by laffinet on 2009-06-22
Thanks for the suggestion. I tried various servers, didn't seem to make a difference. Might try everything again, just to be sure.

Not keen on reinstalling, only just did that when 9.04 came out.

---

### Post by ph_gachoud on 2011-03-18
For me it was resolved by removing a debian packages line on my sources.list that was for cinelera: 
# CINELERRA
#deb [http://www.debian-multimedia.org](http://www.debian-multimedia.org) sid main non-free
1) commented this line
2) apt-get clean
3) apt-get update
4) apt-get install k9copy
for me dvdrip was also not installing:
> pg@pipoTower: /media/datas/linux$ apti dvdrip
[sudo] password for pg: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 dvdrip : Depends: transcode (>= 2:1.0.2-0.8) but it is not going to be installed
          Depends: ffmpeg but it is not going to be installed
          Recommends: subtitleripper but it is not going to be installed
E: Broken packages

---

### Post by tgm4883 on 2011-03-18
> **ph_gachoud said:**
> For me it was resolved by removing a debian packages line on my sources.list that was for cinelera: 
# CINELERRA
#deb [http://www.debian-multimedia.org](http://www.debian-multimedia.org) sid main non-free
1) commented this line
2) apt-get clean
3) apt-get update
4) apt-get install k9copy
for me dvdrip was also not installing:

while your help is appreciated, please don't post in threads that are 1.5 years since the last post.

---

