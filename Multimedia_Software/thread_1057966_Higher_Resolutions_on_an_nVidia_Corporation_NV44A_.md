---
title: "Higher Resolutions on an nVidia Corporation NV44A [GeForce 6200] (rev a1)"
date: 2009-02-02
forum: Multimedia Software
---

### Post by shields on 2009-02-02
When I installed 8.04 on my machine, the video worked very well. I had very high resolution options, including my desired 1024X768. Then -- seemingly out of the blue -- those options disappeared. 800X600 was the highest I can select. Good night -- it looks like Windows 3.1. :(

I have looked all over these forums for a solution to this problem and have found and implemented dozens. But none that I tried work. Instead they probably made matters worse. I tried everything from enabling hardware drivers to downloading specific nvdia drivers to installing EvnyNG. That was a mistake. It lowered my options to make 640X480 my best resolution.  I also have fruitlessly tried the "sudo dpkg-reconfigure -phigh xserver-xorg" The best I can get is 800X600.  Even editing xorg.conf and placing 1024X768 in the DISPLAY subsection was unproductive.

Listing PCI devices (though my card is an AGP) reveals that my card reads:
```
01:00.0 VGA compatible controller: nVidia Corporation NV44A [GeForce 6200] (rev a1)
```

Has anyone managed to restore the high resolutions I originally had using this card? I could just reinstall 8.04, but that sounds too much like a suggestion from Microsoft.

Thank you.

---

### Post by shields on 2009-02-03
Oh well -- I did the whole reinstall, and the high resolution was not available this time. Same version. Same CD. Weird.

So I installed Kubuntu and not only do I get the high resolutions, my audio works without difficulty. I'd really like to stick with Ubuntu, but I just don't have the patience to dumb around with it on that machine.

---

### Post by shields on 2009-02-11
OK - this time I installed after booting to the live CD. The resolution is 1024x768, something I could not get when installing straight from that same CD.

Weird. But it works.

---

### Post by shields on 2009-04-04
So this morning, when I turn on the PC, the highest resolution is 800X600.

Hmmm...
Options:
[LIST=1]
[*]Dumb around with the settings some more
[*]Replace the video card
[*]Do yet another reinstall
[*]Install Windows 7 and play with it
[*]Dig up my old XP CD
[/LIST]

I am leaning toward moving my attention from Ubuntu to Windows 7. It's pretty cool, and probably no more frustrating than this has been.

---

### Post by shields on 2009-05-10
Well -- I've been talking to myself through this thread, but in case I need this information again, I will post the solution. :)

The problem was the monitor. Somehow it didn't like the high resolutions I was requesting. A different monitor fixed the problem. :KS

Thanks for all the suggestions!  ;)

---

