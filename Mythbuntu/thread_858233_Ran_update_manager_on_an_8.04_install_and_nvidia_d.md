---
title: "Ran update manager on an 8.04 install and nvidia drivers not working"
date: 2008-07-13
forum: Mythbuntu
---

### Post by jdkoola on 2008-07-13
Hi,

I apologize if this question has already been answered.  

I ran the Update Manager on an 8.04 beta install, it downloaded some 300+ updates.

After that the nvidia drivers/screen resolution doesn't seem to be working properly.

I'm using a Westinghouse 42" 1080P LCD monitor w/ an AMD mobo that has a NVIDIA 7 series onboard graphics chipset connected using a VGA connector.

My resolution of 1920x1080 no longer shows up.  I've run nvidia-xconfig as root but it doesn't detect my tv's resolution correctly.  I tried copying over an old xorg.conf file w/ the 1920x1080 option (that was working before) but when I restart X it still doesn't recognize that option.

I'm extremely frustrated at this point as it seems like I spend more time trying to fix Mythbuntu than actually using it.

---

### Post by jbman on 2008-07-13
Try the newest nvidia drivers with envyng and see if that makes a difference. There is also a chance your tv is not giving the system the correct info so it can't get the correct res.

Check out the modeline list on the mythtv website, heaps of ideas as well to overcome this plus some modelines for tvs

---

### Post by jdkoola on 2008-07-13
Thanks for the quick reply.

I downloaded the latest driver from NVIDIA's website.  I ran their script and compiled a new module for my kernel.  Everything worked great.

UNTIL

I restarted.  I had the exact same problem.  It wouldn't save the info on reboot.

---

### Post by jbman on 2008-07-14
I think you should have used envyng as not to cause problems later with updates and it does not cause issues with nvidia. 

try installing envyng from apt-get and try again. I think that will fix the nvidia issue for you. Since it checks if you have everything then installs what u need and the drive you choose.

---

