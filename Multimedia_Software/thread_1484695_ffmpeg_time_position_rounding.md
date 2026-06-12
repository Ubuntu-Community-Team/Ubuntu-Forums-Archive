---
title: "ffmpeg time position rounding"
date: 2010-05-16
forum: Multimedia Software
---

### Post by missing.bracket on 2010-05-16
I've written a bash script that extracts the audio out of a movie file and saves it out in separate .wav files using ffmpeg.  Here is the key ffmpeg command:

```
ffmpeg -i $movie_file -vn -ss $start_time -t $duration ${file_name}_${counter}.wav

```

$start_time and $duration are floating point numbers that contain time information in the form of seconds and milliseconds (ss.xxx).  It is important that I am able to control the time down to the millisecond. 

My script works *exactly as hoped* on .avi files.

My script needs to work on an existing archive of .mov files.  My problem is, when I try to use it on a .mov, the audio files created always have start times and durations that have been **rounded up** to the **nearest half-second**.  This breaks up the audio in the wrong spots, and creates files that last too long and have too much extra audio.

What can I do to make my ffmpeg command create .wav files from .mov files that properly recognize a specific number of _milliseconds_?  Or, asked another way, how can I eliminate the rounding behavior?

Thanks!

---

### Post by missing.bracket on 2010-05-16
Any ideas?  Would it be helpful if I supplied more information?  Is there a better place for me to direct this question?

---

### Post by FakeOutdoorsman on 2010-05-17
Have you tried placing *-ss* (and possibly *-t*) before your input?  I'm not sure if it will help, but it is worth a try.  Stop by the *#ffmpeg* IRC channel and ask there too.

---

### Post by missing.bracket on 2010-05-17
I hadn't considered changing the order of the input parameters.  I've given it a shot and (alas) it doesn't change the rounding in the creation of the output file.  Thanks for the input, though!

---

### Post by xzero1 on 2010-05-17
I haven't tried this but I would try the -vframes option. Compute the number of frames needed based on the framerate.

---

