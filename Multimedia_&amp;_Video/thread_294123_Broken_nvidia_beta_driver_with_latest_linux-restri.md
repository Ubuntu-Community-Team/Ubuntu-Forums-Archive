---
title: "Broken nvidia beta driver with latest linux-restricted-module"
date: 2006-11-06
forum: Multimedia &amp; Video
---

### Post by ziritrion on 2006-11-06
Hi. Since this is my first post, I'd like to thank you all in advance for all the good info I've found here for setting up Ubuntu. Keep up the good work! :D 

Now, my problem: I have a Dell Inspiron 9400 with a nVidia 7800 GS card which I bought 2-3 weeks ago. I've installed Ubuntu Edgy on it and I decided to follow the Beryl how-to, which I managed to run flawlessly to my delight, except for a few glitches that I guess are the beta state of Beryl's fault.

Recently I noticed that I couldn't upgrade with the upgrade manager, so I decided to manually run apt-get install dist-upgrade, which uninstalled the nvidia beta driver. After messing around with xorg.conf, I managed to screw up everything and not being able to run X, but a friend of mine just helped me to get X running with the nv driver, just as it was by default.

I've seen a couple of posts mentioning this issue but I didn't get anything out of them. My question is: is there any way to install the nvidia driver and run Beryl again? when I run apt-get install nvidia-glx I get:

nvidia-glx: Depende: nvidia-kernel-1.0.9625

(I run Ubuntu in Spanish; Depende~needs).

Thanks in advance for everything. If you need any additional info, please let me know.

---

### Post by rianquinn on 2006-11-06
The nvidia driver appears to be removed from the repo. You might have to manually install it.

Try this:

[http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/nVIDIA](http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/nVIDIA)

Use the manual method. 

Not sure why they broke the repo. Seems to me if you are going to put something into a repo you shouldn't mess around with it. It really does effect a lot of people quickly. 

I too had to give up Beryl because of this problem. I'm waiting for KDE 4. It might take a while but I'm tired of dealing with all of this crap. I just want to use my computer.

Hope this helps!!!!

---

### Post by tseliot on 2006-11-06
You can try my UNSTABLE repositories:
[http://albertomilone.com/driver.html](http://albertomilone.com/driver.html)

---

### Post by ziritrion on 2006-11-06
Thanks for your tips!

I tried tseliot's repositories and the instructions on his website, but X crashed anyway and I had to go back to the old config file.

I've also noticed that aptitude or apt-get install the 386 kernel, even though I don't want it and I start with the generic one. Why is that?

I think I'll wait until the repository thing gets fixed and/or final drivers are released (weeks? months?). Thanks for your replies anyway!

---

### Post by Zeroangel on 2006-11-07
> **rianquinn said:**
> The nvidia driver appears to be removed from the repo. You might have to manually install it.

Try this:

[http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/nVIDIA](http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/nVIDIA)

Use the manual method. 

Not sure why they broke the repo. Seems to me if you are going to put something into a repo you shouldn't mess around with it. It really does effect a lot of people quickly. 

I too had to give up Beryl because of this problem. I'm waiting for KDE 4. It might take a while but I'm tired of dealing with all of this crap. I just want to use my computer.

Hope this helps!!!!
Yeah, I'm writing this in Lynx now. The attempt to follow the Beryl tutorial completely trashed my X-Server, mostly starting with the broken repo. I'm about 3 hours into troubleshooting the problem with no success so far.

I highly recommend that you do NOT change your repos until the problem is fixed and announced.

---

### Post by SishGupta on 2006-11-07
I had this problem too. The repo isn't broken (at least not as of last weekend)

There have been ubuntu security updates which superscede the amaranth repo. You need to force the amaranth versions for LRM and another package (i cant remember the name) and then amaranth's nvidia-glx will work.

I am sorry I cant be of more help not only am i on my windows laptop but i am now using "method 2" for the beta drivers as i wanted the ubuntu security updates. I suggest you do the same.

---

