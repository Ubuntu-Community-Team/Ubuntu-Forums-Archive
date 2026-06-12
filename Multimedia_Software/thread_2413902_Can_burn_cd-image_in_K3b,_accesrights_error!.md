---
title: "Can burn cd-image in K3b, accesrights error?!?"
date: 2019-03-03
forum: Multimedia Software
---

### Post by astrogator2 on 2019-03-03
I've been trying to burn a cd-image to an empty cd, but keep getting an error with regurgitation of the cd without any action.  It says it doesn have accesrights to open the device, and I have to change device-settings in K3b to solve it. Burning a dvd image is no problem, so it doesn't make any sense to me.
Debug output:
 [FONT=Hack]Devices[/FONT]
 [FONT=Hack]-----------------------[/FONT]
 [FONT=Hack]ATAPI DVD A  DH20A4P 9P53 (/dev/sr0, CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R DL) [DVD-ROM, DVD-R sequentieel, DVD-R Dual Layer sequentieel, DVD-R Dual Layer Jump, DVD-RAM, DVD-RW met beperkte overschrijving, DVD-RW sequentieel, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Beperkte overschrijving, Layer Jump] [%7][/FONT]
 [FONT=Hack]
[/FONT]
 [FONT=Hack]System[/FONT]
 [FONT=Hack]-----------------------[/FONT]
 [FONT=Hack]K3b Version: 18.4.3[/FONT]
 [FONT=Hack]KDE Version: 5.47.0[/FONT]
 [FONT=Hack]Qt Version:  5.11.1[/FONT]
 [FONT=Hack]Kernel:      4.18.0-15-generic[/FONT]
 [FONT=Hack]
[/FONT]
 [FONT=Hack]Used versions[/FONT]
 [FONT=Hack]-----------------------[/FONT]
 [FONT=Hack]cdrecord: 1.1.11[/FONT]
 [FONT=Hack]
[/FONT]
 [FONT=Hack]cdrecord[/FONT]
 [FONT=Hack]-----------------------[/FONT]
 [FONT=Hack]/usr/bin/wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.[/FONT]
 [FONT=Hack]/usr/bin/wodim: Resource temporarily unavailable. Cannot get mmap for 12587008 Bytes on /dev/zero.[/FONT]
 [FONT=Hack]TOC Type: 1 = CD-ROM[/FONT]
 [FONT=Hack]
[/FONT]
 [FONT=Hack]cdrecord command:[/FONT]
 [FONT=Hack]-----------------------[/FONT]
 [FONT=Hack]/usr/bin/wodim -v gracetime=2 dev=/dev/sr0 speed=48 -sao driveropts=burnfree -data -tsize=158720s -[/FONT]

---

### Post by speartip on 2019-03-21
[SIZE=2][FONT=arial]Try running the following commands in a terminal & try again:
```
cd /usr/bin
```
then:
```
[COLOR=#000000]sudochmod -v 4711 cdrdao && sudo chmod -v 4711 wodim &&sudo chmod -v 0755 growisofs[/COLOR]
```

[/FONT][/SIZE]

---

