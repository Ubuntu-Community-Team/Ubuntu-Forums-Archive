---
title: "Jack/wineasio/reaper problem"
date: 2008-02-08
forum: Multimedia &amp; Video
---

### Post by jperrella on 2008-02-08
hey everyone. I'm brand new to linux, and basically am trying to get the audio app Reaper to run in Ubuntu because i'm fed up with m$. I followed a walk through on the Reaper forums, and basically am all set except for one tiny (hopefully) problem.

when i launch jack i get an error that says:

Cannot connect to JACK server as client.

then it shows this in the message box

[img]http://stashbox.org/79957/ss1.png[/img]

any help in figuring out the problem would be great.

I'm using a mac mini, and the setup created by this how-to: [http://www.cockos.com/forum/showthread.php?t=16786](http://www.cockos.com/forum/showthread.php?t=16786)

(please keep in mind that i am brand new to linux and need things spelled out very simply)

thanks

---

### Post by Burillo on 2008-02-20
try running qjackctl with admin piveleges (gksudo/kdesudo qjackctl)

also, do you have your kernel patched? check this with "sudo apt-get install linux-image-rt" in console window

OK, if you're brand new to linux, follow this one. First of all, launch a console window. If you don't know how - Alt+F2 (this will bring up Windows-like "Run..." dialog), type xterm and press enter. This will bring up XTerm window. type "sudo apt-get install linux-image-rt" without quotes. If it says it's already installed - good. If not - install and reboot. Then once you're up and running again, Alt+F2 and type "gksudo qjackctl" without quotes (i assume you're under GNOME. In Kase of KDE - type "kdesudo qjackctl" without quotes) and try again.

This "Operation not permitted" stuff usually relates to the need of admin priveleges for the operation to complete, so if you get one of these errors with other software - you can try running it with escalated priveleges. Though i STRONGLY advice you to use this technique ONLY in case of URGENT need! running everything with root priveleges is VERY DANGEROUS (that's what made Windows so vulnerable)!!!

---

### Post by kgi on 2008-02-20
Hi there.

Your problem is *probably* that you're trying to run jack in realtime mode (the "-R" flag), but you don't have sufficient permissions to do so.

Very briefly, running in realtime mode gets you better (lower) latency, at the cost of some computational efficiency (realtime kernels actually have worse throughput) and, in my experience, somewhat less stability.

Jack is wonderful, but debugging its foibles can be tough, especially if you're also trying to use wineasio. Here's a couple of additional tips; I hope they're useful.

The line that starts "/usr/bin/jackd ..." is the actual command that qjackctl is running. In other words, the GUI application isn't really an application, it's just a wrapper that runs a non-GUI application. You could just as easily open a terminal (say, xterm or konsole) and type the command and get the same result.

Now, to work out what the various options to jackd mean, you need to read the manual page. I usually just type "man jackd" in a terminal, but that's a bit crude, so you can also read the man pages in various browsers; for example, in konqueror, it would be '#jackd' or 'man:/jackd'.

This man page says:

> 
-R, --realtime 

 Use realtime scheduling. This is needed for reliable low-latency performance. On most systems, it requires jackd to run with special scheduler and memory allocation privileges, which may be obtained in several ways. The simplest, and least-secure method is to run jackd with root privileges. This means that all JACK clients must also run as root. With a Linux 2.6 kernel, ordinary users can run jackd and its clients using options of the realtime LSM. Linux 2.4 kernels need "POSIX draft capabilities" enabled (see the <linux/capability.h> include file). Using that method, ordinary users who invoke the daemon using jackstart, can later launch JACK clients without running them as root. See [http://jackit.sourceforge.net/docs/faq.php#a52](http://jackit.sourceforge.net/docs/faq.php#a52) for more information.


I would advise just getting jack working first before you mess around with getting realtime privileges. To do this, either just run the command without the '-R' flag, or do so in the GUI (there'll be an option in the setup to unselect the realtime option) .You might get some clicks in the sound, but jack should run.

Moreover, try adding the "unlock memory" flag (-u) to jackd; I've found that this sometimes helps with wine apps, but I don't pretend to know why.

In order to get realtime privileges, I think you'll need to install a realtime kernel and modify your /etc/security/limits.conf file; see, for example [https://help.ubuntu.com/community/UbuntuStudio/DapperPreparation]("https://help.ubuntu.com/community/UbuntuStudio/DapperPreparation")

Hope this helps.

---

### Post by kgi on 2008-02-20
Forgot to mention that these days, installing a realtime kernel is as simple as running:

```
sudo apt-get install linux-rt
```

Beware, however, that the most recently-installed kernel is usually the one that gets booted first, which is often not what you want. You may need to edit

```
/boot/grub/menu.lst
```

to control the default boot kernel.

I apologise if this all sounds terribly manual (editing config files, typing stuff in, etc). I am sure that modern distributions have nice shiny ways to do this, but I'm a bit old-school and find typing commands faster and less error-prone.

---

