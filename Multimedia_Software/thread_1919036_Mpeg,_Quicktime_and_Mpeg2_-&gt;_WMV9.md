---
title: "Mpeg, Quicktime and Mpeg2 -&gt; WMV9"
date: 2012-02-02
forum: Multimedia Software
---

### Post by WickedXXL on 2012-02-02
Hi Guys,


Xubuntu 10.10  / Follwed the Instruction here everything fine & installed.

I am very new to the Linux World so please excuse if i ask quesions which have been answered already..

But it is very important to me to solve this problem and i searchd alot up to now , but couldn`t solve it myself..


I have to encode around 80,000 files to WMV9  , 25frames , 720x576, 4000bitrate, audio 192 from one folder to another..

I have installed FFmpeg and all dependencies etc (I assume) and winfFF gui..i have to work with the GUI is i will still need some time to get accustomed to the console :)  But WinFF still shows only WMV2 but i need WMV 9 ?


SO can somebody explain my how i can get all files from /home/downloads/d/mpeg2  encoded to /home/downloads/d/wmv/   for example?

What is the command line parameter?  


I really don`t get it ! thank you! 

I already checked some tutorials but they are over my head :)

---

### Post by wolfen69 on 2012-02-02
What codec packages have you installed?

---

### Post by WickedXXL on 2012-02-02
> **wolfen69 said:**
> What codec packages have you installed?


Medubuntu, w32codecs and everythign else i could find !

Somebody else told me there is no way to encoe WMV9 in linux?

That`s not true right?

---

### Post by ron999 on 2012-02-02
> **WickedXXL said:**
> 

Somebody else told me there is no way to encoe WMV9 in linux?


Is this what you mean by WMV9?

[IMG]http://img684.imageshack.us/img684/117/wmv9.png[/IMG]

---

### Post by Judo on 2012-02-02
FFMPEG has *some* support for encoding WMV 9 (FourCC WMV3) but it's not complete.  It could be enabled at build, I think, but it's probably not sufficient for what you're doing.

---

### Post by FakeOutdoorsman on 2012-02-02
FFmpeg can not currently encode this proprietary format.
```
$ ffmpeg -codecs
 D..... = Decoding supported
 .E.... = Encoding supported
 ..V... = Video codec
 ..A... = Audio codec

 D A    wmalossless     Windows Media Audio 9 Lossless
 D A D  wmapro          Windows Media Audio 9 Professional
 DEA D  wmav1           Windows Media Audio 1
 DEA D  wmav2           Windows Media Audio 2
 D A D  wmavoice        Windows Media Audio Voice
 DEVSD  wmv1            Windows Media Video 7
 DEVSD  wmv2            Windows Media Video 8
 D V D  wmv3            Windows Media Video 9
 D V D  wmv3_vdpau      Windows Media Video 9 VDPAU
 D V D  wmv3image       Windows Media Video 9 Image

```

---

### Post by WickedXXL on 2012-02-03
Thank you all very much for your help ! 

Of course WMV9 does not work actually ! Thank you !

---

