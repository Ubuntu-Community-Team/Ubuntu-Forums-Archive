---
title: "High pitched squeal when not playing sounds"
date: 2009-07-14
forum: Multimedia Software
---

### Post by jem7v on 2009-07-14
Running Ubuntu 9.04, with NVidia HDA and Realtek ALC662 rev1.  The problem did not exist under 8.10 or earlier versions (have been running Ubuntu on this PC since 7.10, and on other PCs since 6.06).

The problem:
- A quiet, high-pitched squeal that is present whenever the computer is *not playing sounds* or *not muted.*

Details about symptoms:
- Playing a sound file (any source) eliminates the noise while the sound is playing.  Stopping the sound will usually make it return, but often at a different pitch and volume level.
- The sound file is not simply hiding the high pitched noise, as you can actually hear the noise cut in and out as the sound file starts and stops.
- The noise is in stereo: sometimes it is only on the left speaker, sometimes it is only on the right speaker.
- Muting the volume control eliminates the noise while muted, but if un-muted, the noise is still there at the same pitch and intensity as before.
- If I change the volume control in Ubuntu, the pitch of the noise changes randomly, and it disappears in some of the spots on the volume control... until a sound is played and stopped.
- If I am playing a sound file that has moments of silence in the middle of it, the noise will appear during those quiet parts of the sound file.
- The noise is not being contributed by my speakers, as it also present when using headphones.
- It is not a microphone, as there is not one hooked up to this computer and all the input/capture/microphone tracks are muted in the volume mixer.
- It does this no matter what device is chosen under "Sound Preferences," whether it be PulseAudio or Alsa or OSS.

Any ideas where the problem may lie?

---

### Post by Thad Boyd on 2009-10-21
Hi jem7v,

Did you ever find a solution to this problem?  Because I upgraded to Karmic yesterday and have been experiencing the same symptoms.

MB is Gigabyte EP43-UD3L; onboard sound is Realtek ALC888.

My problem is almost identical to yours; a high-pitched whine that starts several seconds after any use of audio.  However, in my case adjusting the volume does not change the pitch of the sound; it does the same thing as any other alsa event, which is to say that it makes the whine stop for a few seconds before it starts up again.

I'm running Mythbuntu, in case that makes any difference, and did not have this problem in Jaunty.  (I switched to Karmic due to a recurring problem with freezes that I believe is because of the nVidia proprietary graphics drivers, but that's a whole separate issue.)

I've tried a few things I've seen suggested in other threads (muting mic boost, uninstalling pulseaudio) but the problem persists.

Did anyone ever find a fix for this?  Any other ideas at all?  Thanks.

---

### Post by fbianconi on 2009-11-02
there's a bug with powersave options
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/381201](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/381201)
solved my problem by comenting out the line
options snd-hda-intel power_save=10
in
/etc/modprobe.d/alsa-base.conf
in karmic

---

### Post by wb31337 on 2009-11-04
> **fbianconi said:**
> there's a bug with powersave options
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/381201](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/381201)
solved my problem by comenting out the line
options snd-hda-intel power_save=10
in
/etc/modprobe.d/alsa-base.conf
in karmic

I was also having the same problem, this worked great. Thanks!

---

### Post by ColeNi on 2010-01-07
> **fbianconi said:**
> there's a bug with powersave options
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/381201](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/381201)
solved my problem by comenting out the line
options snd-hda-intel power_save=10
in
/etc/modprobe.d/alsa-base.conf
in karmic
I'm having the same problem, I just installed Karmic Koala on my laptop and am brand new to Ubuntu, and I don't understand how to try this fix...

---

### Post by jem7v on 2010-01-07
> **fbianconi said:**
> there's a bug with powersave options
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/381201](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/381201)
solved my problem by comenting out the line
options snd-hda-intel power_save=10
in
/etc/modprobe.d/alsa-base.conf
in karmic

Beautiful!  Solved the problem.  Sorry I didn't see this and respond sooner, I must have missed the e-mail notification.



ColeNi:

Open up a terminal.  (For example, Applications > Accessories > Terminal)
Type ```
sudo gedit /etc/modprobe.d/alsa-base.conf 
```
Enter your password.
Find the line that says "options snd-hda-intel power_save=10"; for me, it was the last line of the file.
Put a # at the start of that line to comment it out.
Save the file.
Close GEdit.
Close the terminal.
Finally, praise something to celebrate: the Linux community (for helping out), koala bears everywhere (for being so cute), or an inanimate carbon rod (just for the heck of it.)

Your problem should probably now be solved.

---

### Post by ColeNi on 2010-01-10
> **jem7v said:**
> Beautiful!  Solved the problem.  Sorry I didn't see this and respond sooner, I must have missed the e-mail notification.



ColeNi:

Open up a terminal.  (For example, Applications > Accessories > Terminal)
Type ```
sudo gedit /etc/modprobe.d/alsa-base.conf 
```Enter your password.
Find the line that says "options snd-hda-intel power_save=10"; for me, it was the last line of the file.
Put a # at the start of that line to comment it out.
Save the file.
Close GEdit.
Close the terminal.
Finally, praise something to celebrate: the Linux community (for helping out), koala bears everywhere (for being so cute), or an inanimate carbon rod (just for the heck of it.)

Your problem should probably now be solved.

Hey thanks a lot, this worked...!  Just our of curiosity though, I read somewhere else that if you change the 10 in the same line ("options snd-hda-intel power_save=10") to a "0" this would also fix the problem. Does anyone know if this works?

---

### Post by jem7v on 2010-01-20
I don't know if it works or not.  Why not try it yourself and let us know?

---

### Post by farfellas on 2010-10-09
i seem to be having the same issue with Ubuntu 10.04 LTS - the Lucid Lynx -
i couldnt resolve this with what was advised in this post as the line 
"options snd-hda-intel power_save=10"
did not exist in my 
alsa-base.conf file

any ideas guys?

---

