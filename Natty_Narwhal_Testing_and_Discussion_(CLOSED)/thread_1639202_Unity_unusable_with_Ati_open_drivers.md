---
title: "Unity unusable with Ati open drivers"
date: 2010-12-06
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by madjr on 2010-12-06
Does anyone else have the same problem with unity and the ATI open drivers?

i have a ati x1250
natty alpha1

those are the only drivers available.

in the classic desktop panels renders ok, but glitches also appear in flash videos on **full screen**. 

These glitches don't happen with 10.10 or 10.04

I guess many Ati users wont be able to use the new desktop ;/

here is a pic so you can see how bad the tearing is:

---

### Post by madjr on 2010-12-06
ok, seems am not the only one with the bug.

[https://bugs.launchpad.net/unity/+bug/681915](https://bugs.launchpad.net/unity/+bug/681915)

---

### Post by sonicb00m on 2010-12-07
I cant even get the desktop to load. It just sits there at the wallpaper. So you're a lucky one :D

---

### Post by godhika on 2010-12-07
Hmm, no problems here with the radeon drivers here. Are you running 32 or 64 bit? It looks like the 32bit specific problems they had at beginning of the cycle

---

### Post by coffeecat on 2010-12-07
I think it must depend on your ATI video chipset. I'm posting from a working Unity desktop on a machine with a Radeon HD4350 using the open source driver. If I try to enable such things as wobbly windows or the cube, compiz goes all funny on me with missing windows bars and an unusable desktop - which doesn't happen on my Intel graphics laptop. But if I leave Visual Effects on 'none' in Appearance Preferences, Unity seems stable enough without the artefacts that the OP was seeing.

> **sonicb00m said:**
> I cant even get the desktop to load

> **godhika said:**
> Hmm, no problems here with the radeon drivers here.

@sonicb00m and @godhika, what video cards are you using?

---

### Post by godhika on 2010-12-07
A Hd3450 Mobility card (r500 chipset if I remember correctly)

Edit: I should mention that it is not completely without problems: Alt+Tab for example kills compiz. But I don't see any heavy rendering problems like the original poster

---

### Post by sonicb00m on 2010-12-07
I have the HD5450. I wish i had stuck with Nvidia instead of buying an ATi for a change.

---

### Post by Killigrew on 2010-12-07
HD5000 Series Cards are not fully supported by the open-source driver as the GTX400/500 Series is by nuveau. Better use catalyst drivers for these cards to get full opengl support.

greetings

---

### Post by slooksterpsv on 2010-12-07
> **sonicb00m said:**
> I cant even get the desktop to load. It just sits there at the wallpaper. So you're a lucky one :D

Same problem I'm having. Also wish I could move the icons on the Unity bar =( I want to rearrange haha. Other than that, granted this is an alpha, I love it.

---

### Post by sonicb00m on 2010-12-08
Isn't it the Catalyst drivers that are installed when you use the Proprietary driver manager? I used those and have this desktop issue.

I use 64bit btw.

---

### Post by seenthelite on 2010-12-08
I have a Desktop with ATi and Alpha 1 will not even install, yet same ISO installs on computer with nVidia. 64 Bit also. Downloaded ISO on Monday night.   :o

---

### Post by screaminj3sus on 2010-12-08
OSS drivers and unity work fine for me (mobility hd2600)

---

### Post by rajeev1204 on 2010-12-08
> **sonicb00m said:**
> I have the HD5450. I wish i had stuck with Nvidia instead of buying an ATi for a change.

Let me rephrase that for you.

'You wish you had stuck with ubuntu 10.10 instead of 11.04 alpha1.' ;)

---

### Post by sonicb00m on 2010-12-09
haha no such problem! I have 10.10 as my main installation and 11.04 on a test partition.

I'm not that satisfied with the card in Linux. The HD video playback is not that great even with the proprietary driver. It works well in windows though.

---

### Post by Reiger on 2010-12-09
The main issue is one of support. It's “getting there” but there's a lot of stuff that needs work doing still. Just like the nouveau drivers for that matter.

---

