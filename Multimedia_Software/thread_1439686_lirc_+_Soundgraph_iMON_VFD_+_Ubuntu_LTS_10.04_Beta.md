---
title: "lirc + Soundgraph iMON VFD + Ubuntu LTS 10.04 Beta 1 (64bit)"
date: 2010-03-26
forum: Multimedia Software
---

### Post by mbulow on 2010-03-26
EDIT: Solution in #3 (At least in my case)
 
 
 
Hi all
 
I have just build a HTPC and decided to give Ubuntu a try.
 
Hardware:
 
Case: OrigenAE M10 (With a Soundgraph iMON IR/VFD)
CPU: Intel Core i3 530
Motherboard: Intel DH57JG
RAM: 2 x 2GB Kingston ValueRAM
SSD: Intel X25-M 80GB
 
 
 
My first attempt at Ubuntu was 9.10 (64bit). Installed without any problems at all, but as soon as I booted and GNOME loaded, the whole thing would lock up (no mouse or keyboard response).
 
Second attempt was 10.04 Beta 1 (64bit). Installed and everything seems to be working just fine.
 
Only problem so far is that I just can't figure out how to make lirc work with my iMON IR/VFD.
 
Well... That's not entirely true :oops:
 
I started searching for a solution and I found a lot of different solutions to the problem. After about 10 or 12 attempts I finally made it work. The LCD worked (lcdproc) and irw (and mode2) responded when I pressed the remote-buttons.
 
I wrote down the solution and reinstalled the entire system (messed around with a lot of other things).
 
The sad part is that the solution I found didn't work after all. The solution must have been some combination of all my attempts, but I have no idea what I have to do to make it work again :cry:
 
I have read that the iMON VFD device (ID: 15c2:0036) can be a real problem under Linux and now I know. But at least I KNOW it can work, just don't know HOW I did it)
 
Has anyone else made it work? I'm all out of ideas right now, and starting to get real frustrated...

---

### Post by eric_pwb on 2010-03-26
I am having a huge problem with my imon vfd, id 0044. 
It works fine in windows 7, but not at all in ubuntu, not 8.04, 8.10, 9.04, 9.10, or 10.04 beta1 on the same machine. When trying to echo to the device as root I get a  broken pipe error. With lcdproc running I get send packet failed errors in my kernel log. 

However if I connect the vfd to my macbook pro 5,5 in karmic, it works like a charm.

So this leads me to believe that there is an incompatibility in the kernel for the chipset, in my case the h55 on my p7h55m-pro mobo.

Any ideas?

---

### Post by mbulow on 2010-03-29
Finally made it work :)
 
This time I wrote it down and was ABLE to reproduce:
 
1) Install Ubuntu LTS 10.04 Beta 1
 
2) Update the system ( System => Administration => Update Manager => Install Updates )
 
3) Install lirc ( Select "Soundgraph iMON PAD IR/VFD" as remote )
 
4) Create /etc/modprobe.d/lirc.conf
options lirc_imon debug=1 nomouse=1 display_type=1 pad_thresh=5 ir_protocol=1
 
5) Reboot and test lirc by starting "mode2 -r -d /dev/lirc0"
 
6) Install lcdproc
 
7) Edit /etc/LCDd.conf
Change Driver=curses to Driver=imon
 
8) Reboot
VFD shows corrupt data
 
9) Install lirc-modules-source
 
10) Apply patch: [https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/517956](https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/517956)
 
11) Reboot
Both lirc and lcdproc work :D

---

### Post by eric_pwb on 2010-03-29
Solved My problem too!! Thanks Alot!!!

Mine in antec multimedia station elite 15c2:0044

---

### Post by Hotwheelz79 on 2010-05-10
Hi,

I have 2 questions guys.

1. Has this issue been fixed  in the final release?
2. Are you using Mythbuntu?

Thanks.

:-)

---

### Post by Rhiadon on 2010-05-31
I've tried to follow these steps and I've had no luck. I run dpgk-reconfigure lirc to change the remote to the "Soundgraph iMON PAD IR/VFD" and I get the following output:

```
dpkg-reconfigure lirc
 * Stopping remote control daemon(s): LIRC                               [fail] 
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service udev reload

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the reload(8) utility, e.g. reload udev
 * Loading LIRC modules                                                  [ OK ] 
 * Unable to load LIRC kernel modules. Verify your
 * selected kernel modules in /etc/lirc/hardware.conf


```

I'm at a loss at this point. I do indeed have a 15c2:0044 device that I've had for quite a while and I've never had any luck getting it to work. Any help you guys can hook me up with would be awesome. If you need to me to post the contents of files to help troubleshoot, let me know. I'm at a point where I have no idea what the next step should be.

FYI: I just upgraded to 10.04

---

### Post by Krautmaster on 2010-10-02
damn...

i tryed it for hours to get my origenae M10 ir (VF310) running but it just don't work yet. Fu.

I use lirc 0.8.6 on ubuntu 10.04.1.

I configured lirc for Soundgraph iMON PAD IR/VFD but irw and mode2 dont't recognize any command coming in. 

What should i do?

this is what i did:

> $ sudo apt-get install lirc lirc-modules-source lcdproc

# Lirc
> Remote Control configuration: SoundGraph iMON IR/VFD IR transmitter, 
> if present: None

# Timing patch installieren
$ cd /usr/src/lirc-0.8.6/
$ wget
[http://launchpadlibrarian.net/38821679/lirc-0.8.6-VFD_0x0036_timing.patch](http://launchpadlibrarian.net/38821679/lirc-0.8.6-VFD_0x0036_timing.patch)
$ sudo dkms remove -m lirc -v 0.8.6 -k `uname -r` $ sudo patch -p0 < lirc-0.8.6-VFD_0x0036_timing.patch
$ sudo dkms add -m lirc -v 0.8.6
$ sudo dkms build -m lirc -v 0.8.6
$ sudo dkms install --force -m lirc -v 0.8.6

# Der obige Patch verursacht packet write Fehlermeldungen im syslog # Anleitung:
[http://codeka.com/forums/viewtopic.php?f=3&t=35&start=10&st=0&sk=t&sd=a](http://codeka.com/forums/viewtopic.php?f=3&t=35&start=10&st=0&sk=t&sd=a)
# Diese Methode funktioniert:
$ cd /usr/src/lirc-0.8.6/drivers/lirc_imon
$ sudo dkms remove -m lirc -v 0.8.6 -k `uname -r` $ mcedit lirc_imon.c # Nach Methode send_packet suchen und folgendes direkt vor dem return
einfügen:
    ...
    set_current_state(TASK_INTERRUPTIBLE);
        schedule_timeout(5);
       
        return retval;
$ sudo dkms add -m lirc -v 0.8.6
$ sudo dkms build -m lirc -v 0.8.6
$ sudo dkms install --force -m lirc -v 0.8.6 # System neu starten


# Treiber lirc_imon konfigurieren
$ cd /etc/modprobe.d
$ sudo nano lirc_imon.conf
options lirc_imon display_type=1 ir_protocol=1 $ sudo nano usbhid options usbhid quirks=0x15c2:0x0036:0x0004 $ depmod -a $ update-initramfs -u

# LCD
$ cd /etc
$ sudo nano LCDd.conf
[server]
...
Driver=imon
...
ServerScreen=no
...

> System neustarten


---

