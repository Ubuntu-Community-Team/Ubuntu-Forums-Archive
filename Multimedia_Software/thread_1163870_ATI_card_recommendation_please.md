---
title: "ATI card recommendation please"
date: 2009-05-19
forum: Multimedia Software
---

### Post by coffeecat on 2009-05-19
I'm in the odd position of wanting to replace a nvidia card with an ati. Bear with me - I'll explain. 

I have two desktop machines. Desktop 1 has the nvidia MCP61P motherboard chipset with onboard VGA, but I use a PCIe nvidia Geforce 8400GS card and everything works fine graphics wise.

Desktop 2 - which is my main machine - has the nvidia GeForce 7025/nForce 630a chipset and I use an identical 8400GS card. This is the problem one. I'm convinced now that there is some obscure conflict somewhere between the onboard chipset, the nvidia PCIe card and the proprietary driver. I experienced [this issue]("http://ubuntuforums.org/showthread.php?t=965180&highlight=nvidia") with Intrepid. Numerous non-Ubuntu live CDs are simply incapable of configuring the xserver, so I can't try them out on this machine. And with Jaunty, if I try to log out and log in, the xserver hangs. This is all also true with another GeForce 7300 PCIe card. All these issues are resolved if I use the open source nv driver or the onboard 7025 graphics. Using the nv driver means I don't get compiz. The onboard graphics is a non-starter because then I can't plug into my DVI KVM switch.

So I'm willing to spend money to see if an ATI card will solve the issue. It's either that or a new motherboard, but then I'd have to re-activate Vista, and I don't want to go through that ordeal. :(

My requirements:

I don't game. Well, perhaps the odd bout of PPRacer to impress Windows users. :wink: I only want acceleration for compiz. So a modest spec is enough.

I hate noise, so I will look for a passively-cooled card - so again a relatively modest spec. But, please, if you have a fan-cooled card that works, post the chipset. I can search for a make that specialises in passive cooling.

Recommendations on **personal** experience if you can, please. I had a look at [this community documentation]("https://help.ubuntu.com/community/RestrictedDrivers/ATI") page where it implies that the old Radeon 9250 card will give you 3d and compiz with the open source ati driver. But it doesn't. I've got a PCI Radeon 9250 which was the work of a minute to slip in. No compiz, so I don't trust the rest of the page. It solved the logout-in problem though. 

Any suggestions short of telling me to get my head examined will be welcome. :p

---

### Post by coffeecat on 2009-05-20
So, that's an overwhelming vote of confidence in ATI cards then! :lol:

Actually, the problem is (possibly) solved - although I'm not holding my breath. Turns out it was a BIOS issue. I'd noticed that on the other machine, fitting a PCIe card automatically disabled the onboard graphics, but on this one it didn't. The output of lspci showed me both graphics sets, and I'd never been able to find how to disable the onboard one in the BIOS.

Well, this morning I did. Under Advanced chipset was a line "iGPU Frame Buffer Control" set to auto, and below that a greyed out line "VGA Share Memory" showing 256MB. It turned out that I had to set the first to manual, which let me get into the second and set it to disabled. That seems to have fixed most of the issues (fingers crossed), **and** I've got back 256MB of my system memory into the bargain. Can't be bad. Easy when you know how, but...

<sarcasm>
Round of applause, if you please Ladies and Gentlemen, to Phoenix for their wonderfully intuitive user interface.
</sarcasm>

:wink:

Anyway, if anyone does want to recommend an ATI card, I'd still be interested. For future reference you see.

---

