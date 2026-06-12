---
title: "WMV files streamed over the internet won't play in Firefox."
date: 2013-05-01
forum: Multimedia Software
---

### Post by alhefner on 2013-05-01
Trying to install GStreamer extra plugins and GSteamer extra plugins (i386) for the Windows Media Player Plug-in so I can view Windows video streamed over the Internet.

I get the following error that I'm unsure of how to correct.

*edit* **SOLVED**! I went to the sticky at the top of this section and did what it said... magic! MAGIC I say!

```

The following packages have unmet dependencies:

gstreamer0.10-plugins-ugly: Depends: libc6 (>= 2.7) but 2.15-0ubuntu10.4 is to be installed
                            Depends: libgcc1 (>= 1:4.1.1) but 1:4.6.3-1ubuntu5 is to be installed
                            Depends: libglib2.0-0 (>= 2.31.2) but 2.32.3-0ubuntu1 is to be installed
                            Depends: libgstreamer-plugins-base0.10-0 (>= 0.10.35.2) but 0.10.36-1ubuntu0.1 is to be installed
                            Depends: libgstreamer0.10-0 (>= 0.10.35.2) but 0.10.36-1ubuntu1 is to be installed
                            Depends: libmad0 (>= 0.15.1b-3) but 0.15.1b-7ubuntu1 is to be installed
                            Depends: liborc-0.4-0 (>= 1:0.4.16) but 1:0.4.16-1ubuntu2 is to be installed
                            Depends: libstdc++6 (>= 4.1.1) but 4.6.3-1ubuntu5 is to be installed
gstreamer0.10-plugins-ugly:i386: Depends: libc6 (>= 2.7) but 2.15-0ubuntu10.4 is to be installed
                                 Depends: libgcc1 (>= 1:4.1.1) but 1:4.6.3-1ubuntu5 is to be installed
                                 Depends: libglib2.0-0 (>= 2.31.2) but 2.32.3-0ubuntu1 is to be installed
                                 Depends: libgstreamer-plugins-base0.10-0 (>= 0.10.35.2) but 0.10.36-1ubuntu0.1 is to be installed
                                 Depends: libgstreamer0.10-0 (>= 0.10.35.2) but 0.10.36-1ubuntu1 is to be installed
                                 Depends: libmad0 (>= 0.15.1b-3) but 0.15.1b-7ubuntu1 is to be installed
                                 Depends: liborc-0.4-0 (>= 1:0.4.16) but 1:0.4.16-1ubuntu2 is to be installed
                                 Depends: libstdc++6 (>= 4.1.1) but 4.6.3-1ubuntu5 is to be installed

```

I would like to correct these unless there is something else to use in place of the Windows Media Player Plug-in.

---

### Post by andrew.46 on 2013-05-01
Do you have an example of such a stream?

---

