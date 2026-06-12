---
title: "Graphics on GA-MA78GM-S2H"
date: 2008-09-02
forum: Mythbuntu
---

### Post by xykevinr on 2008-09-02
Hi,

I bought a Gigabyte GA-MA78GM-S2H. Its an AMD 780G chipset board with built in ATI HD3200 graphics.

I'm trying to use it with 8.04.1 Mythbuntu (and all updates) and various levels of ATI catalyst drivers including the latest.

I've had various problems i've seen elsewhere - either corrupt Myth images (which go away when you run myth in a window), or crappy/no hardware acceleration. 

After days of messing about, I went to my local hardware shop, bought a NVIDIA card for about $30 (£16 for me). This worked straight away. 

I'd really like to go to the internal graphics - is anyone running on one of these boards and have everything working ? If so, could you post details of your catalyst version etc 

thanks, Kev

---

### Post by Andrew U.K. on 2008-09-03
I'm using the same motherboard but have not tried the drivers yet. But like you I'm using a nvidea card for t.v. out. 

Have you got the acpi working?
Cheers,
Andrew

---

### Post by xykevinr on 2008-09-03
In short no, haven't tried it. Bigger fish to fry.

Longer version. Upgraded to bigger hdd in my backend server the other day, whilst copying old files over had lid off box, decided to tidy desk while big copy was going on. Dropped a friggin screw onto the motherboard and fried it:icon_frown:. My MA78GM-S2H is a frontend only so it doesnt do anything until i fix the rear !

 :(

Maybe later....

---

### Post by Andrew U.K. on 2008-09-04
now that's the sort of thing that happens to me...

---

### Post by JugeHuge on 2008-09-04
I have Asus M3A78-EMH HDMI with 780G chipset which have integrated HD3200 connected on Panasonic plasma with HDMI

Don't use Catalyst 8.6, 8.7 and 8.8 drivers.. At least what i have tried. It will cause mosaic effect on mythtv menu or shows menu but no submenus.

i would suggest that you use repository fglrx driver.. it has it flaws also but currently it works best.

---

### Post by juicestain on 2008-09-04
> After days of messing about, I went to my local hardware shop, bought a NVIDIA card for about $30 (£16 for me). This worked straight away.

Which card exactly? I've got the same board as you and I'm getting some strange effects after I install to the latest Catalyst drivers. My refresh rates are wonky i think. 

Link to post with pic...
[http://ubuntuforums.org/showthread.php?t=906528](http://ubuntuforums.org/showthread.php?t=906528)

If your nvidia card works on a 120hz tv, then i'm gonna grab one and FINALLY watch some tv. hehe

---

### Post by Andrew U.K. on 2008-09-08
Hi juicestain
I'm using a nvidea MSI 8400GS 256MB DDR2 DVI VGA HDTV out PCI-E Graphics Card for my T.V. out. It cost about £23 at ebuyer.

Andrew

---

### Post by dsbw on 2008-09-08
Got it, tried every driver for the past several months, none worked.

Tossed it.

---

### Post by Crick on 2009-01-10
I have to register a big me too here as well. I would have spent 50-100 hours getting nowhere getting ANY fglrx driver to work after I had tried to upgrade to the latest. I got annoyed at the slow firefox scrolling and the tearing with DVD, thought it might have been fixed and worth upgrading the driver. I got back to my original 1920x1080 resolution once after 8 hours, but could not for the life of me get that back after that (thought that with a bit more effort I may have done).

It could have probably been easier if I had been prepared to do a full reinstall, but that would have probably involved at least as much time getting to where I was before.

I went out and bought an nvidia 9400GT and I got it working within an hour after my PC's case was closed. Works fantastically; great 3D, no tearing in DVDs, performance in Wine is far better.

Moral of the story: 
1. Backup your HDD before messing with finicky drivers if they are currently working - an hour invested there could save you fifty.
2. Buy AMD/ATI to support open source, and hope that given the documentation the developers can build drivers that will be near to the binary blob drivers by the next Ubuntu LTS release. That gives AMD over a year to get things working. I am not angry at AMD, I understand that difficult projects take time, and throwing more people at the problem will not solve it faster (see Mythical Man Month). They have demonstrated good faith so far; I will reserve judgment until the next LTS release.
3. In the meantime, be prepared to get a cheap nvidia card.

---

### Post by mogators on 2009-03-29
Add me to the list.  My graphics are scrambled on this board when running myth as well.  I can use the geometry to run the frontend, but the backend is still not configured right and I cant see it to even try to get it working.  Anybody know of a way to get the backend to display?  How do I go back to using fglrx as jugehuge suggested?

---

