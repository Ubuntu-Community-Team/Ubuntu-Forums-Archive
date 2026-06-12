---
title: "Broken Package - avidemux2.6-qt:amd64"
date: 2015-06-30
forum: Multimedia Software
---

### Post by Quarkrad on 2015-06-30
Running 14.04.  I keep getting notifications of a broken package - Synaptic tells me it is avidemux 2.6, when I reinstall I get an internal error:  No file name for avidemux2.6-qt4:amd64.  Any suggestion most appreciated.

---

### Post by monkeybrain20122 on 2015-06-30
Try  run in the terminal

```
sudo dpkg --configure  -a
```

---

### Post by Yellow Pasque on 2015-06-30
After that, see what this gives:
```
apt-cache policy avidemux2.6-qt
```
I guess you're using this PPA?: [https://launchpad.net/~rebuntu16/+archive/ubuntu/avidemux+unofficial](https://launchpad.net/~rebuntu16/+archive/ubuntu/avidemux+unofficial)

---

### Post by Quarkrad on 2015-07-01
Thank you - unfortunately no difference.  Here is the output:

```
dad@dadubuntu:~$ sudo dpkg --configure  -a
[sudo] password for dad: 
Setting up esound-common (0.2.41-11) ...
Setting up libavidemux2.6-ffmpeg:amd64 (1:2.6.10-1~ppa+trusty0) ...
dpkg: dependency problems prevent configuration of avidemux2.6-qt4:
 avidemux2.6-qt4 depends on avidemux2.6-common; however:
  Package avidemux2.6-common is not installed.

dpkg: error processing package avidemux2.6-qt4 (--configure):
 dependency problems - leaving unconfigured
Setting up libaudiofile1:amd64 (0.3.6-2) ...
Setting up libx265-35:amd64 (1.4-4~ppa+trusty0) ...
Setting up libesd0:amd64 (0.2.41-11) ...
Setting up libdcaenc0 (1:2+git2014.06.17-1~ppa+trusty0) ...
Setting up libavidemux2.6-6:amd64 (1:2.6.10-1~ppa+trusty0) ...
Setting up libavidemux2.6-qt4-6:amd64 (1:2.6.10-1~ppa+trusty0) ...
Setting up avidemux2.6-plugins-common:amd64 (1:2.6.10-1~ppa+trusty0) ...
Setting up avidemux2.6-plugins-qt4:amd64 (1:2.6.10-1~ppa+trusty0) ...
Processing triggers for libc-bin (2.19-0ubuntu6.6) ...
Errors were encountered while processing:
 avidemux2.6-qt4
```

