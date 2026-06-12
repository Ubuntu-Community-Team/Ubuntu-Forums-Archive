---
title: "Re: upgrade video to 4K and enhance video quality simultaneously"
date: 2023-10-11
forum: Multimedia Software
---

### Post by satimis on 2023-10-11
Hi all,

I tried upgrade an old .mp4 video to 4K resolution with following step:

Desktop computer - AMD Ryzen5 8-core CPU
Display - 32" 4K Dell display
RAM - 32G onboard

OS - Ubuntu 22.04 desktop

**[COLOR="#FF0000"]On Terminal run following command:[/COLOR]**
$ ffmpeg -i old_video.mp4 -vf scale=3840:2160 new_video_4k.mp4

It works, taking about 9 min to finish
File size - increasing from 37.5 MB to 283.9 MB

The 4K new video takes up the full 32" 4K display.  But there is no improvement on its quality.  Is there any way to enhance the video quality as well.

Please advise.  Thanks

Regards

---

### Post by SeijiSensei on 2023-10-11
You can't create information that does not exist in the original source. Upscaling a video will rarely improve quality.

---

### Post by Dennis N on 2023-10-11
You are going to need an AI upscaler that works on video in the same way that Upscayl works on photos. Maybe start here:

[5 Best AI Video Upscaling Software for 2023]("https://photography.tutsplus.com/articles/5-best-ai-video-upscaling-software-for-2023-free-premium--cms-107285")

---

### Post by satimis on 2023-10-12
> **Dennis N said:**
> You are going to need an AI upscaler that works on video in the same way that Upscayl works on photos. Maybe start here:

[5 Best AI Video Upscaling Software for 2023]("https://photography.tutsplus.com/articles/5-best-ai-video-upscaling-software-for-2023-free-premium--cms-107285")
Hi,

Thanks for your advice and link.

I tried;
[https://app.tensorpix.ai/videos](https://app.tensorpix.ai/videos)
online

Upload the original old video, size 37.5MB

**[COLOR="#FF0000"]Options selected[/COLOR]**
noise reduction v2
deep cleaner light
(only allowed selecting 2 options)

It took about 23 min to finish processing but not much improvement obtained.  Please see attached screenshots

Regard

---

### Post by Dennis N on 2023-10-12
I've only been doing images, not videos, but I think the same limitations to AI upscaling would apply. The quality of the output depends on the quality of the input, like resolution (dpi) and focus. Your original might just be a poor candidate for these reasons. You can read this article that discusses video editing and its limitations. It will give you answers from an expert.

[What Video Upscalers Can and Can't Do]("https://www.extremetech.com/extreme/338403-what-video-ai-upscalers-can-and-cant-do")

---

### Post by satimis on 2023-10-12
> **Dennis N said:**
> I've only been doing images, not videos, but I think the same limitations to AI upscaling would apply. The quality of the output depends on the quality of the input, like resolution (dpi) and focus. Your original might just be a poor candidate for these reasons. You can read this article that discusses video editing and its limitations. It will give you answers from an expert.

[What Video Upscalers Can and Can't Do]("https://www.extremetech.com/extreme/338403-what-video-ai-upscalers-can-and-cant-do")

Thanks for your link.

On Google searching I found follows:-

[B][COLOR="#FF0000"]1)
BEST Free Video Enhancer to Improve Video Quality[/COLOR][/B]
[https://www.guru99.com/video-quality-enhancer.html](https://www.guru99.com/video-quality-enhancer.html)

**All of them are NOT FREE**

[B][COLOR="#FF0000"][COLOR="#FF0000"]2)
Open Source Video Upscalers[/COLOR][/COLOR][/B]
[https://sourceforge.net/directory/video-upscalers/](https://sourceforge.net/directory/video-upscalers/)

[B][COLOR="#FF0000"]3)
Top 3 AI Video Upscaling Open-Source Software in 2023[/COLOR][/B]
[https://www.hitpaw.com/video-tips/ai-video-upscaling-open-source.html](https://www.hitpaw.com/video-tips/ai-video-upscaling-open-source.html)

folks on the forum having experience please shed me some light.

Thanks

---

