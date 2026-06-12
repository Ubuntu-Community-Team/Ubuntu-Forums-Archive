---
title: "Best Software for Recording Video from EasyCAP device?"
date: 2018-12-30
forum: Multimedia Software
---

### Post by mattlach on 2018-12-30
So,

My fiance has several old VCR tapes she wants to dub to digital format before the tapes degrade.

I went out and bought a VCR (a difficult thing to do in 2018) and did my research and bought a Linux compatible EasyCAP device to give me a analogue composite video input via USB.

So my only remaining question is, what is the best software to use to record this content to a file?

The last time I did this it was ca. 2001.   I used a Hauppauge PCI TV card, and a Windows based software named VirtualDub to record to hard drive using a HUFFYUV lossless compression plugin to minimize CPU load.  I needed to stripe two 7200RPM hard drives in order to get enough write speed to make this work without messing things up.

Today, the hardware is not as limited, and I'm guessing the EasyCap device accelerates mpeg2 compression or something like that, or the USB interface likely wouldn't be fast enough to capture all the RAW data.

All of this said, what software is best to use to commit the stream from the EasyCap device to a file?    I liked VirtualDub on Windows.   It looks like it had a Linux version at some point, but that seems long since defunct.

It seems like there are several programs that can read the input from EasyCap and record video files.   Cheese is one example, but it doesn't give me enough options for what to do with the data for my liking.

What do you guys recommend I use to write the stream to a file?   Can ffmpeg somehow do this directly from the command line?  That would be ideal.

I'd appreciate any thoughts on this subject matter.

Thanks,
Matt

---

### Post by #&amp;thj^% on 2018-12-30
May I suggest you take a careful look at this guide: [https://www.instructables.com/id/EasyCap-DC60-STK1160-VLC-Xubuntu-1310-OpenSource-V/](https://www.instructables.com/id/EasyCap-DC60-STK1160-VLC-Xubuntu-1310-OpenSource-V/)

And for scripting see if anything interesting suits you here: [http://easycap.blogspot.com/p/command-line-tv.html](http://easycap.blogspot.com/p/command-line-tv.html)

---

### Post by mattlach on 2018-12-30
> **1fallen said:**
> May I suggest you take a careful look at this guide: [https://www.instructables.com/id/EasyCap-DC60-STK1160-VLC-Xubuntu-1310-OpenSource-V/](https://www.instructables.com/id/EasyCap-DC60-STK1160-VLC-Xubuntu-1310-OpenSource-V/)

And for scripting see if anything interesting suits you here: [http://easycap.blogspot.com/p/command-line-tv.html](http://easycap.blogspot.com/p/command-line-tv.html)

Thank you for those links, particularly the first one.   It looks like it will be very useful.  It did not show up in my initial Googling!

---

### Post by mattlach on 2018-12-30
Well, I can't make this work.   No matter what I do, even though I am pointing at the correct audio device (I can hear the audio in other software) VLC just doesn't record the audio track, only the video.

Is there any other software I can try?  Maybe I can use ffmpeg directly from the command line?

---

### Post by mattlach on 2018-12-31
In the end I could never get VLC to get the audio track no matter what I did.   I wound up installing OBS and using that instead.  It worked like a charm, except for the audio track being out of sync by almost exactly a second.   Delaying the audio by one second seems to have fixed it though.

---

