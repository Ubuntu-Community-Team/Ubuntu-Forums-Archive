---
title: "video volume normalizer tool"
date: 2012-12-04
forum: Multimedia Software
---

### Post by martinmak on 2012-12-04
I know mp3gain can normalize mp3 files,but I want to normalize volume for my video files.I searched a ddvideo video to mp4gain ,but it need to recodec my videos to mp4 format.
I think many peoples want to normalize video files at the same sound level.Please share your experiences.Thanks.

---

### Post by AstroLlama on 2012-12-05
Is this for making permanent changes to the volume level or only for playback?

---

### Post by silverhaze06 on 2012-12-07
If you want to make permanent changes to the file, the only way I know how is to extract the audio portion of the file in pitivi, then tweak it in audacity, then put the tweaked audio file back in the video with pitivi.

If you just want even volume for playback, use vlc. Click the "show extended settings" button. Then click on the compressor tab and enable it. Then drag down the threshold until the loud parts are no longer way too loud. (I usually do between -25dB and -30dB) Then, turn up the ratio a bit. (I usually set it between 5.1 to 10.1) 

After that I slowly turn up the makeup gain so I can hear the quiet parts. (most files you usually don't want to turn it up past +10dB to avoid clipping the quiet parts of the audio.)

As far as the other settings for the compressor on vlc go, you don't need to worry about them.

---

