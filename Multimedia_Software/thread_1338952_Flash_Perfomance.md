---
title: "Flash Perfomance"
date: 2009-11-27
forum: Multimedia Software
---

### Post by Cypher1101 on 2009-11-27
Just out of curiosity, I wanted to ask the community as a whole if anyone gets satisfactory performance from flash on their Linux install. I am not limiting this to any hardware, environment, or even distro. If you use Linux period and find flash usable at all, I'd like to know about it. Be as specific as possible.

I have found fixes for Youtube using greasemonkey scripts to embed the videos in an mplayer window. That's very impressive, but I'm not sure if those scripts can be modified to work with other content providers, like hulu for example. If anyone knows of a similar fix that works for more, if not all, sites that use flash,  then let's hear it. I've googled this for hours and apart from youtube with mplayer and greasemonkey, there aren't many leads

---

### Post by lovinglinux on 2009-11-27
I have experienced really bad flash performance until this week, when I replaced my old P4 3.0Ghz HT processor with a Core 2 duo 2.93 Ghz. Flash works perfectly now, although it still uses too many CPU cycles. With the P4 I was unable to watch flash videos from some web sites, but now I can even encode videos while watching.

I'm not sure if the problem was the capability of the processor to handle the crappy flash code or if the processor was dying, because during last week I was also experiencing intensive CPU usage and lack of application responsiveness with other CPU intensive tasks. It reached a point that it was freaking me out. I wasn't able to multitask anymore if there was something CPU intensive running in the background, like the update-apt-*something* process.

Anyway, you might try the Flash Optimization section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567), although those workarounds were not working for me lately, except for the YouTube related tweaks. I guess YouTube already implemented the code to allow hardware acceleration, so the *OverrideGPUValidation* works pretty well.

---

### Post by PariahVayne on 2009-11-27
> **lovinglinux said:**
> I have experienced really bad flash performance until this week, when I replaced my old P4 3.0Ghz HT processor with a Core 2 duo 2.93 Ghz. Flash works perfectly now, although it still uses too many CPU cycles. With the P4 I was unable to watch flash videos from some web sites, but now I can even encode videos while watching.

I'm not sure if the problem was the capability of the processor to handle the crappy flash code or if the processor was dying, because during last week I was also experiencing intensive CPU usage and lack of application responsiveness with other CPU intensive tasks. It reached a point that it was freaking me out. I wasn't able to multitask anymore if there was something CPU intensive running in the background, like the update-apt-*something* process.

Anyway, you might try the Flash Optimization section of [Firefox optimization and troubleshooting thread]("http://ubuntuforums.org/showthread.php?t=1193567"), although those workarounds were not working for me lately, except for the YouTube related tweaks. I guess YouTube already implemented the code to allow hardware acceleration, so the *OverrideGPUValidation* works pretty well.

My P4 3.0Ghz plays Flash fine.

---

### Post by lovinglinux on 2009-11-27
> **PariahVayne said:**
> My P4 3.0Ghz plays Flash fine.

I also have a notebook with only 256 Mb of RAM and a Sempron 3500, which plays better than my old P4. It uses a lot of CPU cycles, but it's playable.  So I guess my processor was indeed reaching end of life or something. Is that possible? Could it have been damaged when my ASUS motherboard burned more than a year ago?

---

### Post by PariahVayne on 2009-11-27
> **lovinglinux said:**
> I also have a notebook with only 256 Mb of RAM and a Sempron 3500, which plays better than my old P4. It uses a lot of CPU cycles, but it's playable.  So I guess my processor was indeed reaching end of life or something. Is that possible? Could it have been damaged when my ASUS motherboard burned more than a year ago?

Probably, I can play Flash fullscreen with no issues :3

---

### Post by Cypher1101 on 2009-11-28
That's basically what I expected to hear. It seems that it takes a beast of a processor linux to get performance comparable to what most windows users get. Not the greatest news, but good to know.

edit: I turned off gpu validation and its works fine now

---

