---
title: "No sound on anything"
date: 2008-08-09
forum: Multimedia Software
---

### Post by ur0b0r0 on 2008-08-09
i have ubuntu gutsy and i have used it since release , i had the problem of youtube or other things not playing but i solved it like 2 months ago, the problem is today i login and for my surprise there is no sound on anything , not even the sound tests on the sound preferences.it doesnt even recognize my device, i log on windows and it works great but ubuntu doesnt get it.
if it helps, i installed virtualbox a while ago, i think it has to do with it, i dont know is the last thing i have done after playing frets on fire and using opera.
Help is very much appreciated.:confused:

---

### Post by exchequer on 2008-08-09
I have Hardy, but I had the same problem. After I installed the "ubuntu restricted drivers" package everything was fine. Just search for it in Synaptic. If you already have that then I have no other suggestions :(

---

### Post by Choad on 2008-08-09
similar thing happened with me after installing a seemingly unconnected package. try removing it

---

### Post by ur0b0r0 on 2008-08-09
> **Choad said:**
> similar thing happened with me after installing a seemingly unconnected package. try removing it

probably thats the problem but how do i recognize wich package is the one thats not working and how do i remove it?

---

### Post by Choad on 2008-08-09
think back to everything you have installed yourself recently. if it was from add/remove applications you can search for it again there, if it was from the command line you can probably find it by pressing "up" for a long time, then instead of apt-get install do apt-get remove. if it was from a random .deb file you'll have to find the name of the package. if you used firefox you can just look through the download history and see the name of the files there. then uninstall them from the command line

i don't know of any method to find automagically what program is affecting sound :(

---

