---
title: "Recording Streaming screen and audio"
date: 2007-05-24
forum: Multimedia Production
---

### Post by saphil on 2007-05-24
I considered putting this in the "extreme beginners" area because I don't really know enough about this to search to see if somebody else has laready got the answer.

I want to have camtasia-like capability, to capture windows on the desktop, including webcam input (possibly) as well as audio, so I can record a complete webinar for training purposes.  I don't want to webex the thing since webex uses a local client and doesn't work well in Linux.  It is insane to have to use a windows client to watch a webinar about the Ubuntu Advantage.

---

### Post by eye208 on 2007-05-25
Install "gtk-recordMyDesktop".

---

### Post by saphil on 2007-05-25
Thanks! Here is my progress report

I got
```
qt-recordmydesktop-0.1.tar.gz   gtk-recordmydesktop-0.3.4.tar.gz  
recordmydesktop-0.3.4.tar.gz

```Untarred and ran ./configure for the base package "recordmy"

found that I needed pygtk-2.10.4.tar.gz, so I went to get that, and
untared and installed.  It says
```
 configure: error: Package requirements (pygobject-2.0 >= 2.12.1) were not met:
No package 'pygobject-2.0' found

```found that here:
[http://download.gnome.org/sources/pygobject/2.12/](http://download.gnome.org/sources/pygobject/2.12/)

[FONT=Arial]compile and installed pygobject, pygtk, and recordmydesktop 
(Compiled with Jack disabled)
I don't know Jack.  Should I get him enabled?

in recordmydesktop the make command had this error
[/FONT]```
configure: error: You need pygtk >=2.4 and the appropriate development headers to proceed

```[FONT=Arial]
Which I just installed (./configure,  make and make install)
so I am stuck.  


[/FONT]

---

### Post by eye208 on 2007-05-25
Why not just install the binary from the repos and let APT sort out the dependencies automatically?

---

### Post by nedecor on 2007-05-25
sudo apt-get install gtk-recordmydesktop

To install, the universe repositories must be enabled.

---

### Post by saphil on 2007-05-25
because I have no idea where the right repo might be. :-) 

here's my repo list
```
deb http://ca.archive.ubuntu.com/ubuntu/ feisty main restricted universe multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ feisty restricted multiverse

deb http://ca.archive.ubuntu.com/ubuntu/ feisty-updates main restricted universe multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ feisty-updates restricted multiverse

deb http://ca.archive.ubuntu.com/ubuntu/ feisty-security main restricted universe multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ feisty-security restricted multiverse

deb http://ca.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ feisty-proposed restricted main multiverse universe
deb-src http://ca.archive.ubuntu.com/ubuntu/ feisty-backports restricted multiverse
```

What else should I have in there?

---

### Post by nedecor on 2007-05-25
> **saphil said:**
> 

What else should I have in there?

That should do it, go ahead and try to install.

sudo apt-get install gtk-recordmydesktop

---

### Post by saphil on 2007-05-25
Well, I did a reinstall from synaptic of both recordMyDesktop and gtk-recordMyDesktop
so the window comes up..  Now I just get a 256 error saying configurations are wrong.  This is a hopeful advancement.

error log /root/gtk-recordMyDesktop-crash.log
```
#This is the command given at initialization:
recordmydesktop -o /root/out.ogg -fps 15 -x 732 -y 456 
                          -width 84 -height 176 -channels 1 -freq 22050 
                          -device hw:0,0 -v_quality 63 -s_quality 10 
                           -shared-threshold 75 -workdir /tmp --zero-compression 

# output edited in forum for line wrap

#recordMyDesktop stderror output:

    Error parsing arguments.
    Type --help or -h for usage.

```

---

### Post by iovar on 2007-05-25
The "error parsing arguments" message indicates that there are incompatible versions of the interface
and the commandline tool installed in your computer. The versions in the feisty  repositories are compatible 
with each other, but incompatible with the latest source distributions, so my guess is that you successfully
installed the commandline program from source and you didn't remove it, before installing from apt.

You can test it by running 
~$ which recordmydesktop
on a terminal.

If it prints /usr/local/bin/recordmydesktop, you are using the version installed from source.
You can also run this to see the version number of the program in your path
~$ recordmydesktop --version 

In order to remove that from your computer and let the version installed from apt- to be executed,
get the recordmydesktop-0.3.4.tar.gz tarball again, unpack it and run:

~$ ./configure
~$ sudo make uninstall

Or if you haven't removed the files just get in the folder and run 
~$ sudo make uninstall

After this you should be able to run the program normally. 

If you want the latest version in an easy way, go to [http://www.getdeb.net/]("http://www.getdeb.net/release.php?id=613")
and download the precompiled debs.

Also another thing:

> recordmydesktop -o **/root/out.ogg** ...

Why are you running as root? That's the quickest way to cripple your system!

---

### Post by saphil on 2007-05-26
> Why are you running as root? That's the quickest way to cripple your system!

I was running record mydesktop as root because I started it from the root terminal window I was installing from. Ooops!

Thanks for the version mismatch hint.  That was exactly what was going on.  I could select a piece of a window or whole screen.  Resolution of the moovie was a little rough at fullscreen.  Maybe it would help to use 800x600 on the screen resolution?  Can I set sound inputs?

---

