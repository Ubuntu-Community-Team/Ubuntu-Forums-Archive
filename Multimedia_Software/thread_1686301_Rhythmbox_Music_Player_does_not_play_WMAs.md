---
title: "Rhythmbox Music Player does not play WMAs"
date: 2011-02-12
forum: Multimedia Software
---

### Post by Maaku on 2011-02-12
I have noticed that when I import my music folder, it never had all the albums I have. So, when I looked, I noticed that all the songs that were not imported had the wma file extension. MP3 is fine, I did have problems with that last time.

I have a lot of good songs encoded with wma. So, how do I get Rhythmbox to play these wma sound files?

I have done some searching, but it does not seem to work. I have tried using gstreamer-0.10-plugins-ugly and multiverse. I even did a restart, which was not really necessary as it has nothing to do with hardware.

Thanks for your support.

---

### Post by mc4man on 2011-02-12
Well it would depend on what type of wma, 
If they are wma lossless then rhythmbox isn't going to play.
wma2 you should be able to already, wma3 you may not if on lucid, on maverick it's supported by default thru the gstreamer ffmpeg plugin

running this will show what support you have
```
gst-inspect | grep wma
```

Ex. here
 > gst-inspect | grep wma
ffmpeg:  ffenc_wmav1: FFmpeg Windows Media Audio 1 encoder
ffmpeg:  ffenc_wmav2: FFmpeg Windows Media Audio 2 encoder
ffmpeg:  ffdec_wmapro: FFmpeg Windows Media Audio 9 Professional decoder
ffmpeg:  ffdec_wmav1: FFmpeg Windows Media Audio 1 decoder
ffmpeg:  ffdec_wmav2: FFmpeg Windows Media Audio 2 decoder
ffmpeg:  ffdec_wmavoice: FFmpeg Windows Media Audio Voice decoder

If on lucid and needing wma3(pro) support then this ppa will provide much better gstreamer plugins (highly trusted ppa IMO

[https://launchpad.net/~gstreamer-developers/+archive/ppa](https://launchpad.net/~gstreamer-developers/+archive/ppa)

---

### Post by Maaku on 2011-02-16
> **mc4man said:**
> Well it would depend on what type of wma, 
If they are wma lossless then rhythmbox isn't going to play.
wma2 you should be able to already, wma3 you may not if on lucid, on maverick it's supported by default thru the gstreamer ffmpeg plugin

running this will show what support you have
```
gst-inspect | grep wma
```Ex. here
 

If on lucid and needing wma3(pro) support then this ppa will provide much better gstreamer plugins (highly trusted ppa IMO

[https://launchpad.net/~gstreamer-developers/+archive/ppa]("https://launchpad.net/%7Egstreamer-developers/+archive/ppa")

Thanks for the reply, mc4man.

Here is the output of that command:
```

ffmpeg:  ffenc_wmav1: FFmpeg Windows Media Audio 1 encoder
ffmpeg:  ffenc_wmav2: FFmpeg Windows Media Audio 2 encoder
ffmpeg:  ffdec_wmapro: FFmpeg Windows Media Audio 9 Professional decoder
ffmpeg:  ffdec_wmav1: FFmpeg Windows Media Audio 1 decoder
ffmpeg:  ffdec_wmav2: FFmpeg Windows Media Audio 2 decoder
ffmpeg:  ffdec_wmavoice: FFmpeg Windows Media Audio Voice decoder
typefindfunctions: video/x-ms-asf: asf, wm, wma, wmv

```

I am a little bit confused with using those other plugins, etc. I added it to my Software Sources, and when I tried installing them, it never made any difference. I am not sure if I did it correctly. I am fairly new to Ubuntu's environment. I can use it as a user, but not really as a advanced user where can I troubleshoot it, etc.

Thanks for your help.

---

### Post by mc4man on 2011-02-16
well you have full wma support in gstreamer and should be able to play all wma except protected wma's and wma lossless

---

### Post by Maaku on 2011-02-18
> **mc4man said:**
> well you have full wma support in gstreamer and should be able to play all wma except protected wma's and wma lossless

Well, when I try and play any wma file, I get playback errors. I tried playing it in Movie Player, and it said that the stream is encrypted and does not support decryption.

Does this mean it's protected? If so, how can I remove it? Or could you advise any other application that has the ability to play both protected and unprotected wma's?

I have tried this using Banshee and Rhythmbox. I am running Ubuntu 10.10.

---

### Post by mc4man on 2011-02-18
> it said that the stream is encrypted and does not support decryption.
Not aware of any linux app that can play or remove the protection.
Possibly the windows install that protected them in the first place can un-protect them.

---

### Post by johntaylor1887 on 2011-02-18
Do you have w32codecs installed? (assuming you are using 32bit ubuntu)

---

### Post by alinastil on 2011-02-18
and when stopped working?

---

### Post by Maaku on 2011-02-21
> **mc4man said:**
> Not aware of any linux app that can play or remove the protection.
Possibly the windows install that protected them in the first place can un-protect them.

I tested this. They play in Windows Media Player without any problems.

> **johntaylor1887 said:**
> Do you have w32codecs installed? (assuming you are using 32bit ubuntu)

Yes, this is 32bit. Not sure if I have them installed. How would I check this?

> **alinastil said:**
> and when stopped working?

Well, now you mention that, they did used to work on the 9.* versions and probably 10.4. I am using 10.10 now.

---

