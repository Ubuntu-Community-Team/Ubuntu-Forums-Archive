---
title: "S4 Resume - USB Power Issue"
date: 2011-03-11
forum: Mythbuntu
---

### Post by rvm5 on 2011-03-11
I can successfully suspend (S4, via pm-hibernate) and resume my mythtv system via the power button on my machine.  I would like to accomplish the above via my MCE remote.  I enabled all the  USB devices (which were initially disabled).  However, after suspend, I don't see any power to my USB mouse or my USB Receiver for the remote.

After some searching for topics related to my motherboard, I found this thread
[http://vip.asus.com/forum/view.aspx?id=20110209160418914&board_id=1&model=P7H55-M+PRO&page=1&SLanguage=en-us](http://vip.asus.com/forum/view.aspx?id=20110209160418914&board_id=1&model=P7H55-M+PRO&page=1&SLanguage=en-us)
which basically says that I need to enable this in the kernel?  Here's a snippet from that thread:
------------------------------------
"The solution was:   Device Drivers -> USB Support -> USB runtime power management (autosuspend) and wakeup"
------------------------------------

Can someone shed light on the best way to enable my USB receiver to respond to remote during an S4 suspend?

---

### Post by matt06 on 2011-03-12
Hi rvm5.  Unfortunately, I'm not familiar with checking or setting kernel options and perhaps S4 is quite different, but take a look at this thread..

[mceusb and S3 wakeup]("http://ubuntuforums.org/showthread.php?t=1502401")

In short, double-check contents of /proc/acpi/wakeup, configure lirc to use the proper remote and button (there are many versions of the MCE remote), can you wake from *any* USB devices?  Or anything other than the power button for that matter?

---

### Post by rvm5 on 2011-03-13
Hi matt06, 
    thanks for your response.  I was trying the instructions in the link you sent earlier.  In my case, I can't seem to wakeup via any USB device: mouse, remote, keyboard (ps2) etc...

---

### Post by matt06 on 2011-03-14
In that Asus forum thread you linked to Brandon seems to indicate that S4 (or is it S3?) resume works with Windows installed so I would look for info on setting that kernel option.  It's my understanding that you'd have to compile a custom kernel to set options, but I'm no Ubuntu or Linux expert.

Have you tried using the S3 option in your BIOS or are you looking for S4 only?  S3 is suspend to RAM, S4 is suspend to disk (Windows calls S3 "standby" and S4 "hibernate" IIRC).

---

### Post by rvm5 on 2011-03-16
Thanks again for your response.

I tried the S3 option (pm-suspend) and faced the same issue. I didn't expect to recompile a custom kernel for this functionality, but I guess that's what I'll research into next.

---

### Post by Steve_M on 2011-03-18
I had the exact same issue last night. I'm not sure where I found the solution but here is what I did

Get ID of remote receiver (0815)
**lsusb**
Bus 002 Device 002: ID 0471:_0815_ Philips (or NXP) eHome Infrared Receiver

Get port details (2-1)
**> grep 0815 /sys/bus/usb/devices/*/idProduct**
/sys/bus/usb/devices/_2-1_/idProduct:0815

Check state of port  (disabled)
**cat /sys/bus/usb/devices/2-1/power/wakeup**
_disabled_

Edit /etc/rc.local to enable port
Add line 
**echo enabled > /sys/bus/usb/devices/2-1/power/wakeup**

also from another source
Add lines (these I did first but it didn't work on it's own - may be not needed)
[B]sudo sh -c "echo USB0 > /proc/acpi/wakeup"
sudo sh -c "echo USB1 > /proc/acpi/wakeup"
sudo sh -c "echo USB2 > /proc/acpi/wakeup"
sudo sh -c "echo USB3 > /proc/acpi/wakeup"
[/B]

Reboot & it worked

---

### Post by matt06 on 2011-03-19
Good stuff Steve.  Thanks for posting.

---

### Post by rvm5 on 2011-03-26
Steve_M, cool....  The instructions work for me to the point that when I execute a pm-suspend the system goes to sleep entering the S3 state.  Now, when I press the power button on my remote the receiver's red LED lights up.  However, the system does not wake up.  Looks like I am almost there....

thanks!

---

### Post by mice80 on 2011-11-05
> **Steve_M said:**
> I had the exact same issue last night. I'm not sure where I found the solution but here is what I did

Get ID of remote receiver (0815)
**lsusb**
Bus 002 Device 002: ID 0471:_0815_ Philips (or NXP) eHome Infrared Receiver

Get port details (2-1)
**> grep 0815 /sys/bus/usb/devices/*/idProduct**
/sys/bus/usb/devices/_2-1_/idProduct:0815

Check state of port  (disabled)
**cat /sys/bus/usb/devices/2-1/power/wakeup**
_disabled_

Edit /etc/rc.local to enable port
Add line 
**echo enabled > /sys/bus/usb/devices/2-1/power/wakeup**

Reboot & it worked

Hi, this my first post ... and I really need some help here :(

**lsub**
Bus 004 Device 002: ID 15c2:0042 SoundGraph Inc.

so my reciever ID si **0042**

[B]grep 0042 /sys/bus/usb/devices/*/idProduct
[/B]/sys/bus/usb/devices/4-2/idProduct:0042but when I check for port state 
**cat /sys/bus/usb/devices/4-2/power/wakeup**
i don t get any info ... NOT disabled, NOT enabled ... just blank

--------------------------------------------------------------------------------------
xxxxxxxxxxxxxxx:~$ grep 0042 /sys/bus/usb/devices/*/idProduct
/sys/bus/usb/devices/4-2/idProduct:0042
xxxxxxxxxxxxxxx:~$ cat /sys/bus/usb/devices/4-2/power/wakeup
                                  ------>BLANK
xxxxxxxxxxxxxxx:~$ 
--------------------------------------------------------------------------------------

If I try this on my keyboard 

--------------------------------------------------------------------------------------

xxxxxxxxxxxxxxxx:~$ lsusb
Bus 002 Device 002: ID 413c:2003 Dell Computer Corp. Keyboard

xxxxxxxxxxxxxxxx:~$ grep 2003 /sys/bus/usb/devices/*/idProduct
/sys/bus/usb/devices/2-1/idProduct:2003

xxxxxxxxxxxxxxxx:~$ cat /sys/bus/usb/devices/2-1/power/wakeup
disabled
xxxxxxxxxxxxxxxx:~$ 

---------------------------------------------------------------------------------------
so I can enable the usb port to wake the computer with the keyboard, but it doesn t work with my IR reciever




THX !!

---

### Post by Steve_M on 2011-11-05
From this page ([http://www.soundgraph.com/forums/showthread.php?t=5954](http://www.soundgraph.com/forums/showthread.php?t=5954)) on the manufacturers website

"Power-On feature in iMON is not USB wake up. "

Looks like your out of luck with this remote.

---

### Post by mice80 on 2011-11-06
> **Steve_M said:**
> From this page ([http://www.soundgraph.com/forums/showthread.php?t=5954](http://www.soundgraph.com/forums/showthread.php?t=5954)) on the manufacturers website

"Power-On feature in iMON is not USB wake up. "

Looks like your out of luck with this remote.


ahhhhhhh ....  looks like I will have to buy a new reciever ... 

and everything was working so great ... XBMC ... iMON reciever ... MCE script and the remote of all remotes Harmony ...

btw ... I really appreciate your help, thx for your fast reply Steve_M

---

### Post by Steve_M on 2011-11-06
If you have a smart phone you may be able to run a wake-on-lan app. Not quite as useful as the remote, but if the phone lives in your pocket most of the time it can be useful.

It can be a handy thing anyway, I can remotely turn on the lounge or bedroom systems with WOL, then use VNC or SCP to administer them from my study.

---

