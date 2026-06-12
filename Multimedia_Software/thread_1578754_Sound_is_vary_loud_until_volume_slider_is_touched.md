---
title: "Sound is vary loud until volume slider is touched"
date: 2010-09-20
forum: Multimedia Software
---

### Post by Aaddron on 2010-09-20
Sorry if the title isn't clear, don't know how else to explain the issue. Basically every time I boot into Ubuntu any sound will be vary loud until I move the volume slider, it doesn't matter how much I move the slider as long as it moves then all sound will play at the normal volume and volume control works like it's suppose too until I reboot. This problem started in 9.10 and still happens in 10.04 and 10.10(as of a couple days ago).

As far as I can tell the issue only exists in Ubuntu, doesn't happen in Fedora(Gnome), OpenSuSE(KDE) or Kubuntu.

Running 10.04.1 32-bit, Logitech Clear Chat USB Headset, don't have any speakers.

---

### Post by Aaddron on 2010-09-21
Bump

---

### Post by Aaddron on 2010-09-30
Don't know if it's allowed but bump again, any ideas would be helpful. 

If it helps any, in the last week I've been told to try deleting .pulse directory and rebooting and to try using Alsamixer to adjust the volume then entering sudo alsactl store. Neither worked.

Lowering the volume in Alsamixer makes the volume quieter but as soon as I touch the volume slider the volume jumps to where it should be and is vary quiet because Alsamixer is way down.

So basically the problem is the volume is for some reason defaulting to max every time I start up the computer despite all the volume controls being at the normals levels/exactly where I left them when I shutdown the computer.

---

### Post by lidex on 2010-09-30
Have a look here:
[https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats](https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats)
Scroll down to the section "Volume range anomalies"

---

### Post by Aaddron on 2010-10-01
Thanks for the reply, "Volume not stored, or muted after reboots" sounds the most like my problem but according to the page it being debugged and the workaround is I think what I'm already doing (adjusting the volume after it's booted by touching the volume slider)

Tried amixer set and it didn't help.

Also tried the info under "Volume range anomalies" which had no effect.

Is there any way to track the progress of the debugging?

---

### Post by lidex on 2010-10-02
Have a look here:
[https://launchpad.net/bugs/bugtrackers/pulseaudio-bugs](https://launchpad.net/bugs/bugtrackers/pulseaudio-bugs)

---

### Post by Aaddron on 2010-10-04
Will do, thanks!

---

### Post by Aaddron on 2010-10-23
After going through all of the PulseAudio bug reports I couldn't find any that matched my issue. So I started my own(marked duplicate see bottom of post):

[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/661885](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/661885)

Also I previously stated that this bug didn't effect Kubuntu, as of 10.10 it now does which makes no sense until looking at the release notes:

"PulseAudio

**Kubuntu now uses the PulseAudio sound server by default.** **Building on the efforts of Ubuntu over the last several release cycles**, this system is now used by Kubuntu to give users enhanced configurability, flexibility and ease of use. System Settings and KMix have been updated to enhance Pulseaudio control integration."

This adds to my belief that this is a Ubuntu specific bug.

If anyone has any more ideas please post.

EDIT: Found an earlier bug report for this issue, here's the link:

[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/598308](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/598308)

---

### Post by forliberty on 2011-12-03
Aaddron found a fix for this that is referenced in one of the links in his post above, but for the ease of those googling this bug, here it is: 

1. sudo gedit /etc/pulse/daemon.conf

2. add a ; and a space to the beginning of this line:

   flat-volumes = no

3. Reboot

This solved the problem for me...it had been a minor annoyance for me ever since I loaded 10.04-64 on my machine.

---

