---
title: "Pulseaudio suddenly defaults to Mute when rebooting/startup"
date: 2009-05-01
forum: Multimedia Software
---

### Post by Cybie257 on 2009-05-01
I've been using Pulseaudio and overall it works great. Suddenly, for some unknown reason, when I boot up my computer it's defaulting PulseAudio volume to Mute. I tried adjusting it up and rebooting hoping the setting will stick, no luck. Tried re-installing PulseAudio, still no luck. 

Any ideas? 

Jaunty 64

-Cybie

---

### Post by Cybie257 on 2009-05-01
Anyone???

Is there a configuration file somewhere that I can change a setting to max out the volume on boot up???

-Cybie

---

### Post by Cybie257 on 2009-05-02
This has been solved. 

Reading through many bug articles, apparently something 'un-ticks' the check-box for:

     Audio settings management (alsa-utils)

within the Services Settings. (IE: System->Administration->Services)

Weird. Never had that problem before. 

But, it's fixed. :guitar:

-Cybie

---

### Post by astx813 on 2009-08-20
> **Cybie257 said:**
> This has been solved. 

Reading through many bug articles, apparently something 'un-ticks' the check-box for:

     Audio settings management (alsa-utils)

within the Services Settings. (IE: System->Administration->Services)

:guitar: You, sir or ma'am, rock!  This was one of those minor nuisances I went months without addressing, and when I finally did, the first articles made it look like I was gonna have to do all sorts of crap to fix it.  I do love these simple solutions!  I owe you a beer.

---

### Post by nchase on 2009-09-10
This was very helpful to me as well. Thank you.

---

### Post by bigjoe7 on 2009-09-18
many thanks - that worked for me.

---

### Post by nortexoid on 2009-10-09
Same here, and first hit on google (for "ubuntu pulseaudio defaults to mute"). The beauty of excellent discussion forums...

---

### Post by bhagwad on 2009-11-06
> **Cybie257 said:**
> This has been solved. 

within the Services Settings. (IE: System->Administration->Services)

-Cybie

I'm using Karmic and I can't find "Services" under System->Administration - is there another workaround for this?

---

### Post by koxel on 2009-11-07
> **bhagwad said:**
> I'm using Karmic and I can't find "Services" under System->Administration - is there another workaround for this?

gnome 2.26 removed service admin.. and you can use bum(bootup manager)

---

### Post by addtoqueue on 2009-12-05
> **koxel said:**
> gnome 2.26 removed service admin.. and you can use bum(bootup manager)

And how do you fix PulseAudio's mute on boot using BootUp Manager in Karmic?  There aren't any alsa-utils listed there.

---

### Post by iMerlin on 2009-12-12
There's no alsa-utils in my "bum" (insert lame joke here) (Bootup Manager).

I like Ubuntu as much as the next guy but these constant changes in the sound systems are starting to annoy me.

---

### Post by flabdablet on 2011-06-20
> **Cybie257 said:**
> This has been solved. 

Reading through many bug articles, apparently something 'un-ticks' the check-box for:

     Audio settings management (alsa-utils)

within the Services Settings. (IE: System->Administration->Services)

Weird. Never had that problem before. 

But, it's fixed. :guitar:

-Cybie

Thanks, Cybie. You just fixed a new Debian Wheezy installation whose sound I've been struggling with for the last week. More beer for you!

---

### Post by biju1256 on 2012-04-13
Hi all,
I am not so tech savy... pls help me in using the commands in Ubuntu 11.10.
Using Laptop "Dell with Intel Pentium"

rgds,
Biju

---

