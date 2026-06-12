---
title: "Regza 37Z3030DB, nVidia 6200 and Foxconn 661FX7MJ-RSH mobo - edges of screen missing."
date: 2008-09-12
forum: Multimedia Software
---

### Post by tedrogers on 2008-09-12
Hi all,

Asking for help here is my last ditch attempt, as I've tried loads but can't seem to fix this problem.

I've tried using a range of modelines from mythtv.org, edited the xorg.conf to include the appropriate Vert and Horiz lines - but all to no avail.

No matter what resolution I select in X, I cannot get it to show me the whole screen. Some of the top is missing, as are the bottom and sides of the screen.

Changing resolutions in X windows provides a range of refresh rates to choose from for certain (but not all res's), but none of them will allow me to see the full screen.

I'm connecting the 6200 gfx card to the HDMI connector on my Toshiba 37Z3030DB Regza Z LCD TV using a DVI to HDMI cable. This cable works fine with my other computer running an ATI X1950 card...so I know it works.

I also tried an old GeForece 3 gfx card, but this didn't show up at all - blue screen on the TV the whole time - even with a different OS like Fedora 9.

The weird thing is that the problem also exists in the BIOS / POST screen of the Foxconn 661FX7MJ-RSH motherboard / 6200 gfx card. The edges of the POST screen are missing, as are they when you go into the BIOS menu. Does this mean it is the graphics card or the mobo?

I guess I will try the X1950 with the Foxconn tonight to see if I can elimiinate the 6200 or the mobo, but apart from that I don't know what else to try.

All I want to do is run Elisa as a media centre!

Any help appreciated.

Thanks.

---

### Post by tedrogers on 2008-09-25
Well I have now tried a couple more GFX cards and they all do the same thing...(ATI X1950, nVidia 6400, nVidia 7300GS) so all I can assume now is that it is the motherboard that is acting peculiarly with the LCD tv.

I'm totally lost here and have NEVER seen anything like this in 20 years of messing about with computers.

I don't suppose anyone else will have any ideas...but its worth a try.

HELP!

---

### Post by SiHa on 2008-10-01
I think your problem here isnt't the graphics cards, but more the fact that your monitor is a TV.

**All** TV's overscan. That is to say that they display the picture slightly larger than the visible screen area. This is to cut off the ragged edges and teletext that's sent in the VBI. God knows why but even modern LCD panels do this.

If you're lucky there will be a service menu where you can turn off overscan (I think It's sometimes called 'truevision' or something like that). There is on My panasonic anyway.

AFAIK there is **no** way to correct this from the PC using a digital output like DVI. If you have S-Video, composite or component in/out, you could try that instead. Install Nvidia-Settings, and reboot with the one of these connected in place of the DVI. When you run the above, there should be an overscan slider that you can adjust to get the edges of the screen visible.

I must admit, I only use Mythtv on the TV, so leave the overscan on, because I only found the option to turn it off after I had adjusted the Myth GUI to display on the visible porton only. The desktop still has no edges!

Cheers,

Simon

---

### Post by tedrogers on 2008-10-02
I narrowed this down to the motherboard actually.

I tested the gfx card with an Asus mobo system and no problems.

The same card in the Foxconn mobo and no edges, in POST, BIOS or with Myth / Win XP installed.

Interestingly though in XP the nVidia overscan is much more comprehensive, so I was able to shrink the screen. In Mythbuntu, the nVidia overscan features are less comprehensive and whilst I was able to make the screen smaller the best I could get it was too small so the edges of the screen were black, but at least I could see what I was doing!!

New mobo on the way in the post...so fingers crossed it will sort it.

Thanks for the reply.

---

### Post by SiHa on 2008-10-02
Well how the mobo affected the overscan I'll never know - glad you're on the way to getting it sorted though.

---

### Post by tedrogers on 2008-10-03
I know, it is very strange. I cannot explain it even after being embroiled in trying to fix it for all this time.

I guess it is just one of the inexplicable "nuances" that certain hardware posses.

---

