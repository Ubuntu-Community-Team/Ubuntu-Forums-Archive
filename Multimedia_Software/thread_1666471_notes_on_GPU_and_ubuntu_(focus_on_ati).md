---
title: "notes on GPU and ubuntu (focus on ati)"
date: 2011-01-13
forum: Multimedia Software
---

### Post by Claus7 on 2011-01-13
Hello,

this thread has a purpose of giving some notes about the things going on gpus that were not so straightforward for me at the beginning. *These notes (I think) will be valuable for other installation processes concerning the harnessing of the gpu power*, which seems to play an important role for some time now.

The field is really vast, so I have focused on ati graphics cards. In general someone can choose among ati, nvidia and intel. Here, I'm not concerned on the pros and cons of this choice. 

Now:
we have an ati card and we want to make it visible from our ubuntu. In order to do so we have to use a software tool which is called a driver. There are many options for this including the open source and proprietary drivers. For better performance the proprietary drivers are proposed, yet it does not mean that the open source ones are bad.

For gpu harnessing it is proposed to use the proprietary ones. For ubuntu there are two options on this: either the driver provided from the repositories (restricted) or the one provided by amd. The driver's name is [COLOR="RoyalBlue"]fglrx[/COLOR] on both occasions and is the software which is responsible on how the OS will use the GPU card. From synaptic (using maverick) the version of the driver is 8.780-0.

There is also another software named [COLOR="#4169e1"]Catalyst[/COLOR], which enables the ati owners to make some configurations on their cards, using a graphical interface which in full name is called Catalyst Control Center (ccc). It can also be found from synaptic with the name fglrx-amdcccle. After installed it can be found from System->Preferences->Ati Control Center. In general the version of Catalyst is not supposed to be the same with that of the driver installed. There are specific Catalyst versions working with corresponding versions of fglrx drivers. For maverick the version, stated in ACC, is supposed to be incorrect having the number 2.13 instead of something like 10.10 (which does not follow strictly the maverick's numbering).

Apart from synaptic, someone can install the fglrx driver from amd's website. The package in question provides also the Catalyst software needed [COLOR="#4169e1"]so both of them are installed[/COLOR]. At the time or writing Catalyst 10.12 was the latest one out (the fglrx version escapes me, not knowing if it is necessarily the same as that of catalyst...).

Now, for things to work, the versions stated should be compatible with the version of xserver. For maverick, in order to find out which version of [COLOR="#4169e1"]xorg-server[/COLOR] we are using the command:
```
man xorg | grep xorg-server
```
would suffice. 
The output is:
> X Version 11          xorg-server 1.9.0              Xorg(1)
We can also find out from synaptic, looking at the package named xserver-xorg-core. There it says:
2:*1.9.0*-0ubuntu7.1, discerning for clarity the version written in italics.

If you visit amd's website you might see that their drivers are compatible with x.x version of [COLOR="#4169e1"]xorg[/COLOR]. In order to see which version your ubuntu is using, then again from synaptic finding the package xorg will give you the answer (here 1:*7.5*+6ubuntu3, again in italics the version in question).

To find out which GPU the command:
```
lspci | grep VGA
```
will be enough.

Hope these notes are giving a clearer picture on the issue, which was very vague for me at the beginning. This might help in the feature, when specific versions of drivers are needed for specific applications.

Regards!

---

### Post by armyofgayunicorns on 2011-01-13
Thanks for that, I use my windows partition for gaming so I'm not too bothered about optimising my Ati card in Ubuntu, but I would like to know about what to do when the update manager also wants to install updates relating to the onboard intel gpu. The intel gpu is disabled in my bios so I'm guessing the updates won't have any effect either way, but can they cause any sort of conflict, or will they only do anything if I take the ATi card out and reactivate the intel onboard gpu?

---

### Post by Yellow Pasque on 2011-01-13
> **armyofgayunicorns said:**
> Thanks for that, I use my windows partition for gaming so I'm not too bothered about optimising my Ati card in Ubuntu, but I would like to know about what to do when the update manager also wants to install updates relating to the onboard intel gpu. The intel gpu is disabled in my bios so I'm guessing the updates won't have any effect either way, but can they cause any sort of conflict, or will they only do anything if I take the ATi card out and reactivate the intel onboard gpu?
The intel video driver comes installed with a regular Ubuntu install regardless of whether any intel hardware is present and/or active. Updating it has no effect if your intel GPU is disabled in the BIOS.

---

