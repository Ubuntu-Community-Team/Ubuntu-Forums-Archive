---
title: "Screw my ATI card: Getting replacement. What NVIDIA should I get?"
date: 2007-03-09
forum: Multimedia &amp; Video
---

### Post by wulfhound on 2007-03-09
After dealing with every Edgy Xubuntu guide I could find, I can't get my ATI driver to run FLGRX or FGLRX (rest assured I typed it right when it counted. It's 3:20 am. I am not looking it up this second LOL)

I got the Mesa thingy coming up still, and tried over and over (from clean installs of Xubuntu, no less) to make it work. I can't work with a refresh rate of 60 hz.

So...

What I need to do with my card is NOT play video games. I need it to watch movies I download (Stargate Atlantis)....I also do make music videos but that's covered if I can at least watch the movies. I also of course, need it to work with Xubuntu Edgy. If I have to upgrade to Feisty, that's cool too.

Basically...I need an honest opinion on a tried and true Nvidia card that is a "low end model" meaning I don't have a TON of money (around 300 coming to me from taxes, I know, woo hoo....sigh). I'd prefer to buy a router with that money too, but I realize, just because I don't need high end doesn't mean the card's going to be cheap. 

I've got 2GB ram, I run a Via chipset....I know, I didn't build the thing, my ex-fiance did. Right now my video card is an ATI Radeon 9000. I think that's a separate one LOL...I'm not sure. I can look farther into that if I have to.

I just can't stand this screen anymore. Does it matter what my monitor is? I didn't think it did but let me know if it does.

Thanks,

Sandaili

---

### Post by renzokuken on 2007-03-09
i have a nVidia Geforce 6200 that runs all movies and stuff fine with no lag. that cost me £40 about 6 months ago or more.

you can get dirt cheap 7600 cards now. with 256mb spec. just make sure you check whether you need an AGP or a PCI-E card before you buy

---

### Post by Erlander on 2007-03-10
I've fitted a Gigabyte 7600 GS AGP with 256 Mb in the last week.  Heatsink only (no fan and therefore quieter).  Took me a few tries to set it up correctly but I am very pleased with it now.

Rob

---

### Post by mrreality13 on 2007-03-10
> **Erlander said:**
> I've fitted a Gigabyte 7600 GS AGP with 256 Mb in the last week.  Heatsink only (no fan and therefore quieter).  Took me a few tries to set it up correctly but I am very pleased with it now.

Rob

I have the 256 pci-e version and i love it for the $$
in a biostar 939 geforce 6100//2 gigspc3200/x2 4200+

---

### Post by tseliot on 2007-03-10
> **sandaili said:**
> After dealing with every Edgy Xubuntu guide I could find, I can't get my ATI driver to run FLGRX or FGLRX (rest assured I typed it right when it counted. It's 3:20 am. I am not looking it up this second LOL)
There's no need to use fglrx.

Your card will work with the open source driver.

Set the driver to "radeon" in the Section device of your /etc/X11/xorg.conf and then restart the Xserver.

That's all.

> **sandaili said:**
> I got the Mesa thingy coming up still, and tried over and over (from clean installs of Xubuntu, no less) to make it work. I can't work with a refresh rate of 60 hz.
sudo dpkg-reconfigure xserver-xorg

select the radeon driver, then press ENTER when you don't know the answer to a question.

When it asks you about your monitor specs, select "Advanced" and set the vertical and horizontal refresh rate.

if that doesn't work you might want to use a modeline.

---

### Post by Ryguy085 on 2007-03-18
I was having a lot of problems getting my ATI X800GT card working. Finally found a program called ENVY. Used it and the "Install the ATI Driver manually" option. Had fglrx up and running in no time at all. Beryl was then up and running shortly after. No problems since then. Go give that a try.

---

