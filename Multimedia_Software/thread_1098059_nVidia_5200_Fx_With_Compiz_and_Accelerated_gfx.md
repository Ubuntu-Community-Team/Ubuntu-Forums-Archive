---
title: "nVidia 5200 Fx With Compiz and Accelerated gfx?"
date: 2009-03-16
forum: Multimedia Software
---

### Post by tombom62 on 2009-03-16
I have tried everything I can think, searched the forums, and all kinds of stuff but I cannot get my nVidia card to work with 3d gfx or Compiz.  Has anyone else used this card on Compiz and 3d acceleration?  I really need it not only for the effects, but for games.  I have installed Compiz, and I have tried even just enabling "Extra" effects, (NOTE:  The "Custom" doesn't show up) but it says> Desktop effects could not be enabledAny help is appreciated.

thanks,
tombom:popcorn:

---

### Post by inobe on 2009-03-16
what version of ubuntu

what have you tried

what changes have you made

is this card connected to an agp 4x's slot and not 4/8x's

have you gotten all the updates

---

### Post by Therion on 2009-03-16
Have you installed the nVidia Restricted Driver?

---

### Post by tombom62 on 2009-03-16
> **inobe said:**
> what version of ubuntu

what have you tried

what changes have you made

is this card connected to an agp 4x's slot and not 4/8x's

have you gotten all the updates

intrepid.

all kinda stuff.  Like using an older driver thing, modifying xorg.conf according to some other posts i found

it's actually the pci version:(

yep.  

> Have you installed the nVidia Restricted Driver? 
I can't get the restricted drivers to install.

---

### Post by tombom62 on 2009-03-16
bump

---

### Post by Prof.Arronax on 2009-03-16
> **tombom62 said:**
> *intrepid*.

[I]all kinda stuff.  Like using an older driver thing, modifying xorg.conf according to some other posts i found

it's actually the pci version:(

yep.  

I can't get the restricted drivers to install.[/I]   

  Virtually the same problem here.  Oddly enough, on this "play" machine I had installed Ubuntu 7.04 (feisty, Gnome) and it worked fine. Wiped the drive and installed the current version (8.10 intrepid, Gnome) and I'm limited to 800x600, 256 colours and no desktop effects.  The NVidia type 64meg AGP or PCI card is capable of substantially more than that!  But neither of mine register properly with this version of the OS.

Are we overlooking something during the system install?

Thanks in advance.

---

### Post by Therion on 2009-03-17
Have you tried using Envy?

I hesitate to recommend this only because this is an unofficial route to installing your video driver and by using this method, when you get a kernel header update (and you will get one) the driver will, most likely, bork on you.

The solution is to drop to a Terminal and re-run Envy from the command line.  So, if you're okay with that, proceed with using Envy to install your driver and hope for the best.

Good luck!

[https://launchpad.net/envy](https://launchpad.net/envy)

---

### Post by tombom62 on 2009-03-17
ok, so I can try that, but it may ruin my video eventually?

---

### Post by tombom62 on 2009-03-17
tried and... failed

---

### Post by Prof.Arronax on 2009-03-17
> **Therion said:**
> [I]Have you tried using Envy?

I hesitate to recommend this only because this is an unofficial route to installing your video driver and by using this method, when you get a kernel header update (and you will get one) the driver will, most likely, bork on you.

The solution is to drop to a Terminal and re-run Envy from the command line.  So, if you're okay with that, proceed with using Envy to install your driver and hope for the best.

Good luck!

[https://launchpad.net/envy](https://launchpad.net/envy)[/I]     

Regrettably, that URL is dead. :(

---

### Post by tombom62 on 2009-03-17
no it's not.  but here's the envy homepage:
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

### Post by tombom62 on 2009-03-18
(bump)

---

### Post by kaibob on 2009-03-18
> **tombom62 said:**
> ...I can't get the restricted drivers to install.

I have an nVidia FX5200 card and it works fine in Hardy (8.04). It was immediately recognized and the restricted driver installed without a hitch. I did try to upgrade to Intrepid but had problems with the FX5200 and went back to Hardy. So, if all else fails, you may want to consider Hardy. 

BTW, I did try Compiz, and it worked fine. Also, I checked 3d acceleration with GLX gears and that worked fine too. I do have a very popular Dell monitor, which I think may make things easier.

Anyways, I wish I had more to offer in the way of advice but consider Hardy if no one else can help. Good luck!

---

### Post by tombom62 on 2009-03-18
ok.  isn;t hardy pretty similar as far as performance?

---

### Post by kaibob on 2009-03-19
> **tombom62 said:**
> ok.  isn;t hardy pretty similar as far as performance?

Yeah, I think they're pretty close. If anything, Hardy seemed just a bit faster to me.

---

### Post by tombom62 on 2009-03-19
> **kaibob said:**
> Yeah, I think they're pretty close. If anything, Hardy seemed just a bit faster to me.

OK, I might do that.  my only thing is I also have windows, and I have some important stuff in there and I almost accidentally deleted it installing intrepid, then I did it with wubi.  So now I have intrepid with wubi.  I was gonna get a new hard drive soon-ish and put intrepid on thereand then use it as my main os, but maybe when i do that i can use hardy instead.;)

---

### Post by tombom62 on 2009-03-20
(bump)

---

