---
title: "vlc playing audio cd without sound"
date: 2024-10-15
forum: Multimedia Software
---

### Post by satimis on 2024-10-15
Hi all,

I run following command on Terminal to mount the audio cd
~$ gio mount cdda://sr0/

Then
$ gio list cdda://sr0/```

Track 1.wav
Track 2.wav
Track 3.wav
Track 4.wav
Track 5.wav
Track 6.wav
Track 7.wav
Track 8.wav
Track 9.wav
....

```

Playing on vlc
```
Track 1.wav

```

but without sound emitted.  Its progress bar continues to run.

Please help.  Thanks

Regards

---

### Post by Autodave on 2024-10-15
Did you go into the sound mixer and see if the correct input is being used.....and the correct output?

---

### Post by satimis on 2024-10-15
> **Autodave said:**
> Did you go into the sound mixer and see if the correct input is being used.....and the correct output?
Hi,

Thanks for your advice.

Ubuntu 22.04
Where is the sound mixer?  I could not find it in "Activities".

Besides on VLC
Audio -> Audio Device
only following items found;
JBL Pebbles Analogue Stereo
Built-in Audio Digital Stereo (IEC958)

"Audio Disc" above them disappears.  According to my recollection this happens after running "update"

Regards

---

### Post by satimis on 2024-10-16
Hi Autodave,

I found out the trick.  It must be performed in following way:

1. Insert the CD
2. Start VLC
3. Media -> Open Disc
4. Under "Disc" select "Audio CD"
5. Disc device [/dev/sr0]
   Track  [0]
6. -> Play
7. -> Play (again)

Then it works with sound

Regards

---

### Post by satimis on 2024-10-16
Hi Autodave,

I found out the trick.  It must be performed in following way:

1. Insert the CD
2. Start VLC
3. Media -> Open Disc
4. Under "Disc" select "Audio CD"
5. Disc device [/dev/sr0]
   Track  [0]
6. -> Play
7. -> Play (again)

Then it works with sound

Regards

---

