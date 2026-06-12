---
title: "lirc: no /dev/lirc0 - actual device number changes on restart"
date: 2010-05-30
forum: Multimedia Software
---

### Post by otoh on 2010-05-30
Firstly, installed mythbuntu and for the most part, it just works. AWESOME!

My only issue that I can't figure out thus far is the remote. I'm using a Hauppauge Nova-T USB Stick, and generally the setup for the Nova-T 500 is good. No problem with lircd.conf, .lircrc etc.

My problem is that the remote doesn't work on startup. Looked in /etc/lirc/hardware.conf and it says, as expected:

REMOTE_DEVICE="/dev/lirc0"

Which doesn't work because I have no /dev/lirc0 (I do have a /dev/lircd). However, running /proc/bus/input/devices, I discover that my IR receiver is event5, so if I change the /etc/lirc/hardware.conf to:

REMOTE_DEVICE="/dev/input/event5"

And restart lirc, it works fine. Unfortunately, upon restarting the PC, the IR receiver doesn't always have the same path - eg it could be event6 or event8 etc - so then I need to fix the /etc/lirc/hardware.conf again.

This looks like it's cropped up here before, but I couldn't find an actual resolution. Any ideas?

MTIA!

---

### Post by otoh on 2010-06-08
Solved this - I apologise to the original author of the solution for mislaying where I found it :( But essentially it was:

[LIST]
[*]cat /proc/bus/input/devices to discover the name of the device; mine was called something like 'IR-receiver inside USB tuner'
[*]cd /etc/udev/rules.d
[*]Create a new file - anyname.rules, eg I made win-tv.rules - content:
[*]KERNEL=="event[0-9]", ATTRS{name}=="IR-receiver*", SYMLINK+="lirc0"
[/LIST]

Restart and voila, /dev/lirc0 is there, /etc/lirc/hardware.conf works as expected!

Hope this helps someone!

---

### Post by sisco311 on 2010-06-08
You don't have to create a new the symbolic link(/dev/lirc0), there should be already one in /dev/input/by-path/ ;)

To mark this thread as [SOLVED] Click the "[COLOR="Red"]Thread Tools[/COLOR]" Menu at the top of the page and then "Mark this thread as Solved".

---

### Post by otoh on 2010-06-08
> **sisco311 said:**
> You don't have to create a new the symbolic link(/dev/lirc0), there should be already one in /dev/input/by-path/ ;)

Ooh, I see it now, I guess it's pci-0000:00:1d.7-event-ir - I guess I could have used this in my hardware.conf. Never came across that in much searching on the problem! Assuming it stays the same on reboot, will remember for next time!

> **sisco311 said:**
> To mark this thread as [SOLVED] Click the "[COLOR="Red"]Thread Tools[/COLOR]" Menu at the top of the page and then "Mark this thread as Solved".

I'm sure that wasn't there before... Huge thanks either way :)

---

