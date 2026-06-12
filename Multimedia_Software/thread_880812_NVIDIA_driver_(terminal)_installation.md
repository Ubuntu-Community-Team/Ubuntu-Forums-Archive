---
title: "NVIDIA driver (terminal) installation?"
date: 2008-08-05
forum: Multimedia Software
---

### Post by ArtF10 on 2008-08-05
GRAPHICS CARD:  GeForce FX 5500(or 5600...one of these two)
DISTRIBUTION:  UBUNTU HARDY 8.04

I would like to install the latest proprietary drivers for my video card(Ubuntu Hardy 8.04).  I have a clean install of Ubuntu and have only updated the system.i.e. I have not installed restricted drivers through the pop up balloon that shows up prompting me to do so.  From my experience with Ubuntu **Fiesty**, I found that the guide by TSELIOT was good and did the job.  I would just follow that guide instead of following the pop up balloon that showed up after a fresh install.  That guide was easy to follow through from a terminal and I became ver ycomfortable with using it to install the drivers.

This is the link to the guide(I used METHOD 1 --> the only OFFICIALLY SUPPORTED METHOD):

[http://albertomilone.com/latest_nvidia_udsf_feisty.html#METHOD_1](http://albertomilone.com/latest_nvidia_udsf_feisty.html#METHOD_1)

**QUESTION:** Can I still follow this guide with Ubuntu Hardy 8.04(LIVE-CD INSTALLATION)?  Or is there an easier way to install the driver?

---

### Post by NT4usB on 2008-08-05
According to [page one]("http://albertomilone.com/nvidia_scripts1.html") EnvyNG is for Hardy and can be found in the repositories.
That said, I've used Envy several times. Usually after other attempts at installing driver.
I find running the envy option to completly remove the existing drivers first, then installing gives good results.
Be sure to grab the latest installer off Albertos website (or use the one from the repositories.) I've been bitten by running one I had laying around from prior installs and it's just not the same...

---

### Post by ArtF10 on 2008-08-05
BTW, forgot to mention, my video card is NOT PCI-Express.....it is PCI or AGP(not sure.....would have to open CPU and check.  So basically, it's quite old.  **128 MB GeForce 5200 FX.**

Ok, so I take it you're suggesting that I should use EnvyNG.  I have understood the steps described on the website you linked.  

**QUESTION:** Is EnvyNG the easiest AND SAFEST way to install the video card driver?

---

### Post by Stan_1936 on 2008-08-05
It says on the website with the text instructions, you listed in the first post, that it is specifically for FIESTY, so I'm guessing NO you cannot use that method with HARDY!

The ENVYNG solution, that was suggested in the 2nd post, sounds good, although I would wait for a more experienced member to reply to your question above(in the 3rd post).

---

### Post by ArtF10 on 2008-08-06
Is EnvyNG the recommended way to install the video card driver, in Ubuntu Hardy?

Anyone?

---

### Post by NT4usB on 2008-08-06
The recommended way is enable the restricted driver manager and let it install that way.
The alternitve way is envy from the repositories.
The fun way is fixing it after both those don't work.

---

### Post by ArtF10 on 2008-08-07
Haha, I know I know......My end goal is to install Compiz Fuzion.

Does the envy installation offer any advantages, in terms of the performance of Compiz Fusion, when compared to the restricted manager installation?

---

### Post by NT4usB on 2008-08-07
May be that Envy gets you more recent drivers. I dunno. You'd have to read the release notes to check that.
I only use Envy because it works and I can get to it quick and easy when a kernel upgrade wrecks the video on my mythbox. ssh in, run it, done.

---

