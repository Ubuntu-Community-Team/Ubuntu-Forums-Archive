---
title: "sound gone when pulseaudio daemon started"
date: 2008-10-23
forum: Multimedia Software
---

### Post by fabbaz on 2008-10-23
i recently fixed my hardware issues and was thus able to finally upgrade to hardy, and now i have a funny problem with pulseaudio

i actually don't care about the pulse audio features, and there actually isn't a pulse daemon running when i start the system, and everything works fine. i can listen to music, flash videos, everything works.
now recently i found out that there finally is a milkdrop visuals version for linux, called projectM and i installed it, and it didn't work because it needs the pulseaudio daemon running (otherwise it blinks for a second and is crashed again, see [http://ubuntuforums.org/showpost.php?p=4847561&postcount=52)]("http://ubuntuforums.org/showpost.php?p=4847561&postcount=52)"), since it visualizes not only a programs output, but aparently everything your speakers shout out. which is cool.

but now the funny thing:

as soon as the daemon is started with "pulseaudio -D", no programm, neither rhythmbox nor totem can start any playback. they give a error message about a refused connection or something, and won't play a sound. (edit: the error message reads: An error occurred: Failed to connect stream: Invalid argument)
as soon as i typed "pulseaudio -k" everything works again.
i tried this about 10 times in a row, starting the daemon reliably kills my audio output, killing the daemon fixes it again :D

now my problem is: i would so much love to see the projectM visualisations, and there doesn't seem to be another way for that than to have the daemon running. but obviously visualisations are no good if there is no audio output. has somebody a similar problem?
thanks for your help!
(i use xfce on a originally ubuntu install, but don't think that is any part of the issue)

---

### Post by prshah on 2008-10-23
> **fabbaz said:**
> as soon as the daemon is started with "pulseaudio -D", no programm, neither rhythmbox nor totem can start any playback. they give a error message about a refused connection or something, and won't play a sound. (edit: the error message reads: An error occurred: Failed to connect stream: Invalid argument)
as soon as i typed "pulseaudio -k" everything works again.
i tried this about 10 times in a row, starting the daemon reliably kills my audio output, killing the daemon fixes it again :D


Open System-Preferences-Sound, Set everything to PulseAudio Sound Server, and test each one; if this works, check other programs. If they don't work, or the test itself fails, post back for further setup.

---

### Post by fabbaz on 2008-10-23
thanks for the hint.
was set on "autodetect": works,
"pulseaudio sound server" doesnt, giving error message:
"audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Failed to connect: Connection refused"
so test failed.

---

### Post by markbuntu on 2008-10-23
You are most likely missing some packages that are important to getting pulseaudio working properly and also having a few setup issues. There is a list of packages you should probably have here:

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

Look for the Packages section. After that, reboot and use System/Preferences/Default Sound Card to set pulseaudio as the alsa default sound card. As you will see in that thread, setting up sound can get far more involved.

---

### Post by fabbaz on 2008-10-23
okay, thank you for that, looks like i will need more time to get into that. i'll report back after the weekend on how it went.

---

