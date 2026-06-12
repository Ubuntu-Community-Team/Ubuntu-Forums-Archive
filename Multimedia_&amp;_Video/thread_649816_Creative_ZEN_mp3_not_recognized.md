---
title: "Creative ZEN mp3 not recognized"
date: 2007-12-25
forum: Multimedia &amp; Video
---

### Post by Ivan Wagner on 2007-12-25
Hi to all!!

I'm trying to get my Creative ZEN mp3 player working under Ubuntu Feisty! There's no way the device gets recognized by Gnomad 2, even though the device is seen in the usb by **lsusb**:

```

Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 003 Device 004: ID 0a5c:4502 Broadcom Corp. 
Bus 003 Device 005: ID 0a5c:4503 Broadcom Corp. 
Bus 003 Device 003: ID 413c:8126 Dell Computer Corp. 
Bus 003 Device 002: ID 0a5c:4500 Broadcom Corp. 
Bus 003 Device 001: ID 0000:0000  
Bus 005 Device 002: ID 046d:c047 Logitech, Inc. 
Bus 005 Device 001: ID 0000:0000  
Bus 001 Device 006: ID 041e:4157 Creative Technology, Ltd 
Bus 001 Device 001: ID 0000:0000  

```

By using the **mtp-detect** command, the output is the following:

```

libmtp version: 0.2.1

Attempting to connect device(s)
Detect: No Devices have been found

```

Can anyone help me out?


Cheers,

Ivan.

---

### Post by nickaj on 2007-12-25
I have the exaxt same problem, same player, recognized by lsusb but not by anything else.

---

### Post by NamedUser on 2007-12-25
I have a creative Zen V and I can interface to it just fine using Rythmbox. I don't know if anything else works or not since I haven't tried. Well, I use Gutsy, but I'm pretty sure it was the same deal in Feisty.

---

### Post by dje on 2007-12-25
Have you tried kzenexplorer?
```
sudo apt-get install kzenexplorer
```
If that doessn't work ensure libmtp5 is installed
```
sudo apt-get install libmtp5
```
Hope that helps :)

---

### Post by nickaj on 2007-12-25
I've tried amarok, banshee, rythmbox, gnomad, and now kzenexplorer but none of them recognize it.  the libmtp site ( [http://libmtp.sourceforge.net/index.php?page=compatibility](http://libmtp.sourceforge.net/index.php?page=compatibility) ) lists most creative products  but not my exact model (Creative Zen 4GB).  The closest one is the Creative Zen 8GB, but I don't think that there's any difference betwee the models besides memory size.

---

### Post by nickaj on 2007-12-25
Of course the problem could just be the flaky hardware in my old laptop.  I'll test it on my other PC (also running feisty) and see whether there's a difference.  Thanks to everyone with advice!

---

### Post by nickaj on 2007-12-25
Not being recognized on the other computer either, so I'm stuck in the same position as Ivan.  If anyone has ideas that would be amazing.

---

### Post by nickaj on 2007-12-25
OK so I've made a small amount of progress...

[[COLOR="Red"]This thread[/COLOR]]("http://forum.ubuntu-fr.org/viewtopic.php?pid=1408205") suggested running as root.

When I run the programs as the root user the system at least knows that a device exists, and the "docked" screen comes up on he player, but gnomad still gives and error message.

"sudo mtp-detect" gives me:
[INDENT][INDENT]Autodetected device with VID=041e and PID=4157 is UNKNOWN.
Please report this VID/PID and the device model name etc to the
libmtp development team!
PTP: Opening session
PTP: request code 0x0000 sending req wrote only 16 bytes instead of 0
PTP ERROR IO: Trying again after resetting USB
PTP: Opening session
Could not get device info!
Connection error.
No devices.
[/INDENT][/INDENT]

