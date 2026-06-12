---
title: "Experimental 3D NVIDIA DRIVERS are now in Natty"
date: 2011-02-01
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by webme on 2011-02-01
The opensource drivers 3D Nvidia drivers are in Natty, but unusable.
I hope that this drivers will come soon.
For a picture take a look @ [http://iloveubuntu.net/experimental-3d-license-free-and-open-source-nvidia-drivers-have-landed-main-natty-narwhal-repos](http://iloveubuntu.net/experimental-3d-license-free-and-open-source-nvidia-drivers-have-landed-main-natty-narwhal-repos)

---

### Post by Simian Man on 2011-02-01
Those have been in Fedora for ages.  They work pretty well, but not as fast as the Nvidia ones obviously.  More than sufficient for Compiz though.  Glad to see Ubuntu catching up :).

---

### Post by cariboo on 2011-02-01
I have one system that has been using nouveau plus the experimental library since Natty testing started,  It's even been mentioned in this sub-forum several times already.

---

### Post by gnomeuser on 2011-02-01
They've been available for ages. First in the xorg-edgers PPA and since the beginning of Natty at least in the main repos for install.

The big change would be when they get installed by default, seeing as upstream has not released a 1.0 nor will support the Gallium driver presently.. that is not likely to happen for Natty. Unity requires these features though so they may be up against the wall at some point especially if the situation doesn't change much for Natty+1.

---

### Post by webme on 2011-02-01
> **gnomeuser said:**
> They've been available for ages. First in the xorg-edgers PPA and since the beginning of Natty at least in the main repos for install.

The big change would be when they get installed by default, seeing as upstream has not released a 1.0 nor will support the Gallium driver presently.. that is not likely to happen for Natty. Unity requires these features though so they may be up against the wall at some point especially if the situation doesn't change much for Natty+1.

In the main repo, you say?
This is the first time that I personally see this experimental 3D for Nvidia when you run "Additional Drivers". Last time I've installed Natty ( 5,6 days ago) this option was not there.

---

### Post by lucazade on 2011-02-01
> **webme said:**
> In the main repo, you say?
This is the first time that I personally see this experimental 3D for Nvidia when you run "Additional Drivers". Last time I've installed Natty ( 5,6 days ago) this option was not there.

libgl1-mesa-dri-experimental was present also in Maverick repos.

---

### Post by MacUntu on 2011-02-01
"libgl1-mesa-dri-experimental" has been there for ages.

[QUOTE=gnomeuser] Unity requires these features though so they may be up against the wall at some point especially if the situation doesn't change much for Natty+1.[/QUOTE]

Unity Qt seems to work fine as a fallback, so I see no dilemma for now.

---

### Post by superlex on 2011-02-01
> **lucazade said:**
> libgl1-mesa-dri-experimental was present also in Maverick repos.

Yes, it provides nouveau_dri.so, that works very well for me. 
So, is it not a news of natty?
And then, is it the same of gallium3D's nouveau_dri.so?

---

### Post by gnomeuser on 2011-02-01
> **MacUntu said:**
> 
Unity Qt seems to work fine as a fallback, so I see no dilemma for now.

True now that we have a 2D solution this is less of a problem, though one that also brings with it some undesirable drawbacks (such as having to support essentially two codebases for the same job for years).

The main reason why the 2D solution is likely staying though seems to be the ARM video support situation, which is some what more dire than nvidia in the open. I hope Linaro will have good things to tell us soon but that frankly worries me more than nvidia which seems like a "solved problem" in some ways. Perhaps though their will convergence, Nvidia is pushing Tegra hard and with good success. They plan to update the Tegra platform every year and already it is very powerful and well suited for tablet deployments (where obviously Ubuntu would like to play a role eventually).. so fun times ahead in 3D land.

---

### Post by lucazade on 2011-02-01
> **superlex said:**
> Yes, it provides nouveau_dri.so, that works very well for me. 
So, is it not a news of natty?
And then, is it the same of gallium3D's nouveau_dri.so?

It seems you are right :)

[https://launchpad.net/ubuntu/maverick/i386/libgl1-mesa-dri-experimental](https://launchpad.net/ubuntu/maverick/i386/libgl1-mesa-dri-experimental)

 This version of Mesa provides GLX and DRI capabilities: it is capable of
 both direct and indirect rendering. For direct rendering, it can use DRI
 modules from the libgl1-mesa-dri package to accelerate drawing.
 .
 This package does not include the OpenGL library itself, only the DRI
 modules for accelerating direct and indirect rendering. The drivers
 in this package may provide more features than the drivers in the
 libgl1-mesa-dri at the cost of less stability.

Good to know.. so Natty version includes also Gallium bits?

I was thinking about this old thread.. [http://ubuntuforums.org/showthread.php?t=1531554](http://ubuntuforums.org/showthread.php?t=1531554) :)

---

### Post by webme on 2011-02-01
> **lucazade said:**
> libgl1-mesa-dri-experimental was present also in Maverick repos.

The important thing mentioned by me :is the first time that "Experimental 3D drivers" for NVIDIA appears by default here.
Look @ the attached pictured.

---

### Post by lucazade on 2011-02-01
> **webme said:**
> The important thing mentioned by me :is the first time that "Experimental 3D drivers" for NVIDIA appears by default here.
Look @ the attached pictured.

Already seen.
I personally care more to which kind of driver I could install than to jockey gui frontend.

Does this driver contain Gallium 3D? 
Did the old libgl1-mesa-dri-experimental provide 3D but from Mesa and not from Gallium?

---

### Post by webme on 2011-02-01
> **lucazade said:**
> Already seen.


Does this driver contain Gallium 3D? 
Did the old libgl1-mesa-dri-experimental provide 3D but from Mesa and not from Gallium?

Being put in that GUI might possibly show that the devs are giving it more attention and in Natty +1 could become quite stable and full 3D capable. That's the point (at least in my opinion)!!!

---

### Post by gnomeuser on 2011-02-01
> **webme said:**
> Being put in that GUI might possibly show that the devs are giving it more attention and in Natty +1 could become quite stable and full 3D capable. That's the point (at least in my opinion)!!!

I'm the biggest Nouveau cheerleader around, but that sounds a bit optimistic. I believe by Natty+2 Nouveau will be able to present stable sufficiently capable and performant 3D to support Unity on most cards. It will still be behind the binary driver in performance and likely support. Also the story Gallium and thus also Nouveau has in mind for VDPAU are so far not I understand in code form. Even core X people have started talking about using VDPAU to back the "next generation X" and it is needed to play HD content reasonably on most machines. With Tegra being pushed heavily I worry that to compete this needs to change now, but it is likely very hard work.

So for desktop targets I think the next LTS could be good in this configuration but it would still be a bit slow and not support the some opengl features (meaning that gaming is problematic for a non-trivial gaming).

But yes, I would welcome exposing the Gallium driver more, perhaps proposing it jockey by default (though still recommend the proprietary driver). Wider, opt-in, testing would be interesting.

*edit*

I forgot, Ubuntu is also expressing an interest in Wayland as a long term goal. This depends on features the proprietary driver doesn't support and for legal reasons are unlikely ever to. While Wayland likely for the cycle after the next LTS at the earliest, having the foundation well tested and deployed would have advantages.

---

### Post by MacUntu on 2011-02-02
Power consumption is another issue: Nouveau needs more juice than the BLOB (idle and under load) - at least on my four cards, two of them being mobile ones.

---

