---
title: "how to install mp3 decoder plugins in ubuntu"
date: 2009-12-04
forum: Multimedia Software
---

### Post by deepink on 2009-12-04
hello all,
i recently installed ubuntu 9.04 on my aspire 5738 which already have windows xp installed.
I cannot play mp3 with rythmbox. It gives me an error saying MPEG-1 Layer3 decoder not installed.
plz help with how to install decoders and plugins plus how to install other softwares..

thans in advance.
regards,
deepink.

---

### Post by dvlchd3 on 2009-12-04
Unfortunately due to copyright laws, Ubuntu is not allowed to have certain audio and video codecs installed by default.  However, they can make them available after installation.  Try these steps:

Add the medibuntu repository:
```

sudo wget http://www.medibuntu.org/sources.list.d/[your_distro].list --output-document=/etc/apt/sources.list.d/medibuntu.list
```
Replace '[your_distro]' with your distribution (i.e. jaunty for 9.04, karmic for 9.10, etc)

Import the gpg key.  You will receive a message saying the source could not be authenticated (or something like that) just say yes.
```

sudo aptitude update && sudo aptitude install medibuntu-keyring && sudo aptitude update
```

Install the w32codecs package and ubuntu-restricted-extras
```

sudo aptitude install w32codecs ubuntu-rectricted-extras
```

All done!

You may also want to check out this guide.  Its a great help to new Ubuntu users who want a functional desktop with the most typically used software.  (This is where the above came from.  I know its for 9.04, but if you follow the above when adding the medibuntu part, you should be ok with any other distro from ~8.04-9.10.)
[http://www.howtoforge.com/the-perfect-desktop-ubuntu-9.04](http://www.howtoforge.com/the-perfect-desktop-ubuntu-9.04)

---

### Post by deepink on 2009-12-04
i tried but it says ERROR 407:Proxy authentication Required.
and takes me back to my home directory..

help..

thank you.

---

### Post by byStanderone on 2009-12-04
...do a backport update, and install the ubuntu-restricted-extras

---

### Post by deepink on 2009-12-04
thanks for your response... but im an absolute beginner.
can you plz tell me how to  install the ubuntu-restricted-extras...


i tried what dvlchd3 had suggested.... 
 


d@dlaptop:~$ sudo wget [http://www.medibuntu.org/sources.list.d/jaunty.list](http://www.medibuntu.org/sources.list.d/jaunty.list) --output-document=/etc/apt/sources.list.d/medibuntu.list
--2009-12-04 21:43:01--  [http://www.medibuntu.org/sources.list.d/jaunty.list](http://www.medibuntu.org/sources.list.d/jaunty.list)
Resolving proxy1.pn.gbpuat.ac.in... 10.1.1.4
Connecting to proxy1.pn.gbpuat.ac.in|10.1.1.4|:8080... connected.
Proxy request sent, awaiting response... 407 Proxy Authentication Required
2009-12-04 21:43:38 ERROR 407: Proxy Authentication Required.






plz help.....




thanks,
Regards,
Deepink.

---

### Post by byStanderone on 2009-12-05
enable your backport by editing: sudo gedit /etc/apt/sources.list

uncomment the line: #deb [http://archive.ubuntu.com/ubuntu/hardy-backports](http://archive.ubuntu.com/ubuntu/hardy-backports)   
main restricted universe multiverse  (simply remove # before deb)

...save and exit, then sudo apt-get install ubuntu-restricted-extras...you can re-edit sources.list if you want to, and mark the line which you formerly unmarked. (i assume you are using hardy, if not so just change the word hardy to whatever version you are using...intrepid or whatever)

---

### Post by deepink on 2009-12-05
i may seem stupid.... but plz help i m havin hard time with this installations n all....
i tried and again got stuck....


d@dlaptop:~$ sudo apt-get install ubuntu-restricted-extras
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ubuntu-restricted-extras



what to do???
not happy:(

---

### Post by byStanderone on 2009-12-05
...patience is the key to everything, take your time. what version of ubuntu are u in? make sure that you have edited sources.list correctly.

---

### Post by deepink on 2009-12-06
hey i m using jaunty.....

still nothin worked

---

### Post by byStanderone on 2009-12-06
...ok, we'll do it thru another way, download and install the restricted extras from [http://packages.ubuntu.com/jaunty/ubuntu-restricted-extras](http://packages.ubuntu.com/jaunty/ubuntu-restricted-extras) maybe this would start-up things at the moment.

---

### Post by aysiu on 2009-12-06
> **deepink said:**
> i may seem stupid.... but plz help i m havin hard time with this installations n all....
i tried and again got stuck....


d@dlaptop:~$ sudo apt-get install ubuntu-restricted-extras
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ubuntu-restricted-extras



what to do???
not happy:(
Can you post the output of these two commands? ```
sudo apt-get update
cat /etc/apt/sources.list
```

---

### Post by deepink on 2010-01-25
d@d-laptop:~$ sudo apt-get update
E: Type 'universe' is not known on line 7 in source list /etc/apt/sources.list

---

### Post by aysiu on 2010-01-25
> **deepink said:**
> d@d-laptop:~$ sudo apt-get update
E: Type 'universe' is not known on line 7 in source list /etc/apt/sources.list Your sources.list file is messed up.

Can you paste the command ```
cat /etc/apt/sources.list
``` into the terminal and post the output back here?

---

### Post by Gakhar on 2013-05-01
I have a similar problem in ubuntu.

$ sudo apt-get update

Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) maya InRelease
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise InRelease
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates InRelease
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security InRelease
Ign [http://archive.canonical.com](http://archive.canonical.com) precise InRelease
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise InRelease
Ign [http://dl.google.com](http://dl.google.com) stable InRelease
Err [http://packages.linuxmint.com](http://packages.linuxmint.com) maya Release.gpg
  Something wicked happened resolving 'packages.linuxmint.com:http' (-5 - No address associated with hostname)


$ cat /etc/apt/sources.list
deb [http://packages.linuxmint.com/](http://packages.linuxmint.com/) maya main upstream import
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-updates main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security main restricted universe multiverse
deb [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) precise partner
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) precise free non-free

#deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) precise-getdeb apps
#deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) precise-getdeb games

---

### Post by oldos2er on 2013-05-01
If a post is older than a year or so and hasn't had a new reply in that  time, instead of replying to it, create a new thread. In the software  world, a lot can change in a very short time, and doing things this way  makes it more likely that you will find the best information. You may  link to the original discussion in the new thread if you think it may be  helpful.

---

