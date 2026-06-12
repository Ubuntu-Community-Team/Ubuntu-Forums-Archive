---
title: "Video Encoding"
date: 2011-01-04
forum: Multimedia Software
---

### Post by Pedroriel on 2011-01-04
Hello Forums,

I just wanted to know what people think is the best video encoding program. I want to be able to convert any video files to any format, mostly x264, avi that sort of stuff. I used AVS encoder in windows. Any recommendations please? 

Pedro

---

### Post by Jahid65 on 2011-01-04
You can use Winff to convert your Videos, but for x264 you need to install an unlocked FFmpeg(with x264 support) (The package in the does not have x264 support). So use Winff for AVI Converting. 

Or you can use Handbrake to convert your video to x264/mp4/mkv/Iphone/Ipod/AppleTV. It's the easiest way I know.
```
sudo add-apt-repository ppa:stebbins/handbrake-releases
sudo apt-get update
sudo apt-get install handrake-gtk
```

---

### Post by Wungle on 2011-01-20
> **Jahid65 said:**
> 
```
sudo add-apt-repository ppa:stebbins/handbrake-releases
sudo apt-get update
sudo apt-get install handrake-gtk
```

Hi Jahid - typo in the code.  
Last line should read:
```
sudo apt-get install handbrake-gtk
```

---

