---
title: "sound delay viewing dvb-s in kaffeine"
date: 2008-12-14
forum: Multimedia Software
---

### Post by txutxe on 2008-12-14
hi everyone,

i'm experiencing some delay-related problems with kaffeine and satellite tv. It doesn't happen while watching DVD, neither with kaffeine nor with vlc.

The thing is that, while viewing some channels on satellite TV, the sound comes like half a second later than the picture. Sometimes it's even closer, less than half a second, but there's always a delay. In some other channels there's never a delay. Finally, in other channels where you can watch German series, for example, i watch them dubbed in English. The original audio has no delay, but when i switch to English, again, it appears half a second (or less) after the picture.

has anyone else experienced this?

I'm running kubuntu 8.04 and kaffeine version 0.8.6.

I've tried also to install several newer and older versions of kaffeine and ffmpeg codecs from source code, but there's always the same delay.

My card is a lifeview pci trio, saa7134. Do you think it has to be with the card itself? As i said, other versions of kaffeine and ffmpeg behave the same way. I don't think the card is malfunctioning, though. The reason is that in the same machine there's also a windows partition, where the card seems to tune all the channels without any delay at all.

May be there's a workaround for this? I don't know.. may be an option i can set in kaffeine that "forces" the picture to appear half a second later? may be a plugin?

Thanks in advance for your help.

---

### Post by xc3RnbFO8P on 2008-12-14
From Synaptic Package Manager install:
**gstreamer0.10-fluendo-mpegdemux** (0.10.15-1)

---

### Post by txutxe on 2008-12-14
hello,

thanks for the info. However... there seems to be some delay in some channels, it's not half second as it used to, but still they don't match perfectly.

Do i have to set up anything? May be some option from "xine's engine" menu option in kaffeine? Or am i just paranoid about it? hehe.

does the installation of gstreamer0.10-fluendo-mpegdemux make kaffeine use this codec by default?

I'm sorry if this is pretty basic staff, I'm an actual newbie in Linux!!!

Thanks.

---

