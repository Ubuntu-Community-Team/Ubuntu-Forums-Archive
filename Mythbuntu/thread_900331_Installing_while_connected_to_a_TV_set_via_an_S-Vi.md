---
title: "Installing while connected to a TV set via an S-Video cable"
date: 2008-08-25
forum: Mythbuntu
---

### Post by OneHundredAndTen on 2008-08-25
I am trying to install Mythbuntu, and I have hit the following snag:

My PC is connected to my TV set via an S-Video cable. When I boot my PC off the Mythbuntu 8.04.1 CD I initially get output to my TV set all right. However, once Mythbuntu attempts to start the installation configuration, my TV screen goes blank. It would seem to be the case that, at that point in time, Myhtbuntu does not know how to configure X windows to deal with an S-Video output. Indeed, if I start the installation with my PC connected to a monitor using an ordinary connector instead, everything works fine.

Is it at all possible to tell Mythbuntu that the installation process is to be done connected to a TV set by an S-Video cable, so that it configures its X server accordingly when launching the X windows-based installation sequence?

---

### Post by pnauta on 2008-08-25
OK, I'm assuming you have either a NVidia or Radeon video card installed, and you're installing from the Live CD.

- Boot in safe mode.
- Do the install
- Get the package called "envyng"
- After installing envyng, start it up and install your flavor of video driver

That should get you a setup that will detect your monitor, which you can now set at it's desired resolution, connector and whether you want Twinview or even disable the VGA port.

---

### Post by volkswagner on 2008-08-25
Using the restricted driver manager, part of Mythbuntu-control-centre is the preferred method.  Envyng is a last resort.

You should perform the install with a monitor, than enable the restricted drivers, shutdown, and reconnect via svid.

---

### Post by pnauta on 2008-08-26
@Volkswagner: the thing you should appreciate is that many newbies like me ge stuck in the initial installation when you have a custom video setup like this one.  It drove me crazy, and I wish someone had told me about envyng at that stage.  And the last resort is often the only resort in Linux :(  I used a DVI-HDMI cable to setup Mythbuntu on a modern mobo with a Nvidia 7050 chipset, and I had the exact same result, and this was the only way it worked.  That was with 7.10, and now with 8.04 I had to repeat it, and again the only way out was using envyng.

So instead of telling us newbies the correct way, maybe you can tell us WHY envyng is not preferrable.  Then let's get those bugreports in because this is the biggest and saddest problem of Linux in general, ie that you still (after more than 15 years!) can't rely on PnP functionality and get stuck right during installation.

---

