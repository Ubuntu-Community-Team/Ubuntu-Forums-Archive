---
title: "cheese stops working"
date: 2011-04-09
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by beew on 2011-04-09
It was working last week but after one week of updates it stops working. When  it opens all its shows is a bunch of coloured horizontal stripes. (Cheese works fine in Maverick for same machine)  

So far after a week of updates webcam stop working, wireless stops working, are we getting really closer to final release?? :confused:

This is the graphic card's info
> *-display               
       description: VGA compatible controller
       product: RS690M [Radeon X1200 Series]
       vendor: ATI Technologies Inc
       physical id: 5
       bus info: pci@0000:01:05.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=64
       resources: irq:18 memory:d0000000-dfffffff memory:cfdf0000-cfdfffff ioport:9000(size=256) memory:cfe00000-cfefffff



---

### Post by beew on 2011-04-09
Ok, I am pretty sure that the culprit is the  radeon driver. Just ran the same installation of 11.04 in another machine with a Nvidia card (using the nouveau driver) and cheese was working fine (I installed 11.04 in an external drive so I can test it on different machines and hardwares)

P.S. the nouveau driver is still nowhere as smooth as it is in Maverick.

---

### Post by beew on 2011-04-09
There is something more. If start cheese at the launcher somehow it kills the internet (I am using a usb wireless card with driver rtl8187 because the wl driver cannot be installed for some reasons) Trying to start the terminal afterwards it shows up as a white box and typing wouldn't work. Moreover somehow the shut down button is disabled so have to do a hard reboot.

After rebooting I started cheese from the terminal, there was no error message but Compiz crashed.

What the ??? Natty has more problems than Unity..

---

### Post by rburkartjo on 2011-04-09
working okay on my end

---

### Post by beew on 2011-04-09
What is your graphic card?

---

### Post by beew on 2011-04-10
It turns out to be a kernel problem. The kernel has not been upgraded  properly because I have a dual boot and for some reason Maverick (which  controls grub) has not detected the kernel upgrade in Natty.

Updated grub in Maverick and now problem is solved. Cheese works again. I wouldn't have thought of that!
[http://ubuntuforums.org/showthread.php?t=1725539&page=2](http://ubuntuforums.org/showthread.php?t=1725539&page=2)

---

