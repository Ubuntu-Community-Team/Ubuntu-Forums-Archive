---
title: "So I installed this wireless card..."
date: 2009-07-19
forum: Networking &amp; Wireless
---

### Post by Dansid on 2009-07-19
I'm really new to Ubuntu; take this into consideration when you give an answer.  Today I seated a Netgear wireless-G PCI adapter, model WG311 into my desktop.  

Followed a bunch of guides and ended up installing a driver into the OS so it can talk to the card.  

The issue is every time I restart Ubuntu forgets the settings. I have to enter these two commands to get it up and running again:

sudo modprobe ndiswrapper
iwconfig

How can I go about having the system remember these settings so the web is available on the get-go?

P.S.  I don't really even know what those two commands that I enter are, let alone the process I went through to install the driver.  Please help me get this car locked into the start up.

Thankye kind.

---

### Post by cariboo on 2009-07-19
next time you start the computer type:

```
ndiswrapper -m
```

the above command writes an alias for wlan0 (default wireless device) into the module configuration file so that ndiswrapper kernel module is loaded automatically when this interface is used. Then you can type:

```
modprobe ndiswrapper
```

If you don't know what a command does, in a terminal type:

```
man modprobe
```

This command will tell you more than you want to know about the command. :)

---

### Post by Kraut~salat on 2009-07-19
ndiswrapper is a tool that lets you use Windows WiFI drivers with Linux. You give it a .inf file, which is the Windows driver and it will do some magic with it. Then you have to tell Linux to use ndiswrapper to supply the driver to the linux kernel. Drivers in Linux are called "modules". Modules can be loaded to the kernel via the modprobe command. The "modprobe ndiswrapper" command just loads the ndiswrapper into the kernel. This module simply is a wrapper (hence the name) for the Windows driver that makes to windows driver Linux compatible.

And yes, reading the man-pages is vital if you want to use Linux. Man stands for Manual. You read them via
man <any command/configfile/... here>

Try 
man man
for starters. You quit a man-page with 'q'.
man modprobe
will tell you everything about how to load kernel modules. basically every command line program has a man page, as do many config files and even system calls for C programmers.

---

### Post by Dansid on 2009-07-19
well thank you guys.  very helpful, gonna go try it out now.

have a good one.

---

### Post by Dansid on 2009-07-21
> **cariboo907 said:**
> next time you start the computer type:

```
ndiswrapper -m
```the above command writes an alias for wlan0 (default wireless device) into the module configuration file so that ndiswrapper kernel module is loaded automatically when this interface is used. Then you can type:

```
modprobe ndiswrapper
```If you don't know what a command does, in a terminal type:

```
man modprobe
```This command will tell you more than you want to know about the command. :)

After I enter ndiswrapper -m I get this warning: WARNING: All config files need .conf: /et/modprobe.d/ndiswrapper, it will be ignored in a future release.  
module configuration already contains alias directive

And then when I enter modprobe ndis wrapper it gives me a FATAL: error inserting ndiswrapper, this long link, and then that the operation is not permitted.  If instead I use sudo modprobe ndis wrapper, the internet indeed hooks up, but still, the settings aren't saved. 

Could someone please help me save this setting?

---

### Post by Kraut~salat on 2009-07-22
try adding
alias wlan0 ndiswrapper
to /etc/modules.conf.

Hopefully this will auto load ndiswrapper every time you boot up.

edit: check out the sticky thread in this forum dealing with ndiswrapper. Check the first port, at  the very end of number 4. There it says what you have to do to load ndiswrapper autmatically. Which is pretty much adding "ndiswrapper" to /etc/modules

---

