---
title: "Graphics Cards which Unity Supports"
date: 2011-04-25
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by ds_shellback on 2011-04-25
Hi,

I've successfully installed Unity Beta on a system with Intel 82945G graphics chipset - this works fine

However, the following graphics cards both boot straight to the Gnome desktop from the live CD - will these run Unity 2D perhaps ?

ATI Radeon 7000
nVidia FX5200

I'm really struggling with an Intel 82865G Chipset system currently quite happy under 10.10 which when booted from live cd just gives large black blocks where the menus should be when you click "Applications" or "Places" etc.

Will older hardware have ubuntu/unity support? - Is there a list of supported graphics hardware for Unity?

---

### Post by terry_gardener on 2011-04-25
> **ds_shellback said:**
> Hi,

I've successfully installed Unity Beta on a system with Intel 82945G graphics chipset - this works fine

However, the following graphics cards both boot straight to the Gnome desktop from the live CD - will these run Unity 2D perhaps ?

ATI Radeon 7000
nVidia FX5200

I'm really struggling with an Intel 82865G Chipset system currently quite happy under 10.10 which when booted from live cd just gives large black blocks where the menus should be when you click "Applications" or "Places" etc.

Will older hardware have ubuntu/unity support? - Is there a list of supported graphics hardware for Unity?

you will properly be hard pressed getting nvidia and ati cards to work with unity from live cd. 

don't know about a list, i have tested it on nvidia 6150se, 8200gs and gtx460 and they all work with unity using nvidia-current driver. 

if the card doesn't work with unity you can either use unity 2d or classic gnome

---

### Post by mc4man on 2011-04-25
As far as w/ nvidia cards the "try me" session is not very helpful in letting you know that you can test the nouveau 3d drivers and unity.
 
If your adapter did work w/ nouveau then most likely it would also work with the appropriate nvidia driver in a real install
(one could only easily test nvidia drivers on a live session for a short time - karmic and maybe lucid

If your adapter didn't work with the nouveau 3d that doesn't mean that the nvidia wouldn't provide 3d and unity support, you'd need to actually do an install to see or ask around

---

### Post by Joe of loath on 2011-04-25
ATI no, nVidia yes. The 173xx proprietary drivers still work with the FX5200, and it copes (just about) with the desktop effects in KDE.

---

### Post by ds_shellback on 2011-04-26
Thanks everyone for that information.

The Intel 82865G rev 02 chipset system I've got (Integrated Graphics) seems the most problematic at the moment it doesn't enen want to run the natty gnome desktop properly (even though it has a current 10.10 install) from the live 11.04 beta 2 cd - I suppose it's a bug in the beta 2 for this chipset.

This bug report indicates that it's not supported because it's openGL 1.3

[https://bugs.launchpad.net/unity/+bug/696999]("https://bugs.launchpad.net/unity/+bug/696999")

And the bug pointed at a list of hardware requirements - _Looks expensive_!

[https://wiki.ubuntu.com/DesktopExperienceTeam/UnityHardwareRequirements]("https://wiki.ubuntu.com/DesktopExperienceTeam/UnityHardwareRequirements")

---

### Post by screaminj3sus on 2011-04-26
Reqs don't look that expensive for a modern desktop operating system to me.

Remember the cards you have are like 10 years old, they don't run the latest stuff forever.

---

### Post by sgage on 2011-04-26
I have an NVIDIA GeForce 8500 GT card in my computer. I reinstalled Natty a yesterday from the 4/25 daily. I was astonished that it came up in Unity! Usually the first thing I do is install the proprietary drivers so I can get Unity, but yesterday's install did it automatically during installation. I was pleasantly surprised.

---

### Post by dino99 on 2011-04-26
hm, i've the same 8500gt card on a maverick updated to natty i386, and i always have a popup saying "it seems your card is not able to run unity" when logging. Difference between dist-upgrade and a fresh install is still a mystery .

Going to make a fresh install in a few weeks when the main bugs will be fixed.

---

