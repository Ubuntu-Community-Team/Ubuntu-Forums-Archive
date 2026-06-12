---
title: "Lirc with mceusb2 driving me insane :("
date: 2007-03-19
forum: Multimedia &amp; Video
---

### Post by deb123 on 2007-03-19
I bought a Hauppauge WinTv-PVR 150 MCE, and I've been trying to make this work for 2 weeks now. The card runs fine, but i can't get the remote to work :(

It is a kit that comes with a usb IR blaster. The remote is tagged "RC6".
I tried about everything i could: 3 different tutorials, tried to install from source, tried it on Debian and Fedora core too before going back to ubuntu edgy.
The install goes well (i choose to install only the mceusb2 driver)
On all three different linux distributions, and no matter how i install/build/configure it, it always does the same thing:  irw just returns a command prompt and crashes the lircd daemon.
So there must be something i consistently do wrong... ;)
Btw, i have always used the 2.6.17+ kernels, because i need it for my hard drives... Could that be the problem?

Here's a few logs:
ls -la /dev/lirc*
```
crw-rw-rw- 1 root root 61, 0 2007-03-19 19:38 /dev/lirc
srw-rw-rw- 1 root root     0 2007-03-19 19:06 /dev/lircd
prw-rw-rw- 1 root root     0 2007-03-19 19:38 /dev/lircm

```dmesg |grep lirc
```
[17179589.524000] lirc_dev: IR Remote Control driver registered, at major 61 
[17179589.532000] lirc_mceusb2: no version for "lirc_get_pdata" found: kernel tainted.
[17179589.532000] lirc_mceusb2: Philips eHome USB IR Transciever and Microsoft MCE 2005 Remote Control driver for LIRC v0.26
[17179589.532000] lirc_mceusb2: Daniel Melander <lirc@rajidae.se>, Martin Blatter <martin_a_blatter@yahoo.com>
[17179589.536000] usbcore: registered new driver lirc_mceusb2
```
lsusb
```
Bus 002 Device 003: ID 05e3:070e Genesys Logic, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 045e:00a0 Microsoft Corp. 
Bus 001 Device 001: ID 0000:0000  
```


mode2
```
mode2: error opening /dev/lirc
mode2: No such device

```


Hardware.conf
```
# /etc/lirc/hardware.conf
#
# Arguments which will be used when launching lircd
LIRCD_ARGS=""

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD=false

#Try to load appropriate kernel modules
LOAD_MODULES=true

# Run "lircd --driver=help" for a list of supported drivers.
DRIVER=""
# If DEVICE is set to /dev/lirc and devfs is in use /dev/lirc/0 will be
# automatically used instead
DEVICE=""
MODULES="lirc_mceusb2"

# Default configuration files for your hardware if any
LIRCD_CONF=""
LIRCMD_CONF=""
```

The remote works on windows, so it shouldn't be a hardware problem...
I am completely stuck. Any help or ideas are greatly appreciated!
Thanks!

Vincent

---

### Post by deb123 on 2007-03-23
While browsing (hopelessly) through the files in the kernel directories, i saw the "irda" module. It looks like it has something to do with IR remote controls... Could that be conflicting with lirc?

Still trying to get lirc to work... :(

---

### Post by vbc on 2007-03-27
I am not an "expert". I have been beating my head against the same wall as you.

I have exactly the same hardware as you, and **HAD** exactly the same problem. Sometime during the many hours I spent trying to solve this, my "/dev/lirc" entry changed to "/dev/lirc0" (Note the zero)! I remember seeing something about this happening in the many posts I read, but I don't recall why it happens.

Re-run your "[FONT="Courier New"]ls -la /dev/lirc*[/FONT]" command. If your "/dev/lirc" is now "/dev/lirc0", then edit the DEVICE parameter in your "/etc/lirc/hardware.conf" to be "/dev/lirc0". Mine looks like this:
```
# /etc/lirc/hardware.conf
#
# Arguments which will be used when launching lircd
LIRCD_ARGS=""

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD=false

#Try to load appropriate kernel modules
LOAD_MODULES=true

# Run "lircd --driver=help" for a list of supported drivers.
DRIVER=""
# If DEVICE is set to /dev/lirc and devfs is in use /dev/lirc/0 will be
# automatically used instead
DEVICE="/dev/lirc0"
MODULES="lirc_mceusb2"

# Default configuration files for your hardware if any
LIRCD_CONF=""
LIRCMD_CONF=""

```

Then restart lirc:

[FONT="Courier New"]sudo /etc/init.d/lirc restart
[/FONT]

Then try "irw" and push buttons on your remote. Hopefully, you will see button codes.
If you do, then fire up the frontend and it *should* work with the remote.

If this doesn't fix it, keep trying other things, because the hardware you (and I) bought works **GREAT** with MythTV (eventually).

There are probably better ways to fix this, but this worked for me.

---

### Post by deb123 on 2007-03-29
Thanks for your reply, i was starting to lose hope that it is possible to make this work.
I am not a linux expert either, but if there's one thing good about all this trouble, it's that i learned quite a lot about linux :)
I can create /dev/lirc0 with "mknod /dev/lirc0 c 61 0", but it still doesn't work. It's always the same thing: irw returns a command prompt, and lircd crashes.
I will try to make a fresh ubuntu install again, to make sure nothing else could be conflicting with lirc (like one of the many lirc versions that i installed).