[[COLOR="Red"]Another thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=199250") has a long process for recompiling gnomad and libmtp but its for older versions of ubuntu, and I don't have enough experience to do the kind of stuff it prescribes.

---

### Post by Ivan Wagner on 2007-12-26
Sorry guys I'm on Gusty...

Anyways by **sudo mtp-detect** I get the following messages:

```

libmtp version: 0.2.1

Attempting to connect device(s)
Device 1 (VID=041e and PID=4157) is UNKNOWN.
Please report this VID/PID and the device model to the libmtp development team
PTP: Opening session
LIBMTP PANIC: Could not get device info!
LIBMTP PANIC: configure_usb_devices() error code: 7 on line 1806
Detect: There has been an error connecting. Exiting

```

And when I tried for the second time:

```

libmtp version: 0.2.1

Attempting to connect device(s)
Device 1 (VID=041e and PID=4157) is UNKNOWN.
Please report this VID/PID and the device model to the libmtp development team
PTP: Opening session
PTP: request code 0x1002 sending req wrote only 0 bytes instead of 16
PTP_ERROR_IO: Trying again after resetting USB
PTP: Opening session
LIBMTP PANIC: Could not get device info!
LIBMTP PANIC: configure_usb_devices() error code: 7 on line 1806
Detect: There has been an error connecting. Exiting

```

But on the Zen's display (by the way it is the 8 GB version...) I see the USB icon... This didn't happen before...

---

### Post by Ivan Wagner on 2007-12-26
Ok people I have version 0.2.1 of libmtp on my machine... Creative Zen 8GB has problems until version (excluded) 0.2.2. So I'll attempt to compile the library from source.

Cheers,

Ivan.

---

### Post by Papa-san on 2007-12-26
Any suggestions when you get this?
```
john@john-laptop:~$ sudo mtp-detect
Password:
sudo: mtp-detect: command not found
john@john-laptop:~$

```

---

### Post by nickaj on 2007-12-26
I upgraded to gutsy, but it didnt change a whole lot.  after compiling the newer libmtp version, "mtp-detect' can recognize the player but my media players still cant find it.

I suspect that the players are still using the old libmtp package (libmtp6 aka. 0.2.1) which is the default with gutsy.  libmtp7 is on the system but i dont know if the media players know to use it or even can use it.  Is there a way to force gnomad, banshee etc to use the new libmtp?

---

### Post by mylo on 2007-12-26
> **Papa-san said:**
> Any suggestions when you get this?
```
john@john-laptop:~$ sudo mtp-detect
Password:
sudo: mtp-detect: command not found
john@john-laptop:~$

```

try installing the libmtp-dev package - it should be in there with several other programs.

---

### Post by nickaj on 2007-12-26
THESE INSTRUCTIONS WORK:
[http://ubuntuforums.org/showthread.php?t=643512&highlight=libmtp](http://ubuntuforums.org/showthread.php?t=643512&highlight=libmtp)

(for gnomad anyway.  i started it with "sudo gnomad2", don't know yet if it will work from GUI)

---

### Post by tomleech on 2007-12-28
sorry didn't mean to send this twice

hello 
I have exactly the same problem (identical error message with mtp-detect) with my new zen 8gb and have libmtp 0.2.1 installed (as libmtp6 from the synaptic package manager i think).  how do you install libmtp 0.2.4?
this is probably a very stupid question but I don't know anything about installing packages outside of the gui installers
thanks
tom

---

### Post by tomleech on 2007-12-28
hello
I have exactly the same problem (identical error message with mtp-detect) with my new zen 8gb and have libmtp 0.2.1 installed (as libmtp6 from the synaptic package manager i think). how do you install libmtp 0.2.4?
this is probably a very stupid question but I don't know anything about installing packages outside of the gui installers
thanks
tom
EDIT - i worked this out using msak007's how to  'Creative Zen MP3 player working in Dapper using Gnomad' in hardware and laptops, replacing the old libmtp and gnomad versions with the newest ones and using make install not checkinstall and now my zen appears to be recognized and working

---

### Post by &lt;&lt;joe&gt;&gt; on 2008-04-02
did anyone get this working
i am geting the same error
```

joe@Fox:~$ sudo mtp-detect
libmtp version: 0.2.1

Attempting to connect device(s)
Device 1 (VID=041e and PID=4157) is UNKNOWN.
Please report this VID/PID and the device model to the libmtp development team
PTP: Opening session
PTP: request code 0x1002 sending req wrote only 5975689584 bytes instead of 16
PTP_ERROR_IO: Trying again after resetting USB
PTP: Opening session
LIBMTP PANIC: Could not get device info!
LIBMTP PANIC: configure_usb_devices() error code: 7 on line 1806
Detect: There has been an error connecting. Exiting
joe@Fox:~$ 

```

---

### Post by knowledge_is_power on 2008-04-07
I have the exact same problem.  Except I dual boot.  In windows it finds it good and I can transfer music, etc from winamp, but nothing in ubuntu.  I JUST replaced my 2gb with a 4gb zen v, and thats when the problem started.  (eg. the 2gb worked great.... ???) Only thing i can think of is that i upgraded the firmware on my old one.  imma give it a try and get back to you guys.

---

### Post by knowledge_is_power on 2008-04-07
k yea wtf.  no deal.  the only thing i can think of is that my old one was a zen v plus and this is only a zen v video??  shouldnt make a difference since they are both mtp. but then why would one work and the other one not?:confused::confused:

---

### Post by knowledge_is_power on 2008-04-07
ok.  so check out the attached .txt file.  thats the output i get.  similar?
when i run 
```
sudo gnomad2 
```
it works just fine.
but not when i just run gnomad, or in amarok or in rythmbox or in anything.  anyone know how to fix?  with my 2gb model, it actualy automagically ran rythmbox whenever i connected it. it was beautiful.

it would be stupid if libmtp supported the ven v plus but not the zen v video, or the zen v 2gb but not the zen v 4gb. :(

---

### Post by gandalf001 on 2008-07-09
Hi,
I've got this problem and solve it (I have Ubuntu 7.10)
My creative Zen Mp3 model is 4157 (given by lsusb) and that's the problem.

The version of gnomad2 that I have installed by "add/remove program" was not working so I had compiled the last version by following the instructions here:

[http://gnomad2.sourceforge.net/?section=article](http://gnomad2.sourceforge.net/?section=article)
(same here : [http://www.linux.ie/articles/tutorials/zen.php](http://www.linux.ie/articles/tutorials/zen.php))

by that wasn't working so I try to install manually libmtp7 and compile gnomad with it.

(I suggest you to run ./configure separately to check that you will build gnomad2 with the good version of the package)

And finally I found :
[https://bugs.launchpad.net/ubuntu/+s...jb/+bug/227540](https://bugs.launchpad.net/ubuntu/+s...jb/+bug/227540)

<< Binary package hint: libnjb5

File /etc/udev/rules.d/45-libnjb.rules simply misses an entry for this device. As a result, when it is plugged in, the device file is created with wrong ownership (root.root) and gnomad2 under normal user fails to see the device (NOTE: it does not report "permission denied", it just reports that it can't see it on the USB bus).

Apparently it is a big pain, as people recommend to compile the latests versions of libmtp and gnomad from source and then run them with superuser privileges, while it is a matter of 1 line in the rules file.

This entry seems to solve the problem:
# Creative Zen
SYSFS{idVendor}=="041e", SYSFS{idProduct}=="4157", GROUP="plugdev", MODE="0660"

The device in question:
[http://fi.europe.creative.com/produc...&product=16999](http://fi.europe.creative.com/produc...&product=16999)

True for Ubuntu 7.10 and 8.10, however in 8.10 libmtp7.rules contain the required line and changes in libnjb.rules are not needed for gnomad2 operation. In 7.10 it is however a problem. >>

So I added these lines in this file and it works  :guitar:
But it should work with libmtp7  :confused:

---

