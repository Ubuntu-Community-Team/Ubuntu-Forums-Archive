---
title: "question re: Nvidia 6200 PCI-x compatibility w/ Dapper"
date: 2006-06-07
forum: Multimedia &amp; Video
---

### Post by arc sol on 2006-06-07
i'm a bottom-feeder in the IT dept here, thus the assignment. i have this unit that i need to load Ubuntu on. the one problem i had before is that i can't get it to work with an ATI Radeon card (Radeon X550 PCI-x) circa Breezy Badger.

here are the specs:

mobo:Asus P5RD1-VM
proc: P4 LGA775 @ 2.66GHz
video: ATI Radeon X550 PCI-x
ram: 512mb DDR
hd: seagate IDE

the mobo has a built-in video card that i disabled thru the BIOS (i.e. placed the PCI port as the 1st display device). at first i can't get thru the Hotplug subsystem during bootup but i managed to bypass that thru a guide i found here. the problem that appeared is that X can't start. after reading the error message i *think* Ubuntu isn't compatible with the video card.

now the higher-ups decided to get a Nvidia 6200 PCI-x to plug into that Asus mobo (P5RD1-VM) to replace the ATI. any idea if this card will work with Dapper? any tips/things to watch out during/after installation? 

thanks a lot in advance for the kind souls who will reply.

---

### Post by tseliot on 2006-06-07
[QUOTE=arc sol]i'm a bottom-feeder in the IT dept here, thus the assignment. i have this unit that i need to load Ubuntu on. the one problem i had before is that i can't get it to work with an ATI Radeon card (Radeon X550 PCI-x) circa Breezy Badger.

here are the specs:

mobo:Asus P5RD1-VM
proc: P4 LGA775 @ 2.66GHz
video: ATI Radeon X550 PCI-x
ram: 512mb DDR
hd: seagate IDE

the mobo has a built-in video card that i disabled thru the BIOS (i.e. placed the PCI port as the 1st display device). at first i can't get thru the Hotplug subsystem during bootup but i managed to bypass that thru a guide i found here. the problem that appeared is that X can't start. after reading the error message i *think* Ubuntu isn't compatible with the video card.

now the higher-ups decided to get a Nvidia 6200 PCI-x to plug into that Asus mobo (P5RD1-VM) to replace the ATI. any idea if this card will work with Dapper? any tips/things to watch out during/after installation? 

thanks a lot in advance for the kind souls who will reply.[/QUOTE]
1) My father has a Nvidia Geforce 6200 PCI-E and it works great on Dapper livecd.

2) BTW I suppose that the ATI card can work on Ubuntu (both on Dapper and Breezy).

Try this: 

1) Boot in Recovery mode (you can select it from the GRUB menu almost as soon as you turn your computer.

In this way the xserver won't be started.

2) Reconfigure the Xserver:

```
dpkg-reconfigure xserver-xorg
```


and select the "vesa" driver when it asks you. If you don't know the answer to the other questions just press ENTER to use the default answer.

3) Restart your computer:

```
reboot
```


Boot as usual and you should be able to see the graphical interface (the desktop enviroment).

If that doesn't work, repeat the process I described above but this time set the driver to "vga" or "ati".

---

