---
title: "Mplayer :[AO_ALSA]unable to find simple control 'PCM',0"
date: 2009-03-26
forum: Multimedia Software
---

### Post by plutov03 on 2009-03-26
I've just installed mplayer from add/remove and it's doesn't work well.
[AO_ALSA]unable to find simple control 'PCM',0 ,always appears when i tried to player any multimedia file.I googled myself and couldn't solve it.
Please help me!

---

### Post by andrew.46 on 2009-03-26
Hi plutov03,

> **plutov03 said:**
> I've just installed mplayer from add/remove and it's doesn't work well.
[AO_ALSA]unable to find simple control 'PCM',0 ,always appears when i tried to player any multimedia file.I googled myself and couldn't solve it.
Please help me!

Can I ask you to run the following in a Terminal window and then post the full output here?

```
mplayer -ao help
```

I suspect that there is a problem with your use of alsa and MPlayer, this can be rectified by using a different audio out.

Andrew

---

### Post by binbash on 2009-03-27
I have same error at ubuntu jaunty.

MPlayer 1.0rc2-4.3.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Pentium(R) Dual  CPU  T2330  @ 1.60GHz (Family: 6, Model: 15, Stepping: 13)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Available audio output drivers:
	oss	OSS/ioctl audio output
	alsa	ALSA-0.9.x-1.x audio output
	esd	EsounD audio output
	pulse	PulseAudio audio output
	jack	JACK audio output
	nas	NAS audio output
	sdl	SDLlib audio output
	openal	OpenAL audio output
	mpegpes	DVB audio output
	v4l2	V4L2 MPEG Audio Decoder output
	null	Null audio output
	pcm	RAW PCM/WAVE file writer audio output

This codecs.conf is too old and incompatible with this MPlayer release! at line 6

---

### Post by andrew.46 on 2009-03-27
Hi binbash,

> **binbash said:**
> 
MPlayer 1.0rc2-4.3.3 (C) 2000-2007 MPlayer Team

There must be a certain uncomfortable feeling for the Ubuntu developers to push out such an old version of MPlayer as an official part of a brand new release. But this is an old problem that would probably not benefit from another airing I guess.

```
Available audio output drivers:
	oss	OSS/ioctl audio output
	alsa	ALSA-0.9.x-1.x audio output
	esd	EsounD audio output
	pulse	PulseAudio audio output
	jack	JACK audio output
	nas	NAS audio output
	sdl	SDLlib audio output
	openal	OpenAL audio output
	mpegpes	DVB audio output
	v4l2	V4L2 MPEG Audio Decoder output
	null	Null audio output
	pcm	RAW PCM/WAVE file writer audio output

```

This is your list of available audio drivers. If alsa is off the menu for whatever reason try to open a video file with the following syntax which forces another driver:

```
mplayer -ao pulse myfile.avi
```

where -ao is forcing the audio out(put), next to try would be oss. The million dollar question would be 'why is alsa failing'? And this one I am not sure about.

My own copy of MPlayer under Jaunty does not have this problem, as the attached screenshot demonstrates but I have compiled my own from svn.

Andrew

---

### Post by binbash on 2009-03-27
pulse plays fine at command line but when you use a gui (mplayer's gui or gnome-mplayer etc) when you select pulse as output it does not play and gives an error about the pulse.I am quite sure this is because of old mplayer 

Anyways i am pulling svn build of mplayer and compile it with CoreAVC

---

### Post by andrew.46 on 2009-03-27
Hi binbash,

> **binbash said:**
> pulse plays fine at command line but when you use a gui (mplayer's gui or gnome-mplayer etc) when you select pulse as output it does not play and gives an error about the pulse.I am quite sure this is because of old mplayer 

Could very well be. I personally use rvm's SMPlayer for an MPlayer frontend and it is definitely worth a try.

> Anyways i am pulling svn build of mplayer and compile it with CoreAVC

All the best with this. These forums seem to be awash with MPlayer guides at the moment: straight svn, vdpau, coreAVC and FFmpeg-MT. Quite exciting times with MPlayer at the moment on Ubuntu. I used [the straight svn guide]("http://ubuntuforums.org/showthread.php?t=1081070") for my own copy :-).

**Edit:** BTW I have been reading through your excellent blog, nicely done!! And I see you have your own [info for coreavc]("http://www.ubuntu-inside.me/2009/02/howto-mplayer-with-coreavc-better-hd.html"). Do you need to specify: --enable-alsa --enable-pulse ? Normally doing this can get you into a little trouble.

Andrew

---

### Post by rvm4000 on 2009-03-27
> **plutov03 said:**
> I've just installed mplayer from add/remove and it's doesn't work well.
[AO_ALSA]unable to find simple control 'PCM',0 ,always appears when i tried to player any multimedia file.I googled myself and couldn't solve it.
Please help me!

Try adding this option: *-mixer-channel Master*

That would tell mplayer to use the Master control instead of PCM to control the volume.

---

### Post by binbash on 2009-03-28
@andrew.46

If you don't do that, you can't use pulse etc support.I tried without pulse (--enable-pulse ) and i didn't get pulse support installed.I only wrote what i have tried there so be sure i tried without --enable-pulse etc : ) .

---

### Post by andrew.46 on 2009-03-28
Hi binbash,

> **binbash said:**
> If you don't do that, you can't use pulse etc support.I tried without pulse (--enable-pulse ) and i didn't get pulse support installed.I only wrote what i have tried there so be sure i tried without --enable-pulse etc : ) .

I hope you don't think I was picking on your blog, in fact I have enjoyed reading it immensely!

Oddly enough I have managed to get -ao pulse working without specifying it in ./configure and adding paths to header files (as is usually required). Granted it is not the most up-to-date version of Jaunty, I am running it in VirtualBox and there is an odd message about problems with pause but it works well enough. I attach a screenshot of the action :-).

Andrew

---

### Post by Hellaxe on 2009-08-11
Hello people:
any news about how to use Mplayer and Alsa?
I've (finally) upgraded to Jaunty and this issue is anoying,
OSS is doing the job but I'd preferred ALSA.
Thanks for your answers.

---

### Post by GrFD on 2010-05-05
andrew.46, Thanks for your tips about [CODE]mplayer -ao help[/CODE.
I've been sure my Linux should use ALSA, but it was OSS. After I've set OSS in mplayer (and also in VLC-player), I can just normally look and listen movies with sound and without any stupid alarm.
Thanks a lot of!

---

### Post by voltsy on 2011-10-22
For reasons that might be conmpletely different, I was getting exactly the same message from mplayer when launched by playing media files (in Gnome) using the "Open with..." method of selecting mplayer.

On my eeepc 701SD running Lucid 10.04 (netbook version) the fix was to edit ~/.mplayer/gui.conf and change ao = "alsa" to ao = "pulse"

Strangely, putting ao="pulse" in ~/.mplayer/config had no effect at all

mplayer version: 
MPlayer SVN-r1.0~rc3+svn20090426-4.4.3 (C) 2000-2009 MPlayer Team via medibuntu repository

---

