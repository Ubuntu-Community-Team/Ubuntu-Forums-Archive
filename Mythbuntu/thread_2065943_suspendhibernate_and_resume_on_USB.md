---
title: "suspend/hibernate and resume on USB"
date: 2012-10-03
forum: Mythbuntu
---

### Post by davidstoll on 2012-10-03
Well, resume on USB works really well with all forms of suspend/hibernate and also (my favorite) suspend-hybrid.

However, I have 2 issues.  I've searched around, but I can't seem to find anything posted that works for me.

1) I don't seem to be able to wake my frontend using my MCE usb ir remote.  It worked the first time I tried (but maybe I just bumped the mouse?).  But now I can only wake by usb keyboard or mouse.

2) I don't seem to be able to make mythfrontend suspend/hibernate the computer.  I enabed the shutdown menu and gave it different commands, but they all seem to require sudo and therein lies the problem.  It either just shuts down or does nothing because when I select shutdown from the mythtv exit menu, I assume it's waiting for the sudo password.

I'm hoping someone can assist me or if there is another thread I should look at, I would appreciate the nudge.

Thanks so much

---

### Post by melben on 2012-10-03
Try looking here:
[http://forums.overclockers.com.au/showthread.php?t=810214](http://forums.overclockers.com.au/showthread.php?t=810214)

Ben

---

### Post by davidstoll on 2012-10-03
> **melben said:**
> Try looking here:
[http://forums.overclockers.com.au/showthread.php?t=810214](http://forums.overclockers.com.au/showthread.php?t=810214)

Ben

Thanks, the visudo settings definately helped with issue #2.  Thanks!

However, my usb ir remote still doesn't want to wake up the pc.  Everything shows "enabled" in... cat /proc/acpi/wakeup

?

I did notice that my little ir reciever for my MCE remote normally blinks a little red light when it sees a signal.  However, when the pc is sleeping, it does not respond, so it's like it isn't getting any power or something.

---

### Post by davidstoll on 2012-10-03
I found the solution per:
[http://www.mythtv.org/wiki/MCE_Remote#S3_.2F_Suspend_To_RAM](http://www.mythtv.org/wiki/MCE_Remote#S3_.2F_Suspend_To_RAM)

From Ubuntu/Mythbuntu 10.10 onwards
Kernel changes require you to explicitly power USB devices during sleep. If after following the above the PC does not wake from sleep:

Get ID of remote receiver (0008)
lsusb
Bus 002 Device 003: ID 1784:0008 TopSeed Technology Corp. eHome Infrared Transceiver

Get port details (2-3)
grep 0008 /sys/bus/usb/devices/*/idProduct
/sys/bus/usb/devices/2-3/idProduct:0008

Check state of port (disabled)
cat /sys/bus/usb/devices/2-3/power/wakeup
disabled

If you just want a solution for the current session:
sudo su
echo enabled > /sys/bus/usb/devices/2-3/power/wakeup
exit

For a permanent solution, edit /etc/rc.local to enable port Add line
sudo sh -c "echo enabled > /sys/bus/usb/devices/2-3/power/wakeup"

on reboot the port will be powered when in S3, and the PC will wake from the remote.

---

### Post by davidstoll on 2012-10-03
> **melben said:**
> Try looking here:
[http://forums.overclockers.com.au/showthread.php?t=810214](http://forums.overclockers.com.au/showthread.php?t=810214)

Ben

On other thing about that post.  I like pm-suspend-hybrid better and also, it doesn't seem to be obvious that you need to replace "mythtvuser" with whatever your login is.

so:
sudo visudo

go to the bottom and add this line:
mythtvuser ALL=(ALL) NOPASSWD: /usr/sbin/pm-suspend-hybrid

Where "mythtvuser" is your login username.

---

### Post by davidstoll on 2012-10-04
I can wake up the pc via remote, but only a short while after the pc was turned off.  I let it go several hours and tried to wake it up and none of my usb devices would wake it up, let alone the remote.

Why would this be?

---

