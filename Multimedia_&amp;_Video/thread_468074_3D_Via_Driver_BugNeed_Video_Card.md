---
title: "3D Via Driver Bug/Need Video Card?"
date: 2007-06-08
forum: Multimedia &amp; Video
---

### Post by wmichaelb on 2007-06-08
Recently, my mother board died suddenly. So I purchased and installed a PC Chips M861G mobo with a Sempron proc, largely because it was inexpensive and accepted the same DDR memory that I'd had in the original mobo. Since I had to reinstall the OS anyway, I upgraded to Feisty. 

Suddenly, whenever I was listening to internet radio and the screensaver kicked in, the system froze. I had no way to deal with this other than to force a reboot by shutting down the power. So far I've been lucky and not corrupted anything that way; but I did some research on the bug report page, and found one that seems to be related to my problem. It seems that there is a known bug with the drivers for the Via chipset that crashes the system whenever a 3D application tries to run.

So my questions are these:

1.) Is there an inexpensive video card that is known to work with 3D applications on Ubuntu? It doesn't look like the bug is going to get fixed anytime soon.

2.) If I do install said video card, do I need to reinstall the entire bleeping system? Or can I simply install a driver? If so, how?

I'm running the above mobo with an 80GB IDE HD, and 1 GB of RAM, if it makes any difference. 

Thanks in advance!

---

### Post by dannyboy79 on 2007-06-08
> **wmichaelb said:**
> Recently, my mother board died suddenly. So I purchased and installed a PC Chips M861G mobo with a Sempron proc, largely because it was inexpensive and accepted the same DDR memory that I'd had in the original mobo. Since I had to reinstall the OS anyway, I upgraded to Feisty. 

Suddenly, whenever I was listening to internet radio and the screensaver kicked in, the system froze. I had no way to deal with this other than to force a reboot by shutting down the power. So far I've been lucky and not corrupted anything that way; but I did some research on the bug report page, and found one that seems to be related to my problem. It seems that there is a known bug with the drivers for the Via chipset that crashes the system whenever a 3D application tries to run.

So my questions are these:

1.) Is there an inexpensive video card that is known to work with 3D applications on Ubuntu? It doesn't look like the bug is going to get fixed anytime soon.

2.) If I do install said video card, do I need to reinstall the entire bleeping system? Or can I simply install a driver? If so, how?

I'm running the above mobo with an 80GB IDE HD, and 1 GB of RAM, if it makes any difference. 

Thanks in advance!

No you wouldn't have to reinstall teh system, you should NEVER EVER have to reinstall ever. Hell, I changed my motherboard and cpu and still didn't need to reinstall ubuntu!!!!!


If all you need is a cheap vid card, go with an Nvidia chipset for sure. I bought the XFX GeForce 6200 128mb DDR ram, it's got vga, dvi, and s-vid out. I think it was $39.99 after rebates. That was awhile ago.

Check this out, [http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=2844188&Sku=P450-7894](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=2844188&Sku=P450-7894)

it's got 64mb less ram but it's GDDR2 versus only ddr. Also, it supports 256 with Turbocache which I think means that it can share your system ram, not sure though. It's only $24.99 after rebate and I can gurantee that it'll work with the nvidia-glx-new driver from the repo's Which is basically the proprietary 9755 nvidia driver. That's of course PCIe, so you need to make sure you have got that but it sounds like your system is older, so you may have to go with AGP, that would b here:
[http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=697013&CatId=694](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=697013&CatId=694)
but that doesn't have dual heads (2 monitor support via vga or dvi, it does have tv-out though) that's only 34.99 (no rebates), I believe that card would use the nvidia-glx from the repo's which is the 9631 nvidia driver.

---

### Post by wmichaelb on 2007-06-08
Thank you, DannyBoy! Your comment about not reinstalling intrigues me; I tried to reboot my system after installing the new mobo, and it would absolutely not boot. I forget the exact error message, but it sounded like a missing driver. I believe that this board has a PCI slot or two, so the GEForce 6200 should work. I'll look into it.

---

### Post by dannyboy79 on 2007-06-09
well both those I showed you are NOT for PCI slots, they were PCIe (which is PCI Express) or AGP so again make sure you get the correct card. if you don't have either PCIe or AGP, than your last resort would be PCI, if it's just for basic 3d acceleration. Also, think about it, if you changed your bios  BUT not your hard drive, than the reason it didn't boot certainly was not a missing driver as you didn't change anything on the hard drive! So it probably didn't boot IF your hard drives were recognized differently when you hooked them to the MB, then you would have just needed to modify your menu.lst which is a grub config file. OR it could be other reasons but we could have gotten to boot, either from help oin the forums or in the irc channel.

---