---

### Post by vbc on 2007-03-29
There are **lots** of people with this problem. Apparently, the penguins are buying this card/remote in large numbers. :)

Unfortunately, my "solution" **did not** survive a reboot. Now, I have neither "/dev/lirc" **or** "/dev/lirc0", so I am back to troubleshooting mode.

At least I had it working for a few hours, so I know it's possible. I will post on this thread if I figure it out.

Good Luck.

---

### Post by deb123 on 2007-03-30
It's good to know that we're not alone.
Do you know which version of lirc worked on your computer?
Would it work after rebooting if you type "mknod /dev/lirc0 c 61 0"

Well, weekend is coming. I'll have more time to play with lirc. ;)

---

### Post by majoridiot on 2007-03-30
i suggest starting from scratch with this guide: [https://help.ubuntu.com/community/Install_Lirc_Edgy](https://help.ubuntu.com/community/Install_Lirc_Edgy)

it worked perfectly the first time with my MCE usb remote (RC6). i also suggest using superm1's
"third party repositiory" given in that guide as well- it builds a much more responsive remote module.
for mceusb2

good luck!

---

### Post by deb123 on 2007-03-31
> **majoridiot said:**
>  i also suggest using superm1's
"third party repositiory" given in that guide as well- it builds a much more responsive remote module.
for mceusb2

good luck!

I had already tried this guide from scratch, but it didn't work.

But...

\\:D/ 
I now have my remote working!!!! :D
\\:D/ 

This morning, i tried a few ideas that i wanted to check during the week, and (**magic**) it worked! But i've been struggling with this problem for a few weeks now, so i really wanted to know what made this work. The bug was beaten and retreating, so i wasn't about to let it get away so easily :) I wanted this little monster's head stuffed and hanging over my fireplace ;) lol

Ok, getting to the point:
There seems to be a lot of different remotes that are labeled "RC6". I have this one:
[http://www.mythtv.org/wiki/images/archive/2/28/20070303025534%21Mce-hauppauge.jpg](http://www.mythtv.org/wiki/images/archive/2/28/20070303025534%21Mce-hauppauge.jpg)

Now, i don't know if there's a hardware difference between all the RC6, but it seems the lirc_mceusb2 driver didn't have my remote control's id built in. So it never picked up the usb device, and lircd always crashed.

After installing any version of lirc with lirc_mceusb2, "cat /proc/bus/usb/devices" would always show:
```
T:  Bus=01 Lev=01 Prnt=01 Port=02 Cnt=01 Dev#=  2 Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=16 #Cfgs=  1
P:  Vendor=045e ProdID=00a0 Rev= 0.00
S:  Manufacturer=Microsoft
S:  Product=eHome Infrared Transceiver
S:  SerialNumber=MS0005es
C:* #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
E:  Ad=01(O) Atr=03(Int.) MxPS=  16 Ivl=1ms
E:  Ad=81(I) Atr=03(Int.) MxPS=  16 Ivl=1ms
```

Note the "Driver=(none)" near the end.

So i went to see in the source file of the driver (lirc_mceusb2.c)
Around line 120, there is a list of vendor IDs and a table of all the supported device IDs:
```
#define VENDOR_PHILIPS		0x0471
#define VENDOR_SMK              0x0609
#define VENDOR_TATUNG		0x1460
#define VENDOR_GATEWAY		0x107b
#define VENDOR_SHUTTLE		0x1308
#define VENDOR_MITSUMI          0x03ee
#define VENDOR_TOPSEED          0x1784 
#define VENDOR_RICAVISION       0x179d
#define VENDOR_ITRON            0x195d
#define VENDOR_FIC		0x1509

static struct usb_device_id usb_remote_table [] = {
	{ USB_DEVICE(VENDOR_PHILIPS, 0x0815) },	/* Philips eHome Infrared Transciever */
	{ USB_DEVICE(VENDOR_SMK, 0x031d) },	/* SMK/Toshiba G83C0004D410 */
	{ USB_DEVICE(VENDOR_TATUNG, 0x9150) },  /* Tatung eHome Infrared Transceiver */
	{ USB_DEVICE(VENDOR_SHUTTLE, 0xc001) },  /* Shuttle eHome Infrared Transceiver */
        { USB_DEVICE(VENDOR_GATEWAY, 0x3009) },  /* Gateway eHome Infrared Transceiver */
        { USB_DEVICE(VENDOR_MITSUMI, 0x2501) },  /* Mitsumi */
	{ USB_DEVICE(VENDOR_TOPSEED, 0x0001) },  /* Topseed eHome Infrared Transceiver */ 
	{ USB_DEVICE(VENDOR_RICAVISION, 0x0010) }, /* Ricavision internal Infrared Transceiver */
	{ USB_DEVICE(VENDOR_ITRON, 0x7002) },   /* Itron ione Libra Q-11 */
	{ USB_DEVICE(VENDOR_FIC, 0x9242) },     /* FIC eHome Infrared Transceiver */
	{ }					/* Terminating entry */
};
```

So i added:
```
#define VENDOR_MICROSOFT	0x045e
```
And
```
	{ USB_DEVICE(VENDOR_MICROSOFT, 0x00a0) },
```
(Got the codes from "lsusb" or also "cat /proc/bus/usb/devices" ->Vendor & ProdId)

Rebuilt the driver, modprobe lirc_mceusb2, restarted lircd, and now irw works! :)
Also, now  "cat /proc/bus/usb/devices" shows:
```
...
I:  If#= 0 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=lirc_mceusb2
...
```

