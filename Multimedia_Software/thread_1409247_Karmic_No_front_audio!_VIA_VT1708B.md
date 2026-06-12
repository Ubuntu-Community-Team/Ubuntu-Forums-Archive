---
title: "Karmic: No front audio! VIA VT1708B"
date: 2010-02-17
forum: Multimedia Software
---

### Post by Michael%S on 2010-02-17
I spent over an hour today and over an hour last night googling and trying everything and so far no success. I found many threads with oddly similar complaints, but their solutions haven't worked for me. So here's the story:
Last week I upgraded my system, basically a complete overhaul (in the old case). The new system is based on an ASUS MB which comes with VIA VT1708B audio onboard. I installed the latest 32-bit Linux Mint on it. The case's front audio jack doesn't work, the rear audio works but is too quiet.

_Things I have tried that have not worked:_
[LIST]
[*]Different combinations of settings in the basic sound preferences dialog, the GNOME ALSA mixer, and the PulseAudio volume control (I've probably played around with these so much that I've tried every combination)
[*]The ALSA backports package. Installed smoothly but no change resulted.
[*]The ALSA update script. I ran it several times, restarting each time. The version I get via cat /proc/asound/version stays at 1.0.21, whereas the terminal-based alsamixer seems to have been successfully upgraded to 22.
[*]The adjustment to the ALSA config described here: [link](http://ubuntuforums.org/showpost.php?p=8229137&postcount=13). I tried it twice (before the last restart, and at some point in my attempts last night) and it has done no good so far. (In between I made most of my attempts with that line removed.)
[/LIST]


Observations that might be relevant:
-When I click on "Independent HP" in the GNOME ALSA window, no new track appears, and the toggle is unselected again when I quit and reopen the dialog. In the terminal's alsamixer Indep. HP can be unmuted, and stays that way. (But it doesn't help)
-The front audio worked at some point during installation, perhaps when I installed Windows XP, I don't remember anymore.
-The speakers themselves still work - they're plugged into my laptop as well as my desktop and have been working there as good as ever. They also work fine when plugged into the back of the desktop, but then the volume is too low for some things.

I'd be willing to install a clean Karmic install if it may help, but I doubt it. I may just do it anyway because I forgot to take the 64-bit edition when installing and I'm kind of sick of some things about Mint... But I have other stuff to do right now.

I don't know what other information might help... Here's aplay -l's output, in case that's any use:
```
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: VT1708B Analog [VT1708B Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 0: SB [HDA ATI SB], device 1: VT1708B Digital [VT1708B Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

And here's an alsa-info dump from right now: [http://paste.ubuntu.com/378440/](http://paste.ubuntu.com/378440/)

All help much appreciated!!!
Michael

---

### Post by hemimaniac on 2010-02-17
Sounds like another reason to head back to jaunty until the LTS is released, imo the dev team have totally lost their minds. They took a fairly problem free distro and basically "partially" stripped out soon to be replaced code to only replace it with partially completed code. I have never witnessed such an outburst in the number of hardware/compatability complaints around a release such as this one?

Such things such as asoundconf-gtk [as an example(wich is the default for most people that have been around long enough to see the amount of tutorials developed around it)], is there, but not there, wtg!

I have piled my Karmic disks in the soon to be coaster pile, or was it really a vista release skinned as ubuntu, hard to tell with the problems surrounding it, yet it is called the linux distro that my grandother can use?, PLEASE. She could use jaunty no problem, even reinstalled it herself, this stuff "Karmic" I wouldn't wish on an enemy let alone a family member. I have been a fan of ubuntu and ubuntu based flavors for quite some time, especially those who wish to embrace OSS, but this here, might actually get that annoying uncle to stop calling if you install it on his computer, he will become an enemy and you will be considered an ememy of the state, neat way to get you out of those awkward Christmas dinners you never liked going to anyway......

---

### Post by Michael%S on 2010-02-17
Yeah, I've been thinking about switching back to Jaunty... But really Karmic has generally been great, except for this stuff now.

Anyone try the Lucid Alpha? As an LTS I'd guess it's less buggy than alphas generally might be... Maybe I can just switch early.

btw, I just tested the front jack on Windows to make sure. Sure enough, it works perfectly. But I'm not so desperate yet as to use Windows for anything but gaming. :)

---

### Post by Michael%S on 2010-02-18
I would really appreciate some help here. If someone in the know could at least indicate whether there is a solution in Karmic that would be helpful. I can downgrade to Jaunty and wait for Lucid. I just need to know if there's a solution to wait for here. :\

:popcorn:

---

### Post by Michael%S on 2010-02-21
I've managed to get the ALSA Update script to work (thanks, tahutchinson), but front sound still doesn't work. In alsamixer now I can't switch Independent HP on, I don't know if that's a good thing or a bad thing.
Any ideas, anyone?

---

### Post by draco31.fr on 2010-02-21
Hi guys,

I've got the same problem with the "Independent HP" control.
My card is a VIA VT2020 (onboard card on ASUS P7P55D Deluxe motherboard).

I tried different versions of alsa-driver.
From the repository, it doesn't work : card is not supported.
From alsa-driver-1.0.21.37.g604cb.405.g80b0d : all works fine, including "Independent HP" control.
Until alsa-driver-1.0.22.1 : some troubleshooting with some controls ...
From alsa-driver-1.0.22.1 and newer : all OK, except the "Independent HP" control.

I'm trying different git version to see if this will be solved, but nothing from now.

PS : sorry for my bad english.

I can send you the source for revision alsa-driver-1.0.21.37.g604cb.405.g80b0d, if you want to test yourself (I think the tarball isn't avaible on the alsa site).

---

### Post by Michael%S on 2010-02-21
Thanks, but I don't really have the time to experiment so much right now. I really just want my system to work fully so I can keep enjoying it like I used to before the upgrade...

---

### Post by draco31.fr on 2010-02-23
I'm agree with you.
But I think that reinstalling Jaunty will spent you much time than trying to install a git version of ALSA.
Obviously, you cannot be sure that version will work fine on your system.
You can also just force the install of the old version of ALSA from the Jaunty repository.

---

### Post by Michael%S on 2010-02-23
> **draco31.fr said:**
> I'm agree with you.
But I think that reinstalling Jaunty will spent you much time than trying to install a git version of ALSA.
Obviously, you cannot be sure that version will work fine on your system.
You can also just force the install of the old version of ALSA from the Jaunty repository.

Right now I just have my speakers plugged in in the back... It's not great, because if I want to plug them into something else it's a bit of a hassle to get to the jack, but it's easier than starting to experiment with all of that stuff. :)

---

