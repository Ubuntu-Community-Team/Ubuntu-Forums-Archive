---
title: "Transferred songs to iPod Touch via Rhythmbox are missing on iPod"
date: 2010-07-04
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by kyleabaker on 2010-07-04
I'm trying to transfer songs to my iPod Touch (iOS 4) using Rhythmbox with all current system updates applied.

The song transfers appear to complete successfully and I'm able to select my iPod in Rhythmbox and play the songs I've transferred, but when I disconnect my iPod and browse the songs on it there are none of the songs that I just transferred.

Its like Rhythmbox isn't triggering library indexing or library database updating...something like that.

Others seeing this problem? Is there a solution to this?

---

### Post by d3v1150m471c on 2010-07-04
have you tried gtkpod? I believe it's in the repositories.

---

### Post by kyleabaker on 2010-07-04
> **d3v1150m471c said:**
> have you tried gtkpod? I believe it's in the repositories.

Thanks for the suggestion. I just now installed it and ran it. Upon starting, it removed a few duplicate songs on my iPod. Saving the changes triggered the library update process properly...so I guess I can use this to make the transferred songs appear.

I wonder what the problem is with what ever it is that Rhythmbox uses to communicate with iPods. This will be a huge issue for new Ubuntu 10.10 users if it isn't fixed for the final release.

---

### Post by kyleabaker on 2010-07-04
Doing a little more research, I've found that Rhythmbox uses libimobiledevice:
[http://www.libimobiledevice.org/](http://www.libimobiledevice.org/)

They actually answer my question and apparently a fix is being worked on:
> **I can see my iPhone/iPod Touch in Rhythmbox, move over music and I know it is was copied to the device but it never shows up on the device!**
Make sure you see the "Sync in Progress" screen on your device before unplugging it. It is that screen which will make your device recognize the tracks you copied over. Unplugging the device earlier will leave the files on the device, however never update the device media player's music database. Currently Rhythmbox does not have an optimal workflow syncing the changes and this is being worked on (like syncing directly after all tracks are finished copied). Also make sure you have an "iTunes_Control/Device" folder. If not, follow step 5 from here.

Looks like all I can do is wait for this issue to finally be solved..

---

