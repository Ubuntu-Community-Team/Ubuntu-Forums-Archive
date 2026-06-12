---
title: "Hauppuage HVR-1600 Reviews"
date: 2009-09-17
forum: Mythbuntu
---

### Post by bsntech on 2009-09-17
Hello all,

I am considering purchasing the Hauppauage HVR-1600 TV tuner to upgrade from my analog PVR-150 card.

The HVR-1600 has both an analog and digital tuner so I will be able to record the analog cable but also pick up the HD channels.

My question is this - I've read some buzz online about how the HVR-1600 has horrible analog tuner quality.  Others indicate (even with a posted e-mail response from Hauppauage Tech Support) that the PVR-150 is much more superior than the HVR-1600 for the analog tuner.

Does anyone have any kind of reference or experience between these two cards and just how "bad" the difference is between the two?

I am using MythBuntu with the PVR-150 currently and although the PVR-150 is supposed to record in stereo, it does not.  So I was hoping by doing the upgrade to the HVR-1600, I would get stereo recording through analog and I would also have the added bonus of having a digital tuner.

Thank you for any responses!

---

### Post by klc5555 on 2009-09-17
> **bsntech said:**
> Hello all,

I am considering purchasing the Hauppauage HVR-1600 TV tuner to upgrade from my analog PVR-150 card.

The HVR-1600 has both an analog and digital tuner so I will be able to record the analog cable but also pick up the HD channels.

My question is this - I've read some buzz online about how the HVR-1600 has horrible analog tuner quality.  Others indicate (even with a posted e-mail response from Hauppauage Tech Support) that the PVR-150 is much more superior than the HVR-1600 for the analog tuner.

Does anyone have any kind of reference or experience between these two cards and just how "bad" the difference is between the two?

I am using MythBuntu with the PVR-150 currently and although the PVR-150 is supposed to record in stereo, it does not.  So I was hoping by doing the upgrade to the HVR-1600, I would get stereo recording through analog and I would also have the added bonus of having a digital tuner.

Thank you for any responses!

I've always found my 1600 to be superior in analog recording quality to my pvr 150. No question, hands down. Even after many months of tweaking the pvr 150.

Digital reception on the 1600, however, I've found to be not even worth bothering with because of the serious signal-strength requirements (on QAM --never tried VSB). I eventually just disconnected the digital side of my 1600 and got a $40 cast-off Avermedia card to handle the SD/HD requirements on that particular backend. Much better. However, my 1600 remains in service as an analog-only card, pending Comcast nuking the last local analogs in a month or so.

---

### Post by bsntech on 2009-09-18
Good to know with the analog.

Have you found that when you had your PVR-150 that you had to adjust the contrast/hue/brightness quite a bit?  It seemed pretty bad when I first set it up, but after changing those values, it was better.

Is this same setup required for the HVR-1600 as well - where the picture controls need to be adjusted or is there some kind of auto-adjust built-in?  That is what is nice about the Hauppauage Windows application - it seemed to auto-adjust those for each channel changed to.

I got a cheap bi-directional coax amplifier (since I use cable Internet as well) so I am hoping that the extra +11 db gain will help out with getting those clearQAM channels.  I sure don't want to run another coax cable out of the house onto an antenna to use OTA digital.  If I do that, I might as well cancel my basic cable TV service and save $15 a month.

---

### Post by klc5555 on 2009-09-18
> **bsntech said:**
> Good to know with the analog.

Have you found that when you had your PVR-150 that you had to adjust the contrast/hue/brightness quite a bit?  It seemed pretty bad when I first set it up, but after changing those values, it was better.

Is this same setup required for the HVR-1600 as well - where the picture controls need to be adjusted or is there some kind of auto-adjust built-in?  That is what is nice about the Hauppauage Windows application - it seemed to auto-adjust those for each channel changed to.

