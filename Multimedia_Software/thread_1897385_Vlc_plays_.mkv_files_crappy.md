---
title: "Vlc plays .mkv files crappy"
date: 2011-12-19
forum: Multimedia Software
---

### Post by crazy bird on 2011-12-19
Hi,
 
I've noticed a few times that whenever i want to see a movie in .mkv file format, that Vlc plays that movie crappy. The screen is pixelated and it shocks. Is this a Vlc issue or a .mkv file issue? It thougth that Vlc could play .mkv files without any problems...
 
Any solution for this? I've installed all multimedia support (see my site). I'm running Ubuntu 10.04.3 with all the latest updates.

---

### Post by SeijiSensei on 2011-12-19
Try installing **smplayer**.

---

### Post by crazy bird on 2011-12-19
> **SeijiSensei said:**
> Try installing **smplayer**.

No result, still shocking.

---

### Post by crazy bird on 2011-12-20
Bump

---

### Post by sudodus on 2011-12-20
Are you sure that the mkv video clips are good? Can they be played with another OS and another software?

Are you sure that your computer, graphics card and graphics driver are powerful enough? Can they play the same quality video clips with another encoding or container?

Can you convert a mkv clip to for example mp4 using for example *ffmpeg*, and test how that will play with VLC?

---

### Post by SeijiSensei on 2011-12-20
> **crazy bird said:**
> No result, still shocking.

Since you now have smplayer installed, try playing the file with it then choosing "Options > View Logs > Mplayer" from the menu or hitting the shortcut key Ctrl-m.  This will bring up an extensive log from mplayer detailing all the streams it found in the Matroska container and what codecs it is using to decode the video and audio streams.  If mplayer is having trouble playing a file, the log may give you some clues about the problem.  

You can also try replacing mplayer with mplayer2.  (It's a fork of the original mplayer code.)  Run these commands to add a PPA repository to your sources and install mplayer2. 
```

sudo add-apt-repository ppa:ripps818/coreavc
sudo apt-get update
sudo apt-get install mplayer

```
Note that mplayer2 will be named mplayer and replace your old version of that program that came from Ubuntu.  smplayer will then use the new version.

What video card do you have?  How fast is your CPU?  These matter a lot in terms of the quality of video output.

---

### Post by crazy bird on 2011-12-21
> Are you sure that the mkv video clips are good? Can they be played with another OS and another software?
Vlc doesn't show the file correct, smplayer the same. I'll try using a different OS and mediaplayer.
 
> Are you sure that your computer, graphics card and graphics driver are powerful enough? Can they play the same quality video clips with another encoding or container?
- Intel Core2 Quad cpu
- Nvidia Geforce 9500GT (1 gig memory)
- 4 gig RAM
 
Should be sufficient.
 
> Can you convert a mkv clip to for example mp4 using for example *ffmpeg*, and test how that will play with VLC? I normally use Devede to convert video's. I'll try that too.

---

### Post by crazy bird on 2011-12-21
> **SeijiSensei said:**
> Since you now have smplayer installed, try playing the file with it then choosing "Options > View Logs > Mplayer" from the menu or hitting the shortcut key Ctrl-m. This will bring up an extensive log from mplayer detailing all the streams it found in the Matroska container and what codecs it is using to decode the video and audio streams. If mplayer is having trouble playing a file, the log may give you some clues about the problem. 
 
You can also try replacing mplayer with mplayer2. (It's a fork of the original mplayer code.) Run these commands to add a PPA repository to your sources and install mplayer2. 
```

sudo add-apt-repository ppa:ripps818/coreavc
sudo apt-get update
sudo apt-get install mplayer

```
Note that mplayer2 will be named mplayer and replace your old version of that program that came from Ubuntu. smplayer will then use the new version.
 
What video card do you have? How fast is your CPU? These matter a lot in terms of the quality of video output.
 
I'll try that PPA!

---

### Post by sudodus on 2011-12-21
> **crazy bird said:**
> Vlc doesn't show the file correct, smplayer the same. I'll try using a different OS and mediaplayer.
 

- Intel Core2 Quad cpu
- Nvidia Geforce 9500GT (1 gig memory)
- 4 gig RAM
 
Should be sufficient.
 
 I normally use Devede to convert video's. I'll try that too.

What graphics driver are you using? Is it the default driver, the 'built-in' proprietary driver, that is offered more or less automatically, or have you downloaded a driver from nvidia?

And yes, your hardware should be sufficient.

Good luck with your testing :-)

---

### Post by crazy bird on 2011-12-21
> **sudodus said:**
> What graphics driver are you using? Is it the default driver, the 'built-in' proprietary driver, that is offered more or less automatically, or have you downloaded a driver from nvidia?
 
I'm using the nvidia-current driver. I have the PPA from here: [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

---

### Post by sudodus on 2011-12-21
> **crazy bird said:**
> I'm using the nvidia-current driver. I have the PPA from here: [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates]("https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates")
So I understand you are satisfied with the performance of the graphics in general :-) Then check along the two other lines ... {different OS and mediaplayer, Devede to convert video's}

---

### Post by SeijiSensei on 2011-12-21
> **crazy bird said:**
> I'm using the nvidia-current driver. I have the PPA from here: [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

In smplayer, make sure you have the vdpau driver enabled.  It's in Preferences > General > Video.  It can make a big difference if you have an NVIDIA card, though your CPU has enough horsepower to handle H.264 decodes by itself.

---

### Post by VietCanada on 2011-12-21
Crazybird,

I have the same problem and the same specs. Dual core, Nvidia 9500gt, 4mb ram but I'm using 10.10 64 bit. HDMI connection to 42" TV. VLC 1.1.4 and DeVeDe. Same driver and ppa for Nvidia card.

I had this problem in the past using mplayer. VLC was the solution then.

Installing Smplayer with m2 ppa and setting the video driver to vdpau seems to work. I was able to watch the end of my file without any problems due to brightness or speed. TY sudodus and [SeijiSensei]("http://ubuntuforums.org/member.php?u=698195").

---