I don't know if a newer version of lirc (if any?) or the one in superm1's repository would have this little modification already done. I have used lirc v0.8.1 from the lirc web site.

When i think of all the time i spent for something that just couldn't work for such a simple reason.. :-({|= 

Now, to get the IR blaster working... :)

---

### Post by majoridiot on 2007-03-31
now that is *exceptionally* odd, as that is the exact same remote i use and it builds without fail the
first time.

i'll send superm1 a link to this to see if it's something in packaging or what.

glad you got it working! :)

---

### Post by superm1 on 2007-03-31
> **deb123 said:**
> I had already tried this guide from scratch, but it didn't work.

But...

\\:D/ 
I now have my remote working!!!! :D
\\:D/ 

This morning, i tried a few ideas that i wanted to check during the week, and (**magic**) it worked! But i've been struggling with this problem for a few weeks now, so i really wanted to know what made this work. The bug was beaten and retreating, so i wasn't about to let it get away so easily :) I wanted this little monster's head stuffed and hanging over my fireplace ;) lol

Ok, getting to the point:
There seems to be a lot of different remotes that are labeled "RC6". I have this one:
[http://www.mythtv.org/wiki/images/archive/2/28/20070303025534%21Mce-hauppauge.jpg](http://www.mythtv.org/wiki/images/archive/2/28/20070303025534%21Mce-hauppauge.jpg)

Now, i don't know if there's a hardware difference between all the RC6, but it seems the lirc_mceusb2 driver didn't have my remote control's id built in. So it never picked up the usb device, and lircd always crashed.

After installing any version of lirc with lirc_mceusb2, "cat /proc/bus/usb/devices" would always show:
```
T:  Bus=01 Lev=01 Prnt=01 Port=02 Cnt=01 Dev#=  2 Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=16 #Cfgs=  1
P:  Vendor=045e ProdID=00a0 Rev= 0.00
S:  Manufacturer=Microsoft
S:  Product=eHome Infrared Transceiver
S:  SerialNumber=MS0005es
C:* #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
E:  Ad=01(O) Atr=03(Int.) MxPS=  16 Ivl=1ms
E:  Ad=81(I) Atr=03(Int.) MxPS=  16 Ivl=1ms
```Note the "Driver=(none)" near the end.

So i went to see in the source file of the driver (lirc_mceusb2.c)
Around line 120, there is a list of vendor IDs and a table of all the supported device IDs:
```
#define VENDOR_PHILIPS        0x0471
#define VENDOR_SMK              0x0609
#define VENDOR_TATUNG        0x1460
#define VENDOR_GATEWAY        0x107b
#define VENDOR_SHUTTLE        0x1308
#define VENDOR_MITSUMI          0x03ee
#define VENDOR_TOPSEED          0x1784 
#define VENDOR_RICAVISION       0x179d
#define VENDOR_ITRON            0x195d
#define VENDOR_FIC        0x1509

static struct usb_device_id usb_remote_table [] = {
    { USB_DEVICE(VENDOR_PHILIPS, 0x0815) },    /* Philips eHome Infrared Transciever */
    { USB_DEVICE(VENDOR_SMK, 0x031d) },    /* SMK/Toshiba G83C0004D410 */
    { USB_DEVICE(VENDOR_TATUNG, 0x9150) },  /* Tatung eHome Infrared Transceiver */
    { USB_DEVICE(VENDOR_SHUTTLE, 0xc001) },  /* Shuttle eHome Infrared Transceiver */
        { USB_DEVICE(VENDOR_GATEWAY, 0x3009) },  /* Gateway eHome Infrared Transceiver */
        { USB_DEVICE(VENDOR_MITSUMI, 0x2501) },  /* Mitsumi */
    { USB_DEVICE(VENDOR_TOPSEED, 0x0001) },  /* Topseed eHome Infrared Transceiver */ 
    { USB_DEVICE(VENDOR_RICAVISION, 0x0010) }, /* Ricavision internal Infrared Transceiver */
    { USB_DEVICE(VENDOR_ITRON, 0x7002) },   /* Itron ione Libra Q-11 */
    { USB_DEVICE(VENDOR_FIC, 0x9242) },     /* FIC eHome Infrared Transceiver */
    { }                    /* Terminating entry */
};
```So i added:
```
#define VENDOR_MICROSOFT    0x045e
```And
```
    { USB_DEVICE(VENDOR_MICROSOFT, 0x00a0) },
```(Got the codes from "lsusb" or also "cat /proc/bus/usb/devices" ->Vendor & ProdId)

Rebuilt the driver, modprobe lirc_mceusb2, restarted lircd, and now irw works! :)
Also, now  "cat /proc/bus/usb/devices" shows:
```
...
I:  If#= 0 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=lirc_mceusb2
...
```I don't know if a newer version of lirc (if any?) or the one in superm1's repository would have this little modification already done. I have used lirc v0.8.1 from the lirc web site.

