---
title: "HOWTO: install ESS Teledrive 2898 modem driver"
date: 2006-05-31
forum: Networking &amp; Wireless
---

### Post by helmut_hed on 2006-05-31
These are combined instructions for Breezy 5.10 through Hardy 8.04.  There is considerable overlap with the PCTel modem directions because they share some code.

First, make sure you have a supported ESS modem (or the Creative DI3635, which is ESS based) by doing this:

lspci -d 125d: -n

You should see output like this:

0000:00:09.0 0780: 125d:2898 (rev 01)

The driver supports 125d:2898 devices only.

If you see a line with "125d:XXXX", where XXXX is some other number (e.g., 2839), your modem is not supported by this driver, although it was manufactured by ESS.

Next, download the driver itself from here:

[http://tx.technion.ac.il/~raindel/ess_2.6-v0.4.tar.gz](http://tx.technion.ac.il/~raindel/ess_2.6-v0.4.tar.gz)

For Breezy Badger (5.10) you will need three packages for gcc-3.4 (as with many other drivers under Breezy, you need to get gcc version 3.4 because that's the compiler version used by the kernel). You can find them here:

[http://security.ubuntu.com/ubuntu/pool/main/g/gcc-3.4/gcc-3.4-base_3.4.6-5ubuntu1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/g/gcc-3.4/gcc-3.4-base_3.4.6-5ubuntu1_i386.deb)
[http://security.ubuntu.com/ubuntu/pool/main/g/gcc-3.4/gcc-3.4_3.4.6-5ubuntu1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/g/gcc-3.4/gcc-3.4_3.4.6-5ubuntu1_i386.deb)
[http://security.ubuntu.com/ubuntu/pool/main/g/gcc-3.4/cpp-3.4_3.4.6-5ubuntu1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/g/gcc-3.4/cpp-3.4_3.4.6-5ubuntu1_i386.deb)

Now install a couple of packages using apt-get as follows:
sudo apt-get install build-essential
sudo apt-get install linux-headers-386

Next, install the gcc 3.4 packages:

sudo dpkg -i gcc-3.4-base_3.4.6-5ubuntu1_i386.deb
sudo dpkg -i cpp-3.4_3.4.6-5ubuntu1_i386.deb
sudo dpkg -i gcc-3.4_3.4.6-5ubuntu1_i386.deb

Make gcc point to version 3.4:

sudo rm /usr/bin/gcc
sudo ln -s /usr/bin/gcc-3.4 /usr/bin/gcc

For Dapper and later, all the packages you need are on the install CD. Use the Synaptic Package Manager, under System->Administration, to find and install the "build-essential" and "linux-headers-386" packages.

The remainder of the steps apply to all releases.

Unpack the driver itself and run the setup script:
tar xvzf ess_2.6-v0.4.tar.gz
cd ess_2.6-v0.4
sudo ./setup

If the setup command found no errors (it shouldn't) the modem will now be ready to use. Go to System->Administration->Networking to set up your connection if you haven't already.

Regards,
Jeff Trull

---

### Post by Extreme Coder on 2006-12-27
I can't express how much I am happy to find this post(wierd enough, the scanModem tool led me to this link ;) ), but this helped me a lot. I'm 'batch' installing Ubuntu on 15 computers in an office, and sadly all of them use this modem. Fortunately, this is not a problem anymore :D

Thanks again!

---

### Post by Olaf Scheel on 2007-02-05
Dear Jeff,
 
your driver works great with kubuntu 6.06, however, I can´t get it running with Kubuntu 6.10 and need help.
During compilation, these messages are shown:
 
olaf@rechenmonster:~/ess_2.6-v0.2$ sudo ./setup
checking for running kernel version...2.6.17
checking for gcc...4.1.2
searching for kernel includes...found at /usr/src/linux-headers-2.6.17-10/include/
checking for autoconf.h.../usr/src/linux-headers-2.6.17-10/include//linux/autoconf.h
checking for asm/mach-default...yes
checking for kernel version in version.h...UTS_RELEASE is 2.6.17-10
checking type of tty_struct.count...int
checking for presence of udev...present
detecting your modem...found. Your modem is a ess type modem.
** compilation error
please read the FAQ about reporting compilation problems
and report this problem.  A transcript of the build process
has been saved in make.log.  When reporting problems to
the development team, please send us this file.
olaf@rechenmonster:~/ess_2.6-v0.2$
 
The make.log file reads like this:
 
  LD	binary.a
make -C /usr/src/linux-headers-2.6.17-10 M=/home/olaf/ess_2.6-v0.2
make[1]: Betrete Verzeichnis '/usr/src/linux-headers-2.6.17-10'				("enter directory")
 
  WARNING: Symbol version dump /usr/src/linux-headers-2.6.17-10/Module.symvers
           is missing; modules will have no dependencies and modversions.
 
  LD      /home/olaf/ess_2.6-v0.2/built-in.o
  CC [M]  /home/olaf/ess_2.6-v0.2/essserial-2.6.o
/bin/sh: scripts/genksyms/genksyms: not found
make[2]: *** [/home/olaf/ess_2.6-v0.2/essserial-2.6.o] Fehler 127				("error 127")
make[1]: *** [_module_/home/olaf/ess_2.6-v0.2] Fehler 2					("error 2")
make[1]: Verlasse Verzeichnis '/usr/src/linux-headers-2.6.17-10'				("exit directory")
make: *** [all] Fehler 2										("error 2")
 
 
Since I am new to linux, I don´t know what the error codes mean an how to fix it.
Thank you for reading
 
Greetings from Hamburg, Germany
Olaf Scheel

---

### Post by helmut_hed on 2007-02-25
Olaf and all,

The driver has now been updated to handle Ubuntu 6.10 (Edgy) and all kernels through 2.6.20.  Revised instructions are in the first message - the new file is version 0.3 instead of 0.2.  Let me know if you encounter any problems.

Regards,
Jeff

---

### Post by DoneRightI.T. on 2007-06-07
hoping for an update. 
Running Feisty Fawn 7.04

error during compilation is as follows... not sure If its me, or something missed.. but would really appreciate some help.

checking for running kernel version...2.6.20
checking for gcc...4.1.2
searching for kernel includes...found at /lib/modules/2.6.20-16-generic/build/include
checking for autoconf.h.../lib/modules/2.6.20-16-generic/build/include/linux/autoconf.h
checking for asm/mach-default...yes
checking for kernel version in version.h...t.c: In function ‘main’:
t.c:4: error: ‘UTS_RELEASE’ undeclared (first use in this function)
t.c:4: error: (Each undeclared identifier is reported only once
t.c:4: error: for each function it appears in.)
./configure: line 318: ./t: No such file or directory
rm: cannot remove `./t': No such file or directory
** error
could not determine a proper UTS_RELEASE
** compilation error
please read the FAQ about reporting compilation problems
and report this problem.  A transcript of the build process
has been saved in make.log.  When reporting problems to
the development team, please send us this file.

---

### Post by DoneRightI.T. on 2007-06-07
updated to the latest version.. compiled/installed just fine.

TY

---

### Post by VAHID216 on 2007-06-09
Hello really thanks for this . I'm happy :d to find this totally. But i have problem when i dialling to ISP after verfying user and pass the  modem was disconnecting . How can i fix this problem?
thnx for this driver.

---

### Post by VAHID216 on 2007-06-12
sorry but this links 
[http://archive.ubuntu.com/ubuntu/poo...untu8_i386.deb](http://archive.ubuntu.com/ubuntu/poo...untu8_i386.deb)
[http://archive.ubuntu.com/ubuntu/poo...untu8_i386.deb](http://archive.ubuntu.com/ubuntu/poo...untu8_i386.deb)
[http://archive.ubuntu.com/ubuntu/poo...untu8_i386.deb](http://archive.ubuntu.com/ubuntu/poo...untu8_i386.deb)
doesnt work please correct it.

---

### Post by Olaf Scheel on 2007-07-04
Hello Jeff,
is it possible to use this modem to send a fax?
Olaf

---

### Post by helmut_hed on 2007-07-04
I don't know!  I've never used a modem to send a fax in Linux, so I don't even know how to try...

The driver is the 2.4 kernel driver supplied by ESS long, long ago, hacked by me to support 2.6 kernels.  If it could fax back then, I guess it can now.

Regards,
Jeff

---

### Post by helmut_hed on 2007-07-04
VAHID216 - thanks for letting me know about the broken links.  Should be OK now.  I don't know what to tell you about your disconnection problem;  doesn't sound like a driver issue but there are things you can do to find out.  Do you see any modem-related messages in /var/log/messages that appear while you are trying to connect to your ISP?

You could do this in a terminal window:

tail -f /var/log/messages

and then try to connect as usual.  Any new messages will appear in your terminal window.

---

### Post by Silvain on 2007-12-12
> **helmut_hed said:**
> 
----------------------snipped----------------------------------------
The remainder of the steps apply to both Breezy and Dapper.

Unpack the driver itself and run the setup script:
tar xvzf ess_2.6-v0.2.tar.gz
cd ess_2.6-v0.2
sudo ./setup
-----------------------snipped------------------------------------------
Regards,
Jeff Trull

had to change this some , minor really,to this, thought I would mention this for some beginners helps maybe .
tar xvzf ess_2.6-v0.3.tar.gz
cd ess_2.6-v0.3


Very helpful post !
----------------------
   U rock  :guitar:

---

### Post by helmut_hed on 2007-12-13
Thanks!  Instructions fixed now.

Jeff

---

### Post by tekoholix on 2008-04-18
Old thread, I know, but relevant nonetheless:

Under Hardy Beta (2.6.24-16), make fails on this driver.

Here's the make.log:

  LD	binary.a
make -C /lib/modules/2.6.24-16-generic/build M=/home/paul/ess_2.6-v0.3
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
scripts/Makefile.build:46: *** CFLAGS was changed in "/home/paul/ess_2.6-v0.3/Makefile". Fix it to use EXTRA_CFLAGS.  Stop.
make[1]: *** [_module_/home/paul/ess_2.6-v0.3] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make: *** [all] Error 2

---

### Post by helmut_hed on 2008-04-18
Thanks, Tekoholix, this driver is really overdue for an update.  I plan to get on it "soon".  Probably after Hardy ships.

Jeff

---

### Post by helmut_hed on 2008-05-01
For Tekoholix and anyone else who's waiting on a driver update, I've released the
new version. See updated instructions at the start of this thread.  Hopefully we'll
be OK for another year or so...

Regards,
Jeff

---

