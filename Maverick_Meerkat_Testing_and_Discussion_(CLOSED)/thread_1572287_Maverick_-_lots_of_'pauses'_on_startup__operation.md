---
title: "Maverick - lots of 'pauses' on startup / operation"
date: 2010-09-10
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by conor on 2010-09-10
Hello, 

I'm experiencing a problem that I haven't seen before on the maverick 10.10 beta.  I've got it on a full HD install.  As the system starts up, and also periodically during use, the system will freeze up.  I hit enter a bunch of times and it starts rolling again.  I can't tell if it is an I/O error or what.  Could anybody tell me what logfile I should look under, or if this has happened to them before?

It starts right after the grub prompt and a Glib error about not being able to do something because of an unknown username. 

I know this is vague and unhelpful, but if anyone has any hints as to where I can start looking it'd be muchly appreciated.  

Cheers,
Conor

---

### Post by lisati on 2010-09-10
Moved to Maverick Meerkat Testing and Discussion

---

### Post by VMC on 2010-09-10
> **conor said:**
> Hello, 

I'm experiencing a problem that I haven't seen before on the maverick 10.10 beta.  I've got it on a full HD install.  As the system starts up, and also periodically during use, the system will freeze up.  I hit enter a bunch of times and it starts rolling again.  I can't tell if it is an I/O error or what.  Could anybody tell me what logfile I should look under, or if this has happened to them before?

It starts right after the grub prompt and a Glib error about not being able to do something because of an unknown username. 

I know this is vague and unhelpful, but if anyone has any hints as to where I can start looking it'd be muchly appreciated.  

Cheers,
Conor

Maybe startup in recovery mode and type ```
cat /etc/passwd
```,then look for the user and their home directory. Make sure it exists. 

If you can get to a desktop its "system>admin>Users&Groups".

Maybe you had the /home as a partition that got deleted.

---

### Post by conor on 2010-09-10
Hi VMC,

Thanks for your suggestion.  Everything appears fine in userland.  I just installed some updates and it seems boot now wants to be more verbose.  I've come across some errors: 

```
udevd[396]: worker [402] unexpectedly returned with status 0x0100

udevd[396]: worker [402] failed while handling '/devices/pci0000:00/0000:00:1f.2/host2/target2:0:0/2:0:0:0/block/sda/sda3'

udevd[396]: worker [410] unexpectedly returned with status 0x0100

udevd[396]: worker [410] failed while handling '/devices/pci0000:00/0000:00:1f.0'

udevd[396]: worker [418] unexpectedly returned with status 0x0100

udevd[396]: worker [418] failed while handling '/devices/pci0000:000000:00:1b.0'

udevd[396]: worker [420] unexpectedly returned with status 0x0100

udevd[396]: worker [420] failed while handling '/devices/virtual/block/loop2'

udevd[396]: worker [424] unexpectedly returned with status 0x0100

udevd[396]: worker [424] failed while handling '/devices/platform/i8042/serio1'

udevd[396]: worker [429] unexpectedly returned with status 0x0100

udevd[396]: worker [429] failed while handling '/devices/virtual/tty/tty1'

udevd[396]: worker [430] unexpectedly returned with status 0x0100

udevd[396]: worker [430] failed while handling '/devices/virtual/block/loop0'

udevd[396]: worker [431] unexpectedly returned with status 0x0100

udevd[396]: worker [431] failed while handling '/devices/pci0000:00/0000:00:1d.7/usb1/1-2/1-2:1.0'

udevd[396]: worker [432] unexpectedly returned with status 0x0100

udevd[396]: worker [432] failed while handling '/devices/pci0000:00/0000:00:1c.1/0000:03:00.0'

udevd[396]: worker [433] unexpectedly returned with status 0x0100

udevd[396]: worker [433] failed while handling '/devices/virtual/block/loop1'

udevd[396]: worker [434] unexpectedly returned with status 0x0100

udevd[396]: worker [434] failed while handling '/devices/virtual/block/loop3'

udevd[396]: worker [435] unexpectedly returned with status 0x0100

udevd[396]: worker [435] failed while handling '/devices/virtual/block/loop4'

udevd[396]: worker [443] unexpectedly returned with status 0x0100

udevd[396]: worker [443] failed while handling '/devices/virtual/block/loop5'

udevd[396]: worker [444] unexpectedly returned with status 0x0100

udevd[396]: worker [444] failed while handling '/devices/virtual/block/loop6'

init: udevtrigger post-stop process (528) terminated with status 1

udevd[396]: worker [445] unexpectedly returned with status 0x0100

udevd[396]: worker [445] failed while handling '/devices/virtual/block/loop7'

udevd[396]: worker [447] unexpectedly returned with status 0x0100

udevd[396]: worker [447] failed while handling '/devices/virtual/tty/tty3'

udevd[396]: worker [448] unexpectedly returned with status 0x0100

udevd[396]: worker [448] failed while handling '/devices/virtual/tty/tty2'

udevd[396]: worker [484] unexpectedly returned with status 0x0100

udevd[396]: worker [484] failed while handling '/devices/virtual/tty/tty6'

udevd[396]: worker [485] unexpectedly returned with status 0x0100

udevd[396]: worker [485] failed while handling '/devices/virtual/tty/tty4'

udevd[396]: worker [486] unexpectedly returned with status 0x0100

udevd[396]: worker [486] failed while handling '/devices/virtual/tty/tty5'

udevd[396]: worker [492] unexpectedly returned with status 0x0100

udevd[396]: worker [492] failed while handling '/devices/LNXSYSTM:00/LNXSYBUS:00/TOS1900:00'

udevd[396]: worker [494] unexpectedly returned with status 0x0100

udevd[396]: worker [494] failed while handling '/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:26/PNP0C09:00/TOS6205:00'

```

Does anyone know if these could be causing the slowdowns?

---

### Post by conor on 2010-09-12
Just if anyone is Interested, it seems the problem was a Toshiba BIOS power-save feature that halts the HDD when nothing is happening, causing the drive to shut off a number of times during boot.  This can be disabled in the bios.

---

### Post by blazk on 2010-09-14
I have similar problem with my Toshiba NB205 netbook. Since the kernel 2.6.35-19 (2.6.35-21 at the moment) the boot pauses several times and each time I have to hit a key to continue. I do not have any freezes during the operation. It happens again during shutdown.

I could not find anything about HDD power saving in the BIOS.

also could not find any clues for that problem in /var/log/syslog.

I am running a bit nonstandard setup: maveric meerkat installed
from alternate cd + xorg edgers ppa packages.

still not solved for me..

---

### Post by conor on 2010-09-14
I jumped the gun a little when I tagged this post as solved.

The option you are looking for is called SATA controller or something like that and the options are ACPI or Compatibility.  You want Compatibility.  

Pauses still happen once during startup, at times during apt-get processes, sometimes while streaming flash videos and once during shutdown.  

Not sure how to fix.  But it is improved.  I also found the desktop interface to be much less problematic than the Unity interface.

---

### Post by blazk on 2010-09-14
Oh ok, mine was in 'Compatibility' mode all the time ('AHCI' mode caused very slow boot in earlier ubuntus and freebsd).

Also I tried to downgrade from xorg-edgers ppa to the stock xorg but it did not help (initially it appeared to me that these pauses happened only during the framebuffer mode switching, though now it seems they are more frequent).

I am using 2.6.35-17 kernel which does not seem to have this pausing problem.

---

### Post by conor on 2010-09-20
There is a bug for this issue here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/638434](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/638434)

---

