---
title: "[SOLVED] No sound after plugging in headphones in the microphone jack"
date: 2007-09-01
forum: Multimedia &amp; Video
---

### Post by runemaste644 on 2007-09-01
I accidentally plugged in headphones into my microphone jack, which gave me a very loud beep when i unplugged it. I muted my laptop, unplugged the headphones, and kept it muted for a while. I unmuted it recently and it has not produced audio. my sound card is:

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

But I'm also afraid that if i fix it, it will give microphone feedback. The sound works fine in Windoze.

```
sudo apt-fix my sound card!
```

---

### Post by TryMe on 2007-09-01
Just guessing but have you checked your sound settings?
system -> Preferences -> Sound
You can test each setting. try the OSS options. reset the default device.
On the sound tab enable software sound mixing (ESD)

edit:
also a good thread to read
[http://ubuntuforums.org/showthread.php?p=3290184]("http://ubuntuforums.org/showthread.php?p=3290184")

---

### Post by runemaste644 on 2007-09-03
Still doesnt work... Hmm that could have given it a bug and made the microphone the speaker :p Oh i hope i can fix my HD audio...

And apt-fix wouldnt work! (that would be  a convenient command though if it set stuff back to default...)

---

### Post by TryMe on 2007-09-03
No I don't think plugging your headphones into your microphone jack would not have any effect other then shorting something out. But you say it works under windows. Are you duel booting? If you boot to a live cd does your sound start working?

---

### Post by runemaste644 on 2007-09-04
I am dual booting. I am nervous about the live cd (i might accidentally do install which will wipe my hard drive probably) I used Wubi to install ubuntu anyway.

---

### Post by TryMe on 2007-09-05
You should download the ubuntu  live cd.
[http://www.ubuntu.com/getubuntu/download]("http://www.ubuntu.com/getubuntu/download")
 It boots to a full desktop with an icon labeled Install. If you don't click on the icon and go through the install wizard you are in little danger of wiping anything out. Besides you only need to boot the disk. Sound should play automatically when gnome starts.

---

### Post by runemaste644 on 2007-09-05
I have a Live CD but im pretty sure that on the Live CD it would work. Umm, Would using an ISO image in VirtualBox count? It simulates an actual computer with grub and everything. (Of course i would do that in windows!) But, it obviously messed up the settings or something on the virtual disk, if it wasn't that, sound wouldnt work in Windows either. And i am in Windows now, and it takes a looooooooooooooooooooooooooooooooong time for windows to shut down

---

### Post by dfreer on 2007-09-07
If sound doesn't work in the host OS, it is almost certain that it won't work in your guest OS in virtualbox. Have you tried checking your alsamixer and making sure all of the sound levels are turn up?
```
alsamixer
```

---

### Post by runemaste644 on 2007-09-07
I would do the VirtualBox stuff in Windows, where the sound works!!!!! DUH!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

---

### Post by runemaste644 on 2007-09-07
> **runemaste644 said:**
> I have a Live CD but im pretty sure that on the Live CD it would work. Umm, Would using an ISO image in VirtualBox count? It simulates an actual computer with grub and everything. ***_(Of course i would do that in windows!)_*** But, it obviously messed up the settings or something on the virtual disk, if it wasn't that, sound wouldnt work in Windows either. And i am in Windows now, and it takes a looooooooooooooooooooooooooooooooong time for windows to shut down
  Look at that and see what i said

---

### Post by dfreer on 2007-09-08
indeed you did, evidently I missed that. generally I hear of virtualbox being installed on mac and linux hosts, and actually didn't realize they had a windows port (silly me, I know). no need for:
> DUH!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
;)
On topic, have you tried checking whether anything is muted in alsamixer yet?

---

### Post by runemaste644 on 2007-09-08
Yeah, unlesss it *really* messed me up and now tries to play out of my mike.:-k

---

### Post by victorgreen on 2007-09-13
there are so many threads about sound guys. Ive changed 20 or so settings 4 different ways and they all had different outcomes. look around like im doing

---

### Post by runemaste644 on 2007-09-13
Oh, yeah. Earlier i found out my PCM was muted and when i unmuted it the sound worked.

---

