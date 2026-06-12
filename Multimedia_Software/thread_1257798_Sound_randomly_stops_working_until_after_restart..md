---
title: "Sound randomly stops working until after restart."
date: 2009-09-04
forum: Multimedia Software
---

### Post by 98whbf on 2009-09-04
Hey all. I'm running intrepid ibex 8.10 on a thinkpad r400 laptop. every once in a while, mabey once every two days if i am lucky but a lot of times once a day the sound will just randomly stop working until i restart. i have check all the sound controls and verified that the speakers are working. after i restart all the settings are exactly the same but the sound works again. 

funny thing is this is a new computer and i had this exact same problem on my old computer which was a gateway??? i used the same speakers with that laptop, but i do not think it is them because even if you unplug the speakers the internal speakers will not play sound either
thanks all

---

### Post by scragar on 2009-09-04
Next time sound stops working try running:
```
sudo lsof | grep snd
```
And look at what's using your sound card. I've had this problem with deluge, once you find out what is locking up the sound card it's a simple matter of closing said program, testing sound again, and re-opening the program.

---

### Post by 98whbf on 2009-09-04
> **scragar said:**
> Next time sound stops working try running:
```
sudo lsof | grep snd
```And look at what's using your sound card. I've had this problem with deluge, once you find out what is locking up the sound card it's a simple matter of closing said program, testing sound again, and re-opening the program.

Thanks. Is there anyway to tell from the list what is locking it? Or is it just guess and check?

---

### Post by scragar on 2009-09-04
> **98whbf said:**
> Thanks. Is there anyway to tell from the list what is locking it? Or is it just guess and check?

When I run it and audio is working it looks like this:
```
[b][scragar @ sbox working in ~]
$[b] alsalock
Password: 
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/scragar/.gvfs
      Output information may be incomplete.
mixer_app  2736 scragar   21u      CHR              116,7       0t0       4505 /dev/snd/controlC0
```
When deluge has caused an audio problem it looks more like this:
```
[b][scragar @ sbox working in ~]
$[b] alsalock
Password: 
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/scragar/.gvfs
      Output information may be incomplete.
deluge   3754  scragar   .....
mixer_app  2736 scragar   21u      CHR              116,7       0t0       4505 /dev/snd/controlC0
deluge   3754  scragar   .....
deluge   3754  scragar   .....
deluge   3754  scragar   .....
deluge   3754  scragar   .....
deluge   3754  scragar   .....
deluge   3754  scragar   .....
deluge   3754  scragar   .....
deluge   3754  scragar   .....
deluge   3754  scragar   .....
deluge   3754  scragar   .....
```
It's really easy to see when is causing the problem.

---

### Post by 98whbf on 2009-09-04
> **scragar said:**
> When I run it and audio is working it looks like this:
```
[b][scragar @ sbox working in ~]
$[b] alsalock
Password: 
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/scragar/.gvfs
      Output information may be incomplete.
mixer_app  2736 scragar   21u      CHR              116,7       0t0       4505 /dev/snd/controlC0
```When deluge has caused an audio problem it looks more like this:
```
[b][scragar @ sbox working in ~]
$[b] alsalock
Password: 
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/scragar/.gvfs
      Output information may be incomplete.
deluge   3754  scragar   .....
mixer_app  2736 scragar   21u      CHR              116,7       0t0       4505 /dev/snd/controlC0
deluge   3754  scragar   .....
deluge   3754  scragar   .....
deluge   3754  scragar   .....
deluge   3754  scragar   .....
deluge   3754  scragar   .....
deluge   3754  scragar   .....
deluge   3754  scragar   .....
deluge   3754  scragar   .....
deluge   3754  scragar   .....
deluge   3754  scragar   .....
```It's really easy to see when is causing the problem.

