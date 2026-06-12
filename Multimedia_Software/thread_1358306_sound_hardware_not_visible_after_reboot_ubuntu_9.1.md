---
title: "sound hardware not visible after reboot ubuntu 9.10"
date: 2009-12-18
forum: Multimedia Software
---

### Post by kubaa on 2009-12-18
Hi,

I am new on ubuntu, i have just skip from windows few days ago.
Everything goes fine besides my sound:(
When I turn on my computer i have no sound.
When i go to see system->preferences->sound->hardware is empty.
Then when i put in terminal: 
sudo alsa force-reload
The soundcard appears and everything works fine.
In  system->preferences->sound->hardware appears internal audio.

But when I shut down the computer and turn it on again the problem occurs again.

How can I solve this?

Thanks for support!

---

### Post by saltmore on 2009-12-18
Easiest thing would be launch it at startup. Not a pretty solution but should work.
[ ]("https://answers.launchpad.net/ubuntu/+question/68564")

---

### Post by kubaa on 2009-12-18
I have just done what you told me and the problem is still repeating:(
After rebooting i do not have a sound and no soundcard appears in preferences/sound/hardware

---

### Post by kubaa on 2009-12-18
I have just done what you adviced me and it still repeats. after rebooting the soundcard is not visible:(

---

### Post by Ubuntaqua on 2009-12-18
> **kubaa said:**
> I have just done what you adviced me and it still repeats. after rebooting the soundcard is not visible:(

Try to go to System --> Administration --> Logfiles reader (I'm not sure of the name of the menu entry in english, sorry). Then search in a few logfiles if you see anything related to Alsa not succeding on startup (take a look at dmesg, syslog, messages for exemple).

---

### Post by kubaa on 2009-12-18
I found in syslog such things as:

Dec 17 14:03:11 xxx pulseaudio[1886]: alsa-sink.c: ALSA woke us up to write new data to the device, but there was actually nothing to write!
Dec 17 14:03:11 xxx pulseaudio[1886]: alsa-sink.c: Most likely this is a bug in the ALSA driver 'snd_hda_intel'. Please report this issue to the ALSA developers.
Dec 17 14:03:11 xxx pulseaudio[1886]: alsa-sink.c: We were woken up with POLLOUT set -- however a subsequent snd_pcm_avail() returned 0 or another value < min_avail.

and many times:

Dec 17 17:48:14 xxx pulseaudio[2256]: alsa-sink.c: Error opening PCM device front:0: Device or resource busy

Dec 17 17:51:21 xxx wpa_supplicant[955]: CTRL-EVENT-SCAN-RESULTS 
Dec 17 17:51:33 xxx pulseaudio[2256]: alsa-sink.c: Error opening PCM device front:0: Device or resource busy
Dec 17 17:51:56 mirga pulseaudio[2256]: alsa-sink.c: Error opening PCM device front:0: Device or resource busy

---

### Post by Ubuntaqua on 2009-12-18
It is odd indeed.
What sound card is it ?

---

### Post by kubaa on 2009-12-18
I am sorry but i do not know how to check what soundcard it is:(

---

### Post by kubaa on 2009-12-18
When i put in terminal lspci it says:

Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller

---

### Post by jeromestpierre on 2009-12-20
I am experiencing the exact same issue since I upgraded to 9.10. 

Anyone has found a solution yet?

---

### Post by jeromestpierre on 2009-12-20
It's fixed on my end. For myself, it was an ALSA driver version problem. I had change my GRUB menu list to boot the previous kernel version since some issues I didn't had time to fix on 9.04. Since then I had completely forgot about that.

Running the command below to know which ALSA version my system was using before fixing my mess was printing: Advanced Linux Sound Architecture Driver Version 1.0.18rc3.
```

cat /proc/asound/version

```Now running the same command, after fixing my GRUB menu to really use the latest Kernel, gives me the output: Advanced Linux Sound Architecture Driver Version 1.0.20.

Please note that before using the right kernel I also reinstalled PulseAudio, so it might be a combination of both actions that finally fixed it for me.

---

### Post by JurJoa on 2010-02-02
Hi,

We have had the same problem after installing ubuntu 9.10 in a laptop:
    system->preferences->sound->hardware was empty!
The most strange thing is that running previously ubuntu directly from cd, some sound was reproduced correctly with an ogg file.

- The difference: after installing ubuntu on the hard-disk we have tried to "improve" it:
    system->administration->hardware divers
We hade selected the nvidia driver (recommended), but also the software modem.
This last had probably originated a conflict with the modem itself from our laptop and after this the sound hardware had disappeared.
You can search if your ALSA, etc is wrong, but all seems to be correctly (reading [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449) ).

- Our solution: Enter again in
    system->administration->hardware drivers
select software modem and take it off.

Now we can hear different sound files and the videos are also not more mute!

Best regards

---

