---
title: "Nvdia drivers, where and how?"
date: 2006-01-05
forum: Multimedia &amp; Video
---

### Post by AgonxOC on 2006-01-05
I just got Linux working today after two painful days of bad ISO CD images and other things. I need to find the drivers for the video card and how to intall it...

Thanks

Alex

---

### Post by Omnios on 2006-01-05
For nvidia you need to add extra repositories

this link is dated as the there are slight differences but basicly all you have to do is uncomment, (remove # from addresses in the sources list)

This is from the older release but tells you what to do, do not use the addresses on this page
[http://ubuntuguide.org/#extrarepositories]("http://ubuntuguide.org/#extrarepositories")


 this link has the recent sources.list
[http://ubuntuforums.org/showthread.php?t=92672]("http://ubuntuforums.org/showthread.php?t=92672")

and read the Unofficial Ubuntu users guid on installing the nvidia driver.

[http://ubuntuguide.org/#installnvidiadriver]("http://ubuntuguide.org/#installnvidiadriver")

---

### Post by AgonxOC on 2006-01-05
Now I get the drill, but I am not sure where to go to type the commands...

sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
sudo gedit /etc/apt/sources.list

Where do I go to type the command as listed above..

Alex

---

### Post by Omnios on 2006-01-05
In the terminal

---

### Post by AgonxOC on 2006-01-05
Ok found the terminal and it has already: 

alex@ubuntu:~$

I paste:

sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup

And it promps me for the password, now once I type it, it doesnt do anything, Why?

Alex

---

### Post by Omnios on 2006-01-05
[QUOTE=AgonxOC]Ok found the terminal and it has already: 

alex@ubuntu:~$

I paste:

sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup

And it promps me for the password, now once I type it, it doesnt do anything, Why?

Alex[/QUOTE]

 If it whent back to alex@ubuntu: it did do something it just does not tell you so.

---

### Post by AgonxOC on 2006-01-05
Got it...

Now I get this for the repositories

---------------------------------------------------------------------------------------------------
deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

---------------------------------------------------------------------------------------------------

I am using 5.10 and the link is for 5.04 What should I do some of the lines are non excistant..

1 Find this section

...
## Uncomment the following two lines to fetch updated software from the network
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

2 Replace with the following lines

## Uncomment the following two lines to fetch updated software from the network
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

## Backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted


Alex

---

### Post by Omnios on 2006-01-05
As I said above dont use the 5.04 what you want is the 5.10 I just gave you the link because it tells you how to do it. 

 This a copy of my sources.list

 ```
 

## Major bug fix updates produced after the final release of the
## distribution.
 deb http://ca.archive.ubuntu.com/ubuntu breezy-updates main restricted
 deb-src http://ca.archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
 deb http://ca.archive.ubuntu.com/ubuntu breezy universe
 deb-src http://ca.archive.ubuntu.com/ubuntu breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
 deb http://ca.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
 deb-src http://ca.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

 deb http://security.ubuntu.com/ubuntu breezy-security main restricted
 deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

# deb http://security.ubuntu.com/ubuntu breezy-security universe
# deb-src http://security.ubuntu.com/ubuntu breezy-security universe

 deb http://ca.archive.ubuntu.com/ubuntu breezy multiverse

```

 Basicly you want to uncomment the restricted and possibly multiverse by removing the # in front of them.

---

### Post by AgonxOC on 2006-01-05
So I did that same you have there.. Thanks alot... Once I do this do I have to do it again?

Alex

PS I am trying to install Real Player and I hung in 

&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring realplayer &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;
 &#9474;                                                                                                                                                                       &#9474;
 &#9474; Cannot find the downloaded Real Player file.                                                                                                 &#9474;
 &#9474;                                                                                                                                                                       &#9474;
 &#9474; The file /desktop/rp8_linux20_libc6_i386_cs2_rpm does not exist, or it                                                        &#9474;
 &#9474; is corrupt. You may have downloaded the wrong file, or put it in the                                                            &#9474;
 &#9474; wrong location. Please try again.                                                                                                                  &#9474;
 &#9474;                                                                                                                                                                       &#9474;
 &#9474; If the file you downloaded has a different name, the filename may have                                                    &#9474;
 &#9474; changed since this installer was last updated. You can still try to use                                                          &#9474;
 &#9474; the installer; just rename the file you downloaded to                                                                                   &#9474;
 &#9474; /desktop/rp8_linux20_libc6_i386_cs2_rpm . Note that if you do this,                                                           &#9474;
 &#9474; there is no guarantee the installer will work.                                                                                                  |

What do I need to do?
And I highly appreciate your help..

---

### Post by Omnios on 2006-01-05
After editing your sources list run.

 ```
sudo apt-get update
```

 This updates the software list to your sources.list

---

### Post by AgonxOC on 2006-01-05
Where can I find rp8_linux20_libc6_i386_cs2_rpm.... I cannot seem to find it...

Alex

---

### Post by handy on 2006-01-05
I took the easy way out re: nVidia commercial drivers & a pile of other things & used **Automatix**

[http://ubuntuforums.org/forumdisplay.php?f=77](http://ubuntuforums.org/forumdisplay.php?f=77)

Great for noobs like me, & you can still get your hands dirty in the OS everyday if you want...  :p 

**[EDIT:]**  Automatix is perfectly safe to use on 32 AND 64bit Breezy.

Cheers,

handy

---

