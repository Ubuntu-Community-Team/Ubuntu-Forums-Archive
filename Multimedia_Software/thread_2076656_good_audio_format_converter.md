---
title: "good audio format converter"
date: 2012-10-26
forum: Multimedia Software
---

### Post by majorburt on 2012-10-26
as the title suggests, i am looking for a good music converter. i would like it to be easy to use as well as able to convert alot of different formats.

anybody have any suggestions?

---

### Post by BertN45 on 2012-10-26
I use XCFA, which supports MP3, M4A, AAC, OGG, FLAC, WAV. For other formats like WMA I go back to Windows XP in VirtualBox and  FormatFactory.

---

### Post by majorburt on 2012-10-26
> **BertN45 said:**
> I use XCFA, which supports MP3, M4A, AAC, OGG, FLAC, WAV. For other formats like WMA I go back to Windows XP in VirtualBox and  FormatFactory.

can i mess with the song's info (artest, track number, name, album) and things like that with XCFA?

---

### Post by majorburt on 2012-10-26
> **BertN45 said:**
> I use XCFA, which supports MP3, M4A, AAC, OGG, FLAC, WAV. For other formats like WMA I go back to Windows XP in VirtualBox and  FormatFactory.

i tried to install it through the software center but i got this error/warning (The action would require the installation of packages from not authenticated sources.)

i get this error in alot of things, how do i fix it?

---

### Post by ajgreeny on 2012-10-26
Try soundconverter which is available from a ppa [https://launchpad.net/ubuntu/precise/+package/soundconverter](https://launchpad.net/ubuntu/precise/+package/soundconverter) if not from the normal repos for precise. I am still using 10.04 at the moment so have no idea about its availability in 12.04's normal repos, nor for 12.10.

You can also use avconv or ffmpeg, depending on your version of ubuntu, in the terminal.  Whatever you use you will probably need to make sure you have all the codecs that are available from various sources, such as gstreamer plugins, w32codecs (or w64codecs), etc etc, but I am assuming you are already aware of that need.

---

### Post by cybrsaylr on 2012-10-26
Soundconverter works fine with 12.04 and I got it using Synaptic Package Manager.

Prefer using Synaptic Package Manager instead of  the software center.

---

### Post by ajgreeny on 2012-10-26
> **cybrsaylr said:**
> Soundconverter works fine with 12.04 and I got it using Synaptic Package Manager.

Prefer using Synaptic Package Manager instead of  the software center.
Thanks for the info cybrsaylr.

I also agree with you about synaptic.  It's the first thing I install in those versions of ubuntu that do not contain it as default

---

### Post by majorburt on 2012-10-27
you guys rock so much! thank you all for the info.

---

### Post by mike acker on 2012-10-27
> **cybrsaylr said:**
> Soundconverter works fine with 12.04 and I got it using Synaptic Package Manager.

Prefer using Synaptic Package Manager instead of  the software center.

yep, +1 for SoundConverter

ps I found it in the Software library (12.04 LTS )

what I've found is some of the music library program features don't work on the earlier .wav format -- .flac seems to be preferred

the thing that seems to be missing is an option to correct level to 0db

remember: everything should be at 0db except the level on the final power amp.

---

### Post by BertN45 on 2012-10-27
I have just detected formatjunkie, it is new and installed without problems. It seems to offer all formats you could wish for. See for description: [http://ubuntuguide.net/install-format-junkie-media-converter-in-ubuntu](http://ubuntuguide.net/install-format-junkie-media-converter-in-ubuntu)

By the way I installed xcfa using the software center, if that fails you prbably have a problem with software center.

---

### Post by Abhinav Kumar on 2012-11-01
ffmpeg with WinFF

---

### Post by andrew.46 on 2012-11-03
Although WinFF is a fine application I have always thought that time learning the FFmpeg *commandline* is time well spent and a suitably configured copy of FFmpeg will convert most common audio codecs with little difficulty and great flexibility.

---

### Post by thatstheguy on 2012-11-03
> **BertN45 said:**
> I use XCFA, which supports MP3, M4A, AAC, OGG, FLAC, WAV. For other formats like WMA I go back to Windows XP in VirtualBox and  FormatFactory.

I am having problems trying to convert .wav to mp3 using XCFA in Ubuntu 12.10.  Am I missing some codecs?  Any help would be appreciated.  Thanks.

-Chris

---

### Post by Linuxisfast on 2012-11-04
> **thatstheguy said:**
> I am having problems trying to convert .wav to mp3 using XCFA in Ubuntu 12.10.  Am I missing some codecs?  Any help would be appreciated.  Thanks.

-Chris

Enable medibuntu repository and install libavcodec-extra, lame and ffmpeg.

---

### Post by Abhinav Kumar on 2012-11-04
Have a look at man page of ffmpeg by typing in terminal ```
man ffmpeg
```.
You can also look  [here]("http://www.catswhocode.com/blog/19-ffmpeg-commands-for-all-needs")

---

### Post by Yellow Pasque on 2012-11-04
ffmpeg is a verstile tool and its comprehensive man page can be intimidating to those new to it. Finding specific examples on the interweb is probably a better way to start.

---

### Post by majorburt on 2012-11-08
thanks everyone! finally got sound converter to work. 

you guys all rock!!!

---

