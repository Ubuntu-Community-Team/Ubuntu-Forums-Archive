---
title: "Nvidia GT 430 no sound via HDMI after new kernel"
date: 2011-12-12
forum: Multimedia Software
---

### Post by cacycleworks on 2011-12-12
Hey Everyone,

If y'all would please, I'd like a quick yes/no answer to this situation:

I did the steps in [this thread]("http://ubuntuforums.org/showpost.php?p=11526509&postcount=18") and it worked. Then I let it update and the kernel went to next version. Is there a way to see if the people that release the linux-alsa-driver-modules PPA will update soon?

If they don't I will consider either reinstalling from the 10.04.3 CD or try to revert back out of the upgrade.

Thanks!!
Chris

---

### Post by cacycleworks on 2011-12-15
Bump -- would really appreciate someone's opinion if I should roll back the update (and/or reinstall 10.04.3) or just wait a while for the new ppa...

Thanks,
Chris

---

### Post by BicyclerBoy on 2011-12-16
I would not have installed the exact backports module from kernel devs (that matches your kernel).

What you should do is install the empty backports meta-package that always matches the kernel release. This way your install does not break with every kernel update.

This is what works with lucid:
The user space alsa library needs to updated from iQuik ppa BUT this does not work with ubuntu-audio-dev ppa.

Using synaptic package man:
un-install all packages from ubuntu-audio-dev ppa
install linux-backport-modules-alsa-lucid-generic
add the iQuik ppa
[https://launchpad.net/~team-iquik/+archive/alsa?field.series_filter=lucid](https://launchpad.net/~team-iquik/+archive/alsa?field.series_filter=lucid)

reload
mark all updates etc..

---

### Post by cacycleworks on 2011-12-17
Awesome, thanks! I'll go into work to try and mess with it tomorrow... :)

---

### Post by BicyclerBoy on 2011-12-17
Because you are using 10.04 pulse audio you will still need to find the right HDMI codec..& then add the appropriate entry to 
/etc/pulse/default.pa

The GT430 has 4 codecs/sub-devices.
Assuming your mobo sound is card0; amend below if required:

speaker-test -c 2 -r 48000 D hw:1,3
speaker-test -c 2 -r 48000 D hw:1,7
speaker-test -c 2 -r 48000 D hw:1,8
speaker-test -c 2 -r 48000 D hw:1,9
close/re-open terminal after each cmd if it works or fails..

hot plug events ELD etc:
dmesg | grep HDMI

one of these contains eld from monitor:
ls /proc/asound/card1/eld#*

---

