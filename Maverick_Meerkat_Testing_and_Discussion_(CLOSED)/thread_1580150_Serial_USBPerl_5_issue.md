---
title: "Serial USB/Perl 5 issue"
date: 2010-09-22
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by odror on 2010-09-22
Did anyone have a problem accessing a serial USB device using perl5 on ubuntu 10.10?

I have a script written in perl that was working fine on ubuntu 10.04, when accessing /dev/ttyUSB0 (USB to serial port)

In the current version this script freeze or goes to an infinite loop when accessing the ttyUSB device. any thoughts?



I have the MyBlaster.pl that controls IR blaster. it was working fine on Ubuntu 10.04. now it freezes
The following subroutine is called and freeze:

my $serial=init_serial("/dev/ttyUSB0","19200");

The first few line of this subroutine are:

> sub init_serial {
        my($port,$baud)=@_;
        my($termios,$cflag,$lflag,$iflag,$oflag);
        my($voice);

        my $serial=new FileHandle("+>$port") || die "Could not open $port: $!\n";

The call to New FileHandler fails, which is in

> IO::File::new(/usr/lib/perl/5.10/IO/File.pm:35):


---

### Post by tormod on 2010-09-23
Do you have a serial port so you can verify that this is a "USB serial" issue and not just a "serial" issue?

---

### Post by odror on 2010-09-24
I do not have a serial port I have a USB to Serial device.

I was able to trace the problem to the open command. when /dev/ttyUSB0 is being open.

AT this point I think that the issue is either kernel/driver/USB issue. or libc issue.

When you open a device it should not freeze. It should at least return an error message.

---

### Post by tormod on 2010-09-24
What chipset (or kernel driver) is your USB-serial adapter using?

---

### Post by odror on 2010-09-24
> **tormod said:**
> What chipset (or kernel driver) is your USB-serial adapter using?

looking at lsmod

I am seeing these modules **usbserial **and **pl2303**

---

### Post by tormod on 2010-09-24
I have the same chipset. Do you have a small program to reproduce it, that does not depend on specific serial input? Then I could try it out myself.

---

### Post by odror on 2010-09-24
> **tormod said:**
> I have the same chipset. Do you have a small program to reproduce it, that does not depend on specific serial input? Then I could try it out myself.

I will try to send it this evening. Basically I am using a perl script for MyBlaster.

One of the first thing the script does is to open the device (/dev/ttyUSB0) for reading and writing using the open command. It freezes on the open operation. I do not think that you need to use perl. for that.

---

### Post by odror on 2010-09-25
> **tormod said:**
> I have the same chipset. Do you have a small program to reproduce it, that does not depend on specific serial input? Then I could try it out myself.

use the following program. it will reproduce the problem. It will freeze when opening the port.

> #!/usr/bin/perl

$|=1;
use POSIX qw(:termios_h);
use FileHandle;
use Time::HiRes qw( sleep ); 

$port = "/dev/ttyUSB0" ;
$serial = new FileHandle("+>$port") ;	  	  




---

### Post by tormod on 2010-09-25
Thanks, I can reproduce the hang with this C code:
```
#define _GNU_SOURCE
#include <fcntl.h>
#include <stdio.h>

int main (int argc, char **argv)
{
   int fd;

   fd = open("/dev/ttyUSB0", O_RDWR);
   printf("fd has value %i\n", fd);
}
```

---

### Post by tormod on 2010-09-25
It does not hang when using the 2.6.35-22.33-generic kernel on Ubuntu 10.04.

---

### Post by odror on 2010-09-25
> **tormod said:**
> It does not hang when using the 2.6.35-22.33-generic kernel on Ubuntu 10.04.

Yes I know that. It was working for me also in 10.04.

The problem started after the upgrade to 10.10

---

### Post by odror on 2010-09-25
> **tormod said:**
> Thanks, I can reproduce the hang with this C code:
```
#define _GNU_SOURCE
#include <fcntl.h>
#include <stdio.h>

int main (int argc, char **argv)
{
   int fd;

   fd = open("/dev/ttyUSB0", O_RDWR);
   printf("fd has value %i\n", fd);
}
```

I just confirmed that this C code works fine in 10.04, but fails on 10.10. I it clearly a driver issue, or less likely a libc issue.

---

### Post by tormod on 2010-09-25
> **odror said:**
> Yes I know that. It was working for me also in 10.04.

The problem started after the upgrade to 10.10
The point is that I was using the latest Maverick kernel successfully in 10.04. So it does not seem to be a kernel issue.

---

### Post by odror on 2010-09-25
I tried that program using the same computer, but booting to the ubuntu 10.10 beta live CD. When I do that I Do not have the probem

One of the following is likely:

It may be a kernel/libc problem since the beta live CD.

My Ubuntu 10.10 is not a fresh install, but rather an upgrade of ubuntu 10.04. It is possible that the upgrade process was not done well.

When I did the upgrade I clones ubuntu 10.04 (from dell xps 9000) to an SSD drive, and then installed the SSD drive on HP 380t machine. The Hp computer seemed to have excepted the cloned Dell drive with no problem, and then I upgraded the HP machine to 10.10. Can this be the problem?

Beside a fresh install Do you have any idea how I can fix the problem.

---

### Post by odror on 2010-09-25
I am sorry to confuse everyone. I have done more extensive tests.

It **DOES NOT** work on any computer using the beta 10.10 live cd. It still will not work even if I compile using 10.04 libc. It is learly an Ubuntu 10.10 Kernel issue.

I was wrong in the prior post. Because it worked only once. from the second test on it did not work. ( It means that the serial device remember being on 10.04 machine. for one session only).

---

### Post by tormod on 2010-09-25
I also reproduced it on a live CD (Maverick after the Beta, Sep 15 I think). But since the latest Maverick kernel works fine (as I reported above, testing in 10.04) it can not be the kernel.

---

### Post by odror on 2010-09-25
> **tormod said:**
> I also reproduced it on a live CD (Maverick after the Beta, Sep 15 I think). But since the latest Maverick kernel works fine (as I reported above, testing in 10.04) it can not be the kernel.

Did you tested on kernel from the 10.10 ubuntu dist. it may represent modification to the kernel done for ubuntu. Unless it is a libc issue. It is not hardware issue.

---

### Post by odror on 2010-09-26
I found a workaround that solves the problem.

after reboot type the commands:

> modprobe -r pl2303
modprobe  pl2303


---

