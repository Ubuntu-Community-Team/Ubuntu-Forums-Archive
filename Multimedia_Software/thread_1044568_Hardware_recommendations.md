---
title: "Hardware recommendations?"
date: 2009-01-19
forum: Multimedia Software
---

### Post by pullinghairout on 2009-01-19
OK, I finally have given up.
I can no longer stand my Nvidia card with Ubuntu, and I want to buy something new... Course, since I am prolly the last person on the planet still running AGP, it seems like a no-brainer... I need to jump to PCI-express.  Which means a new mobo... so i'm essentially just building a new machine because I don't like Nvidia!

So...  from a driver standpoint, what brand of video card will let me update a driver without having to reboot and futz with X.ORG for an hour or two every time the Linux kernel or the video driver gets updated?

And (since I just thought about it!)  The sound quality from the integrated audio on my current mobo ('SoundMax') has been simply horrible since dapper.  Is there a preferred audio card that Ubuntu supports that will support 5.1, or is that still a ways off?

Don't get me wrong... I am pleased with Ubuntu, it's just getting old to have to spend my weekends playing in X.org and booting into windoze to listen to music!

---

### Post by pullinghairout on 2009-01-19
anyone?

---

### Post by Melcar on 2009-01-19
For sound, any of today's onboard solutions should work fine.  If not, try to get a hold of an older Audigy2 card (either the Value model or ZS); they both work out of the box and support 5.1 sound.
As for video cards, either nvidia or ATI will do.  Both driver sets have the potential to give you problems, and you will always have to re-install drivers when you update kernels.  If you don't mind having a slow card (but still be able to fully use Compiz and watch Xv accelerated videos with no problems, as well as light 3D gaming) you could look into a r5xx based ATI card (x1k cards) since those will work out of the box with no need of proprietary drivers.  Beware that open source drivers for ATI only support opengl1.3 (no games with Wine or any other app. that needs opengl2 compliance) and are about half as fast as the regular ATI driver.

---

### Post by jrusso2 on 2009-01-19
> **pullinghairout said:**
> anyone?

Heh, Nvidia makes the best and they work the best with Linux. All that is left is ATI if you want to try that.  From my experience its much worse on Linux.  

But its your right to try.

---

### Post by beastrace91 on 2009-01-19
If you plan on doing any 3D at all... do yourself a favor and go NVidia.

~Jeff

---

### Post by Cammy on 2009-01-19
I still run AGP, and I also have an nvidia card.  No problems here.

'course I do have to install the new headers and re-install the driver after kernel updates, but that only takes a minute.

Someone did post a how to that describes how to automatically re-install the driver after kernel updates, but I can't seem to find that thread right now.

---

### Post by Melvinator on 2009-01-19
I have had ATI and Nvidia cards in several laptops and desktops. I have been running Ubuntu since 6.04, and never had a problem with the Nvidia. I seem to have some problems with loosing the drivers or some other thing going wrong with ATI. Stick with Nvidia, you will have less problems. Just my opinion.

---

### Post by linuxisevolution on 2009-01-19
> **pullinghairout said:**
> OK, I finally have given up.
I can no longer stand my Nvidia card with Ubuntu, and I want to buy something new... Course, since I am prolly the last person on the planet still running AGP, it seems like a no-brainer... I need to jump to PCI-express.  Which means a new mobo... so i'm essentially just building a new machine because I don't like Nvidia!

So...  from a driver standpoint, what brand of video card will let me update a driver without having to reboot and futz with X.ORG for an hour or two every time the Linux kernel or the video driver gets updated?

And (since I just thought about it!)  The sound quality from the integrated audio on my current mobo ('SoundMax') has been simply horrible since dapper.  Is there a preferred audio card that Ubuntu supports that will support 5.1, or is that still a ways off?

Don't get me wrong... I am pleased with Ubuntu, it's just getting old to have to spend my weekends playing in X.org and booting into windoze to listen to music!

I have 6.1 sound that works fine in Ubuntu. Maybe try a different distro, such as Mepis or Slax. Those are very easy to use and hardware supported. As for Video, Nvidia is the best supported... Try using Envy.

---

### Post by pullinghairout on 2009-01-19
Thanks for the replies.  I appreciate the input.

I kind of suspected that Nvidia or ATI would be pretty capable, but I did not know the speed/opengl2 limits of the ATI drivers.
Maybe I'm being a little naive, but I guess I've gotten so used to the way system updates and software installations are so polished, I just kind of expected there to be something out there that would bypass the process of messing with it for so long after updating the driver or the kernel to get it working right again... I mean (and again, I may be being naive about this) but couldn't the driver be downloaded and installed/recompiled automatically like anything else?  And for that matter, couldn't it also say "oh, well if your X.org settings for *that* driver look like *this*, then I will correct them appropriately for *this* driver"?
But i digress.

And for the sound, I'm just not sure why the sound is so good in windoze (yeah - I can't get SolidWorks to play nice with wine) but Ubuntu is so...  I don't know.  It's almost like the difference between FM and Am.  
Maybe I am just expecting my computer to sound as good as my McIntosh. *sigh*

But thank you again for the replies.

---

### Post by jrusso2 on 2009-01-19
Its because of the drivers.  A lot of time the drivers in Linux do not enable all the features of the sound card or hardware acceleration.

Many Linux drivers are very basic.

---

### Post by Melcar on 2009-01-19
Many sound cards under Windows run with fancy filters, which aren't available under Linux.  Basically, under Linux you hear "real sound", while in Windows you hear equalizer effects that mix the output.  That's the main difference between the platforms.  You also get better mixer support with Linux drivers.

---

### Post by pullinghairout on 2009-01-20
> **Melcar said:**
> Basically, under Linux you hear "real sound", while in Windows you hear equalizer effects that mix the output.

While that may be true, and I'm not doubting you that it is, it just seems like with all of the development going on in Linux, that someone would have addressed this by now.  
I've not heard the "real sound" vs "equalized sound" before, but perhaps it's a computer thing that I am simply not understanding.  
Windows gives what i would consider to be near-CD quality sound from the soundcard.  I have even used the 5.1 output from the soundcard to feed my amps, and to be honest, the quality is fairly decent.
However, from Ubuntu, the same connections sounds distorted, clipped, and overdriven... but again, that's through my McIntosh amp, so maybe a standard set of computer speakers are enough to hide this.  
Like I said, maybe I'm just expecting my computer to sound like a premium sound system.

---

### Post by Melcar on 2009-01-20
Windows drivers often have options to normalize the sound (smooth out the volume levels), or clipping removal.  Often they use equalizer presets to amp up the sound (or turn it down).  None of these things are available in ALSA by itself (the purpose of ALSA is to make cards work, not to "pretty up" the sound output).  You can, however, use equalizer presets on some players like Amarok and Audacious, as well as use plugins in said players to remove clipping or normalize the sound.

---

### Post by pullinghairout on 2009-01-20
Well, between alsa, oss, esd, jack... I think i have tried any and every gain i could find to no avail, and all that software equalization does is make the distortion sound a little muddier (or crisper) on the output side.  But doesn't actually remove it.  But again, maybe I'm just expecting more from a computer than it can provide.  And as i said earlier, it's just surprising to me that this sort of thing hasn't been addressed in Linux before.  (naive, yes? :) )

---

