---
title: "Fast input channel switching with bttv"
date: 2009-08-04
forum: Multimedia Software
---

### Post by flux81 on 2009-08-04
Hi all,

I'm trying to ask the V4L2 bttv driver to switch quickly (as fast as possible) between different channels on the same device.

The following works:

    int index = 1;
    if (-1 == ioctl ( m_nFd, VIDIOC_S_INPUT, &index)) 
    {
        exit (0);
    }

but it's not synchronous (I'm using streaming). That is, suppose the current channel is 0, the input appears to switch to channel 1 immediately after the ioctl() without waiting to completely fill the output buffer on channel 0, hence I get mixed up images from different channels. Are there any good ways do this input channel switching and ensuring good performance?

Thanks very much

---

