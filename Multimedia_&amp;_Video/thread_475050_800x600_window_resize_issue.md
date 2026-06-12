---
title: "800x600 window resize issue"
date: 2007-06-15
forum: Multimedia &amp; Video
---

### Post by rorytheherb on 2007-06-15
Hi all (new to linux)

I am running Ubuntu Studio i386 on a pc with a diamond agp video card.  when i boot i can see the boot verbiage until the login screen appears.  the colors are a mess and i type in my username, enter, password, enter, and then i get proper 800x600 resolution.  i believe during the login it is going to a higher resolution my card or monitor doesn't support.  is there a way to force ubuntu (or the agp card?) to stay at 800x600?  

that issue is tolerable as it is, but when i am running certain apps (Ardour gtk2, e.g.)  i cannot resize the windows to fit on my screen.  this prevents me from using the software because there is no way to even move some windows such that i can press the buttons i need!  is there a way to split the toolbars etc so they are on multiple windows which could then be sent to other workspaces?  

I bet i need to install some type of agp driver to solve this problem... it seems like more than a bug that went overlooked-- i'm sure the software was tested at 800x600 resolution to see that everything would run smoothly!

any help would be appreciated... i am eager to get started on my projects again!

thanks,
Rory

oh and here is the display portion per  "sudo lshw":

  *-display
                description: VGA compatible controller
                product: NV5 [RIVA TNT2/TNT2 Pro]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@01:00.0
                version: 11
                size: 32MB
                width: 32 bits
                clock: 66MHz
                capabilities: vga bus_master cap_list
                configuration: latency=32 maxlatency=1 mingnt=5
                resources: iomemory:d4000000-d4ffffff iomemory:d2000000-d3ffffff

---

