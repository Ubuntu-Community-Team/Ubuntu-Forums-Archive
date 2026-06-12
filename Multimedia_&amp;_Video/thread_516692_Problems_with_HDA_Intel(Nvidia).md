---
title: "Problems with HDA Intel(/Nvidia?)"
date: 2007-08-03
forum: Multimedia &amp; Video
---

### Post by J. Jones on 2007-08-03
Okay, first of all: I'm pretty new to Linux. I installed Ubuntu on a new desktop as a sort of summer project to keep me busy.

And, boy, has it ever.

The problem I can't seem to overcome here is my integrated audio card. To begin with, everything functioned perfectly - except recording. I couldn't do that in any program but audacity, and with audacity there would always be loud, high-pitched shrieking feedback. 

Now, according to the site I bought my computer from, my sound card is an Azalia ALC86-DTS. From what I hear, that means it's HDA-Intel, and my recording problems would make sense. However, Ubuntu recognized it as HDA-Nvidia, which had me confused for a long time as to what my sound card really was. My computer has an Nvidia 6150 chipset, though, and I hear that those usually have integrated Nvidia sound cards. And if they don't, sometimes operating systems have trouble picking up the replacement sound cards.

So that's the first problem: Intel or Nvidia?

I've been working under the assumption that it's an Intel sound card while I've been trying to fix it, and so I followed the directions that supposedly worked for everyone else and compiled the latest ALSA driver (1.0.14).

BIG mistake, apparently.

Now I have no sound at all, and Ubuntu doesn't even pick up a sound card. I've tried adding 'options snd-hda-intel model=3stack' to my computer,but that didn't help. My sound card's supposed to be six channels, but I'm confused as to what that means. It doesn't have any different audio-outs from a normal 3-channel sound card, except for S/PDIF.

THAT'S the second problem. What have I done to make Ubuntu NOT recognize my sound card anymore?

Honestly, at this point I'd settle for a way to get my old, imperfect setup back. At least it played sound, you know? I've tried uninstalling and reinstalling the ALSA driver packages through Synaptic, but when I run cat /proc/asound/version it told me that I was using the newer drivers that I'd compiled myself. Dang.

So, that pretty much sums up two months of frustration. Hope somebody can help.

EDIT: After trying a few more things, I thought I'd bring up a few more details that might be of use.

        -- The command alsamixer yields this result: alsamixer: function snd_ctl_open failed for default: No such device
        -- The physical sound card IS still recognized when I run commands like lspci -v, but NOT when I try to run anything that requires sound to play.

I'm almost convinced right now that the problem lies in something I did while installing the ALSA driver. Maybe the installed .deb version of the driver is conflicting with the version that I configured and installed myself? I haven't heard anything like that happening to other people, though. I'm in the dark.

EDIT 2: Alright, I updated the kernel and now I have sound again. No recording still, but sound. The new kernel must have replaced the drivers I 'installed' with its own, though, because cat /proc/asound/version now tells me I'm using ALSA 1.0.14rc1 as opposed to 1.0.14. Sort of afraid to upgrade the drivers again, but I DO want to be able to record eventually...

One more thing: My sound card type is now recognized as ALC861, which is the same as its HDA-Intel designation number. It's still called HDA Nvidia, though. I'm assuming that's because of my computer's chipset.

---