When i think of all the time i spent for something that just couldn't work for such a simple reason.. :-({|= 

Now, to get the IR blaster working... :)
Okay, looks like you found a new remote that works with the driver!

What you need to do is submit this patch upstream to lirc and they will get it added to CVS.  Next time I rebuild packages, i'll add your remote to them locally.  I don't know that this can make it in time for feisty though.

---

### Post by deb123 on 2007-03-31
Newbie question: How or to whom should i submit the patch?
Should I send the full C file or should i use a program like diff to extract the difference?

---

### Post by deb123 on 2007-04-03
Well the codes for this remote are now in the lastest revision of the driver :)
[http://lirc.cvs.sourceforge.net/lirc/lirc/drivers/lirc_mceusb2/](http://lirc.cvs.sourceforge.net/lirc/lirc/drivers/lirc_mceusb2/)

---

### Post by superm1 on 2007-04-03
Wonderful :)
The feisty package won't have this directly fixed, but feisty+1 will, and I'll eventually do my own patched version for it as well.

---

### Post by Lymen on 2007-04-05
I have the same remote and have been having similar problems.  Where do I find the source file for the driver mceusb2?
thanks!

---

### Post by deb123 on 2007-04-06
This is the lirc package that i used:
[http://prdownloads.sourceforge.net/lirc/lirc-0.8.1.tar.bz2](http://prdownloads.sourceforge.net/lirc/lirc-0.8.1.tar.bz2)

Extract the archive in /usr/src
and if you have the same remote as i do, copy the file included in the attached archive over:
/usr/src/lirc-0.8.1/drivers/lirc_mceusb2/lirc_mceusb2.c

To make sure you have the same remote, when you type "lsusb", you should get an entry with these exact codes:
ID 045e:00a0 Microsoft Corp. 

Now, you should rebuild the driver, modprobe lirc_mceusb2, and irw should work.

---

### Post by ntetreau on 2007-04-30
Hi all, thanks for the thread.  My remote worked out of the box finally following the Ubuntu wiki link you provided on the first page.  I am now trying to figure out if my usb black box that came with the used pvr-150 i bought is also an ir blaster.  Anyway to tell?  From the wiki and the web, I figured I needed to do something like this to make it work:

sudo apt-get install setserial

create /etc/modprobe.conf

added:
alias char-major-61-0 lirc_mceusb2
options lirc_mceusb2 debug=0
alias char-major-61-1 lirc_serial
options lirc_serial irq=3 io=0x2f8
install lirc_serial /bin/setserial /dev/ttyS1 uart none;\
         /sbin/modprobe --ignore-install lirc_serial
add above lirc_dev lirc_mceusb2

Also copied my PACE NTL remote conf file into /etc/lircd.conf

When I issue some command like this nothing happens, but to error message:

irsend SEND_ONCE blaster 1

No red light or anything, syslog gets 2 lines one for accepting a new client on one for removing it.  

So it looks good, but I don't get anything on my box and no feedback from the device.  Anything got this to work?

---

### Post by superm1 on 2007-04-30
If it has a tranmitter, there is a little LED at the end of a cable to plug in.  Plug it in, and support is there already with the mceusb2 driver for transmitting.

---

### Post by ntetreau on 2007-04-30
Thanks for your email, mine looks like the big box in the picture attached, except it's all black.  I seem to be missing the smaller thingy with a wire.  I wouldn't know where to plug that since the other bigger box is a usb device.

---

### Post by superm1 on 2007-04-30
> **ntetreau said:**
> Thanks for your email, mine looks like the big box in the picture attached, except it's all black.  I seem to be missing the smaller thingy with a wire.  I wouldn't know where to plug that since the other bigger box is a usb device.
The USB device has two jacks that look like headphones on the back.  That is where you plug in the IR blaster.  If you don't have the IR blaster though, you can't use it for sending IR signals!

---

### Post by ntetreau on 2007-05-01
Thanks superm1, didn't want to hijack the thread.  Anyway,  I'm missing it but Hauppauge will ship me one shortly, I'll probably be back on the thread at that time, thanks again.

Nic

---

### Post by Ninto on 2007-05-27
I'm having a similar problem as this, except with a different receiver.

I have the Ricavision eHome Infrared Transceiver which shows as:

```
T:  Bus=01 Lev=01 Prnt=01 Port=02 Cnt=02 Dev#=  3 Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=16 #Cfgs=  1
P:  Vendor=0768 ProdID=0023 Rev= 0.00
S:  Manufacturer=Ricavision
S:  Product=eHome Infrared Transceiver
S:  SerialNumber=RH00001E
C:* #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
E:  Ad=01(O) Atr=02(Bulk) MxPS=  16 Ivl=0ms
E:  Ad=81(I) Atr=02(Bulk) MxPS=  16 Ivl=0ms

```

The default lirc_mceusb2.c file has a different Ricavision transceiver showing, with a different vendor and product ID, so I changed the entry to reflect what shows up in cat /proc/bus/usb/devices as per above, then: 

cd /usr/src/lirc-0.8.2pre2/
./config
make
make install
modprobe lirc_mceusb2
/etc/init.d/lircd restart
irw

Then irw seems to close immediately, and lircd stops.  /var/log/messages shows:

May 27 15:47:25 localhost lircd-0.8.2-CVS[3354]: lircd(userspace) ready
May 27 15:47:29 localhost lircd-0.8.2-CVS[3354]: accepted new client on /dev/lircd
May 27 15:47:29 localhost lircd-0.8.2-CVS[3354]: could not get file information for /dev/lirc
May 27 15:47:29 localhost lircd-0.8.2-CVS[3354]: default_init(): No such file or directory 
May 27 15:47:29 localhost lircd-0.8.2-CVS[3354]: caught signal

/dev/lirc does exist.

cat /proc/bus/usb/devices shows the same problem as above, Driver=(none)

Thoughts?  I'm going insane with this, I've tried so many things so far, and nothing seems to work.

---

### Post by trieb on 2007-09-03
I am having the exact problem that you have described above, though the remote I am using is a different version of the RC6, which looks identical. 

T:  Bus=02 Lev=01 Prnt=01 Port=01 Cnt=01 Dev#=  4 Spd=12  MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=0609 ProdID=0334 Rev= 1.00
S:  Manufacturer=SMK CORPORATION
S:  Product=MCE TRANCEIVR Emulator Device 2006
S:  SerialNumber=PA070417173846G
C:* #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
E:  Ad=01(O) Atr=03(Int.) MxPS=  32 Ivl=2ms
E:  Ad=81(I) Atr=03(Int.) MxPS=  32 Ivl=2ms

I followed the same sequence of steps in updating the lirc_mceusb2.c file, though I had no success.  Any sugguestions?

---

### Post by trieb on 2007-09-03
After uninstalling the packages and a reboot, I was able to follow the steps you mentioned to get the  remote to work!!  Thanks for posting the solution.

---

### Post by jadedjay on 2007-11-11
> **Ninto said:**
> I'm having a similar problem as this, except with a different receiver.

I have the Ricavision eHome Infrared Transceiver which shows as:

```
T:  Bus=01 Lev=01 Prnt=01 Port=02 Cnt=02 Dev#=  3 Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=16 #Cfgs=  1
P:  Vendor=0768 ProdID=0023 Rev= 0.00
S:  Manufacturer=Ricavision
S:  Product=eHome Infrared Transceiver
S:  SerialNumber=RH00001E
C:* #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
E:  Ad=01(O) Atr=02(Bulk) MxPS=  16 Ivl=0ms
E:  Ad=81(I) Atr=02(Bulk) MxPS=  16 Ivl=0ms

```

The default lirc_mceusb2.c file has a different Ricavision transceiver showing, with a different vendor and product ID, so I changed the entry to reflect what shows up in cat /proc/bus/usb/devices as per above, then: 

cd /usr/src/lirc-0.8.2pre2/
./config
make
make install
modprobe lirc_mceusb2
/etc/init.d/lircd restart
irw

Then irw seems to close immediately, and lircd stops.  /var/log/messages shows:

May 27 15:47:25 localhost lircd-0.8.2-CVS[3354]: lircd(userspace) ready
May 27 15:47:29 localhost lircd-0.8.2-CVS[3354]: accepted new client on /dev/lircd
May 27 15:47:29 localhost lircd-0.8.2-CVS[3354]: could not get file information for /dev/lirc
May 27 15:47:29 localhost lircd-0.8.2-CVS[3354]: default_init(): No such file or directory 
May 27 15:47:29 localhost lircd-0.8.2-CVS[3354]: caught signal

/dev/lirc does exist.

cat /proc/bus/usb/devices shows the same problem as above, Driver=(none)

Thoughts?  I'm going insane with this, I've tried so many things so far, and nothing seems to work.

Did you resolve this problem?

I have a similar problem with another Remote thats sold as a MCE remote.  Followed the same steps as yourself, but yet still Driver=(none).  
Does anybody know how to get an output from the lirc_mceusb2 module so I can see what is happening?

---

### Post by amorgen on 2007-11-11
Hello all,
I am having the same problem. I succeded editing the lirc_mceusb2.c adding :
```
#define VENDOR_PINNACLE         0x2304
```
and
```
{ USB_DEVICE(VENDOR_PINNACLE, 0x0225) }, /* Pinnacle Systems, Inc. PCTV Remote USB RC6 */
```
Then irrecord helped me to change the conf.
Regards

---

### Post by jadedjay on 2007-12-01
I have another RC6 remote and I added the Vendor ID (147a)and Device ID (e017) to lirc_mceusb2  and rebuilt the module and used rmmod and modprobe to update lirc_mceusb2 on my system.

The receiver is found.  /dev/lirc0 is created.  handware.conf is configured as shown earlier in this thread.

But when I run irw,  I can press one button before the receiver locks up.

Can anybody give me some suggestions of what I should try next?

---

### Post by spp58ca on 2007-12-07
I have the Pinnacle MCE that Amorgen was able to get working but I can't get mine to work.

I've made the changes, rebuilt and loaded the driver.

irw doesn't produce any output.

irrecord prints ...s on screen when I press buttons then fails with "cannot find gaps".

mode2 produces output such as:
space 26150
pulse 500
space 350
pulse 550
space 800
pulse 500
space 850

lsusb sees the device
Bus 002 Device 003: ID 2304:0225 Pinnacle Systems, Inc. [hex] 

Any suggestions as to what to do next?

---

### Post by libhack on 2007-12-09
I too have been working the Pinnacle Remote and came across this thread because of similar problems described above by spp58ca - in fact his description is exactly what I was seeing.

I believe I have found the solution - an additional patch is needed to the lirc_mceusb2.c file - in addition to adding the vendor/product IDs for Pinnacle as per amorgen.

a
                 case 0x90:

line needs to be added just above the case 0x8F: line

with this change everything from then on seemed to work - immediately irw gives the output of the actual keys being pressed (using the well-defined mceusb lirc.conf file)
- irrecord does not fail with cannot find gaps

seems as though the Pinnacle allows for a full 16 byte message from the device

hope this is of use

for those interested I came across by setting the debug flag in the driver to 1 and looking at the system log files - where records beginning with 90 were seen

---

### Post by libhack on 2007-12-19
and finally heres a patch which actually gets the transmitter to work for the Pinnacle MCE Remote

---

### Post by superm1 on 2007-12-19
If you can, please submit this patch upstream and file a bug in ubuntu against lirc.  In the event that there is no new upstream release, we'll have it added on.  If there is a new upstream release, we will be able to drop it.

---

### Post by spp58ca on 2008-01-01
> **libhack said:**
> and finally heres a patch which actually gets the transmitter to work for the Pinnacle MCE Remote

Thanks. For us novices is there a how to that describes how to compile and install this. I was able to get the source and the patch program using the synaptic package manager and was able to do the patch. It's just not clear what needs to be done next.

---

### Post by plopplop on 2008-01-07
> **libhack said:**
> and finally heres a patch which actually gets the transmitter to work for the Pinnacle MCE Remote

I am having exactly the same problems as described in this thread with my Pinnacle PCTV Tuner card. After all the pain for setting up the card itself, I now would like the remote to work. But... well... let's say it's taking a while....

I have the Pinnacle MCE remote, or at least I think I have.

I tried you patch against version 0.8.2 and against the latest version from CVS. However, the patching exited with errors:
```
sudo patch lirc_mceusb2.c lirc_mceusb2.c.patch
patching file lirc_mceusb2.c
Hunk #1 FAILED at 122.
Hunk #2 FAILED at 143.
Hunk #3 succeeded at 218 (offset 35 lines).
Hunk #4 FAILED at 450.
Hunk #5 FAILED at 631.
Hunk #6 FAILED at 803.
Hunk #7 FAILED at 816.
Hunk #8 FAILED at 926.
7 out of 8 hunks FAILED -- saving rejects to file lirc_mceusb2.c.rej
```

So I decided to make the changes in the lirc_mceusb2.c file myself. I attached my file at this message. Then I compiled and run the installation on Ubuntu 7.10 according to the steps described at [http://www.mythtv.org/wiki/index.php/MCE_Remote#Installation_guides](http://www.mythtv.org/wiki/index.php/MCE_Remote#Installation_guides)

However, the problem still occurs. For instance:
```
ls -l /dev/lir*
crw-r--r-- 1 root root 61, 0 2008-01-07 23:52 /dev/lirc
srw-rw-rw- 1 root root     0 2008-01-07 23:56 /dev/lircd
prw-r--r-- 1 root root     0 2008-01-07 23:52 /dev/lircm
```

And running irw exits immediately, the well known story...

Any idea what I did wrong?

---

### Post by murrayc on 2008-02-01
Did this patch ever get upstream to lirc? Was any Ubuntu launchpad bug ever submitted?

---

### Post by terryva on 2008-03-07
I went in and did the same edits but could not build lirc :(

Can you tell me how to build it?

Cheers,

Terry

---

### Post by the_crowbar on 2008-03-13
I was able to get my remote working with these instructions.  I actually use an older MCE remote with the Pinnacle receiver. The remote included with the Pinnacle receiver also works. Here is what I did:

Step 1) Verify the receiver you now have. Run "lsusb" and look for a line like this:
```

Bus 002 Device 002: ID 2304:0225 Pinnacle Systems, Inc. [hex]

```
Important part is 2304:0225
The ID needs to be 2304:0225. Other receivers may work, but I don't know about them.

Step 2) Down load lirc. Go to the [www.lirc.org](www.lirc.org) website and download a CVS snapshot. (As of 03-13-2008 0.8.3pre1 is the newest.)

Step 3) Extract the snapshot (tar -jxvf lirc-0.8.3pre1.tar.bz2) This should create a new directory called lirc-0.8.3pre1.

