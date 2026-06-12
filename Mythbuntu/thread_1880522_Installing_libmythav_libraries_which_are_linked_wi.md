---
title: "Installing libmythav libraries which are linked with x264"
date: 2011-11-13
forum: Mythbuntu
---

### Post by QuestionofMyth on 2011-11-13
So, I can enable x264 support in ffmpeg by installing the libavcodecs-extra package from multiverse. However, mythffmpeg is not linked with these libraries but rather links its own libmythav libraries. Does Mythbuntu have any precompiled libmythav libraries that are linked with x264?

Alternately, is there any disadvantage to using ffmpeg to do my transcodes via user job script as opposed to libffmpeg? The scripts I've found are all using libffmpeg, but I wish to transcode to x264 so right now that's not possible unless I use the ffmpeg linked with the standard libav* libraries.

Thanks.

---

### Post by nickrout on 2011-11-14
you can use any script you like to transcode.

---

### Post by nhtrader on 2011-11-14
Would you please explain why you're interested in x264 and what benefits it has for you?

---

### Post by nickrout on 2011-11-14
The benefits are clear, smaller files with better quality.

Many people use handbrake to go to h.264 files. There are plenty of examples in the wiki and on the mailing list archive.

---

