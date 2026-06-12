---
title: "[SOLVED] MP3 Settings for Sound Juicer"
date: 2008-07-29
forum: Multimedia Software
---

### Post by Alexander-GG on 2008-07-29
Hi,

I'm using Ubuntu Hardy just about 2,5 weeks. But, I was so charmed with it, that 3 days ago I made a decision to completely remove Windows from my PC (I don't like the dual boot systems). So I did and now Ubuntu is the prime and only OS at my main PC ... and I feel fine!

I have just one question (right now). Do someone know how to change the mp3 converting settings for Sound Juicer. By default it is set to VBR 128 kbps. It looks so - Cd Quality, MP3 - "audio/x-raw-int,rate=44100,channels=2 ! lame name=enc mode=0 vbr-quality=6 ! id3v2mux".

I want to set - CBR 320 kbps or ABR 320 kbps. (At least 256 kbps will be fine too).

Today I ripped CD in flac format and then converted it by Gnome Sound Converter to MP3 CBR 256 kbps. But, this is a double time work.

Please, help me!!!

---

### Post by evets25 on 2008-07-29
Perhaps you should try grip? I find it has many, many more options for configuring how exactly your music is ripped and encoded. Plus, it's a lot easier to configure. Sound Juicer is great if you just want basic ripping functionality, but as soon as you want to change anything or configure it slightly differently, it becomes very difficult to do so. Anywho, just run this to install grip and try it out: 

```
sudo apt-get install grip
```

---

### Post by Alexander-GG on 2008-07-30
Thank you. I'll give a try to grip. As I can see from it's manual and screenshots, it's really mach more functional.

Thank you!

---

### Post by vanadium on 2008-07-30
This mp3 command line in sound juicer is a problem: if you search this forum, you will see that apparently nobody manages to create lame vbr encoded mp3's using sound juicer.

grip indeed is more flexible as it allows using and setting up the actual command line tools. However, I currently use Rubyripper with much satisfaction. It is probably the most secure ripping application available for Linux.

The issue is that linux ripping relies on cdparanoia. cdparanoia seems not anymore developed and it is unsuited to reliably cope with modern CD rom drives that cache audio data.

Rubyripper circumvents this by ripping large chuncks of audio several times and comparing the rips using crc checks. If rips do not match, the section is reripped until 3 rips match.

It appears to be easy to compile Rubyripper, though it might be easier to get the package from [www.getdeb.net](www.getdeb.net) for Gutsy, which does work on Hardy as well.

---

### Post by Alexander-GG on 2008-07-30
Thank you. I'll give a try to Ruby.

I found a good installation manual here - [http://ubuntuforums.org/showthread.php?t=799621](http://ubuntuforums.org/showthread.php?t=799621).

Thank You. :)

---

### Post by vanadium on 2008-07-30
Thank you for this useful link: you made me upgrade to 5.2. The procedure indeed works flawlessly and fast for me.

---

### Post by Alexander-GG on 2008-07-30
I'm glad. Welcome. :)

---

### Post by vanadium on 2008-08-02
I had a rather disconcerting experience with Rubyripper 0.32. I was ripping Tubular Bells II (Mike Oldfield), where tracks flow into each other. To my consternation, there was a strong click between Track 2 ("Dark Star") and Track 3 ("Clear Light"). It appears as if Rubyripper does not always cuts the track on the correct place, and indeed, I could see in Audacity that there was an abrupt difference in the last sample for track 2 and the first of track 3, which is causing the click. This is very unfortunate because Rubyripper at the moment seems to be the only accurate ripping application for Linux.

It might be due to the rather complex indexing on this continuous album: despite the fact that tracks are continuous, each track has "pregaps" and Rubyripper might be leaving the pregaps out.

I see wether I can report this to the developpers. In the mean time: be warned! A workaround where you loose a lot of convenience is to have Rubyripper rip to a single wav/flac file with cue sheet. Then, with shntool, you can transcode in one go to separate ogg/mp3 tracks, which will be perfectly gapless (in case of mp3: provided you use the lame encoder).

---

### Post by Alexander-GG on 2008-08-02
A have tried almost everything. The best method for me is to rip CD with the Sound Juicer in flac format and than convert it to CBR 256 mp3 with Sound Converter. It takes a lot of time, but the result is satisfactory.

