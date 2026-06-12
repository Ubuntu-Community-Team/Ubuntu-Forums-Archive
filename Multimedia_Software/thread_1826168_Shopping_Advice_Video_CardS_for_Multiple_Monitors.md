---
title: "Shopping Advice: Video CardS for Multiple Monitors"
date: 2011-08-16
forum: Multimedia Software
---

### Post by muddyh2o on 2011-08-16
Hey guys

I'm about to start a new build for my primary machine at home.  The plan is to load up a server/workstation motherboard (ASUS KGPE-D16) with two 8-core chip, as much RAM as it will take (32GB) and to put two graphics cards in it.  One to power my main 24" monitor (ideally via HDMI) and the other card to power two screens, one 24" on each left and right side via DVI (unless I can find a dual-HDMI card that meets my needs).

Does that make sense?

Here's my question for this awesome group of intelligent individuals:

What video card model should I choose?  Obviously, I'd like them to match so I can SLI / CrossFire if I really want to, but what setup should I plan on to have a good experience managing multiple displays on multiple video cards?

Oh, and budget is probably up to about $300 per card, maybe a little more if it makes a lot of sense.

I'm not alone in having tons of problems with trying to get multi monitor support in the last few versions of Ubuntu, and honestly it's the only reason why I'm still running Windows7: the multi monitor support is just SO DAMNED easy! :)  I shouldn't have to spend this much energy thinking about video card model- it should just work, shouldn't it?

Thanks in advance for your help.

-j

---

### Post by muddyh2o on 2011-08-25
80 views. 

0 replies.

Did I poorly write the message?

Did I ask a stupid question?

I just want to know what's recommended for a dual-card, triple-head setup on Ubuntu for a desktop.

Thanks again in advance.

---

### Post by thewolfman on 2011-08-26
Hi Muddy,

I cannot give you advice on what card to buy but I can tell you that you should not buy any card that has a SIS chip in it as it is not supported. (they went out of business anyway!!). Only Mandriva based systems still offer SIS support but it is not the "bee's knee's" if you know what I mean!!.

Regards thewolfman:p

---

### Post by mjwaters on 2011-08-26
I am looking for a new graphics card too. I don't need much, $100 max. 

My X800pro's fan is slowly dying and its being funny about large images and starting video playback. I'm sure there is a software fix for the bugs and I could jury rig the fan, but I don't have a lot of free time.


**TL;DR: Has anyone had good experience with a certain card or could recommend a certain chipset ?**

---

### Post by BicyclerBoy on 2011-08-26
@ muddywater..
Multi-monitor support is not very good compared with windows but this not surprising as there are a lot more separate problems in the way..kernel Xorg close source drivers.etc..
Xorg Xinerama was the old multi-monitor solution but it breaks openGL performance.

Do you want one big desktop or separate X screens.
Do you want openGL or video performance ?

I'm definitely no AMD/ATI fanboy but their eye-finity multi-monitor support may do what you want.

nVidia consumer cards only allow dual monitor twinview or multi-monitor separate X screens.
nVidia pro quadro cards allow mosaic & sli-mosaic.

The top-end AMD/ATI card has 4 outputs.
The current top-end nVidia fermi card has 3 outputs.

$300 does not go very far in my corner..2x US price here.
$300 may get you a GTX550 but this may be slower than the old GTX260 (216OC).
But you get VDPAU feature set C (GTX260 is  A)

The linux nVidia driver has always been superior to AMD drivers.
AMD video decode (out-of-the-box) is rubbish.
But the latest AMD card has better openGL performance & lower power dissipation.

---

