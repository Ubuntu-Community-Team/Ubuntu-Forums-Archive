---
title: "Sony Vaio + JVC miniDV + Kino = Problems.  Help please?"
date: 2007-03-20
forum: Multimedia &amp; Video
---

### Post by SendDerek on 2007-03-20
**This issue was resolved thanks to a new kernel update in feisty!  Thanks to everybody for your help!**

Hello!

I have been trying to get my combination of hardware to work tonight and I just haven't been having any luck so I thought I would call upon the powers of the gurus to get me outta this mess! :)

Basically, I have a JVC GR-290U DV Camcorder and a Sony Vaio FE550G laptop.  I would like to use Kino since I hear all kinds of great things about it, but I haven't gotten very far yet.  I have the camcorder hooked up via firewire to my port on my laptop.

When I first started my journey, I just simply tried to see what would happen.  I turn on my camcorder and opened up Kino and nothing happened.  I goto preferences and I get the message: 
> 
ieee 1394 subsystem is not responding


So, I start doing some searching on google and find a little tutorial [here]("http://www.bxlug.be/en/articles/220").  I got the same message after that as well.

I find yet another tutorial [here]("http://ubuntuforums.org/showthread.php?t=56468&highlight=raw1394") and I still got the same message.  After following the instruction to install and run gscanbus I find that there is a little penguin pictured (that's good, right?) but when I turned on my camcorder, I get the error message "Error while reading from IEEE1394: : Resource temporarily unavailable" scrolling down the terminal.  The program became very unresponsive and I closed it out via terminal.  

I found yet another article [here]("http://www.ubuntuforums.org/showthread.php?t=261752") and it informs me to execute these commands:
> 
sudo modprobe raw1394
sudo chmod a+rw /dev/*1394

Now, when I open up Kino, I don't get the error message reported in the preferences, but I do get this error message showing up in the bottom information bar:
> 
WARNING: raw1394 kernal module not loaded or failure to read / write /dev/raw1394!


So, now I feel that I've gotten further and that I'm close.  Here is the story in summary form:

I have followed these guides so far (listed in order):

[http://www.bxlug.be/en/articles/220](http://www.bxlug.be/en/articles/220)
[http://ubuntuforums.org/showthread.php?t=56468](http://ubuntuforums.org/showthread.php?t=56468)
[http://www.ubuntuforums.org/showthread.php?t=261752](http://www.ubuntuforums.org/showthread.php?t=261752)

Kino Preferences Settings:
AV/C Device:  {NO OPTION AVAILABLE}
dv1394 Device: /dev/dv1394/0


***************
*  OUTPUTS   *
***************

// lsmod | grep 1394 output:
> 
hildretd@vaio:~$ lsmod | grep 1394
video1394              20184  0 
raw1394                30584  0 
ohci1394               37040  1 video1394
ieee1394              306104  4 video1394,raw1394,sbp2,ohci1394


//testlibraw:
> 
command not found


//ls /dev
```

acpi       ptybf  ptyq4  ptyu9  ptyye     tty20  ttyb2  ttyp7  ttyt8  ttyxd
agpgart    ptyc0  ptyq5  ptyua  ptyyf     tty21  ttyb3  ttyp8  ttyt9  ttyxe
audio      ptyc1  ptyq6  ptyub  ptyz0     tty22  ttyb4  ttyp9  ttyta  ttyxf
bus        ptyc2  ptyq7  ptyuc  ptyz1     tty23  ttyb5  ttypa  ttytb  ttyy0
cdrom      ptyc3  ptyq8  ptyud  ptyz2     tty24  ttyb6  ttypb  ttytc  ttyy1
cdrw       ptyc4  ptyq9  ptyue  ptyz3     tty25  ttyb7  ttypc  ttytd  ttyy2
console    ptyc5  ptyqa  ptyuf  ptyz4     tty26  ttyb8  ttypd  ttyte  ttyy3
core       ptyc6  ptyqb  ptyv0  ptyz5     tty27  ttyb9  ttype  ttytf  ttyy4
disk       ptyc7  ptyqc  ptyv1  ptyz6     tty28  ttyba  ttypf  ttyu0  ttyy5
dri        ptyc8  ptyqd  ptyv2  ptyz7     tty29  ttybb  ttyq0  ttyu1  ttyy6
dsp        ptyc9  ptyqe  ptyv3  ptyz8     tty3   ttybc  ttyq1  ttyu2  ttyy7
dvd        ptyca  ptyqf  ptyv4  ptyz9     tty30  ttybd  ttyq2  ttyu3  ttyy8
dvdrw      ptycb  ptyr0  ptyv5  ptyza     tty31  ttybe  ttyq3  ttyu4  ttyy9
fb0        ptycc  ptyr1  ptyv6  ptyzb     tty32  ttybf  ttyq4  ttyu5  ttyya
fd         ptycd  ptyr2  ptyv7  ptyzc     tty33  ttyc0  ttyq5  ttyu6  ttyyb
full       ptyce  ptyr3  ptyv8  ptyzd     tty34  ttyc1  ttyq6  ttyu7  ttyyc
fuse       ptycf  ptyr4  ptyv9  ptyze     tty35  ttyc2  ttyq7  ttyu8  ttyyd
hda        ptyd0  ptyr5  ptyva  ptyzf     tty36  ttyc3  ttyq8  ttyu9  ttyye
hpet       ptyd1  ptyr6  ptyvb  ram0      tty37  ttyc4  ttyq9  ttyua  ttyyf
initctl    ptyd2  ptyr7  ptyvc  ram1      tty38  ttyc5  ttyqa  ttyub  ttyz0
input      ptyd3  ptyr8  ptyvd  ram10     tty39  ttyc6  ttyqb  ttyuc  ttyz1
kmem       ptyd4  ptyr9  ptyve  ram11     tty4   ttyc7  ttyqc  ttyud  ttyz2
kmsg       ptyd5  ptyra  ptyvf  ram12     tty40  ttyc8  ttyqd  ttyue  ttyz3
kqemu      ptyd6  ptyrb  ptyw0  ram13     tty41  ttyc9  ttyqe  ttyuf  ttyz4
log        ptyd7  ptyrc  ptyw1  ram14     tty42  ttyca  ttyqf  ttyv0  ttyz5
loop0      ptyd8  ptyrd  ptyw2  ram15     tty43  ttycb  ttyr0  ttyv1  ttyz6
MAKEDEV    ptyd9  ptyre  ptyw3  ram2      tty44  ttycc  ttyr1  ttyv2  ttyz7
mem        ptyda  ptyrf  ptyw4  ram3      tty45  ttycd  ttyr2  ttyv3  ttyz8
mixer      ptydb  ptys0  ptyw5  ram4      tty46  ttyce  ttyr3  ttyv4  ttyz9
net        ptydc  ptys1  ptyw6  ram5      tty47  ttycf  ttyr4  ttyv5  ttyza
null       ptydd  ptys2  ptyw7  ram6      tty48  ttyd0  ttyr5  ttyv6  ttyzb
nvidia0    ptyde  ptys3  ptyw8  ram7      tty49  ttyd1  ttyr6  ttyv7  ttyzc
nvidiactl  ptydf  ptys4  ptyw9  ram8      tty5   ttyd2  ttyr7  ttyv8  ttyzd
port       ptye0  ptys5  ptywa  ram9      tty50  ttyd3  ttyr8  ttyv9  ttyze
ppp        ptye1  ptys6  ptywb  random    tty51  ttyd4  ttyr9  ttyva  ttyzf
psaux      ptye2  ptys7  ptywc  raw1394   tty52  ttyd5  ttyra  ttyvb  urandom
ptmx       ptye3  ptys8  ptywd  rtc       tty53  ttyd6  ttyrb  ttyvc  vcs
pts        ptye4  ptys9  ptywe  sda       tty54  ttyd7  ttyrc  ttyvd  vcs1
ptya0      ptye5  ptysa  ptywf  sda1      tty55  ttyd8  ttyrd  ttyve  vcs2
ptya1      ptye6  ptysb  ptyx0  sda2      tty56  ttyd9  ttyre  ttyvf  vcs3
ptya2      ptye7  ptysc  ptyx1  sda5      tty57  ttyda  ttyrf  ttyw0  vcs4
ptya3      ptye8  ptysd  ptyx2  sda6      tty58  ttydb  ttys0  ttyw1  vcs5
ptya4      ptye9  ptyse  ptyx3  sda7      tty59  ttydc  ttyS0  ttyw2  vcs6
ptya5      ptyea  ptysf  ptyx4  sdb       tty6   ttydd  ttys1  ttyw3  vcs7
ptya6      ptyeb  ptyt0  ptyx5  sdb1      tty60  ttyde  ttyS1  ttyw4  vcs8
ptya7      ptyec  ptyt1  ptyx6  sg0       tty61  ttydf  ttys2  ttyw5  vcsa
ptya8      ptyed  ptyt2  ptyx7  sg1       tty62  ttye0  ttyS2  ttyw6  vcsa1
ptya9      ptyee  ptyt3  ptyx8  shm       tty63  ttye1  ttys3  ttyw7  vcsa2
ptyaa      ptyef  ptyt4  ptyx9  snapshot  tty7   ttye2  ttyS3  ttyw8  vcsa3
ptyab      ptyp0  ptyt5  ptyxa  snd       tty8   ttye3  ttys4  ttyw9  vcsa4
ptyac      ptyp1  ptyt6  ptyxb  sndstat   tty9   ttye4  ttys5  ttywa  vcsa5
ptyad      ptyp2  ptyt7  ptyxc  sonypi    ttya0  ttye5  ttys6  ttywb  vcsa6
ptyae      ptyp3  ptyt8  ptyxd  stderr    ttya1  ttye6  ttys7  ttywc  vcsa7
ptyaf      ptyp4  ptyt9  ptyxe  stdin     ttya2  ttye7  ttys8  ttywd  vcsa8
ptyb0      ptyp5  ptyta  ptyxf  stdout    ttya3  ttye8  ttys9  ttywe  video
ptyb1      ptyp6  ptytb  ptyy0  tty       ttya4  ttye9  ttysa  ttywf  video1394
ptyb2      ptyp7  ptytc  ptyy1  tty0      ttya5  ttyea  ttysb  ttyx0  vmmon
ptyb3      ptyp8  ptytd  ptyy2  tty1      ttya6  ttyeb  ttysc  ttyx1  vmnet0
ptyb4      ptyp9  ptyte  ptyy3  tty10     ttya7  ttyec  ttysd  ttyx2  vmnet1
ptyb5      ptypa  ptytf  ptyy4  tty11     ttya8  ttyed  ttyse  ttyx3  vmnet8
ptyb6      ptypb  ptyu0  ptyy5  tty12     ttya9  ttyee  ttysf  ttyx4  xconsole
ptyb7      ptypc  ptyu1  ptyy6  tty13     ttyaa  ttyef  ttyt0  ttyx5  zero
ptyb8      ptypd  ptyu2  ptyy7  tty14     ttyab  ttyp0  ttyt1  ttyx6
ptyb9      ptype  ptyu3  ptyy8  tty15     ttyac  ttyp1  ttyt2  ttyx7
ptyba      ptypf  ptyu4  ptyy9  tty16     ttyad  ttyp2  ttyt3  ttyx8
ptybb      ptyq0  ptyu5  ptyya  tty17     ttyae  ttyp3  ttyt4  ttyx9
ptybc      ptyq1  ptyu6  ptyyb  tty18     ttyaf  ttyp4  ttyt5  ttyxa
ptybd      ptyq2  ptyu7  ptyyc  tty19     ttyb0  ttyp5  ttyt6  ttyxb
ptybe      ptyq3  ptyu8  ptyyd  tty2      ttyb1  ttyp6  ttyt7  ttyxc

```

// dmesg | grep 1394
```

[17179577.624000] ieee1394: Initialized config rom entry `ip1394'
[17179578.092000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[177]  MMIO=[d0006000-d00067ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[17179579.372000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0800460301f93164]
[17179592.840000] ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1)
[17179592.840000] ieee1394: sbp2: Try serialize_io=0 for better performance
[17179592.972000] ieee1394: raw1394: /dev/raw1394 device initialized
[17179592.996000] video1394: Installed video1394 module

```

// dmesg | tail -n 40
```

[17179608.668000] bridge-eth0: attached
[17179608.696000] /dev/vmnet: open called by PID 4865 (vmnet-netifup)
[17179608.696000] /dev/vmnet: hub 1 does not exist, allocating memory.
[17179608.696000] /dev/vmnet: port on hub 1 successfully opened
[17179608.700000] /dev/vmnet: open called by PID 4866 (vmnet-netifup)
[17179608.700000] /dev/vmnet: hub 8 does not exist, allocating memory.
[17179608.700000] /dev/vmnet: port on hub 8 successfully opened
[17179608.704000] /dev/vmnet: open called by PID 4864 (vmnet-natd)
[17179608.704000] /dev/vmnet: port on hub 8 successfully opened
[17179608.800000] bridge-eth0: enabling the bridge
[17179608.800000] bridge-eth0: up
[17179608.904000] /dev/vmnet: open called by PID 4888 (vmnet-dhcpd)
[17179608.904000] /dev/vmnet: port on hub 8 successfully opened
[17179609.012000] /dev/vmnet: open called by PID 4899 (vmnet-dhcpd)
[17179609.012000] /dev/vmnet: port on hub 1 successfully opened
[17179609.500000] Bluetooth: Core ver 2.8
[17179609.500000] NET: Registered protocol family 31
[17179609.500000] Bluetooth: HCI device and connection manager initialized
[17179609.500000] Bluetooth: HCI socket layer initialized
[17179609.532000] Bluetooth: L2CAP ver 2.8
[17179609.532000] Bluetooth: L2CAP socket layer initialized
[17179609.536000] Bluetooth: RFCOMM socket layer initialized
[17179609.536000] Bluetooth: RFCOMM TTY layer initialized
[17179609.536000] Bluetooth: RFCOMM ver 1.7
[17179621.296000] NET: Registered protocol family 10
[17179621.296000] lo: Disabled Privacy Extensions
[17179621.296000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[17179621.296000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[17179621.296000] IPv6 over IPv4 tunneling driver
[17179625.236000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[17179631.476000] vmnet1: no IPv6 routers present
[17179631.964000] vmnet8: no IPv6 routers present
[17179634.700000] NET: Registered protocol family 17
[17179634.720000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[17179645.592000] eth1: no IPv6 routers present
[17179657.960000] eth1: no IPv6 routers present
[17181215.584000] psmouse.c: GlidePoint at isa0060/serio4/input0 lost synchronization, throwing 1 bytes away.
[17181216.092000] psmouse.c: resync failed, issuing reconnect request
[17181216.768000] input: PS/2 Mouse as /class/input/input6
[17181216.780000] input: AlpsPS/2 ALPS GlidePoint as /class/input/input7

```


Sorry so lengthy... I just want to be as detailed as possible and try to help you help me!

Thanks for your help in advance!

-Derek

---

### Post by SendDerek on 2007-03-20
When I try dvgrab, I get the following message:
> 
Error: no camera exists


My camera is turned on and the connection is good.

---

### Post by SendDerek on 2007-03-20
So, I figured I would try and restart the computer just to see what happens.  Well, as you can imagine, I'm still posting here and the problem hasn't made any more progress.  Does anybody have any ideas of what might be happening?

---

### Post by SendDerek on 2007-03-23
Maybe this helps a little more?

etc/fstab:
```

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda6 :
UUID=038d7087-a15a-4c61-9161-31acde4e0d47 / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/sda7 :
UUID=bca325a3-52fb-46b8-9b60-abf81c447d37 /home ext3 defaults 0 2
# Entry for /dev/sda1 :
UUID=4894444594443828 /media/windows ntfs-3g defaults,locale=en_US.UTF-8 0 1
# Entry for /dev/sda5 :
UUID=bfba4fb7-6698-498d-bdff-125005538ce4 none swap sw 0 0
/dev/hda /media/cdrom0 udf,iso9660 user,noauto 0 0

```

---

### Post by SendDerek on 2007-03-23
Okay, so I went to kinodv.org and found a tutorial on installing Kino in Ubuntu here [(clicky here)]("http://www.kinodv.org/article/view/155/1/13/").

I typed this command:
> 
$ sudo gedit /etc/udev/rules.d/40-permissions.rules


And then I edited the permissions like they should be (changed 'GROUP="disk"' to 'GROUP="video"').  I am still getting the same error message as before.

Any ideas?

---

### Post by SendDerek on 2007-03-23
Okay... so I think I've made some more progress.  Basically, I followed the tutorial in the my last post to install kino 1.0.  Since I have installed this, the error message has gone away, and now it seems like the program is just waiting for me DV Camcorder to turn on and start playing.  I click on "capture" and then I press play on my camcorder, but nothing happens.  It's almost like my camera isn't actually recognized in the first place.

Any ideas?

I have also found this guide here on the same subject, but I don't know if it's the same problem that I have:
[http://ubuntuforums.org/showthread.php?t=2792](http://ubuntuforums.org/showthread.php?t=2792)

---

### Post by SendDerek on 2007-03-25
BTW:  I still get the "camera not found" error message when trying out dvgrab in the command line.

---

### Post by SendDerek on 2007-03-27
Does anybody have any experience with JVC Camcorders?

---

### Post by Skerit on 2007-04-01
Well, I admire your persistence! :P 

I'm not here to offer you a solution, I am here to whine alongside you! :)

It absolutely makes no sense, but I have the same problem, which is completely absurd as I had no problem in dapper or in my previous edgy installs, I followed the same guides as I did before and now nothing works...

---

### Post by albesan on 2007-04-04
Hello team,

Yep, on the same boat... and no answers yet.


a.

---

### Post by SendDerek on 2007-04-04
Welp, I'm glad to know that I'm not the only one then.

I feel like I'm so close though.  

And it doesn't even have to be a Sony computer that we're talking about, it could be on any computer with any DV camcorder.  Maybe the JVC's don't work well with linux?

I've emailed the support staff at JVC with this:
> 
Model:  GR-D290U
Purchase Date:  2006-12-10
Product Type:   Camera
Inquiry Type:   Software Installation
Email Body:     Hello!

I know this is a long shot, but I figured I would ask really quick...

Would you be able to assist me in getting my DV Camcorder to work though
Ubuntu Linux?  I seem to be having a difficult time with it and I was
hoping that maybe you may know whether or not this is compatible with
linux?

Thank you for your time.

-Derek


And this is what I got back (11 days later):
> 
Dear Mr Hildreth,

Thank you for contacting JVC Customer Care.

That should work, but we are unfamiliar with that program. I suggest
contacting them for assistance.

Please feel free to email us back for further questions or support about
your JVC Product.



Sincerely,
Joe Sanchez


My favorite part is "we are not familiar with that program".  Uh, dude...  it's not a program, it's an OS.  Please do JVC a favor and leave the technical department.

:)

---

### Post by pimpaulogy on 2007-04-05
I'm in your same boat.  I've got a Sony Handycam DCR-HC20 NTSC and I can't, for the life of me, get Ubuntu (was Breezy, now Edgy) to recognize/see my camera.

I really hope that somebody out there can chime in with a solution to our problem.

---

### Post by Ench on 2007-04-06
I have sony dcr-trv103-ntsc handycam, and I had some problems with dvgrab... I read some of the stuff in this post, and I am using kino now and all seems fine...

When you just press Play on the camera, it doesn't show the video in Kino?

Do you have other devices connected via Firewire?

Have you tried on another computer if everything else is working ok?

I don't know if this helps, but.. :) yuou can check

---

### Post by pimpaulogy on 2007-04-07
Thanks for the advice.

Unfortunately, I don't have any other firewire devices to connect.

If I push play on the camera and have kino open to capture, nothing happens.

I know there is some type of connectivity because it says DVin on the screen of my camera when I connect it.

The only other computers I have are laptops that have firewire but I don't have a cable to connect 6pin to 6pin.

Hopefully, somebody will see this thread that has experienced the issue and fixed it.  Crossing fingers.

---

### Post by SendDerek on 2007-04-08
> **Ench said:**
> I have sony dcr-trv103-ntsc handycam, and I had some problems with dvgrab... I read some of the stuff in this post, and I am using kino now and all seems fine...

When you just press Play on the camera, it doesn't show the video in Kino?

Do you have other devices connected via Firewire?

Have you tried on another computer if everything else is working ok?

I don't know if this helps, but.. :) yuou can check

Thanks for the advice for sure... I, like pimpaulogy, don't have any other firewire devices to try out.  I wish I had now! lol

---

### Post by pimpaulogy on 2007-04-20
Is this dead?  I still have the issue, but I haven't seen any possible solutions to try.  Bummer if that is the case.

---

### Post by SendDerek on 2007-04-20
I don't think it's entirely dead just yet... just waiting for some more input.

I myself havn't been able to find much more information on the matter.  I kind of did a quick'n'dirty fix and booted up my windows partition.  I'd would LOVE to prevent that at all costs.

---

### Post by pimpaulogy on 2007-04-20
That's what I am trying to avoid.  I just did a clean install of Feisty so we will see if that changes anything.  Of course, I am fighting with my screen resolution again.  Wish I would have remembered how I fixed it before.

---

### Post by SendDerek on 2007-04-21
I just did a clean install of fiesty as well...  I'll probably have to go through all of those steps again to get the permissions right and stuff.  Oh well.  I'll be downloading kino 1.0 soon and then trying it out.

---

### Post by pimpaulogy on 2007-04-24
SendDerek, have you figured out the magic dust yet to sprinkle on the box to get this to work?

---

### Post by SendDerek on 2007-04-24
Well... I feel like I am soooo close, and yet so far away.  I'm not sure if I'll ever be able to get this to work.

Anyways, I've gotten Kino 1.0 up and running and I've gotten this far:
> 
no av/c compliant cam connected or not switched on?


Well, it's plugged in and turned on.  I'm not sure what I'm doing wrong, but I'm investigating.

I just noticed that under preferences -> ieee 1394 -> av/c device there is nothing listed at all.  No options what-so-ever.

---

### Post by SendDerek on 2007-04-25
So,  I just realized (duh moment) that I have an external DVD+/-RW Sony drive that can be hooked up either by firewire or usb.  I went ahead and connected the drive via firewire, inserted a CD, and PRESTO!  It worked!

So, I know now that my firewire port works and that I have access to it.  The bad news is, it just sounds like my camcorder isn't compatible.  Of course, I would hate to conclude this and not do anything else.  So, I'll keep persisting on my own and research on how other people are doing with JVC camcorders and Linux...

---

### Post by SendDerek on 2007-04-25
Okay, so with a little bit more playing around I've found something very interesting...

First, I plug in the DVD burner without a CD via USB cable.  I insert the CD and it works.  I then eject the cd via desktop.

Second, I plug in the DVD burner without a CD via 6-4pin firewire cable.  I insert the CD and it works!  I eject the cd via desktop.

Third, I plug in the DVD burner without a CD via 4-4pin firewire cable.  I insert the CD and it DOESN'T work!

Forth, I verify that the DVD burner is still good by repeating my second step.  It works.

I have a 4-pin firewire connection on my laptop, so a 4-4pin firewire is a must.

I believe that this is a strange occurance.  It would leave me to believe that my 4-4 firewire cable is bad, but it's not because I was able to rip DV on my Windows partition.  So, the cable is good.  Why doesn't Linux like my 4-4pin firewire cable?

---

### Post by pimpaulogy on 2007-05-02
Still no solution.  Here's a bit more info:

When I plug my Camcorder in with the Firewire cable and turn it on, I see on the screen of the camcorder that it says DVin so there has to be some type of connection.

If I type DMESG in the terminal, this is the output:

ieee1394: received packet during reset; ignoring
ieee1394: received packet during reset; ignoring
ieee1394: received packet during reset; ignoring
ieee1394: received packet during reset; ignoring
ieee1394: received packet during reset; ignoring
ieee1394: received packet during reset; ignoring

and that could go on forever.

---

### Post by SendDerek on 2007-05-03
Interesting, timely article about the new Linux Firewire Stack:
[http://www.linuxtoday.com/developer/2007050302926NWKN](http://www.linuxtoday.com/developer/2007050302926NWKN)

---

### Post by pimpaulogy on 2007-05-04
Well, I figured out at least one of my issues, and it seems to be a common theme amongst other people. The FireWire cable that I bought (actually two of them) were causing an issue.  The only cable that works (tested with Windows) was the one that came with my FireWire card.  The two I bought from Fry's for about $6 each seem to cause an issue (will lock up my Windows box if I use them).

I still can't connect with my linux box, but the error message isn't what I listed before, which was infinitely repeated.

---

### Post by jacktar on 2007-05-07
I take it you are using the mains adaptor on your camcorder ? I had a similar problem with my Sony until I plugged it into the mains.

---

### Post by pimpaulogy on 2007-05-07
@Jactar:

Note really sure what you mean by the "mains adapter"?  I just have a port on my camera for a 4 pin firewire cable and that's what I plug in to.  My realization was that I needed to use the firewire cable that came with my firewire card, not the additional cables that I bought from Fry's.  Not sure what the ones from Fry's fail, but they do.

---

### Post by SendDerek on 2007-05-08
> **jacktar said:**
> I take it you are using the mains adaptor on your camcorder ? I had a similar problem with my Sony until I plugged it into the mains.

I'm not sure what you mean by 'mains' either.  I'm in the same boat I think... I have one 4-pin firewire port on my laptop, and one 4-pin firewire port on my JVC camcorder.

My firewire cable, however, does work and it is good (tested with Windows).

---

### Post by J-D-Cronin on 2007-05-08
I'm assuming that by "mains" jacktar is reffering to the electrical wall outlet...

---

### Post by jacktar on 2007-05-08
Yes, thats right, the A/C power supply.

---

### Post by SendDerek on 2007-05-08
Oh!  Well, in that case... when I was doing my tests, I had it both plugged and unplugged.  It didn't seem to make any difference.  

Why?  What was your train of thought on the 'mains' concept?  Would it matter?

---

### Post by jacktar on 2007-05-09
If I don't have the external power supply plugged in I get a warning message telling me there is no camcorder connected or not switched on. My camcorder is a Sony. Your camcorder instructions should tell you if its necessary with yours.

---

### Post by pimpaulogy on 2007-05-09
I also have a Sony, and at least with Windows, I can capture the video with or without the power cord plugged into the camera.  Not sure about on the Linux side.  I have basically given up on the Linux side until I see that somebody solved the issue.

---

### Post by carlosponti on 2007-05-09
I have a canon ZR200 mini-digital camcorder and have the same issue with dvgrab stating error:no camera found. using a 6-4 cable and feisty fawn. ps there is a site that will list wether your camera is [ supported]("http://www.linux1394.org/hcl.php?class_id=3").

---

### Post by SendDerek on 2007-05-15
Well, the bad news is that after looking at that "supported' website, I didn't find my model.  Darn.  Does this really mean that I'm out of luck?

---

### Post by Aphorism on 2007-05-15
Sorry, but my time is slight, can we boil this down?

My first guess is that you have yet to have your IEEE1394 subsystem in place -- that being FireWire if you have succumbed to the Apple marketing campaign.

If we can start with that, we can solve the issue.

The camera shouldn't be an issue -- DV is DV.

Sorry to not help much further, but perhaps you can distill your problem down a bit.  Were you ever able to get the 1394 subsystem up?

Sincerely,
TJS

ALSO:  I wish more people would use [https://answers.launchpad.net/ubuntustudio/+addquestion](https://answers.launchpad.net/ubuntustudio/+addquestion) , as then many of us get instant emails.  Forums and mailinglists are useless to many of us.  Sorry...

---

### Post by SendDerek on 2007-05-28
Well... I just tried it with my cousin's Sony DV camcorder and it worked perfectly.  I guess my JVC just insn't  compatible.

*sigh*  Oh well...  I'll be more careful next time I get a camcorder.  

**Thanks for all of the help on this topic peoples! **

---

### Post by pratik5705 on 2007-06-15
I have a JVC GRD-650US.

This morning I got it to work with Kino.

I have Kubuntu Fiesty. What I did was add two lines to /etc/modules as suggested by one thread 

What works for me is to add:
raw1394
video1394
to my /etc/modules file.


see here: [http://ubuntuforums.org/archive/index.php/t-2792.html](http://ubuntuforums.org/archive/index.php/t-2792.html)

then I restarted. Opened up Kino. First time there were some issues. I went to the capture screen. pressed capture. It said it did not recognize a camera. I restarted Kino. Went to options or preferences. In the section for dv cameras, it selects something like /dev/raw1394/0

selected capture, it prompted me to press play on the handycam. (make sure handycam is in play mode and not rec mode) and press play on ur handycam. still no video on the computer, but it was recording soemthing.. i like it record for 10-15 seconds. then pressed stop on Kino. and lo an behold. it did capture video.

however the video was jerky. i need to figure that out though...
hope this helps

---

### Post by SendDerek on 2007-06-15
Great news!

I believe that after some kernal updates in Fiesty, my JVC camcorder works now!  

Thanks for your help everybody! 

And thanks to pratik5705 for giving me inspiration to trying this whole thing again!


[MARKED AS **SOLVED!**]

---

