---
title: "screen tearing problem on a compaq evo n600c ati radeon mobility m6 LY"
date: 2011-01-20
forum: Multimedia Software
---

### Post by n600c on 2011-01-20
[SIZE=2]Hi all[/SIZE]

been using ubuntu since 9.10
and am now using 10.10

though as the title states i've got a video tearing issue
the driver being used as per what sudo lshw -c display mentions
is radeon

  *-display               
       description: VGA compatible controller
       product: Radeon Mobility M6 LY
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: agp agp-2.0 pm vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=66 mingnt=8
       resources: irq:11 memory:48000000-4fffffff ioport:3000(size=256) memory:40200000-4020ffff memory:40220000-4023ffff

I've check the forum for the passed 5 days for a solution about tearing
and all i've ever found was for newer ati cards or nvidia
or the solutions to fix the tearing never worked
before 10.10, (i think it was in 9.10)
i had done some change to Xorg.conf which had fixed that issue
(and now ubuntu 10.10 no longer uses the Xorg.conf file)
but for the life of me i cant remember where i got the info from
or what i had typed into the search function to fix this issue

so if anyone can please help me figure this out, i'd really appreciate it

thank you in advance for any and all help

---

