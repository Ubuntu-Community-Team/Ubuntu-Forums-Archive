---
title: "Nvidia driver update trouble"
date: 2008-09-06
forum: Multimedia Software
---

### Post by Findarato on 2008-09-06
Hello,

I just wanted to make a thread about the problem I had trying to update my nvidia graphics driver. 

First of all, I went to the official nvidia website, downloading the newest stable driver and followed the procedure. It told me that the driver couldn't get installed while x-server was running. Quick check on the forum, someone said I should go text-mode (alt-f1) and killall gmd to proceed, which is probably where the error is. 
After I did this, the installation went on, and everything seemed fine, nvidia asking me to reboot my machine to finish etc. 
Upon reboot, I had a popup saying my graphics hardware couldn't be detected... I could still choose a simple 800x600 resolution though, so I did.
I then tried to solve the problem by installing the driver through Envy, which gave me another result: This time I had all the resolutions UNDER 800x600, which was a lot more choice then I had before, but totally useless :S Weirdly enough, after this, my compiz was functionning, indicating something must have gone right.
When that didn't function, I thought I could re-activate the "nvidia restricted driver" through the hardware admin panel of ubuntu. This killed everything, giving me a message "out of range" on my monitor after I rebooted. 
I then rebooted my machine in recovery mode and tried "xserver fix", which in turn gave me a screen with flickering green lines...

I then rebooted AGAIN in recovery mode, ran package repair and decided to try and install the new driver (the one I had downloaded at the very beginning and, luckily enough, should still be on my desktop, eventhough I couldn't graphically see it) again to at least get back my 800x600 view. 
Luckily enuogh I managed to find my way around the text-mode (I am still very novice at this) and installed the driver.

Now a miracle happened, because after this time (remember, I did the same thing already once before), the actual Nvidia splash screen came upon boot and now I have the newest driver installed and running...

I don't know exactly what I did wrong and what I did right, but I hope my experience will  be of use to someone.

---

### Post by overdrank on 2008-09-06
Great, glad to hear you are up and running :)
Moved to Multimedia & Video

---

