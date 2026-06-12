---
title: "Wake from suspend with Remote Wonder"
date: 2011-06-22
forum: Multimedia Software
---

### Post by jshoor on 2011-06-22
Hi there,

I was just wondering if anyone has had any luck using an ATI Remote Wonder to wake up their machine from suspend?  There are some great instructions for the MCE Remote that I have followed up until I get to the point where I have to "enable sysfs based wakeup on Remote Control device"

When I try to run the command: 
echo enabled > /sys/bus/usb/devices/2-1/power/wakeup

it fails with an invalid argument error.

I did notice that both /sys/bus/usb/devices/usb1/power/wakeup
and /sys/bus/devices/usb2/power/wakeup are both enabled, and I can disable and reenable them easily enough.  So, I assume its a problem with the ATI Remote Wonder?  Is there some special reason why the MCE Remote would work but the ATI Remote would not?  Is there something else special I need to do to get the ATI Remote to work?  

Im running 2.6.32-32-generic, if that has any bearing on the issue.

Thanks in advance!
Jonas

---