Step 4) Patch the file with the new info. I used vi from the command line, but any text editor will work. i.e. gedit, kate, etc. Here is exactly what I did:
Change to directory and patch file. cd lirc-0.8.3pre1/drivers/lirc_mceusb2. Run 'ls' and make sure the lirc_mceusb2.c file is in the current directory.  Run 'vi lirc_mceusb2.c'. Search for a line that says vendor section. It will look like this:
```

#define VENDOR_MITSUMI          0x03ee
#define VENDOR_TOPSEED          0x1784
#define VENDOR_RICAVISION       0x179d
#define VENDOR_ITRON            0x195d
#define VENDOR_FIC              0x1509
#define VENDOR_LG               0x043e
#define VENDOR_MICROSOFT        0x045e
#define VENDOR_FORMOSA          0x147a
#define VENDOR_FINTEK           0x1934
#define VENDOR_PINNACLE         0x2304

```

The last line is the new one I added.
The next section of the file looks like this:
```

        /* Microsoft MCE Infrared Transceiver */
        { USB_DEVICE(VENDOR_MICROSOFT, 0x00a0) },
        /* Formosa eHome Infrared Transceiver */
        { USB_DEVICE(VENDOR_FORMOSA, 0xe015) },
        /* Fintek eHome Infrared Transceiver */
        { USB_DEVICE(VENDOR_FINTEK, 0x1934) },
        /* Pinnacle Windows Vista Transceiver */
        { USB_DEVICE(VENDOR_PINNACLE, 0x0225) },
        /* Terminating entry */
        { }

```
I added the two lines with the word Pinnacle in them.

