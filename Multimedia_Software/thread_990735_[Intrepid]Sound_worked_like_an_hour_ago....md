---
title: "[Intrepid]Sound worked like an hour ago..."
date: 2008-11-23
forum: Multimedia Software
---

### Post by Githlar on 2008-11-23
I'm really not sure what happened. I shut down my computer to install Vista. When I brought it back up the sound didn't work (I don't think). I didn't really notice it until I went to call home using Skype and it gave me an audio output error. Then I checked my volume options and all that is left is PCM where there used be be something like 8-10 options.

I don't remember making any software changes to my computer before I shut it down. Or, none that would mess with the sound at all anyway.

It is worth noting that I removed pulseaudio and am using esound (so I can call out using Skype); though switching back doesn't help my situation.

Has anybody else had any problems like this?

I don't know anything about fiddling with ALSA (which is where I'm guessing the problem is) or I'd give something relating to that.

System: Dell Inpiron 1525
Sound Hardware: Intel HD Audio

If you need any more info, I'll be glad to supply it.

---

### Post by Githlar on 2008-11-23
I tested my problem on a fresh install of Intrepid, but apparently the installation CD doesn't set it up right in the first place?

It is worth noting that this install originated as Hardy and was web-upgraded.

I tried a hint on [HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto) and updated ALSA to its latest version. I didn't work, but then again, that HowTo seems to be more for audio that didn't work in the first place. Like I said, mine worked in the first place, it just suddenly died for no reason after running Intrepid for a few days.

---

### Post by stinger30au on 2008-11-23
my sound on 8.10 will magically vanish every now and then, nothing gets muted, it just decides to go silent

i reboot an its good to run for a few more days straight before it does it again

---

### Post by Githlar on 2008-11-23
Rebooting was the first thing I tried. Unfortunately, it doesn't help at all =(

---

### Post by psyke83 on 2008-11-23
> **stinger30au said:**
> my sound on 8.10 will magically vanish every now and then, nothing gets muted, it just decides to go silent

i reboot an its good to run for a few more days straight before it does it again

There's a bug in Intrepid causing the PCM mixer to get muted. I suspect you have mistaken the PulseAudio mixer device for the real mixer device:

In previous version of Ubuntu, this would open your volume control:
```
$ alsamixer
```

That won't work anymore (because PulseAudio is assigned as the default device). You need to manually specify your hardware device:
```
$ alsamixer -Dhw
```

See: [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

---

### Post by Githlar on 2008-11-23
Now this is very odd. Like I said, I installed Vista. I went to install the sound driver in Vista and I got this error: 

ExitError:Error = Device Object not present, restart the system and run setup again.

I also dont' have my sound device in the Device Manager, however I do have an "Other Device" called Base System Device located at PCI bus 2, device 9, function 2 - I think this is probably it.

It's appearing that it's more like a hardware problem than a software problem. Time to call tech support...

---

### Post by psyke83 on 2008-11-23
> **Githlar said:**
> Now this is very odd. Like I said, I installed Vista. I went to install the sound driver in Vista and I got this error: 

ExitError:Error = Device Object not present, restart the system and run setup again.

I also dont' have my sound device in the Device Manager, however I do have an "Other Device" called Base System Device located at PCI bus 2, device 9, function 2 - I think this is probably it.

It's appearing that it's more like a hardware problem than a software problem. Time to call tech support...

Yes, it's possible - but there's also a bug in Intrepid causing the PCM mixer to get muted. You should check the more "mundane" solutions before chalking it up to defective hardware.

---

### Post by Githlar on 2008-11-23
I didn't mention it, but that was like one of the first things I checked. PCM was all the way up, but all of my audio settings were gone - except PCM. However, I contacted Dell tech support and they told me to run some diagnostics on it. I did and they turned out fine. 'Lo and behold, when I rebooted my computer my sound was bad. Now isn't that odd...

---

### Post by psyke83 on 2008-11-24
> **Githlar said:**
> I didn't mention it, but that was like one of the first things I checked. PCM was all the way up, but all of my audio settings were gone - except PCM. However, I contacted Dell tech support and they told me to run some diagnostics on it. I did and they turned out fine. 'Lo and behold, when I rebooted my computer my sound was bad. Now isn't that odd...

I definitely think you're mixing the PulseAudio mixer controls with the real mixer controls for your card. See my post above.

---

### Post by deh1963 on 2008-11-24
Thanks psyke83.  This has been driving me nuts for the past week.  My sound was working fine and then it just up and quit after one of the latest updates.

Dan

---

### Post by DJ_Peng on 2008-12-29
I got this bug this am after I took a WINE update. Thanks for making me double check if the PCM channel was muted. (It was.)

---