Sorry all I'm not too good with computers yet / I might just be a complete buffoon but i can't tell what's causing the problem. Here's what mine looks like: 
```
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/98whbf/.gvfs
      Output information may be incomplete.
pulseaudi  5956        98whbf  mem       CHR      116,5               13340 /dev/snd/pcmC0D0p
pulseaudi  5956        98whbf  mem       REG        8,1   362800    2417016 /usr/lib/libsndfile.so.1.0.17
pulseaudi  5956        98whbf   21u      CHR      116,7               13380 /dev/snd/controlC0
pulseaudi  5956        98whbf   37u      CHR      116,7               13380 /dev/snd/controlC0
pulseaudi  5956        98whbf   38u      CHR      116,5               13340 /dev/snd/pcmC0D0p
gconf-hel  5959        98whbf  mem       REG        8,1   362800    2417016 /usr/lib/libsndfile.so.1.0.17
mixer_app  6044        98whbf   22u      CHR      116,7               13380 /dev/snd/controlC0
thebat.ex  6319        98whbf   10u      CHR      116,7               13380 /dev/snd/controlC0
explorer.  6324        98whbf   10u      CHR      116,7               13380 /dev/snd/controlC0

```

---

### Post by scragar on 2009-09-04
Are you running something in wine right now? I ask only because explorer.(exe?) and thebat.ex(e?) look to be windows applications.
If you aren't running wine start by killing those off:
```
killall explorer.exe thebat.exe
```
And check your sound, if it's still not working then it may be because of pulse audio(which used to cause problems with lots of people back when it was first introduced, but shouldn't be a problem now).
```
killall pulseaudio
```
I'd try killing off the wine applications first though, pulse hasn't been known to cause many people audio problems for almost a year(and even then it's mostly been people playing around with jack and a few programs that don't support audio), but I wouldn't rule it out completely.

---

### Post by 98whbf on 2009-09-04
> **scragar said:**
> Are you running something in wine right now? I ask only because explorer.(exe?) and thebat.ex(e?) look to be windows applications.
If you aren't running wine start by killing those off:
```
killall explorer.exe thebat.exe
```And check your sound, if it's still not working then it may be because of pulse audio(which used to cause problems with lots of people back when it was first introduced, but shouldn't be a problem now).
```
killall pulseaudio
```I'd try killing off the wine applications first though, pulse hasn't been known to cause many people audio problems for almost a year(and even then it's mostly been people playing around with jack and a few programs that don't support audio), but I wouldn't rule it out completely.

ok well a little update. I was running wine. i use my mail client with wine. I closed those programs and sound still didn't work. here is what the sudo lsof | grep snd looks like after killing those programs
```
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/98whbf/.gvfs
      Output information may be incomplete.
pulseaudi  5956        98whbf  mem       CHR      116,5               13340 /dev/snd/pcmC0D0p
pulseaudi  5956        98whbf  mem       REG        8,1   362800    2417016 /usr/lib/libsndfile.so.1.0.17
pulseaudi  5956        98whbf   21u      CHR      116,7               13380 /dev/snd/controlC0
pulseaudi  5956        98whbf   37u      CHR      116,7               13380 /dev/snd/controlC0
pulseaudi  5956        98whbf   38u      CHR      116,5               13340 /dev/snd/pcmC0D0p
gconf-hel  5959        98whbf  mem       REG        8,1   362800    2417016 /usr/lib/libsndfile.so.1.0.17
mixer_app  6044        98whbf   22u      CHR      116,7               13380 /dev/snd/controlC0
98whbf@98whbf-laptop:~$ killall pulseaudio
98whbf@98whbf-laptop:~$ killall gconf-hel
gconf-hel: no process killed
98whbf@98whbf-laptop:~$ killall mixer_app
mixer_app: no process killed

```as you can see i then tried to kill the pulseaudio, but sound still didn't work, and to be honest i'm not sure it did anything because there was no indication, but something may have happened, idk???
when i tried to kill the other things listed as you can see it says no process killed. Thanks for your help

---

### Post by scragar on 2009-09-04
The other two applications are called "mixer-applet" and "gconf-helper"

---

### Post by 98whbf on 2009-09-04
> **scragar said:**
> The other two applications are called "mixer-applet" and "gconf-helper"

