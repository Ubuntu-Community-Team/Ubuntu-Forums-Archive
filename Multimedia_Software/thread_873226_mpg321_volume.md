---
title: "mpg321 volume"
date: 2008-07-28
forum: Multimedia Software
---

### Post by artesvida on 2008-07-28
I have a small server that I'm using to play hold music for our phone system.  It works great, but the volume is inadequate.  As far as I can tell, mpg321 is playing as loudly as possible.  From the script:

mpg321 -o oss -a /dev/dsp -g 100 -q -@ $playlist

A few questions:  Is there a way to get mpg321 to play more loudly?  If not, is there a way to get these mpg files to be "louder" when played?  Finally, this setup uses the audio that's on the motherboard (it's an older HP PC) -- will I get better volume with an add-in audio card?

I'm looking to avoid having to purchase a headphone amp for this setup.

Thanks!

---

### Post by mssever on 2008-07-29
> **artesvida said:**
> I have a small server that I'm using to play hold music for our phone system.  It works great, but the volume is inadequate.  As far as I can tell, mpg321 is playing as loudly as possible.  From the script:

mpg321 -o oss -a /dev/dsp -g 100 -q -@ $playlist

A few questions:  Is there a way to get mpg321 to play more loudly?  If not, is there a way to get these mpg files to be "louder" when played?  Finally, this setup uses the audio that's on the motherboard (it's an older HP PC) -- will I get better volume with an add-in audio card?

I'm looking to avoid having to purchase a headphone amp for this setup.

Thanks!
I don't know a solution, but depending on your audio files, you could try this workaround:

Open the files in Audacity and run Effect > Amplify.

---

### Post by cariboo on 2008-07-30
You can use mp3gain to increase the gain of your mp3 files:

```
mp3gain -g i some.mp3 
```

Where i is a number of your choice.

Mp3gain is available in the repositories.

Jim

---

