---
title: "NVidia Screen Resolution Issues after Gutsy to Hardy upgrade"
date: 2008-08-02
forum: Multimedia Software
---

### Post by BuntuFreak on 2008-08-02
All right, I had everything working fine. NVidia drivers for my MX 4000 128MB video card, Compiz Fusion, AWN Manager. EVERYTHING! This was with Gutsy. Then I finally gave in.

Upgraded to Hardy using the Update Manager. Had the standard problem with locale-gen that everyone had. Got past that. Everything came up fine. NOT!

Compiz stopped working. Computer freezes, spontaneously reboots. If not spontaneously logs me out. If not, spontaneously restarts X. Needless to say I have to start over.

So then, first problem. NVidia settings does not allow me to specify 1440 X 900 resolution. Well it does, but screen is shifted to the right. I can only run in 1280 X 768. And I turned off Compiz and AWN, but it still spontaneously reboots. If not at the very least leaves glitches - portions of windows killed or moved.

1) Can someone tell me how I reinstall NVidia drivers.
2) Can someone tell me how I reinstall Compiz & AWN.

I have searched all forums but have not found satisfactory solutions. I have tried everything I can. I think it boils down to me first being able to have a glitch free NVidia driver before I try do anything else. Hence posting it in this Topic.

Thanks in advance for any help.

Best.

---

### Post by BuntuFreak on 2008-08-05
No one? Common people! Much as I would hate it, after several months of Ubuntu Joy, I'll be forced to go back to Vista. And that would really suck.

---

### Post by BuntuFreak on 2008-08-06
All right. I fixed it. Hopefully it helps someone else in the same situation.

Go to Nvidia Screen Resolution applet. Change to the next highest frequency. In my case, options available were 50, 60 and 75.

When I went to Nvidia Settings manager, I only saw 60 and 75 as possible options. Changing frequency to either value there did not make a difference. But when I went to Nvidia Screen Manager, it showed frequency as 50 which was strange. I simply changed it to 60 and my screen shifted back to original place.

Now Compiz gives me "white windows". Maybe I'll have to uninstall and cleanup then install Compiz again.

---

### Post by Stenrad on 2008-08-06
I had similar problems to you. :-( But then I found this:- 

[http://ubuntusoftware.info/uu/]("http://ubuntusoftware.info/uu/")

Solved all of the above problems - highly recommended! Plus Hardy used to lock up on me rather alot - now it hard ever does. :-) Hope that helps!

Stenrad.

---

