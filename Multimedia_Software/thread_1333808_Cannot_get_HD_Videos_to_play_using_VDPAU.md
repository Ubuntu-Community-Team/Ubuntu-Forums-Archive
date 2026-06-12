---
title: "Cannot get HD Videos to play using VDPAU"
date: 2009-11-21
forum: Multimedia Software
---

### Post by bburrito on 2009-11-21
I have been trying for literally a week now and have not been able to get mplayer to work with VDPAU.  Whenever I try any hd videos I have, they all come across shaky and my cpu power shoots up which tells me it is not working like it is supposed to. Can anybody point me in the right direction?  I have tried loading and unloading all sorts of drivers, but Mplayer just gives me an error saying that it cant load the -vo video output.  I have searched for this error and tried several methods of trying to resolve this with no luck. I even tried using a version of mplayer that came preconfigured with vdpau but it still does not work.  If I try other programs like Movie Player or VLC , the videos just stutter and again 100% cpu usage.  The hardware is a Zotac Ion system with Atom N330.   Video card is supposed to be plenty fast for HD video, but it seems so far that I cant get the system to use the video card for decoding the HD video.  Any ideas?

---

### Post by renkinjutsu on 2009-11-21
Do you have the [nvidia]("http://nvidia.com/object/unix.html") drivers installed? .. You need it to be able to use vdpau

also, it's a good idea to install mplayer from source, and let it automatically detect vdpau.. 

just to make sure.. you're trying to run with vdpau in an environment running X right?

---

### Post by bburrito on 2009-12-08
Well, I thought I had it up and running as all of a sudden performance increased for some large files, but now I am not so sure.  I am trying to play a 1080p x264 mkv file and it is causing my processor to spike at 90% percent and I am getting choppy video playback and dropped frames.  Even a 720p file was causing 60-80% cpu utilization  Yes, I am using an x environment using the latest version of Ubuntu.  

The nvidia driver that I have installed is nvidia-195-libvdpau.  Is that correct?  How would I go about installing from source?   I admit I am a linux noob.

My system is a Zotac Ionitx with the Atom330 which I have overclocked to 2.1 ghz.  From what I have heard this system is plenty powerful for playing back hd video.  Now this is a dual core processor which shows up as 4 threads in Ubuntu.  Is there any problem with this and VDPAU?

---

### Post by Bachstelze on 2009-12-08
MPlayer doesn't use VDPAU by default. Try this, and see if it changes something.

```
mplayer -vc ffh264_vdpau foo.mkv
```

---

### Post by gradinaruvasile on 2009-12-08
> **Bachstelze said:**
> MPlayer doesn't use VDPAU by default. Try this, and see if it changes something.

```
mplayer -vc ffh264_vdpau foo.mkv
```

Actually its:

mplayer [COLOR="Red"]-vo vdpau -vc ffh264vdpau[/COLOR] foo.mkv

Make sure you have the VDPAU-enabled version of mplayer. From the VDPAU PPA:

[https://launchpad.net/~nvidia-vdpau/+archive/ppa](https://launchpad.net/~nvidia-vdpau/+archive/ppa)

---

### Post by xc3RnbFO8P on 2009-12-08
Add this in your
~/.mplayer/config

> vo=vdpau,xv,
vc=ffh264vdpau,ffvc1vdpau,ffmpeg12vdpau

---

### Post by bburrito on 2009-12-09
So ok, this is total noob territory but how do I access ~/.mplayer/config?

I found mplayer.conf in the /usr/local/etc/ path but because I was logged in as a regular user I could not access it.  Where would I make these configuration changes at?

---

### Post by bburrito on 2009-12-09
I tried installing the vdpau version from the PPA mentioned but it forces a no-gui version.  Is there any way to have a gui and still use vdpau?

---

### Post by bburrito on 2009-12-11
Ok, so I have mplayer installed now and when running it from terminal using the commands mentioned it runs 1080p videos beautifully now.   BUT, when I try to run it from the gui it still stutters and craps out.  I tried running ~/mplayer$ ./configure --enable-gui --disable-x264-lavc --disable-x264 --enable-vdpau --prefix=/usr --confdir=/etc/mplayer --mandir=/usr/share/man  which I found on another website but unfortunately this errors out with the following error:   Error: The GUI requires libavcodec with PNG support (needs zlib).  I went and checked to see if the libavcodec is installed and yes I have libavcodec-extra-52 installed via synaptic.   Does anybody know what could be going wrong here?  I have not been able to find another package with zlib in it.

---

### Post by xc3RnbFO8P on 2009-12-12
> Ok, so I have mplayer installed now and when running it from terminal using the commands mentioned it runs 1080p videos beautifully now. BUT, when I try to run it from the gui it still stutters and craps out.
~/.mplayer/config 
Its a hidden folder use ctrl-h or in file browser> view> show hidden files.
You can also do:
> gedit /home/your folder/.mplayer/config
and add these lines:
> vo=vdpau,xv,
vc=ffh264vdpau,ffvc1vdpau,ffmpeg12vdpau

---

### Post by arun181818 on 2009-12-15
Try smplayer. It can be installed from ubuntu software centre.
In preferences, go to the performance settings and change loop filter to skip (always)
See if this helps.

---

