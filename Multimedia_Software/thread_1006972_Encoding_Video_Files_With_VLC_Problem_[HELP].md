---
title: "Encoding Video Files With VLC Problem [HELP]"
date: 2008-12-09
forum: Multimedia Software
---

### Post by Valtiel on 2008-12-09
I have been trying to encode a .flv video format to .mp4 format [using MPEG-4 for video and MPEG AAC for audio (this is to be played on a PSP)] using VLC without any luck. I've been able to do this using Windows before but for some reason I can't pull it off in Ubuntu.

I ran a seach on google and found this turotial: [http://tazbuntu.blogspot.com/2008/10/convert-video-formats-with-vlc.html](http://tazbuntu.blogspot.com/2008/10/convert-video-formats-with-vlc.html)

I enabled Midibuntu as told in [I have Ubuntu 8.10] [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Then went to Synaptic and downloaded the following [some of those were already installed]

[B]gstreamer0.10-plugins-ugly
gstreamer0.10-plugins-ugly-multiverse
gstreamer0.10-plugins-bad
gstreamer0.10-plugins-bad-multiverse
gstreamer0.10-ffmpeg
ffmpeg2theora[/B]

The tutorial says to install the entire libavcodec files so I installed the following:

[B]libavcodec51
libavcodec-dev
libdlna0
libdlna-dev[/B]

The tutorial says to install the following plugins but:
**w32codecs** : doesn't come up in Synaptic 
 

I'm supposed to intall libdivx for encoding and decoding but when I search for "libdivx" only **avifile-divx-plugin** shows up on the list [I installed that file]

Now after installing all of these files I'm still having problems. When I try to encode the video file, VLC gives me the following error.

[INDENT]
Streaming / Transcoding failed:
VLC could not find encoder "MPEG AAC Audio".
Streaming / Transcoding failed:
VLC could not find encoder "MPEG-4 Video".[/INDENT]


[LIST=1]
[*]Can anybody help me solve this? 

[*]Why does VLC says that it can't find MPEG AAC and MPE-4? The files I installed say that they support these formats?
[/LIST]

---

### Post by wolfen69 on 2008-12-10
[Handbrake]("http://handbrake.fr/") is the 1 click solution to convert videos to mp4 format (and other formats). i have used it for exactly what you want. (i have a psp also) it won't get any easier. you will notice the "presets" on the right of the app for psp's and ipods. i converted some .flv vids to mp4 and it works perfectly.

[This]("http://handbrake.fr/rotation.php?file=HandBrake-0.9.3-Ubuntu_GUI_i386.deb") is the file you need. just click to install.

---

### Post by Valtiel on 2008-12-10
> **wolfen69 said:**
> [Handbrake]("http://handbrake.fr/") is the 1 click solution to convert videos to mp4 format (and other formats). i have used it for exactly what you want. (i have a psp also) it won't get any easier. you will notice the "presets" on the right of the app for psp's and ipods. i converted some .flv vids to mp4 and it works perfectly.

[This]("http://handbrake.fr/rotation.php?file=HandBrake-0.9.3-Ubuntu_GUI_i386.deb") is the file you need. just click to install.

While this doesn't solve my problem with VLC, it does solve my encoding issues. 

Thanks for making this application known to me. It works fantastically :p

---

### Post by coolcat on 2008-12-20
Hi Valtiel,
That tutorial you used is from my blog.
At the very beginning it mentions an update to the page and that you should check out my new page about the WinFF video/audio converter. After I upgraded to Ibex 8.10 I had encountered audio problems when converting a video using VLC.

When you went to Medibuntu did you add both the repository address?;
sudo wget [http://www.medibuntu.org/sources.list.d/intrepid.list](http://www.medibuntu.org/sources.list.d/intrepid.list) --output-document=/etc/apt/sources.list.d/medibuntu.list

and the GPG key?;
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

Both of those need to be added to your repository list in order for you to see or get the codecs you say are missing.

Alternatively you can open up the Synaptic Package Manager and do a search for Ubuntu-Restricted-Extras
If Synaptic can't find that package then you either don't have the Medibuntu repository address inserted into your list or didn't import the GPG Key.

I'm happy that Handbrake works for you and if you have the time you may want to check out the WinFF tool at my page here;

[http://tazbuntu.blogspot.com/2008/11/new-video-converting-and-audio-ripping.html](http://tazbuntu.blogspot.com/2008/11/new-video-converting-and-audio-ripping.html)

It works with Linux and Windows. Updates and new features added on a regular basis.

And I hope to soon find a fix for the audio bug in VLC conversions.
When I do, I will have a new tutorial on my blog.

TaZMAn

[http://tazbuntu.blogspot.com/](http://tazbuntu.blogspot.com/)

---

### Post by indecisive on 2008-12-25
Handbrake scares me.  What are its legal specifications?

---

### Post by wolfen69 on 2008-12-25
> **indecisive said:**
> Handbrake scares me.  What are its legal specifications?

if you use handbrake without proper written consent, the codec police will soon be knocking at your door. followed by 4-5 years hard labor. 

seriously, i don't know what you're worried about. i'm sure 1000's of people use it just fine. are you worried the government is monitoring your activities and will prosecute? what exactly are you worried about?

---

### Post by rocksocke on 2009-03-29
this resolves the vlc-issue:

 sudo apt-get install libavcodec-unstripped-51

hth

---

### Post by alecz20 on 2009-04-12
> **rocksocke said:**
> this resolves the vlc-issue:

 sudo apt-get install libavcodec-unstripped-51

hth

It does seem to solve them, GREAT THANKS!

---

