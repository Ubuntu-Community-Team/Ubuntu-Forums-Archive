---
title: "Sound/Video Driver Conflict"
date: 2008-04-22
forum: Multimedia Software
---

### Post by Fubini on 2008-04-22
Hello,

I'm completely inexperienced with Linux, and it was not too long ago I decided to try out Ubuntu in a dual-boot configuration. I have an nVidia 7600 GT XXX edition from XFX and a Creative Audigy 2 soundcard.

Sound playback worked just fine without installing any sound drivers. I haven't tried to find or install any yet.

To get the video hardware working I first tried using the Restricted Driver Manager in Ubuntu. This works as far as getting the video card to work, but has the unfortunate side effect of stopping all sound playback.

When I disable this driver (always through that interface) the sound always works, but when I enable it the sound never works. In both cases the lspci command lists both the video card and sound card as recognized, with the only difference being that the video card gets assigned different IRQ channels (they aren't on the same one in either case).

Somehow the nVidia driver is interfering with the sound playback, but I really don't know where to start troubleshooting this sort of thing in Linux. Help would be appreciated.

Thanks,
Fubini

---

### Post by mrg201 on 2008-04-27
Hi,

I'm afraid I can't help, I just wanted to say that it seems alot of people have this problem, and that it is the same for ATI cards as well as nvidia. So it seems it is a problem with accelerated 3D using restricted drivers in general, not specific to nvidia. Nor is it specific to a particular sound card as I am using a standard laptop Intel ICH5 on-board card, whereas the previous poster is using a creative.

I was hoping someone may start addressing this considering it does seem to be a common problem. As far as I can tell it is not a driver issue as the drums at the log in work for me in both cases, it is just after I have logged in with my ATI driver activated that the sound breaks.

aplay -l, lspci -v all give sensible results.

Plus, installing the newest drivers from alsa-project doesn't help.

Changing the device being used to OSS by volume control has no effect either.

Nor is it a group or permissions issue as these are all correct.

I have tried clean installs of Hardy Heron and Feisty Fawn and used restricted manager as well as envyng to install drivers. All have same problem.

Oh, and alsamixer is picking up the card fine and all the alsamixer channels are unmuted, so I don't think it is that either.

As an example, here is the error splay gives me when trying to play an mp3 file:

Cannot open /dev/dsp or /dev/sound/dsp!
splay: Failed to open sound device.

Many thanks

---

