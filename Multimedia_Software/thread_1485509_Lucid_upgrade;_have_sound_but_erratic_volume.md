---
title: "Lucid upgrade; have sound but erratic volume"
date: 2010-05-16
forum: Multimedia Software
---

### Post by DrJohn999 on 2010-05-16
Upgraded via Update Manager from 9.10 sound-previously-working-just-fine-system. Now, for example, running any audio-producing app (Rythmbox is a good example but its the same for anything including out of a VirtualBox XP install or with MythBuntu):

The main volume control functions, but goes from muted to full volume in just 4 steps; raising it higher has no effect. It gets stranger: in Alsamixer or gnome-alsa-mixer I can see that lowering the desktop volume control to mute causes Master, PCM, Front, Surround, Center, LFE, and Side all to go to zero. Raising the desktop control one step causes all of these but Front to go to 100% instantly. Increasing the desktop control by a few more steps causes Front to step to 100%, after which no further volume increase is perceived. It's as if each step in the desktop volume equals some 25% of the Front setting, and 100% of the others. The audio setting in System, Preferences, Sound, Hardware is "Analog Stereo Output."

If I click 'Mute' on Master in the mixer then all the speakers mute, but unmuting Master does not unmute anything else. Only after I move and release the mouse-down state from the master volume do the other channels unmute.

The volume control in Rythmbox, on the other hand, works seemingly correctly (maybe its going thru Pulseaudio?) And as an aside, why are there no controls for Pulse if it sits on top of ALSA?

I'm really confused by this, as all of it work as "expected" while running 9.10. Here is some output from this system (an ASUS M4A78T-E):

```
$ &#8206;uname -a
Linux M4A78T.mydomain.loc 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:28:05 UTC 2010 x86_64 GNU/Linux
$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: VT1708S Analog [VT1708S Analog]
  Subdevices: 1/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 0: SB [HDA ATI SB], device 1: VT1708S Digital [VT1708S Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.21.
$ head -n 1 /proc/asound/card*/codec#*
Codec: VIA VT1708S
$ ls /proc/asound/card*
/proc/asound/cards

/proc/asound/card0:
codec#0  id  oss_mixer  pcm0c  pcm0p  pcm1p


```
and its all up to date:
```
$ sudo apt-get update
:
:
$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


```

Thanks for any suggestions.

---

### Post by MrNugget on 2010-05-17
Same here. It's really a pain in the ***, because I usually use my mouse wheel to adjust the volume via icon. Now if I just turn one "step" too much, my ears nearly fall off (headphones most of the time).

Other than that... mplayer, Google Chrome and other audio applications block each other. For example, I have to close Chrome and wait a few seconds to get sound working in mplayer.

---

### Post by lidex on 2010-05-17
On an upgrade you'll probably have some issues. Do 'Part A' here:
[http://ubuntuforums.org/showthread.php?t=789578]("http://ubuntuforums.org/showthread.php?t=789578")

Also upgrade alsa via the alsa-upgrade link in my sig.

---

### Post by tenshikun12 on 2010-06-03
Hi,

I think my problem is a bit different: I have either sound, but no sound controller; or else sound controller, but no sound. The change depends on wether I have pulseaudio installed or not.

I upgraded ALSA and did Part A on the suggested thread, but my sound is the same and the volume control is not there.

Any suggestions?

Thank you

---

### Post by lidex on 2010-06-04
> **tenshikun12 said:**
> Hi,

I think my problem is a bit different: I have either sound, but no sound controller; or else sound controller, but no sound. The change depends on wether I have pulseaudio installed or not.

I upgraded ALSA and did Part A on the suggested thread, but my sound is the same and the volume control is not there.

Any suggestions?

Thank you

Right-click the alsa-info script link in my sig and "save as" to your user folder. Then run this command in a terminal:
```
sudo bash utils_alsa-info.sh
```
Enter your user password when prompted. Provide a link for the output or post it here using code tags.

---

### Post by tenshikun12 on 2010-06-04
Hi,

I got help from another post ( [http://ubuntuforums.org/showthread.php?p=9408250#post9408250](http://ubuntuforums.org/showthread.php?p=9408250#post9408250) ) and it solved my problem. However, here goes the output of your script (in the file).

Thanks

---

### Post by highfructose327 on 2010-07-09
I was having the sound stepping issue as the OP and MrNugget very quiet or bleeding ear drums. There is a workaround at [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/441195/comments/15](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/441195/comments/15) that fixed it for me. Thanks to Daniel T Chen and pato101

> 1) see if you have the file ~/.pulse/default.pa
    if not, just get a copy from:
cp /etc/pulse/default.pa ~/.pulse

2) Now, edit ~/.pulse/default.pa
    goto line 55 which should be:
load-module module-udev-detect
    and modify it to be
load-module module-udev-detect ignore_dB=1 (I did not need to do this step)

3) now go a bit up and uncomment the line
#load-module module-alsa-sink
    and modify it to be:
load-module module-alsa-sink control=PCM

4) stop any apps playing sound

5) kill pulseaudio (pulseaudio will respawn by itself):
killall pulseaudio

6) run alsamixer at a terminal and make sure you have Master and LFE levels to about 50 or even 100 if you want loud range. Navigation inside alsamixer is: left and right arrows select channel, up and down arrows modify channel level, M mutes/unmutes a channel.

7) Move gnome sound volume slider: you'll see that now Master and LFE are not touched and that the slider only applies to PCM channel.

8) Go rhythmbox or whatever and play your favourite songs or whatever. Play with the gnome volume slider and see if everything is just OK.


thought I should add the output of aplay -l output

> **** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: VT1708S Analog [VT1708S Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 0: SB [HDA ATI SB], device 1: VT1708S Digital [VT1708S Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


---

### Post by TennSeven on 2010-07-25
I had nearly the exact same problem as OP (mine was maxing at 3 steps instead of 4), and fructose's post solved it.  Thanks for sharing the information!

Note: I also did not have to do the first step.

-TennSeven

---

### Post by lsutiger on 2012-11-23
Thank you!!

---

