---
title: "login display resolution"
date: 2006-07-19
forum: Multimedia &amp; Video
---

### Post by roger peppe on 2006-07-19
I've found this question asked in several places around the net (*), but never a good answer. Maybe someone here might be able to help.
My login screen uses a different display resolution to when I've logged in. In my case, using a widescreen monitor, this means that I can't see the login screen at all! (I managed to log in blind, eventually...)

(For reference's sake, it's taken quite a while to get anything going at all; I acquired a new graphics card (Radeon 9600 based), as my original card (an Intel 915) didn't support 1680x1050, even when using the 915resolution utility and inserting a notionally correct Modeline into /etc/X11/xorg.conf).

I suppose the real question is: why does the login screen use a different resolution setting from the logged-in screen, when as far as I can see it uses all the same configuration files? From the log file, it appears that it's trying to use 1920x1440, which isn't a resolution that's mentioned at all in my xorg.conf.

Thanks to anyone who might be able to shed some light on this issue.

Data:
system: kubuntu dapper 6.06
kernel: Linux ce-gw109 2.6.15-23-386 #1 PREEMPT Tue May 23 13:49:40 UTC 2006 i686 GNU/Linux
vid card: some random ATI video card (it came out of central stores)
monitor: viewsonic VA2012w-2
xorg.conf: see attached file
log: see attached file (from /var/log/Xorg.0.log)

(*) references:
[https://launchpad.net/distros/ubuntu/+source/gdm/+bug/16472](https://launchpad.net/distros/ubuntu/+source/gdm/+bug/16472)
[https://launchpad.net/distros/ubuntu/+ticket/1187](https://launchpad.net/distros/ubuntu/+ticket/1187)
[http://ubuntuforums.org/showthread.php?t=203072](http://ubuntuforums.org/showthread.php?t=203072)
[http://www.irclinux.org/freenode/ubuntu/2006/05/02/](http://www.irclinux.org/freenode/ubuntu/2006/05/02/)

---

### Post by mlind on 2006-07-19
Although I'm not an expert on the subject, I can help you troubleshoot this problem. 

Looking at your xorg.conf, you seem to request two modelines, which X server rejects because of invalid Mzh values for your monitor.

Use **fglrx** (propietary ati driver) instead of ati if possible. You'll find install instructions here [https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-5ead174a0b3294527486cd4d71ded66b40003f25](https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-5ead174a0b3294527486cd4d71ded66b40003f25)


In a nutshell, backup your /etc/X11/xorg.conf and execute
```

sudo dpkg-reconfigure **xserver-xorg**

```

Remove any wacom entries from xorg.conf, you don't need those if you haven't got a TabletPC.



If you look your Xorg.0.log closely, lines starting with (WW) are usually sings of trouble (except warning about font path).

If dpkg-reconfigure doesn't find valid hsync & vrefresh values for your monitor, you must check these from your monitor's manual
```

(II) RADEON(0): VA2012w-2: Using hsync range of 30.00-94.00 kHz
(II) RADEON(0): VA2012w-2: Using vrefresh range of 50.00-75.00 Hz

```

These values are probably invalid ?
Problems seem to continue on Xorg.0.log, line 615 and onwards, where should be report of valid modes, not rejected ones.


```

(WW) RADEON: No matching Device section for instance (BusID PCI:1:0:1) found

```
Hmm.. BusID should be correct after you execute dpkg-reconfigure for xserver-xorg (lspci should report similar value)

---

### Post by roger peppe on 2006-07-19
I can see that there might be problems with my xorg.conf file, but *it works fine when I'm logged in*. Why the difference?! Why does logging in magically make my display settings work OK?

---

### Post by mlind on 2006-07-19
> **roger peppe said:**
> I can see that there might be problems with my xorg.conf file, but *it works fine when I'm logged in*. Why the difference?! Why does logging in magically make my display settings work OK?

I'm not sure. Could be that display manager/driver does some sort of fallback or has the logic to lookup the valid modes, but greeter doesn't.
But by fixing your X.org configuration you'll eventually fix this issue too.

---

### Post by roger peppe on 2006-07-19
Well, I just installed the proprietary driver, and that has finally fixed the problem (no additional change to xorg.conf necessary). Thanks for the info. I'm still confused about how there could be such a difference (isn't it using the same machinery in both modes?), but I'm happy now, so I'll rapidly retreat...

---

### Post by mlind on 2006-07-19
> **roger peppe said:**
> Well, I just installed the proprietary driver, and that has finally fixed the problem (no additional change to xorg.conf necessary). Thanks for the info. I'm still confused about how there could be such a difference (isn't it using the same machinery in both modes?), but I'm happy now, so I'll rapidly retreat...

I'm not sure, these thing often work in mysterious ways. Just make sure your
monitor is working with correct refresh rate, and you've got 3D acceleration
(**glxgears** actually works) then you're all set.

---

### Post by roger peppe on 2006-07-20
good suggestion about glxgears. i tried it, and got lots of "could not register entrypoint" messages. thank god for google - replacing /usr/lib/libGL.so.1.2 with one from [http://www.ground-impact.com/libGL.so.1.2](http://www.ground-impact.com/libGL.so.1.2) fixed the problem. so it seems like i've got a completely working graphics card. woohoo. i've also realised why many people hate X so much...
systems software should *not* "work in mysterious ways"!

---

### Post by roger peppe on 2006-07-20
PS thanks very much for the help! It's been much appreciated.

---

### Post by mlind on 2006-07-20
> **roger peppe said:**
> PS thanks very much for the help! It's been much appreciated.

Yeah, no problem. Glad you got it sorted out.

---

