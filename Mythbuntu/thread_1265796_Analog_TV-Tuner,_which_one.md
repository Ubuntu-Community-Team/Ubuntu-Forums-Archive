---
title: "Analog TV-Tuner, which one?"
date: 2009-09-13
forum: Mythbuntu
---

### Post by Xetroc on 2009-09-13
Hi.

I am building my first mediacenter, and wanted to try out Mythbuntu.

I need an analog tv-tuner, and want to know if anyone can recommend any?

I found the list of supported cards, but I am unsure if i should chose a hardware or software encoding card.

My CPU is an AMD Athlon 64 X2 4800+ 2.4ghz, is the cpu large enough to support a software encoding tvtuner and go MPEG-4 ?

My budget is kinda limited, but then again, don't want something really crappy, as analog signal is bad enough as it is. Might consider 2 tuners.

Hope someone can help me, Thanks alot :popcorn:

---

### Post by ahood on 2009-09-14
My myth system (8.04) has Hauppauge PVR-150, -250, and a -500 tv tuner cards (4 tuners in total). These older Hauppauge cards have worked out of the box for me with 8.04. I have not tried the newer digital/analog Hauppauge cards. 

See the following post.

[http://ubuntuforums.org/showthread.php?p=7816518#post7816518](http://ubuntuforums.org/showthread.php?p=7816518#post7816518)

If you have specific questions, fire away.

Hope this helps.

---

### Post by newlinux on 2009-09-14
I have software and hardware analog encoding cards, and after adjusting the capture settings, I really can't tell much of a difference in quality. Any modern CPU should have not problems with a software encoding card takeing up much CPU. It's so easy a caveman could do it.

---

### Post by Xetroc on 2009-09-14
Thanks alot for the replies.

> **ahood said:**
> My myth system (8.04) has Hauppauge PVR-150, -250, and a -500 tv tuner cards (4 tuners in total). These older Hauppauge cards have worked out of the box for me with 8.04. I have not tried the newer digital/analog Hauppauge cards. 

See the following post.

[http://ubuntuforums.org/showthread.php?p=7816518#post7816518](http://ubuntuforums.org/showthread.php?p=7816518#post7816518)

If you have specific questions, fire away.

Hope this helps.

I've considered the Hauppauge cards, my friends said he once had the pvr-500, but he told me the quality was bad, compared with the quality when connecting the cable directly to the tv.

What can you tell me about the image quality ?

Gonna read your link, thanks.

> **newlinux said:**
> I have software and hardware analog encoding cards, and after adjusting the capture settings, I really can't tell much of a difference in quality. Any modern CPU should have not problems with a software encoding card takeing up much CPU. It's so easy a caveman could do it.

Hmm, shouldn't MPEG-4 with software encoding give me a better quality than MPEG-2 with hardware enconding ?

Or does MPEG-4 just produce smaller files with the same quality ? 

I think i'm leaning towards software encoding, can you recommend any cards which works under mythbuntu ?

---

### Post by newlinux on 2009-09-14
> **Xetroc said:**
> 

Hmm, shouldn't MPEG-4 with software encoding give me a better quality than MPEG-2 with hardware enconding ?

Or does MPEG-4 just produce smaller files with the same quality ? 

I think i'm leaning towards software encoding, can you recommend any cards which works under mythbuntu ?

Not necessarily, especially since hardware encoding card have dedicated hardware specifically for encoding. Some of it depends on your encoding settings (and  on the algorithm used for encoding). In this case, what mpeg-4 is mainly better at doing is producing a smaller file.

Are you looking for a PCI or PCIe card? You can take a look at the wiki at linuxtv.org for more info on cards that work.

---

### Post by ahood on 2009-09-15
> **Xetroc said:**
> Thanks alot for the replies.

I've considered the Hauppauge cards, my friends said he once had the pvr-500, but he told me the quality was bad, compared with the quality when connecting the cable directly to the tv.

What can you tell me about the image quality ?

Gonna read your link, thanks.

I don't see a noticeable difference between recorded show and direct analog cable, which includes watching on a 50 inch screen tv. However, video quality is affected by a number of factors, which includes driver used (v4l vs mpeg), resolution (480x480 vs 720x480) and video bitrate (2200 vs 4500 vs 6000). It could also be that I am not that picky about video quality issues.

Because I have only used Hauppauge, I cannot comment on other analog tv tuner cards. 

Because we do a lot of recording, I record initially at a moderate quality setting (720x480, 4500 video bit rate), and then transcode the recordings down to a lower quality setting (2200 video bit rate). The video quality is surprisingly good. 

I cannot complain about the hauppauge cards. They are easy to setup and have done the recordings reliably. Nevertheless, newer hauppauge cards may have superior quality, even for analog signals.

Regards,

---

