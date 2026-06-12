---
title: "how do i fix sound for my debian 4.0"
date: 2008-03-11
forum: Multimedia &amp; Video
---

### Post by ELiz on 2008-03-11
Hi...
   Mine is a lenovo laptop... I installed debian in it... I found there was no sound... so i tried installing realtek audio driver (I read some where it might be useful)... But after this installation, with alsaconf soundcards are not detected.. think i installed the wrong driver..
these are the output for the following commands...

1. alsaconf
modinfo: could not open /lib/modules/2.6.18-4-686/kernel/sound/core/snd.ko: No such file or directory
modinfo: could not open /lib/modules/2.6.18-4-686/kernel/sound/core/snd.ko: No such file or directory
modinfo: could not open /lib/modules/2.6.18-4-686/kernel/sound/core/snd.ko: No such file or directory
Unloading ALSA sound driver modules: (none loaded).
Building card database...

2.  lspci -c|grep Audio

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

3. alsamixer
alsamixer: function snd_ctl_open failed for default: No such device

and in my /proc there is no asound folder....
how can i solve this problem.... i really dont want to reinstall my debian again... i am stuck with my project because of this audio problem..What should i do???
Eliz

:confused:

---

### Post by kerry_s on 2008-03-12
did you reboot?

---

### Post by ELiz on 2008-03-12
yup i did the reboot..:(

---

### Post by kerry_s on 2008-03-12
okay, rereading your post, the error message tells me your not running "alsaconf" as root

so type " su " put your password then start " alsaconf " as root.
after you reboot, then you can run " alsamixer " as your normal user(not root).

---

### Post by ELiz on 2008-03-12
yes i logged in as root... still teh problem persists... During installation of realtek driver i lost old drivers... so which sound driver should i install???

---

### Post by kerry_s on 2008-03-12
yeah, my guess is your installing the drivers screwed it up. you shouldn't need to install any drivers. just run alsaconf as root. i have no idea how to fix that. you could try removing completely the driver you put, alsa-base, alsa-utils. then install alsa-base and alsa-utils again.

---

### Post by ELiz on 2008-03-13
I solved my problem ... first reinstalled debian... did'nt have sound still... so followed this link
[https://wiki.ubuntu.com/LaptopTestingTeam/Lenovo3000C200_89224MG?highlight=%28CategoryLaptop%29](https://wiki.ubuntu.com/LaptopTestingTeam/Lenovo3000C200_89224MG?highlight=%28CategoryLaptop%29)

Eliz:)

---

### Post by souneedalink on 2008-03-13
I use Debian Lenny on my new R61e thinkpad and sound worked fine on install. jfyi

---

### Post by kerry_s on 2008-03-13
> **souneedalink said:**
> I use Debian Lenny on my new R61e thinkpad and sound worked fine on install. jfyi

i've done a couple of thinkpad's too, i never had to compile the drivers either, i can't remember the model #'s though. guess we just got lucky. :lolflag:

---

