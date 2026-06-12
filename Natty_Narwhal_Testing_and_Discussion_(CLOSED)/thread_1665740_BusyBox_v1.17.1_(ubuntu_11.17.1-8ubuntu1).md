---
title: "BusyBox v1.17.1 (ubuntu 1:1.17.1-8ubuntu1)"
date: 2011-01-12
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Quackers on 2011-01-12
Built-in shell (ash)

Enter help for a list of built-in commands

(initramfs)

This is what just greeted me when trying to boot into my other Natty install. It was alright a few hours ago. No updates that I haven't already rebooted since. 

Anyway, I just tried booting again and it went fine.

Is this a sign of impending problems? Or just a temporary glitch?

---

### Post by cariboo on 2011-01-12
I think it was more of a temporary glitch, as I haven't seen anything like that on any of my 5 Natty installs.

4 of them are so stable, it's getting boring. :), The only one that breaks is my gnome 3/gnome-shell experiment, gnome3 seems to be pretty stable, but if you add gnome-shell to the mix it crashes frequently.

---

### Post by Quackers on 2011-01-12
Yes, on the whole very stable :-) I'll avoid gnome-shell for the moment then :-)
It's the only (or first :-) ) time this has happened on either install, so we'll see. Booting can be a hit and miss affair though. Sometimes I get the bottom panel, sometimes I don't. Sometimes I get the sound icon showing that sound is muted, but it isn't, and it doesn't do anything at all if I click on the icon. Nothing too disastrous though lately, which is good :-) I use both Natty's as my daily OS, although I can always fall back to Maverick if disaster strikes.

---

### Post by Quackers on 2011-01-13
The same Natty install now reports on boot, that the machine does not appear to have the necessary graphics to use openGL. Nonsense of course, so if I just OK the message and carry on booting, the desktop loads just fine - along with all the usual effects. Strange!

---

### Post by ronacc on 2011-01-13
if you haven't reinstalled your graphics driver since the update to xorg try that . after the update the first reboot went ok for me but the next one couldn't find the driver so I removed and reinstalled nvidia-current and all has been well since .
note: I  have added to my xorg.conf

Section "ServerFlags"
Option "IgnoreABI" "True"
EndSection

---

### Post by Quackers on 2011-01-13
Thanks ronacc, I'll bear that in mind.
No, I haven't done anything at all with the nvidia driver, with either install, since I first installed Natty. Obviously I've run the updates for it, from time to time, but nothing else.
Presumably I would just remove ncidia-current (nothing else)?
And what do your additions to xorg.conf do, please?
Thanks.

---

### Post by Harry33 on 2011-01-13
> **ronacc said:**
> if you haven't reinstalled your graphics driver since the update to xorg try that . after the update the first reboot went ok for me but the next one couldn't find the driver so I removed and reinstalled nvidia-current and all has been well since .
note: I  have added to my xorg.conf

Section "ServerFlags"
Option "IgnoreABI" "True"
EndSection

Ronacc, I think those lines in xorg.conf are only used when a new series of xorg-server has been installed and Nvidia has not yet published a a new driver for new xorg-server.
Natty has xorg-server 1.9 series in repos and the recent nvidia-current_260.19.29 fully supports it.
So those lines are not needed, unless you have installed the newest snapshot of xorg-server 1.9.99.901 (1.10 series).

---

### Post by ronacc on 2011-01-13
yes just use system>administration>hardware drivers  to remove Nvidia-current and then re install it . The added section tells the server to ignore the ABI  , the update to xorg breaks the current ABI , actually I use that all the time , my sys runs fine without it ( Nvidia 7600gs ) . If your box needs the ABI you'll have to wait until everything gets caught up .

---

### Post by Harry33 on 2011-01-13
> **Quackers said:**
> Thanks ronacc, I'll bear that in mind.
No, I haven't done anything at all with the nvidia driver, with either install, since I first installed Natty. Obviously I've run the updates for it, from time to time, but nothing else.
Presumably I would just remove ncidia-current (nothing else)?
And what do your additions to xorg.conf do, please?
Thanks.

Those lines are used to overcome (ignore) the fact that nvidia-current driver ABI does not match the one of the installed xorg-server and video drivers.

Package nvidia-current_260.19.29-0ubuntu1 is the newest driver ATM.
That one provides virtual packages xserver-xorg-video-8 and xorg-driver-video.
So it seems to me it is not the same ABI than the xorg-server 10 series will have.
Xorg-server 1.10 will provide virtual package xorg-video-abi-9.
Meaning nvidia-current would not support it.

---

### Post by Harry33 on 2011-01-13
> **ronacc said:**
> 
...
the update to xorg breaks the current ABI , actually I use that all the time , my sys runs fine without it ( Nvidia 7600gs ) . If your box needs the ABI you'll have to wait until everything gets caught up .

What xorg are you actually talking about?
The reference number of the ABI of the nvidia-current is 8.

---

### Post by ronacc on 2011-01-13
my server version  is 1.9.0.902 the update came down jan 12 after I saw your post about 1.10 and removed all the stuff Plun noted in your thread so I held off rebooting until the xorg stuff relevant to my sys came back .(later that day) .

---

### Post by Harry33 on 2011-01-13
> **ronacc said:**
> my server version  is 1.9.0.902 the update came down jan 12 after I saw your post about 1.10 and removed all the stuff Plun noted in your thread so I held off rebooting until the xorg stuff relevant to my sys came back .(later that day) .

OK, right.
The nvidia-current_260.19.29-0ubuntu1 fully supports your xorg-server 1.9 branch.
I haven't tested the xorg-server 1.10 yet.

---

### Post by Quackers on 2011-01-13
It's all foreign to me :confused:
Are you speaking English? :-)

As all this xorg stuff was done automatically, I wasn't even aware I had one until I saw it mentioned a while ago :-) Maybe I've just been luckier with my hardware than some!

But again, thanks to both of you for the info :wink:

---

