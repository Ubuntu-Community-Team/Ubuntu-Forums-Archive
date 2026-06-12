---
title: "Acer Revo, 1080p extremely choppy on Lucid"
date: 2010-05-15
forum: Multimedia Software
---

### Post by davavanstone on 2010-05-15
Hey there, I have recently bought a Revo R3610 to use as a media center.

The problem im getting is 1080p playback, no matter what i try the video and sound is choppy.  This is played from the HDD not as a network share.

Ive tried running films in VLC, mplayer and boxee but all with no avail.

Here are the terminal output of vlc

 [0x126b708] avcodec decoder error: more than 5 seconds of late video -> dropping frame (computer too slow ?)
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one

Another film here

[0xe1d888] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
 m_el[mi_level] == NULL
 arrrrrrrrrrrrrg Up cannot escape itself
[0x126f3c8] dts decoder: DTS channels:6 samplerate:48000 bitrate:1536000
[0x12e12b8] pulse audio output: No. of Audio Channels: 6
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
Stream with high frequencies VQ coding
QPainter::begin: Paint device returned engine == 0, type: 1
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one


this goes over and over

I know for a fact the revo can handle 1080 no probs, as a friend had 2 r3600 (slower models) that play it perfectly.

I have the nvidia drivers installed but it seems to be pushing the processor cores to the max and not using the gpu

any ideas? VDPAU is enabled in boxee but this doesnt help

Dave

---

### Post by Xianath on 2010-05-15
It looks like your video file does not conform to the H.264/MPEG4 AVC HP (high profile) level 4.1 (aka Blu-Ray / DBV), and so can not be decoded in hardware, hence the choppiness. You will need to recode it for compliance. The key word most likely to help in your googling is DXVA. Try a Blu-Ray or HD-DVD if you have any, they should play fine.

---

### Post by davavanstone on 2010-05-15
DXVA stands for DirectX Video Acceleration. DirectX is Microsoft Windows API for interfacing with graphics cards. (GPU)

I dont think it has anything to do with the film as i have tried the same HD films that play on my mates r3600

---

### Post by xc3RnbFO8P on 2010-05-15
Do you have **libvdpau1** installed? (in Synaptic Package Manager)

---

### Post by Xianath on 2010-05-15
I'm aware what DXVA stands for :) Choppy playback is very common when hardware acceleration doesn't kick in. The main reason it wouldn't kick in is bad input format that the hardware can't or doesn't want to handle. There's a lot of info on the 'net on how to make clips DXVA (and hence, VDPAU, VAAPI, XvMC, XvBA, XDAF or whatever else people come up with). It's just likelier you'll find help searching for that rather than VDPAU.

Either way, the errors you posted looked like a source problem, and that was the only thing we had to go by. Since it plays on other boxes just fine, then you have a config problem, very likely what Ringi pointed out.

---

### Post by davavanstone on 2010-05-15
yup libvdpau1 is installed. it is a completely fresh install of lucid, the only difference is that my mates revo is running karmic so gonna try downgrading. Thanks for you help lads, will try karmic and see how i get on

---

### Post by xc3RnbFO8P on 2010-05-15
Before you do, try SMPlayer, in Option> Preferences> General> Video> output driver, choose vdpau

---

### Post by davavanstone on 2010-05-15
Nope, karmic didnt do it, neither did smplayer, must be a hardware problem. we have tried 5 different hd vids even 720, all of which play on the r3600 but not on the r3610

very strange...

---

### Post by xc3RnbFO8P on 2010-05-16
What Kernel are you using, **uname -r**
On my Acer Revo 3600, **2.6.32-21-generic-pae, upgrade from Karmic**
I installed Karmic and Nvidia 185 drivers (vdpau) (after upgrade Nvidia 195.36.15)
Mediubuntu
FFmpeg ubuntu
Mplayer (change the config file)
> gedit /home/your folder/.mplayer/config
and add these lines:
> vo=vdpau,xv,
vc=ffh264vdpau,ffvc1vdpau,ffmpeg12vdpau 
After upgrade I use SMPlayer with output driver vdpau, uses about 10% CPU
[http://ubuntuforums.org/attachment.php?attachmentid=138022&d=1259511338]("http://ubuntuforums.org/attachment.php?attachmentid=138022&d=1259511338")

---

### Post by athut on 2010-05-28
Alright, I ran into this problem last night.  NVIDIA GPUs, perhaps others for that matter, have issues doing there job when you have things like the fancy desktop overlay running.  Go to settings>appearance and turn off visual effects.  All should be well.

Cheers

---

### Post by fuzzmo on 2010-05-28
athut - Thanks for that.  I had the same issue as the OP - turned off effects, and voila 1080p video smooth as butter through Boxee.  Also I am only using it with 1GB of ram at the mo, so anything higher should be gravy...

---

### Post by abdusamed on 2010-06-26
I don't know why but this happens.. when I'm watching an anime and the whole screen pans to either side, the video seems to lag.. like choppiness..I know to fix this problem u need to fix the frame rate or something..like syncing it... in 7, i was using nivida decoder GPU and it did it fine.. what should i do in smyplayer or xmbc? I remember after playing around with the setting in xmbc, i did fix the issue..but after my vdpau is working [after installing libvdapu1] I'M SO GLADE ITS WORKING--- choppiness during panning return..any fix?

---

### Post by Pied on 2010-11-12
Hello,

I'm having a problem with the Revo and video playback as well.

From viewing the same files on different platforms I don't think it's an  encoding issue but probably a hardware decoding issue.  The Revo simply  doesn't have the processor to do the decoding without the help of the  ION hardware decoders.

I've enabled the proprietary Nvidia drivers in Ubuntu and told the player in XBMC to use Vpau but no joy yet.

To narrow things down (before I go to the XBMC forums) does anyone know of a way to verify/test so see if Vpau is installed and working on the system.  Ideally some sort of video test suite?

Assuming it is installed and working then I might be a problem with XBMC but I've tried other video players on Ubuntu and they are choppy as well.

Many thanks for any help.

---

### Post by Jose Catre-Vandis on 2010-11-12
To eliminate a hardware problem, download the XBMC Live CD, boot from it, and try the Video.This should work.....

---

### Post by Pied on 2010-11-15
What a long strange trip it's been...

Loaded up a pen/thumb drive with XBMC live and tried it on the same source and still choppy.

Tried a different file of the same movie (WMV as compared to MKV) and it was better but still choppy.

I was convinced it was a driver issue so took the plunge and installed Windows 7 - Installed Boxee instead of XBMC and the playback is working flawlessly on multiple formats, encodings and containers.

So it would appear it's an issue with either XBMC or the Driver under Ubuntu or both.

I can't believe something seem to work in Windows that doesn't work in Linux...

My preference would still be to run Linux but it's going to be a tough sell to change OS's on the machine..again.  I guess I could go with a dual boot to test.

---

### Post by aaarrrggh on 2011-02-05
Hi Mate,

I just had this same problem and managed to resolve it by going to System > Preferences > Appearance, then clicking on the 'Visual Effects' tab and setting the value to 'none'.

I signed up on this forum just to let you know how I fixed this myself btw ;-)

---

