---
title: "more than 4 GB RAM - worth to invest?"
date: 2012-05-14
forum: Multimedia Software
---

### Post by arapaho on 2012-05-14
1) Is it worth to invest in more than 4 GB RAM and use 64-bit system? I'd like to have hardware specification for comfortable editing of some photo and video from camera on Linux. 

2) Is Linux software able to take advantage of multi-core processors while editing media files? Does Linux kernel and  graphic drivers for Linux support some advanced technologies that are used on Intel i5, i7 CPU?

I want to be sure that my system and applications are capable of using what I invested in.

---

### Post by roelforg on 2012-05-14
May i note that when you have the pae kernel, 32bit linux can access a max of 64gb ram.
But my 2gb laptop almost never surpasses 35% ram usage (and this is with firefox open with 15 tabs and mixxx running with large songs and more stuff)

---

### Post by sudodus on 2012-05-14
> **arapaho said:**
> 1) Is it worth to invest in more than 4 GB RAM and use 64-bit system? I'd like to have hardware specification for comfortable editing of some photo and video from camera on Linux. 

It depends on how big videos you want to edit. For me it is enough with 4 GB.
> 
2) Is Linux software able to take advantage of multi-core processors while editing media files? Does Linux kernel and  graphic drivers for Linux support some advanced technologies that are used on Intel i5, i7 CPU?

I want to be sure that my system and applications are capable of using what I invested in.

Some software is able to take advantage of multi-core processors, for example ffmpeg. There are advanced proprietary graphics drivers for nvidia and ATI, that can use the graphics chip (for example vdpau for nvidia), to ease the burden of the CPUs ...

Download an iso file and test *ubuntu live (booted from a USB or CD drive)!

---

### Post by arapaho on 2012-05-14
@roelforg
I'm asking specifically about graphics editing.

> **sudodus said:**
> It depends on how big videos you want to edit. For me it is enough with 4 GB.
For example converting an hour of HD video to another format? I don't want to get stuck for hours with one application and being unable to check email in the meantime.
And when I edit a photo and listen to internet radio I don't want to wait a minute or two until change is applied. It should work more or less immediately, I mean within seconds.

> **sudodus said:**
> Download an iso file and test *ubuntu live (booted from a USB or CD drive)!
I don't have such top class hardware yet. That's why I'm asking because I am unable to check it myself. I need to know if it does make sense to invest money in it or some middle class would be enough.

Would you recommend to buy separate graphic card or this graphic unit that is available on some Intel CPU's would be enough?

---

### Post by roelforg on 2012-05-14
> **arapaho said:**
> @roelforg
I'm asking specifically about graphics editing.



I know you did,
i was just illustrating how my 2gb easely takes my playing multi-100-mb audiofiles, converting even larger mp4 files to mp3/mp4/flv/whatever at the same time.
The hw-strain is comparable.

Another example: I have a youtube download script that downloads and converts youtube vids to mp4 and mp3 and my lappy happely takes it whilst playing large videos without even stuttering the audio!

---

### Post by sudodus on 2012-05-14
> **arapaho said:**
> @roelforg
I'm asking specifically about graphics editing.


For example converting an hour of HD video to another format? I don't want to get stuck for hours with one application and being unable to check email in the meantime.
And when I edit a photo and listen to internet radio I don't want to wait a minute or two until change is applied. It should work more or less immediately, I mean within seconds.

It takes a lot of time to convert an hour of HD video, and I don't think that RAM is the limiting factor, it is the processing power (CPU possibly aided by the graphics processor). By the way, it is easy to upgrade RAM afterwards if necessary, if you buy a motherboard, that can manage a lot of RAM, so check for that!
> 

I don't have such top class hardware yet. That's why I'm asking because I am unable to check it myself. I need to know if it does make sense to invest money in it or some middle class would be enough.

Would you recommend to buy separate graphic card or this graphic unit that is available on some Intel CPU's would be enough?
Yes, I think you should buy a separate graphics card. I prefer nvidia, but I have read that the support for ATI in Ubuntu is also good now.

[[COLOR="Red"]_http://en.wikipedia.org/wiki/Comparison_of_Nvidia_graphics_processing_units_[/COLOR]]("http://en.wikipedia.org/wiki/Comparison_of_Nvidia_graphics_processing_units")

---

### Post by roelforg on 2012-05-14
> **sudodus said:**
> Yes, I think you should buy a separate graphics card. I prefer nvidia, but I have read that the support for ATI in Ubuntu is also good now.

It is.
Just remember to use the terminal and run
```

sudo amdcccle

```
when you want the ati/amd control panel because the links in dash don't run it as root and it can't do a lot when not run as root.
Besides that little detail, it all works like a breeze.

(typing this from my laptop with a ATI Mobility Radeon HD 2400 XT, it works fine on my friends laptop (ATI) as well)

---

