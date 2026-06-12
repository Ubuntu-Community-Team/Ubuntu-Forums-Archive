---
title: "How to install Live555 package in Ubuntu Hardy"
date: 2009-11-12
forum: Multimedia Software
---

### Post by zelalem on 2009-11-12
Hi, I don't know if it the proper forum to ask this question. I just downloaded the [live555-latest.tar.gz]("http://www.live555.com/liveMedia/public/live555-latest.tar.gz") file and unzipped it and following the guideline on their website I created a make file using genMakefile script (it is a general script for all linux platforms). Then when I run the make command it failed. I got two errors, which are:
CC: command not found and also [rtcp_from_spec.o] error 127. 

I changed the C compiler from cc to gcc (which is what i have on my ubuntu hardy machine) and also for cpp compiler, i changed g++ in the conf.linux file. But without success. Anyone tried to install this package? Please tell me how to install teh package in Ubuntu Hardy?

Thank you.

Best regards,

Zelalem

---

### Post by andrew.46 on 2009-11-12
Hi zelalem,

> **zelalem said:**
>  Please tell me how to install teh package in Ubuntu Hardy?

Easiest way is first ensure you have the appropriate compiler:

```

$ sudo apt-get install build-essential

```

then make sure you* don't *have the repository live555 libraries on your system:

```

$ sudo apt-get remove liblivemedia-dev

```

and finally download, build and install the libraries:

```

$ cd $HOME
$ wget http://www.live555.com/liveMedia/public/live555-latest.tar.gz
$ tar xvf live555-latest.tar.gz
$ cd live
$ ./genMakefiles linux
$ make
$ sudo cp -r $HOME/live /usr/lib
$ make clean

```

and that should get you going :).

Andrew

---

### Post by zelalem on 2009-11-13
Hi Andrew, thank you for your prompt response. I followed your step and I got teh following error.
/usr/bin/ld: cannot find -lgcc_s
[IMG]file:///tmp/moz-screenshot.jpg[/IMG]collect2: ld returned 1 exit status
make[1]: *** [testMP3Streamer] Error 1
make[1]: Leaving directory '/home/zelaelm/live/testProgs'
make: *** [all] Error 2

I no longer get the previous error. I hope I am closer to the solution. Give me your advice how I can solve this.

Zelalem

---

### Post by andrew.46 on 2009-11-13
Hi zelalem,

> **zelalem said:**
> 
```
/usr/bin/ld: cannot find -lgcc_s
```


You have a problem with your compiler by the look of it and unfortunately I am far from an expert with such things :-(. On my Hardy system the compiler is as follows:
```

andrew@skamandros:~$ **[COLOR="Red"]g++ --version[/COLOR]**
g++ (GCC) 4.2.4 (Ubuntu 4.2.4-1ubuntu4)
Copyright (C) 2007 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
```

Can you check that you have the same? It would probably be an idea to reverse any changes to configuration files that you have made in attempting to compile this package, the Hardy defaults are sufficient to compile Live555 with no extra intervention.

All the best,

Andrew

---

### Post by zelalem on 2009-11-13
Hi Andrew you are right that is the problem. Mine is 3.4.6. You know I had problem with apt-get package manager (I was not able to use it b/c of the mess caused by live555) and I was trying to fix it by installing various packages manually. I will try to install the version that exist on your machine. If I face any problem I will inform you.

Thank you again for your assistance.

Zelalem

---

### Post by andrew.46 on 2009-11-13
Hi zelalem,

> **zelalem said:**
> Hi Andrew you are right that is the problem. Mine is 3.4.6. You know I had problem with apt-get package manager (I was not able to use it b/c of the mess caused by live555) and I was trying to fix it by installing various packages manually. I will try to install the version that exist on your machine.

Good to know that at least the problem is known :). Good news is that the compiler I have on Hardy is simply the one that is installed by default with the *build-essential* meta package.

All the best,

Andrew

---

### Post by zelalem on 2009-11-14
Hi Andrew, thank you for your help. I think now it is working. You know I had difficulty removing the g++ compiler (even when after i installed the latest version the previous version was referred when i say "g++ --version"). Anyway, i then manually removed teh old file from /usr/bin and the correct version is now referrred. I also had teh same problem with gcc. I used a similar technique and corrected that as well. All this mess has happened b/c I had manually installed some packages so as to install the live555 software. 

Another thing the linker which gave me a hard time is /usr/local/lib/libgcc_s.so was also referring to a non existent file (libgcc_s.so.1 which is teh linker of the previous version of gcc). So I removed the link and then created anotehr link that points to teh linker of version 4.2 which i found in /usr/lib/gcc/i486-linux-gnu/4.2/libgcc_s.so). And now I compiled it there is no error.

Anyway althought there are still some mesterious things I learned a lot. Thank you again.

Cheers

---

### Post by andrew.46 on 2009-11-14
Hi zelalem,

> **zelalem said:**
> Hi Andrew, thank you for your help. I think now it is working. 

This is excellent news :). I initially worked out the installation method for Live555 on Ubuntu simply so I could compile the svn MPlayer against the most recent libraries, as MPlayer uses Live555 for *some* online streams. You can see this in [a guide I wrote for Hardy]("http://ubuntuforums.org/showthread.php?t=558538"). Can I be a little curious and ask what your use for Live555 is?

All the best,

Andrew

---

### Post by zelalem on 2009-11-14
HI Andrew, thank you for the best wish. I installed Live555 to use its API to develop an RTSP proxy. You know, I was looking for an rtsp stack and couldn't find one. I got a package called rtspd, but couldn't build it. Apparently, I learned that even VLC is developed with Live555. So, I decided to look at it. If you used its APIs, you may help me in that area as well. I'm also looking for a guide about its API. I hope you can suggest one. How about you? What do you use it for?

Thank you again for everything.

Regards,

---

### Post by andrew.46 on 2009-11-14
Hi zelalem,

> **zelalem said:**
> How about you? What do you use it for?

I am afraid that my use is very primitive :). I compile my own svn MPlayer and vlc and for these an up to date installation of Live555 is required. I am afraid that I have never gone into Live555 and further than that.

Andrew

---

### Post by zelalem on 2009-11-16
Hi Andrew, that is good. 

Best regards,

Zelalem

---

