---
title: "LIRC /dev/lirc0 issue"
date: 2010-09-25
forum: Multimedia Software
---

### Post by selectedusername on 2010-09-25
Hi,

I'm running Ubuntu 10.10 beta with MythTV 0.23.1 on my HTPC setup. For the HTPC I'm using a HFX mini cabinet which has a built-in Soundgraph iMon VFD and IR receiver. I've installed LCDproc and configured and my VFD works like a charm. So far so good.
I've also installed LIRC to be able to control the HTPC with a remote. I don't have the original remote but intend to use a MCE remote I have lying around.
After installing LIRC I have no /dev/lirc0 which should be my handle to the IR-receiver.
```
ls /dev/
``` does not contain a lirc0 but only lircd.
If I run
```
lirc | grep "lirc"
```
I can see that both ir_lirc_codec and lirc_dev have been loaded. What am I missing? Any help is greatly appreciated!

---

### Post by QwkBrnFox on 2010-10-06
Hi Selected, 

I just went through the same problem, except that my /dev/lirc0 existed yesterday (I upgraded all the packages today).  Something in the new 2.6.35-22 kernel is borked.  I also have the 2.6.35-20 kernel on my system (left over from before the upgrade?) - when I boot to with that kernel does have the /dev/lirc0 entry.

I'll enter a bug, and post it here.

Good luck!

Todd

---

### Post by QwkBrnFox on 2010-10-07
Here's the bug:  

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/655512](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/655512)

Devs seem to be looking into it (thanks, Devs!).

---

### Post by QwkBrnFox on 2010-10-08
The Devs solved it - I had lirc-modules-source installed as well as lirc.  Seems there was some sort of conflict?  apt-get remove lirc-modules-source fixed it up.

Hope that this works for you.

Todd

---

### Post by TSlackM on 2010-10-09
I'm also suffering from no /dev/lirc0
using kernel 2.6.35.22 latest in 10.10

tried purging lirc and lircmodules source and reinstalled just lirc.
lircd -v   lircd 0.8.7-pre3
mouse workes fine, but none of the buttons, also in my hardware.conf

REMOTE_DEVICE=/dev/lirc0 
changes to 
REMOTE_DEVICE=/dev/input/event2
after a reboot. 

dmesg [http://pastebin.com/5tLRQH4A](http://pastebin.com/5tLRQH4A)

any tips?

edit:
testing event2 with evtest shows every button working, so i guess something has changed,
now i have to get it working with irw,

---

### Post by ymmatt on 2010-10-14
I'm having the same issue with the new kernel, it is a new install and I've been banging my head on this for 2 days.

The kernel won't load the module I need: lirc_atiusb

The symptoms are similar to his issue: [http://old.nabble.com/atiusb-module-does-not--build-with-kernel-2.6.35-td29254059.html](http://old.nabble.com/atiusb-module-does-not--build-with-kernel-2.6.35-td29254059.html)

except that after looking at the code it doesn't seem that is the same solution, but I can't be sure.

I have two machines with the same install(kernel) and the bug is replicable by simply installing lirc and trying to insert lirc_atiusb
```
sudo apt-get lirc
sudo modprobe lirc_atiusb
```
results:
```
WARNING: All config files need .conf: /etc/modprobe.d/lirc-blacklist, it will be ignored in a future release.
FATAL: Module lirc_atiusb not found
```

This is obvious, but if I edit my hardware.conf to include the module and try to restart lirc (sudo /etc/init.d/lirc restart) i receive this error:
```
Unable toload LIRC kernel modules. Verify your selected kernel modules in /etc/lirc/hardware.conf
```

and dmesg outputs
```
[38999.024638] lirc_atiusb: disagrees about version of symbol lirc_register_driver
[38999.024643] lirc_atiusb: Unknown symbol lirc_register_driver (err -22)
[39066.058431] lirc_atiusb: disagrees about version of symbol lirc_register_driver
[39066.058436] lirc_atiusb: Unknown symbol lirc_register_driver (err -22)
```

I'm going to post this on the bug referenced here as I think that is the place for it.

---

### Post by a-user on 2010-10-14
guys, it is no bug. first i thoguht this too. i even posted to the mentioned bug report.

the thing is, that with kernel 2.6.35 it changed how this gets handled. imon is now a kernel driver hence it uses the linux devince input.

if you tried installing lirc and installung also new imon kernel modules that where not shipped with your ubuntu then it could get dirty to revert this back.

anyhow here is a thread where i explained how you do it correctly. it is on the general forums here:
[http://ubuntuforums.org/showthread.php?p=9952389#post9952389](http://ubuntuforums.org/showthread.php?p=9952389#post9952389)

if you have questions, don't hesitate to ask., but it could be that i cant answer till monday. anyhow, i posted in that thread how to do it, how to get it to work.

---

### Post by Kheops_74 on 2010-10-17
I upgrade to 10.10 and since i don't have the /dev/lirc0 anymore. I was using lirc_zilog in 10.04 but it seems to be missing.

Any idea?

---

### Post by a-user on 2010-10-18
Why you don't read the post just before yours? There is all explained! >.>

---

### Post by Kheops_74 on 2010-10-18
I read it a lot of time. Maybe we don't talk about the same thing. I try to make my pvr150 blaster work. In ther past, steps was simple.

Install lirc dev
patch with the lirc_zilog.diff
reconfigure lirc
load lirc_zilog module
change the harware.conf to add keys of my motorola setupbox
verify lircd.conf
reboot
et voilà.  /dev/lirc0 is there and it works

Steps seems different but they don't work

Thank for the help.

---

### Post by a-user on 2010-10-18
@[Kheops_74]("http://ubuntuforums.org/member.php?u=200309"): well next time tell that you are using a different remote control directly in your post.

anyway, i don't know if your remote control now has a driver in the kernel too. if so than you broke the modules with your installation of a different lirc version (patched).

if you try now the steps i wrote of course it wont work, cause you already messed up the modules.

first you should check if the kernel now directly supports your remote hardware. if so remove all lirc related, reinstall the kernel (image/modules), then reinstall lirc from the ubuntu repositories (not any other lirc you downloaded anywhere else, no patches!) and try to do what i wrote.

if your hardware is not support by the kernel through "linux deveice input" then i can't help you.


remember: stuff has changed with new kernel. many remote control hardware is now directly supported by the kernel under a common interface layer called "linux device input". installing your own modules from lirc versions not build to work with THIS here released kernel will only break things.

---

### Post by Kheops_74 on 2010-10-21
Ok i solve my problem ([http://ubuntuforums.org/showthread.php?t=1598968](http://ubuntuforums.org/showthread.php?t=1598968)). Thanks

---