I got a cheap bi-directional coax amplifier (since I use cable Internet as well) so I am hoping that the extra +11 db gain will help out with getting those clearQAM channels.  I sure don't want to run another coax cable out of the house onto an antenna to use OTA digital.  If I do that, I might as well cancel my basic cable TV service and save $15 a month.

 A fair amount of recording brightness/hue/contrast/etc. fiddling with the pvr 150. None of that with the analog side of the 1600.

The only fly in the analog side of the 1600 is the somewhat flakey cx18 kernel driver it depends on. First of all, it will require the vmalloc parameter to be set in the kernel line in grub in order to load together with the module for the NVidia driver. 

Second, even though the "first capture" problem mentioned in the mythtv wiki entry on the 1600 has been fixed in recent iterations of the cx18 driver, (kernels newer than 2.6.26) nevertheless the driver doesn't always load correctly at boot. The symptoms will be either scratchy noise instead of audio from the card, or occasionally a blank screen from it. The workaround consists simply of unloading and reloading the cx18 module: i.e. stop the backend (because mythbuntu is particularly annoying that way), sudo rmmod cx18, sudo modprobe cx18. Restart the backend. And then it works.

The analog side of the 1600 is, all-in-all quite good. I just wish the digital half of it sucked less.

---

### Post by bsntech on 2009-09-18
Good to know.

The more I've been reading online about the analog and digital stuff, it is getting a little out of hand.  It seems that now the FCC is no longer requiring clearQAM of the local channels to be broadcast - so that defeats your digital tuner - unless you use it for OTA channels.

In addition, many cable providers are decommissioning their analog altogether - which means either way, an external cable box would be required for each TV in the house - here comes more fees!

I might be reading too much into it and maybe they will still be required by the FCC to carry at least your locals in analog (afterall, that was the big push for the DTV transition is that those with satellite or cable wouldn't need a converter box).

Glad to hear that the analog is fixed with the picture controls.  I'll still have to fudge with the controls though for the PVR-150 since I plan to keep it installed in the event there are two things on simultaneously that I want to record.  But, I'll set the HVR-1600 as the default.

I picked up the 74021 version with the clearQAM on eBay for $55 yesterday.  The guy has a different remote with it than what it came with, but I have the remote and such from the PVR-150 that I'll continue to use.

Hopefully the digital tuner will pick up some of those channels by amplifying the coax signal once it comes into the house.  Right now it comes from the electric pole to the house (probaby 30 feet), down the house (about 10 feet), all the way across the house to tie into the electrical grounding (another 20 feet), and then all the way back to the other side of the house where the first splitter is.  So that is a good 80 feet of coax before it even reaches the first drop.

---

### Post by dano1 on 2009-09-19
no problem with my hvr1600 after a few tweaks-see mythtv for most of em. works for me for the price, both analogue and digital(witch i rarely use-need a cable box to unscramble all but local signals but when i had one all looked great)

---

### Post by ahood on 2009-09-19
> **bsntech said:**
> Good to know.

The more I've been reading online about the analog and digital stuff, it is getting a little out of hand.  It seems that now the FCC is no longer requiring clearQAM of the local channels to be broadcast - so that defeats your digital tuner - unless you use it for OTA channels.

In addition, many cable providers are decommissioning their analog altogether - which means either way, an external cable box would be required for each TV in the house - here comes more fees!

I might be reading too much into it and maybe they will still be required by the FCC to carry at least your locals in analog (afterall, that was the big push for the DTV transition is that those with satellite or cable wouldn't need a converter box).

I can see the day where mythtv users will lose the freedom to record multiple shows simultaneously from cable companies. It probably isn't surprising to anyone that monopolies like cable companies results in charging more for less service. At least it seems that way.

Anyway, I hope mythtv developers continue development on Internet video sources. That way, when the time is necessary (i.e., I cannot record what I want to record without exorbitant restriction or high cost, I can dump cost of cable altogether.

Apologies for the rant.

Cheers!

---

