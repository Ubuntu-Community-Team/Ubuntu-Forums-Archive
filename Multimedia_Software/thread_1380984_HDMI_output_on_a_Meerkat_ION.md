---
title: "HDMI output on a Meerkat ION"
date: 2010-01-14
forum: Multimedia Software
---

### Post by MirrorMatter on 2010-01-14
Hello, everyone.

I work at a television station and we recently purchased a System76 Meerkat ION with the intended purpose of using the HDMI out port for broadcast purposes.  We have an existing AJA HA5 box which is capable of converting HDMI to HD-SDI (HD-SDI being the baseband standard in professional broadcasting).  The converter is only willing to accept the following values:

1920 x 1080 @ 29.97
1280 x 720 @ 59.94

I am wondering if it is possible to manually configure Xorg.conf (or whatever file is being edited by NVIDIA X Server Settings) to tell the HDMI output to only produce the latter resolution (1280 x 720).  Otherwise, my boss wants it sent back.  :)

Any ideas?

---

### Post by MirrorMatter on 2010-01-15
I may have added too much extraneous information in my initial post.  What I am wondering is simply this:

Is it possible to edit a configuration file to permanently set the output resolution of an HDMI port to 1280 x 720 and, if so, how can that be accomplished?

---

