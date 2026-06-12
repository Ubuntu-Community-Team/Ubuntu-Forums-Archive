---
title: "Disc burners do not work for an audio CD"
date: 2020-04-05
forum: Multimedia Software
---

### Post by jordboal on 2020-04-05
I tried all these several times on my Ubuntu 18.04.4 LTS. Brasero starts burning a music CD but freezes. Burner and SimpleBurn do not have the function to burn audio CDs. K3b says that I do not have permission to read or burn a CD/DVD. What on Earth happens?

---

### Post by Autodave on 2020-04-05
First of all, are you burning .wav files?

If so, then try *xfburn.*

---

### Post by Yellow Pasque on 2020-04-06
> **Autodave said:**
> First of all, are you burning .wav files? If so, then try *xfburn.*
xfburn (and Brasero) can handle formats other than WAV for audio CD's (assuming the appropriate gstreamer plugins are installed). It will transcode as an intermediate step.

>  K3b says that I do not have permission to read or burn a CD/DVD.
For K3b, I always find it best to make sure the user is a member of the cdrom group and set K3b's preferences to use 'cdrom' as the burning group.

---

### Post by lwalper on 2020-04-25
1. Yes, burning .wav files
2. K3B burn failed with the error "try using TAO mode" (or something to that effect)
3. Installed xfburn
4. Tried to burn using TAO mode
5. Burn run failed

How do I burn an audio CD?

---

