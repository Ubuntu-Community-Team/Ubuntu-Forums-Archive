---
title: "How do I compress DVD iso images but keep Dolby Digital?"
date: 2008-11-23
forum: Multimedia Software
---

### Post by Maheriano on 2008-11-23
I got some 480i DVD and I'm ripping them but they're about 8 gigs each and after ripping my entire library I don't think I'm going to have much space left on my drive. So how can I rip them a different way? My main concern is that I keep the digital audio playback which is why I was originally ripping them into an image and using VCD to play them. Is it possible?

---

### Post by LinuxPS2 on 2008-11-24
should be able to rip them using something like dvd::rip or acid-rip and still keep the 6 channel sound... i think it might depend on the container format too... not sure though, i know mkv can store multiple audio tracks that are 5.1 and I'm pretty sure mp4 container can too...

I hope that works for you- if you really just wanna have it as an ISO I'm not quite sure other than stripping out the extra audio tracks but I don't know how to do that or if it would decrease the size significantly

---

### Post by RawMustard on 2008-11-24
Rip the DVD using vobcopy then use avidemux to save the ac3/dts file to separate files.  Then tell avidemux to encode the video to xvid or h264 without sound.  Once encoding has finished, mix the sound and video into an mkv file using mkvtoolnix-gui.

Works brilliantly I do it all the time. you can even mix in the chapters by using chapextract to extract them from the dvd.

The mkv container format can hold as many files and combinations you like, you can hold music video covers, chapters, subs, you name it, it simply is the very best!

All the tools I mentioned are an apt-get install away, as simple as abc :)

---

### Post by Maheriano on 2008-11-24
Cool, do these ways also keep all the menus and extra features as well? I want everything that's normally on the DVD to be available.

---

### Post by shirilover on 2008-11-24
No, they most likely won't. However, you can use k9copy to shirink the overall size of the DVD(DVD9 -> DVD5). This may introduce macroblocking and other video irregularities.

---

### Post by RawMustard on 2008-11-25
> **Maheriano said:**
> Cool, do these ways also keep all the menus and extra features as well? I want everything that's normally on the DVD to be available.

Yes it can, but you have to do each title separately and then mix it all together in mkvtoolnix, it's a big job! Plus the only players that can handle multiple tracks and chapters in mkv are vlc and mplayer from my understanding.

---

