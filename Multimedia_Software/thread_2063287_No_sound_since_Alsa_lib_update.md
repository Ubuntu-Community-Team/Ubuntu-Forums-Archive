---
title: "No sound since Alsa lib update"
date: 2012-09-26
forum: Multimedia Software
---

### Post by SixStringSW on 2012-09-26
I'm running 64-bit Ubuntu 10.04 LTS on a Mac Mini. Sound has been iffy for a long time, not working for some users or situations, no sound over Skype, and when I'd run VLC, I'd almost always get a warning to update my alsa-lib (which was 1.21).

I updated it and now I have no sound whatsoever. I've been Googling all day and trying various solutions, but no joy.

Currently, here's what I see:

The speaker icon on my task bar appears to be muted but when I click on it, the sound volume is all the way up and the Mute All option is grayed out. If I click on Sound Preferences, the dialog shows no Hardware, and Output is set to Dummy Stereo.

aplay -l yields "no soundcards found."

lspci | grep -i audio yields "Audio device: nVida Corp. MCP79 High Definition Audio (rev b1)

cat /proc/asound/version yields "No such file or directory"

uname -a yields "2.6.32-41-generic #89-Ubuntu SMP Fri Apr 27 22:18:56 UTC 2012 x86_64 GNU/Linux"

GNOME ALSA Mixer (GUI) brings up a blank box.

alsamixer yields "No such file or directory"

pulseaudio yields "Daemon already running"

The last lines in my alsa-base.conf file are:
 
options snd-pcsp index=-2
options snd-hda-intel model=imac24

which is what I had before and (mostly) worked.

I'm not a Linux guru or anything, but I'm not a complete noob (tho' maybe you should treat me as one).

Help, please!!

---

### Post by BicyclerBoy on 2012-09-26
From a little reading it seems that:
snd-hda-intel model=imac24
is not very likely to be right..(for MAC pro laptop?)

The Mac mini
options snd-hda-intel model=macmini 
or 
options snd-hda-intel model=auto

Problem with iProducts is they change the h/w but not the model descriptors.

My 10.04.3 box has been running alsa 1.0.24 for ages..(1.0.23 kernel modules)

---

### Post by SixStringSW on 2012-09-26
No joy. It's one of the older Mac Minis, circa 2009.

---

### Post by BicyclerBoy on 2012-09-27
I think your mac mini is a core2duo with ION/9300/9400m chipset graphics (MCP79).

The 24" iMac used the MCP79 at one point.

Should work with no modprobe options.
Often the options are needed to get the jacks in the right place etc.

Could try these options:
mbp55 or imac27

With Ubuntu distros nVidia recommend running:-
sudo update-initramfs -k all -u
 after changing /etc/modprobe.d/*.conf files.

If want to try something else; upgrade alsa..(easy said than done).
I have been using these packages in lucid.
In proposed lucid:-
linux-backports-modules-alsa-lucid-generic
User space alsa 1.0.24:-
iquik alsa lucid ppa 

I would try the backports module first (1.0.23), the iquik ppa was recommended for getting HDMI audio working etc..
Try your different modprobe.d options but if aplay -l fails to list any cards it is hopeless.

---

### Post by SixStringSW on 2012-09-27
As I originally said, it was more or less working until I updated from 1.0.21. The update script updated all kinds of stuff, so no telling what got screwed up.

Is there a way to essentially wipe the entire sound driver setup and reinstall from scratch?

---

### Post by SixStringSW on 2012-09-27
I really think the problem lies in the fact I get "no such file" trying to run alsamixer, even as root. (Though I am in the audio group.)

If I try to force-reload alsa, I'm told no sound driver modules are loaded. Since lspci sees the card, it seems to be an alsa driver problem. Also, alsaconf reports "No PCI cards found."

Linux and sound drive me crazy.

---

### Post by BicyclerBoy on 2012-09-27
Yes that is the problem, that is what I assumed. Very remiss of me not to suggest checking user groups (audio) & trying
sudo aplay -l
(good check of permissions problems)

The linux-backports-modules--generic: are kernel modules updates that match your kernel.
This is where the fix has to come from..

Can you look thru output of:
dmesg
(see any warnings errors?)

Can you reboot via grub screen, holding down <shift> key.
Select oldest kernel image listed.
Does sound work (aplay -l) ?

Not sure you can blame alsa or kernel without prove..There are h/w data tables in the BIOS that are often the root cause.

---

### Post by SixStringSW on 2012-09-27
> **BicyclerBoy said:**
> Yes that is the problem, that is what I assumed. Very remiss of me not to suggest checking user groups (audio) & trying
sudo aplay -l
(good check of permissions problems)

The linux-backports-modules--generic: are kernel modules updates that match your kernel.
This is where the fix has to come from..

Can you look thru output of:
dmesg
(see any warnings errors?)

Can you reboot via grub screen, holding down <shift> key.
Select oldest kernel image listed.
Does sound work (aplay -l) ?

Not sure you can blame alsa or kernel without prove..There are h/w data tables in the BIOS that are often the root cause.

aplay -l says "No sound cards found," even as sudo.

A few lines from the end on dmesg says:

   76.951820] gnome-alsamixer[2682]: segfault at 0 ip 0000000000405c78 sp 00007fff7ecda2e0 error 4 in gnome-alsamixer[400000+e000]

I'll try booting to an earlier kernel (I'm using 2-6-32-41). 

Why would updating the alsa-lib cause this?

---

### Post by BicyclerBoy on 2012-09-27
The user space libs/utilities talk to the kernel space layer.

The gnome-alsamixer error is likely another symptom & not the cause.

Your problem may have got worse with a recent kernel updates..
"lucid proposed" got a new one yesterday (2.6.32-43?)

---

### Post by SixStringSW on 2012-09-27
I'm using 32-41, which seems to be the problem. I booted to 2.6.32-32, and I'm back where I was: sound works, but with some problems.

alsamixer now works fine.
aplay -l now shows my sound card.

However, the volume icon on my task bar still looks like it's muted. When I click it, "Mute All" is grayed, there is no volume slider, and clicking on Sound Properties brings up a message box saying "Waiting for sound system to respond." 

But I do have sound again. I'd sure like to eliminate the above problems though.

---

### Post by BicyclerBoy on 2012-09-28
The system wide settings are pulse audio..
Install run from terminal: 
pavucontrol
- this so much more flexible/useful than gnome sound thing..
- does it show pulse server running ?

The linux-backports-modules-alsa-generic package is a wrapper for a kernel matching package..

All the lucid kernels are supported, this is the best chance to fix..
You can just uninstall it if it does not work..

---

### Post by SixStringSW on 2012-09-30
> **BicyclerBoy said:**
> The system wide settings are pulse audio..
Install run from terminal: 
pavucontrol
- this so much more flexible/useful than gnome sound thing..
- does it show pulse server running ?

The linux-backports-modules-alsa-generic package is a wrapper for a kernel matching package..

All the lucid kernels are supported, this is the best chance to fix..
You can just uninstall it if it does not work..

pavucontrol is already installed, apparently. When I try to execute it, I get "Connection failed: access denied." Same with running it as sudo.

---

### Post by BicyclerBoy on 2012-09-30
sudo apt-get install linux-backports-modules-alsa-generic
(you can always un-install it)

If you want HDMI audio then:
add the iquik ppa

---

