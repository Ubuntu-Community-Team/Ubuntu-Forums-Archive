---
title: "sound skipping and stuttering since fresh install of ubuntu 10.04"
date: 2011-06-25
forum: Multimedia Software
---

### Post by monkey in orbit on 2011-06-25
I know this is a problem which affects many people and i have found many different threads about this but solutions seems to be specific to each.
In my case i've been having this problem since fresh install (which i tried twice). The stuttering and skipping happens with any program i've tried, rythmbox, vlc, totem, youtube etc..

here's my info:
[http://www.alsa-project.org/db/?f=373e299edb1e7c053070418c170710510da29c32](http://www.alsa-project.org/db/?f=373e299edb1e7c053070418c170710510da29c32)

I've already tried a few things:
-first i tried playing around with the alsamixer, any setting i tried gave no result for this problem
-second i tried to tweak the line "load-module module-udev-detect tsched=0" which made the problem worst as sound would radomly stop or if i was online then id get a bunch of distortion etc..
-third i've upgraded alsa but problem still persists, i think it might be a little better but it still cant go 2mins without skipping and stuttering.

I know many say to just remove pulseaudio but since its the intergrated sound device in ubuntu i'm hesitant on doing this for fear of loosing functionality, but If its the only solution for me to have sound without stuttering then i'll do it.

Could anyone give me some assistance or guidance with this?
thanx!

---

### Post by lidex on 2011-06-26
Where did you get that kernel? The only one I saw in lucid-updates was 2.6.32.32.38

Try booting a different kernel. Also you mentioned an alsa upgrade yet you are not at the latest version - see signature. But first you should try resetting your pulse configuration.
Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* ~/.pulse-cookie 
sudo rm /etc/asound.conf
```
**Reboot**
* Ignore any 'No such file or directory' errors*

---

### Post by monkey in orbit on 2011-06-27
Thank you for your help,

About the kernel, i got it in an recent update, its from june 19th i beleive.

i did get "no such file or directory" msgs when i ran the terminal after inputting those codes. Rebooted.. same stutters.

The ALSA upgrade, the most recent i found was 1.0.23.. Should i try updating that to the one in your sig?

---

### Post by lidex on 2011-06-27
> **monkey in orbit said:**
> Thank you for your help,

About the kernel, i got it in an recent update, its from june 19th i beleive.

i did get "no such file or directory" msgs when i ran the terminal after inputting those codes. Rebooted.. same stutters.

The ALSA upgrade, the most recent i found was 1.0.23.. Should i try updating that to the one in your sig?

It may help.

---

### Post by monkey in orbit on 2011-06-27
well on first run the upgrade itself seem to work with no extra config needed, different programs sounds great but it hasnt changed the stuttering skipping problem. :(

I do get 50% peaks in system resources when this happens and it seems  to happen more often when i'm doing things, browsing, typing etc. but i'm not talking about doing anything heavy, just the normal cpu use and i'm running on 3g of ram, this shouldnt be happening.

Should i just purge pulse audio? Or is there a way I can just shut it off to test and see if it makes a difference in a positive/negative way?

Sound is **really** important to me, it's starting to drive me nuts.

---

### Post by lidex on 2011-06-27
Have you tried this:
```
Q. PulseAudio is working correctly, but I am noticing some stuttering on my system. Is there anything I can do to help?
A. Edit the file /etc/pulse/daemon.conf:
Code:

$ gksudo gedit /etc/pulse/daemon.conf

Find the following lines (usually at the bottom):
Code:

default-fragments = 8
default-fragment-size-msec = 10

Try experimenting with different values for both of these entries. I can't tell you what values are optimal for your system, as each sound card has different buffer sizes and characteristics - therefore you'll need to use trial & error. The default fragment amount and size used by an untweaked PulseAudio installation is 4 and 25, respectively.

Note 1: you must restart pulseaudio for any configuration changes to take effect.
Note 2: If your system was stuttering in versions of Ubuntu prior to Hardy, then you could be suffering from an ALSA kernel issue - these instructions probably won't help.
```

---

### Post by monkey in orbit on 2011-07-04
Once again thanks for the help and sorry for the delay in responding..

i've played around with the values.. 
I seems to have found some values to make it a little better so hopefully continuing to play with them will bring the problem to stop eventually.. I hope i'm on the right track.

If I change the values to, lets say 20 and 25 and then to 4 and 10, it doesn't seem to make that a big a difference from one to another.. Would it be because I have to be very precise in finding the right ones for my system or would it normally bring a big difference in how my sound reacts to such bing swings in value changes?

---

### Post by lidex on 2011-07-06
Try this using a Terminal="Applications->Accessories->Terminal"
```
echo "options snd-hda-intel model=laptop position_fix=1 enable=yes" | sudo tee -a /etc/modprobe.d/alsa-base.conf
``` **Reboot**

---

