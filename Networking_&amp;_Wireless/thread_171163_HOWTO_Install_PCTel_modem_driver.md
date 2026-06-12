---
title: "HOWTO: Install PCTel modem driver"
date: 2006-05-06
forum: Networking &amp; Wireless
---

### Post by helmut_hed on 2006-05-06
First, make sure you have a supported PCTel modem by doing this:

lspci -d 134d: -n

You should see output like this:

0000:00:09.0 0780: 134d:7890 (rev 01)

The driver supports devices in the range 134d:7890 through 134d:7897.

If you see a line with "134d:2189", you unfortunately have a PCTel 688 HSP modem, which is not supported *by this driver*.  This driver supports the PCT789 only. However, you may have luck with the Smartlink driver, according to [this post.]("http://phep2.technion.ac.il/linmodems/archive-sixth/msg01584.html")

Next, download the driver itself from here:

[http://linmodems.technion.ac.il/pctel-linux/pctel-0.9.7-9-rht-9.tar.gz](http://linmodems.technion.ac.il/pctel-linux/pctel-0.9.7-9-rht-9.tar.gz)

For Breezy Badger (5.10) you will need three packages for gcc-3.4 (as with many other drivers under Breezy, you need to get gcc version 3.4 because that's the compiler version used by the kernel).  You can find them here:

[http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.4/cpp-3.4_3.4.4-6ubuntu8_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.4/cpp-3.4_3.4.4-6ubuntu8_i386.deb)
[http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.4/gcc-3.4_3.4.4-6ubuntu8_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.4/gcc-3.4_3.4.4-6ubuntu8_i386.deb)
[http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.4/gcc-3.4-base_3.4.4-6ubuntu8_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.4/gcc-3.4-base_3.4.4-6ubuntu8_i386.deb)

Now install a couple of packages using apt-get as follows:
sudo apt-get install build-essential
sudo apt-get install linux-headers-2.6.12-9-386

Next, install the gcc 3.4 packages:

sudo dpkg -i gcc-3.4-base_3.4.4-6ubuntu8_i386.deb
sudo dpkg -i cpp-3.4_3.4.4-6ubuntu8_i386.deb
sudo dpkg -i gcc-3.4_3.4.4-6ubuntu8_i386.deb

Make gcc point to version 3.4:

sudo rm /usr/bin/gcc
sudo ln -s /usr/bin/gcc-3.4 /usr/bin/gcc

For Dapper Drake (6.06) and thereafter, all the packages you need are on the install CD.  Use the Synaptic Package Manager, under System->Administration, to find and install the "build-essential" and "linux-headers-386" packages.

The remainder of the steps apply to all of Breezy, Dapper, and later releases.

Unpack the driver itself and run the setup script:
tar xvzf pctel-0.9.7-9-rht-7.tar.gz
cd pctel-0.9.7-9-rht-7/
sudo ./setup

If the setup command found no errors (it shouldn't) the modem will now be ready to use.  Go to System->Administration->Networking to set up your connection if you haven't already.

Regards,
Jeff Trull
PS: I cribbed the gcc 3.4 instructions from other posters, especially blastus, but I tested them myself.  See [http://ubuntuforums.org/showthread.php?t=79896&highlight=gcc-3.4](http://ubuntuforums.org/showthread.php?t=79896&highlight=gcc-3.4)

---

### Post by niraj on 2006-06-03
Could someone send me pctel-0.9.7-9-rht-6.tar.gz? The site seems to be down and I can't find it on Google on any other sites. Can't even find it on file sharing apps like eMule :(

I'll edit this post once I have received an e-mail.

Edit: Got the mail... thanks. Trying it out now.

Compiling went fine, setup worked flawlessly and activated my modem. But when I went to Network -> Properties and asked it to autodetect my modem it just got stuck. I installed gnomeppp, but in it's setup it does not detect any modem on my system. If I try to dial it says 'cannot open modem'.

Also, if you're using the 686 kernel like me, then you should use linux-headers-686 instead of linux-headers-386

---

### Post by Malac on 2006-06-26
Hi All,
To niraj my modem uses the above drivers and is on "/dev/ttyS_PCTEL0" you could try this by manually typing it in to the Network Settings form.

Not sure whether anyone can help but I am trying to setup two modems.
I have tried searching the forums but the search engine says the word "two" is too short to include.

My problem is I have an ADSL USB Modem which I use all the time.
But occasionally I need to connect using my 56k PCTEL dialup PCI modem to another ISP to send e-mail.
I can do this using the drivers mentioned above but only after changing all my config files over to the PCTEL modem and rebooting as at the moment both interfaces are using the ppp0 interface.
This takes about 10 minutes and is fast becoming a pain in the bum every time I want to send one e-mail.

Can someone point me in the direction of how to configure one of the modems to another interface name and also how to dialout on a specific interface.

Ultimately I'd like to just dialout on the PCTEL when I need to send e-mail then just hangup that connection without disconnecting the ADSL USB Modem.

Any help would be greatly appreciated.

---

### Post by gary4gar on 2006-06-29
mime driver is not supported
any idea when new driver will be available??

---

### Post by K3WHO on 2006-07-26
I'm having trouble with this myself. I have "build-essentials" and "linux-headers-386" installed. When I run ./setup I get this...

> 
osiris@tegan:~/pctel-0.9.7-9-rht-6$ sudo ./setup
checking for running kernel version...2.6.15
checking for ptserial...ptserial-2.6.c
checking for gcc..../configure: line 353: gcc: command not found
** error
no suitable gcc version could be found.
please install gcc.
** compilation error
please read the FAQ about reporting compilation problems
and report this problem.  A transcript of the build process
has been saved in src/make.log.  When reporting problems to
the development team, please send us this file.
osiris@tegan:~/pctel-0.9.7-9-rht-6$


It doesn't make any sense to me since I know gcc is installed. Anyone know of a workaround for this?

---

### Post by helmut_hed on 2006-07-27
Hi K3WHO,

Do you have Dapper installed, or was this a kernel upgrade from Breezy?

If you have Dapper, can you try these two commands and send the output?

which gcc

gcc --version

Thanks!

Jeff

---

### Post by K3WHO on 2006-07-30
Thanks for the reply :)I tried both of those commands and no luck with that either :(

> 
osiris@tegan:~$ which gcc
osiris@tegan:~$ gcc --version
-bash: gcc: command not found
osiris@tegan:~$


any other ideas?

---

### Post by helmut_hed on 2006-07-31
Hi K3WHO,

This indicates that gcc is not in fact installed.  Are you running Dapper or Breezy?  gcc should be installed as part of build-essential under Dapper.  Are you certain you installed build-essential?  Is it possible you are running Breezy instead?  If so there are a different set of directions described above.

Regards,
Jeff

---

### Post by K3WHO on 2006-07-31
I'm running Dapper. I know that build-essential is installed...

```
osiris@tegan:/etc/apache2$ sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree... Done
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
osiris@tegan:/etc/apache2$

```

```
osiris@tegan:/etc/apache2$ sudo apt-get install gcc
Reading package lists... Done
Building dependency tree... Done
gcc is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

```

it's weird..lol

---

### Post by fseigert on 2007-03-28
Hi! 

This forum seems fine. I have installed Ubuntu Version 6.10. The modem i have is HSP56MR PCTEL the manufactor said. After the installation there will be AC´97 VIA 82XX ALSA regocnice. This is my first time to work with ubuntu/linux. 
If i want to build the connection i can only choose with standard /dev/modem and /dev/ttyS0 - no especially modem name to choose. And it seems that the modem isn´t correct up to now. 
By the way, i can not find the linux headers 386 paket and the build essential paket in the synaptic paket package.

And I don´t know how i make the computer/modem to dial! What button is for the connection to build?
Could someone help me?

---

### Post by helmut_hed on 2007-03-28
Hi fseigert,

I'm a little confused - the "PCTel HSP56MR" and the "AC '97 Via 82xx ALSA" are quite different things.  You need to have a specific type of PCTel modem for this to work.

Can you post the output of this command?

lspci -d 134d: -n

Also, you will definitely need both "build-essential" and "linux-headers-386" packages.  To find them, run Synaptic, click the Search button, and type

build-essential

into the box that pops up.  You should see a listing for this package appear after a few seconds.  If it is already installed you will see a solid green box;  if it is not installed there will be an empty box.  Click on it and select "Mark for Installation".  Do the same for "linux-headers-386" package.  Then click the Apply button (green check mark).

After this point you can follow the other directions given.  Make sure there are no error messages.  You will have a /dev/modem link that is correct for the PCTel driver.

Good luck,
Jeff

---

### Post by fseigert on 2007-03-30
Thanks Jeff,

when i type lspci -d 134d: -n there is nothing. When i type lspci then there is the list:
00:00.0 Host bridge: VIA Technologies ....
00:01.0 PCI bridge: VIA ....
00:10.0 USB Controller: VIA Technologies, ... VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Con...
00:10.3 USB Controller: VIA ... USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA...
00:11.1 IDE interface: VIA Technologies VT82C586A/B/VT82C686A/AB/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA...
00:11.6 Communication controller: VIA Technologies, Inc. AC´97 Modem Controller (rev80)
00:12.0 Ethernet controller: VIA...
01:00.0 VGA compatible controller: VIA...

I have an laptop, maybe this is the answer of other connection points?
And (rev80) is for the usb controller and for the modem controller, is this correct?

The kernel i have is 2.6.17-10.

And when i want to load the synaptics packages i can´t find it, also with your description in searching routine. I realize that all the packages are green!! Maybe i have to load this two packages from ubuntu website, is this right?

With hope 
Frank

---

### Post by helmut_hed on 2007-03-30
Hi Frank,

I'm sorry to bring you bad news but if you had a PCTel modem supported by this driver, it would be listed in your lspci output somewhere.  You might try looking at the "slmodem" driver, or trying this site:

[http://linmodems.technion.ac.il/](http://linmodems.technion.ac.il/)

You should probably try their "scanmodem" script which is described there, for help.

Good luck,
Jeff

---

### Post by fseigert on 2007-03-30
Hi Jeff,

thanks, i hope the modem is VIA AC97 and it will be function when i installing two more packages. Maybe the manufacture gave me wrong information. I started another tread to look for doing the packages on. 

Will give you a final post when i know if the modem is working.

Frank

---

### Post by dr_d12 on 2007-04-07
Thanks, that was exactly what I needed to get online with this old Compaq
 -Dave

---

### Post by TransMayernik751 on 2008-06-04
I'm running Xubuntu 8.04 with a PCTel modem installed in the first PCI slot and I followed you directions. Everything was fine until the last command. This is the error I got:

camphill@camphill:~/pctel-0.9.7-9-rht-7$ sudo ./setup
checking for running kernel version...2.6.24
checking for ptserial...ptserial-2.6.c
checking for gcc...4.2.3
checking for kernel gcc version...4.2.3
searching for kernel includes...found at /lib/modules/2.6.24-16-generic/build/include
checking for autoconf.h.../lib/modules/2.6.24-16-generic/build/include/linux/autoconf.h
checking for asm/mach-default...yes
checking for kernel version in utsrelease.h...t.c:1:19: error: stdio.h: No such file or directory
t.c: In function ‘main’:
t.c:4: warning: incompatible implicit declaration of built-in function ‘printf’
./configure: line 476: ./t: No such file or directory
rm: cannot remove `./t': No such file or directory
** error
could not determine a proper UTS_RELEASE
** compilation error
please read the FAQ about reporting compilation problems
and report this problem.  A transcript of the build process
has been saved in src/make.log.  When reporting problems to
the development team, please send us this file.

I'm a complete noob to Xubuntu let alone Linux. Any ideas?
Thanks,
Nate

---

### Post by helmut_hed on 2008-06-04
Hi Nate,

Well, missing stdio.h is a new one... that's a pretty basic ingredient.  Have you installed the "build-essential" package?

Jeff

---

### Post by TransMayernik751 on 2008-06-05
Jeff,
You were right. The build-essentials pack wasn't installed (I thought it was), but I took care of that. Problem is, I ran into a new error. This is what I get when I try to compile it:

camphill@camphill:~/pctel-0.9.7-9-rht-7$ sudo ./setup
[sudo] password for camphill: 
checking for running kernel version...2.6.24
checking for ptserial...ptserial-2.6.c
checking for gcc...4.2.3
checking for kernel gcc version...4.2.3
searching for kernel includes...found at /lib/modules/2.6.24-16-generic/build/include
checking for autoconf.h.../lib/modules/2.6.24-16-generic/build/include/linux/autoconf.h
checking for asm/mach-default...yes
checking for kernel version in utsrelease.h...UTS_RELEASE is 2.6.24-16-generic
checking type of tty_struct.count...int
checking for presence of udev...present (kernel version 2.6.13 or later)
detecting your modem...found. Your modem is a pct789 type modem.
** compilation error
please read the FAQ about reporting compilation problems
and report this problem.  A transcript of the build process
has been saved in src/make.log.  When reporting problems to
the development team, please send us this file.

Here's the contents of the make.log file:

  CC	vuart.o
  LD	binary.a
make -C /lib/modules/2.6.24-16-generic/build M=/home/camphill/pctel-0.9.7-9-rht-7/src
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
scripts/Makefile.build:46: *** CFLAGS was changed in "/home/camphill/pctel-0.9.7-9-rht-7/src/Makefile". Fix it to use EXTRA_CFLAGS.  Stop.
make[1]: *** [_module_/home/camphill/pctel-0.9.7-9-rht-7/src] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make: *** [all] Error 2

I have no clue what this means. Any ideas?
Thanks in advance

---

### Post by helmut_hed on 2008-06-05
Aha!  I need to update this HOWTO :) The driver version given above is old.  Please try this link instead:

[http://linmodems.technion.ac.il/pctel-linux/pctel-0.9.7-9-rht-9.tar.gz](http://linmodems.technion.ac.il/pctel-linux/pctel-0.9.7-9-rht-9.tar.gz)

I believe this issue is fixed in that version.  Let me know if I'm wrong.

Jeff

---

### Post by TransMayernik751 on 2008-06-05
Success! I'm able to dial out no problem...

I just gotta get my ISP settings correct. It won't stay connected.

Thanks for the help, Jeff. I would've never figured that out on my own.

---

### Post by TransMayernik751 on 2008-06-13
One last thing. This install worked so well, I built another Ubuntu box for our office. I used another PCTEL I had laying around with a similiar chipset and was successful in getting the modem to work. I went to install the 135+ updates waiting for a fresh install of Ubuntu 8.04. Since downloading 100mb over dialup is pretty slow, I left it go overnight. When I came in this morning, the computer froze on the screensaver. I was forced to do a cold reboot. It started back up fine, but now the modem doesn't work. I tried reinstalling the drivers for it, but I got the following error:

detecting your modem...found. Your modem is a pct789 type modem.

compilation done

installation done
** error activating modem driver via insmod
please read the FAQ about reporting problems and report
this problem.  A transcript of the attempted activation
has been saved in src/make.log.  When reporting problems to
the development team, please send us this file.

The last few lines of the make.log file read:
/misc/pctel_hw.ko
/sbin/depmod -a
/sbin/insmod linmodem.ko
insmod: error inserting 'linmodem.ko': -1 Invalid module format
make: *** [insmod] Error 1

Any ideas?

---

### Post by helmut_hed on 2008-06-13
Hi TransM,

Perhaps the old modules are still lying around somewhere... I recommend this:

cd pctel-0.9.7-9-rht-9
sudo make uninstall
cd ..
rm -rf pctel-0.9.7-9-rht-9

then try the instructions again from the top.  Hopefully that will clear up your problem.

Regards,
Jeff

---

### Post by TransMayernik751 on 2008-06-13
This is what I got:

nate@ubuntuPCC:~/pctel-0.9.7-9-rht-9$ sudo make uninstall
make: *** No rule to make target `uninstall'.  Stop.

---

### Post by helmut_hed on 2008-06-13
Sorry, I missed one level of directories.  Please try this:

cd pctel-0.9.7-9-rht-9/src
sudo make uninstall
cd ../..
rm -rf pctel-0.9.7-9-rht-9

and let me know if that works.

Jeff

---

### Post by TransMayernik751 on 2008-06-13
It uninstalled ok, but I'm still having problems installing it. I think it may have something to do with update manager needing to finish installing updates. Problem is, I can't get it to do this through the proxy here at work. I'll take the computer home today and plug it into my (unrestricted) ISP.

Thanks for the help!

---