```

dad@dadubuntu:~$ apt-cache policy avidemux2.6-qt
libavidemux2.6-qt5-6:
  Installed: (none)
  Candidate: 1:2.6.10-1~ppa+trusty0
  Version table:
     1:2.6.10-1~ppa+trusty0 0
        500 [http://ppa.launchpad.net/rebuntu16/avidemux+unofficial/ubuntu/](http://ppa.launchpad.net/rebuntu16/avidemux+unofficial/ubuntu/) trusty/main amd64 Packages
libavidemux2.6-qt4-6:
  Installed: 1:2.6.10-1~ppa+trusty0
  Candidate: 1:2.6.10-1~ppa+trusty0
  Version table:
 *** 1:2.6.10-1~ppa+trusty0 0
        500 [http://ppa.launchpad.net/rebuntu16/avidemux+unofficial/ubuntu/](http://ppa.launchpad.net/rebuntu16/avidemux+unofficial/ubuntu/) trusty/main amd64 Packages
        100 /var/lib/dpkg/status
avidemux2.6-qt4-dbg:
  Installed: (none)
  Candidate: 1:2.6.10-1~ppa+trusty0
  Version table:
     1:2.6.10-1~ppa+trusty0 0
        500 [http://ppa.launchpad.net/rebuntu16/avidemux+unofficial/ubuntu/](http://ppa.launchpad.net/rebuntu16/avidemux+unofficial/ubuntu/) trusty/main amd64 Packages
avidemux2.6-qt4:
  Installed: 1:2.6.10-1~ppa+trusty0
  Candidate: 1:2.6.10-1~ppa+trusty0
  Version table:
 *** 1:2.6.10-1~ppa+trusty0 0
        500 [http://ppa.launchpad.net/rebuntu16/avidemux+unofficial/ubuntu/](http://ppa.launchpad.net/rebuntu16/avidemux+unofficial/ubuntu/) trusty/main amd64 Packages
        100 /var/lib/dpkg/status
avidemux2.6-qt5:
  Installed: (none)
  Candidate: 1:2.6.10-1~ppa+trusty0
  Version table:
     1:2.6.10-1~ppa+trusty0 0
        500 [http://ppa.launchpad.net/rebuntu16/avidemux+unofficial/ubuntu/](http://ppa.launchpad.net/rebuntu16/avidemux+unofficial/ubuntu/) trusty/main amd64 Packages
libavidemux2.6-qt4-dbg:
  Installed: (none)
  Candidate: 1:2.6.10-1~ppa+trusty0
  Version table:
     1:2.6.10-1~ppa+trusty0 0
        500 [http://ppa.launchpad.net/rebuntu16/avidemux+unofficial/ubuntu/](http://ppa.launchpad.net/rebuntu16/avidemux+unofficial/ubuntu/) trusty/main amd64 Packages
libavidemux2.6-qt4-dev:
  Installed: (none)
  Candidate: 1:2.6.10-1~ppa+trusty0
  Version table:
     1:2.6.10-1~ppa+trusty0 0
        500 [http://ppa.launchpad.net/rebuntu16/avidemux+unofficial/ubuntu/](http://ppa.launchpad.net/rebuntu16/avidemux+unofficial/ubuntu/) trusty/main amd64 Packages
avidemux2.6-qt5-dbg:
  Installed: (none)
  Candidate: 1:2.6.10-1~ppa+trusty0
  Version table:
     1:2.6.10-1~ppa+trusty0 0
        500 [http://ppa.launchpad.net/rebuntu16/avidemux+unofficial/ubuntu/](http://ppa.launchpad.net/rebuntu16/avidemux+unofficial/ubuntu/) trusty/main amd64 Packages
libavidemux2.6-qt5-dbg:
  Installed: (none)
  Candidate: 1:2.6.10-1~ppa+trusty0
  Version table:
     1:2.6.10-1~ppa+trusty0 0
        500 [http://ppa.launchpad.net/rebuntu16/avidemux+unofficial/ubuntu/](http://ppa.launchpad.net/rebuntu16/avidemux+unofficial/ubuntu/) trusty/main amd64 Packages
libavidemux2.6-qt5-dev:
  Installed: (none)
  Candidate: 1:2.6.10-1~ppa+trusty0
  Version table:
     1:2.6.10-1~ppa+trusty0 0
        500 [http://ppa.launchpad.net/rebuntu16/avidemux+unofficial/ubuntu/](http://ppa.launchpad.net/rebuntu16/avidemux+unofficial/ubuntu/) trusty/main amd64 Packages
dad@dadubuntu:~$ 
```


Here (attached) is the output of Synaptic

---

### Post by Yellow Pasque on 2015-07-01
> avidemux2.6-qt4 depends on avidemux2.6-common; however:
Package avidemux2.6-common is not installed.

So what happens when you try to install avidemux2.6-common ?

---

### Post by matt_symes on 2015-07-01
@Quarkrad


Please try to use code tags when pasting terminal output into posts.

You use code tags by enclosing the terminal output in your post like this

[noparse]```
 text from terminal
```[/noparse]

to get output like this

```
 text from terminal
```

It's much easier to read. 

You can also highlight the text to wrap between code tags and hit the # button above where you are typing your text.

I have edited your post #4 to add code tags for you.

---

### Post by Quarkrad on 2015-07-01
I can confirm that I am using the ppa quoted above.  When I try to in avidexmux2.6-common I get:

```
E: /var/cache/apt/archives/avidemux2.6-common_1%3a2.6.10-1~ppa+trusty0_all.deb: trying to overwrite '/usr/share/locale/es/LC_MESSAGES/avidemux.mo', which is also in package avidemux-common 1:2.5.4-0ubuntu14
```

---

### Post by Yellow Pasque on 2015-07-01
Well, you've got avidemux packages from the Ubuntu repos mixed with avidemux packages from the PPA. Maybe you should just remove all installed avidemux packages, and then install avidemux2.6-qt4.

---

### Post by Quarkrad on 2015-07-02
Yes - that fixed it. Thank you for your help.

---

