---
title: "raw1394 system crash after seconds of dv capture"
date: 2008-08-26
forum: Multimedia Software
---

### Post by bonnem on 2008-08-26
Hello,

using debian/ubuntu for years I have a strange crash. Trying to hook up dv video cameras to a standard pccard ohci interface with raw1394 both dvgrab and kino keeps crashing after a couple of seconds of grabbing.

Tried using stock kernels and compiling different kernels, (2.6.22, 2.6.25 and 2.6.26), clean xubuntu, debian etch and debian lenny distro's, different camera's (sony trv110e and trv900e) the whole system keeps on hanging.

No syslog messages, no dvgrab/kino messages, so no google starting point. I've read something about the IEEE stack and SMP + > 900MB memory problems. but with a the kernel parameter mem=512mb the camera ain't recognized.

The complete system (including mouse, caps/numlock) is hanging. Ubuntu automatically reboots when I pull out the pcmcia card :S 
Rebooting and  rebuilding for days this really drives me mad! The new firewire-core interface ain't working with dv capturing.

The system is a standard thinkpad T60, ohci conceptronic firewire-card, 1.5g ram and no errors anywhere.

Has anyone encountered a similar problem?  A system crash ain't a linux thing.. Help is much appreciated!

---

### Post by bonnem on 2008-08-26
here maybe a quick fix on my own post.. somehow the ati module (fglrx) seems to give some strange problems.. not loading the flgrx module seems to conflict with capturing and controlling dv with firewire.

Although even capturing in tty locks up, unloading the module and using vesa seems to grap and control dv just fine.. 

I'll dig deeper into it and post a bug report for ati :P

---

### Post by DuncanNZ on 2009-02-23
Hi there, since you're having trouble with capture over Firewire to Kino you might want to look at my recent update of the [https://help.ubuntu.com/community/Firewire](https://help.ubuntu.com/community/Firewire) page. Please let me know if there are any problems with that guide.

---

