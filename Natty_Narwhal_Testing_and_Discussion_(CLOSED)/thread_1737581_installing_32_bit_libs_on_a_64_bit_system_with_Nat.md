---
title: "installing 32 bit libs on a 64 bit system with Natty"
date: 2011-04-23
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by nbubis on 2011-04-23
Hi all,

I'm having trouble installing 32 bit libs on a 64 bit installation of natty (beta 2). I'm trying to install 32 bit openmotif 2.3.x by doing:

```
sudo dpkg --force-architecture -i libmotif4_2.3.3-5_i386.deb
```

This leads to an error I believe is due to the recent "multiarch" support:

```
dpkg: warning: overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
Selecting previously deselected package libmotif4:i386.
dpkg: error processing libmotif4_2.3.3-5_i386.deb (--install):
 libmotif4:i386 2.3.3-5 (Multi-Arch: no) is not co-installable with libmotif4:amd64 2.3.3-5ubuntu1 (Multi-Arch: no) which is currently installed
Errors were encountered while processing:
 libmotif4_2.3.3-5_i386.deb
```
[B]
Any ideas on how to solve this? [/B]

The final goal is installing a Citrix ICA client.

---

### Post by Billxyzzy on 2011-04-24
To help the OP I have bumped this thread and to also add
my comments.
I am attempting to install a Brother DCP 7040 printer.
While working to install a driver a bug was generated.
Launchpad bug #769241
At the time I only had the bug info.
A driver is suggested but not specifically for the
DCP 7040.  The driver is installed and the USB
handshake is completed.  However no print job is
completed.  Be it a test page, diagnostic page or a
standard text document.  Natty thinks the document is
printed but the printer does nothing.
This is repeatable as often as you like.

I have spent some time investigating by looking for 
drivers on the Brother site.
What I have found is that the vast majority of drivers
available (for Linux) are I386 (32bit).
It appears that AMD64 is not even considered.
Further,  most of the Brother devices do not even
consider Linux nor have drivers.
If anyone else is doing document work including printing
I would like your comments/results.
I must add that I have an older Brother printer that works
well so the problem seems to be device specific.
I do not want to return to I386 mode to do work.

I would like to get comments/work arounds by others
if they exist.  Also what problems you have run into.
My opinion is that printing is a very important feature
for anyone doing productive work.

Should we be beating the DEV's over the head on this?
With, at least a baseball bat,  (GRIN)

---

### Post by wojox on 2011-04-24
Have you installed the 32 bit libraries?

```
sudo apt-get update; sudo apt-get install ia32-libs
```

---

### Post by Billxyzzy on 2011-04-24
Good suggestion but libs already installed
error message from dpkg
dpkg: warning: overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)

---

### Post by cariboo on 2011-04-24
I have a Brother HL-5250DN, it automagically loads the correct drivers on my pure 64-bit Natty system.

---

### Post by nbubis on 2011-04-24
yes, ia32-libs is already installed.
As said, from the error this looks like something to do with how Natty "multiarch" support not working with the motif packaging.

---

### Post by Billxyzzy on 2011-04-24
Interesting,  I looked up the driver for the hl-5250dn and
it was 2007 Apr 18
My DCP 7040 driver is dated 2008 June 25
However I did not download your driver to see if it
was i386 or amd64

---

### Post by MadCow108 on 2011-04-24
have you tried doing what the error message suggests?
>  libmotif4:i386 2.3.3-5 (Multi-Arch: no) **is not co-installable** with libmotif4:amd64 2.3.3-5ubuntu1 (Multi-Arch: no) which is currently installed

=> remove libmotif4:amd64 first

---

### Post by Billxyzzy on 2011-04-24
=> remove libmotif4:amd64 first
checked and libmotif4:amd64 is not installed

---

### Post by MadCow108 on 2011-04-24
sure about that?
your error message disappears on my machine when I remove the 64 bit version
please show the output of:
apt-cache policy libmotif4

---

### Post by Billxyzzy on 2011-04-24
something strange here:
synaptic says it is not installed
problem with synaptic?
install and remove?
try to install the i386 version?

---

### Post by Billxyzzy on 2011-04-24
Missed part of your previous message 
here is result
bill@bill-GA-MA78GM-US2H:~$ sudo apt-cache policy libmotif4
[sudo] password for bill: 
libmotif4:
  Installed: (none)
  Candidate: 2.3.3-5ubuntu1
  Version table:
     2.3.3-5ubuntu1 0
        500 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) natty/multiverse amd64 Packages

---

### Post by dino99 on 2011-04-24
then remove the 32 lib and
install the 64 one then remove/purge it
at last reinstaal the 32 one

---

### Post by nbubis on 2011-04-24
Un-installing the 64 bit version and then installing the 32 bit one doesn't help, and moreover should not be the solution - you should be able to install them side by side.

Trying to install only the 32-bit version leads to a dependency issue, which is not really resolvable (needs 32 bit libc6) unless you want to remove half of your system:

```
name@user$ sudo dpkg --force-architecture -i libmotif4_2.3.3-5_i386.deb

dpkg: warning: overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ... 235307 files and directories currently installed.)
Unpacking libmotif4:i386 (from libmotif4_2.3.3-5_i386.deb) ...
dpkg: dependency problems prevent configuration of libmotif4:i386:
 libmotif4:i386 depends on libc6 (>= 2.7).
 libmotif4:i386 depends on libice6 (>= 1:1.0.0).
 libmotif4:i386 depends on libsm6.
 libmotif4:i386 depends on libx11-6.
 libmotif4:i386 depends on libxext6.
 libmotif4:i386 depends on libxft2 (>> 2.1.1).
 libmotif4:i386 depends on libxmu6.
 libmotif4:i386 depends on libxp6.
 libmotif4:i386 depends on libxt6.
dpkg: error processing libmotif4:i386 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libmotif4:i386

name@user$ sudo dpkg --force-architecture -i libc6_2.11.2-10_i386.deb 

dpkg: warning: overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
Selecting previously deselected package libc6:i386.
dpkg: error processing libc6_2.11.2-10_i386.deb (--install):
 libc6:i386 2.11.2-10 (Multi-Arch: no) is not co-installable with libc6:amd64 2.13-0ubuntu13 (Multi-Arch: same) which is currently installed
Errors were encountered while processing:
 libc6_2.11.2-10_i386.deb
```

---

### Post by Billxyzzy on 2011-04-27
I am bringing back this thread again to add more comments.
I tested my printer problem on Lucid (10.04),Maverick (10.10) and Natty with same problems. I also installed 
openSUSE on another test drive and found the same problems.
It appears that this is not a Ubuntu specific problem
rather it is a Linux problem.  Going to the brother
driver site and reading the FAQ's  this problem goes back several Ubuntu versions. The suggested fixes in the
brother FAQ's approach it as a specific printer problem.
As the problem is software development problem it seems
to me that enough people have to make enough noise and
get the proper attention.

Let me add that my "printer"  is, in fact, a multiple use
device (printer scanner and copier) all in one package.
The scanner function also does not work in any of the
tests I made on the various systems. Today I feel that
buying several devices when a single device will do the
job is a waste of space and money. The manufacturers are
very happy to sell new devices with grater power and
capabilities.  It is the same old story,  the software
is behind the hardware development curve.

If anyone is even interested in looking at 
Launchpad bug #769241 and adding comments. I would
appreciate your time.  I will be adding as much
info as I can to the bug report.

---