Search through the file for this section:
```

                       switch (ir->buf_in[i]) {
                        /* data headers */
                        case 0x90:
                        case 0x8F:
                        case 0x8E:
                        case 0x8D:
                        case 0x8C:
                        case 0x8B:
                        case 0x8A:
                        case 0x89:
                        case 0x88:
                        case 0x87:

```
I added the "case 0x90" line.

Save and exit. In vi use ":wq".

Step 5) Recompile lirc. I had to add build-essential and linux-headers-2.6.22-14-generic.
"sudo apt-get install build-essential linux-headers-2.6.22-14-generic" I am on amd64 so i386 may be different. Once you have the needed packages run ./configure from the lirc-0.8.3pre1 directory. For option 1 choose USB Devices->Windows Media Center Remote new version (older version). Then "save and run configure"

Step 6) Once configure finishes it will say to run make and make install. Run make with "make". Once that finishes run make install. "sudo make install" This will install the new kernel modules and the new lirc daemon under /usr/local/bin/

Step 7) You can reboot or just stop Lirc, remove the kernel modules, and start lirc back up.
sudo /etc/init.d/lirc stop
sudo rmmod lirc_mceusb2
sudo rmmod lirc_dev
sudo /etc/init.d/lirc start

I was able to use the lirc included with 7.10 rather than the newly compiled 8.3pre1 version. So far (1 hour) things are working well.

