---
title: "[SOLVED] Need to change graphics settings"
date: 2008-02-16
forum: Multimedia &amp; Video
---

### Post by K3l3v on 2008-02-16
Hello.

My computer goes through a 'normal' boot-up routine (Bios loads, POSTs, Grub loads, and the system acts like it's coming online), but when it's time for X to load (and the gui login screen to come up), I get a "monitor not detected" warning and my screen goes blank.

I'm running Ubuntu 7.10 on an nForce3-a board with a gForce video card.

Everything had been good until 1.5 mo's ago.  I traced the problem to a dead Power supply.  After replacing the supply, the bios would not recognize any HDD's or DVD/CD ROM drives.  Got that problem fixed, and got the Bios to recognize components.

I put the HDD in a different comupter (emachines T2080) while checking components.  I know the video settings got set to something different then.

Anyone have any idea how to fix this?

Thanks.

---

### Post by overdrank on 2008-02-16
> **K3l3v said:**
> Hello.

My computer goes through a 'normal' boot-up routine (Bios loads, POSTs, Grub loads, and the system acts like it's coming online), but when it's time for X to load (and the gui login screen to come up), I get a "monitor not detected" warning and my screen goes blank.

I'm running Ubuntu 7.10 on an nForce3-a board with a gForce video card.

Everything had been good until 1.5 mo's ago.  I traced the problem to a dead Power supply.  After replacing the supply, the bios would not recognize any HDD's or DVD/CD ROM drives.  Got that problem fixed, and got the Bios to recognize components.

I put the HDD in a different comupter (emachines T2080) while checking components.  I know the video settings got set to something different then.

Anyone have any idea how to fix this?

Thanks.

HI and have you tried to reconfigure your xorg. You can use this command ```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by benerivo on 2008-02-16
Does it do the same when you boot the ubuntu live cd?

---

### Post by K3l3v on 2008-02-16
Thanks for the quick reply...

1.  I have tried to reconfigure the X server, but I used

dpkg-reconfigure xserver-xorg

as opposed to the script you listed.  Would that make a difference.

2.  No, it does not do the same thing with the live CD.  In fact, I am using the same computer with the live CD to make this reply right now.

Again, thank you for your quick reply.

---

### Post by overdrank on 2008-02-16
> **K3l3v said:**
> Thanks for the quick reply...

1.  I have tried to reconfigure the X server, but I used

dpkg-reconfigure xserver-xorg

as opposed to the script you listed.  Would that make a difference.

2.  No, it does not do the same thing with the live CD.  In fact, I am using the same computer with the live CD to make this reply right now.

Again, thank you for your quick reply.

HI and I believe the geforce 3 will use the nvidia legacy driver, and you could also try Envy
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)
So you may search synaptic manager for the nvidia driver and then try and reconfigure your xorg. The phigh tag just acts as automatic

---

### Post by K3l3v on 2008-02-16
Woohoo!  The problem is fixed!

I tried the code you suggested: sudo dpkg-reconfigure -phigh xserver-xorg  and everything worked.  I am now typing this reply on the fixed system.

Thanks again!

---

### Post by overdrank on 2008-02-16
> **K3l3v said:**
> Woohoo!  The problem is fixed!

I tried the code you suggested: sudo dpkg-reconfigure -phigh xserver-xorg  and everything worked.  I am now typing this reply on the fixed system.

Thanks again!

Great and good luck! :KS

---

### Post by lazerdave on 2008-02-18
I've been having the same problem.  I have no clue on what card I'm using but when I do 

sudo dpkg-reconfigure -phigh xserver-xorg

I get 

lazerdave@linux-server:~$ sudo dpkg-reconfigure -phigh xserver-xorg
FATAL: Error inserting battery (/lib/modules/2.6.22-14-generic/kernel/drivers/acpi/battery.ko): No such device
FATAL: Error inserting battery (/lib/modules/2.6.22-14-generic/kernel/drivers/acpi/battery.ko): No such device
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20080217223526
FATAL: Error inserting battery (/lib/modules/2.6.22-14-generic/kernel/drivers/acpi/battery.ko): No such device

This is not a laptop system.

I just moved it from a Sony LCD monitor to an NEC XE21.  Going through System>Administration>Screens And Graphics, none of the seemingly correct options work.



> **K3l3v said:**
> Woohoo!  The problem is fixed!

I tried the code you suggested: sudo dpkg-reconfigure -phigh xserver-xorg  and everything worked.  I am now typing this reply on the fixed system.

Thanks again!

---

