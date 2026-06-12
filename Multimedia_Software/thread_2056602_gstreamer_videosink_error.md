---
title: "gstreamer videosink error"
date: 2012-09-11
forum: Multimedia Software
---

### Post by Gannin on 2012-09-11
Whenever I try to play a video with Xubuntu using Parole, it gives me an error that says "Gstreamer backend error Configured videosink video is not working."  However, Xubuntu doesn't seem to offer any options on how to change the gstreamer configuration or choose what videosink you have it configured for.

Any help?

---

### Post by diegomanule on 2012-10-26
Hello,

I have the same problem with gstreamer and xubuntu, I think it might be parole...

Moving to VLC.. If you solved this could you please reply with the solution.

Thanks in advance.

Diego.

---

### Post by Toz on 2012-10-26
Have you installed **xubuntu-restricted-extras**?

For more info, see here: [https://help.ubuntu.com/community/RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats").

---

### Post by cppdeveloper on 2013-01-19
The solution to the Xubuntu Parole errors:

"GStreamer backend error"

and

"Could not initialise Xv output"


is to run in the command line the following, only once:

parole --xv false

---

