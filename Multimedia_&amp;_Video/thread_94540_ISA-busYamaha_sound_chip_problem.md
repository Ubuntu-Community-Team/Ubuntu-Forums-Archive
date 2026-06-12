---
title: "ISA-bus/Yamaha sound chip problem"
date: 2005-11-24
forum: Multimedia &amp; Video
---

### Post by Entropia on 2005-11-24
I'm running Ubuntu 5.10 BB on a Toshiba Satellite 4000CDT. It installed ok and boots up fine, except the sound chip doesn't work. The machine has a working Yamaha OPL3-SA3 chip and I've been trying to call 'modprobe snd-opl3sa2' which should work ok but it doesn't (checked this one with Google). Instead it gives out an error like so:
```

root@belarus:/root# modprobe snd-opl3sa2
FATAL: Error inserting snd_opl3sa2 (/lib/modules/2.6.2.12-9-386/kernel/sound/isa/snd-opl3sa2.ko): No such device
FATAL: Error running install command for snd-opl3sa2

```
This indicates that Ubuntu doesn't find the ISA-bus on the machine. How can I fix it? :)

---

### Post by Entropia on 2005-12-09
Doesn't anyone have a solution?

---

### Post by mpvano on 2005-12-09
Hi:

I could be wrong, but I believe that your machine uses the older ISA architecture to connect the sound chip set to the bus, instead of the more modern internal PCI architecture. This means the chips act as if they are on an old style ISA card (even though they're on the main board.)

All of my older Toshibas that use that chipset have worked that way. Unfortunately, I don't use Ubuntu on any of them, but I can tell you more or less what the problem is from the way I set them up using other distributions.

ISA card interfaces are NOT self-configuring - you need to specify EXACTLY all the details of the interface to the drivers or they won't have any way to find the card.

In the old (!) days when ISA sound cards were common, linux releases used to come with a configuration program that would help you set up ISA card sound by trial and error, but I haven't seen anything like this in recent releases because ISA cards are so infrequently used today. Sadly, that probably means you need to know how to modify configuration files in the /etc directory directly.

For what it's worth, the most common port values for that sound card are as follows:
As described by Toshiba Device Manager (values are hex)
  Windows Sound System emulation IO               530-537
  Soundblaster Pro emulation IO                         220-22f
  FM Synthesizer for sound effects and midi       388
  Card control port                                               120
  MPU401 midi IO on game port                          330-331
  Joystick                                                               201
  Hardware interrupt                                             INT             5
  DMA controllers used                                         0,1


These would probably be good values to assume for your machine unless you have other information (it's usually all in the Toshiba printed manuals).

To get the modules to use these values, they need to be setup as "arguments" passed to the module loader. That happens by entering them correctly in the module configuration files in /etc/.

Here would be typical lines that do the setup (taken from my Satellite 315CDT when it was running RH 6.2 a few years ago).

WARNING! This setup is for the old OSS sound system modules only (the ones that do NOT start with "snd-") I can't help you with the corresponding lines for the ALSA drivers, but perhaps somebody else can provide that info. If not, I believe that the older OSS sound system is present in Ubuntu and still works just fine if it's set up properly.

alias sound opl3sa2
options opl3sa2 io=0x370 mss_io=0x530 mpu_io=0x330 irq=5 dma=1 dma2=0
alias midi opl3
options opl3 io=0x388

These lines would typically be placed into a file in the directory /etc/modprobe.d and then the "update-modules" command would be run to configure the system to start up properly.

You should be able to experiment with loading the modules manually using the modprobe command and giving these values on the command line of the appropriate modules as you load them, but again that may be beyond what you'd like to get into here....

I'm sorry, but I've never set up OSS modules on Ubuntu, so I can't be more specific - you'll need more help from someone else, or perhaps someone knows how to find the old debian sound configuration utility that used to do all this from menus for you....

Again, this information may not solve your problem, but hopefully it will get you pointed in the right direction if I've correctly diagnosed your problem.

Mario

---

