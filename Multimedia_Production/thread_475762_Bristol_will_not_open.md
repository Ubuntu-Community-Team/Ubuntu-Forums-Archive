---
title: "Bristol will not open"
date: 2007-06-16
forum: Multimedia Production
---

### Post by GregoryMA on 2007-06-16
I installed ubuntu studio and was somewhat surprised to see that bristol was not included in it.  So, I installed bristol only to discover that I was mislead; bristol is included.  However, there is no icon and I can't for the life of me figure out how to start the program.  Maybe I am just overlooking something but I can't figure it out?  Do I have to run bristol as a plug-in in another program?
Does anybody know what I'm doing wrong?
Thanks, Greg.

---

### Post by nalmeth on 2007-06-17
Open a terminal Applications -> Accessories -> Terminal

OR 

Hit Alt-F2

and enter bristol

You can add it to the gnome-menu, just right-click on Applications and 'Edit Menus'

---

### Post by GregoryMA on 2007-06-17
Thanks for the heads up.  It is up and running.

---

### Post by nalmeth on 2007-06-17
Another heads up, bristol-engine persists to run on my system after I close bristol, and eats up some CPU.


System - Administration - System Monitor

Go into processes, you can see it and kill it from there

---

### Post by morganpatrick on 2008-04-02
I'm also having some serious Bristol problems.

When I tried to run startBristol before, Brighton would open up and immediately shut down.

Then I tried to uninstall it and Synaptic wouldn't allow me to without also removing ubuntu-audio. So I didn't remove it

Then I tried to install it by downloading the newest tarball from Bristol's site, hoping it would just overwrite it. It appeared to install, but I still can't run anything.

Here's some output:

```
morgan@morgan:~$ bristol
bristol: error while loading shared libraries: libbristolmidi.so.0: cannot open shared object file: No such file or directory
```

```
morgan@morgan:~$ startBristol -2600
spawning midi thread
parent going into idle loop
got the long semaphore
got the short semaphore
midi sequencer
Opened listening control socket: 5028
Error opening midi device bristol, exiting midi thread
bristol version 0.20.4
connected to :0.0
display is 1280 by 1024 pixels
Window is w 1280, h 1024, d 24, 0 0 0
Using DirectColor display
alloc color by name Blue
Initialise the arp2600 link to bristol: 8140af0
hostname is localhost, bristol
TCP port: 5028
Connected to the bristol control socket: 4
bristolengine already active
parent exiting
return - no data in buffer
cleanupBrighton(0)
cleared sigpipe handler
cleanupBrighton(0)
midi write error, fd 4, size 1
midi write error, fd 4, size 12
midi write error, fd 4, size 1
return - no data in buffer
socket closed
request acked: -1
morgan@morgan:~$ 
```

I also read somewhere that it's easier to just download Bristol and run it locally without installing. So here's the result of that:

```
morgan@morgan:~/Desktop$ cd bristol
morgan@morgan:~/Desktop/bristol$ cd bin
morgan@morgan:~/Desktop/bristol/bin$ ./startBristol -2600
bash: ./startBristol: Permission denied
```

very frustrating.

---

### Post by morganpatrick on 2008-04-04
alright, I've gotten Bristol to run a few times on different os configurations and here's how I did it every time:

1) get a newer deb from some repository, like here:
[http://apt.64studio.com/64studio/](http://apt.64studio.com/64studio/)

or here:
2) [ftp://musix.ourproject.org/pub/musix/deb/](ftp://musix.ourproject.org/pub/musix/deb/)

then follow step 1 here:
[http://trac.64studio.com/64studio/ticket/358](http://trac.64studio.com/64studio/ticket/358)

getting dev dependencies from synaptic. Only when you go to the sourceforge page, get bristol 0.20.1, one of the newer versions.

Then just ./configure, make and sudo make install.

for some reason the only thing that works for me is if you slather 0.20 on top of 0.10 on top of the version included in ubuntu studio.

---

### Post by ncopeland on 2008-06-09
There are a few different problems here I think.

> continues to run
This may happen but should only be for a short time.

> midi write error, fd 4, size 1
Then again, maybe not. There were a few reports of the engine already running and although it should be possible to reconnect there may be issues with the state of the engine. The next release 0.20.6 includes a heartbeat or type of Active Sense from the GUI to the engine to allow both parts to exit should the other fail. Anticipated in June '08 and it should resolve both of these issues.

I can't comment on loading two version on top of each other, should not be necessary.

Further integration into Ubuntu, ie, with icons for the menus, is something I will admit to hoping somebody else might do for me. Kind of busy otherwise.

Regards,

Nick.

---

