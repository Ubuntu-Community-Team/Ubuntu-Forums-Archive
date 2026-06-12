---
title: "Can i use Mythbuntu with this setup?"
date: 2009-03-23
forum: Mythbuntu
---

### Post by ryanmission on 2009-03-23
Hi, im new here and curious!!!

I have my main PC, connected to my 42" LCD TV via a DVI > HDMI cable.

The PC is also connected to my Rogers Digital Cable STB, which is a SA3250HD. It's connected via firewire. (Not sure if it's an enabled port yet, but my Vista recognizes the SA3250HD box but doesnt have drivers for it).

Note: The SA3250HD is also connected to my TV via component for regular tv watching.

I want to run Mythbuntu in VMWare on my Main PC, only to record TV through the firewire, and playback on Vista through the HDMI.

Here's a TERRIBLE visual.

[:TV:]------------->[:SA3250HD:]
...|......Component.......|...
...|...............................|...
...|HDMI..............FWire|...
...V..............................V...
...-------->[;PC:]<--------...

If you're more confused after looking at that, sorry lol. 

But my question: Is it possible?

Thanks!

---

### Post by theophile on 2009-03-23
That should work. I can't speak for the compatibility with vmware though, but that cabling arrangement should work fine. You'll only run into problems with the SA3250HD if you have more than one output (not including firewire) connected at once. e.g. if you have the DVI and S-video ports both connected, the s-video output will be disabled unless the DVI-connected device is turned on. Retarded, but that's how they programmed it.

---

### Post by ryanmission on 2009-03-23
> **theophile said:**
> That should work. I can't speak for the compatibility with vmware though, but that cabling arrangement should work fine. You'll only run into problems with the SA3250HD if you have more than one output (not including firewire) connected at once. e.g. if you have the DVI and S-video ports both connected, the s-video output will be disabled unless the DVI-connected device is turned on. Retarded, but that's how they programmed it.

Awesome! Thanks for the fast reply...

Do you know of any guides for configuration/installation?

---

### Post by theophile on 2009-03-23
Guides for MythTV? There are tons of them easily located via Google.

The SA3250HD can be a bit fidgety. There are tools being developed in this forum (e.g. mythprime). You may have luck with them but I never have. My personal knowledge base has some stuff on the SA3250HD, maybe it will be helpful:
[http://monopedilos.com/dokuwiki/doku.php?id=start](http://monopedilos.com/dokuwiki/doku.php?id=start)

---

### Post by ryanmission on 2009-03-26
Hi, i've taken a look at your website you posted and im following the firewire configuration for MythTV.

Unfortunately however im at the stage where i need to use "plugreport". I've gone ahead and installed it....but when i try to run it in terminal i get nothing.

ryan@ryan-myth:~$
ryan@ryan-myth:~$ plugreport
ryan@ryan-myth:~$
ryan@ryan-myth:~$

Now, im running this in VMWare on a vista box...do i need to enable the firewire in VMware somehow..? or how can i check to see if the firewire connection is detected on my Mythbuntu?

thanks!

---

### Post by ryanmission on 2009-03-27
bump

---