### Post by Cerebrux on 2010-12-21
Currently there is a HUGE bug and uncertainty about the Unity in combination with proprietary ATI/AMD Hardware drivers:

[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/685682](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/685682)
Still there is no news about how to fix this.

---

### Post by Harry33 on 2010-12-21
Well, huge or not.
Sometimes these bugs concerning proprietary drivers are troublesome.
It is clear that Canonical nor any other linux community cannot debug and fix the source, if the problem is in AMD/ATI.
I have wittnessed an argue between Nvidia Corporation and one Ubuntu devs concerning one application library and nvidia-current.

---

### Post by jerrylamos on 2010-12-22
> **Harry33 said:**
> Well, huge or not.
Sometimes these bugs concerning proprietary drivers are troublesome.
It is clear that Canonical nor any other linux community cannot debug and fix the source, if the problem is in AMD/ATI.


From a user's standpoint the problem is "Compiz" using code paths that no other software uses.  "Compiz" has been causing trouble since Intrepid.  From a user's standpoint, the "debug and fix the source" should be done on "Compiz" since all my real applications run fine.

Jerry

---

### Post by Harry33 on 2010-12-22
> **jerrylamos said:**
> From a user's standpoint the problem is "Compiz" using code paths that no other software uses.  "Compiz" has been causing trouble since Intrepid.  From a user's standpoint, the "debug and fix the source" should be done on "Compiz" since all my real applications run fine.
Jerry

Yes I know ATI proprietary drivers and Compiz has been a pain in the a.. for some time.
So much that I decided to give upp and bought a bit more than year ago Nvidia 285GTX.
Well, the problems with Compiz ended there. Nvidia and Compiz run fine together.

---

### Post by screaminj3sus on 2010-12-22
> **Cerebrux said:**
> Currently there is a HUGE bug and uncertainty about the Unity in combination with proprietary ATI/AMD Hardware drivers:

[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/685682](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/685682)
Still there is no news about how to fix this.
Isn't it just because fglrx doesn't support the 2.6.37 kernel yet? This happens during every ubuntu development cycle... I know 11.1 will, not sure when it will support 2.6.38 which will probably ship with the final natty.

> **Harry33 said:**
> Yes I know ATI proprietary drivers and Compiz has been a pain in the a.. for some time.
So much that I decided to give upp and bought a bit more than year ago Nvidia 285GTX.
Well, the problems with Compiz ended there. Nvidia and Compiz run fine together.

Compiz works wonderfully for me in maverick with fglrx and an hd2600. Ati's drivers have massively improved from where they were a year ago.

---

### Post by Harry33 on 2010-12-22
> **screaminj3sus said:**
> 
...
Compiz works wonderfully for me in maverick with fglrx and an hd2600. Ati's drivers have massively improved from where they were a year ago.

Well my woman has a desktop with Maverick-64bit and an ATI HD2600 Pro. She is using the open source radeon driver (xorg-edgers PPA), fglrx simply is not that good.
BTW. Isn't it so that ATI has dropped the support of HD2000 series in their newest fglrx drivers.
At least this has happened several months ago in Windows.

---

### Post by screaminj3sus on 2010-12-22
> **Harry33 said:**
> Well my woman has a desktop with Maverick-64bit and an ATI HD2600 Pro. She is using the open source radeon driver (xorg-edgers PPA), fglrx simply is not that good.
BTW. Isn't it so that ATI has dropped the support of HD2000 series in their newest fglrx drivers.
At least this has happened several months ago in Windows.

Nope, 2xxx series is still supported. And on a laptop fglrx is far better than the oss drivers. Even with latest kernel and xorg edgers ppa power management on the open source drivers is ridiculously bad.

Also I happen to know the 11.1 fglrx drivers has some really nice fixes coming >_>

2xxx series is still supported by catalyst in both windows and linux.

only 1xxx series and below isn't

---

### Post by bardic on 2011-04-04
Hey all,
I'm still experiencing this with beta 1. I see [here]("https://bugs.launchpad.net/unity/+bug/681915") that a fix has been released. How would I go about getting this fix?


thanks!

---

