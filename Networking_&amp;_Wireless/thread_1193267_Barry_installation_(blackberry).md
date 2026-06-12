---
title: "Barry installation (blackberry)"
date: 2009-06-21
forum: Networking &amp; Wireless
---

### Post by zanderone on 2009-06-21
Hello!
I am a complete linux beginner with a dell Mini running ubuntu. For minimum necessary functionality i need to be able to charge my blackberry from this machine. I have read soo many posts but they are too many new things to learn all at once and it seems like all the directions explain different ways  to do it!  I will install whatever is easiest but all I really need is bcharge.

using these directions: [http://ubuntuforums.org/showthread.php?t=661785&page=2](http://ubuntuforums.org/showthread.php?t=661785&page=2)


[LIST=1]
[*]using synaptic, I installed: libusb-dev, libssl-dev, libtar-dev, libgtkmm-2.4-dev, libglademm-2,4-dev, zlib1g-dev so that I would have necessary header (.h) files for the build.
[*]Downloaded barry-0.12.tar.bz2 from [http://sourceforge.net/projects/barry/](http://sourceforge.net/projects/barry/)
[*]unpack and cd to barry-0.12/
[*]./configure --enable-gui
[*]sudo make install
[*]sudo cp modprobe/blacklist-berry_charge /etc/modprobe.d/
[*]sudo gedit udev/10-blackberry.rules.Debian and replace /usr/sbin/bcharge everywhere with /usr/local/sbin/bcharge. Yoatu can specify a prefix in step 4 for the configure script to have the utilities (and libraries and includes) to go to /usr instead of the default /usr/local. I wanted things in /usr/local as a reminder to me that this is the only (non-synaptic) manual mod to my system. Then...
[*]sudo cp udev/10-blackberry.rules.Debian /etc/udev/rules.d/10-blackberry.rules
[*]reboot
[/LIST]

I think everything up to step 5 has worked now after this the last few lines of the terminal say:

 g++ -DHAVE_CONFIG_H -I.. -ansi -Wall -fno-strict-aliasing -g -c time.cc  -fPIC -DPIC -o .libs/time.o
../libtool: line 1281: g++: command not found
make[1]: *** [time.lo] Error 1
make[1]: Leaving directory `/home/alexandre/Desktop/barry-0.14/src'
make: *** [install-recursive] Error 1

I would really appreciate help with this. Also in step one I used sudo apt-get install to get the libraries, how do you do this with synaptic - it only finds things on your computer, not new packages from the internet it seems.

Thanks!

---

### Post by kevdog on 2009-06-21
Between step 4 and 5 did you just run the make command?  And as far as the configure flags, I haven't tried to compile barry since Christmas.  At that time I was trying to compile the svn sources (or git or whatever they were using at the time), and the --enable-gui option wouldn't work.  If you just do a ./configure followed by a make, will that compile cleanly?

---

