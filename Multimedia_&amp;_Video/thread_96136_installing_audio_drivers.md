---
title: "installing audio drivers"
date: 2005-11-28
forum: Multimedia &amp; Video
---

### Post by duvel on 2005-11-28
Although Alsa 1.0.3 introduced support for my audio chip, I am unable to get any SP/DIF output. The computer manufacturer (Shuttle) sent me a link to Linux drivers and I have downloaded them. When I run the install script, I get this result:

```
configure: error: this packages requires a curses library
make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.
bzip2: Can't open input file test.wav.bz2: No such file or directory.
cp: cannot stat `test.wav': No such file or directory
Remove Folder.....
./install: line 89: alsaconf: command not found

```

Also, when I run lshw, I get this result for multimedia:

 ```
*-multimedia
             description: Multimedia audio controller
             product: IXP150 AC'97 Audio Controller
             vendor: ATI Technologies Inc
             physical id: 14.5
             bus info: pci@00:14.5
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ATI IXP AC97 controller
             resources: iomemory:ec205000-ec2050ff irq:17

```

Wouldn't this seem to indicate that there is already a driver?

Thanks.

---

### Post by duvel on 2005-11-29
Could someone please respond to this message? It is really frustrating having no sound _and_ no help.

Thanks.

---

### Post by Smaskens on 2005-12-19
Install libncurses5-dev with Synaptic. This helps for curses library problem.

---