Cheers,
the_crowbar

---

### Post by ebrusky on 2008-04-26
I'd like to thank the_crowbar, I followed your guide and the changes worked perfectly(After resolving the small problem I list below.) I just picked up this remote off WOOT on a whim, and I'm glad I was able to get it working. 

The only problem I encountered was with the Mythbuntu load that I'm using. Mythbuntu doesn't have the lirc_mceusb2.ko file in the right directory. A friend discoverd this when we removed the driver I had made and then attempted to reload the module and it still loaded. We then searched around for the driver that Mythbuntu was actually loading and replaced it with the driver file I had made, and the remote worked right away.

Mythbuntu seems to look at the lirc_mceusb2.ko file in the "/lib/modules/2.6.22-14-generic/ubuntu/media/lirc/lirc_mceusb2" directory. So we just copied the new driver file from "/lib/modules/2.6.22-14-generic/misc" to the other directory and it worked right away.

Hope this helps any Mythbuntu users out there.:KS :KS

---

### Post by mihatz on 2008-06-06
Implementation of lirc modules seems to be somewhat different in 8.04 Hardy Heron, if you install them with apt-get from the repos. Module sources are installed trough dkms framework (Dynamic Kernel Module Support) so that they can be recompiled dynamically every time you upgrade your kernel. Sure does sound smart, but requires slightly different approach.

