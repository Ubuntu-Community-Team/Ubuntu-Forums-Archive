---
title: "Envy broke my Dapper"
date: 2006-10-30
forum: Multimedia &amp; Video
---

### Post by kevinf311 on 2006-10-30
I think tseliot may be able to help the most here. I installed his envy script in my continuing campaign to get my nVidia FX 5200 card to have the "nvidia" drivers instead of the "nv" ones. This is not the goal of this post though.

After I ran the script, I got the black screen of "my video card doesn't like the driver." I had encountered this before, in other failed attempts, so I pulled up my xorg.conf file and changed the "nvidia" back to "nv" which usually pulls the blindfold of my computer. No luck this time. So after freaking out for a minute or two, I pulled up the forum on my roommates laptop. I searched for "Sweet merciful crap, I killed my computer" and found the command: sudo dpkg-reconfigure xserver-xorg

This appeared to fix things, however, during normal use I started noticing some differences. The shut down box no longer had "restart" or "shut down" options. Also, after being on for a while (more than 2 hours) applications stopped opening. I would get a "Starting [application]" window, and then it would poof. I restarted (the hard way) and booted up the older kernel that  was on the grub loader. This replenished the shut down screen, but I still have the same application problems (although it now takes about a day to stop). 

Since I don't know what all tseliot's script removed, I can't look for any back ups that might have been made. Any help in restoring my system to its previous awesomeness would be greatly appreciated.

Thanks, Kevin

---

### Post by kevinf311 on 2006-11-01
*bump*

---

### Post by BLTicklemonster on 2006-11-03
"something" happened a little while ago. I received a message that I had an update pending, I don't remember what, but it looked important, not your usual stuff, so I went for it. I totally lost my nvidia driver, so I think it was a kernel upgrade? Anyway, nothing I do will allow me to get an nvidia driver going. I tried the basic install nvidia-glx, but I had problems with the nvidia kernel, it said some dependencies weren't met, even though I had the one listed showing as installed in synaptic. I tried remove, --purge remove, nothing worked. I finally removed all the nvidia stuff I could find and also some linux kernel stuff just to see how pissed off I could get ubuntu!!! I then went to tseliot's site, and tried the bleeding edge stuff. It all installed; I watched it loading from his site. I did everything I was told to do, even looking to be sure the nv module was unloaded. Rebooted, and I had an error, and I'm back in vesa. 

And the point I'm bringing us to (after showing that I am utterly screwed as of late) is that when I use envy (this has happened to me since last week or so whenever I tried using it, btw) from the command line after ctrl+alt+f1, I am told there's an md5 checksum error. Now wait a minute... ts wrote the program, and the download is coming from his site, so I'm left wondering wtf?

Fortunately, I had the presence of mind to have worked my butt off the past few days getting dapper and edgy to both be bootable, so I'm good to go (I was expecting something along this line to happen. I have XP bootable, too .. like tri boot instead of dual boot, eh? but I want to see how long I can go without resorting to that)

So ts, if you end up back here, I ask you, wtf, eh m8?

*EDIT:

Nothing worked. I'm reinstalling edgy right now. I wonder wtf that update was?

---

