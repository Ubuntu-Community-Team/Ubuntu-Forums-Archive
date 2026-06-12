---
title: "was trying to convert ogv to mkv. audio skipping after."
date: 2010-12-02
forum: Multimedia Software
---

### Post by polardude1983 on 2010-12-02
So I did a short 30 second video of Recordmydesktop in ogv, and was wanting to convert it to mkv. So when I did the video was awesome but the sound kept skipping. Here is the conversion command i did

```
ffmpeg -i test.ogv -vcodec libx264 -vpre medium -crf 24 -threads 0 -acodec copy test.mkv
```

video was great, audio not. can anyone help me?

---

### Post by everythingsround on 2010-12-08
I had the same problem...Solution:

swapped out 'copy' after -acoded with 'libfaac'

Hope it's not too late to be of some help :p

---

### Post by polardude1983 on 2010-12-12
Well it still stuttered for me even when i did that, but i did find a solution, to mux the orginal audio from the ogv and input into the mkv. here is what i do

1. Rename recorded video file to "test.ogv"
2. Place test.ogv in Home folder
3. Run command in Terminal
4. ffmpeg -i test.ogv -vcodec libx264 -vpre medium -crf 24 -threads 0 -acodec copy test.mkv
5. Extract audio from OGV with nautilus script "Extract Audio"
6. Rename audio to "test.mp3"
7. Merge test.mp3 with test.mkv with this terminal command
8. mkvmerge -o output-test.mkv -A test.mkv test.mp3
9. Video will be renamed to output-test.mkv

---

