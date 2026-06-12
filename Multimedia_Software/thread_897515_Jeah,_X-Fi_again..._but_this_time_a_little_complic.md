---
title: "Jeah, X-Fi again... but this time a little complicated..."
date: 2008-08-22
forum: Multimedia Software
---

### Post by 159874 on 2008-08-22
It's about tadaaa X-Fi :D but this time it's also about my GeForce 7900 GT.

What do they have in common? Jeah, let me explain that:

I first installed Ubuntu 7.10 since that version is more or less supported by the beta driver for my X-Fi XtremeMusic. So I configured my system, installed the driver and was happy that everything was ok... THEN I tried to install my GeForce driver (nvidia-glx-new) over the restricted "Hardware Drivers"... so far so good... I rebooted and what I did get was not nice resolution and 3D support but "Graphics save mode" and lots of problems... I first thought this is a problem with my xorg.conf and I played around with it a lot but no luck.... after 8 hours I finally installed Ubuntu 8.04. But there still was my little X-Fi Card... so I searched the internet for a resolution to get my X-Fi running on 8.04. And I found one :D (jeah, the n00b finds a tutorial *snatch*)

[http://ubuntuforums.org/showpost.php?p=4823915&postcount=675](http://ubuntuforums.org/showpost.php?p=4823915&postcount=675)

So I followed the tutorial, compiled myself a new kernel and installed successfully my X-Fi driver... and it did actually work... yeah.. nice I thought...... really nice
And then... again I tried to install my nice nvidia driver. This time over the installer from the nvidia homepage because of my new kernel.
I rebooted... (jeah, I could have restarted gdm but its a old windows habit :D). And again it was not the nvidia logo which introduced me to my new perfect sys but the nice "graphics save mode".. Again no luck.

I tried many things and finally I uninstalled the X-Fi driver and reinstalled my graphics driver and tada: no sound but 3d and high-res.

So, my question is: WHY? What does X-Fi driver and nVidia driver have in common; where is this damn conflict???

If you need precise information (and I'm sure you do) please also post a way to acquire those informations... since I'm a n00b I might not know :D



-------------
$Number

---

### Post by amtam on 2008-08-23
> So, my question is: WHY? What does X-Fi driver and nVidia driver have in common; where is this damn conflict???

Let me know if and when you find out... ;)

The best way to get them both working is to **first** install your graphics and then the X-Fi. Then they can happily live together, until you update the nvidia-driver (either manually or through Envy).

I don't think the problem/conflict will be fixed until Creative or Alsa releases a half-decent driver.

---

### Post by 159874 on 2008-08-25
Jeah, I've done a lot to get things running... but no luck at all. It seems that it does not matter which driver I install first... all I know is that loading both modules at the same time is not possible. Damn Creative; after 3 jears or so they still don't made a decent driver for linux... 

Perhaps I'll try Ubuntu 7.10; installing the nVidia Driver first could solve the problem... but you Guys always mention "Envy". Do you know that Envy does not support Ubuntu at all? It can uninstall a driver yes, but not more...

Is there somebody who has both drivers running at the same time? :D


-----------
$Number

---

