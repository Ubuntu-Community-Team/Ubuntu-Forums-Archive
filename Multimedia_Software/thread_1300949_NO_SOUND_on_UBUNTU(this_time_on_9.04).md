---
title: "NO SOUND on UBUNTU(this time on 9.04)"
date: 2009-10-25
forum: Multimedia Software
---

### Post by gariden on 2009-10-25
Hi everyone,

I'm kinda new on ubuntu and I have limited knowledge on linux. I've seen lots of forums everywhere to try to solve my problem but I was unsucessfull. I know it's a usual thread, but i'd thank really much any help on this. Just ask all the information you will need. Thanks!

---

### Post by Dorrax on 2009-10-25
OSS worked for my laptop. Look it up. ALSA is the default sound driver for ubuntu, and it doesn't work with a lot of soundcards.

---

### Post by gariden on 2009-10-25
Hello Dorrax, 

tnks for ur fast replay :). I've already tried alsa, OSS, and pulse audio has my sound drivers. I changed them through the system->preferences->sound menu and it didn't work out.
There's something important about my hp pavillon dv3 notebook pc: I've made a dual boot with windows vista through grub. Windows gets the sound perfectly. Could there be any relation with this?

Tnks in advance
Gariden

---

### Post by AutoStatic on 2009-10-26
Hello gariden, if possible could you post the output of the following command in a terminal?
```
aplay -l && lspci | grep -i audio && cat /proc/asound/card*/codec#* | grep -i codec
```
You can paste the command in the terminal with ctrl+shift+v.

---

### Post by KeLa on 2009-10-26
Here is my post to another thread about this problem:
[http://ubuntuforums.org/showpost.php?p=8129309&postcount=10](http://ubuntuforums.org/showpost.php?p=8129309&postcount=10)

Also notice that after every kernel update you have to do the driver update again.

---

### Post by AutoStatic on 2009-10-26
No. Updating Alsa is not the way to go.

---

### Post by gariden on 2009-10-26
Hi autostatic.
Here it is.

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
Codec: IDT 92HD75B2X5
Codec: Generic 10de ID 3

Thank you!

---

### Post by Ulysses361 on 2009-10-27
Please try this solution:

[https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/81520](https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/81520)

---

### Post by gariden on 2009-10-27
Hi!
Thank you Ulysses361! It works! Now I have sound!
But I've another problem...:(
The sound isn't work correctly. It sounds like hiccups...
What can I do?
Thank you again for your help!

---

### Post by Ulysses361 on 2009-10-27
@gariden: are you using model option hp-hdx in both the alsa-base.conf file and options.conf file?

Make sure to set the volume on all channels to 77% (instead of 100%).

If that does not help, try upgrading to ALSA 1.0.21 using this link:

[http://monespaceperso.org/blog-en/2009/08/31/upgrade-alsa-1-0-21-on-ubuntu-jaunty-9-04/](http://monespaceperso.org/blog-en/2009/08/31/upgrade-alsa-1-0-21-on-ubuntu-jaunty-9-04/)

Keep mixer volume at 77% for all channels.

---

### Post by AutoStatic on 2009-10-28
Hello gariden, how does your */etc/modprobe.d/alsa-base.conf* file look now?
Maybe you could add an extra line to this file:
```
options snd-hda-intel enable_msi=1
```
This will hopefully prevent the hiccups.

Source: [https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/64930](https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/64930)

---

### Post by gariden on 2009-10-28
Hi! 
I tried to add the line "options snd-hda-intel enable_msi=1" in [I]/etc/modprobe.d/alsa-base.conf
but it didn't work...

[/I]Ulysses361: 
I don't understand. So I have to add the 3 lines:
alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel
options snd-hda-intel model=hp-hdx
in options.conf file?
And how I set the volume in all chanels?
Sorry for so much questions.
Thank you for all the help

---

### Post by Ulysses361 on 2009-10-29
You can adjust the volume to 77% on the different channels using alsamixer or gnome-alsamixer.

If gnome-alsamixer is not installed on your pc, please run these commands:

sudo aptitude update
sudo aptitude install gnome-alsamixer

---

### Post by gariden on 2009-10-29
It's SOLVED!!! :):o:popcorn:
Thanks a lot to everyone!! I guess it was only a matter of rebooting, since the next time I turned my PC on the sound got right, without hiccups!

Thanks again for all the help everyone.

---

### Post by kolslorr on 2009-10-29
I skipped intrepid because of this sound problem, but U sir, u solved my problem in Karmic.

Thanks!

---