I wish the Gnome has something like a Easy CD-DA Extractor. That will be really nice.

---

### Post by vanadium on 2008-08-02
mp3 CBR 256 kbps is not an optimal setting. With a vbr setting, you will produce smaller files that are at least equal in quality.

My concern is "secure ripping", and if possible: "accurate ripping". "Secure ripping" means that at the very least, the program tells you if there was an error and where.

If it is just for ripping some tunes, Sound Juicer is fast, easy and convenient enough.

---

### Post by Alexander-GG on 2008-08-02
Yes, you are right. CBR 256 kbps is not optimal setting, but it is all that Sound Converter has (maybe because of gstreamer spesiphications?). The optimal settings for me is ABR 320 kbps and almost all of my albums (about 90 at PC) are ripped with Easy CD-DA Extractor, which I think is the best CD ripper. ABR is much better than VBR, cause it's more close to target bitrate and at the same time it gives a flaxibility to sound ripper not to force record to 320 kbps while there is a silence or low level sound at the track. In some cases it increases the bitrate even up to 330 or more kbps.

Easy CD-Extractor is a great ripper, but I completely removed Windows from my PC and I don't want to look back. I also was very used to Photoshop. But, there is a GIMP, so I'm getting used to it now.

I installed the Rubyripper, but it can't find my SATA DVD Rewriter. Maybe I should change the default path to it? But I tried and it writes that it can't detect my CD drive. I have no idea what to change.

---

### Post by vanadium on 2008-08-02
After compiling rubyripper, indeed I also had a little problem configuring the cdrom. This was not needed installing a precompiled *.deb.

Hit the "preferences" button in Rubyripper. In Cdrom device, you need to enter the correct device yourself. The easiest way is to look it up in your /etc/fstab. Open a command terminal and display your /etc/fstab file with the command

```

cat /etc/fstab

```

My cdrom line reads like:

```

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

and it is the first entry (/dev/sdc0) that I had to enter in the settings.

---

### Post by Alexander-GG on 2008-08-02
Thanks a lot. I'll try this tomorrow. In case of any problem I'll inform you.

But, what about the correct settings for mp3? It suports the 320 kbps? And how to fill the command line for mp3 settings?

Thank you beforehand. :)

---

### Post by Alexander-GG on 2008-08-03
Today I found this - [http://filesharefreak.com/tutorials/rubyripper-native-secure-cd-ripping-on-linux/](http://filesharefreak.com/tutorials/rubyripper-native-secure-cd-ripping-on-linux/) , But it's for KDE I guess.

---

### Post by Major_Kong on 2008-08-03
> **Alexander-GG said:**
> Today I found this - [http://filesharefreak.com/tutorials/rubyripper-native-secure-cd-ripping-on-linux/](http://filesharefreak.com/tutorials/rubyripper-native-secure-cd-ripping-on-linux/) , But it's for KDE I guess.

The encoder settings are the same.

[http://wiki.hydrogenaudio.org/index.php?title=LAME#Quick_start_.28short_answer.29](http://wiki.hydrogenaudio.org/index.php?title=LAME#Quick_start_.28short_answer.29) - You might want to read this.

---

### Post by Alexander-GG on 2008-08-03
Thank you. This site is really useful. :)

---

### Post by Alexander-GG on 2008-08-05
Thank you very much. I'm using Rubyripper about 2 dayes and it works great! Thanks a lot! :)

---

### Post by BishopPell on 2008-11-09
Hi,

I know the recommendation was to use grip or rubywripper, but I have come across another forum post and referenced website which provides the correct command to fix soundjuicer.  It seems that by default sound juicer is configured for VBR encoding for MP3.  You can enable absolute bit rate encoding

Change the gstreamer pipeline to:

audio/x-raw-int,rate=44100,channels=2 ! lame name=enc vbr=0 bitrate=192 ! id3v2mux

Check out this website for more: [http://www.stchman.com/cd_rip.html](http://www.stchman.com/cd_rip.html)

This other forum post had it referenced

[http://ubuntuforums.org/showthread.php?t=838237](http://ubuntuforums.org/showthread.php?t=838237)

---

