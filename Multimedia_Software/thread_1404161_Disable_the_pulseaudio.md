---
title: "Disable the pulseaudio?"
date: 2010-02-11
forum: Multimedia Software
---

### Post by AquaFusion on 2010-02-11
I look everywhere to find how to disable PulseAudio, even their wiki didn't seem have the information on 9.10. The reason why I need the pulseaudio to be disabled because it keep crashing my Ubuntu. Again I dont really need the sound. So is there a way to disable PulseAudio without affecting the ubuntu-desktop? Because i attempted to uninstall PulseAudio though the Sypantic Package Manager, found out if I remove PulseAudio, it will remove ubuntu-desktop, is there a way to turn off PulseAudio without affecting ubuntu-desktop?

If anyone wonder, I am using Karmic 9.10

---

### Post by VertexPusher on 2010-02-11
ubuntu-desktop is an empty (meta-)package. You won't lose anything if you remove it.

---

### Post by ell02 on 2010-02-11
[http://ubuntuforums.org/showthread.php?t=1313253&highlight=remove+pulse](http://ubuntuforums.org/showthread.php?t=1313253&highlight=remove+pulse)
This post worked well for me,the 4th down .Pulse doesn't like a game i play.

---

### Post by VertexPusher on 2010-02-11
> **ell02 said:**
> [http://ubuntuforums.org/showthread.php?t=1313253&highlight=remove+pulse](http://ubuntuforums.org/showthread.php?t=1313253&highlight=remove+pulse)
This post worked well for me,the 4th down.
That's way too complicated, and risky because the autoremove step may uninstall an arbitrary number of packages. There's no guarantee that it will work for everyone. Installing esound also doesn't make sense because it will never be used by anything.

Removing PulseAudio is actually quite simple:
```
sudo apt-get install gstreamer0.10-alsa gnome-alsamixer
sudo apt-get purge pulseaudio gstreamer0.10-pulseaudio
```
That's all it takes. And in case you want to revert the changes later, just enter:
```
sudo apt-get install ubuntu-desktop
```

---

### Post by AquaFusion on 2010-02-11
> **VertexPusher said:**
> That's way too complicated, and risky because the autoremove step may uninstall an arbitrary number of packages. There's no guarantee that it will work for everyone. Installing esound also doesn't make sense because it will never be used by anything.

Removing PulseAudio is actually quite simple:
```
sudo apt-get install gstreamer0.10-alsa gnome-alsamixer
sudo apt-get purge pulseaudio gstreamer0.10-pulseaudio
```That's all it takes. And in case you want to revert the changes later, just enter:
```
sudo apt-get install ubuntu-desktop
```
 

Ok great, that what I need, simple thing to do. I will try that and see what happen. I have disabled ALSA as well since my log before crashing is blaming on ALSA for the screw up. It saying that ALSA cannot find the audio device and refuse to work or something like that, hence the crashing moment. But my guts telling me that PulseAudio have something to do with it since WINE use PulseAudio for my gaming. I had this similar problem in 8.10 when there is no sound at all, but the problem got fixed with my friend but later on, problem appeared again.

Curious why the community insist on using PulseAudio since PulseAudio have problems, I noticed the problem with PulseAudio started all the way from 8.04 to now. 4 major version of Ubuntu and yet it still have problems?

---

### Post by VertexPusher on 2010-02-12
> **AquaFusion said:**
> I have disabled ALSA as well since my log before crashing is blaming on ALSA for the screw up. It saying that ALSA cannot find the audio device and refuse to work or something like that, hence the crashing moment.
Which log is blaming what kind of screw-up on ALSA?

Of course, if you disable ALSA, there will be no audio devices.

> Curious why the community insist on using PulseAudio since PulseAudio have problems, I noticed the problem with PulseAudio started all the way from 8.04 to now. 4 major version of Ubuntu and yet it still have problems?
The community doesn't really insist on it. PulseAudio is promoted by a small number of very vocal fanboys.

---

### Post by arealityfarbetween on 2010-04-20
> **VertexPusher said:**
> That's way too complicated, and risky because the autoremove step may uninstall an arbitrary number of packages. There's no guarantee that it will work for everyone. Installing esound also doesn't make sense because it will never be used by anything.

Removing PulseAudio is actually quite simple:
```
sudo apt-get install gstreamer0.10-alsa gnome-alsamixer
sudo apt-get purge pulseaudio gstreamer0.10-pulseaudio
```That's all it takes. And in case you want to revert the changes later, just enter:
```
sudo apt-get install ubuntu-desktop
```

How about this?
```
sudo chmod -x /usr/bin/pulse*
```Then you just configure your ~/.asoundrc and choose a mixer.

It's a question of whether you want to remove or simply disable. I too found all those instructions way to complicated.

Personally though, when I disabled pulse (in any way, removal or other) I had exactly the same problems with audio on alsa so turned out to be a driver problem in snd_intel8x0 fixed by adding tsched=0 to my default.pa.

And for the record, i'm not a pulse fanboy but it beats alsa hands down in useability plus can be made to do some fairly obviously useful stuff (think network sound system...) although my expedition with alsa got me the same results (working surround in my case). I don't really see what the issue is with pulse though-the way i understand it couldn't exist without alsa or some kind of sound driver anyway, it that right?

Just my two pence. :-)

---

### Post by Gimbal1492 on 2010-06-07
> **arealityfarbetween said:**
> How about this?
```
sudo chmod -x /usr/bin/pulse*
```Then you just configure your ~/.asoundrc and choose a mixer.


If you modify the permissions on a file that was installed from a dpkg-managed package, and do not take a certain "next step" (details to follow) then the next  time when the package providing that file is updated, it will effectively undo your work.

As far as what that certain "next step" would be: There's a manual page for the command, dpkg-statoverride . It's where the details would happen to be, authoritatively, as far as what that certain "next step" would be, in consistently modifying the permissions of a package-provided file.

Two pence, back, with accrual.

---

### Post by DoctorLard on 2010-08-24
Pulse Audio has absolutely zero utility on my media PC since it cannot do DTS or AC-3 pass-through. It down-mixes everything to stereo.

---

