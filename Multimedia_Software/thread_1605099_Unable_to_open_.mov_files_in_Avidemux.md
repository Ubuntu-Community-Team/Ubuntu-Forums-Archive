---
title: "Unable to open .mov files in Avidemux"
date: 2010-10-24
forum: Multimedia Software
---

### Post by rmcellig on 2010-10-24
I am using version 2.5.3. When I open my .mov files, all I get is a green screen with audio and no video. What should I do?

Is there an easy to use video converter that would allow me to for example to batch convert my mov files to avi?

---

### Post by coffeecat on 2010-10-25
I imagine the video codec is one avidemux can't handle. Do you know which one it is? Notwithstanding that, .mov files from the Mac world have video encoded with h264 which avidemux is hopeless at. I'm very underwhelmed with avidemux because even when you present it with a video that it can handle, if you try to edit it, more often than not you lose audio/video sync.

The answer to your question really depends on which video/audio codecs are in your .mov file, but one app in the repo which may do the job for you is (surprisingly) devede. If you choose DivX/MPEG-4 from the greeter screen it will  render your video into an .avi with xvid (comptaible with divx). You can add several individual files and it will plough through them one by one, fulfilling your batch requirement, but it will name them *yourchosenname*01_01.avi, *yourchosenname*01_02.avi and so on, rather than the original filename. I've tried it with some saved .mov getamac ads and it did the job nicely.

---

### Post by rmcellig on 2010-10-25
Thanks Coffeecat!!

How can I tell which codec is used in my .mov files?

Do you think that when it comes to compatibility I should convert all my mov files to avi format?

---

### Post by coffeecat on 2010-10-25
> **rmcellig said:**
> How can I tell which codec is used in my .mov files?

If you right-click on the file > Properties > Audio/Video tab, it should tell you the codecs.

> **rmcellig said:**
> Do you think that when it comes to compatibility I should convert all my mov files to avi format?

It depends. If you simply want to play them on your Ubuntu computer, using VLC and/or installing all the restricted stuff with the ubuntu-restricted-extras package for Totem should be enough. But if you are wanting to re-encode them for your multimedia player you need to make sure the output files are playable despite what the multimedia player manual might say about file formats. For example: if take the .vob files from a ripped DVD or from the VIDEO_TS folder made by my TV HD/DVD recorder, stitch them together and transcode the resultant mpg file to AVI with devede, my Sony PS3 will play it happily. But if I take that same mpg file and edit it with MPEGStreamclip in MacOS and then transcode it to avi with devede the PS3 won't play it. I'm still puzzling that one out. And the reason I don't use Avidemux to edit the mpg is that when I watch a movie I prefer to see the actors' lip movements matching the sound of their voices. :rolleyes:

Don't forget that each transcode will reduce video quality.

---

### Post by rmcellig on 2010-10-25
Thanks! Good advice. Do you use macs as well? I have Ubuntu dual booting on my iMac. I have a couple of issues I am still trying to fix. It's frustrating at times. I really like wiling in Ubuntu rather than in Os X. I find I have more freedom in Ubuntu.

---

### Post by rmcellig on 2010-10-25
This is the codec used in my mov files:

XVID MPEG-4

What is the best tool to edit these files? Devede?

---

### Post by rmcellig on 2010-10-25
This is the codec used in my mov files:

XVID MPEG-4

What is the best tool to edit these files? Devede?

---

### Post by coffeecat on 2010-10-25
I've got a Mac Mini and I use a KVM switch to share peripherals between the Mini and my home-built Ubuntu machine. Not a whiff or sniff of Windows there although I've left Windows (barely used) on my two laptops.

Yes, I much prefer to use Ubuntu. Interestingly, the clarity of fonts and things in general is better in Ubuntu than on the Mac using the same monitor. But that may be down to the graphics chipsets, Intel on the Mac and an ATI HD4350 in Ubuntu which, despite all the moaning and groaning about ATI around the forum, suits me very well.

By the way, if you are tempted to try MPEGStreamclip on your Mac, [link here]("http://www.squared5.com/"), be aware of a couple of things. You have to enrich Apple with £15 (or whatever the Canadian equivalent is) for a codec package before it will cope with MPEG-2 and, although it will transcode, it has a bewildering choice of codecs and I've never got it to output satisfactory AVIs. I'm sure there's a way though.

The other transcoder that used to be useful was Handbrake. Unfortunately they dropped AVI support over a year ago and at the moment there are only development releases compatible with the versions of gnome that come with Lucid and Maverick. You can get the Mac version but no AVI output, only h264/mp4 iirc.

---

### Post by coffeecat on 2010-10-25
> **rmcellig said:**
> This is the codec used in my mov files:

XVID MPEG-4

What is the best tool to edit these files? Devede?

You posted while I was typing my previous post.

You can't edit with devede, only transcode to AVI or author DVDs. I don't know why Avidemux is choking on that. You could try converting it to XVID/AVI with devede and then editing it with Avidemux, but be prepared for loss of audio/sync. Some people seem happy with Avidemux but I've rarely used it without loss of sync.

The other alternative is MPEGStreamclip as I've linked in my previous post. That should be happy with your .mov files even without the £15-worth from Apple. I should have added that I tried the Windows version of MPEGStreamclip in Wine. Long story short: I eventually got it to "work", but it was not a happy experience.

---