well this is weird

```
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/98whbf/.gvfs
      Output information may be incomplete.
pulseaudi  5956        98whbf  mem       CHR      116,5               13340 /dev/snd/pcmC0D0p
pulseaudi  5956        98whbf  mem       REG        8,1   362800    2417016 /usr/lib/libsndfile.so.1.0.17
pulseaudi  5956        98whbf   21u      CHR      116,7               13380 /dev/snd/controlC0
pulseaudi  5956        98whbf   37u      CHR      116,7               13380 /dev/snd/controlC0
pulseaudi  5956        98whbf   38u      CHR      116,5               13340 /dev/snd/pcmC0D0p
mixer_app  6044        98whbf   22u      CHR      116,7               13380 /dev/snd/controlC0
98whbf@98whbf-laptop:~$ killall mixer_applet
mixer_applet: no process killed
98whbf@98whbf-laptop:~$ killall pulseaudio
98whbf@98whbf-laptop:~$ 
```i killed gconf-helper, so it is gone now. i killed pulseaudio and mixer_applet but they remain and sound still doesn't work

---

### Post by scragar on 2009-09-04
```
killall mixer_applet2
```
Sorry, for some reason it got renamed and I missed it.

Anything like the mixer applet which normally isn't in your list of applications will either need to be started again manually, or will ask you. Pulse audio should be started manually, press alt+F2 and type ```
pulseaudio
```, the mixer applet goes on the panels, so I think that should prompt you to restart it.

---

### Post by Baneblade on 2009-09-04
im having the same issue on my machines. To save me having to reboot all the time which can become quite tiresome Im currently doing this:

```
killall pulseaudio

sudo alsa force-reload

pulseaudio -D
```

which fixes it instantly as long as you ahve closed anything that is using sound before.

---

### Post by scragar on 2009-09-04
> **Baneblade said:**
> im having the same issue on my machines. To save me having to reboot all the time which can become quite tiresome Im currently doing this:

```
killall pulseaudio

sudo alsa force-reload

pulseaudio -D
```

which fixes it instantly as long as you ahve closed anything that is using sound before.

The problem is you shouldn't have to do that. If something is stopping sound from working once you've realised what it is you can file a bug report and it can be fixed, just forcing alsa to restart and continuing as if nothing happened doesn't help find and fix bugs, it just puts an expectation on other users to have to play about with this sort of thing when it should be fixed.

---

### Post by Baneblade on 2009-09-04
> **scragar said:**
> The problem is you shouldn't have to do that. If something is stopping sound from working once you've realised what it is you can file a bug report and it can be fixed, just forcing alsa to restart and continuing as if nothing happened doesn't help find and fix bugs, it just puts an expectation on other users to have to play about with this sort of thing when it should be fixed.

I couldn't agree more that sentiment, which is why i have already posted my findings on the active bug [here]("https://bugs.launchpad.net/ubuntu/+bug/398252") some time ago when I discovered this problem.

I posted the temporary fix above to assist other users while this bug is being fixed (should be by Karmic hopefully). Also please don't berate others on the forums, we are all here donating our time trying to help out each other. ;)

---

### Post by 98whbf on 2009-09-05
> **scragar said:**
> ```
killall mixer_applet2
```Sorry, for some reason it got renamed and I missed it.

Anything like the mixer applet which normally isn't in your list of applications will either need to be started again manually, or will ask you. Pulse audio should be started manually, press alt+F2 and type ```
pulseaudio
```, the mixer applet goes on the panels, so I think that should prompt you to restart it.

it still doesn't work after all this. any other ideas?

---

### Post by 98whbf on 2009-09-05
> **Baneblade said:**
> im having the same issue on my machines. To save me having to reboot all the time which can become quite tiresome Im currently doing this:

```
killall pulseaudio

sudo alsa force-reload

pulseaudio -D
```which fixes it instantly as long as you ahve closed anything that is using sound before.

this finally worked. thanks for the help. i too hope this is fixed by the time karmic comes out

---

