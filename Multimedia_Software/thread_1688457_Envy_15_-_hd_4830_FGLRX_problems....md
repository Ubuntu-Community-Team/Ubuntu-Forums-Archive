---
title: "Envy 15 - hd 4830 FGLRX problems..."
date: 2011-02-15
forum: Multimedia Software
---

### Post by fxRichard on 2011-02-15
I have an HP Envy 15 with the 4830 ATI card in it and when I use any of the prorietary fglrx drivers they all provide me with black screens on boot.  I was however able to get 11.1 and 10.12 drivers to boot ONE time each at some point however since then they just hang at boot with a black screen.  The open source Ubuntu drivers work but they are very choppy and kill the battery life.  This is for Ubuntu 10.10 x64.  Any input??  This is driving me crazy, bought this laptop and can't even use it until this is fixed, thanks.

---

### Post by lukeiamyourfather on 2011-02-15
Have you tried the binary drivers directly from AMD? It might be worth trying newer (and older) drivers to see if they have the same issue. Depending on how much you want to get into troubleshooting you could try another distribution like Ubuntu 10.04 LTS.

---

### Post by fxRichard on 2011-02-15
I have tried the ones recommended by Ubuntu to start.  I have also tried the following:

Catalyst 10.3
Catalyst 10.10
Catalyst 10.12
Catalyst 11.1

When attempting each driver I would remove the currently installed ones as follows:

```

sudo dpkg --purge fglrx-modaliases fglrx-dev fglrx-amdcccle fglrx

```

Then I would perform:
```

sudo ./ati-driver-installer-*-x86.x86_64.run --buildpgk Ubuntu/maverick

sudo dpkg -i fglrx*.deb

```

Before I attempted installing the proprietary drivers I removed the default Ubuntu drivers via:
```

sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon

```

Once I installed the drivers I would run:
```

sudo aticonfig --initial -f

```

---

### Post by Baszczo on 2011-07-13
Hi. I have this problem to (Ubuntu version doesn't metter). It's strange that fglrx works but only to first rebot :( Any idea to fix it?

I found some information at: [http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide)
> This has been tested using Ubuntu 10.04 64-bit on a ATI Radeon HD 4830 (HP Envy 15-1060ea). It's worth noting that I had to disable TLS (aticonfig --tls=0) to get things to stay stable!
If you've properly installed the driver, but experience problems when starting the X server, such as hanging, black/white/gray screen, distortion, etc., your system BIOS may have a buggy ACPI implementation. To work around, press Ctrl+Alt+F1 to get to a terminal (or failing that, boot to recovery mode) and run:
$ sudo aticonfig --acpi-services=off
But this don't resolve my problem.

Bug report:
[http://ati.cchtml.com/show_bug.cgi?id=203](http://ati.cchtml.com/show_bug.cgi?id=203)

---

### Post by juampaflo on 2011-09-10
Hi!
I have exactly the same problem with my HP Envy 15-1050ca (amd mobility radeon hd 4830).

I try:
[INDENT]Ubuntu 10.10 32bits, 11.04 32bits and 11.04 64bits
Catalyst 10.12, 11.4 (through Restricted Drivers Manager) and 11.8
[/INDENT]The same problem on them.

I try the above solutions in the thread with no success.
If anyone find out how to solve this please share the solution!
Sorry the English. I'm Spanish native.

---

### Post by juampaflo on 2012-03-21
Hi!

Has anyone found a solution to this problem?

I tried Ubuntu 11.10 and AMD Catalyst™ 12.2 Proprietary Linux x86 Display Driver whit no success.

Thank!

---

### Post by EricRanders on 2012-05-30
I'm also having this problem, I found this interesting bug report...

[http://ati.cchtml.com/show_bug.cgi?id=203](http://ati.cchtml.com/show_bug.cgi?id=203)

---

