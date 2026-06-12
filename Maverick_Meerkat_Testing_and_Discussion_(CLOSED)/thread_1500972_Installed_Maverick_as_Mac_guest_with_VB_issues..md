---
title: "Installed Maverick as Mac guest with VB issues."
date: 2010-06-03
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by GARoss on 2010-06-03
I know it's alpha1 so this is an early post just to let issues be known, OK?

I have VirtualBox v 3.1.8 r61349 installed on Mac OS X 10.6.3 host. Installed as guest OS are Windows XP Home, Ubuntu 10.04 LTS-64 bit & now Ubuntu 10.10 Maverick-64 bit Alpha 1.

Ubuntu 10.10 Maverick Alpha 1 installed without issues. I then proceeded to install Guest Additions without issues. So, mouse & full size window for Maverick working to & from Mac windows.

At boot-up audio is muted every time & will not stay un-muted at re-boot.

I was able to share to a Mac folder & copied a few music files to try audio. I selected Rhythmbox to play an Mp3 & although Rhythmbox seemed to be pre-installed & searched for & installed the required drivers to play Mp3s & ACCs, Rhythmbox suddenly disappeared & couldn't be found. I then re-installed Rhythmbox using the Ubuntu Software Center. Once again it disappeared. Re-booted & repeated the process with the same results! Weird. Hey, it's alpha 1!

I re-try installing Rhythmbox with Synaptic Package Manager.

---

### Post by Merk42 on 2010-06-03
I've had the same issue, I think even with previous development releases.

Also, you may want to update to 3.2.2

---

### Post by cariboo on 2010-06-03
Instead of re-installing, why not just kill the process, use:

```
ps ax | grep rhythmbox
```

to find the pid, then kill it:

```
sudo kill <pid>
```

Then open rhythmbox in a terminal to see what is happening.

---

### Post by GARoss on 2010-06-03
Interesting! 
Mp3s will play in Rhythmbox but it appears the necessary plug-in for AAC audio files (gstreamer0.10-plugins-bad) somehow un-installs Rhythmbox when it is installed.

(Disregard the attached photo)

---

### Post by GARoss on 2010-06-03
> **cariboo907 said:**
> Instead of re-installing, why not just kill the process, use:

```
ps ax | grep rhythmbox
```

to find the pid, then kill it:

```
sudo kill <pid>
```

Then open rhythmbox in a terminal to see what is happening.

When installing *gstreamer0.10-plugins-bad* to play aac music somehow un-installs Rhythmbox. Once Rhythmbox is re-installed, it will play mp3s.

---

### Post by Longinus00 on 2010-06-03
> **cariboo907 said:**
> Instead of re-installing, why not just kill the process, use:

```
ps ax | grep rhythmbox
```

to find the pid, then kill it:

```
sudo kill <pid>
```

Then open rhythmbox in a terminal to see what is happening.

```
killall rhythmbox
```

killall will even tab complete the process name for you!

---

### Post by cariboo on 2010-06-04
I ran into the same problem tonight, I'm in the process of ripping my dvd collection, and wanted to check the results. I selected totem to play the file, it asked me to install gstreamer0.10-plugins-bad, I let it install the codecs, and in the process rhythmbox and totem were removed.

---

### Post by GARoss on 2010-06-04
OK - seems *gstreamer0.10-plugins-bad* install has an issue. As far as I know, which isn't much ;) , this is only needed for AAC audio (iTune audio files) - not mp3s. 

Anyone else have the audio automatically muted at boot?

---

### Post by ranch hand on 2010-06-04
> **GARoss said:**
> OK - seems *gstreamer0.10-plugins-bad* install has an issue. As far as I know, which isn't much ;) , this is only needed for AAC audio (iTune audio files) - not mp3s. 

Anyone else have the audio automatically muted at boot?
In the upper right of the screen there is "search this forum".   A search for muted turned up this;

[http://ubuntuforums.org/showthread.php?t=1490373&highlight=muted](http://ubuntuforums.org/showthread.php?t=1490373&highlight=muted)

---

### Post by GARoss on 2010-06-04
> **ranch hand said:**
> In the upper right of the screen there is "search this forum".   A search for muted turned up this;

[http://ubuntuforums.org/showthread.php?t=1490373&highlight=muted](http://ubuntuforums.org/showthread.php?t=1490373&highlight=muted)

Yup, that fixed it! :)

---

### Post by GARoss on 2010-06-09
An update: Rhythmbox is working now. After upgrading to VB 3.2.4 r62467 nothing changed but I did update Maverick 10.10 yesterday, then tried re-installing Rhythmbox today & successfully installed *gstreamer0.10-plugins-bad* plugin for m4a (AAC audio) without it uninstalling Rhythmbox. Somehow these installs, one or both, effect audio playback - making it drag a tad too slow. A fix for that was made by another Ubuntu forum member & works great. Just add a *sound.conf* file to *etc/modprobe.d* . Create a new file & name it *sound.conf*, then past this text, 

[I]options snd-intel8x0 ac97_clock=48000
options snd slots=snd-intel8x0
# CvwD.FAMlirE10w6:82801AA AC'97 Audio Controller
alias snd-card-0 snd-intel8x0[/I]

inside & you're good to go!

:guitar:

---

