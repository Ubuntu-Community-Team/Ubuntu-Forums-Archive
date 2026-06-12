---
title: "Nvidia 6800 not going into glx mode on edgy"
date: 2007-03-07
forum: Multimedia &amp; Video
---

### Post by mcvoid on 2007-03-07
I hope someone can help.
Every time I try to enable glx for my NVIDIA 6800GT, the screen will go black the next time I boot, so I have to restore the backup to the xorg.conf. I don't know why. I've searched the forums here and google, but I get the same answers. 

[LIST]
[*]I followed this: [http://ubuntuforums.org/showthread.php?t=281823]("http://ubuntuforums.org/showthread.php?t=281823")
[*]I've also tried Envy,
[*]Everything has had the same result.
[/LIST]
Also, after I tried Envy, I got a message asking to download an update for nvidia-glx, but whenever I try to install it, it gives the following error: > E: /var/cache/apt/archives/nvidia-glx_1.0.9746+2.6.17.7-11.1-9746_i386.deb: subprocess pre-installation script returned error exit status 2
This is wierd since I'm pretty sure that I shouldn't be using the i386 packages - I have the generic nvidia kernel and stuff.
I just don't know what's going on, and no matter how many ways I try to fix it, the result is always the same: a blank screen!

end note: After this posting I removed the nvidia-glx package and reinstalled it and I didn't get the error any more - I guess it got the right type this time. The problem is still not fixed, though.

---

### Post by dotman on 2007-03-07
What's in /var/log/Xorg.0.log ? Maybe that will provide some insight to what the error is.

---

### Post by mcvoid on 2007-03-07
From what difference I can tell of the, one says the x server loads the nvidia driver when the screen goes blank - the other (where i can see stuff but can't get to glx stuff) loads the nv driver. that's the only thing i can tell apart from the two monstrously large log files.

Also, I turned my speakers up, and when the screen goes blank, the login sounds chimes off, so the computer isn't locking up - it's just not displaying anything.

---

### Post by superhew on 2007-03-12
i've also been having this problem, for probably over a month now. I gave up and started using an old comp with breezy on it instead. i also have a 6800 (gt, pci-e), as well as an athlon 64 4000+. can't figure it out, have tried all the tutorials, mulitple install discs, etc. the setup was working fine before; twinview, beryl, etc. just decided not to work after a restart. i had a feeling it was with something i had installed, but i have no idea.

---

### Post by dotman on 2007-03-12
I've had that happen before but only on an older monitor where the display was out of range but the monitor wasn't telling me that. When the logs didn't show any fatal errors I changed the resolution in my xorg.cong to only use 640x480 and it worked. Had I any speakers, i would have heard the login noise for GDM, similar to what you are saying. If you have an older monitor, it may be worth a shot.

---

