---
title: "using gstreamer to output raw PCM to a file"
date: 2011-05-26
forum: Multimedia Software
---

### Post by kgeary on 2011-05-26
I've started playing around with gstreamer and I was wondering if someone could help me achieve the following.  I want to start with a wav file and and, using gstreamer and the wavparse plugin, send the raw PCM(?) output to a file rather than alsa?

I'm a newbie to gstreamer so all help is appreciated.

---

### Post by kostkon on 2011-05-26
Do you think this will work?
```
gst-launch-0.10 filesrc location=path_of_input_wav_file ! wavparse ! filesink location=path_of_output_file
```
I don't know, just test it and let me know :P

---

### Post by kgeary on 2011-06-11
That seemed to do the trick.  Thanks

---