Here's how I did it:

There is updated source for mceusb2 from lirc that includes the patch described in this thread, so there is no need for manually editing the source file, just c&p.

Download lirc-modules-source package

wget [http://mirrors.kernel.org/ubuntu/pool/universe/l/lirc/lirc-modules-source_0.8.3~pre1-0ubuntu7_all.deb](http://mirrors.kernel.org/ubuntu/pool/universe/l/lirc/lirc-modules-source_0.8.3~pre1-0ubuntu7_all.deb)

Download latest mceusb2 source from [here]("http://lirc.cvs.sourceforge.net/lirc/lirc/drivers/lirc_mceusb2/")
(The following one is the latest as I write this, check the above link for the updates.)
wget [http://lirc.cvs.sourceforge.net/*checkout*/lirc/lirc/drivers/lirc_mceusb2/lirc_mceusb2.c?revision=1.45](http://lirc.cvs.sourceforge.net/*checkout*/lirc/lirc/drivers/lirc_mceusb2/lirc_mceusb2.c?revision=1.45)

Now you need to rebuild lirc-modules-source package:

First, unpack it to rebuild/ directory that we will temporarily use for rebuilding:
 dpkg -x lirc-modules-source_0.8.3~pre1-0ubuntu7_all.deb rebuild/

then extract control file:
dpkg -e lirc-modules-source_0.8.3~pre1-0ubuntu7_all.deb rebuild/DEBIAN/

after that copy the new mceusb2 source over unpacked one:
cp lirc_mceusb2.c\?revision\=1.45 rebuild/usr/src/lirc-0.8.3~pre1/drivers/lirc_mceusb2/lirc_mceusb2.c
(wget seems to download file with modified name hence the ..\?revision\.. if you do it with your browser, the name will be the same, anyway it doesn't matter.)

Make a backup of original package:
mv lirc-modules-source_0.8.3~pre1-0ubuntu7_all.deb lirc-modules-source_0.8.3~pre1-0ubuntu7_all.deb.original

build new package with modified source:
dpkg -b rebuild/ lirc-modules-source_0.8.3~pre1-0ubuntu7_all.deb
At this point dpkg will complain about some user-defined field and so on, but this is not a problem.

And finally, install the package you have just modified:
dpkg -i lirc-modules-source_0.8.3~pre1-0ubuntu7_all.deb

After this, you still need to install lirc, this is just a guide for installing most recent mceusb2 module.

Hope someone will find this useful until package in the repos is updated.

---

