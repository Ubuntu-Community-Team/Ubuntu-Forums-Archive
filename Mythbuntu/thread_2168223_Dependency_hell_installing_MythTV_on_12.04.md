---
title: "Dependency hell installing MythTV on 12.04"
date: 2013-08-16
forum: Mythbuntu
---

### Post by An_Angry_Penguin on 2013-08-16
I am trying to install MythTV on a pre-existing Ubuntu 12.04 computer, apologies if I am posting in the wrong section.  I am getting a dependency problem with mythtv-frontend message when I did:

sudo apt-get install mythtv

so I did sudo-apt-get install mythtv-frontend and I get:

The following packages have unmet dependencies:
 mythtv-frontend : Depends: libxml-simple-perl but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

Trying to install libxml-simple-perl gives me:

Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libxml-simple-perl : Depends: libxml-sax-perl but it is not going to be installed
                      Depends: libxml-libxml-perl but it is not going to be installed or
                               libxml-sax-expat-perl but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

I am getting tired of going down the rabbit hole, has this happened to anyone else?

---

### Post by tgm4883 on 2013-08-17
That package is in the main Ubuntu repository, so it looks like somehow you disabled it.

[http://packages.ubuntu.com/precise/libxml-simple-perl](http://packages.ubuntu.com/precise/libxml-simple-perl)


Take a look at you software sources (or /etc/apt/sources.list) and see if any of the default repos are disabled

---

### Post by An_Angry_Penguin on 2013-08-17
I solved the problem through more googling, apparently the following lines needed to be in my sources list, quoted from [https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/1052033](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/1052033)

[TABLE]
[TR]
[TD][jidping (jidping-h)]("https://launchpad.net/%7Ejidping-h")             wrote             on 2013-04-09:                          [/TD]
                       [TD="class: bug-comment-index"]           [ #3]("https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/1052033/comments/3")           [/TD]
         [/TR]
            [/TABLE]
                               I solved my problem by adding repos below in /etc/apt/sources.list. they were missing in my os image.
 deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) precise-updates main restricted
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) precise-updates universe
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) precise-updates multiverse

              

Hopefully this will help anyone else who has this problem.

---

### Post by tgm4883 on 2013-08-18
> **An_Angry_Penguin said:**
> I solved the problem through more googling, apparently the following lines needed to be in my sources list, quoted from [https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/1052033](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/1052033)

[TABLE]
[TR]
[TD][jidping (jidping-h)]("https://launchpad.net/%7Ejidping-h")             wrote             on 2013-04-09:                          [/TD]
                       [TD="class: bug-comment-index"]           [ #3]("https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/1052033/comments/3")           [/TD]
         [/TR]
            [/TABLE]
                               I solved my problem by adding repos below in /etc/apt/sources.list. they were missing in my os image.
 deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) precise-updates main restricted
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) precise-updates universe
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) precise-updates multiverse

              

Hopefully this will help anyone else who has this problem.

So in other words, you fixed it by adding back in the default repos that you somehow previously disabled.

---

